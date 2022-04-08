---
title: '''[!DNL Express Checkout] för Adobe Commerce Developer Information'''
description: '''[!DNL Express Checkout] utvecklarinformation."'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 46d5cae4e55a2983a2dc8c442cf5530803be65af
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# [!DNL Express Checkout] utvecklarinformation

>[!IMPORTANT]
>
> Den här funktionen är endast avsedd för användare av tidig Adobe-programvara (EAP) och är ännu inte tillgänglig för alla kunder. För närvarande begränsat till amerikanska kunder. Kontakta Adobe Commerce Support för hjälp och frågor.

Det här avsnittet innehåller information för utvecklare som har ett nära samarbete med Adobe Commerce- och Magento Open Source-koden och vill veta mer om [!DNL Express Checkout] tillägg.

## Tilläggspunkter

Använd tilläggspunkter för att anpassa [!DNL Express Checkout].

Genom att använda tilläggspunkter kan du göra anpassningar utan att ändra huvudkomponenterna i programkoden.

## Leveransinformationssteg

En tilläggspunkt kan användas för att anpassa den automatiska stegnavigeringen efter inloggning med [!DNL Bolt].

När en kund loggar in med [!DNL Bolt], är all giltig information förifylld och omdirigerad till betalningsinformationssteget för att lägga ordern. Se [utcheckningsflöde](https://experienceleague.adobe.com/docs/commerce-merchant-services/express-checkout/manage-checkout/checkout-flow.html) för mer information.

Den här tilläggspunkten förhindrar navigering till ett betalningssteg och kan vara användbar om det finns tillägg som kräver att en kund utför ytterligare åtgärder i leveranssteget. Se ett exempel nedan om hur du kan använda tilläggspunkten med en mixin:

1. Registrera en ny blandning i `require-config.js` filen finns i `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. Utöka modellen i `can-navigate-to-payment.js` filen finns i `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> Det här är ett exempel för en kund i Tyskland som vill stanna på leveransinformationssteget.

Kontrollera [[!DNL Bolt] utvecklarhjälp](https://help.bolt.com/developers/) för mer information om [!DNL Bolt] för utvecklare.
