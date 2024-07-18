---
title: Installera [!DNL Payment Services]
description: Installera tillägget för Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 692a7e55d72b1e2f1a161d508be5e179c4d26bde
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Installera [!DNL Payment Services]

Om du vill börja använda betalningstjänsterna för [!DNL Adobe Commerce] och [!DNL Magento Open Source] måste du slutföra några startsteg.

>[!INFO]
>
> Mer information finns i videon [Konfigurera [!DNL Payment Services] för Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services).

Hämtning och installation av tillägget [!DNL Payment Services] för [!DNL Adobe Commerce] och [!DNL Magento Open Source] är ett nödvändigt steg för att använda [!DNL Payment Services].

![[!DNL Payment Services] tilläggsadministratörsvy](assets/admin-view.png){width="300" zoomable="yes"}

## Hämta tillägget

Du måste hämta tillägget från [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) innan du installerar det.

1. Navigera till tillägget [Betalningstjänster i Commerce Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. Om du vill välja utgåva och version växlar du **[!UICONTROL Edition]** och **[!UICONTROL Your store version]** till de alternativ du vill använda.
1. Klicka på **[!UICONTROL Add to Cart]**.
1. Slutför utcheckningen och klicka på **[!UICONTROL Place Order]**.
1. Kontrollera e-postmeddelandet som är kopplat till din Marketplace-nedladdning för att få orderbekräftelse och information.

## Installera tillägget

Du kan installera tillägget [!DNL Payment Services] för både [!DNL Adobe Commerce] i molninfrastrukturen och lokala instanser, som är länkade till ditt Commerce-konto [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) som tillhandahålls i registreringsprocessen.
[!DNL Magento Open Source]-kunder använder de lokala instruktionerna.

I dispositionen används dessa nycklar vid den första installationen av [!DNL Adobe Commerce], eller i situationer där dispositionsnycklarna inte tidigare sparats i filen `auth.json`.

Mer information om hur du hämtar Composer-nycklar finns i [Hämta dina autentiseringsnycklar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

Mer information om vad du bör tänka på innan du hämtar och installerar ett tillägg finns i [Installera ett tillägg](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html).

### [!DNL Adobe Commerce] i molninfrastruktur

Den här metoden används för att installera tillägget [!DNL Payment Services] för en Commerce Cloud-instans.

1. Uppdatera din `composer.json`-fil:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Använd kommandot `composer update` för att uppdatera alla rotberoenden.

1. Verkställ och push-styr ändringarna.

### Lokala konfigurationer och andra konfigurationer

Den här metoden används för att installera tillägget [!DNL Payment Services] för en lokal instans och [!DNL Magento Open Source]-kunder.

1. Kör följande kommandon för att hämta tillägget:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Använd kommandot `composer update` för att uppdatera alla rotberoenden.

1. Uppgradera din instans:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```

1. Verkställ ändringarna.
1. Uppdatera instansen för att vara säker på att den implementerade koden distribueras.

## Uppgradera tillägget

När en ny version av [!DNL Payment Services] släpps kan du enkelt uppgradera ditt tillägg.

1. Så här hämtar du den senaste versionen av paketet:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Använd kommandot `composer update` för att uppdatera alla rotberoenden.

1. Verkställ och push-styr ändringarna.

## Felsökning

Fel kan uppstå när tillägget [!DNL Payment Services] installeras. Använd följande felsökningsmetoder för att åtgärda felen.

### Felaktiga dispositionsnycklar

Om följande fel visar att du har fel Composer-tangenter:

```
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Kontrollera att Composer-tangenterna är giltiga och att du har tillgång till andra Magento-paket.

Så här ser du vilka dispositionsnycklar som är konfigurerade:

1. Hitta platsen för filen `auth.json`:

   ```bash
   composer config --global home
   ```

1. Visa filen `auth.json`:

   ```bash
   cat /path/to/auth.json
   ```

1. Se [vilka nycklar som är associerade med ditt Commerce-konto `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Inte tillräckligt med minne för PHP

Om följande felmeddelande visas har du inte tillräckligt med minne för PHP:

```
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Öka minnesgränsen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) för PHP i din miljö i `php.ini`.

Du kan också ange minnesgränsen med det här kommandot: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Exempel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
