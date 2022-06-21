---
title: Versionsinformation
description: Den senaste versionsinformationen för [!DNL Product Recommendations] från Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: 78f469dda853a6f46394d5969f879100cf22f8bb
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---

# Versionsinformation

Versionsinformationen innehåller uppdateringar av följande [!DNL Product Recommendations] moduler:

* Från om med mars 2021 [!DNL Product Recommendations] stöds nu i [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) butiker.
* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Stöd för Page Builder i [!DNL Product Recommendations] (valfri) modul: `magento/module-page-builder-product-recommendations`
* Typstöd för visuell likhetsrekommendation för [!DNL Product Recommendations] (valfri) modul: `magento/module-visual-product-recommendations`

Versionsinformationen innehåller:

* ![Nytt](../assets/new.svg) - Nya funktioner
* ![Korrigera](../assets/fix.svg) - Korrigeringar och förbättringar

Läs utvecklardokumentationen för att [läs om produktkompatibilitet](https://devdocs.magento.com/release/availability.html).

## Adobe Commerce 2.3.x och 2.4.x

## 4.0.0 av magento/product-recommendations

* ![Nytt](../assets/new.svg) - Tillagt [beredskapsindikatorer](create.md) för att visualisera utbildningsförloppet för varje rekommendationstyp.
* ![Nytt](../assets/new.svg) - Det här är en större version. Du måste [redigera](install-configure.md#update) roten `composer.json` -fil för ditt projekt. I den här versionen måste du även ange två API-nycklar när du installerar och konfigurerar Product Recommendations: [en produktionsnyckel och en sandlådenyckel](../landing/saas.md).

## 3.3.7 i magento/product-recommendations

* ![Nytt](../assets/new.svg) - Stöd för PHP 8.1 har lagts till
* ![Nytt](../assets/new.svg) - Förbättrad storleksändring av bilder så att olika stora bilder hanteras mer konsekvent i referensvisningsmallen

## 3.3.6 of magento/product-recommendations

* ![Nytt](../assets/new.svg) - Optimerad [!DNL Product Recommendations] metapaket genom att explicit visa beroenden

### 3.3.5 of magento/product-recommendations

* ![Nytt](../assets/new.svg) - Tillagt [Stöd för B2B](onboarding.md#b2bsupport) i Recommendations
* ![Nytt](../assets/new.svg) - Nya feeds har lagts till i [synkronisera katalogdata](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) till Commerce Services via kommandoraden

### 3.3.3 i magento/product-recommendations

* ![Nytt](../assets/new.svg) - Lagt till nytt [rekommendationstyper](type.md): Konvertering (visa i kundvagn), Konvertering (visa för köp) och Senast visade. Dessa nya rekommendationstyper finns i `magento/product-recommendations` modul 3.2.2 och senare.
* ![Korrigera](../assets/fix.svg) - Korrigerade ett problem där Fastly&#39;s Web Application Firewall (WAF) blockerade en cookie felaktigt
* ![Korrigera](../assets/fix.svg) - Ett problem har korrigerats där produkter som tilldelats icke-standardbutiksvyn inte visades i _Recommendations Product Preview_ när du skapar en rekommendation för den specifika butiksvyn
* ![Korrigera](../assets/fix.svg) - Ett problem har korrigerats där vissa rekommendationsenhetsnamn i Page Builder hindrade rekommendationsenheten att visas i butiken

### 3.3.2 of magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Korrigerat saknat beroende för B2B-stöd

### 3.3.1 of magento/product-recommendations

* ![Nytt](../assets/new.svg) - Stöd för B2B-kundgruppspriser har lagts till. När du anger en [prisfilter](filters.md) På en rekommendationsenhet kan B2B-kunder som är inloggade se kundgruppspriserna för produkterna som visas.

### 3.3.0 of magento/product-recommendations

* ![Nytt](../assets/new.svg) - Stöd för Adobe Client Data Layer har lagts till för att standardisera beteendedatainsamling för alla funktioner och tjänster i Adobe Commerce. Se [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) om du vill veta mer.

### 3.2.6 of magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Korrigerade ett modalt JavaScript-fel
* ![Korrigera](../assets/fix.svg) - Korrigerade ett problem där Fastly&#39;s Web Application Firewall (WAF) blockerade en cookie felaktigt

### 3.2.5 of magento/product-recommendations

* ![Nytt](../assets/new.svg) - Magento Services har bytt namn till [Commerce Services](https://docs.magento.com/user-guide/system/saas.html) och förbättrad användbarhet i Admin

### 3.2.4 of magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Korrigerade felet&quot;Det går inte att hämta data om konfigurerbara produktalternativ&quot; vid indexering av produktattribut

### 3.2.3 i magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Korrigerade felet&quot;Det gick inte att hämta data för konfigurerbara produktalternativ&quot; under katalogsynkronisering
* ![Korrigera](../assets/fix.svg) - Ett problem har korrigerats där butikskoden inte ställdes in korrekt när du aktiverade konfigurationen Lägg till butikskod i URL-adress
* ![Korrigera](../assets/fix.svg) - Förbättrad identifiering av ändringar i administratörspanelens konfiguration för att säkerställa att dessa ändringar återspeglas i data för katalogsynkronisering

### 3.2.2 av magento/product-recommendations

* ![Nytt](../assets/new.svg) - Lagt till möjlighet att [preview recommendation results](create.md) vid skapande. Du kan behöva uppdatera modulen till den senaste versionen.
* ![Nytt](../assets/new.svg) - Lagt till möjlighet att [övervaka och hantera](https://docs.magento.com/user-guide/system/catalog-sync.html) katalogsynkroniseringsprocessen från administratören.
* ![Nytt](../assets/new.svg) - Tillagt [filter](filters.md) för att styra vilka produkter som visas i rekommendationerna.
* ![Nytt](../assets/new.svg) - Lade till [Visuell likhet](type.md#visualsim) rekommendationstyp.

### 1.2.1 of magento/module-page-builder-product-recommendations for Page Builder

* ![Nytt](../assets/new.svg) - Stöd för version 3.2.0+ av `magento/product-recommendations` modul

### 3.1.0 av magento/product-recommendations

* ![Nytt](../assets/new.svg) - Lagt till möjlighet att [omsynkronisera](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) katalogen till SaaS-tjänster via kommandoraden.
* ![Nytt](../assets/new.svg) - Stöd för databastabellprefix har lagts till
* ![Korrigera](../assets/fix.svg) - Tog bort stöd för PHP 7.1

### 3.0.8 of magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Korrigerade ett problem där händelser skickades för datainsamling innan modulen konfigurerades, vilket orsakade ogiltig trafik

### 3.0.6 of magento/product-recommendations

* ![Nytt](../assets/new.svg) - **(Beta)** Inkluderar stöd för nya [Visuell likhet](type.md#visualsim) rekommendationstyp.

### 1.0.0 av magento/module-visual-product-recommendations

* ![Nytt](../assets/new.svg) - **(Beta)** [Visuell likhet](type.md#visualsim). Med _Visuell likhet_ rekommendationstyp, kan du distribuera en rekommendationsenhet på produktinformationssidan som visar produkter som visuellt liknar den produkt som visas.

### 3.0.5 of magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Korrigerade felet&quot;Det går inte att hämta produktalternativdata&quot; som kan uppstå under katalogexport.
* ![Korrigera](../assets/fix.svg) - Valutasymbolen i _Intäkter_ kolumn på _Recommendations_ Instrumentpanelen återspeglar nu korrekt den konfigurerade basvalutan.

### 3.0.4 of magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Stöd för Adobe Commerce 2.4.0 har lagts till

### 3.0.3 i magento/product-recommendations

* ![Korrigera](../assets/fix.svg) - Förbättrad symbolimplementering i butiksmall

### 1.0.4 of magento/module-page-builder-product-recommendations for Page Builder

* ![Nytt](../assets/new.svg) - Namnet på produktrekommendationen lades till när du redigerade Page Builder-innehållstypen

### 3.0.2 magento/product-recommendations

* ![Nytt](../assets/new.svg) - En statuskolumn lades till i rutnätet när rekommendationsenheter valdes i Page Builder
* ![Korrigera](../assets/fix.svg) - Ett problem med felaktiga http-/https-protokoll i produkt- och bild-URL:er har korrigerats

### 3.0.1 of magento/product-recommendations

Det här är en större version. Du måste [redigera](install-configure.md#update) projektets rotfil Composer.json.

* ![Nytt](../assets/new.svg) - Hämta [!DNL Product Recommendations] från alternativa SaaS-datautrymmen. På så sätt kan du använda produktrekommendationer som beräknas i din produktmiljö i andra icke-produktionsmiljöer. [Växla SaaS-datautrymmen](settings.md) beskriver den här funktionen ytterligare.

* ![Korrigera](../assets/fix.svg) - Korrigerade ett problem där utcheckning hämtades för kunder som använde Block Origin
* ![Korrigera](../assets/fix.svg) - Korrigerade ett problem med att skicka ovidkommande tilläggshändelser

### 1.0.3 av magento/module-page-builder-product-recommendations for Page Builder

* ![Nytt](../assets/new.svg) - Stöd för Page Builder. Med integreringen i Page Builder kan du exakt och exakt placera rekommendationsenheter på valfri plats i innehåll som skapats i Page Builder. Du kan också formatera rubrikerna och rekommendationsenheterna själva. Gå till [Page Builder](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) för mer information.

### 2.0.0 av magento/product-recommendations

* ![Nytt](../assets/new.svg) - Allmän tillgänglighetsrelease!

## Dokumentation

Mer information om [!DNL Product Recommendations] och [!DNL Product Recommendations] utveckling:

* [Användarhandbok](overview.md)
* [Dokumentation för utvecklare](https://devdocs.magento.com/recommendations/product-recs.html)
