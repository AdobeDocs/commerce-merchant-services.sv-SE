---
title: "Technical Overview"
description: "[!DNL Live Search] startflöde, systemkrav, gränser och begränsningar"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: 9b46ee98d0459b6a4cce2da51ac6308a1102ef30
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# Teknisk översikt

I det här avsnittet beskrivs tekniska krav och tips för installation och optimering [!DNL Live Search] för Adobe Commerce.

## Krav {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1/8.2
* [!DNL Composer]

### Plattformar som stöds

* Adobe Commerce on-prem (EE): 2.4.4+
* Adobe Commerce on Cloud (ECE): 2.4.4+

## Slutpunkt

[!DNL Live Search] kommunicerar via slutpunkten vid `https://catalog-service.adobe.io/graphql`.

>[!NOTE]
>
>Som [!DNL Live Search] inte har tillgång till hela produktdatabasen, [!DNL Live Search] GraphQL och Commerce core GraphQL kommer inte att ha fullständig paritet.

## Gränser och tröskelvärden

För närvarande är [!DNL Live Search] API:t för sökning/kategori har följande begränsningar och statiska gränser som stöds:

### Indexering

* [Index](indexing.md) upp till 300 produktattribut per butiksvy.
* Indexerar bara produkter från Adobe Commerce-databasen.
* CMS-sidor är inte indexerade.

### Fråga

* [!DNL Live Search] har inte tillgång till den fullständiga taxonomin för kategoriträdet, vilket gör att vissa sökscenarier med lagerstyrd navigering inte är tillgängliga.
* [!DNL Live Search] använder en unik GraphQL-slutpunkt för frågor för att stödja funktioner som dynamisk faceting och sökning-som-du-type. Även om den liknar [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)finns det några skillnader och vissa fält kanske inte är helt kompatibla.

Så här begränsar du kundgrupper med katalogbehörigheter:

* Produkter måste tilldelas till rotkategorin.
* Kundgruppen &quot;Inte inloggad&quot; måste ha behörigheten &quot;Tillåt&quot; för bläddring.
* Om du vill begränsa produkter till kundgruppen Ej inloggad går du till varje kategori och anger behörigheter för varje kundgrupp.

### Regler

* Maximalt antal sökmarknadsföringar [regler](rules.md) per butiksvy är 50.
* Kategorimarknadsföring kan ha en regel per kategori.
* Det högsta antalet villkor per regel är 10.
* Det högsta antalet händelser per regel är 25.

### Synonymer

* [!DNL Live Search] kan hantera upp till 200 [synonymer](synonyms.md) per butiksvy.

## Språkstöd

[!DNL Live Search] widgetar stöder följande språk:

* sv_SE (standard)
* de_DE
* es_MX
* fr_FR
* it_IT
* ja_JA
* nl_NL
* no_NO
* pt_PT

Om widgeten upptäcker att språkinställningen för Commerce Admin (_Lager_ > Inställningar > _Konfiguration_ > _Allmänt_ > landsalternativ) matchar ett språk som stöds, det språket som standard. I annat fall är widgetarna standard engelska.

Administratörer kan också ange språket för [sökindex](settings.md#language)för att få bättre sökresultat.

## Kategorimarknadsföring

[Kategorimarknadsföring](category-merch.md) låter dig konfigurera [!DNL Live Search] för att arbeta på produktkategorinivå.

Den här videon är en introduktion till Category Merchandising.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Databas för Widget-kod

Widgeten Produktlistsida och widgeten Sökleverantör är båda tillgängliga för hämtning från deras github-databas.

Detta gör att utvecklare kan anpassa funktionaliteten och stilen helt och hållet. Dessa användare lagrar själva koden samtidigt som de drar nytta av [!DNL Live Search] service.

* [PLP-widget](https://github.com/adobe/storefront-product-listing-page)
* [Sökfältet](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] supports [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) i Commerce (tidigare Multi-Source Inventory, eller MSI). Om du vill aktivera fullständig support måste du [uppdatera](install.md#update) beroende modul `commerce-data-export` till version 10.2.0+.

[!DNL Live Search] returnerar ett booleskt meddelande som anger om en produkt är tillgänglig i Inventory management, men inte innehåller information om vilken källa som har aktien.

## Prisindexerare

Live Search-kunder kan använda nya [SaaS prisindexerare](../price-index/index.md), vilket ger snabbare prisförändringsuppdateringar och synkroniseringstid.

## Stöd för PWA

[!DNL Live Search] fungerar med PWA Studio, men användare kan se små skillnader jämfört med andra Commerce-implementeringar. Grundläggande funktioner som sök- och produktlistsidor fungerar i Venia, men vissa permutationer av Graphql kanske inte fungerar som de ska. Det kan också finnas prestandaskillnader.

* Den nuvarande PWA-implementeringen av [!DNL Live Search] kräver mer bearbetningstid för att returnera sökresultat än [!DNL Live Search] med den inbyggda Commerce Store.
* [!DNL Live Search] i PWA stöder inte [händelsehantering](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Därför kommer sökrapporter och intelligent varuexponering att fungera.
* Filtrera direkt på `description`, `name`, `short_description` stöds inte av GraphQL när det används med [PWA](https://developer.adobe.com/commerce/pwa-studio/), men de returneras med ett mer allmänt filter.

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

## Stöds inte för närvarande

* The [Avancerad sökning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) modulen är inaktiverad när [!DNL Live Search] installeras och länken Avancerad sökning i storefront-sidfoten tas bort.
* [Priser](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) och [Specialpris](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) stöds inte i [!DNL Live Search] Widgeten Popover och Product Listing.

## Cookies

[!DNL Live Search] samlar in användarinteraktionsdata som en del av basfunktionen och cookies används för att lagra dessa data. När användaren samlar in användarinformation måste han eller hon godkänna att lagra cookies. [!DNL Live Search] och [!DNL Product Recommendations] delar dataströmmen och därmed samma cookie-mekanism. Läs mer om det i [Hantera cookie-begränsningar](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
