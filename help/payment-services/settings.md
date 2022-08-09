---
title: Betalningstjänster
description: Efter installationen kan du konfigurera [!DNL Payment Services] i hemmet.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 60d04755b29f107a0543bd71e19ca5b2b6997b4d
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 0%

---

# Inställningar

Du kan anpassa [!DNL Payment Services] efter dina behov med praktiska inställningar i [!DNL Payment Services] Hem.

Konfigurera [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] klicka **[!UICONTROL Settings]**. Dessa konfigurationsalternativ gäller endast för miljön som anges i _[!UICONTROL Payment mode]_fält i_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> Mer information om konfiguration för flera lagringsplatser eller äldre finns i [Konfigurera i administratören](configure-admin.md) ämne.

## Aktivera betaltjänster

Du kan aktivera [!DNL Payment Services] för din webbplats och aktivera antingen sandlådetestning eller direktbetalningar, i [!UICONTROL General] -avsnitt.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Hemvyn](assets/payment-services-menu-small.png)

1. Klicka på **[!UICONTROL Settings]**. Se [Introduktion till [!DNL Payment Services] Startsida](payments-home.md) för mer information.

   The _[!UICONTROL General]_-avsnittet innehåller inställningar som används för att aktivera [!DNL Payment Services] som betalningsmetod.

1. Aktivera [!DNL Payment Services] som betalningsmetod för din butik i _[!UICONTROL General]_sektion, växla (**[!UICONTROL Enable Payment Services as payment method]**) till `Yes`.

1. Om du fortfarande testar [!DNL Payment Services] för din butik, ange **Betalningsläge** till `Sandbox`. Om du är redo att aktivera livebetalningar anger du det till `Production`.

   >[!NOTE]
   >
   >Dina _[!UICONTROL Sandbox Merchant ID]_och_[!UICONTROL Production Merchant ID]_ genereras automatiskt och finns i respektive fält när du är klar med introduktionen av sandlådan och/eller produktionen.

1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

Du kan nu fortsätta att ändra standardinställningarna för [betalningsalternativ](#configure-payment-options) funktioner och butiksvisning.

### Allmänna konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Enable] | webbplats | Aktivera eller inaktivera [!DNL Payment Services] för er webbplats. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | butiksvy | Ange metod, eller miljö, för din butik. Alternativ: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | butiksvy | Ditt handlar-ID för sandlådan, som genereras automatiskt vid introduktion av sandlådor. |
| [!UICONTROL Production Merchant ID] | butiksvy | Ditt handlar-ID för produktion, som genereras automatiskt när sandlådan introduceras. |

## Konfigurera betalningsalternativ

Nu när du har aktiverat Betalningstjänster för din webbplats kan du ändra standardinställningarna för betalningsfunktioner och butiksvisning.

### Kreditkortsfält

The _[!UICONTROL Credit Card Fields]_är ett enkelt och säkert alternativ för utcheckning av betalningsmetoder för kreditkort och betalkort.

Se [Betalningsalternativ](payments-options.md#credit-card-fields) för mer information.

1. Välj butiksvyn i **[!UICONTROL Scope]** som du vill aktivera en betalningsmetod för.
1. Om du vill ändra namnet på betalningsmetoden som visas vid utcheckning redigerar du värdet i **[!UICONTROL Checkout title]** fält.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), växla **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. Aktivera felsökningsläget genom att växla **[!UICONTROL Debug Mode]** väljare.
1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

#### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |

### Betalningsknappar

The [!DNL PayPal Smart Buttons] betalningsalternativ ger en enkel, snabb och säker utcheckningsprocess för kunden. Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

Du kan aktivera och konfigurera betalningsalternativen för smarta PayPal-knappar:

1. Välj butiksvyn i **[!UICONTROL Scope]** som du vill aktivera en betalningsmetod för.
1. Om du vill ändra namnet på betalningsmetoden så som visas vid utcheckning redigerar du värdet i **[!UICONTROL Checkout Title]** fält.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), växla **[!UICONTROL Payment action]** till `Authorize` eller `Authorize and Capture`.
1. Använd växlingsväljarna för att aktivera eller inaktivera [!DNL PayPal smart button] visningsfunktioner:
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Så här använder du Apple Betala [måste ha ett Apple Developer Account](test-validate.md#test-in-sandbox-environment) (komplett med falska kreditkort och faktureringsuppgifter) för att testa det. När du är redo att använda Apple Pay i sandlådan *eller* produktionsläge, efter slutförande av [testning och validering](test-validate.md)kontaktar du din säljare för att aktivera den för din eller dina livebutiker.

1. Aktivera felsökningsläget genom att växla **[!UICONTROL Debug Mode]** väljare.
1. Klicka på **[!UICONTROL Save]**.

   Om du försöker navigera bort från den här vyn utan att spara dina ändringar visas en modal som uppmanar dig att ignorera ändringar, fortsätta redigera eller spara ändringar.

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

#### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: textfält |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | butiksvy | Aktivera eller inaktivera [!DNL PayPal Smart Buttons] på produktinformationssidan. Alternativ: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini cart preview] | butiksvy | Aktivera eller inaktivera [!DNL PayPal Smart Buttons] i förhandsgranskningen av minikundvagnen. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | butiksvy | Aktivera eller inaktivera [!DNL PayPal Smart Buttons] på kundvagnssidan. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | butiksvy | Aktivera eller inaktivera utseendet på betalningsalternativ vid ett senare tillfälle där betalningsknappar visas. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | webbplats | Aktivera eller inaktivera meddelandet Betala senare i kundvagnen, produktsidan, minivagnen och under kassaflödet. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | butiksvy | Aktivera eller inaktivera betalalternativet Venmo där betalningsknappar visas. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | butiksvy | Aktivera eller inaktivera betalningsalternativet Apple Pay där betalningsknappar visas. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |

### Knappformat

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

Du kan konfigurera [!DNL PayPal Smart Buttons] format [i äldre konfiguration i Admin](configure-admin.md#configure-paypal-smart-buttons) eller här inne [!DNL Payment Services Home]. Se [PayPals stilguide för knappar](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) om du vill ha mer information om alternativen.

#### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|--- |--- |--- |
| [!UICONTROL Layout] | Butiksvy | Definiera layoutformat för betalningsknappar. Alternativ: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Butiksvy | Aktivera/inaktivera tagline. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | Butiksvy | Definiera färg på betalningsknapparna. Alternativ: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Butiksvy | Definiera formen på betalningsknapparna. Alternativ: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Butiksvy | Definierar om betalningsknappar använder en standardhöjd. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Butiksvy | Definiera höjden på betalningsknapparna. Standardvärde: ingen |
| [!UICONTROL Label] | Butiksvy | Definiera etikett som visas i betalningsknapparna. Alternativ: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
