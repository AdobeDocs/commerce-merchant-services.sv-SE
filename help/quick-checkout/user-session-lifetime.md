---
title: Livstid för användarsession
description: Administratören ger dig möjlighet att konfigurera cookie-livstiden för din Adobe Commerce-användare för [!DNL Quick Checkout] tillägg.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: 2f14cd437be6d48e24e56b3b31a1c640357b27e3
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Livstid för användarsession

Livslängden för en shoppingsession bestäms av flera faktorer som kan konfigureras i din Adobe Commerce Admin. Se [Konfigurera cookie-livstid](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} om du vill ha mer information.

Den konfigurerade livstiden för cookies kan påverka din [!DNL Quick Checkout] if:

1. På grund av inaktivitet är kunden utloggad från Adobe Commerce.
1. The [!DNL Bolt] -sessionen upphör.

Om en kund lägger en order när deras [!DNL Bolt] -sessionen går ut, beställningen har placerats men användaren är utloggad från båda nätverken.

Om användaren fortfarande är aktiv efter en lyckad utcheckning loggas han/hon inte ut från både Adobe Commerce och [!DNL Bolt].
