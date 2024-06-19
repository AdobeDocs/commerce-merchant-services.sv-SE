---
title: Katalogkortstillägg
description: Återge priser från Commerce Services med hjälp av katalogadaptern
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Katalogadapter

The `[!DNL Catalog Adapter]` tillägget inaktiverar standardproduktprisindexeraren som ingår i Commerce och använder priser som tillhandahålls av [Katalogtjänst](../catalog-service/overview.md) i stället.

Adaptern är utformad för att fungera med [SaaS-dataexport](../data-export/overview.md) och Adobe Commerce Service. SaaS-dataexporten ansvarar för att skicka in priserna och [!DNL Catalog Adapter] hämtar alla priser från Adobe Commerce Service.

När du aktiverar [!DNL Catalog Adapter]påverkas prisindexering och -åtgärder på följande sätt:

- Prisindexeraren som ingår i Adobe Commerce-programmet är inaktiverad.
- Priserna hanteras med SaaS-dataexporten och [SaaS prisindexerare](price-indexing.md).
- När en kund öppnar en produkt, kategori eller annan sida som visar produktpriser hämtas priserna från Adobe Commerce-tjänsten.
- Priserna skickas till Adobe Commerce-tjänsten genom att data synkroniseras från [SaaS-dataexport](../data-export/overview.md).
- Utcheckningen beräknar om priserna dynamiskt.

Du kan aktivera prisindexering på nytt i Commerce genom att ta bort eller inaktivera tillägget Katalogkort.

## Krav

- Adobe Commerce 2.4.4+
- Ha någon av följande Commerce-tjänster installerade:

   - [Live Search](../live-search/install.md)
   - [Recommendations](../product-recommendations/install-configure.md)
   - [Katalogtjänst](../catalog-service/installation.md)

## Installation

Tillägget Catalog Adapter är ett Composer-metapaket som installerar följande moduler:

- **Inaktivering av prisindexerare**-Den här modulen inaktiverar prisindex i Commerce så att priserna levereras via prisindexering i SaaS. Produktprisindexeraren i Commerce kan inte aktiveras när prisindexeringstillägget SaaS är installerat.
- **Prisleverantör**-Den här modulen anger priser för produkter från Adobe Commerce Service. Den utgör sökfrågan och hämtar priserna för produkterna i klientdelen.
- **Sökadapter för katalogtjänst**-Den här modulen överför priser från Adobe Commerce till en Adobe Commerce-tjänst som svar på en produktsökningsbegäran.

## Installationssteg

>[!BEGINTABS]

>[!TAB Molninfrastruktur]

Använd den här metoden för att installera [!DNL Catalog Adapter] för en Commerce Cloud-instans.

1. På din lokala arbetsstation byter du till projektkatalogen för ditt Adobe Commerce i molninfrastrukturprojekt.

   >[!NOTE]
   >
   >Mer information om hur du hanterar Commerce projektmiljöer lokalt finns i [Hantera filialer med CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) i _Användarhandbok för infrastruktur i Adobe Commerce om molnet_.

1. Kolla in miljögrenen för att uppdatera med Adobe Commerce Cloud CLI.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Lägg till katalogadaptermodulen.

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Uppdatera paketberoenden.

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. Verkställ och push-kodsändringar för `composer.json` och `composer.lock` filer.

1. Lägg till, implementera och skicka kodändringar för `composer.json` och `composer.lock` filer till molnmiljön.

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   När uppdateringarna skickas till molnmiljön initieras [Commerce molndistributionsprocess](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) för att tillämpa ändringarna. Kontrollera distributionsstatusen på [distributionslogg](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB Lokalt]

Använd den här metoden för att installera [!DNL Catalog Adapter] för en lokal instans.

1. Lägg till katalogadaptern i projektet med Composer:

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Uppgradera Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >I vissa fall, särskilt när du distribuerar till produktion, kanske du vill undvika att rensa kompilerad kod eftersom det kan ta en stund. Se till att du säkerhetskopierar systemet innan du gör några ändringar.

>[!ENDTABS]


## Återaktivera Adobe Commerce produktprisindexerare

Om du har program från tredje part som är beroende av Adobe Commerce standardproduktprisindexerare kan du aktivera det igen med följande kommandon:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## Inaktivera produktprisindexeraren för scenariot Headless Storefront

Om du har en headless Commerce-instans kan du behöva inaktivera Adobe Commerce produktprisindexerare för att minska belastningen på din Adobe Commerce-instans. Du kan slutföra den här uppgiften genom att installera `magento/module-price-indexer-disabler` modul:

```bash
composer require magento/module-price-indexer-disabler
```

## Användningsscenarier

Följande är några vanliga `[!DNL Catalog Adapter]` scenarier.

### Inga beroenden till Adobe Commerce produktprisindexerare

- Du är återförsäljare av Luma- eller Adobe Commerce Core GraphQL som har en obligatorisk tjänst installerad (Live Search, Product Recommendations, Catalog Service)
- Inga integreringar med tillägg från tredje part som kräver Adobe Commerce produktprisindexerare

1. Installera [!DNL Catalog Adapter].

### Med beroenden till Adobe Commerce produktprisindexerare

- Du är återförsäljare av Luma- eller Adobe Commerce Core GraphQL-produkter och har en tjänst som stöds installerad (Live Search, Product Recommendations, Catalog Service)
- Du använder ett tillägg från en annan leverantör som är beroende av Adobe Commerce produktprisindexerare

1. Installera [!DNL Catalog Adapter].
1. Aktivera Adobe Commerce standardprisindexerare.

### Headless Commerce-instanser

- En handlare med en headless Commerce-instans med de nödvändiga tjänsterna installerade (Live Search, Product Recommendations, Catalog Service)
- Ingen användning av Adobe Commerce standardproduktprisindexerare

1. Installera `magento/module-price-indexer-disabler` från [!DNL Catalog Adapter] paket.

