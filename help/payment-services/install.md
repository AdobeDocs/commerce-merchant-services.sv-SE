---
title: Installera [!DNL Payment Services]
description: Installera tillägget för Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Installera [!DNL Payment Services]

Installera [!DNL Payment Services] tillägg för Adobe Commerce och Magento Open Source är ett nödvändigt steg för att använda [!DNL Payment Services].

![[!DNL Payment Services] tilläggsadministratörsvy](assets/admin-view.png)

The [!DNL Payment Services] tillägg för Adobe Commerce och Magento Open Source kan installeras med Composer-tangenter som är länkade till Magento-ID ([mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) anges i registreringsprocessen. I Composer används dessa nycklar vid den första installationen av Adobe Commerce, eller i situationer där Composer-tangenterna inte tidigare sparats i `auth.json` -fil.

Se [Hämta dina autentiseringsnycklar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) om du vill ha mer information om hur du hämtar Composer-nycklar.

Det finns två sätt att installera det här tillägget på: [Adobe Commerce i molninfrastruktur](https://devdocs.magento.com/payment-services/install-payments.html#magento-commerce-cloud) eller [Lokalt](https://devdocs.magento.com/payment-services/install-payments.html#on-premises) installationer. Dessa metoder kräver att du använder kommandoradsgränssnittet (CLI).

## Uppdatera inställningen för minsta stabilitet

Innan du installerar tillägget måste du ändra `minimum-stability` krav på `RC` (releaseförslag) i `composer.json` -fil. Du kan använda en IDE-redigerare eller en textredigerare (som Visual Studio Code eller Sublime Text).

I `composer.json` fil, ändra `"minimum-stability": "stable"` till `"minimum-stability": "RC"`.

## Installera tillägget

Du kan installera [!DNL Payment Services] för både Adobe Commerce i molninfrastrukturen och lokala instanser.

### Adobe Commerce i molninfrastruktur

Den här metoden används för att installera [!DNL Payment Services] tillägg för en Commerce Cloud-instans.

1. Uppdatera dina `composer.json` fil:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update
   ```

   The `composer update` kommandot uppdaterar alla beroenden. Om du inte vill uppdatera alla beroenden samtidigt använder du det här kommandot i stället: `composer require magento/payment-services`.

1. Verkställ och kör ändringarna.

### Lokalt

Den här metoden används för att installera [!DNL Payment Services] tillägg för en lokal instans.

1. Kör följande kommandon för att hämta tillägget:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update
   ```

   The `composer update` kommandot uppdaterar alla beroenden. Om du inte vill uppdatera alla beroenden samtidigt använder du det här kommandot i stället: `composer require magento/payment-services`.

1. Uppgradera Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```

1. Verkställ ändringarna.
1. Uppdatera din lokala instans för att se till att den implementerade koden distribueras.

## Uppgradera tillägget

När en ny version av [!DNL Payment Services] lanseras kan du enkelt uppgradera tillägget.

1. Så här hämtar du den senaste versionen av paketet:

   ```bash
   composer update
   ```

   The `composer update` kommandot uppdaterar alla beroenden. Om du inte vill uppdatera alla beroenden samtidigt använder du det här kommandot i stället: `composer update magento/payment-services`.

1. Verkställ och kör ändringarna.

## Felsökning

Det kan uppstå fel när du försöker installera [!DNL Payment Services] tillägg. Använd följande felsökningsmetoder för att åtgärda felen.

### Felaktiga dispositionsnycklar

Om följande fel visar att du har fel Composer-tangenter:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Kontrollera att dispositionsnycklarna är länkade till Magento-ID:t som används under [!DNL Payment Services] registrering.

Så här ser du vilka dispositionsnycklar som är konfigurerade:

1. Hitta platsen för `auth.json` fil:

   ```bash
   composer config --global home
   ```

1. Visa `auth.json` fil:

   ```bash
   cat /path/to/auth.json
   ```

1. Se [vilka tangenter som är kopplade till ditt Magento-ID](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Det finns inte tillräckligt med minne för PHP

Om följande felmeddelande visas har du inte tillräckligt med minne för PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Öka minnesgränsen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) för PHP i din miljö i `php.ini`.

Du kan också ange minnesgränsen med det här kommandot: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Exempel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
