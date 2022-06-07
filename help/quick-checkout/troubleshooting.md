---
title: '"Felsökning för [!DNL Quick Checkout]"'
description: '"Felsöka fel, kända fel som kan uppstå när du använder [!DNL Quick Checkout] för Adobe Commerce."'
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Felsökning [!DNL Quick Checkout] för Adobe Commerce

Använd följande felsökningsmetoder för att lösa dessa specifika problem.

## Felaktig [!DNL Composer keys]

Om följande felmeddelande visas har du fel [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Verifiera att [!DNL Composer keys] är länkade till det Magento-ID som användes vid registreringen av Snabbutcheckning.

För att se vilka [!DNL Composer keys] är konfigurerade:

1. Hitta platsen för `auth.json` fil:

   ```bash
   composer config --global home
   ```

1. Visa `auth.json` fil:

   ```bash
   cat /path/to/auth.json
   ```

1. Se [vilka tangenter som är kopplade till ditt Magento-ID](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

## Minsta stabilitet i `composer.json` är inställt på stabil

Om följande felmeddelande visas har du fel [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Ange lägsta stabilitet till `RC` i `composer.json` -fil.

## Det finns inte tillräckligt med minne för PHP

Om följande felmeddelande visas har du inte tillräckligt med minne för PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Öka minnesgränsen](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) för PHP i din miljö i `php.ini`.

Du kan också ange minnesgränsen med det här kommandot: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Exempel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Ogiltig leveransadress

Det finns ett känt problem med [!DNL Quick Checkout].

När standardleveransadressen inte är giltig dirigeras kunden till leveransadresssteget. Endast giltiga leveransadresser visas i butiken.

>[!WARNING]
>
> om det inte finns några giltiga leveransadresser, kan kunden inte se någon tillgänglig leveransadress.

Se [leveransinformation](../quick-checkout/shipping-details.md) för mer information.

## Lägg till gatuadressrader med en ny leveransadress

Det finns ett känt problem med [!DNL Quick Checkout].

När du [logga in med [!DNL Bolt] konto](https://help.bolt.com/shoppers/guides/checkout/log-in/) Du kan lägga till en ny leveransadress med en begränsning på 4 rader per gatuadress.

Adobe Commerce kan vanligtvis konfigureras för att stödja upp till 20 gatuadressrader.

## Kryssruta `enable terms and conditions` visas inte korrekt

Det finns ett känt problem med [!DNL Quick Checkout].

När du aktiverar `Enable terms and conditions` kryssrutan i Admin och logga in med [!DNL Bolt] konto, `Enable terms and conditions` kryssrutan visas inte under utcheckningen. Se [Logga in](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] för mer information.

Se [villkor](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) om du vill ha mer information om Admin-konfigurationen.

## Oväntat beteende när `Display Billing Address On` är inställd på `payment page`

Det finns ett känt problem med [!DNL Quick Checkout].

Om du anger `Display Billing Address On` parameter till `payment page` och [logga in med [!DNL Bolt] konto](https://help.bolt.com/shoppers/guides/checkout/log-in/) när du markerar `My billing and shipping address are the same` kryssrutan som visas på alternativknappen `use existing card`.

![Samma adress](assets/checked-address.png)

Se [Utcheckning](https://docs.magento.com/user-guide/configuration/sales/checkout.html) om du vill ha mer information om `Display Billing Address On` parameter.

## Översätta [!DNL Quick Checkout] extension

Med Adobe Commerce kan ni lokalisera er butik i flera regioner och på flera marknader. Du kan till och med lokalisera felmeddelanden i administrationsvyn.

Se [översätta och lokalisera](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) för mer information.

## Töm cacheminnet

1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

## Få hjälp

Kontakt [Adobe Commerce Support](mailto:quick-checkout-support@adobe.com) om du behöver hjälp.
