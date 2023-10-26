---
title: Installation av prisindexeringshandbok för SaaS
description: Installerar prisindexering för SaaS för en äldre version
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: 4577111a-64a4-4e20-b970-3abfa6758247
role: Admin, Developer
source-git-commit: 3809d27fc3689519e4a162aa52f481d254aec656
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Installation av prisindexeringshandbok för SaaS

SaaS-prisindexering är tillgängligt direkt för support [senaste versionen](index.md#Requirements) för Commerce Services.
Om du inte har den senaste versionen och vill aktivera prisindexering för SaaS för din Adobe Commerce-instans använder du den här miniguiden.

## Förutsättningar

* Adobe Commerce 2.4.4+
* Minst en av följande SaaS-tjänster är installerad:

   * [Katalogtjänst](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations](../product-recommendations/guide-overview.md)

## Installera nödvändiga moduler

Beroende på din konfiguration kan installationsprocessen skilja sig något.
Det finns tillägg som lägger till de nya flödena och stödkoden.

1. Lägg till följande moduler i `composer.json` fil:

   ```json
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
   ```

1. Kör uppgraderingskommandot:

   ```bash
   bin/magento setup:upgrade
   ```

Efter uppgraderingen finns tre nya flöden:

* `prices` - ansvarar för att leverera prisdata till tjänsten
* `scopesCustomerGroup` - ansvarar för att leverera kundgrupper till tjänsten
* `scopesWebsite` - ansvarar för att leverera webbplatser, butiksgrupper och butiksvyer till tjänsten


1. Konfigurera de nya feeds som ska ställas in på läget Uppdatera enligt schema:

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. Indexera om de nya flödena:

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

Kör indexerarna ovan efter behov manuellt. Annars uppdateras data i standardsynkroniseringsprocessen. Läs mer om [Katalogsynkronisering](../landing/catalog-sync.md) service.


Om du vill konfigurera Live Search och Catalog Adapter följer du [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) instruktioner.

## Caveats

Före `103.0.0` version, stöd för prisindexering i SaaS av typerna Simple, Grouped, Virtual, Configurable och Bundle Dynamic.
Det finns stöd för nedladdningsbara produkter, presentkort och paket med fasta produkter från `magento/module-saas-price:103.0.0` version och tillgänglig direkt för de Commerce Services som stöds.

Nya feeds ska synkroniseras manuellt med `resync` [CLI, kommando](../landing/catalog-sync.md#resynccmdline). Annars uppdateras data i standardsynkroniseringsprocessen. Hämta mer information om [Katalogsynkronisering](../landing/catalog-sync.md) -processen.
