---
title: Livstid för användarsession
description: Administratören ger dig möjlighet att konfigurera cookie-livstiden för din Adobe Commerce-användare för [!DNL Quick Checkout] tillägg.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Livstid för användarsession

Livslängden för en shoppingsession bestäms av flera faktorer som kan konfigureras i din Adobe Commerce Admin. Se [Konfigurera cookie-livstid](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} för mer information.

Den konfigurerade livstiden för cookies kan påverka din [!DNL Quick Checkout] if:

1. På grund av inaktivitet är kunden utloggad från Adobe Commerce.
1. The [!DNL Bolt] -sessionen upphör.

Om en kund lägger en order när deras [!DNL Bolt] -sessionen går ut, beställningen har placerats men användaren är utloggad från båda nätverken.

Om användaren fortfarande är aktiv efter en lyckad utcheckning loggas han/hon inte ut från både Adobe Commerce och [!DNL Bolt].
