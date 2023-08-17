---
title: "Utcheckningsflöde för en Adobe Commerce-användare"
description: "Översikt över [!DNL Quick Checkout] för en Adobe Commerce-användare."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# En befintlig Adobe Commerce-användare: Så fungerar det

En befintlig Adobe Commerce-användare kan välja sparad leverans- och betalningsinformation när en beställning görs med [!DNL Quick Checkout] för en snabbare utcheckning.

När en kund anger sin e-postadress i kassan [!DNL Quick Checkout] validerar den och hittar en befintlig [!DNL Bolt] konto.

## Registrerad användare i både Adobe Commerce och [!DNL Bolt]

När en kund är registrerad användare i både Adobe Commerce och [!DNL Bolt] nätverk, båda nätverken tillhandahålls lagrad leverans och betalningsinformation.

Om en [!DNL Bolt] finns i kassan kan kunderna fortsätta med sina [!DNL Quick Checkout] sömlös utcheckning:

1. Ange engångslösenordet som skickas till det [!DNL Bolt] kontots e-postadress eller mobil, beroende på [användarens inställningar i [!DNL Bolt] konto](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Popup för engångslösenord](assets/new-logo-otp-email.png)

1. När du är inloggad med din [!DNL Bolt] läggs uppgifterna automatiskt till:

   - Leveransinformation
   - Betalningssätt

1. Beställ.

>[!NOTE]
>
> Popup-fönstret Bult OTP visas bara när kunden är på utcheckningssidan. Köparen kan välja att inte logga in i Bolt genom att stänga popup-fönstret.

Om kunden är inloggad på Adobe Commerce före utcheckning är [!DNL Bolt] Popup-fönstret för engångslösenord visas inte vid utcheckning, men ett meddelande visas som föreslår att användaren loggar in för att komma åt sin bolt-plånbok.

Om du får problem när du gör en beställning som befintlig Adobe Commerce-användare kan du läsa [Felsöka problem med snabbutcheckning](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) artikel i Adobe Commerce Help Center.

## Automatisk inloggning

Komponenten för automatisk inloggning identifierar när en kund har en aktiv bolt-session och loggar in användaren automatiskt. Detta hoppar över kontoidentifiering och engångslösenordssteg eftersom kunden slutförde dem i en tidigare session.

Det går att konfigurera en automatisk inloggning för [!DNL Quick Checkout] -användare. Du kan aktivera en konfiguration så att en användare loggas in automatiskt vid utcheckning.

1. På _Administratör_ sidlist, navigera till **Lager** > **Konfiguration** > **Utcheckning** för att komma åt den allmänna konfigurationssidan för administratör för utcheckning.
1. I _Tjänstinställningar_ avsnitt för [!DNL Quick Checkout], innehåller all information som krävs för att konfigurera automatisk inloggning.

Se [[!DNL Quick Checkout] konfigurera tjänstinställningar](../quick-checkout/onboarding.md#configure-service-settings) för mer information.

>[!NOTE]
>
> Första gången du loggar in **automatisk inloggning** är aktiverat kräver användarens samtycke för att godkänna det genom att godkänna ett popup-fönster.

## Nytt [!DNL Bolt] konto

Om nej [!DNL Bolt] hittar man sitt standardkonto, fortsätter kunderna med sin färdiga Adobe Commerce-utcheckning och shopparen väljer ut all information de behöver från sin sparade information för att göra beställningen:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod
- Alternativet att registrera sig i [!DNL Bolt] för snabbare utcheckning innan beställningen görs. Köparen kan godkänna villkoren för att skapa [!DNL Bolt] konto.

  ![Kom ihåg [!DNL Bolt]](assets/checkbox-remember-bolt.png)
