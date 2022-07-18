---
title: '"[!DNL Payment Services] Versionsinformation"'
description: Läs versionsinformationen om du vill ha information om alla [!DNL Payment Services] releaser.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 7c02bb8dcb7b5daa68664bd12672ac389f84cfa1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionsinformation

I versionsinformationen beskrivs den första versionen av [!DNL Payment Services] och innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigerat problem](../assets/fix.svg) Korrigeringar och förbättringar
![Känt fel](../assets/bug.svg) Kända fel

Information om funktionsändringar och korrigeringar som släppts utanför den vanliga versionen finns i avsnittet om uppdateringar av värdtjänsten.

Se [Kommande versioner](https://devdocs.magento.com/release/) om du vill veta mer om releasescheman och support.

Se [Tillgänglighet](https://devdocs.magento.com/release/availability.html) i utvecklardokumentationen om du vill veta mer om produktkompatibilitet.

## v1.2.0

_29 juni 2022_

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3264 --> När en inloggad användare tidigare har valt en annan fakturerings-/leveransadress än standardadressen för sitt konto misslyckades utcheckningen. Vi har åtgärdat problemet och nu skickas den valda fakturerings-/leveransadressen (i stället för den sparade standardadressen) och utcheckningen har slutförts.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3314 --> Om du inaktiverar smarta PayPal-knappar för utcheckning visas inga fel.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3330 --> Betalningar misslyckas inte längre vid utcheckning när en gästanvändare anger ett telefonnummer som innehåller streck.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> När autentiseringsuppgifterna för Commerce Services är ogiltiga visas [!DNL Payment Services] Startsidan visas nu i Admin. Ett inloggningsfel visas som varnar dig om att inloggningsuppgifterna är ogiltiga.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] är för närvarande inte kompatibelt med [`commerce-data-export` v101.20 och senare](https://github.com/magento-commerce/commerce-data-export/releases/tag/v101.2.0)som gör den inkompatibel med [[!DNL Channel manager] extension](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

### Uppdateringar av värdtjänster

I versionsinformationen beskrivs funktionsändringar och korrigeringar som har gjorts och släppts utanför de vanliga versionerna av funktionsreleaserna, mellan den aktuella version av v1.2.0 och den tidigare version av 1.1.0 av värdtjänsten.

![Nytt](../assets/new.svg)<!-- Issue PAY-1720 --> Tvister för butiksorder finns nu i [statusrapport för orderbetalning](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Du kan navigera direkt till PayPal Resolution Center från [!DNL Payment Services] att vidta åtgärder i tvister.

![Nytt](../assets/new.svg)<!-- Issue PAY-2854 --> Förbättringar av användarupplevelsen från [!DNL Payment Services] På startsidan kan du ändra en konfiguration på den aktuella arvsnivån och förbättra visningen av rubriken och navigeringen.

![Nytt](../assets/new.svg)<!-- Issue PAY-2854 --> Du kan nu se varningar när du växlar från sandlådeläge till produktionsläge och när du försöker navigera bort från en vy med uppdateringar som inte har sparats.

![Nytt](../assets/new.svg)<!-- Issue PAY-2761 --> Nu kan du anpassa de data som visas i [Statusrapport för orderbetalning](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) och [Utbetalningsrapport](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) genom att visa eller dölja kolumner med hjälp av kontrollen för kolumninställningar.

## v1.1.0

_31 mars 2022_

![Nytt](../assets/new.svg)<!-- Issue PAY-2127 --> Allmän tillgänglighetsrelease—[!DNL Payment Services] är nu [kompatibel med [!DNL Adobe Commerce] och [!DNL Magento Open Source] version 2.4.0 till 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nytt](../assets/new.svg)<!-- Issue PAY-2682 --> The [!DNL Payment Services] tillägg för [!DNL Adobe Commerce] och [!DNL Magento Open Source] finns nu för kanadensiska handlare. Handlare kan visa betalningskonfigurationen i antingen [Franska](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) eller [Engelska](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![Nytt](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] supports [Kanadensiska dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) för kreditkort och PayPal-transaktioner.

![Nytt](../assets/new.svg)<!-- Issue PAY-2680 --> Handlare kan [inbyggt [!DNL Payment Services]](onboard.md) på engelska eller franska.

![Nytt](../assets/new.svg)<!-- Issue PAY-2678 --> Handläggarna kan nu visa ekonomiska rapporter, både [Status för orderbetalning](order-payment-status.md) och [Utbetalningsrapporter](payouts.md), i kanadensiska dollar (CAD).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] är nu kompatibelt med [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3017 --> Förbättrad sandlådelägesvarning för att visa korrekta varningar i flera butiker.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2742 --> Du kan nu aktivera och inaktivera tillgängliga betalningsmetoder, som Venmo, på butiksvynivå. Tidigare kunde du bara konfigurera betalningsmetoder per webbplats.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2277 --> Du kan nu välja [aktivera eller inaktivera enskilda smarta PayPal-knappar](settings.md#payment-buttons).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2561 --> Tidigare borttagna produkter visas inte i kundvagnen på _Granska beställning_ sida.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2842 --> Testa kreditkortstransaktioner [kan misslyckas med PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) när betalningar bearbetas i en sandlådemiljö.

## v1.0.0

_29 november 2021_

![Nytt](../assets/new.svg)<!-- Issue PAY-2127 --> Allmän tillgänglighetsrelease—[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) är nu kompatibelt med [!DNL Adobe Commerce] och [!DNL Magento Open Source] version 2.4.0 till 2.4.3-p1.

![Nytt](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] tillägg för [!DNL Adobe Commerce] och [!DNL Magento Open Source] kan installeras för [[!DNL Adobe Commerce] om molninfrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) eller [Lokalt](install.md#on-premises) -instanser. Dessa metoder kräver att ett kommandoradsgränssnitt används.

![Nytt](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] har stöd för [sandlådekonto](sandbox.md) som gör det möjligt för handlare att bedöma tillägget i testläge.

![Nytt](../assets/new.svg)<!-- Issue PAY-666 --> Handlare kan [konfigurera betalningstjänsterna](settings.md) tillägg med grundläggande betalningsbeteenden, som att använda [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) växla mellan sandlådor och produktionsmiljöer.

![Nytt](../assets/new.svg)<!-- Issue PAY-780 --> Dina kunder kan kolla in med [!DNL Payment Services] eller via [manuell orderhantering](create-order.md).

![Nytt](../assets/new.svg)<!-- Issue PAY-1856 --> Omfattande rapportering, via [Status för orderbetalning](order-payment-status.md) och [Utbetalningsrapporter](payouts.md), är tillgängliga för [!DNL Payment Services] för att ge dig en tydlig bild av butikens order och tillhörande betalningar.

![Nytt](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] stöder flexibla nivåbaserade priser, baserade på den totala bearbetningsvolymen, anpassade till alla handlare.

![Nytt](../assets/new.svg)<!-- Issue PAY-1443 --> Du kan enkelt [anpassa utseende och känsla](payments-options.md) av smarta PayPal-knappar och kreditkortsfält för [!DNL Payment Services] tillägg.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2473 --> Använda [felaktiga dispositionsnycklar](https://support.magento.com/hc/en-us/articles/4406603542541) under installationen av tillägget förhindrar användaren från att [autentisera](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) med rätt `MAGEID`.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] rapporter [kan inte synkroniseras omedelbart](https://support.magento.com/hc/en-us/articles/4406114741517).

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2475 --> Dina [PayPal-sandlådekonto](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] kan inte verifieras om du skapar det kontot under introduktionen.
