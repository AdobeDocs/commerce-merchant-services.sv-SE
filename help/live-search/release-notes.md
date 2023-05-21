---
title: '''[!DNL Live Search] Versionsinformation'
description: "Den senaste versionsinformationen för [!DNL Live Search] från Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# [!DNL Live Search] Versionsinformation

I versionsinformationen beskrivs de senaste versionerna av [!DNL Live Search].
Support ges för den aktuella större versionen. Versionsinformation för äldre versioner finns som referens.
Bland uppdateringarna finns:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigera](../assets/fix.svg) Korrigeringar och förbättringar
![Fel](../assets/bug.svg) Kända fel


_25 april 2023_

![Nytt](../assets/new.svg) Live Search-kunder kan nu utnyttja nya [SaaS prisindexerare](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_14 mars 2023_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

### Nya funktioner

* Produktartikelkort i regelförhandsgranskning
* [Widgeten Produktlistsida](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [Kategorifiltreringsalternativ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* Lagt till möjlighet att dra och släppa för att skapa fäst-händelser
* Nya åtgärder för Fäst:
   * Fäst på plats - Fäst knappen för att skapa Fäst-händelse med ett klick
   * Fäst överst - Placerar produkten på första plats
   * Fäst längst ned - Placerar produkten längst ned i resultaten
   * Plocka upp en händelse med ett klick
* [Intelligent rankning av regler](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### Uppdateringar

* Konfigurera regler sorterar nu positioner automatiskt
* Förhandsgranskning uppdateras nu när en befintlig händelse tas bort
* Regler utan händelser kan sparas
* Ta bort funktionsväljaren &quot;Välj typ&quot;
* Ny redigeringsstatus för ej sparade regler har lagts till

### Korrigeringar

* Ett serverfel har korrigerats när en oavslutad händelse inträffar när filen sparades
* Korrekt borttagning av en specifik händelse vid flera händelser
* En befintlig regelhändelse som inte uppdaterades när en ny händelse har lagts till har åtgärdats
* Korrigerat den andra&quot;Redigera&quot;-klickningen från detaljer, [!DNL Live Search] sida som behöver laddas om
* Synonymer: Ett problem har korrigerats när en användare klickade bort från indata och de inte kunde återställa fokus till fältet
* Andra mindre felkorrigeringar och prestandauppdateringar


* ![Fel](../assets/bug.svg) - Rankning efter&quot;Rekommenderas för dig&quot; stöds endast i Live Search-widgetar. Det stöds inte med standardsökfunktionen för Luma och PWA.
* ![Fel](../assets/bug.svg) - Egna prisattributaspekter återges inte korrekt i Luma, men API:t filtrerar på dem korrekt.

Handlare måste uppgradera [!DNL Live Search] tilläggsversion >= 3.0.1 för att komma åt dessa funktioner.

Vi rekommenderar att du uppgraderar och testar innan du går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

## Tidigare versioner

+++2.0.5 och tidigare

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

* ![Korrigera](../assets/fix.svg) - Live Search genererar ett fel när SDK-resurser inte är tillgängliga på grund av nätverksproblem. Det här felet har åtgärdats.

Handläggarna måste uppgradera Live Search-tilläggsversionen >= 2.0.5 för att få tillgång till dessa funktioner.

Vi rekommenderar att du uppgraderar och testar innan du går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Live Search har nu stöd för filtrering med inställningen &quot;Visa ej i Stock-produkter&quot; i administratören. Om Visa utanför Stock-produkter är inställt på false, `inStock = true` läggs till i filtret.
![Korrigera](../assets/fix.svg) För att förbättra prestanda har blocket Förslag tagits bort från popup-fönstret Live Search. Data skickas fortfarande via GraphQL om du vill ersätta funktionen.
![Korrigera](../assets/fix.svg) `categories` och `categoryPath` har ersatts `categoryIds` för kategorifiltrering. Läs mer i [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) ämne.
![Korrigera](../assets/fix.svg) Tidigare fick en användare som är knuten till ett B2B-företag en felaktig kundgruppskod när de gjorde sökningar. Live Search returnerar nu korrekt värde.
![Korrigera](../assets/fix.svg) Tidigare returneras ett fel om du söker efter en term som inte finns. Felet är nu åtgärdat.

Handlare måste uppgradera [!DNL Live Search] tilläggsversion >= 2.0.4 för att komma åt dessa funktioner.

Man rekommenderar att man uppgraderar och testar innan man går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Live Search har nu stöd för B2B-funktioner genom att man följer kategoribehörigheter, delade kataloger och kundgruppsspecifika priser.

Handlare måste uppgradera [!DNL Live Search] tilläggsversion >= 2.0.3 för att komma åt dessa funktioner.

Man rekommenderar att man uppgraderar och testar innan man går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

Befintlig [!DNL Live Search] installationerna måste uppgraderas till [!DNL Live Search] 2.0.0 för att utnyttja följande nya funktioner, korrigeringar och förbättringar:

![Nytt](../assets/new.svg) [!DNL Live Search] har nu stöd för PHP 8.1 för installationer som kör Adobe Commerce 2.4.4.
![Nytt](../assets/new.svg) The `Magento_ElasticsearchCatalogPermissionsGraphQl` läggs till i listan med moduler som är inaktiverade under installationen.
![Nytt](../assets/new.svg) Antalet tillgängliga rader i [[!DNL storefront popover]](quick-tour.md) kan konfigureras från *Administratör*.
![Nytt](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) kompatibilitet för [!DNL Live Search].
![Nytt](../assets/new.svg) The [!DNL Live Search] installationsprocessen uppdateras med avancerade processändringar.
![Korrigera](../assets/fix.svg) [Avancerad sökning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) länk borttagen från sidfoten i butiken.
![Fel](../assets/bug.svg) Följande produktattribut stöds inte av [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) vid användning i samband med betaversionen av PWA: `description`, `name`, `short_description`
![Fel](../assets/bug.svg) Betaversionen av PWA för [!DNL Live Search] stöder inte [händelsehantering](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Korrigera](../assets/fix.svg) [Anpassat prisattribut](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) returnerar inte längre ett fel när det konfigureras som [facet]({% link live-search/facets-add.md %}).
![Korrigera](../assets/fix.svg) Korrigerat problem som orsakade att ett fel uppstod när inget [valutasymbol](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) är tillgängligt.
![Korrigera](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) nu visas [Specialpris](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (lägsta slutpris) om tillgängligt.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) [Prestanda](performance.md) på kontrollpanelen för rapporter ger insikt i söktermer som kunderna använder.
![Nytt](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) ger tillgång till ett gemensamt datalager med händelsepublicerings- och prenumerationstjänster samt mätvärden.
![Korrigera](../assets/fix.svg) The [[!DNL Storefront popover]](storefront-popover.md) har en ny `active` klassen för `.search-autocomplete` behållare som styr synlighet.
![Korrigera](../assets/fix.svg) I butiken finns [Sökvillkor](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) sidfotslänken tas bort och dess cache inaktiveras för [!DNL Live Search] installationer.
![Fel](../assets/bug.svg) Patch for Search-kort hanterar dubblettprodukter.
![Fel](../assets/bug.svg) [!DNL Live Search] supports [single-source](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) (fysisk) lagerplatser med flera (virtuell) [lager](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Flera lagerkällor stöds inte nu.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) visar föreslagna produkter och miniatyrbilder av de bästa sökresultaten när kunderna skriver frågor i sökrutan.
![Nytt](../assets/new.svg) Handel *Administratör* -sessionen förblir öppen under längre perioder av tangentbordsinaktivitet
![Nytt](../assets/new.svg) [!DNL Live Search] aktiveras automatiskt efter introduktionen
![Korrigera](../assets/fix.svg) Inledande indexeringstid är mindre än en timme
![Korrigera](../assets/fix.svg) Stegvisa produktuppdateringar nära realtid (efter installation och installation)
![Korrigera](../assets/fix.svg) Sorterbara kolumner i synonymredigeraren
![Korrigera](../assets/fix.svg) [!DNL Live Search] returnerar inte längre ett fel om sökvillkoren innehåller ett tomt sorteringsordningsvärde
![Korrigera](../assets/fix.svg) Intervallfiltrering bryts inte längre om attributkoder innehåller strängarna &quot;to&quot; eller &quot;from&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Fel](../assets/bug.svg) The [!DNL Live Search] tjänsten stöder endast [basvaluta](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) av Adobe Commerce-installationen.
![Fel](../assets/bug.svg) När du lägger till en fasett uppdateras inte produktattributsmatningen korrekt om den anges till `Update on Save`. För att undvika det här problemet, gå till [Indexhantering](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) och ange produktattribut för feed till `Update by Schedule`.
![Fel](../assets/bug.svg) [!DNL Live Search] synonymer definieras per butiksvy, men lagras för närvarande per webbplats och identifieras med en kombination av `environmentId` och `storeViewCode`. Därför delar alla webbplatser och vyer i Adobe Commerce-installationen synonymer. Den senast skapade uppsättningen synonymer för butiksvyn har företräde.
![Fel](../assets/bug.svg) Om en synonymterm innehåller flera ord behandlas varje ord som en separat synonym. Om du till exempel definierar&quot;tidsbit&quot; som en synonym till&quot;watch&quot;, behandlas både&quot;time&quot; och&quot;piece&quot; som synonymer till&quot;watch&quot;.

+++

## Dokumentation

Mer information:

* [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce Användarhandbok](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] på Marketplace](https://marketplace.magento.com/magento-live-search.html)
