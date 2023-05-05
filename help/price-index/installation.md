---
title: SaaS - prisindexeringsinstallation
description: Installerar prisindexering för SaaS
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# SaaS - prisindexeringsinstallation

För att konfigurera prisindexering för SaaS måste du installera nya moduler och köra CLI-kommandon. Administratörer behöver kommandoradsåtkomst för att kunna slutföra den här installationen.

## Förutsättningar

* Adobe Commerce 2.4.4+
* Minst en av följande SaaS-tjänster är installerad:

   * [Katalogtjänst](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations](../product-recommendations/guide-overview.md)

## Installera nödvändiga moduler

Beroende på din konfiguration kan installationsprocessen skilja sig något.
Det finns tillägg som lägger till nya feeds och stödkod och det finns ett tillägg som tar bort standardprisflödet.

1. Lägg till följande moduler i `composer.json` fil:

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
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

Luma- och Adobe Commerce Core GraphQL-användare kan installera `catalog-adapter` som ger Luma- och Core GraphQl-kompatibilitet och inaktiverar PHP:s huvudprisindexerare.
Så här använder du `catalog-adapter` modul, [!DNL Live Search] och [!DNL Catalog Service] måste först installeras och konfigureras. Följ [Installera [!DNL Live Search]](../live-search/install.md) och [Installation av katalogtjänst](../catalog-service/installation.md) innan du fortsätter.

Så här konfigurerar du Live Search- och Catalog Adapter: [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) instruktioner.

```bash
composer require adobe-commerce/catalog-adapter
```

PHP Core price indexer kan återaktiveras med följande kommando:

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
