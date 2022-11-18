---
title: Kreditkortssäkringar
description: Köpare kan vault (save) their credit card details for future purchasing.
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Kreditkortssäkringar

Konvertera engångskunder till lojala kunder med kreditkortsbetalning. Köpare kan spara - eller&quot;vault&quot; - sina kreditkortsuppgifter under utcheckningen och använda dem vid ett senare köp för samma eller en annan butik inom samma handlarkonto.

![Vadera deras kreditkort för senare bruk](assets/save-card-for-later.png)

Köpare använder den lagrade token för att slutföra en framtida utcheckning med sin sparade kreditkortsinformation.

![Använd lagrade autentiseringsuppgifter för framtida inköp](assets/use-stored-card.png)

De kan även enkelt ta bort sina kreditkort från [Lagrade betalningsmetoder](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) på mitt konto.

![Lagrade betalningsmetoder i mitt konto](assets/stored-payment-methods.png)

## Aktivera vault

Du kan aktivera kreditkortsvalv för dina butiker i Betalningstjänster [Inställningar](settings.md#card-vaulting).

## Säkerhet

Minimal kreditkortsinformation delas med kunden. de ser bara de fyra sista siffrorna, utgångsdatumet och varumärket för sina kreditkort. Kreditkortsinformationen lagras hos betalningsförmedlaren för att uppfylla kraven [PCI](security.md#PCI-compliance) efterlevnadsstandarder.
