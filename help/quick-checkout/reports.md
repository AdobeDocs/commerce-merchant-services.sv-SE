---
title: "[!DNL Quick Checkout] rapportering"
description: "[!DNL Quick Checkout] erbjuder omfattande rapporteringsinformation."
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# Rapporter

[!DNL Quick Checkout] för Adobe Commerce och Magento Open Source erbjuder omfattande rapportering så att du kan få detaljerad information om utcheckningsstatistik för din butik.

![Rapportvy](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> Du måste aktivera [**Spårning av checkar**](../quick-checkout/settings-quick-checkout.md) på Admin-panelen så att Adobe Commerce kan dela utcheckningsinformation med Bolt. Som standard är det här konfigurationsalternativet inställt på **Ja**. Om det här alternativet är inaktiverat (inställt på **Nej**) påverkas rapporteringen.

## Översiktsrapporter

Diagrammen i översiktsavsnittet innehåller detaljerad information om hur utcheckningen av din butik fungerar, inklusive genomsnittlig utcheckningstid, nya konton som skapas vid utcheckning eller utcheckning.

![Översikt över rapporter](assets/overview-report-checkout.png)

| Diagram | Beskrivning |
|---|---|
| [!UICONTROL Checkout abandonment] | Andelen besökare som avslutar utcheckningsprocessen utan att slutföra ett köp. |
| [!UICONTROL Checkout abandonment breakdown] | Övergivna checkout dividerat med typ av besökare. Alternativ: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | Genomsnittlig tid det tar för en besökare att slutföra utcheckningsprocessen. |
| [!UICONTROL Average checkout time breakdown] | Genomsnittlig utcheckningstid dividerad med besökartyp. Alternativ: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | Orderindelade efter typ av besökare. Alternativ: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## Trendrapporter

Diagrammen i trendavsnittet visar dina trender för utcheckningsupplevelser filtrerade efter kontotyp eller nya konton som skapats under utcheckning.

![Rapportrender](assets/trends-report-checkout.png)

| Diagram | Beskrivning |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | Trenden för övergivna checkout dividerat med besökartyp. Alternativ: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | Orderplacerad trend dividerad med besökartyp. Alternativ: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | Nya konton på er butikstrend. |

## Filtrera data

Du kan filtrera resultaten efter datum eller befintliga förinställningar, som **De senaste 30 dagarna**.

![Filtervy](assets/filter-view.png)

| Fält | Beskrivning |
|---|---|
| [!UICONTROL Preset] | En listruta som visar standardförinställningar som kan användas för att visa specifika dataområden. Som standard: De senaste 30 dagarna |
| [!UICONTROL Date range] | En listruta där du kan välja ett visst dataintervall beroende på de valda datumen. |

