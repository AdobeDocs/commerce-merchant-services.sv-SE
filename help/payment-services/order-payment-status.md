---
title: Statusrapport för orderbetalning
description: Använd rapporten Orderbetalningsstatus för att få en bättre överblick över betalningsstatusen för dina order och identifiera eventuella problem.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: 8295b7c4ea407f0528d6be69655a8b12f7defe15
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 0%

---

# Statusrapport för orderbetalning

[!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] ger er omfattande rapportering så att ni kan få en tydlig bild av butikens order och betalningar.

Det finns två tillgängliga rapportvyer över orderbetalningsstatus som gör att du snabbt kan visa betalningsstatus för dina order:

* **[Visualisering av orderbetalningsstatus](#order-payment-status-data-visualization-view)**—Diagram som är tillgänglig på startsidan för Betalningstjänster som är en visuell representation av aggregerade betalningsstatusar per dag från rapportvyn Orderbetalningsstatus
* **[Rapportvy för orderbetalningsstatus](#order-payment-status-report-view)**—Rapport tillgänglig i orderbetalningsstatus som visar detaljerad betalning, fakturering, leverans, återbetalning och tviststatus för alla transaktioner

Med orderbetalningsstatusvyerna blir det enkelt att förstå var en viss order ligger i orderns kassaprocessflöde. Med hjälp av de här rapporterna kan du snabbt visa beställningar, baserat på betalningsstatus och betalningsdatum, och identifiera eventuella problem.

Du kan hämta transaktioner för orderbetalningsstatus i ett CSV-filformat och använda dem i befintliga bokförings- eller orderhanteringsprogram.

>[!NOTE]
>
>Du kan inte visa ekonomiska rapporter om du inte har [Inbyggt och aktiverat Live-läge](production.md#enable-live-payments) for [!DNL Payment Services].

## Datavisualisering av orderbetalningsstatus

Vyn över orderbetalningsstatus är tillgänglig på startsidan för Betalningstjänster. Det är en visuell representation av de aggregerade betalningsstatusarna per dag från den detaljerade tabellen [Rapportvy för orderbetalningsstatus](#order-payment-status-report-view).

På _Administratör_ sidebar, gå till **Försäljning** > **Betalningstjänster** för att se datavisualiseringen [betalningsstatusdiagram](#statuses-information).

![Visualisering av utbetalningsdata i administratören](assets/orderpayment-dataviz.png){zoomable=yes}

Klicka **Visa rapport** för att navigera till den detaljerade tabellen [Rapportvy för orderbetalningsstatus](#order-payment-status-report-view).

### Anpassa tidsram för statusvärden

Som standard visas 30 dagars betalningsstatus.

I visualiseringsvyn för orderbetalningsstatus kan du anpassa tidsramen för de betalningsstatusar du vill visa genom att välja ett datumintervall:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Vyn för visualisering av orderbetalningsstatus visas i avsnittet Status för orderbetalning.
1. Klicka på **[!UICONTROL Range]** väljarfilter.
1. Välj datumintervall: 30 dagar, 15 dagar eller 7 dagar.
1. Visa statusinformation för angivna datum.

### Statusinformation

Betalningsstatusarna för ett valt datumintervall visas till vänster om visualiseringsvyn för orderbetalningsstatus. Datumen för det valda datumintervallet visas längst ned i vyn. Om det inte fanns några order på ett visst datum visas inte det datumet.

Vyn för visualisering av orderbetalningsstatus innehåller följande information.

| Data | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Mängdintervall för order inom angiven tidsram. data på Y-axeln (vänster) |
| Datumintervall | Datumintervall för den angivna tidsramen. data på X-axeln (nederst) |
| Auktoriserad | Beställning auktoriserad |
| Hämtning begärd | Hämtning begärd för beställning |
| Hämtningen har bekräftats | Orderinspelningen är klar |
| Delvis hämtning | Ordning som delvis fångats |
| Hämtningen misslyckades | Orderhämtningen misslyckades |
| Annullerad | Order annullerad |

## Rapportvy för orderbetalningsstatus

Vyn Orderbetalningsstatus är tillgänglig i vyn Orderbetalningsstatus i Betalningstjänster. Den innehåller detaljerade statusvärden - betalning, fakturering, leverans, återbetalning, tvist med mera - för alla transaktioner. The [Datavisualisering av orderbetalningsstatus](#order-payment-status-data-visualization-view) i Startsidan för betaltjänster är en visuell representation av aggregerade betalningsstatusar per dag från rapportvyn för orderbetalningsstatus.

På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** om du vill visa en detaljerad rapportvy över orderbetalningsstatus i tabellform.

![Beställa betalningstatustransaktioner i administratören](assets/orders-report-data.png)

Du kan konfigurera den här vyn, per avsnitt i det här avsnittet, så att du på bästa sätt kan presentera de data du vill se.

Du kan [ladda ned utbetalningstransaktioner](#download-order-payment-statuses) i ett CSV-filformat som kan användas i befintliga redovisnings- eller orderhanteringsprogram.

>[!NOTE]
>
>De data som visas i den här tabellen sorteras i fallande ordning (`DESC`) som standard med `TRANS DATE`. The `TRANS DATE` är det datum och den tidpunkt då transaktionen initierades.

### Data som används i rapporten

The [!DNL Payment Services] Modulen använder orderdata och kombinerar dem med aggregerade betalningsdata från andra källor (inklusive PayPal) för att tillhandahålla meningsfulla och användbara rapporter.

Orderdata exporteras och sparas i betaltjänsten. När du [ändra eller lägga till orderstatus](https://docs.magento.com/user-guide/sales/order-status-custom.html){target="_blank"} or [edit a store view](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target="_blank"}, [store](https://docs.magento.com/user-guide/stores/store-information.html){target="_blank"}, eller webbplatsnamn, kombineras med betalningsdata och rapporten Orderbetalningsstatus fylls i med den kombinerade informationen.

Det finns två steg i den här processen:

1. Indexet ändras antingen `ON SAVE` (varje gång orderinformation eller butiksinfo ändras) eller `BY SCHEDULE` (enligt ett förkonfigurerat cron-schema), beroende på hur det är konfigurerat i [Indexhantering](https://docs.magento.com/user-guide/system/index-management.html){target="_blank"} i Admin.

   Som standard sker dataindexering `ON SAVE`, vilket innebär att när något ändras i ordningen, orderstatus, butiksvyn, butiken eller webbplatsen sker omindexeringsprocessen omedelbart.

1. Indexerade data skickas till betalningstjänsten som sedan fylls i i rapporten över orderbetalningsstatus.

De enda data som exporteras och sorteras för rapportändamål är data som används av rapporten om orderbetalningsstatus.

>[!NOTE]
>
>De data som visas i den här tabellen sorteras i fallande ordning (`DESC`) som standard med `ORDER DATE`. The `ORDER DATE` är datum- och tidsstämpeln när ordern skapades.

#### Konfigurera dataexport

Även om omindexering som standard sker i `ON SAVE` bör du indexera i `BY SCHEDULE` läge. The `BY SCHEDULE` index körs med ett cron-schema på en minut och alla ändrade data visas i orderstatusrapporten inom två minuter efter dataändringen. Denna schemalagda omindexering hjälper dig att minska eventuella påfrestningar i din butik, särskilt om du har ett stort antal inkommande order, eftersom den inträffar enligt ett schema (inte efter varje beställning).

Du kan ändra indexläge—`ON SAVE` eller `BY SCHEDULE`—[i Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"}.

Mer information om hur du konfigurerar dataexporten finns i [Kommandoradskonfiguration](configure-cli.md#configure-data-export).

### Välj datakälla

I rapportvyn Orderbetalningsstatus kan du välja datakälla:_[!UICONTROL Live]_eller_[!UICONTROL Sandbox]_- som du vill visa rapportresultat för.

![Val av datakällor](assets/datasource.png){width=400px}

If _[!UICONTROL Live]_är den valda datakällan, du kan se rapportinformation för de butiker som använder [!DNL Payment Services] i produktionsläge. If_[!UICONTROL Sandbox]_ är den valda datakällan, kan du visa rapportinformation för sandlådeläge.

Datakällmarkeringar fungerar så här:

* Om du inte har några butiker som använder [!DNL Payment Services] i Live-läget är datakällans val som standard _[!UICONTROL Sandbox]_.
* Om du har några butiker (en eller flera) som använder [!DNL Payment Services] i Live-läget är datakällans val som standard _[!UICONTROL Live]_.
* Vid export av rapporter respekteras alltid valet av datakälla.

Så här väljer du datakälla för [!UICONTROL Order Payment Status] rapport:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicka **[!UICONTROL Data source]** och markera _[!UICONTROL Live]_eller_[!UICONTROL Sandbox]_.

   Rapportresultaten genereras om baserat på den valda datakällan.

### Anpassa tidsram för datum

I rapportvyn Orderbetalningsstatus kan du anpassa tidsramen för statusvärdena som du vill visa genom att välja specifika datum. Som standard visas 30 dagars betalningsstatus i rutnätet.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicka på **[!UICONTROL Order dates]** kalenderväljarfilter.
1. Välj tillämpligt datumintervall.
1. Visa betalningsstatus för dina angivna datum i rutnätet.

### Visa och dölja kolumner

I rapporten Orderbetalningsstatus visas alla tillgängliga informationskolumner som standard. Du kan dock anpassa vilka kolumner som visas i rapporten.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicka på _Kolumninställningar_ ikon (![ikon för kolumninställningar](assets/column-settings.png)).
1. Om du vill anpassa vilka kolumner som ska visas i rapporten markerar eller avmarkerar du kolumnerna i listan.

   Statusrapporten för orderbetalning visar omedelbart de ändringar du har gjort på menyn Kolumninställningar. Kolumninställningarna sparas och gäller även om du navigerar bort från rapportvyn.

### Visa statusvärden

I rapportvyn Orderbetalningsstatus visas omfattande transaktionsstatus och lönestatusinformation för varje betalningsstatusorder.

#### Transaktionsstatus

Som standard visas 30 dagars betalningsstatus i rutnätet.

Bläddra åt vänster och höger för att visa [statusinformation för orderbetalning](#column-descriptions), inklusive orderdatum, auktoriserat datum, fakturerad, levererad, lönestatus med mera.

Antalet rader som returneras i en sökning, eller som visas i standardinställningstiden på 30 dagar för orderbetalningsstatus, visas ovanför vystödrastret för orderbetalningsstatus bredvid väljarfiltret för orderdatumkalender.

#### Lönestatus

Kolumnen Betala visar aktuell status för alla betalningar. A `Capture failed` betalningen visar en röd aviseringsstatus och en `Voided` Betalningen visar en grå aviseringsstatus.

#### Återbetalningsstatus

I kolumnen Återbetalningsstatus visas aktuell status för alla återbetalningar. A `Capture failed` betalningen visar en röd aviseringsstatus och en `Voided` Betalningen visar en grå aviseringsstatus.

### Uppdatera rapportdata

I rapportvyn över orderbetalningsstatus visas en _[!UICONTROL Last updated]_tidsstämpel som visar senaste gången rapportinformationen uppdaterades. Som standard uppdateras rapportdata för orderbetalningsstatus automatiskt var tredje timme.

Du kan också manuellt framtvinga en uppdatering av rapportdata för orderbetalningsstatus för att se den senaste rapportinformationen.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Klicka på _Uppdatera_ ikon (![uppdateringsikon](assets/refresh-button-med.png)).

   Rapportdata för orderbetalningsstatus uppdateras, och *[!UICONTROL Update complete]* visas och den senaste informationen finns i rutnätet.

### Visa tvister

Du kan visa eventuella tvister om dina beställningar och navigera till PayPal Resolution Center och vidta åtgärder för dem i rapporten om status för beställningsbetalning.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Navigera till **[!UICONTROL Disputes column]**.
1. Visa eventuella tvister om en viss order och se [tvistens status](#order-payment-status-information).
1. Klicka på länken Tvist-ID (börjar med _PP-D-_) för att gå till [PayPal Resolution Center](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. Vidta lämpliga åtgärder för tvisten efter behov.

   Om du vill sortera tvister efter status klickar du på kolumnrubriken Tvister.

### Hämta betalningsstatus för order

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

#### Statusinformation

Rapporter om orderbetalningsstatus innehåller följande information.

| Kolumn | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Handelsordernr<br> <br>För att se relaterade [orderinformation](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}klickar du på ID:t. |
| [!UICONTROL Order Date] | Tidsstämpel för orderdatum |
| [!UICONTROL Authorized Date] | Datum och tidsstämpel för betalningsauktorisering |
| [!UICONTROL Order Status] | Aktuell handel [orderstatus](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
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
| [!UICONTROL Disputes] | Status för en tvist om ett beslut (information från tvister och återbetalningar)—*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]*, eller *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Betalningsmetod som används i handelstransaktionen för en order |
| [!UICONTROL Website] | Webbplats där beställningen gjordes |
| [!UICONTROL Store] | Butiker som ordern placerades från |
| [!UICONTROL Store View] | Butiksvy som ordern placerades från |
