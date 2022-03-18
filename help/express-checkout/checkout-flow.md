---
title: Utcheckningsflöde
description: Översikt över [!DNL Express Checkout] i Adobe Commerce.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# [!DNL Express Checkout] flöde

>[!IMPORTANT]
>
> Den här funktionen är endast avsedd för användare av tidig Adobe-programvara (EAP) och är ännu inte tillgänglig för alla kunder. För närvarande begränsat till amerikanska kunder. Kontakta Adobe Commerce Support för hjälp och frågor.

I det här avsnittet finns en översikt över den typiska utcheckningen med [!DNL Express Checkout] för Adobe Commerce.

Slutförd [!DNL Express Checkout] -flödet består av följande steg:

1. Öppna butiken och lägg till artiklar i kundvagnen.
1. Gå till kassan.

![Utcheckning](../assets/proceed-checkout.png)

1. Ange en e-postadress som är kopplad till ett bolt-konto när du uppmanas till detta.
1. Ange det engångslösenord som skickas till det bolt-kontots e-postadress eller telefonnummer.
1. När du har loggat in med ditt bolt-konto fylls utcheckningsinformationen i automatiskt:

   - Leveransinformation
   - Betalningssätt

   >[!NOTE]
   >
   > Du kan använda din befintliga plånboksinformation (adress eller kreditkortsinformation) även om dina utcheckningsuppgifter fylls i automatiskt.

1. Beställ.

The [!DNL Express Checkout] är kompatibelt med andra Adobe Commerce-alternativ för utcheckning, som [presentkort](https://docs.magento.com/user-guide/catalog/product-gift-card.html) eller [rabattkoder](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] användningsfall

The [!DNL Express Checkout] tillåter flera användningsfall under ett utcheckningsflöde:

- Gästanvändare med ett registrerat Bolt-konto.
- Gästanvändare med ett nytt Bolt-konto.
- En befintlig Adobe Commerce-användare med/utan ett registrerat Bolt-konto.

## Utcheckning av gästanvändare: Så här fungerar det

Utcheckningen av gäster skiljer sig från den inloggade upplevelsen. När en kund anger en e-postadress i kassan [!DNL Express Checkout] validerar det för att hitta ett befintligt Bolt-konto.

### Registrerat bultkonto

Om ett bolt-konto hittas fortsätter kunderna med sina [!DNL Express Checkout] sömlös utcheckning:

1. Ange det engångslösenord som skickas till det bolt-kontots e-postadress eller mobil, beroende på användarens inställningar i bolt-kontot.
1. När du har loggat in med ditt bolt-konto fylls utcheckningsinformationen i automatiskt:

   - Leveransinformation
   - Betalningssätt

1. Beställ.

>[!TIP]
>
> Gästanvändare gör beställningen och kan registrera sig i Adobe Commerce.

### Nytt bultkonto

Om inget bolt-konto hittas fortsätter kunderna med standardutcheckningen av Adobe Commerce och shopparen ger all information som behövs för att göra beställningen:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod
- En kryssruta visas för att registrera dig i Bolt för snabbare utcheckning innan beställningen görs. De kan godkänna villkoren för att skapa sitt Bolt-konto.

   ![Kom ihåg Bult](../assets/checked-bolt.png)

- Gästanvändaren gör beställningen och kan registrera sig i Adobe Commerce.

## En befintlig Adobe Commerce-användare: Så här fungerar det

En befintlig användare kan välja befintlig information när en användare gör en beställning med [!DNL Express Checkout] för en snabbare utcheckning.

När en kund anger en e-postadress i kassan [!DNL Express Checkout] validerar det för att hitta ett befintligt Bolt-konto.

### Registrerat Bolt-konto hos en Adobe Commerce-användare

Om ett bolt-konto hittas fortsätter kunderna med standardutcheckningen av Adobe Commerce och shopparen ger all nödvändig information och lägger sedan beställningen:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod

Se [felsökning](../express-checkout/troubleshooting.md) om du får problem när du gör en beställning som Adobe Commerce-användare.

>[!NOTE]
>
> Om användaren har ett bolt-konto och e-postadressen inte visas som registrerad i Adobe Commerce, aktiveras engångslösenordsinloggningen. Se [registrerat bolts-konto](#registered-bolt-account) flöde.

### Nytt bultkonto

Om inget bolt-konto hittas fortsätter kunderna med sin standardutcheckning av Adobe Commerce och shopparen väljer all nödvändig information från sin sparade information för att göra beställningen:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod
- En kryssruta visas för att registrera dig i Bolt för snabbare utcheckning innan beställningen görs. De kan godkänna villkoren för att skapa sitt Bolt-konto.

   ![Kom ihåg Bult](../assets/checked-bolt.png)

## Få hjälp

Kontakta Adobe Commerce Support för hjälp och frågor.
