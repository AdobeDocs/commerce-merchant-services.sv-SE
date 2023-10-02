---
title: SaaS - prisindexering
description: Förbättra prestanda med prisindexering i SaaS
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: b7989b416f852d2c7164d21e8f0598373662b760
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# SaaS - prisindexering

SaaS-prisindexering snabbar upp tiden det tar för prisändringar att återspeglas [Commerce Services](../landing/saas.md) efter att ha lämnats in. På så sätt kan handlare med stora, komplexa kataloger eller med flera webbplatser eller kundgrupper kontinuerligt bearbeta prisändringar.
Om du har ett headless storefront eller använder [catalog-adapter](./catalog-adapter.md) kan man avaktivera Adobe Commerce Core price indexer.

Datorintensiva processer som indexering och prisberäkning har flyttats från Commerce Core till Adobe Cloud-infrastruktur. På så sätt kan handlarna snabbt skala upp resurserna för att öka prisindexeringstiden och spegla dessa förändringar snabbare.

Core indexing data flow to SaaS services looks like:

![Standarddataflöde](assets/old_way.png)

Med prisindexering i SaaS blir flödet:

![Dataflöde för prisindexering i SaaS](assets/new_way.png)

Alla handlare kan dra nytta av dessa förbättringar, men de som kommer att se de största fördelarna är kunder med:

* Konstanta prisförändringar: Marknadsförare som behöver ändra sina priser upprepade gånger för att uppnå strategiska mål, som frekventa kampanjer, säsongsrabatter eller lagerpålägg.
* Flera webbplatser och/eller kundgrupper: Handlare med delade produktkataloger på flera webbplatser (domäner/varumärken) och/eller kundgrupper.
* Ett stort antal unika priser på olika webbplatser eller kundgrupper: handlare med omfattande gemensamma produktkataloger som innehåller unika priser på olika webbplatser eller kundgrupper, till exempel B2B-handlare med priser som förhandlats fram i förväg, varumärken med olika prisstrategier.

SaaS prisindexering är kostnadsfritt för kunder som använder Adobe Commerce och stöder prisberäkning för alla inbyggda Adobe Commerce-produkttyper.

Den här miniguiden beskriver hur prisindexering i SaaS fungerar och hur du aktiverar den.

## Krav

* Adobe Commerce 2.4.4+
* Minst en av följande Commerce Services med den senaste versionen av Adobe Commerce-tillägget:

   * [Katalogtjänst](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations](../product-recommendations/guide-overview.md)

Luma- och Adobe Commerce Core GraphQL-användare kan installera [`catalog-adapter`](catalog-adapter.md) tillägg som är kompatibelt med Luma och Core GraphQl och som inaktiverar Adobe Commerce produktprisindexerare.

## Användning

Synkronisera de nya flödena när du har uppgraderat din Adobe Commerce-instans med prisindexeringsstöd för SaaS:

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-bundle-product-override-data-exporter
magento/module-gift-card-product-data-exporter
```

## Priser för anpassade produkttyper

Prisberäkningar stöds för anpassade produkttyper som baspris, specialpris, grupppris, katalogregelpris osv.

Om du har en anpassad produkttyp som använder en viss formel för att beräkna det slutliga priset kan du utöka beteendet för produktprisflödet.

## Användning

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

Nya feeds ska synkroniseras manuellt med `resync` [CLI, kommando](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Annars uppdateras data i standardsynkroniseringsprocessen. Hämta mer information om [Katalogsynkronisering](../landing/catalog-sync.md) -processen.

## Användningsscenarier

### Luma utan tilläggsberoenden

* En Luma- eller Adobe Commerce Core GraphQL-handlare som har en obligatorisk tjänst installerad (Live Search, Product Recommendations, Catalog Service)
* Inga tillägg från tredje part som är beroende av PHP:s huvudprisindexerare
* Sälja enkla, konfigurerbara, grupperade, virtuella och paketerade dynamiska produkter

1. Aktivera nya feeds.
1. Installera katalogadaptern.

### Luma och Adobe Commerce Core GraphQl med PHP Core price indexer-beroenden

* En Luma- eller Adobe Commerce Core GraphQL-handlare som har en tjänst som stöds installerad (Live Search, Product Recommendations, Catalog Service)
* Med ett tillägg från tredje part som är beroende av PHP:s huvudprisindexerare
* Sälja enkla, konfigurerbara, grupperade, virtuella och paketerade dynamiska produkter

1. Aktivera de nya flödena
1. Installera katalogadaptern.
1. Återaktivera PHP:s huvudprisindexerare.
1. Använd nya feeds och Luma-kompatibilitetskoden i `catalog-adapter` -modul.

### Huvudlös handlare

* En återförsäljare utan huvud som har en tjänst som stöds installerad (Live Search, Product Recommendations, Catalog Service)
* Inget beroende av PHP:s basprisindexerare
* Sälja enkla, konfigurerbara, grupperade, virtuella och paketerade dynamiska produkter

1. Aktivera nya feeds
1. Installera katalogadaptern, vilket inaktiverar PHP-kärnprisindexeraren.

## Anpassade priser

Prisindexeraren för SaaS stöder anpassade funktioner för produkttypspris som finns i Adobe Commerce, till exempel specialpris, grupppris och katalogregelpris.

Det finns till exempel en anpassad produkttyp  `custom_type` och en produkt med SKU:n&quot;Custom Type Product&quot;.

Som standard skickar tillägget Commerce Data Export följande prisfeed till prisindexeraren:

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

Om&quot;Anpassad produkttyp&quot; använder en unik formel för att beräkna produktpriset kan systemintegratörer åsidosätta pris- och rabattfälten genom att utöka tillägget för Commerce Data Export.

1. Skapa ett plugin-program på `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` klassen.

`di.xml` fil:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
    </type>
</config>
```

1. Skapa en metod med den anpassade formeln:

```php
class UpdatePriceFromFeed
{
    /**
    * @param ProductPrice $subject
    * @param array $result
    * @param array $values
    *
    * @return array
    */
    public function afterGet(ProductPrice $subject, array $result, array $values) : array
    {
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
