---
title: Katalogkortstillägg
description: Använda katalogadaptern för att återge priser från Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: 6b578e7113c278a05a64f2db5e032bccc4a9580a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# Katalogadapter

The `Catalog Adapter` tillägget inaktiverar Adobe Commerce standardproduktprisindexerare och använder i stället priser från [Katalogtjänst](../catalog-service/overview.md).
Adobe Commerce produktprisindexerare är inaktiverad och kan inte aktiveras med dessa tilläggsmoduler installerade. Det är bara genom att ta bort eller inaktivera det här tillägget som produktprisindexeraren kan återaktiveras.

## Krav

* Adobe Commerce 2.4.4+
* En av följande Commerce Services har installerats:

   * [Katalogtjänst](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)

## Installation

Använd `catalog-adapter` modul, [!DNL Live Search] och [!DNL Catalog Service] måste först installeras och konfigureras. Följ [Installera [!DNL Live Search]](../live-search/install.md) och [Installation av katalogtjänst](../catalog-service/installation.md) innan du fortsätter.

Kör följande kommando när dessa tjänster har installerats:

```bash
composer require adobe-commerce/catalog-adapter
```

## Aktivera Adobe Commerce produktprisindexerare

Om du har program från tredje part som är beroende av Adobe Commerce standardproduktprisindexerare kan den återaktiveras med följande kommandon:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# reindex Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## Inaktivera produktprisindexeraren för scenariot Headless Storefront

Om du har en Headless Commerce-instans kan du behöva inaktivera Adobe Commerce Product Price indexer för att minska belastningen på din Adobe Commerce-instans.
Detta görs genom att installera `magento/module-price-indexer-disabler` modul:

```bash
composer require magento/module-price-indexer-disabler
```

## Användningsscenarier

Följande är några vanliga `Catalog Adapter` scenarier.

### Inga beroenden till Adobe Commerce produktprisindexerare

* Du är återförsäljare av Luma- eller Adobe Commerce Core GraphQL som har en obligatorisk tjänst installerad (Live Search, Product Recommendations, Catalog Service)
* Inga tillägg från tredje part som är beroende av Adobe Commerce produktprisindexerare

1. Installera katalogadaptern.

### Med beroenden till Adobe Commerce produktprisindexerare

* Du är återförsäljare av Luma- eller Adobe Commerce Core GraphQL-produkter och har en tjänst som stöds installerad (Live Search, Product Recommendations, Catalog Service)
* Du använder ett tillägg från en annan leverantör som är beroende av Adobe Commerce produktprisindexerare

1. Installera katalogadaptern.
1. Aktivera Adobe Commerce standardindexerare för produktpriser igen.

### Headless Commerce-instanser

* En handlare med en Headless Commerce-instans med de nödvändiga tjänsterna installerade (Live Search, Product Recommendations, Catalog Service)
* Ingen användning av Adobe Commerce standardproduktprisindexerare

1. Installera&quot;price disabler&quot; från katalogadapterpaketet
