---
title: Konfiguration av äldre betaltjänster
description: Efter installationen kan du konfigurera [!DNL Payment Services] i Admin på butikskonfigurationen.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: 31ad67d3f3d11c68341de0306eea37f231b2d9b9
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 1%

---

# Konfiguration av äldre betaltjänster

Du kan anpassa [!DNL Payment Services] efter dina behov med hjälp av de praktiska konfigurationsalternativen i Admin.

När du konfigurerar [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] i Admin gäller dessa konfigurationer bara för miljön som är inställd i _[!UICONTROL Method]_fält för_[!UICONTROL General Configuration]_. Alla ändringar du gör i konfigurationsfälten är oberoende av om du byter _[!UICONTROL Method]_markering - om du byter metod återställs inte dina val.

Se [[!UICONTROL General Configuration] section](#general-configuration) för mer information.

## Allmän konfiguration

Du kan aktivera [!DNL Payment Services] för din butik och aktivera antingen sandlådetestning eller direktbetalningar i _[!UICONTROL General Configuration]_-avsnitt.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.

   ![Metodvy](assets/methods-view.png)

1. Expandera avsnittet _[!UICONTROL Recommended Solutions]_.
1. I _[!UICONTROL [!DNL Payment Services]]_-avsnittet, expandera_[!UICONTROL General Configuration]_ -avsnitt.
1. För **Aktivera**, ange att `Yes` för att aktivera [!DNL Payment Services] för er butik.
1. För **Metod**, ange att `Sandbox` om du fortfarande testar [!DNL Payment Services] för din butik eller `Production` om du är redo att aktivera direktbetalningar.

   >[!WARNING]
   >
   >Dina _[!UICONTROL Sandbox Merchant ID]_och_[!UICONTROL Production Merchant ID]_ genereras automatiskt och finns i respektive fält när du har avslutat introduktionen för sandlådan och/eller produktionen. Ta inte bort eller ändra dessa ID:n.

1. Klicka **[!UICONTROL Save Config]** för att spara ändringarna.

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Enable] | webbplats | Aktivera eller inaktivera [!DNL Payment Services] för er webbplats. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | butiksvy | Ange metod, eller miljö, för din butik. Alternativ: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | butiksvy | Ditt handlar-ID för sandlådan, som genereras automatiskt vid introduktion av sandlådor. Ändra eller ändra inte detta ID. |
| [!UICONTROL Production Merchant ID] | butiksvy | Ditt handlar-ID för produktion, som genereras automatiskt när sandlådan introduceras. Ändra eller ändra inte detta ID. |

## [!UICONTROL Credit Card Fields]

The [!UICONTROL Credit Card Fields] betalningsalternativ ger en enkel och säker utcheckning av betalningsmetoder för kreditkort och betalkort.

Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

### Konfigurera kreditkortsfält

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.
1. Expandera avsnittet _[!UICONTROL Recommended Solutions]_.
1. I _[!UICONTROL Payment Services]_-avsnittet, expandera_[!UICONTROL Credit Card Fields]_ -avsnitt.
1. För **[!UICONTROL Title]**, anger du text (om det behövs) för att ändra namnet på betalningsmetoden så som visas vid utcheckningen.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), markera **[!UICONTROL Authorize]** eller **Auktorisera och hämta**.
1. För **Felsökningsläge**, välja `Yes` för att aktivera felsökningsläge (eller `No` för att inaktivera den).
1. Klicka **[!UICONTROL Save Config]** för att spara ändringarna.

#### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

The [!DNL PayPal Smart Buttons] betalningsalternativ ger en enkel, snabb och säker utcheckningsprocess för kunden.

Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

### Konfigurera [!DNL PayPal Smart Buttons]

Du kan aktivera och konfigurera betalningsalternativen för smarta knappar i PayPal i Admin:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.
1. Expandera avsnittet _[!UICONTROL Recommended Solutions]_.
1. I _[!UICONTROL Payment Services]_-avsnittet, expandera_[!UICONTROL PayPal Smart Buttons]_ -avsnitt.
1. Om du vill ändra namnet på betalningsmetoden så som visas vid utcheckning redigerar du _[!UICONTROL Title]_fält.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), markera **[!UICONTROL Authorize]** eller **[!UICONTROL Authorize and Capture]**.
1. Så här inaktiverar du [Betala senare meddelanden](payments-options.md#pay-later-button) (om du vill) väljer du `No` for **[!UICONTROL Display Pay Later Message]**.
1. Om du vill aktivera felsökningsläget väljer du `Yes` för **[!UICONTROL Debug Mode]** (`No` inaktiverar den).
1. Spara ändringarna genom att klicka på **[!UICONTROL Save Config]** .

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: textfält |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | webbplats | Aktivera eller inaktivera meddelandet Betala senare i kundvagnen, produktsidan, minivagnen och under kassaflödet. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | butiksvy | Aktivera eller inaktivera betalalternativet Venmo där betalningsknappar visas. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | butiksvy | Aktivera eller inaktivera betalningsalternativet Apple Pay där betalningsknappar visas. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | butiksvy | Aktivera eller inaktivera utseendet på betalningsalternativ vid ett senare tillfälle där betalningsknappar visas. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | butiksvy | Aktivera eller inaktivera [!DNL PayPal Smart Buttons] på produktinformationssidan. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini-cart preview] | butiksvy | Aktivera eller inaktivera [!DNL PayPal Smart Buttons] i minikundvagnen. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | butiksvy | Aktivera eller inaktivera [!DNL PayPal Smart Buttons] på kundvagnssidan. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] Formatalternativ

| Fält | Omfång | Beskrivning |
|--- |--- |--- |
| [!UICONTROL Layout] | Butiksvy | Definiera layoutformat för PayPal Smart Buttons. Alternativ: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | Butiksvy | Definiera färg på PayPal-knapparna. Alternativ: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Butiksvy | Definiera formen på PayPal-knapparna. Alternativ: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | Butiksvy | Definierar om smarta PayPal-knappar använder en standardhöjd. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Butiksvy | Definiera höjden på smarta PayPal-knappar. Standardvärde: ingen |
| [!UICONTROL Label] | Butiksvy | Definiera etikett som visas i smarta PayPal-knappar. Alternativ: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | Butiksvy | Aktiverar tagline. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
