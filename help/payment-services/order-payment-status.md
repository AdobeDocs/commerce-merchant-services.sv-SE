---
title: Statusrapport för orderbetalning
description: Använd rapporten Orderbetalningsstatus för att få en bättre överblick över betalningsstatusen för dina order och identifiera eventuella problem.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
feature: Payments, Checkout, Orders
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '2045'
ht-degree: 0%

---

# Statusrapport för orderbetalning

[!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] ger er omfattande rapportering så att ni får en tydlig överblick av butikens [transaktioner](transactions.md), beställningar och betalningar.

Det finns två tillgängliga rapportvyer över orderbetalningsstatus som gör att du snabbt kan visa betalningsstatus för dina order:

* **[Visualisering av orderbetalningsstatus](#order-payment-status-data-visualization-view)**—Diagram som är tillgänglig på startsidan för Betalningstjänster som är en visuell representation av aggregerade betalningsstatusar per dag från rapportvyn Orderbetalningsstatus
* **[Rapportvy för orderbetalningsstatus](#order-payment-status-report-view)**—Rapport tillgänglig i orderbetalningsstatus som visar detaljerad betalning, fakturering, leverans, återbetalning och tviststatus för alla transaktioner

Med orderbetalningsstatusvyerna blir det enkelt att förstå var en viss order ligger i orderflödet. Med hjälp av de här rapporterna kan du snabbt visa beställningar, baserat på betalningsstatus och betalningsdatum, och identifiera eventuella problem.

Du kan [ladda ned betalningsstatus för order](#download-order-payment-statuses) i ett CSV-filformat som kan användas i befintliga redovisnings- eller orderhanteringsprogram.

>[!NOTE]
>
>Du kan inte visa ekonomiska rapporter om du inte har [Inbyggt och aktiverat Live-läge](production.md#enable-live-payments) for [!DNL Payment Services].

## Datavisualisering av orderbetalningsstatus

Vyn över orderbetalningsstatus är tillgänglig på startsidan för Betalningstjänster. Det är en visuell representation av de aggregerade betalningsstatusarna per dag från den detaljerade tabellen [Rapportvy för orderbetalningsstatus](#order-payment-status-report-view).

På _Administratör_ sidebar, gå till **Försäljning** > **Betalningstjänster** > _Beställningar_ för att se datavisualiseringen [betalningsstatusdiagram](#statuses-information).

![Visualisering av utbetalningsdata i administratören](assets/orderpayment-dataviz.png){width="800" zoomable="yes"}

Klicka **[!UICONTROL View Report]** för att navigera till den detaljerade tabellen [Rapportvy för orderbetalningsstatus](#order-payment-status-report-view).

### Anpassa tidsram för statusvärden

Som standard visas 30 dagars betalningsstatus.

I visualiseringsvyn för orderbetalningsstatus kan du anpassa tidsramen för de betalningsstatusar du vill visa genom att välja ett datumintervall:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Vyn för visualisering av orderbetalningsstatus visas i dialogrutan _Beställningar_ -avsnitt.
1. Klicka på **[!UICONTROL Range]** väljarfilter.
1. Välj datumintervall: 30 dagar, 15 dagar eller 7 dagar.
1. Visa statusinformation för angivna datum.

### Statusinformation

Betalningsstatusarna för ett valt datumintervall visas till vänster om visualiseringsvyn för orderbetalningsstatus. Datumen för det valda datumintervallet visas längst ned i vyn. Om det inte fanns några order på ett visst datum visas inte det datumet.

Vyn för visualisering av orderbetalningsstatus innehåller följande information.

| Data | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Mängdintervall för order i angiven tidsram; data på Y-axeln (vänster) |
| Datumintervall | Datumintervall för den angivna tidsramen; data på X-axeln (nederst) |
| Auktoriserad | Beställning auktoriserad |
| Hämtning begärd | Hämtning begärd för beställning |
| Hämtning bekräftad | Orderinspelningen är klar |
| Delvis hämtning | Ordning som delvis fångats |
| Hämtningen misslyckades | Orderhämtningen misslyckades |
| Annullerad | Annullerad order |

## Rapportvy för orderbetalningsstatus

Vyn för orderbetalningsstatus är tillgänglig i vyn Hem för Betalningstjänster. Den innehåller detaljerade statusvärden - betalning, fakturering, leverans, återbetalning, tvist med mera - för alla transaktioner.

På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**om du vill visa en detaljerad rapportvy över orderbetalningsstatus i tabellform.

![Beställa betalningstatustransaktioner i administratören](assets/orders-report-data.png){width="800" zoomable="yes"}

Du kan konfigurera den här vyn, per avsnitt i det här avsnittet, så att du på bästa sätt kan presentera de data du vill se.

Du kan [ladda ned utbetalningstransaktioner](#download-order-payment-statuses) i ett CSV-filformat som kan användas i befintliga redovisnings- eller orderhanteringsprogram.

>[!NOTE]
>
>De data som visas i den här tabellen sorteras i fallande ordning (`DESC`) som standard med `TRANS DATE`. The `TRANS DATE` är det datum och den tidpunkt då transaktionen initierades.

### Betalningsstatusuppdateringar

Vissa betalningsmetoder kräver en viss tidsperiod för att få betalningen. [!DNL Payment Services] identifierar nu väntande status för en betalningstransaktion i en order genom att:

* Synkron identifiering `pending capture` transaktioner
* Asynkron övervakning `pending capture` transaktioner

>[!NOTE]
>
>Genom att identifiera väntande status för betalningstransaktioner i en order förhindras att order skickas av misstag om betalningen ännu inte har tagits emot. Detta kan inträffa för e-check- och PayPal-transaktioner.

#### Synkron identifiering av väntande hämtningstransaktioner

Identifiera hämtningstransaktioner automatiskt i en `Pending` status och förhindra att order anger `Processing` status när en sådan transaktion upptäcks.

Vid kundutcheckning eller när en administratör skapar en faktura för en tidigare auktoriserad betalning, [!DNL Payment Services] identifierar automatiskt infångningstransaktioner i en `Pending` status och flyttar motsvarande order till `Payment Review` status.

#### Asynkron övervakning av väntande hämtningstransaktioner

Identifiera när en väntande hämtningstransaktion anger en `Completed` status så att säljarna kan återuppta bearbetningen av den berörda ordern.

För att processen ska fungera som förväntat måste säljarna konfigurera ett nytt cron-jobb. När jobbet har konfigurerats att köras automatiskt förväntas inga andra åtgärder från handlaren.

Se [Konfigurera cron-jobb](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html). När det är konfigurerat körs det nya jobbet var 30:e minut för att hämta uppdateringar för order som finns i en `Payment Review` status.

Handlare kan kontrollera den uppdaterade betalningsstatusen via rapportvyn för orderbetalningsstatus.

### Data som används i rapporten

[!DNL Payment Services] använder orderdata och kombinerar dem med aggregerade betalningsdata från andra källor (inklusive PayPal) för att tillhandahålla meningsfulla och mycket användbara rapporter.

Orderdata exporteras och sparas i betaltjänsten. När du [ändra eller lägga till orderstatus](https://docs.magento.com/user-guide/sales/order-status-custom.html) eller [redigera en butiksvy](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html), [store](https://docs.magento.com/user-guide/stores/store-information.html), eller webbplatsnamn, kombineras med betalningsdata och rapporten Orderbetalningsstatus fylls i med den kombinerade informationen.

Det finns två steg:

1. Indexet ändras antingen `ON SAVE` (varje gång orderinformation eller butiksinfo ändras) eller `BY SCHEDULE` (enligt ett förkonfigurerat cron-schema), beroende på hur det är konfigurerat i [Indexhantering](https://docs.magento.com/user-guide/system/index-management.html) i Admin.

   Som standard sker dataindexering `ON SAVE`, vilket innebär att när något ändras i ordningen, orderstatus, butiksvyn, butiken eller webbplatsen sker omindexeringsprocessen omedelbart.

1. Indexerade data skickas till betalningstjänsten som sedan fylls i i rapporten över orderbetalningsstatus.

De enda data som exporteras och sorteras för rapportändamål är data som används av rapporten om orderbetalningsstatus.

>[!NOTE]
>
>De data som visas i den här tabellen sorteras i fallande ordning (`DESC`) som standard med `ORDER DATE`. The `ORDER DATE` är datum- och tidsstämpeln när ordern skapades.

#### Konfigurera dataexport

Även om omindexering som standard sker i `ON SAVE` bör du indexera i `BY SCHEDULE` läge. The `BY SCHEDULE` index körs med ett cron-schema på en minut och alla ändrade data visas i orderstatusrapporten inom två minuter efter dataändringen. Denna schemalagda omindexering hjälper dig att minska eventuella påfrestningar i din butik, särskilt om du har ett stort antal inkommande order, eftersom den inträffar enligt ett schema (inte efter varje beställning).

Du kan ändra indexläge—`ON SAVE` eller `BY SCHEDULE`—[i Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).

Mer information om hur du konfigurerar dataexporten finns i [Kommandoradskonfiguration](configure-cli.md#configure-data-export).

### Välj datakälla

I rapportvyn Orderbetalningsstatus kan du välja datakälla:**[!UICONTROL Live]** _ eller **[!UICONTROL Sandbox]**- som du vill visa rapportresultat för.

![Val av datakällor](assets/datasource.png){width="300" zoomable="yes"}

If _[!UICONTROL Live]_är den valda datakällan, du kan se rapportinformation för de butiker som använder [!DNL Payment Services] i produktionsläge. If_[!UICONTROL Sandbox]_ är den valda datakällan, kan du visa rapportinformation för sandlådeläge.

Datakällmarkeringar fungerar så här:

* Om du inte har några butiker som använder [!DNL Payment Services] i Live-läget är datakällans val som standard _[!UICONTROL Sandbox]_.
* Om du har en eller flera butiker som använder [!DNL Payment Services] i Live-läget är datakällans val som standard _[!UICONTROL Live]_.
* Vid export av rapporter respekteras alltid valet av datakälla.

Välj datakälla för [!UICONTROL Order Payment Status] rapport:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. Klicka på _[!UICONTROL Data source]_väljarfilter och markera **[!UICONTROL Live]**eller **[!UICONTROL Sandbox]**.

   Rapportresultaten genereras om baserat på den valda datakällan.

### Anpassa tidsram för orderdatum

I rapportvyn Orderbetalningsstatus kan du anpassa tidsramen för statusresultaten genom att välja specifika datum. Som standard visas 30 dagars betalningsstatus i rutnätet.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicka på _[!UICONTROL Order dates]_kalenderväljarfilter.
1. Välj tillämpligt datumintervall.
1. Visa orderbetalningsstatus för angivna datum i rutnätet.

### Filtrera rapportinformation

I rapportvyn Orderbetalningsstatus kan du filtrera statusresultaten som du vill visa genom att välja filtervillkor.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicka på **[!UICONTROL Filter]** väljare.
1. Växla _Lönestatus_ alternativ för att visa rapportresultat för endast valda orderbetalningsstatusar.
1. Visa rapportresultat inom ett orderbeloppsintervall genom att ange en _[!UICONTROL Min Order Amount]_eller _[!UICONTROL Max Order Amount_].
1. Klicka **[!UICONTROL Hide filters]** för att dölja filtret.

### Visa och dölja kolumner

I rapporten Orderbetalningsstatus visas alla tillgängliga informationskolumner som standard. Du kan dock anpassa vilka kolumner som visas i rapporten.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicka på _Kolumninställningar_ ikon (![ikon för kolumninställningar](assets/column-settings.png){width="20" zoomable="yes"}).
1. Om du vill anpassa vilka kolumner som ska visas i rapporten markerar eller avmarkerar du kolumnerna i listan.

   Statusrapporten för orderbetalning visar omedelbart ändringar som du har gjort på menyn Kolumninställningar. Kolumninställningarna sparas och gäller även om du navigerar bort från rapportvyn.

### Visa statusvärden

I rapportvyn Orderbetalningsstatus visas omfattande lönestatusinformation för varje order.

Som standard visas 30 dagars betalningsstatus i rutnätet.

Bläddra åt vänster och höger för att visa [statusinformation för orderbetalning](#column-descriptions), inklusive orderdatum, auktoriserat datum, fakturerad, levererad, lönestatus med mera.

Antalet rader som returneras i en sökning, eller som visas i standardinställningstiden på 30 dagar för orderbetalningsstatus, visas ovanför vystödrastret för orderbetalningsstatus bredvid väljarfiltret för orderdatumkalender.

#### Lönestatus

Kolumnen Betala visar aktuell status för alla betalningar. A `Capture failed` betalningen visar en röd aviseringsstatus och en `Voided` Betalningen visar en grå aviseringsstatus.

#### Återbetalningsstatus

I kolumnen Återbetalningsstatus visas aktuell status för alla återbetalningar. A `Capture failed` betalningen visar en röd aviseringsstatus och en `Voided` Betalningen visar en grå aviseringsstatus.

### Uppdatera rapportdata

I rapportvyn över orderbetalningsstatus visas en _[!UICONTROL Last updated]_tidsstämpel som visar senaste gången rapportinformationen uppdaterades. Som standard uppdateras rapportdata för beställningsbetalningsstatus automatiskt var tredje timme.

Du kan också manuellt framtvinga en uppdatering av rapportdata för orderbetalningsstatus för att se den senaste rapportinformationen.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klicka på _Uppdatera_ ikon (![uppdateringsikon](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Rapportdata för orderbetalningsstatus uppdateras, och *[!UICONTROL Update complete]* visas och den senaste informationen finns i rutnätet.

### Visa tvister

Du kan visa eventuella tvister om dina beställningar och navigera till PayPal Resolution Center och vidta åtgärder för dem i rapporten om status för beställningsbetalning.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Navigera till **[!UICONTROL Disputes column]**.
1. Visa eventuella tvister om en viss order och se [tvistens status](#order-payment-status-information).
1. Granska tvistinformation från [PayPal Resolution Center](https://www.paypal.com/us/cshelp/article/what-is-the-resolution-center-help246) genom att klicka på länken för tvist-ID som börjar med _PP-D-_.
1. Vidta lämpliga åtgärder för tvisten efter behov.

   Sortera tvister efter status genom att klicka på [!UICONTROL Disputes] kolumnrubrik.

### Hämta betalningsstatus för order

Du kan hämta en CSV-fil med alla statusvärden synliga i vystödrastret för orderbetalningsstatus, oavsett om du visar standardstatusvärdena för 30 dagar eller en anpassad tidsram.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Om du vill se statusvärden under en annan tidsram än de senaste 30 dagarna [anpassa tidsramen för datumintervallet för statusvärdena](#customize-dates-timeframe).
1. Klicka på _Ladda ned_ (![hämtningsikon](assets/icon-download.png){width="20" zoomable="yes"}).

Din orderbetalningsstatus hämtas i .csv-format.

### Kolumnbeskrivningar

Rapporter om orderbetalningsstatus innehåller följande information.

| Kolumn | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Handelsordernr<br> <br>För att se relaterade [orderinformation](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}klickar du på ID:t. |
| [!UICONTROL Order Date] | Tidsstämpel för orderdatum |
| [!UICONTROL Authorized Date] | Tidsstämpel för betalningsauktorisering |
| [!UICONTROL Order Status] | Aktuell handel [orderstatus](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
| [!UICONTROL Invoiced] | Fakturastatus för ordern—*[!UICONTROL No]*, *[!UICONTROL Partial]*, eller *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Beställningsstatus—*[!UICONTROL No]*, *[!UICONTROL Partial]*, eller *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Orderns totalbelopp |
| [!UICONTROL Cur] | Valutatyp för order |
| [!UICONTROL Pay Status] | Status för betalning för en viss order |
| [!UICONTROL Paid Amt] | Belopp som betalats på en order |
| [!UICONTROL Cur] | Valutatyp för beloppet som betalats på en order |
| [!UICONTROL Refund Status] | Status för en återbetalning på en order (t.ex. information från returer, RMA och kreditnotor)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]*, eller *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Totalt återbetalt belopp för en order |
| [!UICONTROL Cur] | Valutatyp för beloppet som återbetalas för en order |
| [!UICONTROL Disputes] | Status för en tvist om ett beslut (information från tvister och återbetalningar)—*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]*, eller *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Betalningsmetod som används i handelstransaktionen för en order |
| [!UICONTROL Website] | Webbplats som beställningen placerades från |
| [!UICONTROL Store] | Butiker som beställningen placerades från |
| [!UICONTROL Store View] | Butiksvy som ordern placerades från |
