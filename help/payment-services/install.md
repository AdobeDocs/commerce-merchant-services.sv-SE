---
title: Installera [!DNL Payment Services]
description: Installera tillägget för Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Installera [!DNL Payment Services]

Hämta och installera [!DNL Payment Services] tillägg för [!DNL Adobe Commerce] och [!DNL Magento Open Source] är ett nödvändigt steg för att använda [!DNL Payment Services].

![[!DNL Payment Services] tilläggsadministratörsvy](assets/admin-view.png)

## Hämta tillägget

Du måste först hämta tillägget från [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) innan du installerar den.

1. Navigera till [Utbyggnaden av betaltjänster i Commerce Marketplace](https://marketplace.magento.com/magento-payment-services.html).
1. Om du vill välja utgåva och version växlar du **[!UICONTROL Edition]** och **[!UICONTROL Your store version]** efter dina val.
1. Klicka **[!UICONTROL Add to Cart]**.
1. Slutför utcheckningen och klicka **[!UICONTROL Place Order]**.
1. Kontrollera e-postmeddelandet som är kopplat till din Marketplace-nedladdning för att få orderbekräftelse och information.

## Installera tillägget

Du kan installera [!DNL Payment Services] tillägg för båda [!DNL Adobe Commerce] på molninfrastruktur och lokala instanser som är länkade till ditt Commerce-konto [mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) anges i registreringsprocessen. [!DNL Magento Open Source] kunderna använder de lokala instruktionerna.

I dispositionen används dessa nycklar vid den första installationen av [!DNL Adobe Commerce]eller i situationer där dispositionsnycklarna inte tidigare sparats i `auth.json` -fil.

Se [Hämta dina autentiseringsnycklar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) om du vill ha mer information om hur du hämtar Composer-nycklar.

Se [Installera ett tillägg](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) om du vill ha mer information om vad du bör tänka på innan du hämtar och installerar ett tillägg.

### [!DNL Adobe Commerce] om molninfrastruktur

Den här metoden används för att installera [!DNL Payment Services] tillägg för en Commerce Cloud-instans.

1. Uppdatera dina `composer.json` fil:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Använd `composer update` om du vill uppdatera alla rotberoenden.

1. Verkställ och kör ändringarna.

### Lokala konfigurationer och andra konfigurationer

Den här metoden används för att installera [!DNL Payment Services] tillägg för en lokal instans och [!DNL Magento Open Source] kunder.

1. Kör följande kommandon för att hämta tillägget:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Använd `composer update` om du vill uppdatera alla rotberoenden.

1. Uppgradera din instans:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```

1. Verkställ ändringarna.
1. Uppdatera instansen för att vara säker på att den implementerade koden distribueras.

## Uppgradera tillägget

När en ny version av [!DNL Payment Services] lanseras kan du enkelt uppgradera tillägget.

1. Så här hämtar du den senaste versionen av paketet:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Använd `composer update` om du vill uppdatera alla rotberoenden.

1. Verkställ och kör ändringarna.

## Felsökning

Det kan uppstå fel när du försöker installera [!DNL Payment Services] tillägg. Använd följande felsökningsmetoder för att åtgärda felen.

### Felaktiga dispositionsnycklar

Om följande fel visar att du har fel Composer-tangenter:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Kontrollera att Composer-tangenterna är giltiga och att du har tillgång till andra Magento-paket.

Så här ser du vilka dispositionsnycklar som är konfigurerade:

1. Hitta platsen för `auth.json` fil:

   ```bash
   composer config --global home
   ```

1. Visa `auth.json` fil:

   ```bash
   cat /path/to/auth.json
   ```

1. Se [vilka nycklar som är kopplade till ditt Commerce-konto `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Det finns inte tillräckligt med minne för PHP

Om följande felmeddelande visas har du inte tillräckligt med minne för PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Öka minnesgränsen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) för PHP i din miljö i `php.ini`.

Du kan också ange minnesgränsen med det här kommandot: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Till exempel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
