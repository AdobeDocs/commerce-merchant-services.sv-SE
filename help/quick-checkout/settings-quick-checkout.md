---
title: "Konfigurera [!DNL Quick Checkout] för Adobe Commerce-tillägg"
description: "Lär dig konfigurationsalternativen för [!DNL Quick Checkout] och hur du kan ta med och konfigurera tillägget."
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# [!DNL Quick Checkout] inställningar

[!DNL Quick Checkout] för Adobe Commerce och Magento Open Source innehåller en konfigurationsvy med all nödvändig information för att konfigurera tillägget.

Så här kommer du åt konfigurationsinställningarna:

1. På _Administratör_ sidebar, gå till **Lager** > _Inställningar_ > **Konfiguration**.
1. Expandera på den vänstra panelen **Försäljning** och markera **Utcheckning**.

   ![Snabb utcheckning](assets/quick-checkout-main-view-react.png)

Se [Onboarding](../quick-checkout/onboarding.md) om du vill ha mer information om hur du konfigurerar [!DNL Quick Checkout] för Adobe Commerce.

## Aktivera tillägg

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Enable] | webbplats | Aktivera eller inaktivera [!DNL Quick Checkout] för er webbplats. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | webbplats | Ange metod, eller miljö, för [!DNL Quick Checkout]. Alternativ: [!UICONTROL Sandbox] / [!UICONTROL Production] |

## Kontoautentiseringsuppgifter

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL API key] | webbplats | En privat nyckel som används av bakänden för att interagera med [!DNL Bolt] API:er. |
| [!UICONTROL Publishable key] | webbplats | En tangent som används av den främre änden för att interagera med [!DNL Bolt] API:er. |
| [!UICONTROL Signing secret] | webbplats | Används för signaturverifiering på begäranden som tas emot från [!DNL Bolt]. |

## Tjänstinställningar

| Fält | Omfång | Beskrivning |
|---|---|---|
| [!UICONTROL Title] | butiksvy | Lägg till texten som ska visas som rubrik för det här betalningsalternativet i vyn Betalningsmetod vid utcheckning. Alternativ: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | webbplats | The [betalningsåtgärd](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} för den angivna betalningsmetoden. Alternativ: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | webbplats | Aktivera eller inaktivera felsökningsläget. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | webbplats | Ange om Adobe Commerce tillåter att checkout tracking-information delas med Bolt. Aktiverat som standard. Om funktionen inaktiveras påverkas rapporteringen. Alternativ: [!UICONTROL Yes] / [!UICONTROL No] |