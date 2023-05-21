---
title: "[!DNL Quick Checkout] för Adobe Commerce Developer Information"
description: "[!DNL Quick Checkout] utvecklarinformation."
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] Information för utvecklare

Här hittar du information för utvecklare som har ett nära samarbete med Adobe Commerce och [!DNL Magento Open Source] kod och vill veta mer om [!DNL Quick Checkout] tillägg.

## Förlängningspunkter

Använd tilläggspunkter för att anpassa [!DNL Quick Checkout].

Genom att använda tilläggspunkter kan du anpassa utan att ändra kärnkomponenterna i programkoden.

## Steg för leveransinformation

En tilläggspunkt kan användas för att anpassa den automatiska stegnavigeringen efter inloggning med [!DNL Bolt].

När en kund loggar in med [!DNL Bolt], all giltig information förifylls och omdirigeras till steget betalningsinformation där beställningen görs. Se [utcheckningsflöde](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) för mer information.

Denna förlängningspunkt gör det möjligt att förhindra navigering till ett betalningssteg och kan vara användbar om det finns tillägg som kräver att en kund utför ytterligare åtgärder på fraktsteget. Se ett exempel nedan på hur du kan använda tilläggspunkten med en mixin:

1. Registrera en ny blandning i `require-config.js` fil i `app/code/Vendor/ModuleName/view/frontend/`.

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

1. Utöka modellen i `can-navigate-to-payment.js` fil i `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

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
> Detta är ett exempel för en shoppare i Tyskland (DE) som vill stanna på Frakt detaljer steg.

Kontrollera [[!DNL Bolt] utvecklarhjälp](https://help.bolt.com/developers/) för mer information om [!DNL Bolt] för utvecklare.
