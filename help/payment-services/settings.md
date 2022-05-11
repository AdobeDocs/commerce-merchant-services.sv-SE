---
title: Betalningstjänster
description: After installation, you can configure [!DNL Payment Services] in the Home.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: b30c15ab808be4526424a4a3be19e3d0aedcc662
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 0%

---

# Inställningar

Du kan anpassa [!DNL Payment Services] efter dina behov med praktiska inställningar i [!DNL Payment Services] Hem.

Konfigurera [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] klicka **[!UICONTROL Settings]**. Dessa konfigurationsalternativ gäller endast för miljön som anges i _[!UICONTROL Payment mode]_i Allmänna inställningar.

Se [[!UICONTROL General] inställningssektion](#general-settings) för mer information.

>[!IMPORTANT]
>
> Mer information om konfiguration för flera lagringsplatser eller äldre finns i [Konfigurera i administratören](configure-admin.md) ämne.

## Enable Payment Services

Du kan aktivera [!DNL Payment Services] för din webbplats och aktivera antingen sandlådetestning eller direktbetalningar, i [!UICONTROL General] -avsnitt.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Home view](assets/payment-services-menu-small.png)

1. Klicka på **[!UICONTROL Settings]**. Se [Introduktion till [!DNL Payment Services] Startsida](payments-home.md) för mer information.

   The _[!UICONTROL General]_section includes settings used to enable [!DNL Payment Services] as the payment method.

1. To enable [!DNL Payment Services] as the payment method for your store, toggle (**[!UICONTROL Enable Payment Services as payment method]**) to `Yes`.

1. Om du fortfarande testar [!DNL Payment Services] för din butik, ange **Betalningsläge** till `Sandbox`. Om du är redo att aktivera livebetalningar anger du det till `Production`.

   >[!WARNING]
   >
   >Your _[!UICONTROL Sandbox Merchant ID]_and_[!UICONTROL Production Merchant ID]_ are auto-generated and present in their respectable fields when you finish onboarding for the sandbox and/or production. Ta inte bort eller ändra dessa ID:n.

1. To change the default settings for payment functions and storefront display, set the additional options as needed:

   - [Kreditkortsfält](#credit-card-fields)
   - [Smarta knappar för PayPal](#paypal-smart-buttons)
   - [Button style](#button-style)

1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

### Kreditkortsfält

The _[!UICONTROL Credit Card Fields]_settings provide a simple and secure checkout option for credit card or debit card payment methods.

See [Payments options](payments-options.md#paypal-smart-buttons) for more information.

1. To change the name of the payment method displayed during checkout, edit the value in the **[!UICONTROL Checkout title]** field.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), växla **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. Aktivera felsökningsläget genom att växla **[!UICONTROL Debug Mode]** väljare.
1. Klicka på **[!UICONTROL Save]**.

   If you try to navigate away from this view without saving your changes, a modal appears that prompts you to discard changes, keep editing, or save changes.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Smarta knappar för PayPal

The [!DNL PayPal Smart Buttons] betalningsalternativ ger en enkel, snabb och säker utcheckningsprocess för kunden. Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

Du kan aktivera och konfigurera betalningsalternativen för smarta PayPal-knappar:

1. To change the name of the payment method as shown during checkout, edit the value in the **[!UICONTROL Checkout Title]** field.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), växla **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. Använd växlingsväljarna för att aktivera eller inaktivera [!DNL PayPal smart button] visningsfunktioner:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL PayPal Pay Later enabled]**
   - **[!UICONTROL Show Venmo button]**

1. To change the [Pay Later messaging](payments-options.md#pay-later-button), toggle the **[!UICONTROL Display Pay Later message]** option.
1. Aktivera felsökningsläget genom att växla **[!UICONTROL Debug Mode]** väljare.
1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigate to **[!UICONTROL System]** > **[!UICONTROL Cache Management]** and click **[!UICONTROL Flush Cache]** to refresh all invalid caches.

#### Knappformat

You can also configure the _[!UICONTROL Button style]_options of the PayPal smart buttons:

1. Ändra **[!UICONTROL Layout]**, markera `Vertical` eller `Horizontal`.

   >[!NOTE]
   >
   > Om knappformatet är konfigurerat som `Horizontal` och din butik är konfigurerad för att visa flera smarta PayPal-knappar, du kan bara se två knappar som visas på produktsidan, utcheckningssidan och mini cart, och en knapp som visas i kundvagnen.

1. Aktivera tagline i en vågrät layout genom att växla **[!UICONTROL Show tagline]** väljare.
1. Ändra **[!UICONTROL Color]** väljer du önskat färgalternativ.
1. Ändra **[!UICONTROL Shape]**, markera `Pill` eller `Rect`.
1. Aktivera knapphöjdsväljaren genom att växla **[!UICONTROL Responsive button height]** väljare.
1. Ändra **[!UICONTROL Label]** väljer du önskat etikettalternativ.
1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

Du kan konfigurera [!DNL PayPal Smart Buttons] i Admin eller [!DNL Payment Services Home]. See [PayPal&#39;s Buttons style guide](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) for more information.
