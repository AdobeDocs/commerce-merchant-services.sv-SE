---
title: '''[!DNL Product Recommendations] Versionsinformation'
description: Den senaste versionsinformationen för [!DNL Product Recommendations] från Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 76fb723c2269cfc2af197e7facc588099be8a39f
workflow-type: tm+mt
source-wordcount: '1329'
ht-degree: 0%

---

# [!DNL Product Recommendations] Versionsinformation

Versionsinformationen innehåller uppdateringar av följande [!DNL Product Recommendations] moduler:

* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Stöd för Page Builder i [!DNL Product Recommendations] (valfri) modul: `magento/module-page-builder-product-recommendations`
* Typstöd för visuell likhetsrekommendation för [!DNL Product Recommendations] (valfri) modul: `magento/module-visual-product-recommendations`

Support ges för den aktuella större versionen. Versionsinformation för äldre versioner finns som referens.
Versionsinformationen innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigera](../assets/fix.svg) Korrigeringar och förbättringar
![Fel](../assets/bug.svg) Kända fel

Läs utvecklardokumentationen för att [läs om produktsupport](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Uppdateringar av värdtjänster

Dessa anteckningar beskriver uppdateringar som publicerats utanför en versionshanteringsversion eller förbättringar av värdtjänsten.

+++Värdbaserade tjänstuppdateringar

_18 juli 2023_

![Nytt](../assets/new.svg) [!DNL Product Recommendations] har nu en GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) fråga.

_25 april 2023_

![Nytt](../assets/new.svg) [!DNL Product Recommendations] kan nu dra nytta av [SaaS-prisindexering](../price-index/price-indexing.md).

+++

## Aktuell huvudversion

### 6.0.2 of magento/product-recommendations

_9 maj 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Ett problem har korrigerats där användaren klickade på **[!DNL Add to Cart]** på en enkel produkt i en Recommendations-produktenhet som dirigerade om kunden till hemsidan istället för att stanna kvar på den aktuella sidan.
![Fel](../assets/bug.svg) Det finns ett valideringsfel som orsakas av `referenceBlock` -elementet i `ProductRecommendations Layout` XML-fil

### Tidigare versioner

### 6.0.1 of magento/product-recommendations

_19 mars 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Stöd för PHP 8.3 har lagts till.

### 6.0.0 av magento/product-recommendations

_22 februari 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) The [!DNL Catalog Sync Dashboard] är nu [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Den här förbättrade instrumentpanelen ger insikter i dataströmmar för [!DNL Product Recommendations], [!DNL Live Search]och [!DNL Catalog Service].
![Korrigera](../assets/fix.svg) Korrigerat ett problem som orsakade utcheckningsfel för [!DNL Product Recommendations].

+++5.0.0 och tidigare

### 5.0.1 of magento/product-recommendations

_15 september 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Nya moduler har lagts till för [Saas prisindexerare](../price-index/price-indexing.md).
![Nytt](../assets/new.svg) Nya moduler för dataexport har lagts till som stöd för export av fler produkttyper, inklusive paketerade produkter och presentkort.
![Korrigera](../assets/fix.svg) Tabellstorleken för Produkterna och prisflödena har reducerats avsevärt. Tabeller `catalog_data_exporter_products` och `catalog_data_exporter_product_prices` en betydande minskning av storleken.

#### Kända begränsningar

* The `websiteCode` värdet returneras felaktigt om det innehåller ett understreck (_).

### 5.0.0 av magento/product-recommendations

_20 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Uppdaterat [!DNL Product Recommendations] för Adobe Commerce 2.4.6.
![Nytt](../assets/new.svg) Det här är en större version. [Redigera](install-configure.md#update) roten `composer.json` -fil för ditt projekt.
![Nytt](../assets/new.svg) [!DNL Product Recommendations] nu stöder fullt [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) i Commerce (tidigare Multi-Source Inventory eller MSI). Om du vill aktivera fullständig support måste du [uppdatera](install-configure.md#update) beroende modul `commerce-data-export` till version 10.2.0+.

### 4.0.1 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Tidigare [!DNL Product Recommendations] skulle visa ett fel när visningsvalutan växlades till en annan valuta än standardvalutan. Växling av valutor fungerar nu korrekt.

### 4.0.0 av magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Tillagd [beredskapsindikatorer](create.md) för att visualisera utbildningsförloppet för varje rekommendationstyp.
![Nytt](../assets/new.svg) Det här är en större version. [Redigera](install-configure.md#update) roten `composer.json` -fil för ditt projekt. Den här versionen kräver också att du tillhandahåller två API-nycklar när du installerar och konfigurerar [!DNL Product Recommendations]: [en produktionsnyckel och en sandlådenyckel](../landing/saas.md).

#### Kända begränsningar

* The `websiteCode` värdet returneras felaktigt om det innehåller ett understreck (_).

### 3.3.7 i magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Stöd för PHP 8.1 har lagts till
![Nytt](../assets/new.svg) Förbättrad storleksändring av bilder så att bildstorleksändring hanteras mer konsekvent i referensvisningsmallen

### 3.3.6 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Optimerad [!DNL Product Recommendations] metapaket genom att explicit visa beroenden

### 3.3.5 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Tillagd [Stöd för B2B](onboarding.md#b2bsupport) in [!DNL Product Recommendations]
![Nytt](../assets/new.svg) Nya feeds har lagts till [synkronisera katalogdata](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) till Commerce Services via kommandoraden

### 3.3.3 i magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Lagt till ny [rekommendationstyper](type.md): Konvertering (visa i kundvagn), konvertering (visa till köp) och Senast visade. Dessa nya rekommendationstyper finns i `magento/product-recommendations` modul 3.2.2 och senare.
![Korrigera](../assets/fix.svg) Ett problem har korrigerats där Fast&#39;s Web Application Firewall (WAF) felaktigt blockerade en cookie
![Korrigera](../assets/fix.svg) Ett problem har korrigerats där produkter som tilldelats icke-standardbutiksvyn inte visades i _Recommendations Product Preview_ när du skapar en rekommendation för den specifika butiksvyn
![Korrigera](../assets/fix.svg) Ett problem har korrigerats där vissa rekommendationsenhetsnamn i Page Builder hindrade rekommendationsenheten att visas i butiken

### 3.3.2 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Ett saknat beroende för B2B-stöd har korrigerats

### 3.3.1 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Ytterligare stöd för B2B-kundgruppspriser. När du anger en [prisfilter](filters.md) På en rekommendationsenhet kan B2B-kunder som är inloggade se kundgruppspriserna för produkterna som visas.

### 3.3.0 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Stöd för Adobe Client Data Layer har lagts till för att standardisera beteendedatainsamling för alla funktioner och tjänster i Adobe Commerce. Se [readme](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) om du vill veta mer.

### 3.2.6 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Korrigerat ett JavaScript-modalt fel
![Korrigera](../assets/fix.svg) Ett problem har korrigerats där Fast&#39;s Web Application Firewall (WAF) felaktigt blockerade en cookie

### 3.2.5 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Magento Services har bytt namn till [Commerce Services](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) och förbättrad användbarhet i Admin

### 3.2.4 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Korrigerade felet&quot;Det går inte att hämta data om konfigurerbara produktalternativ&quot; vid indexering av produktattribut

### 3.2.3 i magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Korrigerade felet&quot;Det gick inte att hämta data för konfigurerbara produktalternativ&quot; under katalogsynkronisering
![Korrigera](../assets/fix.svg) Ett problem har korrigerats där lagringskoden inte ställdes in korrekt när du aktiverade konfigurationen Lägg till butikskod i URL
![Korrigera](../assets/fix.svg) Förbättrad identifiering av ändringar i administratörspanelens konfiguration för att säkerställa att dessa ändringar återspeglas i data för katalogsynkronisering

### 3.2.2 av magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Lagt till möjlighet att [preview recommendation results](create.md) vid skapande. Du kan behöva uppdatera modulen till den senaste versionen.
![Nytt](../assets/new.svg) Lagt till möjlighet att [övervaka och hantera](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) katalogsynkroniseringsprocessen från administratören.
![Nytt](../assets/new.svg) Tillagd [filter](filters.md) för att styra vilka produkter som visas i rekommendationerna.
![Nytt](../assets/new.svg) Lagt till [Visuell likhet](type.md#visualsim) rekommendationstyp.

### 1.2.1 of magento/module-page-builder-product-recommendations for Page Builder

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Stöd för version 3.2.0+ av `magento/product-recommendations` modul

### 3.1.0 av magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Lagt till möjlighet att [omsynkronisera](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) katalogen till SaaS-tjänster via kommandoraden.
![Nytt](../assets/new.svg) Stöd för databastabellprefix har lagts till
![Korrigera](../assets/fix.svg) Tog bort stöd för PHP 7.1

### 3.0.8 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Ett problem där händelser skickades för datainsamling innan modulen konfigurerades har korrigerats, vilket orsakade ogiltig trafik

### 3.0.6 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) **(Beta)** Stöd för nya [Visuell likhet](type.md#visualsim) rekommendationstyp.

### 1.0.0 av magento/module-visual-product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) **(Beta)** [Visuell likhet](type.md#visualsim). Med _Visuell likhet_ rekommendationstyp, kan du distribuera en rekommendationsenhet på produktinformationssidan som visar produkter som visuellt liknar den produkt som visas.

### 3.0.5 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Korrigerade felet&quot;Det gick inte att hämta produktalternativdata&quot; som kan uppstå under katalogexport.
![Korrigera](../assets/fix.svg) Valutasymbolen i _Intäkter_ kolumn på _[!DNL Product Recommendations]_Instrumentpanelen återspeglar nu korrekt den konfigurerade basvalutan.

### 3.0.4 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Stöd för Adobe Commerce 2.4.0

### 3.0.3 i magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) Förbättrad symbolimplementering i butiksmallen

### 1.0.4 of magento/module-page-builder-product-recommendations for Page Builder

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Namn på produktrekommendation har lagts till vid redigering av Page Builder-innehållstypen

### 3.0.2 magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) En statuskolumn lades till i rutnätet när rekommendationsenheter valdes i Page Builder
![Korrigera](../assets/fix.svg) Ett problem med felaktiga http-/https-protokoll i produkt- och bild-URL:er har korrigerats

### 3.0.1 of magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

Det här är en större version. [Redigera](install-configure.md#update) projektets rotfil Composer.json.

![Nytt](../assets/new.svg) Hämta [!DNL Product Recommendations] från alternativa SaaS-datautrymmen. På så sätt kan du använda [!DNL Product Recommendations] beräknas i din produktmiljö i andra icke-produktionsmiljöer. [Växla SaaS-datautrymmen](settings.md) beskriver den här funktionen ytterligare.

![Korrigera](../assets/fix.svg) Ett problem där utcheckningen hämtades för shoppare som använder Block Origin har korrigerats
![Korrigera](../assets/fix.svg) Ett problem som skickade ovidkommande tilläggshändelser har korrigerats

### 1.0.3 av magento/module-page-builder-product-recommendations for Page Builder

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Stöd för Page Builder. Med integreringen i Page Builder kan du exakt och exakt placera rekommendationsenheter på valfri plats i innehåll som skapats i Page Builder. Du kan också formatera rubrikerna och rekommendationsenheterna själva. Gå till [Page Builder](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) för mer information.

### 2.0.0 av magento/product-recommendations

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Allmän tillgänglighetsrelease!

+++

## Dokumentation

Mer information om [!DNL Product Recommendations] och [!DNL Product Recommendations] utveckling:

* [Användarhandbok](overview.md)
* [Dokumentation för utvecklare](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
