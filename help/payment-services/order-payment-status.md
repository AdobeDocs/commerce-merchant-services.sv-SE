---
title: Statusrapport för orderbetalning
description: Använd rapporten Orderbetalningsstatus för att få en bättre överblick över betalningsstatusen för dina order och identifiera eventuella problem.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: cd1c735e9b3be0d75019e0987c84899f9aa66951
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 0%

---

# Statusrapport för orderbetalning

[!DNL Payment Services] för Adobe Commerce och Magento Open Source erbjuder omfattande rapportering så att ni får en tydlig bild av butikens order och betalningar.

![Vyn Finansiella rapporter](assets/reports-view.png)

Med rapporten Orderbetalningsstatus kan du enkelt förstå var en viss order ligger i orderflödet. Med den här rapporten kan du snabbt se betalningsstatus för dina order och identifiera eventuella problem.

Du behöver inte öppna flera vyer för att manuellt korsa referensorder och betalningar. [!DNL Payment Services] för Adobe Commerce och Magento Open Source kan ni få en överblick över era order och betalningar - allt i orderbetalningsstatusrapporten.

Se betalningsstatus, fakturerad och levererad status, återbetalningsstatus, tviststatus med mera, allt i den här rapporten i Admin.

Du kan hämta transaktioner för orderbetalningsstatus i ett CSV-filformat och använda dem i befintliga bokförings- eller orderhanteringsprogram.

>[!NOTE]
>
>Du kan inte visa ekonomiska rapporter om du inte har [Inbyggt och aktiverat Live-läge](production.md#enable-live-payments) for [!DNL Payment Services].

## Data som används i rapporten

The [!DNL Payment Services] använder orderdata och kombinerar dem med aggregerade betalningsdata från andra källor (inklusive PayPal) för att ge meningsfulla och användbara rapporter.

Orderdata exporteras och sparas i betaltjänsten. När du [ändra eller lägga till orderstatus](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;} eller [redigera en butiksvy](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;}, [store](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;}, eller webbplatsnamn, kombineras med betalningsdata och rapporten Orderbetalningsstatus fylls i med den kombinerade informationen.

Det finns två steg i den här processen:

1. Indexet ändras antingen `ON SAVE` (varje gång orderinformation eller butiksinfo ändras) eller `BY SCHEDULE` (enligt ett förkonfigurerat cron-schema), beroende på hur det är konfigurerat i [Indexhantering](https://docs.magento.com/user-guide/system/index-management.html){target=&quot;_blank&quot;} i Admin.

   Som standard sker dataindexering `ON SAVE`, vilket innebär att när något ändras i ordningen, orderstatus, butiksvyn, butiken eller webbplatsen sker omindexeringsprocessen omedelbart.

1. Indexerade data skickas till betalningstjänsten som sedan fylls i i rapporten över orderbetalningsstatus.

De enda data som exporteras och sorteras för rapportändamål är data som används av rapporten om orderbetalningsstatus.

>[!NOTE]
>
>De data som visas i den här tabellen sorteras i fallande ordning (`DESC`) som standard med `ORDER DATE`. The `ORDER DATE` är datum- och tidsstämpeln när ordern skapades.

### Konfigurera dataexport

Även om omindexering som standard sker i `ON SAVE` bör du indexera i `BY SCHEDULE` läge. The `BY SCHEDULE` index körs med ett cron-schema på en minut och alla ändrade data visas i orderstatusrapporten inom två minuter efter dataändringen. Denna schemalagda omindexering hjälper dig att minska eventuella påfrestningar i din butik, särskilt om du har ett stort antal inkommande order, eftersom den inträffar enligt ett schema (inte efter varje beställning).

Du kan ändra indexläge—`ON SAVE` eller `BY SCHEDULE`—[i Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}.

Mer information om hur du konfigurerar dataexporten finns i [Kommandoradskonfiguration](configure-cli.md#configure-data-export).

## Tillgänglighet

På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** för att se betalningsstatus för dina order.

![Beställa betalningsstatus i administratören](assets/order-payment-status-report.png)

## Välj datakälla

I rapportvyn Orderbetalningsstatus kan du välja datakälla:_[!UICONTROL Live]_eller_[!UICONTROL Sandbox]_- som du vill visa rapportresultat för.

![Val av datakällor](assets/datasource.png)

If _[!UICONTROL Live]_är den valda datakällan, du kan se rapportinformation för de butiker som använder [!DNL Payment Services] in_[!UICONTROL Live]_ läge. If [!UICONTROL Sandbox]_ är den valda datakällan, du kan se rapportinformation för din sandlådemiljö.

Datakällmarkeringar fungerar så här:

* Om du inte har några butiker som använder [!DNL Payment Services] i Live-läget är datakällans val som standard [!UICONTROL Sandbox]_.
* Om du har några butiker (en eller flera) som använder [!DNL Payment Services] i Live-läget är datakällans val som standard _[!UICONTROL Live]_.
* Vid export av rapporter respekteras alltid valet av datakälla.

Så här väljer du datakälla för [!UICONTROL Order Payment Status] rapport:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicka **[!UICONTROL Data source]** och markera _[!UICONTROL Live]_eller [!UICONTROL Sandbox]_.

   Rapportresultaten genereras om baserat på den valda datakällan.

## Anpassa tidsram för datum

I rapportvyn Orderbetalningsstatus kan du anpassa tidsramen för statusvärdena som du vill visa genom att välja specifika datum. Som standard visas 30 dagars betalningsstatus i rutnätet.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicka på **[!UICONTROL Order dates]** kalenderväljarfilter.
1. Välj tillämpligt datumintervall.
1. Visa betalningsstatus för dina angivna datum i rutnätet.

## Visa statusvärden

Som standard visas 30 dagars betalningsstatus i rutnätet.

Bläddra åt vänster och höger för att visa [statusinformation för orderbetalning](#column-descriptions), inklusive orderdatum, auktoriserat datum, fakturerad, levererad, lönestatus med mera.

Antalet rader som returneras i en sökning, eller som visas i standardinställningstiden på 30 dagar för orderbetalningsstatus, visas ovanför vystödrastret för orderbetalningsstatus bredvid väljarfiltret för orderdatumkalender.

## Uppdatera rapportdata

I rapportvyn över orderbetalningsstatus visas en _[!UICONTROL Last updated]_tidsstämpel som visar senaste gången rapportinformationen uppdaterades. Som standard uppdateras rapportdata för orderbetalningsstatus automatiskt var tredje timme.

Du kan också manuellt framtvinga en uppdatering av rapportdata för orderbetalningsstatus för att se den senaste rapportinformationen.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicka på _Uppdatera_ ikon (![uppdateringsikon](assets/refresh-button-med.png)).

   Rapportdata för orderbetalningsstatus uppdateras, och *[!UICONTROL Update complete]* visas och den senaste informationen finns i rutnätet.

## Hämta betalningsstatus för order

Du kan hämta en CSV-fil med alla statusvärden synliga i vystödrastret för orderbetalningsstatus, oavsett om du visar standardstatusvärdena för 30 dagar eller en anpassad tidsram.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Om du vill se statusvärden under en annan tidsram än de senaste 30 dagarna [anpassa tidsramen för datumintervallet för statusvärdena](#customize-dates-timeframe).
1. Klicka på _Hämta_ (![hämtningsikon](assets/icon-download.png)).

Din orderbetalningsstatus hämtas i .csv-format.

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

## Statusinformation för orderbetalning

I orderbetalningsstatusvyn visas omfattande information om alla statusvärden som visas i rutnätet.

### Kolumnbeskrivningar

Rapporter om orderbetalningsstatus innehåller följande information.

| Kolumn | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Handelsordernr<br> <br>För att se relaterade [orderinformation](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, klicka på ID:t. |
| [!UICONTROL Order Date] | Tidsstämpel för orderdatum |
| [!UICONTROL Authorized Date] | Datum och tidsstämpel för betalningsauktorisering |
| [!UICONTROL Order Status] | Aktuell handel [orderstatus](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot;} |
| [!UICONTROL Invoiced] | Fakturastatus för ordern—*[!UICONTROL No]*, *[!UICONTROL Partial]*, eller *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Leveransstatus för beställning—*[!UICONTROL No]*, *[!UICONTROL Partial]*, eller *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Orderns totalbelopp |
| [!UICONTROL Cur] | Valutatyp för order |
| [!UICONTROL Pay Status] | Status för betalning för en viss order |
| [!UICONTROL Paid Amt] | Betalat belopp på en order |
| [!UICONTROL Cur] | Valutatyp för beloppet som betalats på en order |
| [!UICONTROL Refund Status] | Status för en återbetalning på en order (t.ex. information från returer, RMA och kreditnotor)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]*, eller *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Totalt återbetalt belopp för en order |
| [!UICONTROL Cur] | Valutatyp för beloppet som återbetalas för en order |
| [!UICONTROL Dispute Status] | Status för en tvist om ett beslut (information från tvister och återbetalningar)—*[!UICONTROL New]*, *[!UICONTROL Representment]*, *[!UICONTROL Accepted]*, *[!UICONTROL Pre-arbitration received]*, *[!UICONTROL Arbitration]*, eller *[!UICONTROL Arbitration received]* |
| [!UICONTROL Payment Method] | Betalningsmetod som används i handelstransaktionen för en order |
| [!UICONTROL Website] | Webbplats där beställningen gjordes |
| [!UICONTROL Store] | Butiker som ordern placerades från |
| [!UICONTROL Store View] | Butiksvy som ordern placerades från |
