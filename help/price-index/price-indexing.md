---
title: SaaS - prisindexering
description: Förbättra prestanda med prisindexering i SaaS
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# SaaS - prisindexering

SaaS prisindexering förbättrar webbplatsens prestanda genom att flytta tunga beräkningsprocesser som indexering och prisberäkning från Commerce till Adobe Cloud-infrastrukturen. Med den här metoden kan handlarna snabbt skala upp resurser för att öka prisindexeringstiden för att återspegla prisförändringar snabbare när de skickar data till butiken och anslutna Commerce-tjänster.

I följande diagram visas indexeringsdataflödet till SaaS-tjänster när Commerce använder den [prisindexeringsprocess](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) som ingår i Commerce-programmet:

![Standarddataflöde](assets/old_way.png)

När prisindexering för SaaS är aktiverat ändras dataflödet. Prisindexering utförs med [Commerce SaaS-dataexport](../data-export/data-synchronization.md).

![Dataflöde för prisindexering i SaaS](assets/new_way.png)

Alla handlare kan dra nytta av att använda prisindexering i SaaS, men handlare med projekt med följande egenskaper kan uppnå de största fördelarna:

* **Konstanta prisändringar**-marknadsförare som kräver upprepade prisändringar för att uppnå strategiska mål, som frekventa kampanjer, säsongsrabatter eller lagermarkeringar.
* **Flera webbplatser och/eller kundgrupper**-Merchants med delade produktkataloger på flera webbplatser (domäner/varumärken) och/eller kundgrupper.
* **Många unika priser på webbplatser eller kundgrupper**-Merchants med omfattande delade produktkataloger som innehåller unika priser på olika webbplatser eller kundgrupper. Exempel är B2B-handlare som har priser som förhandlats fram i förväg eller varumärken med olika prisstrategier.

## Använd prisindexering för SaaS

Prisindexering för SaaS aktiveras automatiskt när du installerar Adobe Commerce Services. Det stöder prisberäkning för alla inbyggda Adobe Commerce-produkttyper.

### Krav

* Adobe Commerce 2.4.4+

### Förutsättningar

* En av följande Commerce-tjänster måste installeras med den senaste versionen av Commerce-tillägget:

   * [Katalogtjänst](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)
   * [Recommendations](../product-recommendations/guide-overview.md)


>[!NOTE]
>
>Om det behövs kan standardprisindexeraren i Commerce inaktiveras med [katalogadaptern](catalog-adapter.md).

## Synkronisera priser med prisindexering för SaaS

När du har aktiverat prisindexering för SaaS för Adobe Commerce kan du uppdatera priserna på Storefront och i Commerce Services genom att synkronisera de nya flödena:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### Priser för anpassade produkttyper

Prisberäkningar stöds för anpassade produkttyper som baspris, specialpris, grupppris, katalogregelpris och så vidare.

Om du har en anpassad produkttyp som använder en viss formel för att beräkna det slutliga priset kan du utöka beteendet för produktprisflödet.

1. Skapa ett plugin-program för klassen `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice`.

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

