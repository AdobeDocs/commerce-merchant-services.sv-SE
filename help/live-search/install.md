---
title: "Kom igång med [!DNL Live Search]"
description: "Läs systemkraven och installationsstegen för [!DNL Live Search] från Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: aba1f41965e6c430f569adcf9d940cf399b50b73
workflow-type: tm+mt
source-wordcount: '2266'
ht-degree: 0%

---

# Konfigurera för framgång med [!DNL Live Search]

Adobe Commerce [!DNL Live Search] och [[!DNL Catalog Service]](../catalog-service/guide-overview.md) samarbeta för att tillhandahålla en presterande, relevant och intuitiv söklösning så att era kunder snabbt kan hitta exakt det de behöver. I synnerhet [!DNL Catalog Service] hämtar katalogdata för SaaS-tjänster, som [!DNL Live Search] att använda.

I den här artikeln finns stegvisa instruktioner för hur du implementerar [!DNL Live Search] med [!DNL Catalog Service].

>[!IMPORTANT]
>
>När det gäller webbplatssökningar har Adobe Commerce fler alternativ. Var noga med att läsa [Gränser och begränsningar](boundaries-limits.md) innan de implementeras, säkerställa [!DNL Live Search] passar ditt företags behov.

## Målgrupp

Den här artikeln är avsedd för utvecklare eller systemintegratörer i ditt team som ansvarar för att installera och konfigurera din Adobe Commerce-instans.

## Krav

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## Plattformar som stöds

- Adobe Commerce on Cloud (ECE): 2.4.4+
- Adobe Commerce on-prem (EE): 2.4.4+

## Översikt över arbetsflödet

På en hög nivå, introduktion [!DNL Live Search] kräver att du

![Arbetsflöde för Live Search](assets/livesearch-workflow.png)

## 1. Installera [!DNL Live Search] extension

[!DNL Live Search] installeras som ett tillägg från [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) via [Disposition](https://getcomposer.org/). När du har installerat och konfigurerat [!DNL Live Search], ADOBE [!DNL Commerce] börjar dela söknings- och katalogdata med SaaS-tjänster. I det här skedet *Administratör* -användare kan skapa, anpassa och hantera regler för sökning, synonymer och varuexponering.

>[!NOTE]
>
>Från [!DNL Live Search] 3.0.2, [!DNL Catalog Service] tillägget paketeras i med [!DNL Live Search] installation.

1. Bekräfta att [cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) och [indexerare](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) är igång.

   >[!IMPORTANT]
   >
   >På grund av att supporten för Elasticsearch 7 upphör i augusti 2023 rekommenderas att alla Adobe Commerce-kunder migrerar till sökmotorn OpenSearch 2.x. Mer information om hur du migrerar sökmotorn under en produktuppgradering finns i [Migrerar till OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) i _Uppgraderingshandbok_.

1. Ladda ned `live-search` paketet från [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. Kör följande från kommandoraden:

   ```bash
   composer require magento/live-search
   ```

   Om du lägger till [!DNL Live Search] tillägg till en **new** Adobe Commerce-installation, kör följande för att inaktivera [!DNL OpenSearch] och tillhörande moduler, samt installera [!DNL Live Search]. Fortsätt sedan till steg 4.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Om du lägger till [!DNL Live Search] tillägg till en **befintlig** Installera Adobe Commerce genom att köra följande för att tillfälligt inaktivera [!DNL Live Search] moduler som används för sökresultat i butiker. Fortsätt sedan till steg 4:

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] fortsätter att hantera sökbegäranden från butiken medan [!DNL Live Search] synkroniserar katalogdata och indexerar produkter i bakgrunden.

1. Kör följande:

   ```bash
   bin/magento setup:upgrade
   ```

1. Verifiera att följande [indexerare](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) är inställda på&quot;Uppdatera enligt schema&quot;:

   - Produktfeed
   - Produktvariantfeed
   - Matning för katalogattribut
   - Produktprisfeed
   - Omfattningar för webbplatsdatafeed
   - Omfång Datamatning för kundgrupper
   - Kategoriflöde
   - Kategoribehörighetsfeed

1. Om du installerar [!DNL Live Search] på en ny Commerce-instans är du klar och kan hoppa till [2. Konfigurera API-nycklar](#2-configure-api-keys) -avsnitt. Om du installerar Live Search i en befintlig Commerce-instans fortsätter du till nästa steg.

1. Kör följande kommandon för att aktivera [!DNL Live Search] tillägg, inaktivera [!DNL OpenSearch]och köra `setup`.

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

## 2. Konfigurera API-nycklar

Adobe Commerce API-nyckeln och den tillhörande privata nyckeln krävs för att ansluta [!DNL Live Search] till en installation av Adobe Commerce. API-nyckeln genereras och underhålls i kontot för [!DNL Commerce] licensinnehavare som kan dela det med utvecklaren eller systemintegratören. Utvecklaren kan sedan skapa och hantera SaaS Data Spaces för licenshavarens räkning. Om du redan har en uppsättning API-nycklar behöver du inte generera om dem.

Lär dig hur du konfigurerar API-nycklar i [Commerce Services Connector](../landing/saas.md) artikel.

## 3. Synkronisera katalogdata {#synchronize-catalog-data}

[!DNL Live Search] flyttar katalogdata till infrastrukturen i Adobe SaaS. Data indexeras och sökresultat levereras från detta index direkt till butiken. Beroende på storlek och komplexitet kan indexeringen ta mellan 30 minuter och några timmar.

Kör följande kommandon i den ordning som du vill börja synkronisera katalogdata till SaaS-tjänster:

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

När du kör dessa kommandon börjar den inledande synkroniseringen av katalogdata till SaaS-tjänster.

>[!WARNING]
>
> När data indexeras och synkroniseras är söknings- och kategoribläddringsåtgärderna inte tillgängliga i butiken. Beroende på storleken på katalogen kan processen ta minst en timme från tidpunkten `cron` kör för att synkronisera data till SaaS-tjänster.

### Övervaka synkroniseringsförlopp

Du kan visa data som är synkroniserade och delade med [Instrumentpanel för datahantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Den här instrumentpanelen ger värdefulla insikter om tillgängligheten av produktdata för butiken, så att den snabbt kan visas för kunderna.

![Instrumentpanel för datahantering](assets/data-management-dashboard.png)

#### Framtida produktuppdateringar

Efter den första synkroniseringen kan det ta upp till 15 minuter innan ytterligare produktuppdateringar blir tillgängliga för butikssökning. Mer information finns på [Indexering - direktuppspelande produktuppdateringar](indexing.md).

## 4. Verifiera att data exporterades {#verify-export}

Så här verifierar du att katalogdata har exporterats från din Adobe Commerce-instans och synkroniserats för [!DNL Live Search]har du några alternativ:

- Leta efter poster i följande tabeller:

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- Använd [GraphQL playground](https://developer.adobe.com/commerce/services/graphql/live-search/) med standardfrågan för att verifiera följande:

   - Det returnerade antalet produkter är nästan vad du förväntar dig för butiksvyn.
   - Ansikten returneras.

Mer hjälp finns i [[!DNL Live Search] katalogen inte synkroniserad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) i supportkunskapsbasen.

## 5. Konfigurera data

Om du konfigurerar dina produktdata på rätt sätt får du bra sökresultat för dina kunder. I det här avsnittet aktiverar du widgetar för produktlistor och tilldelar kategorier.

### Aktivera widgetar för produktlistor

När du installerar [!DNL Live Search] 4.0.0+, produktlistwidgetar är aktiverade som standard. När widgetar är aktiverade används en annan UI-komponent för sökresultatsidan och kategoribläddra på produktlistsidan. Den här gränssnittskomponenten gör direktanrop till [Katalogtjänstens API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/), vilket ger snabbare svarstider.

Om du har en [!DNL Live Search] äldre än 4.0.0+ måste du aktivera produktlistwidgeten manuellt.

1. Från *Administratör*, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Under **[!UICONTROL Live Search]**, markera **[!UICONTROL Storefront Features]**.
1. Ange **[!UICONTROL Enable Product Listing Widgets]** till `Yes`.

   ![Aktivera widgetar för produktlistor](assets/ls-admin-enable-widget.png)

När du ändrar den här konfigurationen visas ett meddelande `Page cache is invalidated` visas. Du måste tömma cacheminnet i Magento för att spara ändringen.

1. Öppna [Cachehantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) gör något av följande:

   - Klicka på **[!UICONTROL Cache Management]** i meddelandet ovanför arbetsytan.
   - På _Administratör_ sidebar, gå till **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Välj **Konfiguration** [!UICONTROL Cache Type] och klicka **[!UICONTROL Flush Magento Cache]**.

   Ändringar i butiken görs omedelbart efter att du tömt cachen.

### Tilldela kategorier

Produkter som returneras i [!DNL Live Search] måste tilldelas en [kategori](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). I Luma kan till exempel produkter delas in i kategorier som &quot;Män&quot;, &quot;Kvinnor&quot; och &quot;Kugghjul&quot;. Underkategorierna är också inställda för &quot;Tops&quot;, &quot;Bottom&quot; och &quot;Watches&quot;. Detta ger bättre granularitet vid filtrering.

## 6. Testa anslutningen {#test-connection}

Testa att se till att produktdata returneras i följande scenarier med dina katalogdata nu i SaaS:

- The [!UICONTROL Search] returnerar resultaten korrekt
- Kategoribläddring returnerar resultat korrekt
- Ansikten finns som filter på sökresultatsidor

Om allt fungerar korrekt [!DNL Live Search] är installerat, anslutet och klart att användas.

Om du stöter på problem i butiken ska du kontrollera `var/log/system.log` fil för API-kommunikationsfel eller fel på tjänstsidan.

Tillåt [!DNL Live Search] via en brandvägg lägger du till `commerce.adobe.io` till tillåtelselista.

## 7. Anpassa för butiken

Du har installerat [!DNL Live Search] tillägg, synkroniserade, validerade och konfigurerade dina data. Nu ska du se till att [!DNL Live Search] widgetarna anpassas efter butikens utseende och känsla.

Du kan formatera widgetarna pover och PLP genom att definiera anpassade CSS-regler efter behov. Se [Formatera popoposerelement](storefront-popover.md#styling-popover-example) och [Sidwidget för produktlista](plp-styling.md#styling-example).

Om du vill utöka widgetarnas funktioner är källkoden för varje tillgängligt i en offentlig rapport.
I det här scenariot kan du anpassa JavaScript efter dina egna behov och sedan lägga din egen kod på ditt CDN. Det här anpassade skriptet kommunicerar med [!DNL Live Search] och returnerar resultatet som vanligt, så att du kan styra widgetens funktioner.

- [PLP-widget - repo](https://github.com/adobe/storefront-product-listing-page)
- [Repo av sökfältet](https://github.com/adobe/storefront-search-as-you-type)

## Uppdaterar [!DNL Live Search] {#update}

Innan du uppdaterar Live Search kör du följande kommandorad för att kontrollera vilken version av Live Search som är installerad:

```bash
composer show magento/module-live-search | grep version
```

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

1. Spara `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Avinstallerar [!DNL Live Search] {#uninstall}

Avinstallera [!DNL Live Search], se [Avinstallera moduler](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] paket {#packages}

The [!DNL Live Search] tillägget består av följande paket:

| Paket | Beskrivning |
|--- |--- |
| `module-live-search` | Gör det möjligt för handlare att konfigurera sina sökinställningar för ansikten, synonymer, frågeregler och så vidare, och ger åtkomst till en skrivskyddad GraphQL-spelningsmiljö för att testa frågor från *Administratör*. |
| `module-live-search-adapter` | Slussar sökförfrågningar från butiken till [!DNL Live Search] och återger resultaten i butiken. <br />- Kategoribläddring - dirigera begäranden från butiken [navigering överst](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) till söktjänsten.<br />- Global sökning - dirigera begäranden från [snabbsökning](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) i det övre högra hörnet av butiken längst upp till vänster [!DNL Live Search] service. |
| `module-live-search-storefront-popover` | En sökfunktion som ersätter standardsnabbsökningen och returnerar data och miniatyrbilder av de översta sökresultaten. |

## [!DNL Live Search] beroenden {#dependencies}

Följande [!DNL Live Search] beroenden hämtas av [!DNL Composer].

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## Avancerade begrepp

Följande avsnitt innehåller mer avancerade ämnen när du använder [!DNL Live Search] och [!DNL Catalog Service].

### Slutpunkt

[!DNL Live Search] kommunicerar via slutpunkten vid `https://catalog-service.adobe.io/graphql`.

Som [!DNL Live Search] inte har tillgång till hela produktdatabasen, [!DNL Live Search] GraphQL och Commerce Core GraphQL kommer inte att ha fullständig paritet.

Vi rekommenderar att du anropar SaaS API:er direkt - särskilt katalogtjänstslutpunkten.

- Öka prestanda och minska belastningen på processorn genom att kringgå Commerce databas-/grafikprocess
- Utnyttja [!DNL Catalog Service] federation att ringa [!DNL Live Search], [!DNL Catalog Service]och [!DNL Product Recommendations] från en enda slutpunkt.

I vissa fall är det kanske bättre att ringa [!DNL Catalog Service] för produktinformation och liknande. Se [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) för mer information.

Om du har en anpassad headless-implementering kan du ta en titt på [!DNL Live Search] referensimplementeringar:

- [PLP-widget](https://github.com/adobe/storefront-product-listing-page)
- [Livesökfält](https://github.com/adobe/storefront-search-as-you-type)

Om du inte använder standardkomponenterna, som Sökadapter eller widgetar på Luma, eller AEM CIF widgetar, kommer inte händelser (klickströmsdata som matar Adobe Sensei för intelligent marknadsföring och prestandamått) att fungera som de ska och kräver anpassad utveckling för att implementera headless-händelser.

Den senaste versionen av [!DNL Live Search] används redan [!DNL Catalog Service].

### Språkstöd

[!DNL Live Search] widgetar stöder följande språk:

|  |  |  |  |
|--- |--- |--- |--- |
| Språk | Län | Språkkod | Magento |
| Bulgariska | Bulgarien | bg_BG | bg_BG |
| Katalanska | Spanien | ca_ES | ca_ES |
| Tjeckiska | Tjeckien | cs_CZ | cs_CZ |
| Danska | Danmark | da_DK | da_DK |
| Tyska | Tyskland | de_DE | de_DE |
| Grekiska | Grekland | el_GR | el_GR |
| Engelska | Förenade kungariket | en_GB | en_GB |
| Engelska | Amerikas förenta stater | sv_SE | sv_SE |
| Spanska | Spanien | es_ES | es_ES |
| Estniska | Estland | et_EE | et_EE |
| Baskiska | Spanien | eu_ES | eu_ES |
| Persiska | Iran | fa_IR | fa_IR |
| Finska | Finland | fi_FI | fi_FI |
| Franska | Frankrike | fr_FR | fr_FR |
| Galiciska | Spanien | gl_ES | gl_ES |
| Hindi | Indien | hi_IN | hi_IN |
| Ungerska | Ungern | hu_HU | hu_HU |
| Indonesiska | Indonesien | id_ID | id_ID |
| Italienska | Italien | it_IT | it_IT |
| Koreanska | Sydkorea | ko_KR | ko_KR |
| Litauiska | Litauen | lt_LT | lt_LT |
| Lettiska | Lettland | lv_LV | lv_LV |
| Norska | Norge bokmål | nb_NO | nb_NO |
| Nederländska | Nederländerna | nl_NL | nl_NL |
| Polska | Polen | pl_PL | pl_PL |
| Portugisiska | Brasilien | pt_BR | pt_BR |
| Portugisiska | Portugal | pt_PT | pt_PT |
| Rumänska | Rumänien | ro_RO | ro_RO |
| Ryska | Ryssland | ru_RU | ru_RU |
| Svenska | Sverige | sv_SE | sv_SE |
| Thailändska | Thailand | th_TH | th_TH |
| Turkiska | Turkiet | tr_TR | tr_TR |
| Kinesiska | Kina | zh_CN | zh_Hans_CN |
| Kinesiska | Taiwan | zh_TW | zh_Hant_TW |

Om widgeten upptäcker att språkinställningen för Commerce Admin (_Lager_ > Inställningar > _Konfiguration_ > _Allmänt_ > landsalternativ) matchar ett språk som stöds, det språket som standard. I annat fall är widgetarna standard engelska.

Administratörer kan också ange språket för [sökindex](settings.md#language)för att få bättre sökresultat.

### Databas för Widget-kod

Widgeten Produktlistsida och widgeten för Live-sökfält är båda tillgängliga för hämtning från deras github-databas.

Detta gör att utvecklare kan anpassa funktionaliteten och stilen helt och hållet. Dessa användare lagrar själva koden samtidigt som de drar nytta av [!DNL Live Search] service.

- [PLP-widget](https://github.com/adobe/storefront-product-listing-page)
- [Sökfältet](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] supports [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) i Commerce (tidigare Multi-Source Inventory eller MSI). Om du vill aktivera fullständig support måste du [uppdatera](install.md#update) beroende modul `commerce-data-export` till version 10.2.0+.

[!DNL Live Search] returnerar ett booleskt meddelande som anger om en produkt är tillgänglig i Inventory management, men inte innehåller information om vilken källa som har aktien.

### Prisindexerare

Live Search-kunder kan använda nya [SaaS prisindexerare](../price-index/price-indexing.md), vilket ger snabbare prisförändringsuppdateringar och synkroniseringstid.

### Prisstöd

Live Search-widgetar har stöd för de flesta, men inte alla, pristyper som stöds av Adobe Commerce.

För närvarande stöds baspriser. Avancerade priser som inte stöds är:

- Kostnad
- Lägsta kampanjpris

Titta på [API-nät](../catalog-service/mesh.md) för mer komplexa prisberäkningar.

Prisformatet har stöd för de nationella konfigurationsinställningarna i Commerce-instansen: *Lager* > Inställningar > *Konfiguration* > Allmänt > *Allmänt* > Lokala alternativ > Språk.

### Headless storefront support

Du kan också behöva installera `module-data-services-graphql` som utökar programmets befintliga GraphQL-täckning till att omfatta fält som krävs för storefront-beteendedatainsamling.

```bash
composer require magento/module-data-services-graphql
```

Den här modulen lägger till ytterligare kontexter i GraphQL-frågor:

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### Stöd för B2B

[!DNL Live Search] supports [B2B-funktionalitet](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) med ytterligare [begränsningar](boundaries-limits.md#b2b-and-category-permissions).

### Stöd för PWA

[!DNL Live Search] fungerar med PWA Studio, men användare kan se små skillnader jämfört med andra Commerce-implementeringar. Grundläggande funktioner som sök- och produktlistsidor fungerar i Venia, men vissa permutationer av Graphql kanske inte fungerar som de ska. Det kan också finnas prestandaskillnader.

- Den nuvarande PWA-implementeringen av [!DNL Live Search] kräver mer bearbetningstid för att returnera sökresultat än [!DNL Live Search] med den inbyggda Commerce Store.
- [!DNL Live Search] i PWA stöder inte [händelsehantering](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Därför kommer sökrapporter och intelligent varuexponering att fungera.
- Filtrera direkt på `description`, `name`, `short_description` stöds inte av GraphQL när det används med [PWA](https://developer.adobe.com/commerce/pwa-studio/), men de returneras med ett mer allmänt filter.

Används [!DNL Live Search] Med PWA Studio måste integratörerna också

1. Installera [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Ange `environmentId` i `storeDetails` -objekt.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Cookies

[!DNL Live Search] samlar in användarinteraktionsdata som en del av basfunktionen och cookies används för att lagra dessa data. När användaren samlar in användarinformation måste han eller hon godkänna att lagra cookies. [!DNL Live Search] och [!DNL Product Recommendations] delar dataströmmen och därmed samma cookie-mekanism. Läs mer om det i [Hantera cookie-begränsningar](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
