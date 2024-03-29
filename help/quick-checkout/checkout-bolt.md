---
title: "Checkout flow of a Bolt user in Adobe Commerce"
description: Översikt över [!DNL Quick Checkout] för en bolt-användare i Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
feature: Checkout, Services, Storefront
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Gästanvändare

Utcheckningen av gäster skiljer sig från användarupplevelsen i Adobe. När en kund anger en e-postadress i kassan [!DNL Quick Checkout] validerar den och hittar en befintlig [!DNL Bolt] konto.

>[!WARNING]
>
> The [!DNL In-Store Pickup] (ISPU) stöds inte när [!DNL Quick Checkout] är aktiverat.

## Registrerad [!DNL Bolt] konto

Om en [!DNL Bolt] finns, kunderna fortsätter med sina [!DNL Quick Checkout] sömlös utcheckning:

1. Ange engångslösenordet som skickas till det [!DNL Bolt] kontots e-postadress eller mobil, beroende på [användarens inställningar i [!DNL Bolt] konto](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Popup för engångslösenord](assets/new-logo-otp-email.png){width="300" zoomable="yes"}

1. När du är inloggad med din [!DNL Bolt] läggs uppgifterna automatiskt till:

   - Leveransinformation
   - Betalningssätt

1. Beställ.

>[!TIP]
>
> Gästanvändaren gör en beställning och kan sedan registrera sig i Adobe Commerce.

## Nytt [!DNL Bolt] konto

Om nej [!DNL Bolt] hittar man sitt standardkonto, shoppingkunderna fortsätter med sin färdiga Adobe Commerce-utcheckning och shopparen ger all information som behövs för att beställa:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod
- En kryssruta visas för att registrera [!DNL Bolt] för snabbare utcheckning innan beställningen görs. Köparen kan godkänna villkoren för att skapa [!DNL Bolt] konto.
- Gästanvändaren gör en beställning och kan sedan registrera sig i Adobe Commerce.
