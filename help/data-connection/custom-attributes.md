---
title: Lägg till anpassade orderattribut
description: Lär dig hur du lägger till anpassade orderattribut i dina back office-data och skickar dessa attribut till Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 14d190726324e2f42d66c2270f2e27be5a74132f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# Lägg till anpassade orderattribut

I den här artikeln får du lära dig hur du lägger till anpassade attribut till back office-händelser. Med anpassade attribut kan ni samla in omfattande datainsikter för att förbättra analysen och ytterligare skapa personaliserade upplevelser för era kunder.

Anpassade attribut stöds på två nivåer:

- Ordernivå
- Orderartikelnivå

>[!NOTE]
>
>Adobe [!DNL Commerce] stöder anpassade attribut med datatypen sträng, Boolean eller date.

Om du lägger till anpassade attribut till Office-händelser måste du:

1. Skapa ett projekt i din [!DNL Commerce]-installation.
1. Uppdatera ditt schema så att de nya anpassade attributen kan hämtas korrekt till Experience Platform.
1. Bekräfta att de anpassade attributen hämtas och skickas till Experience Platform i Admin.

>[!IMPORTANT]
>
>Katalogstrukturen och kodexemplen nedan visar hur du kan implementera anpassade attribut. Den katalogstruktur och kod som krävs beror på din butikskonfiguration och -miljö.

## Steg 1: Skapa katalogstrukturen

1. Navigera till katalogen `app/code` i installationen av [!DNL Commerce] och skapa en modulkatalog. Till exempel: `Magento/AepCustomAttributes`. Den här katalogen innehåller de filer som behövs för dina anpassade attribut.
1. Skapa en underkatalog med namnet `etc` i modulkatalogen. Katalogen `etc` innehåller filerna `module.xml`, `query.xml`, `di.xml` och `et_schema.xml`.

## Steg 2: Definiera beroenden och installationsversionen

Skapa en `module.xml`-fil som definierar beroenden och installationsversionen. Exempel:

```xml
<?xml version="1.0"?>
<!--
/**
* Copyright (c) [year], [name]. All rights reserved.
*/
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
        <sequence>
            <module name="Magento_Staging"/>
            <module name="Magento_SalesRule"/>
        </sequence>
    </module>
</config>
```

## Steg 3: Hämta försäljningsorderdata

Skapa en `query.xml`-fil som hämtar försäljningsorderdata. Exempel:

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## Steg 4: Ställa in beroendeinjektionen

Skapa en `di.xml`-fil som ställer in beroendeinjektionen. Exempel:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.example.instrumentedtest"
          android:versionCode="1"
          android:versionName="1.0">
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
    
    <instrumentation
        android:name=".MyInstrumentationTestRunner"
        android:targetPackage="com.example.instrumentedtest"/>
    
    <!-- More instrumentation elements might be here -->
</manifest>
```

## Steg 5: Definiera de tjänster som används för beroendeinjektionen

Skapa en `et_schema.xml`-fil som definierar de tjänster som används för beroendeinjektionen. Exempel:

```xml
<services>
    <service id="App\Controller\MainController" class="App\Controller\MainController">
        <argument type="service" id="doctrine.orm.default_entity_manager"/>
        <argument type="service" id="form.factory"/>
        <argument type="service" id="security.authorization_checker"/>
    </service>

    <!-- ... -->

    <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
        <argument type="service" id="security.authentication_utils"/>
        <tag name="controller.service_arguments"/>
    </service>

    <!-- ... -->
</services>
```

## Steg 6: Skapa en katalog för PHP-filerna

Skapa en katalog med namnet `Module/Provider` på samma nivå som katalogen `etc`. Den här katalogen innehåller `OrderCustomAttributes`- och `OrderItemCustomAttributes` PHP-filerna.

## Steg 7: Definiera OrderCustomAttributes

Skapa en `OrderCustomAttributes.php`-fil som definierar anpassade attribut för ordningen. Exempel:

```php
namespace App\Transformers;

use League\Fractal\TransformerAbstract;
use Illuminate\Support\Collection;

class CustomAttributeTransformer extends TransformerAbstract
{
    protected $availableIncludes = [];
    protected $defaultIncludes = [];

    public function __construct($signsField, $jsonSignsField = null)
    {
        $this->signsField = $signsField;
        $this->jsonSignsField = $jsonSignsField;
    }

    public function transform(Collection $collection)
    {
        // Initialize array for additional information.
        $additionalInformation = [];

        // Source - this comes from values sent to this transformer.
        foreach ($collection->{$this->signsField} ?: [] as $value) {
            if (is_array($value)) {
                // If value is an array, serialize it.
                foreach ($value as &$item) {
                    if (isset($item['custom_attr'])) {
                        // Serialize custom attribute data.
                        ...
                    }
                }
            } else {
                // Add non-array values directly.
                ...
            }
        }

        ...

        return [
            'current' => ...,
            'additional_information' => ...,
            'source' => ...,
        ];
    }

    private function flatten(array $values)
    {
      return Arr::flatten($values);
  }
}
```

## Steg 8: Definiera OrderItemCustomAttributes

Skapa en `OrderItemCustomAttributes.php`-fil som definierar anpassade attribut för orderobjektet. Exempel:

```php
namespace Magento\AepCustomAttributes\Model\Provider;

use Magento\Framework\Serialize\Serializer\Json;

class OrderItemCustomAttribute
{
    private Json $jsonSerializer;
    private string $usingField;

    public function __construct(Json $jsonSerializer, string $usingField)
    {
        $this->jsonSerializer = $jsonSerializer;
        $this->usingField = $usingField;
    }

    public function get(array $values): array
    {
        $output = [];
        $values = $this->flatten($values);

        foreach ($values as $row) {
            $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
            $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

            $attrLabel = implode(',', ['label1', 'label2']);
            $unserializedData['custom_attr1'] = $attrLabel;

            $additionalInformation = [];
            foreach ($unserializedData as $name => $value) {
                $additionalInformation[] = [
                    'name' => $name,
                    'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                ];
            }

            foreach ($additionalInformation as $information) {
                $output[] = [
                    'additionalInformation' => $information,
                    $this->usingField => $row[$this->usingField],
                ];
            }
        }

        return $output;
    }

    private function flatten(array $values): array
    {
        return array_merge([], ...array_values($values));
    }
}
```

## Steg 9: Skapa en katalog för productContext-filen

Skapa en katalog med namnet `Plugin/Module` på samma nivå som katalogen `etc`. Den här katalogen innehåller filen `ProductContext.php`.

## Steg 10: Definiera klassen ProductContext

Skapa en fil med namnet `ProductContext.php` som definierar klassen `ProductContext`. Exempel:

```php
namespace Magento\Catalog\Model\Product;

use Magento\Framework\App\ResourceConnection;
use Magento\Quote\Api\Data\CartInterface;

class ProductContext
{
    private $brandCache = [];
    private $resourceConnection;

    public function __construct(
        ResourceConnection $resourceConnection
    ) {
        $this->resourceConnection = $resourceConnection;
    }

    public function afterGetProductData($subject, array $result)
    {
        if (isset($result['brand_id'])) {
            if (!isset($this->brandCache[$result['brand_id']])) {
                // @todo load brand label by brand id.
                $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
            }
            $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
        }

        return $result;
    }
}
```

## Steg 1: Registrera modulen

Skapa en `registration.php`-fil som registrerar modulen på samma nivå som katalogen `etc`. Exempel:

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## Steg 12: Utöka ditt befintliga XDM-schema

Om du vill vara säker på att de nya attributen för anpassad ordning kan importeras av ditt [!DNL Commerce]-schema i Experience Platform, måste du utöka schemat så att det inkluderar dessa anpassade fält.

Mer information om hur du utökar ett befintligt XDM-schema så att det inkluderar dessa anpassade fält finns i artikeln [Skapa och redigera scheman i användargränssnittet](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) i Experience Platform-dokumentationen. Fältet Klient-ID genereras dynamiskt, men fältstrukturen ska likna exemplet i Experience Platform-dokumentationen.

>[!IMPORTANT]
>
>Anpassade XDM-attribut måste matcha de attribut som skickas från [!DNL Commerce].

Lägg till ett fält för ordernivå i `commerce.order`:

![Beställningsnivå](assets/order-level.png)

Lägg till fält för orderobjektnivå i `productListItems`:

![Beställningsobjektnivå](assets/order-item-level.png)

## Steg 12: Bekräfta att data hämtas

Visa fliken [Dataanpassning](connect-data.md#data-customization) i Admin för att bekräfta att anpassade attributdata hämtas och skickas till Experience Platform.

### Felsökning

Om meddelandet `No custom order attributes found.` visas på fliken **[!UICONTROL Data Customization]** bekräftar du följande:

1. Du har slutfört kraven för att aktivera [Data Connector-tillägget](overview.md#prerequisites).
1. Du har konfigurerat [anpassade orderattribut](#add-custom-order-attributes).
1. Minst en orderhändelse har genererats.
