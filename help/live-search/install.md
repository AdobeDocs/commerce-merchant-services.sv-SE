---
title: "Installera [!DNL Live Search]"
description: "Lär dig installera, uppdatera och avinstallera [!DNL Live Search] från Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 8a98e069cd9ec3d2c4fec33485e5c8186d94518f
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 0%

---

# Installera [!DNL Live Search]

[!DNL Live Search] installeras som ett tillägg från Adobe Marketplace. Efter [!DNL Live Search] modulen (med katalogmoduler som beroenden) är installerad och konfigurerad, [!DNL Commerce] börjar dela söknings- och katalogdata med SaaS-tjänster. I det här skedet *Administratör* -användare kan skapa, anpassa och hantera regler för sökning, synonymer och varuexponering.

Det här avsnittet innehåller anvisningar om hur du gör följande:

* Installera [!DNL Live Search] (Metoder 1 och 2)
* [Uppdatera [!DNL Live Search]](#update)
* [Avinstallera [!DNL Live Search]](#uninstall)

## Innan du börjar {#before-you-begin}

Gör följande:

1. Bekräfta att [cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) och [indexerare](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) är igång.

1. Välj den startmetod som uppfyller dina krav och följ instruktionerna.

   * [Metod 1](#method-1): Installera utan [!DNL OpenSearch]
   * [Metod 2](#method-2): Installera med [!DNL OpenSearch] (Inga driftavbrott)

>[!IMPORTANT]
>
>På grund av att supporten för Elasticsearch 7 upphör i augusti 2023 rekommenderas att alla Adobe Commerce-kunder migrerar till sökmotorn OpenSearch 2.x. Mer information om hur du migrerar sökmotorn under uppgraderingen finns i [Migrerar till OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) i _Uppgraderingshandbok_.

## Metod 1: Installera utan OpenSearch {#method-1}

Den här startmetoden rekommenderas vid installation [!DNL Live Search] till:

* Nytt [!DNL Commerce] installation
* Mellanlagringsmiljö

I det här scenariot avbryts storefront-åtgärder medan [!DNL Live Search] indexerar alla produkter i katalogen. Under installationen [!DNL Live Search] är aktiverade och [!DNL OpenSearch] moduler är inaktiverade.

1. Installera Adobe Commerce 2.4.4+ utan [!DNL Live Search].

1. Ladda ned `live-search` paketet, kör följande från kommandoraden:

   ```bash
   composer require magento/live-search
   ```

1. Kör följande kommandon för att inaktivera [!DNL OpenSearch] och tillhörande moduler, samt installera [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > När data indexeras och synkroniseras är söknings- och kategoribläddringsåtgärderna inte tillgängliga i butiken. Beroende på storleken på katalogen kan processen ta minst en timme från tidpunkten `cron` kör för att synkronisera data till [!DNL Live Search] tjänster.

1. Verifiera att följande [indexerare](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) är inställda på&quot;Uppdatera enligt schema&quot;:

   * Produktfeed
   * Produktvariantfeed
   * Matning för katalogattribut
   * Produktprisfeed
   * Omfång Dataflöde för webbplats
   * Omfång Datautflöde för kundgrupper
   * Kategoriflöde
   * Kategoribehörighetsfeed

1. Konfigurera [API-nycklar](#configure-api-keys) och verifiera att katalogdata [synkroniserad](#synchronize-catalog-data) med [!DNL Live Search] tjänster.

1. Om du vill göra ansikten tillgängliga som filter i butiken lägger du till [facets](facets-add.md) du behöver, enligt [krav på facettering](facets.md).

   Du bör kunna lägga till ansikten efter `cron` kör attributfeeds och exporterar attributmetadata.

1. Kör följande kommando i den här ordningen:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. [Verifiera](#verify-export) att data exporterades.

1. [Testa](#test-the-connection) anslutningen från butiken.

## Metod 2: Installera med OpenSearch {#method-2}

Den här startmetoden rekommenderas vid installation [!DNL Live Search] till:

* En befintlig produktion [!DNL Commerce] installation

I detta scenario [!DNL OpenSearch] hanterar temporärt sökförfrågningar från butiken medan [!DNL Live Search] indexerar alla produkter i bakgrunden utan att störa den normala butiksverksamheten. [!DNL OpenSearch] är inaktiverat och [!DNL Live Search] aktiveras när alla katalogdata har indexerats och synkroniserats.

1. Ladda ned `live-search` paketet, kör följande från kommandoraden:

   ```bash
   composer require magento/live-search
   ```

1. Kör följande kommando för att tillfälligt inaktivera [!DNL Live Search] moduler som används för sökresultat i butiker.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] fortsätter att hantera sökbegäranden från butiken medan [!DNL Live Search] synkroniserar katalogdata och indexerar produkter i bakgrunden.

1. Verifiera att följande [indexerare](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) är inställda på&quot;Uppdatera enligt schema&quot;:

   * Produktfeed
   * Produktvariantfeed
   * Matning för katalogattribut
   * Produktprisfeed
   * Omfattningar av webbplatsens dataflöde
   * Omfattningar av kundgruppsdatafeed

1. Konfigurera [API-nycklar](#configure-api-keys) och verifiera att katalogdata [synkroniserad](#synchronize-catalog-data) med [!DNL Live Search] tjänster.

1. Om du vill göra ansikten tillgängliga som filter i butiken lägger du till [facets](facets-add.md) du behöver, enligt [krav på facettering](facets.md).

   Du bör kunna lägga till ansikten efter `cron` kör produkt- och attributfeeds och exporterar attributmetadata till [!DNL Live Search] tjänster.

1. Kör följande kommando i den här ordningen:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. När synkroniseringen är klar använder du [GraphQL playground](https://developer.adobe.com/commerce/services/graphql/live-search/) med standardfrågan för att verifiera följande:

   * Det returnerade antalet produkter är nästan vad du förväntar dig för butiksvyn.
   * Fasett(n) returneras.

1. Kör följande kommandon för att aktivera [!DNL Live Search] moduler, inaktivera [!DNL OpenSearch]och köra `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Testa](#test-the-connection) anslutningen från butiken.

## Konfigurera API-nycklar {#configure-api-keys}

Adobe Commerce API-nyckeln och den tillhörande privata nyckeln krävs för att ansluta [!DNL Live Search] till en installation av Adobe Commerce. API-nyckeln genereras och underhålls i kontot för [!DNL Commerce] som kan dela det med utvecklaren eller SI. Utvecklaren kan sedan skapa och hantera SaaS Data Spaces för licenshavarens räkning.  Om du redan har en uppsättning API-nycklar behöver du inte generera om dem.

### Licensinnehavare för Adobe Commerce

Om du vill generera en API-nyckel och en privat nyckel ska du läsa [Commerce Services Connector](../landing/saas.md).

### Adobe Commerce-utvecklare eller SI

Utvecklaren eller SI konfigurerar SaaS-datautrymmet enligt beskrivningen i *Commerce Services* i konfigurationen. I *Administratör*, blir Commerce tjänster tillgängliga i *Konfiguration* sidofältet när en SaaS-modul är installerad.

## Synkronisera katalogdata {#synchronize-catalog-data}

[!DNL Live Search] kräver synkroniserade produktdata för sökåtgärder och synkroniserade attributdata för att konfigurera facets. Den inledande synkroniseringen mellan produktkatalogen och katalogtjänsten börjar när [!DNL Live Search] är först ansluten. Beroende på installationsmetod och storlek för katalogen kan det ta upp till 30 minuter innan data exporteras och indexeras av [!DNL Live Search]. Listan med data som synkroniseras och delas med katalogtjänsten finns i schemat, som definieras i:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

Använd [Instrumentpanel för datahantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) för att övervaka synkroniseringsstatusen för produktdata som överförs från Commerce-databasen till Commerce SaaS-tjänster.

### Verifiera export {#verify-export}

Så här verifierar du att katalogdata har exporterats från din Adobe Commerce-instans och synkroniserats för [!DNL Live Search]söker du efter poster i följande tabeller:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Mer hjälp finns i [[!DNL Live Search] katalogen inte synkroniserad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) i supportkunskapsbasen.

### Framtida produktuppdateringar

Efter den första synkroniseringen kan det ta upp till 15 minuter innan ytterligare produktuppdateringar blir tillgängliga för butikssökning. Om du vill veta mer går du till [Indexering - direktuppspelande produktuppdateringar](indexing.md).

## Testa anslutningen {#test-connection}

Kontrollera följande i butiken:

* The [!UICONTROL Search] returnerar resultaten korrekt
* Kategoribläddring returnerar resultat korrekt
* Ansikten finns som filter på sökresultatsidor

Om allt fungerar som det ska, grattis! [!DNL Live Search] är installerat, anslutet och klart att användas.

Om du stöter på problem i butiken ska du kontrollera `var/log/system.log` fil för API-kommunikationsfel eller fel på tjänstsidan.

Om du vill tillåta Live Search via en brandvägg lägger du till `commerce.adobe.io` till tillåtelselista.

## Kontrollerar den installerade versionen

Innan du uppdaterar Live Search kör du följande kommandorad för att kontrollera vilken version av Live Search som är installerad:

```bash
composer show magento/module-live-search | grep version
```

## Uppdaterar [!DNL Live Search] {#update}

Uppdatera [!DNL Live Search]kör du följande från kommandoraden:

```bash
composer update magento/live-search --with-dependencies
```

Om du vill uppdatera till en större version, som 3.1.1 till 4.0.0, redigerar du projektets rot [!DNL Composer] `.json` på följande sätt:

1. Om din nuvarande installation `magento/live-search` versionen är `3.1.1` eller tidigare, och du uppgraderar till version `4.0.0` eller senare kör du följande kommando före uppgraderingen:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Mer information om den installerade `magento/live-search` version, kör följande kommando:

   ```bash
   composer show magento/live-search
   ```

1. Öppna roten `composer.json` fil och sök efter `magento/live-search`.

1. I `require` uppdaterar du versionsnumret enligt följande:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **Spara** `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Avinstallerar [!DNL Live Search] {#uninstall}

Avinstallera [!DNL Live Search], se [Avinstallera moduler](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] paket {#packages}

| Paket | Beskrivning |
|--- |--- |
| `module-live-search` | Gör det möjligt för handlare att konfigurera sina sökinställningar för ansikten, synonymer, frågeregler och så vidare, och ger åtkomst till en skrivskyddad GraphQL-spelningsmiljö för att testa frågor från *Administratör*. |
| `module-live-search-adapter` | Slussar sökförfrågningar från butiken till [!DNL Live Search] och återger resultaten i butiken. <br />- Kategoribläddring - dirigera begäranden från butiken [navigering överst](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) till söktjänsten.<br />- Global sökning - dirigera begäranden från [snabbsökning](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) i det övre högra hörnet av butiken längst upp till vänster [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | En sökfunktion som ersätter standardsnabbsökningen och returnerar data och miniatyrbilder av de översta sökresultaten. |

## [!DNL Live Search] beroenden {#dependencies}

Följande [!DNL Live Search] beroenden hämtas av [!DNL Composer].

* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`
