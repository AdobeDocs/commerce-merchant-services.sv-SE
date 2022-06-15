---
title: '"Utcheckningsflöde"'
description: '"Översikt över [!DNL Quick Checkout] flödar i Adobe Commerce."'
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: c0b1185a53cb84be2335e2e1beb392c9f23070c9
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# [!DNL Quick Checkout] flöde

I det här avsnittet finns en översikt över den typiska utcheckningen med [!DNL Quick Checkout] för Adobe Commerce.

Slutförd [!DNL Quick Checkout] -flödet består av följande steg:

1. Öppna butiken och lägg till artiklar i kundvagnen.
1. Gå till kassan.

![Utcheckning](assets/proceed-checkout.png)

1. Ange en e-postadress som är kopplad till en [!DNL Bolt] konto.
1. Ange engångslösenordet som skickas till det [!DNL Bolt] kontots e-postadress eller telefonnummer.
1. När du är inloggad med din [!DNL Bolt] konto, checkout-information fylls i automatiskt:

   - Leveransinformation
   - Betalningssätt

   >[!NOTE]
   >
   > Du kan använda din befintliga plånboksinformation (adress eller kreditkortsinformation) även om dina utcheckningsuppgifter fylls i automatiskt.

1. Beställ.

The [!DNL Quick Checkout] är kompatibelt med andra Adobe Commerce-alternativ för utcheckning, som [presentkort](https://docs.magento.com/user-guide/catalog/product-gift-card.html) eller [rabattkoder](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] användningsfall

The [!DNL Quick Checkout] tillåter flera användningsfall under ett utcheckningsflöde:

- Gästanvändare med en registrerad [!DNL Bolt] konto.
- Gästanvändare med en ny [!DNL Bolt] konto.
- En befintlig Adobe Commerce-användare med/utan registrerat [!DNL Bolt] konto.

## Utcheckning av gästanvändare: Så här fungerar det

Utcheckningen av gäster skiljer sig från den inloggade upplevelsen. När en kund anger en e-postadress i kassan [!DNL Quick Checkout] validerar den för att hitta en befintlig [!DNL Bolt] konto.

### Registrerad [!DNL Bolt] konto

Om en [!DNL Bolt] finns, kunderna fortsätter med sina [!DNL Quick Checkout] sömlös utcheckning:

1. Ange engångslösenordet som skickas till det [!DNL Bolt] kontots e-postadress eller mobil, beroende på användarens inställningar i dialogrutan [!DNL Bolt] konto.
1. När du är inloggad med din [!DNL Bolt] fyller det i utcheckningsinformationen automatiskt:

   - Leveransinformation
   - Betalningssätt

1. Beställ.

>[!TIP]
>
> Gästanvändare gör beställningen och kan registrera sig i Adobe Commerce.

### Nytt [!DNL Bolt] konto

Om nej [!DNL Bolt] hittar man sitt standardkonto, shopparna fortsätter med sin färdiga Adobe Commerce-utcheckning och shopparen ger all den information de behöver för att beställa:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod
- En kryssruta visas för att registrera dig i [!DNL Bolt] för snabbare utcheckning innan ordern läggs. De kan godkänna villkoren för att skapa sina [!DNL Bolt] konto.

   ![Kom ihåg [!DNL Bolt]](assets/checked-bolt.png)

- Gästanvändaren gör beställningen och kan registrera sig i Adobe Commerce.

## En befintlig Adobe Commerce-användare: Så här fungerar det

En befintlig användare kan välja befintlig information när en användare gör en beställning med [!DNL Quick Checkout] för en snabbare utcheckning.

När en kund anger en e-postadress i kassan [!DNL Quick Checkout] validerar den för att hitta en befintlig [!DNL Bolt] konto.

### Registrerad [!DNL Bolt] konto hos en Adobe Commerce-användare

Om en [!DNL Bolt] hittar man sitt standardkonto, fortsätter kunderna med sin färdiga Adobe Commerce-utcheckning och shopparen ger all nödvändig information och lägger sedan beställningen:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod

Om du får problem när du gör en beställning som befintlig Adobe Commerce-användare kan du läsa [Felsöka problem med snabbutcheckning](https://support.magento.com/hc/en-us/articles/6909450342541) artikel i Adobe Commerce Help Center.

>[!NOTE]
>
> Om användaren har en [!DNL Bolt] Konto och e-post visas inte som de är registrerade i Adobe Commerce, utan utlöser engångslösenordsinloggningen. Se [registrerad [!DNL Bolt] konto](#registered-bolt-account) flöde.

### Nytt [!DNL Bolt] konto

Om nej [!DNL Bolt] hittar man sitt konto, shoppingkontona fortsätter med sin standardutcheckning av Adobe Commerce och shoppingsidan väljer ut all information de behöver från sin sparade information för att göra beställningen:

- Leverans- och faktureringsinformation
- Leveranssätt
- Granska betalningsmetod
- En kryssruta visas för att registrera dig i [!DNL Bolt] för snabbare utcheckning innan ordern läggs. De kan godkänna villkoren för att skapa sina [!DNL Bolt] konto.

   ![Kom ihåg [!DNL Bolt]](assets/checked-bolt.png)

## Få hjälp

Kontakt [Adobe Commerce Support](mailto:quick-checkout-support@adobe.com) om du behöver hjälp.
