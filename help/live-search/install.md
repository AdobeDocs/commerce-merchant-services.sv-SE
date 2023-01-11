---
title: "Installera [!DNL Live Search]"
description: "Lär dig hur du installerar, uppdaterar och avinstallerar [!DNL Live Search] från Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '1279'
ht-degree: 0%

---

# Installera [!DNL Live Search]

Live Search installeras som ett tillägg från Adobe Marketplace. Efter [!DNL Live Search] modulen (med katalogmoduler som beroenden) installeras och konfigureras, [!DNL Commerce] börjar dela söknings- och katalogdata med SaaS-tjänster. I det här skedet *Administratör* -användare kan skapa, anpassa och hantera regler för sökning, synonymer och varuexponering.

Det här avsnittet innehåller anvisningar om hur du gör följande:

* Installera [!DNL Live Search] (Metoder 1 och 2)
* [Uppdatera [!DNL Live Search]](#update)
* [Avinstallera [!DNL Live Search]](#uninstall)

## Innan du börjar {#before-you-begin}

Gör följande:

1. Bekräfta att [cron-jobb](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) och [indexerare](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) är igång.

1. Välj den startmetod som uppfyller dina krav och följ instruktionerna.

   * [Metod 1](#method-1): Installera utan [!DNL Elasticsearch]
   * [Metod 2](#method-2): Installera med [!DNL Elasticsearch] (Inga driftavbrott)

## Metod 1: Installera utan Elasticsearch {#method-1}

Den här startmetoden rekommenderas vid installation [!DNL Live Search] till

* Nytt [!DNL Commerce] installation
* Mellanlagringsmiljö

I det här scenariot avbryts storefront-åtgärder medan [!DNL Live Search] indexerar alla produkter i katalogen. Under installationen [!DNL Live Search] är aktiverade och [!DNL Elasticsearch] moduler är inaktiverade.

>[!TIP]
>
>Om du vill undvika skrivfel håller du markören över kodrutans högra hörn och klickar på knappen [!UICONTROL **Kopiera**] och klistra in den på kommandoraden.

1. Installera Adobe Commerce 2.4.x utan [!DNL Live Search].

1. Ladda ned `live-search` paketet, kör följande från kommandoraden:

   ```bash
   composer require magento/live-search
   ```

   Mer information finns i listan över [!DNL Live Search] [beroenden](#dependencies) som hämtas av [!DNL Composer].

1. Kör följande kommandon för att inaktivera [!DNL Elasticsearch] och tillhörande moduler, samt installera [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > När data indexeras och synkroniseras är söknings- och kategoribläddringsåtgärderna inte tillgängliga i butiken. Beroende på storleken på katalogen kan processen ta minst en timme från tidpunkten `cron` kör för att synkronisera data till [!DNL Live Search] tjänster.

1. Verifiera att följande [indexerare](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) är inställda på `Update by Schedule`:

   * Produktfeed
   * Produktvariantfeed
   * Matning för katalogattribut

1. Konfigurera [API-nycklar](#configure-api-keys) och verifiera att katalogdata [synkroniserad](#synchronize-catalog-data) med [!DNL Live Search] tjänster.

1. Om du vill göra ansikten tillgängliga som filter i butiken lägger du till [facets](facets-add.md) du behöver, enligt [krav på facettering](facets.md).

   Du bör kunna lägga till ansikten efter `cron` kör attributfeeds och exporterar attributmetadata.

1. Vänta minst en timme efter `cron` kör för att synkronisera data. Sedan [verifiera](#verify-export) att data exporterades.

1. [Testa](#test-the-connection) anslutningen från butiken.

## Metod 2: Installera med Elasticsearch {#method-2}

Den här startmetoden rekommenderas vid installation [!DNL Live Search] till:

* En befintlig produktion [!DNL Commerce] installation

I detta scenario [!DNL Elasticsearch] hanterar temporärt sökbegäranden från butiken medan [!DNL Live Search] indexerar alla produkter i bakgrunden utan att störa den normala lagerhanteringen. [!DNL Elasticsearch] är inaktiverat och [!DNL Live Search] aktiveras när alla katalogdata har indexerats och synkroniserats.

>[!TIP]
>
>Om du vill undvika skrivfel håller du markören över kodrutans högra hörn och klickar på knappen [!UICONTROL **Kopiera**] och klistra in den på kommandoraden.

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

1. Verifiera att följande [indexerare](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) är inställda på `Update by Schedule`:

   * Produktfeed
   * Produktvariantfeed
   * Matning för katalogattribut

1. Konfigurera [API-nycklar](#configure-api-keys) och verifiera att katalogdata [synkroniserad](#synchronize-catalog-data) med [!DNL Live Search] tjänster.

1. Om du vill göra ansikten tillgängliga som filter i butiken lägger du till [facets](facets-add.md) du behöver, enligt [krav på facettering](facets.md).

   Du bör kunna lägga till ansikten efter `cron` kör produkt- och attributfeeds och exporterar attributmetadata till [!DNL Live Search] tjänster.

1. Vänta i minst en timme innan data indexeras och synkroniseras. Använd sedan [GraphQL-uppspelning](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) med standardfrågan för att verifiera följande:

   * Det returnerade antalet produkter är nästan vad du förväntar dig för butiksvyn.
   * Fasett(n) returneras.

1. Kör följande kommandon för att aktivera [!DNL Live Search] moduler, inaktivera [!DNL Elasticsearch]och köra `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
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

Adobe Commerce API-nyckeln och den tillhörande privata nyckeln krävs för att ansluta [!DNL Live Search] till en installation av Adobe Commerce. API-nyckeln genereras och underhålls i kontot för [!DNL Commerce] licensinnehavare som kan dela det med utvecklaren eller SI. Utvecklaren kan sedan skapa och hantera SaaS Data Spaces för licenshavarens räkning.  Om du redan har en uppsättning API-nycklar behöver du inte generera om dem.

### Licensinnehavare för Adobe Commerce

Om du vill generera en API-nyckel och en privat nyckel ska du läsa [Commerce Services Connector](../landing/saas.md).

### Adobe Commerce utvecklare eller SI

Utvecklaren eller SI konfigurerar SaaS-datautrymmet enligt beskrivningen i *Commerce Services* i konfigurationen. I *Administratör* blir Commerce Services tillgängligt i *Konfiguration* sidofältet när en SaaS-modul är installerad.

## Synkronisera katalogdata {#synchronize-catalog-data}

[!DNL Live Search] kräver synkroniserade produktdata för sökåtgärder och synkroniserade attributdata för att konfigurera facets. Den inledande synkroniseringen mellan produktkatalogen och katalogtjänsten börjar när [!DNL Live Search] är först ansluten. Beroende på installationsmetod och katalogstorlek kan det ta upp till åtta timmar för data som ska exporteras och indexeras av [!DNL Live Search]. Listan med data som synkroniseras och delas med katalogtjänsten finns i schemat, som definieras i:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Verifiera export {#verify-export}

Så här verifierar du att katalogdata har exporterats från din Adobe Commerce-instans och synkroniserats för [!DNL Live Search]söker du efter poster i följande tabeller:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Mer hjälp finns i [[!DNL Live Search] katalogen inte synkroniserad](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) i supportkunskapsbasen.

### Framtida produktuppdateringar

Efter den första synkroniseringen kan det ta upp till 15 minuter innan ytterligare produktuppdateringar blir tillgängliga för butikssökning. Om du vill veta mer går du till [Indexering - direktuppspelande produktuppdateringar](indexing.md).

## Testa anslutningen {#test-connection}

Kontrollera följande i butiken:

* The [!UICONTROL Search] returnerar resultaten korrekt
* Kategoribläddring returnerar resultat korrekt
* Fasett(er) är tillgängligt som filter på sökresultatsidor

Om allt fungerar som det ska, grattis! [!DNL Live Search] är installerat, anslutet och klart att användas.

Om du stöter på problem i butiken ska du kontrollera `var/log/system.log` fil för API-kommunikationsfel eller fel på tjänstsidan.

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

Om du vill uppdatera till en större version, till exempel från 1.0.0 till 2.0.0, redigerar du projektets rot [!DNL Composer] `.json` på följande sätt:

1. Om din installerade `magento/live-search` versionen är `1.3.1` eller tidigare, och du uppgraderar till version `2.0.0` eller senare kör du följande kommando före uppgraderingen:

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
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **Spara** `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## Avinstallerar [!DNL Live Search] {#uninstall}

Avinstallera [!DNL Live Search], se [Avinstallera moduler](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).

## [!DNL Live Search] paket {#packages}

| Paket | Beskrivning |
|--- |--- |
| `module-live-search` | Gör det möjligt för handlare att konfigurera sina sökinställningar för ansikten, synonymer, frågeregler osv. och ger åtkomst till en skrivskyddad GraphQL-spelgrund för att testa frågor från *Administratör*. |
| `module-live-search-adapter` | Slussar sökförfrågningar från butiken till [!DNL Live Search] och återger resultaten i butiken. <br />- Kategoribläddring - dirigera begäranden från butiken [navigering överst](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) till söktjänsten.<br />- Global sökning - dirigera begäranden från [snabbsökning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) i det övre högra hörnet av butiken till vänster [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | En sökfunktion som ersätter standardsnabbsökningen och returnerar data och miniatyrbilder av de översta sökresultaten. |

## [!DNL Live Search] beroenden {#dependencies}

Följande [!DNL Live Search] beroenden hämtas av [!DNL Composer]:

| Beroende | Beskrivning |
|--- |--- |
| Exportera moduler | Följande moduler samlar in och synkroniserar katalogdata:<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Krävs för att konfigurera din anslutning till Commerce Services. |
| `module-services-id` | Krävs för att konfigurera din anslutning till Commerce Services. |
