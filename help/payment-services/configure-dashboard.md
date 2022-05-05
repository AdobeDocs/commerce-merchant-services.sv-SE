---
title: Konfigurera på kontrollpanelen
description: Efter installationen kan du konfigurera [!DNL Payment Services] på kontrollpanelen.
role: Admin, User
level: Intermediate
exl-id: 015c5c8c-8184-45c1-932a-f4365ddf5a30
source-git-commit: 44e97a0299e980656aef557eb5c2bac9b6443452
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Konfigurera på kontrollpanelen

Du kan anpassa [!DNL Payment Services] efter behov med hjälp av konfigurationsalternativ på kontrollpanelen.

När du klickar [!UICONTROL Settings] på kontrollpanelen kan du snabbt konfigurera [!DNL Payment Services] för Adobe Commerce och Magento Open Source. Dessa konfigurationsalternativ gäller endast för miljön som anges i [!UICONTROL Payment mode] i Allmänna inställningar.

Se [[!UICONTROL General] inställningssektion](#general-settings) för mer information.

>[!IMPORTANT]
>
> Mer information om konfiguration för flera lagringsplatser eller äldre finns i [Konfigurera i administratören](configure-admin.md) ämne.

## Konfigurera betalningstjänster

Du kan aktivera [!DNL Payment Services] för din webbplats och aktivera antingen sandlådetestning eller direktbetalningar i [!UICONTROL General] inställningsavsnitt.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Instrumentpanelsvy](assets/payment-services-menu-small.png)

1. Klicka på **[!UICONTROL Settings]** längst upp till höger på sidan.

   The _[!UICONTROL General]_-avsnittet innehåller de konfigurationsalternativ som används för att ange [!DNL Payment Services] som betalningsmetod.

1. För växlingsalternativet längst upp (**[!UICONTROL Enable Payment Services as payment method]**), ställ in det på `Yes` för att aktivera [!DNL Payment Services] för er webbplats.

1. För **Betalningsläge**, ange att `Sandbox` om du fortfarande testar [!DNL Payment Services] för din butik eller `Production` om du är redo att aktivera direktbetalningar.

   >[!WARNING]
   >
   >Dina [!UICONTROL Sandbox Merchant ID] och [!UICONTROL Production Merchant ID] genereras automatiskt och finns i respektive fält när du har avslutat introduktionen för sandlådan och/eller produktionen. Ta inte bort eller ändra dessa ID:n.

1. Om du vill ändra standardinställningarna för betalningsfunktioner och butiksvisning anger du ytterligare alternativ efter behov:

   - [Kreditkortsfält](#credit-card-fields)
   - [Smarta knappar för PayPal](#paypal-smart-buttons)
   - [Knappformat](#button-style)

1. Spara ändringarna genom att klicka på **[!UICONTROL Save]** längst upp till höger på sidan.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Kreditkortsfält

The [!UICONTROL Credit Card Fields] betalningsalternativ ger en enkel och säker utcheckning av betalningsmetoder för kreditkort och betalkort.

Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

1. För **[!UICONTROL Checkout title]**, anger du text (om det behövs) för att ändra namnet på betalningsmetoden som visas under utcheckningen.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), ange **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. För **[!UICONTROL Debug Mode]**, växlar du väljaren för att aktivera felsökningsläget.
1. Spara ändringarna genom att klicka på **[!UICONTROL Save]** längst upp till höger på sidan.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Smarta knappar för PayPal

The [!DNL PayPal Smart Buttons] betalningsalternativ ger en enkel, snabb och säker utcheckningsprocess för kunden. Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

Du kan aktivera betalningsalternativen för smarta PayPal-knappar på kontrollpanelen:

1. Om du vill ändra namnet på betalningsmetoden så som visas vid utcheckning redigerar du värdet i **[!UICONTROL Checkout Title]** fält.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), ange **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. Använd växlingsväljarna för att aktivera eller inaktivera [!DNL PayPal smart button] visningsfunktioner:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** för att aktivera alternativet att visa knappen under utcheckning.

1. Ändra [Betala senare meddelanden](payments-options.md#pay-later-button) (vid behov) växlar du **[!UICONTROL Display Pay Later message]** alternativ.
1. Om du vill aktivera felsökningsläget klickar du på **[!UICONTROL Debug Mode]**,
1. Spara ändringarna genom att klicka på **[!UICONTROL Save]** längst upp till höger på sidan.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Knappformat

Du kan även konfigurera _[!UICONTROL Button style]_Alternativ för de smarta PayPal-knapparna på kontrollpanelen:

1. Ändra **[!UICONTROL Layout]**, markera `Vertical` eller `Horizontal`.
1. Om du vill aktivera tagline i en vågrät layout klickar du på **[!UICONTROL Show tagline]**.
1. Ändra **[!UICONTROL Color]** väljer du önskat färgalternativ.
1. Ändra **[!UICONTROL Shape]**, markera `Pill` eller `Rect`.
1. Om du vill aktivera knapphöjdsväljaren klickar du på **[!UICONTROL Responsive button height]**.
1. Ändra **[!UICONTROL Label]** väljer du önskat etikettalternativ.
1. Spara ändringarna genom att klicka på **[!UICONTROL Save]** längst upp till höger på sidan.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

Du kan konfigurera [!DNL PayPal Smart Buttons] i Admin eller Dashboard. Se [PayPals stilguide för knappar](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) för mer information.
