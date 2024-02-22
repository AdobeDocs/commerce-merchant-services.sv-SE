---
title: "[!DNL Live Search] Versionsinformation"
description: "Den senaste versionsinformationen för [!DNL Live Search] från Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 89f0cd15e7eeb7f8f1f76df7a3612ba3ef02391e
workflow-type: tm+mt
source-wordcount: '1900'
ht-degree: 0%

---

# [!DNL Live Search] Versionsinformation

I versionsinformationen beskrivs de senaste versionerna av [!DNL Live Search].
Support ges för den aktuella större versionen. Versionsinformation för äldre versioner finns som referens.
Bland uppdateringarna finns:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigera](../assets/fix.svg) Korrigeringar och förbättringar
![Fel](../assets/bug.svg) Kända fel

## Uppdateringar av värdtjänster

Dessa anteckningar beskriver uppdateringar som publicerats utanför en versionshanteringsversion eller förbättringar av värdtjänsten.

_13 februari 2024_

![Nytt](../assets/new.svg) [!DNL Live Search] har nu stöd för att ange en standardregel för [Search Merchandising](rules.md).

_27 oktober 2023_

![Nytt](../assets/new.svg) The [!DNL Live Search] PLP-widgeten har nu stöd för färgrutor.

_12 oktober 2023_

![Nytt](../assets/new.svg) Commerce-administratörer kan nu ange språk för indexet för [!DNL Live Search]. Se [Inställningar](settings.md).
![Korrigera](../assets/fix.svg) Fliken &quot;Sökregler&quot; har bytt namn till &quot;Sökmarknadsföring&quot;.

_13 juni 2023_

![Korrigera](../assets/fix.svg) Ett problem har korrigerats där vissa tecken som citattecken eller apostrofer orsakade problem med rankningen. Omindexering löser dessa problem.

_25 april 2023_

![Nytt](../assets/new.svg) [!DNL Live Search] kan nu dra nytta av de nya [SaaS prisindexerare](../price-index/index.md).

## [!DNL Live Search] 4.1.0 {#410}

_22 feb 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

### Nya funktioner

![Nytt](../assets/new.svg) The [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) är nu tillgängligt. Den här förbättrade instrumentpanelen ger insikter i dataströmmar för [!DNL Product Recommendations], [!DNL Live Search]och [!DNL Catalog Service].
![Nytt](../assets/new.svg) Flera nya funktioner har lagts till i [PLP-widget](plp-styling.md):

* Växla lista/rutnätsvy
* Knapparna Lägg till i kundvagn
* Stöd för färgrutor
* Flera bilder per produkt
* Prisreglage
* Språkstöd

Handlare måste uppgradera [!DNL Live Search] till version >= 4.1.0 för att få tillgång till dessa funktioner.

### Uppdateringar

![Korrigera](../assets/fix.svg) Korrigerade ett problem som orsakade ett fel när gästanvändare lade till produkter i en varukorg i butiksvyer som inte är standard.
![Korrigera](../assets/fix.svg) Korrigerade ett problem som gjorde att sökleverantören alltid visade valutasymbolen framför prisvärdet oavsett språkinställningar.
![Korrigera](../assets/fix.svg) Onödiga typdefinitioner för inaktiverade insticksprogram har tagits bort för att åtgärda kompatibilitetsproblem vid installationen.

## [!DNL Live Search] 4.0.0 {#400}

_13 nov 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

### Nya funktioner

![Nytt](../assets/new.svg) [!DNL Live Search] stöder nu färgrutor i PLP-widgeten.
![Nytt](../assets/new.svg) [!DNL Live Search] visar nu kategorinamnet i stället för kategori-ID:t.
![Nytt](../assets/new.svg) [!DNL Live Search] har nu stöd för genomstrykningspris i PLP-widgeten.
![Nytt](../assets/new.svg) Knappen&quot;Dölj filter&quot; introducerades för att dölja filterpanelen.


### Uppdateringar

![Korrigera](../assets/fix.svg) The [!DNL Live Search] PLP-widgeten är nu aktiverad som standard för nya installationer.
![Korrigera](../assets/fix.svg) Omkonfigurerade CSS-format för att isolera widgetklasser bättre.
![Korrigera](../assets/fix.svg) Mindre felkorrigeringar

Efter installation av version 3.1.1 eller senare aktiverar du de nya indexerarna:

* Produktprisfeed
* Omfattningar av webbplatsens dataflöde
* Omfattningar av kundgruppsdatafeed

När du har uppgraderat testar du den uppdaterade konfigurationen i QA eller Staging innan du överför ändringarna till produktionen.

## Tidigare versioner

+++3.1.1 och tidigare

## [!DNL Live Search] 3.1.1 {#311}

_15 sept 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Fliken Ny kategorimarknadsföring har lagts till. Nu kan man lägga in intelligenta rankningar och manuella rankningar (stift, boost, bury, hide) per kategori
![Nytt](../assets/new.svg) Användare kan lägga till en enskild kategoriregel med intelligent eller manuell rankning
![Nytt](../assets/new.svg) Användare kan nu lägga till regler för intelligent rankning i underkategorier
![Nytt](../assets/new.svg) Detaljerad information ges när underkategorier tas bort med intelligent rankning
![Nytt](../assets/new.svg) Lagt till möjlighet att ta bort regler för ärvda rankningsstrategier
![Nytt](../assets/new.svg) Lagt till möjlighet att ta bort regler för en enskild kategori
![Nytt](../assets/new.svg) Användarna kan nu söka efter kategorinamn när de lägger till en regel
![Nytt](../assets/new.svg) I kategoriträdvyn kan användare nu visa vilken kategori som har regler.
![Nytt](../assets/new.svg) Kategoriförhandsvisning visar bara den valda kategorin.
![Nytt](../assets/new.svg) AEM CIF [Widgeten Pekare](https://github.com/adobe/aem-cif-guides-venia/pull/319) och [PLP-widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) gör att AEM kan utnyttja [!DNL Live Search].

### Uppdateringar

![Korrigera](../assets/fix.svg) Tabellstorleken för Produkterna och prisflödena har reducerats avsevärt. Tabeller `catalog_data_exporter_products` och `catalog_data_exporter_product_prices` en betydande minskning av storleken.
![Korrigera](../assets/fix.svg) Fliken Regler har bytt namn till Sökregler
![Korrigera](../assets/fix.svg) När du rangordnar efter &#39;trending&#39; kan du nu välja mellan: * 3 dagar (standard) * 14 dagar * 30 dagar
![Korrigera](../assets/fix.svg) &#39;Händelser&#39; (Öka/fäst/bränn/dölj) har bytt namn till &#39;Manuell rankning&#39;
![Korrigera](../assets/fix.svg) Rankningstypen har bytt namn till Intelligent ranking
![Korrigera](../assets/fix.svg) Mindre felkorrigeringar

## [!DNL Live Search] 3.1.0 {#310}

_1 sept 2023_

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

### Uppdateringar

![Korrigera](../assets/fix.svg) Widgeten Produktlista har uppdaterats för att använda [Katalogtjänstens API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_7 augusti 2023_

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

### Nya funktioner

![Nytt](../assets/new.svg) Följande värden har lagts till i `storeDetails` objekt:

* &quot;Tillåt alla produkter per sida&quot;
* Valutakurs
* &quot;Produkter per sida på tillåtna värden för stödraster&quot;
* &quot;Produkter per sida på standardvärde för stödraster&quot;
* Butiksspråk

### Uppdateringar

![Korrigera](../assets/fix.svg) Katalogtjänstmoduler har lagts till i metapaketet för att ge stöd för avancerad datahämtning.
![Korrigera](../assets/fix.svg) The **Mitt konto** sidnavigeringen försvinner inte längre när du använder widgeten Produktlistsida.

Handlare måste uppgradera [!DNL Live Search] tilläggsversion >= 3.0.2 för att komma åt dessa funktioner.

Vi rekommenderar att du uppgraderar och testar innan du går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

### Begränsningar

Om du använder widgeten Live Search-produktlistningssida kommer Google Tag Manager att misslyckas. Använd standardsökkortet om Google Tag Manager behövs.

## [!DNL Live Search] 3.0.1 {#301}

_14 mars 2023_

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

### Nya funktioner

![Nytt](../assets/new.svg) Produktartikelkort i regelförhandsgranskning
![Nytt](../assets/new.svg) [Widgeten Produktlistsida](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
![Nytt](../assets/new.svg) [Kategorifiltreringsalternativ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![Nytt](../assets/new.svg) Lagt till möjlighet att dra och släppa för att skapa fäst-händelser
![Nytt](../assets/new.svg) Nya fäst-åtgärder: * Fäst på plats - Fäst-knapp för att skapa en Fäst-händelse med ett klick * Fäst överst - Placerar produkten på den första positionen * Fäst nederst - Placerar produkten längst ned i resultaten * Fäst en händelse med ett klick
![Nytt](../assets/new.svg) [Intelligent rankning av regler](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)
![Nytt](../assets/new.svg) [!DNL Live Search] nu stöder fullt [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) i Commerce (tidigare Multi-Source Inventory, eller MSI). Om du vill aktivera fullständig support måste du [uppdatera](install.md#update) beroende modul `commerce-data-export` till version 10.2.0+.

### Uppdateringar

![Korrigera](../assets/fix.svg) Konfigurera regler sorterar nu positioner automatiskt
![Korrigera](../assets/fix.svg) Förhandsgranskning uppdateras nu när en befintlig händelse tas bort
![Korrigera](../assets/fix.svg) Regler utan händelser kan sparas
![Korrigera](../assets/fix.svg) Ta bort funktionsväljaren &quot;Välj typ&quot;
![Korrigera](../assets/fix.svg) Ny redigeringsstatus för ej sparade regler har lagts till

### Korrigeringar

![Korrigera](../assets/fix.svg) Ett serverfel har korrigerats när en oavslutad händelse inträffar när filen sparades
![Korrigera](../assets/fix.svg) Korrekt borttagning av en specifik händelse vid flera händelser
![Korrigera](../assets/fix.svg) En befintlig regelhändelse som inte uppdaterades när en ny händelse har lagts till har åtgärdats
![Korrigera](../assets/fix.svg) Korrigerat den andra&quot;Redigera&quot;-klickningen från detaljer, [!DNL Live Search] sida som behöver laddas om
![Korrigera](../assets/fix.svg) Synonymer: Ett problem har korrigerats när en användare klickade bort från indata och de inte kunde återställa fokus till fältet
![Korrigera](../assets/fix.svg) Andra mindre felkorrigeringar och prestandauppdateringar


![Fel](../assets/bug.svg) - Rankning efter&quot;Rekommenderas för dig&quot; stöds endast i Live Search-widgetar. Det stöds inte med standardsökfunktionen för Luma och PWA.
![Fel](../assets/bug.svg) - Egna prisattributaspekter återges inte korrekt i Luma, men API:t filtrerar på dem korrekt.

Handlare måste uppgradera [!DNL Live Search] tilläggsversion >= 3.0.1 för att komma åt dessa funktioner.

Vi rekommenderar att du uppgraderar och testar innan du går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

![Korrigera](../assets/fix.svg) - Live Search genererar ett fel när SDK-resurser inte är tillgängliga på grund av nätverksproblem. Det här felet har åtgärdats.

Handläggarna måste uppgradera Live Search-tilläggsversionen >= 2.0.5 för att få tillgång till dessa funktioner.

Vi rekommenderar att du uppgraderar och testar innan du går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

![Nytt](../assets/new.svg) Live Search har nu stöd för filtrering med inställningen &quot;Visa ej i Stock-produkter&quot; i administratören. Om Visa utanför Stock-produkter har värdet false `inStock = true` läggs till i filtret.
![Korrigera](../assets/fix.svg) För att förbättra prestanda har blocket Förslag tagits bort från popup-fönstret Live Search. Data skickas fortfarande via GraphQL om du vill ersätta funktionen.
![Korrigera](../assets/fix.svg) `categories` och `categoryPath` har ersatts `categoryIds` för kategorifiltrering. Läs mer i [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) ämne.
![Korrigera](../assets/fix.svg) Tidigare fick en användare som är knuten till ett B2B-företag en felaktig kundgruppskod när de gjorde sökningar. Live Search returnerar nu korrekt värde.
![Korrigera](../assets/fix.svg) Tidigare returneras ett fel om du söker efter en term som inte finns. Felet är nu åtgärdat.

Handlare måste uppgradera [!DNL Live Search] tilläggsversion >= 2.0.4 för att komma åt dessa funktioner.

Man rekommenderar att man uppgraderar och testar innan man går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

![Nytt](../assets/new.svg) Live Search har nu stöd för B2B-funktioner genom att man följer kategoribehörigheter, delade kataloger och kundgruppsspecifika priser.

Handlare måste uppgradera [!DNL Live Search] tilläggsversion >= 2.0.3 för att komma åt dessa funktioner.

Man rekommenderar att man uppgraderar och testar innan man går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

Befintlig [!DNL Live Search] installationerna måste uppgraderas till [!DNL Live Search] 2.0.0 för att utnyttja följande nya funktioner, korrigeringar och förbättringar:

![Nytt](../assets/new.svg) [!DNL Live Search] nu stöder PHP 8.1 för installationer som kör Adobe Commerce 2.4.4.
![Nytt](../assets/new.svg) The `Magento_ElasticsearchCatalogPermissionsGraphQl` läggs till i listan med moduler som är inaktiverade under installationen.
![Nytt](../assets/new.svg) Antalet tillgängliga rader i [[!DNL storefront popover]](quick-tour.md) kan konfigureras från *Administratör*.
![Nytt](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) stöds för [!DNL Live Search].
![Nytt](../assets/new.svg) The [!DNL Live Search] installationsprocessen uppdateras med avancerade processändringar.
![Korrigera](../assets/fix.svg) [Avancerad sökning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) länk borttagen från sidfoten i butiken.
![Fel](../assets/bug.svg) Följande produktattribut stöds inte av [Commerce GraphQL API](https://developer.adobe.com/commerce/services/graphql/live-search/) vid användning i samband med betaversionen av PWA: `description`, `name`, `short_description`
![Fel](../assets/bug.svg) Betaversionen av PWA för [!DNL Live Search] stöder inte [händelsehantering](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

![Korrigera](../assets/fix.svg) [Anpassat prisattribut](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) returnerar inte längre ett fel när det konfigureras som [facet]({% link live-search/facets-add.md %}).
![Korrigera](../assets/fix.svg) Korrigerat problem som orsakade att ett fel uppstod när inget [valutasymbol](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) är tillgängligt.
![Korrigera](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) nu visas [Specialpris](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (lägsta slutpris) om tillgängligt.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

![Nytt](../assets/new.svg) [Prestanda](performance.md) på kontrollpanelen för rapporter ger insikt i söktermer som kunderna använder.
![Nytt](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) ger tillgång till ett gemensamt datalager med händelsepublicerings- och prenumerationstjänster samt mätvärden.
![Korrigera](../assets/fix.svg) The [[!DNL Storefront popover]](storefront-popover.md) har en ny `active` klassen för `.search-autocomplete` behållare som styr synlighet.
![Korrigera](../assets/fix.svg) I butiken finns [Sökvillkor](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) sidfotslänken tas bort och dess cache inaktiveras för [!DNL Live Search] installationer.
![Fel](../assets/bug.svg) Patch for Search-kort hanterar dubblettprodukter.
![Fel](../assets/bug.svg) [!DNL Live Search] supports [single-source](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) (fysisk) lagerplatser med flera (virtuell) [lager](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Flera lagerkällor stöds inte nu.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

![Nytt](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) visar föreslagna produkter och miniatyrbilder av de bästa sökresultaten när kunderna skriver frågor i sökrutan.
![Nytt](../assets/new.svg) Handel *Administratör* -sessionen förblir öppen under längre perioder av tangentbordsinaktivitet
![Nytt](../assets/new.svg) [!DNL Live Search] aktiveras automatiskt efter introduktionen
![Korrigera](../assets/fix.svg) Inledande indexeringstid är mindre än en timme
![Korrigera](../assets/fix.svg) Stegvisa produktuppdateringar nära realtid (efter installation och installation)
![Korrigera](../assets/fix.svg) Sorterbara kolumner i synonymredigeraren
![Korrigera](../assets/fix.svg) [!DNL Live Search] returnerar inte längre ett fel om sökvillkoren innehåller ett tomt sorteringsordningsvärde
![Korrigera](../assets/fix.svg) Intervallfiltrering bryts inte längre om attributkoder innehåller strängarna &quot;to&quot; eller &quot;from&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Stöds]{type="Informativ" tooltip="Stöds"}

![Fel](../assets/bug.svg) The [!DNL Live Search] tjänsten stöder endast [basvaluta](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) av Adobe Commerce-installationen.
![Fel](../assets/bug.svg) När du lägger till en fasett uppdateras inte produktattributsmatningen korrekt om den anges till `Update on Save`. För att undvika det här problemet, gå till [Indexhantering](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) och ange produktattribut för feed till `Update by Schedule`.
![Fel](../assets/bug.svg) [!DNL Live Search] synonymer definieras per butiksvy, men lagras för närvarande per webbplats och identifieras med en kombination av `environmentId` och `storeViewCode`. Därför delar alla webbplatser och vyer i Adobe Commerce-installationen synonymer. Den senast skapade uppsättningen synonymer för butiksvyn har företräde.
![Fel](../assets/bug.svg) Om en synonymterm innehåller flera ord behandlas varje ord som en separat synonym. Om du till exempel definierar&quot;tidsbit&quot; som en synonym till&quot;watch&quot;, behandlas både&quot;time&quot; och&quot;piece&quot; som synonymer för watch.

+++

## Dokumentation

Mer information:

* [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce Användarhandbok](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] på Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
