---
title: Installera Live Search
description: Lär dig hur du installerar, uppdaterar och avinstallerar Live Search från Adobe Commerce.
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 0%

---

# Installera [!DNL Live Search]

[!DNL Live Search] är en uppsättning fristående [paket](#live-search-packages) som ersätter standardsökfunktionerna i Magento Open Source och Adobe Commerce. The [!DNL Live Search] -modulen installeras från serverns kommandorad och ansluts till din Adobe Commerce-installation som en [service](https://docs.magento.com/user-guide/system/saas.html). När processen är klar [!DNL Live Search] visas på *Marknadsföring* meny under *SEO &amp; Search* i [!DNL Commerce] Admin.

På Adobe Commerce-sidan finns en värdserver för sökadministratören, synkronisering av katalogdata och körning av frågetjänsten.

![Arkitektur för Live Search](assets/architecture-diagram.svg)

Efter [!DNL Live Search] modulen (med katalogmoduler som beroenden) installeras och konfigureras, [!DNL Commerce] börjar dela söknings- och katalogdata med SaaS-tjänster. Nu kan administratörsanvändare konfigurera, anpassa och hantera regler för sökning, synonymer och försäljning.

Det här avsnittet innehåller anvisningar om hur du gör följande:

* [Installera [!DNL Live Search]](#before-you-begin) (Metoder 1 och 2)
* [Uppdatera [!DNL Live Search]](#update)
* [Avinstallera [!DNL Live Search]](#uninstall)

## Krav {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3/7.4
* [!DNL Composer]

### Plattformar som stöds

* Adobe Commerce on prem (EE): 2.4.x
* Adobe Commerce on Cloud (ECE): 2.4.x

## Gränser och tröskelvärden

För närvarande har sökning/kategori-API:t för Live-sökning följande begränsningar och statiska gränser som stöds:

### Indexering

* Indexerar upp till 300 produktattribut per butiksvy
* Indexerar endast produkter från Adobe Commerce-databasen
* Indexerar inte CMS-sidor

### Funktionalitet

* Storefront [Avancerad (formulärsökning)](https://docs.magento.com/user-guide/catalog/search-advanced.html) modul
* [Kundgrupper](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Anpassade prisgrupper](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Flera lagerplatser används av [MCOM](https://docs.magento.com/user-guide/mcom.html) eller andra OMS-tillägg
* [Integrerade B2B-funktioner](https://business.adobe.com/products/magento/b2b-ecommerce.html)

### Frågor

* Livesökning har inte tillgång till hela taxonomin för kategoriträdet, vilket gör att vissa scenarier för navigering i flera lager inte är tillgängliga.
* Live Search använder en unik GraphQL-slutpunkt för frågor för att stödja funktioner som intelligent Faceeting och sökning-som-du-typ. Även om den liknar [Magento GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)finns det några skillnader och vissa fält kanske inte är helt kompatibla just nu.

### Progressive Web Application (PWA)

* Live Search stöder inte [PWA](https://developer.adobe.com/commerce/pwa-studio/) just nu.

## Innan du börjar {#before-you-begin}

Gör följande:

1. Bekräfta att [cron-jobb](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) och [indexerare](https://docs.magento.com/user-guide/system/index-management.html) är igång.

1. Välj den startmetod som uppfyller dina krav och följ instruktionerna.

   * [Metod 1](#method-1): Installera utan [!DNL Elasticsearch]
   * [Metod 2](#method-2): Installera med [!DNL Elasticsearch] (Inga driftavbrott)

   >[!TIP]
   >
   >Om du vill ange instruktioner på kommandoraden för du muspekaren över kodrutans högra hörn och klickar på knappen [!UICONTROL **Kopiera**] länk. Klistra sedan in den på kommandoraden. Om du inte har någon erfarenhet av att arbeta via kommandoraden ber du systemintegratören eller utvecklaren om hjälp.

## Metod 1: Installera utan Elasticsearch {#method-1}

Den här startmetoden rekommenderas vid installation [!DNL Live Search] till

* Nytt [!DNL Commerce] installation
* Mellanlagringsmiljö

I det här scenariot avbryts storefront-åtgärder medan [!DNL Live Search] indexerar alla produkter i katalogen. Under installationen [!DNL Live Search] är aktiverade och [!DNL Elasticsearch] moduler är inaktiverade.

1. Installera Adobe Commerce 2.4.x utan [!DNL Live Search].

1. Ladda ned `live-search` paketet, kör följande från kommandoraden:

   ```bash
   composer require magento/DNL live-search
   ```

   Mer information finns i listan över [!DNL Live Search] [beroenden](#dependencies) som hämtas av [!DNL Composer].

1. Kör följande kommandon för att inaktivera [!DNL Elasticsearch] och tillhörande moduler, samt installera [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch  Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > När data indexeras och synkroniseras är söknings- och kategoribläddringsåtgärderna inte tillgängliga i butiken. Beroende på storleken på katalogen kan processen ta minst en timme från tidpunkten `cron` kör för att synkronisera data till [!DNL Live Search] tjänster.

1. Verifiera att följande [indexerare](https://docs.magento.com/user-guide/system/index-management.html) är inställda på `Update by Schedule`:

   * Produktfeed
   * Produktvariantfeed
   * Matning för katalogattribut

1. Konfigurera [API-nycklar](#configure-api-keys) till [synkronisera](#synchronize-catalog-data) katalogdata till [!DNL Live Search] tjänster.

1. Om du vill göra ansikten tillgängliga som filter i butiken lägger du till [facets](https://docs.magento.com/user-guide/live-search/facets-add.html) du behöver, enligt [krav på facettering](https://docs.magento.com/user-guide/live-search/facets.html).

   Du bör kunna lägga till ansikten efter `cron` kör attributfeeds och exporterar attributmetadata.

1. Vänta minst en timme efter `cron` kör för att synkronisera data. Sedan [verifiera](#verify-export) att data exporterades.

1. [Testa](#test-the-connection) anslutningen från butiken.

## Metod 2: Installera med Elasticsearch {#method-2}

Den här startmetoden rekommenderas vid installation [!DNL Live Search] till:

* En befintlig produktion [!DNL Commerce] installation

I detta scenario [!DNL Elasticsearch] hanterar temporärt sökbegäranden från butiken medan [!DNL Live Search] indexerar alla produkter i bakgrunden utan att störa den normala lagerhanteringen. [!DNL Elasticsearch] är inaktiverat och [!DNL Live Search] aktiveras när alla katalogdata har indexerats och synkroniserats.

1. Ladda ned `live-search` paketet, kör följande från kommandoraden:

   ```bash
   composer require magento/live-search
   ```

   Mer information finns i listan över [!DNL Live Search] [beroenden](#live-search-dependencies) som hämtas av [!DNL Composer].

1. Kör följande kommando för att tillfälligt inaktivera [!DNL Live Search] moduler som används för sökresultat i butiker.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] fortsätter att hantera sökbegäranden från butiken medan [!DNL Live Search] synkroniserar katalogdata och indexerar produkter i bakgrunden.

1. Verifiera att följande [indexerare](https://docs.magento.com/user-guide/system/index-management.html) är inställda på `Update by Schedule`:

   * Produktfeed
   * Produktvariantfeed
   * Matning för katalogattribut

1. Konfigurera [API-nycklar](#configure-api-keys) till [synkronisera](#synchronize-catalog-data) katalogdata till [!DNL Live Search] tjänster.

1. Om du vill göra ansikten tillgängliga som filter i butiken lägger du till [facets](https://docs.magento.com/user-guide/live-search/facets-add.html) du behöver, enligt [krav på facettering](https://docs.magento.com/user-guide/live-search/facets.html).

   Du bör kunna lägga till ansikten efter `cron` kör produkt- och attributfeeds och exporterar attributmetadata till [!DNL Live Search] tjänster.

1. Vänta i minst en timme innan data indexeras och synkroniseras. Använd sedan [GraphQL-uppspelning](https://devdocs.magento.com/live-search/graphql-support.html) med standardfrågan för att verifiera följande:

   * Det returnerade antalet produkter ligger nära vad du förväntar dig för butiksvyn
   * Fasett(n) returneras

1. Kör följande kommandon för att inaktivera [!DNL Elasticsearch] moduler, aktivera [!DNL Live Search] och köra `setup`:

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Testa](#test-the-connection) anslutningen från butiken.

## Konfigurera API-nycklar {#configure-api-keys}

Adobe Commerce API-nyckeln och den tillhörande privata nyckeln krävs för att ansluta [!DNL Live Search] till en installation av Adobe Commerce. API-nyckeln genereras och underhålls i kontot för [!DNL Commerce] licensinnehavare som kan dela det med utvecklaren eller SI. Utvecklaren kan sedan skapa och hantera SaaS Data Spaces för licenshavarens räkning.

### Licensinnehavare för Adobe Commerce

Om du vill generera en API-nyckel och en privat nyckel ska du läsa [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html).

### Adobe Commerce utvecklare eller SI

Utvecklaren eller SI konfigurerar SaaS-dataområdet enligt beskrivningen i avsnittet Commerce Services i konfigurationen. Commerce Services blir tillgängligt på sidofältet Admin Configuration när en SaaS-modul installeras.

## Synkronisera katalogdata {#synchronize-catalog-data}

[!DNL Live Search] kräver synkroniserade produktdata för sökåtgärder och synkroniserade attributdata för att konfigurera facets. Den inledande synkroniseringen mellan produktkatalogen och katalogtjänsten börjar när [!DNL Live Search] är först ansluten. Beroende på installationsmetod och katalogstorlek kan det ta upp till åtta timmar för data som ska exporteras och indexeras av [!DNL Live Search]. Listan med data som synkroniseras och delas med katalogtjänsten finns i schemat, som definieras i:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Verifiera export {#verify-export}

Så här verifierar du att katalogdata har exporterats från din Adobe Commerce-instans och synkroniserats för [!DNL Live Search]söker du efter poster i följande tabeller:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Mer hjälp finns i [[!DNL Live Search] katalogen inte synkroniserad](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) i supportkunskapsbasen.

### Framtida produktuppdateringar

Efter den första synkroniseringen kan det ta upp till femton minuter innan ytterligare produktuppdateringar blir tillgängliga för butikssökning. Om du vill veta mer går du till [Direktuppspelande produktuppdateringar](https://devdocs.magento.com/live-search/indexing.html).

## Testa anslutningen {#test-connection}

Kontrollera följande i butiken:

* The [!UICONTROL Search] returnerar resultaten korrekt
* Kategoribläddring returnerar resultat korrekt
* Fasett(er) är tillgängligt som filter på sökresultatsidor

Om allt fungerar som det ska, grattis! [!DNL Live Search] är installerat, anslutet och klart att användas.

Om du stöter på problem i butiken ska du kontrollera `var/log/system.log` fil för API-kommunikationsfel eller fel på tjänstsidan.

## Uppdaterar [!DNL Live Search] {#update}

Uppdatera [!DNL Live Search]kör du följande från kommandoraden:

```bash
composer update magento/live-search --with-dependencies
```

Om du vill uppdatera till en större version, till exempel från 1.0 till 2.0, redigerar du projektets rot [!DNL Composer] `.json` på följande sätt:

1. Öppna roten `composer.json` fil och sök efter `magento/live-search`.

1. I `require` uppdaterar du versionsnumret enligt följande:

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **Spara** `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## Avinstallerar [!DNL Live Search] {#uninstall}

Avinstallera [!DNL Live Search], se [Avinstallera moduler](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).

## [!DNL Live Search] paket {#packages}

| Paket | Beskrivning |
|--- |--- |
| `module-live-search` | Gör det möjligt för handlare att konfigurera sina sökinställningar för ansikten, synonymer, frågeregler osv., och ger åtkomst till en skrivskyddad GraphQL-uppspelning för att testa frågor från administratören. |
| `module-live-search-adapter` | Slussar sökförfrågningar från butiken till [!DNL Live Search] och återger resultaten i butiken. <br />- Kategoribläddring - dirigera begäranden från butiken [navigering överst](https://docs.magento.com/user-guide/catalog/navigation-top.html) till söktjänsten.<br />- Global sökning - dirigera begäranden från [snabbsökning](https://docs.magento.com/user-guide/catalog/search-quick.html) i det övre högra hörnet av butiken till vänster [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | En sökfunktion som ersätter standardsnabbsökningen och returnerar dynamiska produktförslag och miniatyrbilder av de bästa sökresultaten. |

## [!DNL Live Search] beroenden {#dependencies}

Följande [!DNL Live Search] beroenden hämtas av [!DNL Composer]:

| Beroende | Beskrivning |
|--- |--- |
| Exportera moduler | Följande moduler samlar in och synkroniserar katalogdata:<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Krävs för att konfigurera din anslutning till Commerce Services. |
| `module-services-id` | Krävs för att konfigurera din anslutning till Commerce Services. |
