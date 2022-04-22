---
title: Översikt över introduktion
description: Live Search - introduktionsflöde, systemkrav, gränser och begränsningar
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: f2934746c327528d5d52f2ae356afe303ff9b81b
workflow-type: tm+mt
source-wordcount: '337'
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

* Indexerar upp till 300 produktattribut per butiksvy
* Indexerar endast produkter från Adobe Commerce-databasen
* Indexerar inte CMS-sidor

### Frågebegränsningar

* [!DNL Live Search] har inte tillgång till den fullständiga taxonomin för kategoriträdet, vilket gör att vissa sökscenarier med lagerstyrd navigering inte är tillgängliga.
* [!DNL Live Search] använder en unik GraphQL-slutpunkt för frågor för att stödja funktioner som intelligent faceting och sökning-som-du-type. Även om den liknar [Magento GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)finns det några skillnader och vissa fält kanske inte är helt kompatibla just nu.

### PWA betaversion

* Den aktuella betaversionen av Live Search i PWA kräver mer bearbetningstid för att returnera sökresultat än Live Search i butiken.
* Betaversionen av PWA för [!DNL Live Search] stöder inte [händelsehantering](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* Följande produktattribut stöds inte av GraphQL när de används i relation till betaversionen av [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Stöds inte just nu

* The [Avancerad sökning](https://docs.magento.com/user-guide/catalog/search-advanced.html) modulen är inaktiverad när [!DNL Live Search] installeras och länken Avancerad sökning i storefront-sidfoten tas bort.
* [Kundgrupper](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Anpassade prisgrupper](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Flera lagerplatser används av [MCOM](https://docs.magento.com/user-guide/mcom.html) eller andra OMS-tillägg
* [Integrerade B2B-funktioner](https://business.adobe.com/products/magento/b2b-ecommerce.html)
* Produktpriserna inkluderar inte [moms](https://docs.magento.com/user-guide/tax/vat.html) (moms).
* Ej lagrade produkter visas i sökresultat oavsett [Alternativ för Stock](https://docs.magento.com/user-guide/catalog/inventory-options-global.html) konfiguration.
