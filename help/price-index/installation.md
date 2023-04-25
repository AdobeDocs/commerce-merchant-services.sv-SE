---
title: SaaS - prisindexeringsinstallation
description: Installerar prisindexering för SaaS
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
source-git-commit: 077be6d893b800b9571a869237501e58accc01e8
workflow-type: tm+mt
source-wordcount: '226'
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
Så här använder du `catalog-adapter` modul, [!DNL Live Search] måste först installeras. Följ [Installera [!DNL Live Search]](../live-search/install.md) innan du fortsätter.

```bash
composer require adobe-commerce/catalog-adapter
```

PHP Core price indexer kan återaktiveras med följande kommando:

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
