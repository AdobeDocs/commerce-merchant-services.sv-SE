---
title: Kreditkortsvarning
description: Köpare kan vault (save) their credit card details for future purchasing.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Kreditkortsvarning

Konvertera engångskunder till lojala kunder med kreditkortsbetalning. Köpare kan spara - eller&quot;vault&quot; - sina kreditkortsuppgifter under utcheckningen och använda dem vid ett senare köp för samma eller en annan butik inom samma handlarkonto.

![Vadera deras kreditkort för senare bruk](assets/save-card-for-later.png){width="400" zoomable="yes"}

Köpare använder den lagrade token för att slutföra en framtida utcheckning med sin sparade kreditkortsinformation.

![Använd lagrade autentiseringsuppgifter för framtida köp](assets/use-stored-card.png){width="400" zoomable="yes"}

De kan även enkelt ta bort sina kreditkort i säkrat värde från [Lagrade betalningsmetoder](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) i Mitt konto.

![Lagrade betalningsmetoder i mitt konto](assets/stored-payment-methods.png){width="400" zoomable="yes"}

>[!WARNING]
>
>PayPal kan för närvarande lagra maximalt fem vaultade kort.

## Aktivera vault

Du kan aktivera kreditkortssäkring - för kunder _och_ handlare i Admin - för dina butiker i [!DNL Payment Services] [Inställningar](settings.md#card-vaulting).

## Använd valv i administratören

Om en kund har ett kreditkort med tidigare säkerhet kan en handlare skapa en efterföljande order för den kunden i Admin med hjälp av sina betalningsmetoder.

Du kan bara använda kort i säkert läge i administratören om kunden har både ett befintligt konto och en giltig token lagrad i systemet från en tidigare slutförd betalning.

Så här skapar du en beställning i Admin för en kund som använder sitt kreditkort som säkerhet:

1. [Skapa en beställning och lägg till produkter](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. I _[!UICONTROL Payment & Shipping Information]_väljer du **[!UICONTROL Stored Cards]**som betalningsmetod.
1. Välj önskad betalningsmetod för bankkort.
1. När du har slutfört eventuella andra nödvändiga steg för beställningen [skickar du den](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Använd kreditkort i betal i Admin för kund](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## Säkerhet

Minimal kreditkortsinformation delas med kunden; de ser bara de fyra sista siffrorna, utgångsdatumet och varumärket för sitt kreditkort. Kreditkortsinformation lagras hos betalningsförmedlaren för att uppfylla [PCI](security.md#PCI-compliance)-kompatibilitetsstandarder.
