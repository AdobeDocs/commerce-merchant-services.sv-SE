---
title: SaaS - prisindexering
description: Förbättra prestanda med prisindexering i SaaS
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '409'
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

I den här guiden beskrivs hur prisindexering för SaaS fungerar och hur du aktiverar den.

## Krav

* Adobe Commerce 2.4.4+
* Minst en av följande Commerce Services med den senaste versionen av Adobe Commerce-tillägget:

   * [Katalogtjänst](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations](../product-recommendations/guide-overview.md)

Luma- och Adobe Commerce Core GraphQL-användare kan installera [`catalog-adapter`](catalog-adapter.md) tillägg som är kompatibelt med Luma och Core GraphQl och som inaktiverar Adobe Commerce produktprisindexerare.

## Användning

Synkronisera de nya flödena när du har uppgraderat din Adobe Commerce-instans med prisindexeringsstöd för SaaS:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## Priser för anpassade produkttyper

Prisberäkningar stöds för anpassade produkttyper som baspris, specialpris, grupppris, katalogregelpris osv.

Om du har en anpassad produkttyp som använder en viss formel för att beräkna det slutliga priset kan du utöka beteendet för produktprisflödet.

1. Skapa ett plugin-program på `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` klassen.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
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
           // Override the output $result with your data for the corresponding products (see original method for details) 
           return $result;
       }
   }
   ```
