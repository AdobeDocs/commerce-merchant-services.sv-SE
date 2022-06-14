---
title: '"[!DNL Payment Services] Versionsinformation"'
description: Läs versionsinformationen om du vill ha information om alla [!DNL Payment Services] releaser.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionsinformation

I versionsinformationen beskrivs den första versionen av [!DNL Payment Services] och innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigerat problem](../assets/fix.svg) Korrigeringar och förbättringar
![Känt fel](../assets/bug.svg) Kända fel

Se [Kommande versioner](https://devdocs.magento.com/release/) om du vill veta mer om releasescheman och support.

Se [Tillgänglighet](https://devdocs.magento.com/release/availability.html) i utvecklardokumentationen om du vill veta mer om produktkompatibilitet.

## v1.1.0

![Nytt](../assets/new.svg)<!-- Issue PAY-2127 --> Allmän tillgänglighetsrelease—[!DNL Payment Services] är nu [kompatibel med [!DNL Adobe Commerce] och [!DNL Magento Open Source] version 2.4.0 till 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nytt](../assets/new.svg)<!-- Issue PAY-2682 --> The [!DNL Payment Services] tillägg för [!DNL Adobe Commerce] och [!DNL Magento Open Source] finns nu för kanadensiska handlare. Handlare kan visa betalningskonfigurationen i antingen [Franska](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) eller [Engelska](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![Nytt](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] supports [Kanadensiska dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) för kreditkort och PayPal-transaktioner.

![Nytt](../assets/new.svg)<!-- Issue PAY-2680 --> Handlare kan [inbyggt [!DNL Payment Services]](onboard.md) på engelska eller franska.

![Nytt](../assets/new.svg)<!-- Issue PAY-2678 --> Handläggarna kan nu visa ekonomiska rapporter, både [Status för orderbetalning](order-payment-status.md) och [Utbetalningsrapporter](payouts.md), i kanadensiska dollar (CAD).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] är nu kompatibelt med [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3017 --> Förbättrad sandlådelägesvarning för att visa korrekta varningar i flera butiker.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2742 --> Du kan nu aktivera och inaktivera tillgängliga betalningsmetoder, som Venmo, på butiksvynivå. Tidigare kunde du bara konfigurera betalningsmetoder per webbplats.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2277 --> Du kan nu välja [aktivera eller inaktivera enskilda smarta PayPal-knappar](settings.md#paypal-smart-buttons).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2561 --> Tidigare borttagna produkter visas inte i kundvagnen på _Granska beställning_ sida.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2842 --> Testa kreditkortstransaktioner [kan misslyckas med PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) när betalningar bearbetas i en sandlådemiljö.

## v1.0.0

![Nytt](../assets/new.svg)<!-- Issue PAY-2127 --> Allmän tillgänglighetsrelease—[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) är nu kompatibelt med [!DNL Adobe Commerce] och [!DNL Magento Open Source] version 2.4.0 till 2.4.3-p1.

![Nytt](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] tillägg för [!DNL Adobe Commerce] och [!DNL Magento Open Source] kan installeras för [[!DNL Adobe Commerce] om molninfrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) eller [Lokalt](install.md#on-premises) -instanser. Dessa metoder kräver att ett kommandoradsgränssnitt används.

![Nytt](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] har stöd för [sandlådekonto](sandbox.md) som gör det möjligt för handlare att bedöma tillägget i testläge.

![Nytt](../assets/new.svg)<!-- Issue PAY-666 --> Handlare kan [konfigurera betalningstjänsterna](settings.md) tillägg med grundläggande betalningsbeteenden, som att använda [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) växla mellan sandlådor och produktionsmiljöer.

![Nytt](../assets/new.svg)<!-- Issue PAY-780 --> Dina kunder kan kolla in med [!DNL Payment Services] eller via [manuell orderhantering](create-order.md).

![Nytt](../assets/new.svg)<!-- Issue PAY-1856 --> Omfattande rapportering, via [Status för orderbetalning](order-payment-status.md) och [Utbetalningsrapporter](payouts.md), är tillgängliga för [!DNL Payment Services] för att ge dig en tydlig bild av butikens order och tillhörande betalningar.

![Nytt](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] stöder flexibla nivåbaserade priser, baserade på den totala bearbetningsvolymen, anpassade till alla handlare.

![Nytt](../assets/new.svg)<!-- Issue PAY-1443 --> Du kan enkelt [anpassa utseende och känsla](payments-options.md) av smarta PayPal-knappar och kreditkortsfält för tillägget Betalningstjänster.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2473 --> Använda [felaktiga dispositionsnycklar](https://support.magento.com/hc/en-us/articles/4406603542541) under installationen av tillägget förhindrar användaren från att [autentisera](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) med rätt `MAGEID`.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] rapporter [kan inte synkroniseras omedelbart](https://support.magento.com/hc/en-us/articles/4406114741517).

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2475 --> Dina [PayPal-sandlådekonto](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] kan inte verifieras om du skapar det kontot under introduktionen.
