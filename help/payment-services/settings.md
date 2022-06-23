---
title: Betalningstjänster
description: Efter installationen kan du konfigurera [!DNL Payment Services] i hemmet.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: aed9469d6acf638d86389cbf1c178fccd8d42759
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Inställningar

Du kan anpassa [!DNL Payment Services] efter dina behov med praktiska inställningar i [!DNL Payment Services] Hem.

Konfigurera [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] klicka **[!UICONTROL Settings]**. Dessa konfigurationsalternativ gäller endast för miljön som anges i _[!UICONTROL Payment mode]_i Allmänna inställningar.

Se [[!UICONTROL General] inställningssektion](#general-settings) för mer information.

>[!IMPORTANT]
>
> Mer information om konfiguration för flera lagringsplatser eller äldre finns i [Konfigurera i administratören](configure-admin.md) ämne.

## Aktivera betaltjänster

Du kan aktivera [!DNL Payment Services] för din webbplats och aktivera antingen sandlådetestning eller direktbetalningar, i [!UICONTROL General] -avsnitt.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Hemvyn](assets/payment-services-menu-small.png)

1. Klicka på **[!UICONTROL Settings]**. Se [Introduktion till [!DNL Payment Services] Startsida](payments-home.md) för mer information.

   The _[!UICONTROL General]_-avsnittet innehåller inställningar som används för att aktivera [!DNL Payment Services] som betalningsmetod.

1. Aktivera [!DNL Payment Services] som betalningsmetod för din butik, växla (**[!UICONTROL Enable Payment Services as payment method]**) till `Yes`.

1. Om du fortfarande testar [!DNL Payment Services] för din butik, ange **Betalningsläge** till `Sandbox`. Om du är redo att aktivera livebetalningar anger du det till `Production`.

   >[!WARNING]
   >
   >Dina _[!UICONTROL Sandbox Merchant ID]_och_[!UICONTROL Production Merchant ID]_ genereras automatiskt och finns i respektive fält när du är klar med introduktionen av sandlådan och/eller produktionen. Ta inte bort eller ändra dessa ID:n.

1. Välj butiksvyn i **[!UICONTROL Scope]** som du vill aktivera en betalningsmetod för.
1. Om du vill ändra standardinställningarna för betalningsfunktioner och butiksvisning anger du ytterligare alternativ efter behov:

   - [Kreditkortsfält](#credit-card-fields)
   - [Smarta knappar för PayPal](#paypal-smart-buttons)
   - [Knappformat](#button-style)

1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Kreditkortsfält

The _[!UICONTROL Credit Card Fields]_är ett enkelt och säkert alternativ för utcheckning av betalningsmetoder för kreditkort och betalkort.

Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

1. Om du vill ändra namnet på betalningsmetoden som visas vid utcheckning redigerar du värdet i **[!UICONTROL Checkout title]** fält.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), växla **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. Aktivera felsökningsläget genom att växla **[!UICONTROL Debug Mode]** väljare.

   När du aktiverar felsökningsläget skrivs extra felsökningsinformation om kreditkortsbetalningen till `var/log/payment.log` -fil. Den här informationen kan ge dig mer information om en viss betalning för att underlätta felsökning.

1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Smarta knappar för PayPal

The [!DNL PayPal Smart Buttons] betalningsalternativ ger en enkel, snabb och säker utcheckningsprocess för kunden. Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

Du kan aktivera och konfigurera betalningsalternativen för smarta PayPal-knappar:

1. Om du vill ändra namnet på betalningsmetoden så som visas vid utcheckning redigerar du värdet i **[!UICONTROL Checkout Title]** fält.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), växla **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. Använd växlingsväljarna för att aktivera eller inaktivera [!DNL PayPal smart button] visningsfunktioner:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL PayPal Pay Later enabled]**
   - **[!UICONTROL Show Venmo button]**

1. Ändra [Betala senare meddelanden](payments-options.md#pay-later-button), växlar **[!UICONTROL Display Pay Later message]** alternativ.
1. Aktivera felsökningsläget genom att växla **[!UICONTROL Debug Mode]** väljare.

   När du aktiverar felsökningsläget skrivs extra felsökningsinformation om PayPal-betalningen till `var/log/payment.log` -fil. Den här informationen kan ge dig mer information om en viss betalning för att underlätta felsökning.

1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

#### Knappformat

Du kan även konfigurera _[!UICONTROL Button style]_alternativ för smarta PayPal-knappar:

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

Du kan konfigurera [!DNL PayPal Smart Buttons] i Admin eller [!DNL Payment Services Home]. Se [PayPals stilguide för knappar](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) för mer information.
