---
title: Översikt över introduktion
description: Live Search - introduktionsflöde, systemkrav, gränser och begränsningar
source-git-commit: 6220824c6032a33a760fe5c2bb5d2346e00a074b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Översikt över introduktion

Om du vill komma igång med Live Search för Adobe Commerce måste du slutföra några startsteg för att installera tillägget, konfigurera API-nycklarna och synkronisera katalogen.

## Startflöde

![Live Search - introduktionsdiagram](assets/onboarding-flow.svg)

## Krav {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3/7.4
* [!DNL Composer]

### Plattformar som stöds

* Adobe Commerce on prem (EE): 2.4.x
* Adobe Commerce on Cloud (ECE): 2.4.x

## Gränser och tröskelvärden

För närvarande har API:t för sökning/kategori i Live Search följande begränsningar och statiska gränser som stöds:

### Indexering

* Indexerar upp till 300 produktattribut per butiksvy
* Indexerar endast produkter från Adobe Commerce-databasen
* Indexerar inte CMS-sidor

### Frågebegränsningar

* Livesökning har inte tillgång till hela taxonomin för kategoriträdet, vilket gör att vissa scenarier för navigering i flera lager inte är tillgängliga.
* Live Search använder en unik GraphQL-slutpunkt för frågor för att stödja funktioner som intelligent Faceeting och sökning-som-du-typ. Även om den liknar [Magento GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)finns det några skillnader och vissa fält kanske inte är helt kompatibla just nu.

### PWA betaversion

* Betaversionen av PWA för Live Search stöder inte [händelsehantering](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* Följande produktattribut stöds inte av GraphQL när de används i relation till betaversionen av [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Stöds inte just nu

* The [Avancerad sökning](https://docs.magento.com/user-guide/catalog/search-advanced.html) -modulen inaktiveras när Live Search installeras och länken Avancerad sökning i storefront-sidfoten tas bort.
* [Kundgrupper](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Anpassade prisgrupper](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Flera lagerplatser används av [MCOM](https://docs.magento.com/user-guide/mcom.html) eller andra OMS-tillägg
* [Integrerade B2B-funktioner](https://business.adobe.com/products/magento/b2b-ecommerce.html)
