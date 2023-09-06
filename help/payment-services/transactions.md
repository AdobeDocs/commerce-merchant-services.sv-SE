---
title: Transaktionsrapport
description: Använd rapporten Transaktioner för att få insyn i transaktionsauktoriseringstakt och transaktionstrender.
role: User
level: Intermediate
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 0%

---

# Transaktionsrapport

[!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] ger er omfattande rapportering så att ni kan få en tydlig bild av butikens transaktioner, order och betalningar.

![Transaktionsrapport](assets/transactions-report.png){width="700" zoomable="yes"}

Transaktionsrapporten ger insyn i transaktionsauktoriseringsnivåer och negativa trender för transaktioner så att du effektivt kan övervaka butikens status och i förväg identifiera och åtgärda eventuella transaktionsproblem.

Se enskilda transaktioner för order som lagts i butiken och deras betalningsmetoder, resultat, svarskoder för betalningar med mera.

Informationen i transaktionsrapporten är endast avsedd för försäljning. Dela inte denna information med kunder eller andra potentiella bedragare. Transaktionsinformation kan användas för att kringgå säkerhetskontroller eller placera order som resulterar i återbetalningar.

Du kan hämta Transactions-rapporten i ett CSV-filformat och använda den i befintligt redovisnings- eller orderhanteringsprogram.

>[!NOTE]
>
>Du kan inte visa ekonomiska rapporter om du inte har [Inbyggt och aktiverat Live-läge](production.md#enable-live-payments) for [!DNL Payment Services].

## Rapportvy för transaktioner

Rapportvyn Transaktioner är tillgänglig i vyn Transaktioner för Betalningstjänster. Den innehåller all tillgänglig information om transaktioner för din butik.

På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**om du vill visa en detaljerad rapportvy för transaktioner i tabellform.

![Rapportvy för transaktioner](assets/transactions-report-detail.png){width="600" zoomable="yes"}

Du kan konfigurera den här vyn, per avsnitt i det här avsnittet, så att du på bästa sätt kan presentera de data du vill se.

Se länkade Commerce Order- och leverantörstransaktions-ID:n, transaktionsbelopp, betalningsmetod per transaktion med mera i den här rapporten.

Alla betalningsmetoder har inte samma detaljerade information. Kreditkortstransaktioner ger till exempel svar-, AVS- och CCV-koder i Transactions-rapporten. PayPal Smart-knappar gör det inte.

Du kan [nedladdningstransaktioner](#download-transactions) i ett CSV-filformat som kan användas i befintliga redovisnings- eller orderhanteringsprogram.

### Välj datakälla

I rapportvyn Transaktioner kan du välja datakälla:**[!UICONTROL Live]** eller **[!UICONTROL Sandbox]**- som du vill visa rapportresultat för.

![Val av datakällor](assets/datasource.png){width="300" zoomable="yes"}

If _[!UICONTROL Live]_är den valda datakällan, du kan se rapportinformation för de butiker som använder [!DNL Payment Services] i produktionsläge. If_[!UICONTROL Sandbox]_ är den valda datakällan, kan du visa rapportinformation för sandlådeläget.

Datakällmarkeringar fungerar så här:

* Om du inte har några butiker som använder [!DNL Payment Services] i produktionsläge blir valet av datakälla som standard _[!UICONTROL Sandbox]_.
* Om du har en eller flera butiker som använder [!DNL Payment Services] i produktionsläge blir valet av datakälla som standard _[!UICONTROL Live]_.
* Vid export av rapporter respekteras alltid valet av datakälla.

Välj datakälla för [!UICONTROL Transactions] rapport:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicka **[!UICONTROL Data source]** och markera **[!UICONTROL Live]** eller **[!UICONTROL Sandbox]**.

   Rapportresultaten genereras om baserat på den valda datakällan.

### Anpassa tidsram för datum

I rapportvyn Transaktioner kan du anpassa tidsramen för de transaktioner som du vill visa genom att välja specifika datum. Som standard visas 30 dagars transaktioner i rutnätet.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicka på **[!UICONTROL Transaction dates]** kalenderväljarfilter.
1. Välj tillämpligt datumintervall.
1. Visa transaktionerna för de angivna datumen i rutnätet.

### Filtrera rapportinformation

I rapportvyn Transaktioner kan du filtrera de statusresultat du vill visa genom att välja filtervillkor.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicka på **[!UICONTROL Filter]** väljare.
1. Växla _[!UICONTROL Transaction Result]_alternativ för att visa rapportresultat för endast valda ordertransaktioner.
1. Växla _[!UICONTROL Payment Method]_alternativ för att visa rapportresultat för endast valda betalningsmetoder.
1. Ange en _Minsta orderbelopp_ eller _Maximalt orderbelopp_ om du vill visa rapportresultat inom det orderbeloppsintervallet.
1. Ange en _[!UICONTROL Order ID]_om du vill söka efter en viss transaktion.
1. Klicka **[!UICONTROL Hide filters]** för att dölja filtret.

### Visa och dölja kolumner

I rapporten Transaktioner visas alla tillgängliga informationskolumner som standard. Du kan dock anpassa vilka kolumner som visas i rapporten.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicka på **[!UICONTROL Column settings]** icon ![ikon för kolumninställningar](assets/column-settings.png){width="20" zoomable="yes"}.
1. Om du vill anpassa vilka kolumner som visas i rapporten markerar eller avmarkerar du kolumnerna i listan.

   Transaktionsrapporten visar omedelbart de ändringar du har gjort på menyn Kolumninställningar. Kolumninställningarna sparas och gäller även om du navigerar bort från rapportvyn.

### Uppdatera rapportdata

I rapportvyn Transaktioner visas en _[!UICONTROL Last updated]_tidsstämpel som visar senaste gången rapportinformationen uppdaterades. Som standard uppdateras rapportdata för transaktioner automatiskt var tredje timme.

Du kan även framtvinga en uppdatering av rapportdata manuellt för att se den senaste rapportinformationen.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klicka på _Uppdatera_ ikon (![uppdateringsikon](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Transaktionsrapportens data uppdateras, och *[!UICONTROL Update complete]* visas och den senaste informationen finns i rutnätet.

### Hämta transaktioner

Du kan hämta en CSV-fil med alla transaktioner synliga i rutnätet i transaktionsvyn, oavsett om du visar 30 dagars standardtransaktioner eller en anpassad tidsram.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Om du vill se transaktioner under en annan tidsperiod än de senaste 30 dagarna [anpassa tidsramen för datumintervallet för statusvärdena](#customize-dates-timeframe).
1. Klicka på _Ladda ned_ ![hämtningsikon](assets/icon-download.png){width="20" zoomable="yes"} -ikon.

Transaktionerna hämtas i CSV-format.

### Kolumnbeskrivningar

Transaktionsrapporter innehåller följande information.

| Kolumn | Beskrivning |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Beställnings-ID (innehåller endast värden för slutförda transaktioner och är tomt för avvisade transaktioner)<br> <br>För att se relaterade [orderinformation](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}klickar du på ID:t. |
| [!UICONTROL Provider Transaction ID] | Transaktions-ID som tillhandahålls av betalningsförmedlaren. Innehåller endast värden för genomförda transaktioner och innehåller ett bindestreck för avvisade transaktioner. |
| [!UICONTROL Transaction Date] | Tidsstämpel för transaktionsdatum |
| [!UICONTROL Payment Method] | Betalningsmetod, tillgänglig för Betalningstjänster version 1.6.0 och senare |
| [!UICONTROL Result] | Resultatet av transaktionen—*[!UICONTROL OK]* (lyckad transaktion), *[!UICONTROL Rejected by Payment Provider]* (avvisad av PayPal), *[!UICONTROL Rejected by Bank]* (avvisas av den bank som har utfärdat kortet) |
| [!UICONTROL Response Code] | Felkod som anger avvisandeorsak från betalningsleverantör eller bank. Se en lista över möjliga svarskoder och beskrivningar för [`Rejected by Bank` status](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) och [`Rejected by Payment Provider` status](https://developer.paypal.com/api/rest/reference/orders/v2/errors/). |
| [!UICONTROL AVS Code] | Adress Verification Service code; the processor response information for payment requests. Se [lista över möjliga koder och beskrivningar](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) för mer information. |
| [!UICONTROL CVV Code] | Kortverifieringsvärdekod för kredit- och debetkort, se [lista över möjliga koder och beskrivningar](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) för mer information. |
| [!UICONTROL Amount] | Orderbelopp för transaktion |
| [!UICONTROL Currency] | Valuta som används för order i transaktion |
| [!UICONTROL Type] | [Betalningsåtgärd](../payment-services/production.md#set-payment-services-as-payment-method) för transaktion—`Authorize` eller `Authorize and Capture` |

### Felsvarskoder

The _Svarskod_ -kolumnen visar en specifik felkod eller kod för att slutföra transaktionen. Några vanliga felkoder som du kan se är:

* `PAYMENT_DENIED`—Transaktionen nekades av PayPal eftersom den misstänktes vara bedrägeri.
* `INTERNAL_SERVER_ERROR`—Transaktionen nekades av PayPal och orsakade ett PayPal-serverfel. Transaktionen kan provas igen.
* `INSTRUMENT_DECLINED`- Kunden nekades av PayPal per vald betalningsmetod. Transaktionen kan provas igen med en annan betalningsmetod.
* `9500`—Transaktionen nekades av den associerade banken eftersom den misstänktes vara bedrägeri.
* `5120`—Transaktionen avvisades av den associerade banken eftersom kunden inte hade tillräckliga medel för betalningen.
* `5650`—Transaktionen nekades av den associerade banken eftersom banken kräver stark kundautentisering ([3DS](security.md#3ds)).

Detaljerade felsvarskoder för misslyckade transaktioner är tillgängliga för transaktioner som är nyare än 1 juni 2023. Delvisa rapportdata kommer att visas för transaktioner som inträffade före den 1 juni 2023.

