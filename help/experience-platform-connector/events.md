---
title: Händelser
description: Lär dig vilka händelser som samlar in data och se den fullständiga schemadefinitionen.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 15b7a8be65e5063606bb58755d0719b0ca54de37
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Experience Platform Connector Events

Följande listar [!DNL Commerce] händelser som är tillgängliga när du installerar anslutningstillägget för Experience Platform. De data som dessa händelser samlar in skickas till Adobe Experience Platform. Du kan också skapa [anpassade händelser](custom-events.md) för att samla in ytterligare uppgifter som inte lämnats ut.

Klicka på händelsenamnet för att se den fullständiga schemadefinitionen.

| Händelse | Typ |
|---|---|
| [Lägg i kundvagnen](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | Storefront |
| [Visa kundvagn](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | Storefront |
| [Visa sida](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | Storefront |
| [Visa produkt](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | Storefront |
| [Starta utcheckning](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | Storefront |
| [Fullständig utcheckning](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | Storefront |
| [Logga in](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | Profil |
| [Logga ut](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | Profil |
| [Skapa konto](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | Profil |
| [Redigera konto](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | Profil |
| [Sökning har skickats](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts) | Sök |
| [Mottaget söksvar](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts) | Sök |

>[!NOTE]
>
> The `Sign In`, `Sign Out`, `Create Account`och `Update Account` -händelser aktiveras när en specifik åtgärd utförs. Det indikerar inte att åtgärden lyckades.
