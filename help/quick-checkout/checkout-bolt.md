---
title: Utcheckningsflöde
description: Översikt över [!DNL Quick Checkout] för en bolt-användare i Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Gästanvändare

Utcheckningen av gäster skiljer sig från Adobe. När en kund anger en e-postadress i kassan [!DNL Quick Checkout] validerar den och hittar en befintlig [!DNL Bolt] konto.

## Registrerad [!DNL Bolt] konto

Om en [!DNL Bolt] finns, kunderna fortsätter med sina [!DNL Quick Checkout] sömlös utcheckning:

1. Ange engångslösenordet som skickas till det [!DNL Bolt] kontots e-postadress eller mobil, beroende på [användarens inställningar i [!DNL Bolt] konto](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Popup-fönster för engångslösenord](assets/pop-up.png)

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
- En kryssruta visas för att registrera dig i [!DNL Bolt] för snabbare utcheckning innan ordern läggs. Köparen kan godkänna villkoren för att skapa [!DNL Bolt] konto.

   ![Kom ihåg [!DNL Bolt]](assets/checkbox-remember-bolt.png)

- Gästanvändaren gör en beställning och kan sedan registrera sig i Adobe Commerce.