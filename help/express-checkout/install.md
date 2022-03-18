---
title: Installera [!DNL Express Checkout] för Adobe Commerce
description: Följ de här stegen för att installera [!DNL Upgrade Compatibility Tool] för ditt Adobe Commerce-projekt.
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Installera [!DNL Express Checkout]

>[!IMPORTANT]
>
> Den här funktionen är endast avsedd för användare av tidig Adobe-programvara (EAP) och är ännu inte tillgänglig för alla kunder. För närvarande begränsat till amerikanska kunder. Kontakta Adobe Commerce Support för hjälp och frågor.

The [!DNL Express Checkout] för Adobe Commerce ger en smidig utcheckningsupplevelse som utformats för att konvertera engångsköpare till lojala kontoinnehavare.

The [!DNL Express Checkout] tillägg för Adobe Commerce och Magento Open Source kan installeras med Composer-tangenter som är länkade till [Magento ID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} tillhandahölls i registreringsprocessen. I Composer används dessa nycklar vid den första installationen av Adobe Commerce, eller i situationer där Composer-tangenterna inte tidigare sparats i `auth.json` -fil.

Se [hämta dina autentiseringsnycklar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} om du vill ha mer information om hur du hämtar Composer-nycklar.

Det finns två sätt att installera det här tillägget på: [Adobe Commerce i molninfrastruktur](#magento-commerce-cloud) eller [lokal](#on-premises) installationer. Dessa metoder kräver att du använder kommandoradsgränssnittet (CLI).

## Uppdatera inställningen för minsta stabilitet

Innan du installerar tillägget kan du ändra `minimum-stability` krav på `RC` (releaseförslag) i `composer.json` om du vill prova den officiella versionen. Du kan använda en IDE-redigerare eller en textredigerare (som Visual Studio Code eller Sublime Text).

I `composer.json` fil, ändra `"minimum-stability": "stable"` till `"minimum-stability": "RC"`.

## Installera tillägget

Du kan installera [!DNL Express Checkout] för både Adobe Commerce i molninfrastrukturen och lokala instanser.

### Adobe Commerce i molninfrastruktur

Den här metoden används för att installera [!DNL Express Checkout] tillägg för en Commerce Cloud-instans.

1. Byt till rotkatalogen för projektet i molnet på din lokala arbetsstation.

1. Uppdatera dina `composer.json` fil:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update
   ```

   The `composer update` kommandot uppdaterar alla beroenden. Om du inte vill uppdatera alla beroenden samtidigt använder du det här kommandot i stället: `composer update magento/express-checkout`.

1. Verkställ och kör ändringarna.

### Lokalt

Den här metoden används för att installera [!DNL Express Checkout] tillägg för en lokal instans.

1. Lägg till Express Checkout-modulen i `require` i `composer.json` fil:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update
   ```

   The `composer update` kommandot uppdaterar alla beroenden. Om du inte vill uppdatera alla beroenden samtidigt använder du det här kommandot i stället: `composer update magento/express-checkout`.

1. Uppgradera Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```

1. Verkställ ändringarna.
1. Uppdatera din lokala instans för att säkerställa att den implementerade koden distribueras.

## Uppgradera tillägget

När vi släpper en ny version av [!DNL Express Checkout]kan du enkelt uppgradera tillägget.

1. Så här hämtar du den senaste versionen av paketet:

   ```bash
   composer update
   ```

   The `composer update` kommandot uppdaterar alla beroenden. Om du inte vill uppdatera alla beroenden samtidigt använder du det här kommandot i stället: `composer update magento/express-checkout`.

1. Verkställ och kör ändringarna.

## Felsökning

Det kan uppstå fel när du försöker installera [!DNL Express Checkout] tillägg.

Se [felsökning](../express-checkout/troubleshooting.md) om du får mer information om du stöter på problem när du installerar [!DNL Express Checkout].

## Förutsättningar

Se [krav](../express-checkout/prerequisites.md) för mer information.
