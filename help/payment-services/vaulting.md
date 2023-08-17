---
title: Kreditkortsvarning
description: Köpare kan vault (save) their credit card details for future purchasing.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Kreditkortsvarning

Konvertera engångskunder till lojala kunder med kreditkortsbetalning. Köpare kan spara - eller&quot;vault&quot; - sina kreditkortsuppgifter under utcheckningen och använda dem vid ett senare köp för samma eller en annan butik inom samma handlarkonto.

![Vadera deras kreditkort för senare bruk](assets/save-card-for-later.png)

Köpare använder den lagrade token för att slutföra en framtida utcheckning med sin sparade kreditkortsinformation.

![Använd lagrade autentiseringsuppgifter för framtida inköp](assets/use-stored-card.png)

De kan även enkelt ta bort sina kreditkort från [Lagrade betalningsmetoder](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) på mitt konto.

![Lagrade betalningsmetoder i mitt konto](assets/stored-payment-methods.png)

## Aktivera vault

Du kan aktivera kreditkortsvalv - för kunder _och_ handlare i Admin - för butiker i [!DNL Payment Services] [Inställningar](settings.md#card-vaulting).

## Använd valv i administratören

Om en kund har ett kreditkort med tidigare säkerhet kan en handlare skapa en efterföljande order för den kunden i Admin med hjälp av sina betalningsmetoder.

Du kan bara använda kort i säkert läge i administratören om kunden har både ett befintligt konto och en giltig token lagrad i systemet från en tidigare slutförd betalning.

Så här skapar du en beställning i Admin för en kund som använder sitt kreditkort som säkerhet:

1. [Skapa en beställning och lägg till produkter](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. I _[!UICONTROL Payment & Shipping Information]_, markera **[!UICONTROL Stored Cards]**som betalningsmetod.
1. Välj önskad betalningsmetod för bankkort.
1. När du har utfört andra nödvändiga steg för ordern, [skicka](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Använd bankkreditkort i Admin för kund](assets/admin-vaultedcard.png)

## Säkerhet

Minimal kreditkortsinformation delas med kunden; de ser bara de fyra sista siffrorna, utgångsdatumet och varumärket för sitt kreditkort. Kreditkortsinformationen lagras hos betalningsförmedlaren för att uppfylla kraven [PCI](security.md#PCI-compliance) efterlevnadsstandarder.
