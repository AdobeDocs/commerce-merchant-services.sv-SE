---
title: Händelser
description: Lär dig vilka händelser som samlar in data och se den fullständiga schemadefinitionen.
source-git-commit: 566abe09b8c1b0837a833b2f8fcfe1e81bb6963d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Beacon-händelser för projekt

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

>[!NOTE]
>
> The `Sign In`, `Sign Out`, `Create Account`och `Update Account` -händelser aktiveras när en specifik åtgärd utförs. Det indikerar inte att åtgärden lyckades.
