---
title: "Onboarding Overview"
description: "[!DNL Live Search] startflöde, systemkrav, gränser och begränsningar"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Översikt över introduktion

Kom igång med att använda [!DNL Live Search] för Adobe Commerce, slutföra introduktionsprocessen för att installera tillägget, konfigurera dina API-nycklar och synkronisera katalogen.

## Startflöde

![[!DNL Live Search] introduktionsdiagram](assets/onboarding-flow.svg)

## Krav {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1/8.2
* [!DNL Composer]

### Plattformar som stöds

* Adobe Commerce on-prem (EE): 2.4.4+
* Adobe Commerce on Cloud (ECE): 2.4.4+

## Gränser och tröskelvärden

För närvarande är [!DNL Live Search] API:t för sökning/kategori har följande begränsningar och statiska gränser som stöds:

### Indexering

* Indexerar upp till 300 produktattribut per butiksvy.
* Indexerar bara produkter från Adobe Commerce-databasen.
* Produkterna måste finnas i standardkatalogen för delad katalog.
* CMS-sidor är inte indexerade.

### Fråga

* [!DNL Live Search] har inte tillgång till den fullständiga taxonomin för kategoriträdet, vilket gör att vissa sökscenarier med lagerstyrd navigering inte är tillgängliga.
* [!DNL Live Search] använder en unik GraphQL-slutpunkt för frågor för att stödja funktioner som dynamisk faceting och sökning-som-du-type. Även om den liknar [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)finns det några skillnader och vissa fält kanske inte är helt kompatibla.

Så här begränsar du kundgrupper med katalogbehörigheter:

* Produkter måste tilldelas till rotkategorin.
* Kundgruppen &quot;Inte inloggad&quot; måste ha behörigheten &quot;Tillåt&quot; för bläddring.
* Om du vill begränsa produkter till kundgruppen Ej inloggad går du till varje kategori och anger behörigheter för varje kundgrupp.

### Regler

* Högsta antal regler per butiksvy är 50.
* Det högsta antalet villkor per regel är 10.
* Det högsta antalet händelser per regel är 25.

### Synonymer

* [!DNL Live Search] kan hantera upp till 200 synonymer per butiksvy.

## Prisindexerare

Live Search-kunder kan använda nya [SaaS prisindexerare](../price-index/index.md), vilket ger snabbare prisförändringsuppdateringar och synkroniseringstid.

### Stöd för PWA

Live Search-support betraktas som betaversion eftersom inte hela PWA har testats med [!DNL Live Search]. Grundläggande funktioner som sök- och produktlistsidor fungerar i Venia, men vissa permutationer av Graphql kanske inte fungerar som de ska.

* Den aktuella betaversionen av PWA [!DNL Live Search] kräver mer bearbetningstid för att returnera sökresultat än [!DNL Live Search] med den inbyggda Commerce-butiken.
* [!DNL Live Search] i PWA stöder inte [händelsehantering](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Filtrera direkt på `description`, `name`, `short_description` stöds inte av GraphQL när det används med [PWA](https://developer.adobe.com/commerce/pwa-studio/), men de returneras med ett mer allmänt filter.

### Stöds inte för närvarande

* The [Avancerad sökning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) modulen är inaktiverad när [!DNL Live Search] installeras och länken Avancerad sökning i storefront-sidfoten tas bort.
* Flera lagerplatser används av [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) eller andra OMS-tillägg
* Produktpriserna inkluderar inte [moms](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (moms).
* [Pris](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) stöds inte i Live Search Popover och produktlistningssidwidgeten.

## Cookies

[!DNL Live Search] samlar in användarinteraktionsdata som en del av basfunktionen och cookies används för att lagra dessa data. När användaren samlar in användarinformation måste han eller hon godkänna att lagra cookies. [!DNL Live Search] och [!DNL Product Recommendations] delar dataströmmen och därmed samma cookie-mekanism. Läs mer om det i [Hantera cookie-begränsningar](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
