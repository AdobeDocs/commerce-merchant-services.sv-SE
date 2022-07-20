---
title: Livstid för användarsession
description: Administratören ger dig möjlighet att konfigurera cookie-livstiden för din Adobe Commerce-användare för [!DNL Quick Checkout] tillägg.
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Livstid för användarsession

Livslängden för en shoppingsession bestäms av flera faktorer som kan konfigureras i din Adobe Commerce Admin. Se [Konfigurera cookie-livstid](https://docs.magento.com/user-guide/customers/customer-online-options.html){target=_blank} om du vill ha mer information.

Den konfigurerade livstiden för cookies kan påverka din [!DNL Quick Checkout] if:

1. På grund av inaktivitet är kunden utloggad från Adobe Commerce.
1. The [!DNL Bolt] -sessionen upphör.

Om en kund lägger en order när deras [!DNL Bolt] -sessionen går ut, beställningen har placerats men användaren är utloggad från båda nätverken.

Om användaren fortfarande är aktiv efter en lyckad utcheckning loggas han/hon inte ut från både Adobe Commerce och [!DNL Bolt].
