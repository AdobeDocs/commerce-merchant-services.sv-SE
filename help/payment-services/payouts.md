---
title: Utbetalningsrapport
description: Använd rapporten Betalningar för fullständig transparens av betalningsbelopp, bearbetad volym och detaljerad rapportering om transaktionsnivån för finansiell avstämning.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 0bd6137ec7cd5da04ae6a48f06cd5aec254b46ef
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Utbetalningsrapport

[!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] ger er omfattande rapportering så att ni kan få en tydlig bild av butikens order och betalningar.

![Vyn Finansiella rapporter](assets/reports-view-new.png)

Det finns två tillgängliga rapportvyer för utbetalningarna som gör att du kan se detaljerad information om alla dina utbetalningar:

* **[Vy över visualisering av betaldata](#payouts-data-visualization-view)**—Diagram som är tillgänglig på startsidan för Betalningstjänster som är en visuell representation av aggregerade belopp per dag från rapportvyn Utbetalningar
* **[Rapportvy för utbetalningar](#payouts-report-view)**—Rapport tillgänglig i Utbetalningar som visar detaljerad betalningsinformation för alla transaktioner

Utbetalningsvyerna visar omfattande utbetalningsinformation i korthet, vilket ger er full insyn i betalningsbelopp, bearbetad volym och detaljerad rapportering om transaktionsnivån för finansiell avstämning.

>[!NOTE]
>
>Betalningsrapporter visar endast order som har hämtats (betalningsåtgärden är inställd på [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method)) - eller [markerad som `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## Vy över visualisering av betaldata

Vyn för visualisering av utbetalningsdata är tillgänglig på startsidan för betalningstjänsterna. Det är en visuell representation av aggregerade belopp per dag från den detaljerade tabellen [Rapportvy för utbetalningar](#payouts-report-view).

På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** för att se datavisualiseringstabellen över krediter jämfört med debet och rörliga genomsnitt över tid.

![Visualisering av utbetalningsdata i administratören](assets/payouts-data.png)

Klicka **[!UICONTROL View Report]** för att navigera till den detaljerade tabellen [Rapportvy för utbetalningar](#payouts-report-view).

### Anpassa tidsram för transaktioner

Som standard visas 30 dagars transaktioner.

I datavisualiseringsvyn Betalningar kan du anpassa tidsramen för de utbetalningstransaktioner som du vill visa genom att välja ett datumintervall:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. Vyn för visualisering av utbetalningsdata visas i avsnittet Utbetalningar.
1. Klicka på **[!UICONTROL Range]** väljarfilter.
1. Välj datumintervall: 30 dagar, 15 dagar eller 7 dagar.
1. Visa transaktionsinformationen för de angivna datumen.

### Transaktionsinformation

Transaktionsbeloppen för ett valt datumintervall visas till vänster om visualiseringsvyn för utbetalningsdata. Datumen för det valda datumintervallet visas längst ned i vyn. Om det inte fanns några utbetalningar på ett visst datum visas inte det datumet.

Vyn för visualisering av utbetalningsdata innehåller följande information.

| Data | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Mängdintervall för transaktioner inom en angiven tidsram. data på Y-axeln (vänster) |
| Datumintervall | Datumintervall för den angivna tidsramen. data på X-axeln (nederst) |
| Kredit | Betalningar för den angivna tidsramen |
| Debet | Skulder (återbetalningar) för den angivna tidsramen |
| Glidande medelvärde | Representation av den genomsnittliga utbetalningen för varje datum i den angivna tidsramen |
| Net for range | Nettoutbetalningsbelopp för den angivna tidsramen (intervall) |

## Rapportvy för utbetalningar

Utbetalningsrapportvyn är tillgänglig i vyn Utbetalningar i Betalningstjänster. Den innehåller all tillgänglig information om utbetalningar för din butik/dina butiker. The [Vy över visualisering av betaldata](#payouts-data-visualization-view) i Betalningstjänster Home är en visuell representation av aggregerade belopp per dag i den här mer detaljerade rapportvyn.

På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]** om du vill visa en detaljerad rapportvy i tabellformat.

![Utbetalningstransaktioner i administratören](assets/payouts-report-new.png)

Du kan konfigurera den här vyn, per avsnitt i det här avsnittet, så att du på bästa sätt kan presentera de data du vill se.

Se länkade handelsorder- och transaktions-ID:n, transaktionsbelopp, betalningsmetod per transaktion med mera i utbetalningsrapporten i Admin.

Du kan hämta utbetalningstransaktioner i ett CSV-filformat och använda dem i befintliga redovisnings- eller orderhanteringsprogram.

>[!NOTE]
>
>De data som visas i den här tabellen sorteras i fallande ordning (`DESC`) som standard med `TRANS DATE`. The `TRANS DATE` är det datum och den tidpunkt då transaktionen initierades.

### Välj datakälla

I rapportvyn Betalningar kan du välja datakälla:_[!UICONTROL Live]_eller_[!UICONTROL Sandbox]_- som du vill visa rapportresultat för.

![Val av datakällor](assets/datasource.png)

If _[!UICONTROL Live]_är den valda datakällan, kan du se rapportinformation för dina livebutiker. If [!UICONTROL Sandbox]_ är den valda datakällan, du kan se rapportinformation för din sandlådemiljö.

Datakällmarkeringar fungerar så här:

* Om du inte har några arkiv som är i Live-läge används som standard datakällans val _[!UICONTROL Sandbox]_.
* Om du har arkiv (en eller flera) i Live-läge används som standard valet av datakälla _[!UICONTROL Live]_.
* Vid export av rapporter respekteras alltid valet av datakälla.

Så här väljer du datakälla för rapporten för orderbetalningsstatus:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Klicka **[!UICONTROL Data source]** och markera _[!UICONTROL Live]_eller_[!UICONTROL Sandbox]_.

   Rapportresultaten genereras om baserat på den valda datakällan.

### Visa transaktioner

Som standard visas 30 dagars transaktioner.

Antalet rader som returneras i en sökning, eller som visas i standardvärdet för 30 dagar med transaktioner, visas ovanför stödrastret i betalningsvyn bredvid kalenderväljarfiltret för transaktionsdatum.

Bläddra åt vänster och höger för att visa [information för varje betalningstransaktion](#column-descriptions) i den dagliga rapporten, inklusive transaktionsdatum, referens-ID, fakturanummer och betalningsmetoddetaljer.

#### Anpassa tidsram för transaktioner

I rapportvyn Betalningar kan du anpassa tidsramen för de utbetalningstransaktioner som du vill visa genom att ange specifika datum eller välja ett datumintervall från datumväljaren:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Klicka på kalenderväljarfiltret för transaktionsdatum.
1. Välj tillämpligt datumintervall.
1. Visa utbetalningsstatus i rutnätet för de angivna datumen.

### Visa och dölja kolumner

I rapportvyn Utbetalningar visas de mest tillgängliga informationskolumnerna som standard. Du kan dock anpassa vilka kolumner som visas i rapporten.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. Klicka på _Kolumninställningar_ ikon (![ikon för kolumninställningar](assets/column-settings.png)).
1. Om du vill anpassa vilka kolumner som ska visas i rapporten markerar eller avmarkerar du kolumnerna i listan.

   Utbetalningsrapportvyn visar omedelbart de ändringar du har gjort på menyn Kolumninställningar. Kolumninställningarna sparas och gäller även om du navigerar bort från rapportvyn.

### Hämta transaktioner

Du kan ladda ned en CSV-fil som innehåller alla transaktioner som visas i stödrastret i utbetalningsvyn.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Anpassa tidsramen för datumintervall för dina transaktioner](#customize-transactions-timeframe).
1. Klicka på _Hämta_ (![](assets/icon-download.png)).

Betalningstransaktionerna hämtas i .csv-format.

### Kolumnbeskrivningar

Utbetalningsrapporter innehåller följande information.

| Kolumn | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Betalningsleverantör |
| [!UICONTROL Provider trans] | Transaktions-ID |
| [!UICONTROL Trans date] | Datum och tid då transaktionen initierades |
| [!UICONTROL Type] | Transaktionstyp—*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Se [Transaktionstyper](#transaction-types) för mer information. |
| [!UICONTROL Status] | Aktuell status för transaktionen—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Transaktionskod som anger antingen kredit (*CR*) eller Debet (*DR*) |
| [!UICONTROL Reference ID] | Ursprungligt transaktions-ID som den här händelsen är relaterad till |
| [!UICONTROL Invoice] | Faktura-ID (en per order) för transaktionen |
| [!UICONTROL Commerce order] | Handelsordernr <br> <br>För att se relaterade [orderinformation](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, klicka på ID:t. |
| [!UICONTROL Commerce trans] | ID för handelstransaktion <br> <br>För att se relaterade [transaktionsinformation](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}, klicka på ID:t. |
| [!UICONTROL Pay method] | Kreditkortstyp—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL APPLE_PAY]*, *[!UICONTROL CREDIT_CARD]*—och tillhörande kortleverantör (t.ex. *Visa* eller *MasterCard*) |
| [!UICONTROL Trans amt] | Transaktionens belopp |
| [!UICONTROL Cur] | Valutaenhet för transaktionsbelopp |
| [!UICONTROL Pending] | Belopp som ännu inte ska betalas ut |
| [!UICONTROL Cur] | Valutaenhet för det väntande beloppet |
| [!UICONTROL Seller amt] | Belopp som överförts till eller från en kund <br> <br>Medel som flyttas ut från säljarkontot visar ett bindestreck (-). |
| [!UICONTROL Cur] | Valutaenhet för säljarbeloppet |
| [!UICONTROL Partner fee] | Partneravgifter som är kopplade till transaktionen <br> <br>Medel som flyttas från partneravgiftskontot visar ett bindestreck (-). |
| [!UICONTROL Cur] | Valutaenhet för partneravgiften |
| [!UICONTROL Prov fees] | Avgifter som är kopplade till transaktionen <br> <br>Medel som flyttas från leverantörens avgiftskonto visar ett bindestreck (-). |
| [!UICONTROL Cur] | Valutaenhet för provideravgift |
| [!UICONTROL Fee %] | Procent av transaktionsbeloppet som debiterats som en avgift |
| [!UICONTROL Fixed fee] | Fast provideravgiftsbelopp |
| [!UICONTROL Chbk fee] | Återbetalningsavgift som är kopplad till transaktionen <br> <br>Ett bindestreck (-) anger att återföringsavgiften återförts. |
| [!UICONTROL Cur] | Valutaenhet för återbetalningsavgiften |
| [!UICONTROL Hold amt] | Belopp som spärrats eller frisläppts från spärr <br> <br>Ett bindestreck (-) anger att spärrade medel frisläpps. |
| [!UICONTROL Cur] | Valutaenhet för spärrbeloppet |
| [!UICONTROL Recoup amt] | Belopp som har tagits emot från återköpskontot <br> <br>Medel som flyttas ut från ett postkonto visar ett bindestreck (-). |
| [!UICONTROL Cur] | Valutaenhet för återköpsbelopp |

### Transaktionstyper

Dessa transaktionstyper kan noteras i utbetalningstransaktionerna.

| Rapport | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Pengar som flyttats mellan en köpare och en säljare för en beställning |
| [!UICONTROL AUTH] | Giltiga transaktioner för auktorisering och auktorisering |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Återföringstransaktioner för återföringsavgift och återföringskostnader för återföringskostnader |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | Partneravgifter, betalningsavgifter och avgiftsåterföringstransaktioner |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | Kuponger från bank- eller förlustkonton |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
