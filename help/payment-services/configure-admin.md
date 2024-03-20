---
title: Konfiguration av äldre betaltjänster
description: Efter installationen kan du konfigurera [!DNL Payment Services] i Admin på butikskonfigurationen.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 0%

---

# Äldre [!DNL Payment Services] Konfiguration

Du kan anpassa [!DNL Payment Services] efter dina behov med hjälp av de praktiska konfigurationsalternativen i Admin.

När du konfigurerar [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] i Admin gäller dessa konfigurationer bara för miljön som är inställd i _[!UICONTROL Method]_fält för_[!UICONTROL General Configuration]_. Alla ändringar du gör i konfigurationsfälten är oberoende av om du byter _[!UICONTROL Method]_markering - om du byter metod återställs inte dina val.

## Allmän konfiguration

Du kan aktivera [!DNL Payment Services] för din butik och dina  _[!UICONTROL Merchant Location]_och aktivera antingen sandlådetestning eller direktbetalningar i_[!UICONTROL General Configuration]_ -avsnitt.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.

   ![Metodvy](assets/methods-view.png){width="400" zoomable="yes"}

1. Ange _[!UICONTROL Merchant Country]_fältet i_[!UICONTROL Merchant Location]_.
1. Expandera _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_för att komma åt_[!UICONTROL [!DNL Payment Services]]_ -avsnitt.
1. I _[!UICONTROL [!DNL Payment Services]]_-avsnittet expanderar du_[!UICONTROL General Configuration]_ -avsnitt.
1. För **Aktivera**, ställ in den på `Yes` aktivera [!DNL Payment Services] för er butik.
1. För **Metod**, ställ in den på `Sandbox` om du fortfarande testar [!DNL Payment Services] för din butik eller `Production` om du är redo att aktivera direktbetalningar.

   >[!WARNING]
   >
   >Dina _[!UICONTROL Sandbox Merchant ID]_och_[!UICONTROL Production Merchant ID]_ genereras automatiskt och finns i respektive fält när du har avslutat introduktionen för sandlådan och/eller produktionen. Ta inte bort eller ändra dessa ID:n.

1. För **Mjuk beskrivning** (anpassade värden som visas på kundtransaktionens bankutdrag för att skilja butiker/varumärken/kataloger åt), lägger du till din anpassade text (upp till 22 tecken) i textfältet och ersätter `Custom descriptor` eller det befintliga värdet.
1. Klicka **[!UICONTROL Save Config]** för att spara ändringarna.
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka sedan på **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

![Vyn Adobe Solution](assets/featured-adobe-solution-view.png){width="700" zoomable="yes"}

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Enable] | webbplats | Aktivera eller inaktivera [!DNL Payment Services] för er webbplats. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | butiksvy | Ange metod, eller miljö, för din butik. Alternativ: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | butiksvy | Ditt handlar-ID för sandlådan, som genereras automatiskt vid introduktion av sandlådor. Ändra eller ändra inte detta ID. |
| [!UICONTROL Production Merchant ID] | butiksvy | Ditt handlar-ID för produktion, som genereras automatiskt när sandlådan introduceras. Ändra eller ändra inte detta ID. |
| [!UICONTROL Soft Descriptor] | webbplats eller butiksvy | Lägg till en mjuk beskrivning till webbplatserna och butiksvyn för att lägga till information till kundtransaktioner som avgränsar varumärken, butiker eller produktrader. |

## [!UICONTROL Credit Card Fields]

The [!UICONTROL Credit Card Fields] betalningsalternativ ger en enkel och säker utcheckning av betalningsmetoder för kreditkort och betalkort.

Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.
1. Expandera avsnittet _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. I _[!UICONTROL Payment Services]_-avsnittet expanderar du_[!UICONTROL Credit Card Fields]_ -avsnitt.
1. För **[!UICONTROL Title]**, anger du text (om det behövs) för att ändra namnet på betalningsmetoden så som visas vid utcheckningen.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), markera **[!UICONTROL Authorize]** eller **Auktorisera och hämta**.
1. Om du vill prioritera en betalningsmetod på utcheckningssidan anger du en `Numeric Only` värdet i **[!UICONTROL Sort order]** fält.
1. För **[!UICONTROL Show on checkout page]**, välja `Yes` för att aktivera kreditkortsfält på utcheckningssidan.
1. För **[!UICONTROL Vault Enabled]**, välja `Yes` för att aktivera kreditkortsvalv för utcheckning.
1. För **[!UICONTROL Vault Enabled in Admin]**, välja `Yes` för att göra det möjligt för handlaren att skapa beställningar för kunder med hjälp av deras kreditkort.
1. Aktivera **[!UICONTROL 3DS Secure authentication]** (`Off` som standard) väljer du `Always` eller `When required`.
1. För **[!UICONTROL Debug Mode]**, välja `Yes` för att aktivera felsökningsläge, eller `No` för att inaktivera den.
1. Klicka **[!UICONTROL Save Config]** för att spara ändringarna.
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka sedan på **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | butiksvy | Sorteringsordningen för den angivna betalningsmetoden på utcheckningssidan. `Numeric Only` value |
| [!UICONTROL Show on checkout page] | webbplats | Aktivera eller inaktivera kreditkortsfält på utcheckningssidan. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | butiksvy | Aktivera eller inaktivera [kreditkortsvalv](vaulting.md). Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | butiksvy | Aktivera eller inaktivera funktioner för [handlare som slutför beställningar för kunder i administratören](vaulting.md) med en betalningsmetod som är skyddad. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | webbplats | Aktivera eller inaktivera [Säker 3DS-autentisering](security.md#3ds). Alternativ: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

The [!UICONTROL Apple Pay] betalningsalternativ tillåter handlaren att erbjuda Apple Pay till sina kunder, som kan använda Touch ID på sina enheter för att göra inköp från webbläsaren Safari. Handlare kan lägga till upp till 99 domäner per handelskonto.

Se [Betalningsalternativ](payments-options.md#apple-pay-button) för mer information.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.
1. Expandera avsnittet _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. I _[!UICONTROL Payment Services]_-avsnittet expanderar du_[!UICONTROL Apple Pay]_ -avsnitt.
1. För **[!UICONTROL Title]**, anger du text (om det behövs) för att ändra namnet på betalningsmetoden så som visas vid utcheckningen.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), markera **[!UICONTROL Authorize]** eller **[!UICONTROL Authorize and Capture]**.
1. Ange var [!DNL Apple Pay] är aktiverat i Adobe Commerce genom att välja `Yes` i följande alternativ efter behov:
   * **[!UICONTROL Show Apple Pay on checkout page]**
   * **[!UICONTROL Show Apple Pay on product detail page]**
   * **[!UICONTROL Show Apple Pay in mini cart preview]**
   * **[!UICONTROL Show Apple Pay on cart page]**
1. Om du vill aktivera felsökningsläget väljer du `Yes` för **[!UICONTROL Debug Mode]** (`No` inaktiverar den).
1. Klicka på **[!UICONTROL Save Config]** .
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka sedan på **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | webbplats | Aktivera eller inaktivera [!DNL Apple Pay] på utcheckningssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | butiksvy | Sorteringsordningen för den angivna betalningsmetoden på utcheckningssidan. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | butiksvy | Aktivera eller inaktivera [!DNL Apple Pay] på produktinformationssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | butiksvy | Aktivera eller inaktivera [!DNL Apple Pay] i minikundvagnen. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | butiksvy | Aktivera eller inaktivera [!DNL Apple Pay] på kundvagnssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Google Pay]

The [!UICONTROL Google Pay] betalningsalternativ gör det möjligt för handlaren att erbjuda Google Pay till sina kunder, som kan använda Google Wallet på sina enheter för att göra inköp.

Se [Betalningsalternativ](payments-options.md#google-pay-button) för mer information.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.
1. Expandera avsnittet _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. I _[!UICONTROL Payment Services]_-avsnittet expanderar du_[!UICONTROL Google Pay]_ -avsnitt.
1. (Valfritt) Ändra namnet på betalningsmetoden som visas vid utcheckning genom att ange det nya namnet i **[!UICONTROL Title]** fält.
1. [Ange betalningsåtgärd](production.md#set-payment-services-as-payment-method) genom att välja **[!UICONTROL Authorize]** eller **[!UICONTROL Authorize and Capture]**.
1. Ange var [!DNL Google Pay] är aktiverat i Adobe Commerce genom att välja `Yes` i följande alternativ efter behov:
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Om du vill aktivera felsökningsläget väljer du `Yes` för **[!UICONTROL Debug Mode]** (`No` inaktiverar den).
1. Konfigurera utseendet på _[!UICONTROL Google Pay]_genom att markera **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**och **[!UICONTROL Button Style]**efter behov.
1. Om du vill ange höjden använder standardvärdet för höjd som definieras i **[!UICONTROL Button Style]**.
1. Klicka på **[!UICONTROL Save Config]** .
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka sedan på **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Anger textetiketten som visas för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) för den angivna betalningsmetoden. Alternativ: `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | webbplats | Aktivera eller inaktivera [!DNL Google Pay] på utcheckningssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | butiksvy | Sorteringsordningen för den angivna betalningsmetoden på utcheckningssidan. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | butiksvy | Aktivera eller inaktivera [!DNL Google Pay] på produktinformationssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | butiksvy | Aktivera eller inaktivera [!DNL Google Pay] i minikundvagnen. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | butiksvy | Aktivera eller inaktivera [!DNL Google Pay] på kundvagnssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | Butiksvy | Definiera färgen på [!DNL Google Pay] -knappen. Alternativ: `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | Butiksvy | Definiera typ av [!DNL Google Pay] -knappen. Alternativ: `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

Se [Objektalternativ för Google Pay API-begäran](https://developers.google.com/pay/api/web/reference/request-objects) mer information.

## [!DNL PayPal Payment Buttons]

The [!DNL PayPal payment buttons] betalningsalternativ ger en enkel, snabb och säker utcheckningsprocess för kunden.

Se [Betalningsalternativ](payments-options.md#paypal-smart-buttons) för mer information.

Konfigurera [!DNL PayPal payment buttons]

Du kan aktivera och konfigurera betalningsalternativen för betalningsknapparna i PayPal i Admin:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.
1. Expandera avsnittet _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. I _[!UICONTROL Payment Services]_-avsnittet expanderar du_[!UICONTROL PayPal payment buttons]_ -avsnitt.
1. Om du vill ändra namnet på betalningsmetoden så som visas vid utcheckning redigerar du _[!UICONTROL Title]_fält.
1. Till [ange betalningsåtgärd](production.md#set-payment-services-as-payment-method), markera **[!UICONTROL Authorize]** eller **[!UICONTROL Authorize and Capture]**.
1. Om du vill prioritera en betalningsmetod på utcheckningssidan anger du en `Numeric Only` värdet i **[!UICONTROL Sort order]** fält.
1. Aktivera/inaktivera [Betala senare meddelanden](payments-options.md#pay-later-button), markera `Yes`/`No` for **[!UICONTROL Display Pay Later Message]**.
1. Ange var betalningsknapparna för PayPal ska aktiveras i Adobe Commerce genom att välja `Yes` i följande alternativ efter behov:
   * **[!UICONTROL Show buttons on checkout page]**
   * **[!UICONTROL Show buttons on product detail page]**
   * **[!UICONTROL Show buttons in mini cart preview]**
   * **[!UICONTROL Show buttons on cart page]**
1. Om du vill aktivera Venmo som betalningsalternativ väljer du `Yes` for **[!UICONTROL Venmo Enabled]**.
1. Om du vill aktivera kredit- och debetkort som betalningsalternativ (smart PayPal-knapp) väljer du `Yes` for **[!UICONTROL Credit and Debit Card Enabled]**.
1. Aktivera/inaktivera [PayPal Pay Senare](payments-options.md#pay-later-button) betalningsalternativ, välj `Yes`/`No` for **[!UICONTROL PayPal Pay Later Enabled]**.
1. Om du vill aktivera felsökningsläget väljer du `Yes` för **[!UICONTROL Debug Mode]** (`No` inaktiverar den).
1. Klicka på **[!UICONTROL Save Config]** .
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka sedan på **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: textfält |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | webbplats | Aktivera eller inaktivera meddelandet Betala senare i kundvagnen, på produktsidan, i minikundvagnen och under kassaflödet. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | butiksvy | Aktivera eller inaktivera [!DNL PayPal payment buttons] på utcheckningssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | butiksvy | Aktivera eller inaktivera [!DNL PayPal payment buttons] på produktinformationssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | butiksvy | Aktivera eller inaktivera [!DNL PayPal payment buttons] i minikundvagnen. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | butiksvy | Aktivera eller inaktivera [!DNL PayPal payment buttons] på kundvagnssidan. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | butiksvy | Aktivera eller inaktivera betalalternativet Venmo där betalningsknappar visas. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | butiksvy | Aktivera eller inaktivera alternativ för kredit- och betalkort där betalningsknappar visas. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | butiksvy | Aktivera eller inaktivera utseendet för betalningsalternativ för PayPal Senare där betalningsknappar visas. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Knappformat

Du kan även konfigurera _[!UICONTROL Button style]_alternativ för betalningsknapparna:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Sales]** och välja **[!UICONTROL Payment Methods]**.
1. Expandera avsnittet _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_.
1. I _[!UICONTROL [!DNL Payment Services]]_-avsnittet expanderar du_[!UICONTROL PayPal Smart Button Styling]_ -avsnitt.
1. Ange layouten genom att välja `Vertical` eller `Horizontal` for **[!UICONTROL Layout]**
1. Välj bland de tillgängliga färgerna i **[!UICONTROL Color]**.
1. Ange formen genom att markera `Rectangular` eller `Pill` for **[!UICONTROL Shape]**.
1. Om du vill använda standardhöjden väljer du `Yes` eller `No` for **[!UICONTROL Use Default Height]**.
1. Om du vill ange en anpassad höjd lägger du till önskad pixelhöjd för **[!UICONTROL Height]**.
1. Om du vill ange tagline väljer du `Yes` eller `No` for **[!UICONTROL Tagline]**.
1. Klicka på **[!UICONTROL Save Config]** .
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka sedan på **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

Du kan också konfigurera format för betalningsknappar [i Inställningar](settings.md#button-style) från startsidan för betaltjänster.

### Konfigurationsalternativ

| Fält | Omfång | Beskrivning |
|--- |--- |--- |
| [!UICONTROL Layout] | Butiksvy | Definiera layoutstil för Paypal Payment-knappar. Alternativ: `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | Butiksvy | Definiera färg på knapparna för PayPal-betalning. Alternativ: [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | Butiksvy | Definiera formen på knapparna för PayPal-betalning. Alternativ: `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | Butiksvy | Definierar om betalningsknapparna för PayPal använder en standardhöjd. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | Butiksvy | Definiera höjden på PayPal-betalningsknapparna. Standardvärde: ingen |
| [!UICONTROL Label] | Butiksvy | Definiera etikett som visas i PayPal-betalningsknapparna. Alternativ: `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | Butiksvy | Aktiverar tagline. Alternativ: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Töm cachen

Om du ändrar konfigurationen, [tömma cachen manuellt](/help/payment-services/settings.md#flush-the-cache) så att butiken visar de senaste konfigurationsinställningarna.
