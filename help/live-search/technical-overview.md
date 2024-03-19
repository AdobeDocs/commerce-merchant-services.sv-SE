---
title: "Technical Overview"
description: "[!DNL Live Search] startflöde, systemkrav, gränser och begränsningar"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: e8d4215b1f16f1cb34783674cabc046dec135729
workflow-type: tm+mt
source-wordcount: '1023'
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

Som [!DNL Live Search] inte har tillgång till hela produktdatabasen, [!DNL Live Search] GraphQL och Commerce core GraphQL kommer inte att ha fullständig paritet.

Vi rekommenderar att du anropar SaaS API:er direkt - särskilt katalogtjänstslutpunkten.

* Öka prestanda och minska processorbelastningen genom att kringgå Commerce-databasen/Graphql-processen
* Utnyttja [!DNL Catalog Service] federation att ringa [!DNL Live Search], [!DNL Catalog Service]och [!DNL Product Recommendations] från en enda slutpunkt.

I vissa fall är det kanske bättre att ringa [!DNL Catalog Service] för produktinformation och liknande. Se [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) för mer information.

Om du har en anpassad headless-implementering kan du ta en titt på [!DNL Live Search] referensimplementeringar:

* [PLP-widget](https://github.com/adobe/storefront-product-listing-page)
* [Livesökfält](https://github.com/adobe/storefront-search-as-you-type)

Om du inte använder standardkomponenterna, som Sökadapter eller widgetar på Luma, eller AEM CIF widgetar, kommer inte händelser (klickströmsdata som matar Adobe Sensei för intelligent marknadsföring och prestandamått) att fungera som de ska och kräver anpassad utveckling för att implementera headless-händelser.
Den senaste versionen av [!DNL Live Search] används redan [!DNL Catalog Service].

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

## Kategorimarknadsföring

[Kategorimarknadsföring](category-merch.md) låter dig konfigurera [!DNL Live Search] för att arbeta på produktkategorinivå.

Den här videon är en introduktion till Category Merchandising.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Databas för Widget-kod

Widgeten Produktlistsida och widgeten för Live-sökfält är båda tillgängliga för hämtning från deras github-databas.

Detta gör att utvecklare kan anpassa funktionaliteten och stilen helt och hållet. Dessa användare lagrar själva koden samtidigt som de drar nytta av [!DNL Live Search] service.

* [PLP-widget](https://github.com/adobe/storefront-product-listing-page)
* [Sökfältet](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] supports [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) i Commerce (tidigare Multi-Source Inventory, eller MSI). Om du vill aktivera fullständig support måste du [uppdatera](install.md#update) beroende modul `commerce-data-export` till version 10.2.0+.

[!DNL Live Search] returnerar ett booleskt meddelande som anger om en produkt är tillgänglig i Inventory management, men inte innehåller information om vilken källa som har aktien.

## Prisindexerare

Live Search-kunder kan använda nya [SaaS prisindexerare](../price-index/price-indexing.md), vilket ger snabbare prisförändringsuppdateringar och synkroniseringstid.

## Prisstöd

Live Search-widgetar har stöd för de flesta, men inte alla, pristyper som stöds av Adobe Commerce.

För närvarande stöds baspriser. Avancerade priser som inte stöds är:

* Kostnad
* Lägsta kampanjpris

Titta på [API-nät](../catalog-service/mesh.md) för mer komplexa prisberäkningar.

Prisformatet stöder de nationella konfigurationsinställningarna i Commerce-instansen: *Lager* > Inställningar > *Konfiguration* > Allmänt > *Allmänt* > Lokala alternativ > Språk.

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

* The [Avancerad sökning](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) modulen är inaktiverad när [!DNL Live Search] installeras och länken Avancerad sökning i storefront-sidfoten tas bort.
* [Priser](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) och [Specialpris](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) stöds inte i [!DNL Live Search] fält och sidwidget för produktlista.

## Cookies

[!DNL Live Search] samlar in användarinteraktionsdata som en del av basfunktionen och cookies används för att lagra dessa data. När användaren samlar in användarinformation måste han eller hon godkänna att lagra cookies. [!DNL Live Search] och [!DNL Product Recommendations] delar dataströmmen och därmed samma cookie-mekanism. Läs mer om det i [Hantera cookie-begränsningar](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
