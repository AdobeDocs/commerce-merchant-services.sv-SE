---
title: "Onboarding Overview"
description: "[!DNL Live Search] startflöde, systemkrav, gränser och begränsningar"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Översikt över introduktion

Kom igång med att använda [!DNL Live Search] för Adobe Commerce, slutföra introduktionsprocessen för att installera tillägget, konfigurera dina API-nycklar och synkronisera katalogen.

## Startflöde

![[!DNL Live Search] introduktionsdiagram](assets/onboarding-flow.svg)

## Krav {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### Plattformar som stöds

* Adobe Commerce on prem (EE): 2.4.x
* Adobe Commerce on Cloud (ECE): 2.4.x

## Gränser och tröskelvärden

I nuläget är [!DNL Live Search] API:t för sökning/kategori har följande begränsningar och statiska gränser som stöds:

### Indexering

* Indexerar upp till 300 produktattribut per butiksvy.
* Indexerar bara produkter från Adobe Commerce-databasen.
* CMS-sidor är inte indexerade.

### Fråga

* [!DNL Live Search] har inte tillgång till den fullständiga taxonomin för kategoriträdet, vilket gör att vissa sökscenarier med lagerstyrd navigering inte är tillgängliga.
* [!DNL Live Search] använder en unik GraphQL-slutpunkt för frågor för att stödja funktioner som intelligent faceting och sökning-som-du-type. Även om den liknar [Magento GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)finns det några skillnader och vissa fält kanske inte är helt kompatibla just nu.

### Regler

* Högsta antal regler per butiksvy är 50.
* Det högsta antalet villkor per regel är 10.
* Det högsta antalet händelser per regel är 25.

### Synonymer

* [!DNL Live Search] kan hantera upp till 200 synonymer per butiksvy.

### PWA betaversion

* Den aktuella betaversionen av Live Search i PWA kräver mer bearbetningstid för att returnera sökresultat än Live Search i butiken.
* Betaversionen av PWA för [!DNL Live Search] stöder inte [händelsehantering](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Följande produktattribut stöds inte av GraphQL när de används i relation till betaversionen av [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Stöds inte just nu

* The [Avancerad sökning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) modulen är inaktiverad när [!DNL Live Search] installeras och länken Avancerad sökning i storefront-sidfoten tas bort.
* [Anpassade prisgrupper](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* Flera lagerplatser används av [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) eller andra OMS-tillägg
* Produktpriserna inkluderar inte [moms](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (moms).
