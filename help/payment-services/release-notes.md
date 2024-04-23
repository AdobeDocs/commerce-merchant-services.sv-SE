---
title: "[!DNL Payment Services] Versionsinformation"
description: Läs versionsinformationen om du vill ha information om alla [!DNL Payment Services] releaser.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 8e123367600c40d1d1207b35c4f7fa41079e7172
workflow-type: tm+mt
source-wordcount: '2505'
ht-degree: 0%

---

# Versionsinformation

I versionsinformationen beskrivs den första versionen av [!DNL Payment Services] och innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigerat problem](../assets/fix.svg) Korrigeringar och förbättringar
![Känt fel](../assets/bug.svg) Kända fel

Om du vill se funktionsändringar och korrigeringar som släppts utanför den vanliga versionen av funktionen läser du _Uppdateringar av värdtjänster_ -avsnitt.

Läs mer om kommande releaser, produktsupport och vilka Adobe Commerce-versioner som stöder tillägget Betalningstjänster i Adobe Commerce [Frigör schema](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) och [Produkttillgänglighet](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) ämnen.

## Uppdateringar av värdtjänster

I versionsinformationen beskrivs funktionsändringar och korrigeringar som har gjorts och släppts utanför de vanliga funktionsreleaserna för värdtjänsten.

+++Värdbaserade tjänstuppdateringar

_5 mars 2024_

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-5252 --> Nu kan handlare kopiera data från Dashboard-rutnätet genom att markera innehållet i en enskild cell.

_10 oktober 2023_

![Nytt problem](../assets/fix.svg)<!-- Issue PAY-4888 --> Nu kan handlarna filtrera transaktionerna med kreditkort och betalkort med de fyra sista siffrorna i kortnumret i [Transaktionsrapport](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_12 juli 2023_

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-4587 --> Ett problem som introducerades i utgåvan av Payment Services 2.1.0 och som förhindrade auktoriseringsannulleringar som placerats i tidigare tilläggsversioner har nu åtgärdats. Handlare som använder någon version av Payment Services kan annullera auktoriseringar.

_9 juni 2023_

![Nytt](../assets/new.svg)<!-- Issue PAY-4288 --> Nu kan handlarna [konfigurera _endast_ Betalningsknappar för PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)—och _not_ använda betalningsalternativet PayPal-kreditkort. På så sätt kan handlarna tillhandahålla olika betalningsalternativ, inklusive betalningsknapparna Venmo och PayPal, och använda en befintlig kreditkortsleverantör i stället för betalningsalternativet för PayPal-kreditkort.

![Nytt](../assets/new.svg)<!-- Issue PAY-4050 --> Lagt till en [datavisualisering](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), som visas på startsidan för betalningstjänsten, för statusrapporten för orderbetalning.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-4486--> Tidigare visades inte PayPal PayLater-knappen i utcheckningen för handlare i Storbritannien. Problemet är löst.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-4485--> Vyer för rapportdatavisualisering visas nu på startsidan för Betalningstjänster när Betalningstjänster är inaktiverat.

_25 januari 2023_

![Känt fel](../assets/bug.svg)<!-- Issue PAY-4102 --> Nya installationer av betaltjänster kan inte konfigurera Commerce Services, vilket gör att betalningstjänsterna inte kan användas. Du kan åtgärda problemet genom att uppdatera ditt betaltjänsttillägg till version 1.5.3.

_12 september 2022_

![Nytt](../assets/new.svg)<!-- Issue PAY-3705 --> The `increment_id` är nu tillgängligt för användning vid avstämning av utbetalningar i externa ERP-system. Den sprids till [`custom_id` _och_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), som är synlig både på PayPal-webkroken och i butiksaktivitetsinformationen för en utbetalning.

_31 augusti 2022_

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3629 --> När en ny handlare öppnar startsidan för Betalningstjänster för första gången läses sidan nu in omedelbart för att visa innehållet i stället för att en uppdatering av sidan krävs.

_9 augusti 2021_

![Nytt](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay finns nu som smart PayPal-knapp. Detta [betalningsalternativ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) gör det möjligt för kunder att använda Touch ID-funktionen på sin iOS- eller macOS-enhet för att välja Apple Pay. Apple Pay behandlar betalningen med hjälp av de betalnings- och betalkortsuppgifter som lagras på enheten.

_28 juni 2021_

![Nytt](../assets/new.svg)<!-- Issue PAY-1720 --> Tvister för butiksorder finns nu i [statusrapport för orderbetalning](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Du kan lösa tvister genom att navigera direkt till PayPal Resolution Center från [!DNL Payment Services].

![Nytt](../assets/new.svg)<!-- Issue PAY-2854 --> Förbättringar av användarupplevelsen från [!DNL Payment Services] På startsidan kan du ändra en konfiguration på den aktuella arvsnivån och förbättra visningen av rubriken och navigeringen.

![Nytt](../assets/new.svg)<!-- Issue PAY-2854 --> Du kan nu se varningar när du växlar från sandlådeläge till produktionsläge och när du försöker navigera bort från en vy med uppdateringar som inte har sparats.

![Nytt](../assets/new.svg)<!-- Issue PAY-2761 --> Nu kan du anpassa de data som visas i [Statusrapport för orderbetalning](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) och [Utbetalningsrapport](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) genom att visa eller dölja kolumner med hjälp av kontrollen för kolumninställningar.

+++

## v2.5.0

_23 april 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg)<!-- Issue PAY-5396 --> Betalningstjänster stöder nu [Adobe Commerce riktlinjer för `--db-prefix` parameter](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) för Adobe Commerce version 2.4.7 och senare.

## v2.4.3

_16 april 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg)<!-- Issue PAY-5106 --> Korrigerade ett problem som felaktigt fyllde i ordersummorna vid utcheckning mellan PayPal och Adobe Commerce. Nu kan Merchants se till att ordersummorna är korrekta när man gör en beställning.

## v2.4.2

_11 april 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue xxx --> Stöd för Adobe Commerce 2.4.7 har lagts till.

## v2.4.1

_4 april 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg)<!-- PAY-5322 --> Korrigerade ett PCI-kompatibilitetsproblem med nyare Adobe Commerce-versioner. Betalningstjänster är nu anpassat efter checkout-kraven i Adobe Commerce som betalningsalternativ.

![Korrigera](../assets/fix.svg)<!-- PAY-5323 --> PayLater och Venmo visas korrekt i Adobe Commerce. Korrigerade ett fel som medgav att administratören inte kunde visa alternativen PayLater och Venmo toggle.

## v2.4.0

_20 mars 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- PAY-4868 --> Handlare kan [konfigurera Google Pay genom hela köpprocessen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html), på samma sätt som andra betalningsknappar i Betalningstjänster via administratören.

![Nytt](../assets/new.svg)<!-- PAY-4381 --> [Betalningstjänster stöder Google Pay via GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) som gör det möjligt för handlare att ha en headless Commerce-upplevelse med betalningsmetoden Google Pay.

![Nytt](../assets/new.svg)<!-- PAY-4878 --> Nu medföljer funktionen för grundläggande checkout för betaltjänster för Adobe Commerce och Magento Open Source. Betalningstjänster kan nu stödja handlare med företag i alla 200 länder världen över. Grundläggande utcheckning av betaltjänster ger alternativ för debet/kredit, PayPal, Venmo (där det är tillgängligt) och PayLater (där det är tillgängligt) i en självbetjäning.

![Korrigera](../assets/fix.svg)<!-- PAY-5291 --> Betalningsbekräftelse för vissa transaktioner kan fördröjas. I så fall kan säljarna nu få en uppdaterad betalningsstatus för en order. [Betalningstjänster identifierar den väntande statusen för en betalningstransaktion](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) i en ordning genom att identifiera väntande transaktioner och proaktivt övervaka dessa transaktioner och uppdatera när den väntande statusen har hämtats.

## v2.3.4

_1 mars 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- PAY-5244 --> Korrigerad kompatibilitet för asynkron utcheckning.

![Korrigera](../assets/fix.svg)<!-- PAY-5253 --> Ett fel har korrigerats där en valvtoken som inte tillhör Betalningstjänster inte kunde tas bort.

## v2.3.3

_14 februari 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- PAY-5048 --> Stöd för PHP 8.3 har lagts till

![Korrigera](../assets/fix.svg)<!-- PAY-5048 --> Ett fel med `is_deleted` flagga. Beställningar misslyckas inte på grund av `Rejected` status skickad från tillägget.

## v2.3.2

_26 januari 2024_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg)<!-- PAY-5183 --> REST/GraphQL-prestandaproblem har åtgärdats. Nu återges kreditkortsknappen när den hämtas via API:t.

## v2.3.1

_7 december 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- PAY-5047 --> Varumärket eller betalningsmetoden för kreditkort/betalkort finns nu på följande platser:
- kundordersidan i butiken
- e-postmeddelande med orderbekräftelsen som skickas till kunden
- från [orderinformationsvy](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) i handelsadministratören.

## v2.3.0

_1 december 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- PAY-4381 --> [Betalningstjänster har nu stöd för integrering med GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). Med GraphQL stöd för betalningsknappar, värdbaserade fält och Apple Pay har Betalningstjänster nu stöd för en headless Commerce-konfiguration.

## v2.2.1

_27 september 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-4870 --> Korrigerade ett problem som felaktigt fyllde i det nya rubrikattributet korrekt i Storefront när tilläggsversionen skickades med den senaste versionen. Tidigare med `1.3.0` lanseringen av Commerce Services-kopplingen, du kunde inte utöka `User-Agent header` från tillägget Betalningstjänster.

## v2.2.0

_30 augusti 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- PAY-4638 --> Tillagda [integration med Signifyd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html), som tillhandahåller automatiserade tjänster för bedrägeriskydd.

![Nytt](../assets/new.svg)<!-- PAY-3981 --> [Befordrad Apple Betala till ett separat betalningsalternativ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button)utanför betalningsknapparna för PayPal, för att öka kundens synlighet för betalningsalternativet och för att möjliggöra för handlarna att styra placeringen och formateringen av Apple Pay.

![Nytt](../assets/new.svg)<!-- PAY-4002 --> Förbättrad användarupplevelse vid utcheckning av kreditkortsfält, inklusive formateringsförbättringar som att lägga till betalningsikoner, för att minska kundens kognitiva belastning och öka konverteringsgraden.

![Nytt](../assets/new.svg)<!-- PAY-4002 --> Tillagda funktioner som tillåter handlare att [sortera ordningen på betalningsalternativen](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) för att prioritera vissa betalningsalternativ. Den här funktionen uppmuntrar till högre utcheckningsfrekvens för konversationer.

![Nytt](../assets/new.svg)<!-- PAY-4035 --> Handlarna kan nu effektivt övervaka butikernas hälsa och identifiera eventuella transaktionsproblem med hjälp av nya [Transaktionsrapport](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) finns på startsidan för Admin för betaltjänster. Rapporten innehåller även uppgifter om auktoriseringstariffer för transaktioner och negativa trender för transaktioner.

## v2.1.0

_9 juni 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue xxx --> Stöd för Adobe Commerce 2.4.7-beta1 har lagts till.

![Nytt](../assets/new.svg)<!-- Issue xxx --> Tillagd [tillgänglighet i följande länder och tillhörande valutor](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): Australien, Frankrike, Storbritannien.

![Nytt](../assets/new.svg)<!-- Issue PAY-4296 --> Tillagd [utökade resurser för administratörsroller](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) för att se till att administratörsanvändare kan skapa och hantera beställningar för kunder och kan se Betalningstjänster på menyn Försäljning.

![Nytt](../assets/new.svg)<!-- Issue PAY-4236 --> Tillagd [automatisk annullering för order som orsakar fel vid utcheckning](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![Nytt](../assets/new.svg)<!-- Issue PAY-4183 --> Skapade funktioner för [visa alternativknappen för betalning med kreditkort/betalkort](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) på utcheckningssidan.

## v2.0.0

_10 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-4152 --> Stöd för PHP 8.2 och Adobe Commerce 2.4.6 har lagts till. Inte kompatibelt med PHP 7.x.

## v1.6.1

_10 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg)<!-- Issue PAY-4226 --> Korrigerade ett problem som förhindrade nya betalningstjänster-handlare från att använda utcheckning i administratören. Betalningstjänsterna använde tidigare Commerce-kund-ID, som inte finns för nya kunder.

![Korrigera](../assets/fix.svg)<!-- Issue PAY-4205 --> Korrigerat ett problem som gjorde att den angivna leveransadressen ersattes av läget i standardskatteinställningarna vid utcheckning med [PayPal, alternativ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Nu kan kunderna få sina beställningar levererade till ett annat tillstånd än det som konfigurerats som standard i handlarens skatteinställningar.

![Korrigera](../assets/fix.svg)<!-- Issue PAY-4202 --> Korrigerat ett problem som förhindrade kunder från att använda kortvalsning för att slutföra ett köp eller ta bort en betalningsmetod som är skyddad för en butik [med `Authorize and Capture` betalningsåtgärd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Tidigare uppstod ett fel av typen &quot;Provider Vault ID not found&quot; när kunden försökte använda eller ändra sina kreditkort.

## v1.6.0

_17 februari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-3540 --> Tillagd [Funktion för överensstämmelse med PCI 3DS för handlare som handlar i EU och Storbritannien](security.md#3ds). Detta extra säkerhetsskikt, som kräver att köpare autentiserar med kreditkortsutfärdaren, bidrar till att förhindra onlinebedrägerier och krävs som en del av EU:s regler för regelefterlevnad.

![Nytt](../assets/new.svg)<!-- Issue PAY-3609 --> Lagt till möjlighet att [aktivera kortvalv i administratören](vaulting.md#use-vaulting-in-the-admin). Detta gör att handlare kan skapa en order för kunder i administratören med sina betalningsmetoder som är säkra.

## v1.5.4

_29 januari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-4110 --> Korrigerade ett problem som hindrade köpare från att göra en beställning med hjälp av betalningsknappar på produktsidan, i varukorgen och i varukorgen. Köparna kan nu slutföra beställningarna.

## v1.5.3

_25 januari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-4102 --> Lämnade en korrigering till ett bakåtkompatibelt, inkompatibelt problem. I den här versionen låses tilläggversionen av tjänst-ID till den senaste stabila versionen, vilket gör att nya installationer av Payment Services kan konfigurera Commerce Services.

## v1.5.2

_22 december 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3992 --> Förbättrad fakturering i Betalningstjänster när en betalningsmetod avvisas.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3999 --> Betalningstjänster visar nu betalningsknappar för PayPal korrekt för handlare som använder [Fire Checkout&#39;s](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} anpassad mall för utcheckningssidan. Tidigare visades knapparna i minikorgen ibland.

## v1.5.1

_23 november 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-3923 --> Betalningstjänster inkluderar nu versionsnumret i användaragenthuvudet så att begäranden kan spåra, filtrera eller ta bort oanvända slutpunkter.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3968 --> Betalningstjänster visar nu orderdata korrekt när en order läggs från produktsidan med betalningsknappar.

## v1.5.0

_18 november 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-3880 --> En kund kan nu [avvisa (spara) kreditkortsinformation vid utcheckning](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) som kan användas vid ett senare köp för samma eller en annan butik inom samma handlarkonto.

![Nytt](../assets/new.svg)<!-- Issue PAY-3950 --> Handlare kan nu aktivera [Funktion för direktköp inom handeln](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) för sina butiker så att kunderna kan (använda [bankkortsinformation](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) för att underlätta utcheckningen.

## v1.4.1

_14 oktober 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg)<!-- Issue PAY-3766 --> När en kunds betalningsmetod avvisas är det synliga felmeddelandet mer beskrivande. Kunden uppmanas att ange betalningsinformation igen och försöka igen, prova en annan betalningsmetod eller kontakta sin bank om transaktionen avvisas.

## v1.4.0

_30 september 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-784 --> Betalningstjänster inkluderar nu möjligheten att skapa ett handlarkonto för att [använda flera PayPal-affärskonton](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). På så sätt kan handlaren driva butikerna i olika länder med olika valutor eller använda Adobe Commerce för en del av verksamheten.

![Nytt](../assets/new.svg)<!-- Issue PAY-3231 --> Handlare kan [lägg till en [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) till webbplatser eller enskilda butiksvisningar som visas på kundtransaktionens bankutdrag för att identifiera varumärken, butiker eller produktrader.

![Nytt](../assets/new.svg)<!-- Issue PAY-3707 --> [Aktivera eller inaktivera kreditkortsfält och PayPal-betalningsknappar](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) för utcheckning i inställningarna för betaltjänster.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3546 --> När en kund klickar **[!UICONTROL Edit cart]**, dirigeras sidan om till kundvagnssidan och visar de uppdaterade objekten i stället för att visa en tom kundvagn.

## v1.3.1

_6 september 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3663 --> När en handlares butik nu tar emot en order som är auktoriserad med en icke-global valuta slutförs hämtningsprocessen och inget fel visas.

## v1.3.0

_9 augusti 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-XX --> Allmän tillgänglighetsrelease—[!DNL Payment Services] är nu [stöds av [!DNL Adobe Commerce] och [!DNL Magento Open Source] version 2.4.0 till 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay är nu kompatibelt med webbläsaren Safari v15.5 på mobiler och datorer.

## v1.2.0

_29 juni 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Känt fel](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay är inte kompatibelt med webbläsaren Safari v15.5 på mobiler och datorer. När du använder Safari version 15.5 kan du inte slutföra utcheckningen med Apple Pay.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3264 --> När en inloggad användare tidigare har valt en annan fakturerings-/leveransadress än standardadressen för sitt konto misslyckades utcheckningen. Nu skickas den valda fakturerings-/leveransadressen (i stället för den sparade standardadressen) och utcheckningen har slutförts.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3314 --> Om du inaktiverar betalningsknappar för PayPal för utcheckning visas inga fel.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3330 --> Betalningar misslyckas inte längre vid utcheckning när en gästanvändare anger ett telefonnummer som innehåller streck.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> När autentiseringsuppgifterna för Commerce Services är ogiltiga får du nu en varning från Betalningstjänster via [!DNL Payment Services] Hem i Admin.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] är inte kompatibelt med `commerce-data-export` v101.20 och senare, vilket gör den inkompatibel med [[!DNL Channel manager] extension](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31 mars 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-2127 --> Allmän tillgänglighetsrelease—[!DNL Payment Services] är nu [stöds av [!DNL Adobe Commerce] och [!DNL Magento Open Source] version 2.4.0 till 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Nytt](../assets/new.svg)<!-- Issue PAY-2682 --> The [!DNL Payment Services] tillägg för [!DNL Adobe Commerce] och [!DNL Magento Open Source] finns nu för kanadensiska handlare. Handlare kan visa betalningskonfigurationen i antingen [Franska](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) eller [Engelska](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Nytt](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] supports [Kanadensiska dollar (CAD)](overview.md#accepted-credit-cards-and-currencies) för kreditkort och PayPal-transaktioner.

![Nytt](../assets/new.svg)<!-- Issue PAY-2680 --> Handlare kan [inbyggt [!DNL Payment Services]](onboard.md) på engelska eller franska.

![Nytt](../assets/new.svg)<!-- Issue PAY-2678 --> Handläggarna kan nu visa ekonomiska rapporter, både [Status för orderbetalning](order-payment-status.md) och [Utbetalningsrapporter](payouts.md), i kanadensiska dollar.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] är nu kompatibelt med [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-3017 --> Förbättrad sandlådelägesvarning för att visa korrekta varningar i flera butiker.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2742 --> Du kan nu aktivera och inaktivera tillgängliga betalningsmetoder, som Venmo, på butiksvynivå. Tidigare kunde du bara konfigurera betalningsmetoder per webbplats.

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2277 --> Du kan nu välja [aktivera eller inaktivera enskilda PayPal-betalningsknappar](settings.md#payment-buttons).

![Korrigerat problem](../assets/fix.svg)<!-- Issue PAY-2561 --> Tidigare borttagna produkter visas inte i kundvagnen på _Granska beställning_ sida.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2842 --> Testa kreditkortstransaktioner [kan misslyckas med PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) när betalningar bearbetas i en sandlådemiljö.

## v1.0.0

_29 november 2021_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg)<!-- Issue PAY-2127 --> Allmän tillgänglighetsrelease—[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) stöds nu av [!DNL Adobe Commerce] och [!DNL Magento Open Source] version 2.4.0 till 2.4.3-p1.

![Nytt](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] tillägg för [!DNL Adobe Commerce] och [!DNL Magento Open Source] kan installeras antingen för [[!DNL Adobe Commerce] om molninfrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) eller [Lokalt](install.md#on-premises) -instanser. Dessa metoder kräver att ett kommandoradsgränssnitt används.

![Nytt](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] stöder [sandlådekonto](sandbox.md) som gör det möjligt för handlare att bedöma tillägget i testläge.

![Nytt](../assets/new.svg)<!-- Issue PAY-666 --> Handlare kan [konfigurera betalningstjänsterna](settings.md) tillägg med grundläggande betalningsbeteenden, som att använda [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) växla mellan sandlådor och produktionsmiljöer.

![Nytt](../assets/new.svg)<!-- Issue PAY-780 --> Dina kunder kan kolla in med [!DNL Payment Services] eller via [manuell orderhantering](create-order.md).

![Nytt](../assets/new.svg)<!-- Issue PAY-1856 --> Omfattande rapportering, via [Status för orderbetalning](order-payment-status.md) och [Utbetalningsrapporter](payouts.md), är tillgängliga för [!DNL Payment Services] för att ge dig en tydlig bild av butikens order och tillhörande betalningar.

![Nytt](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] stöder flexibla nivåbaserade priser, baserade på den totala bearbetningsvolymen, anpassade till alla handlare.

![Nytt](../assets/new.svg)<!-- Issue PAY-1443 --> Du kan enkelt [anpassa utseende och känsla](payments-options.md) av betalningsknappar och kreditkortsfält för PayPal för [!DNL Payment Services] tillägg.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2473 --> Använda [felaktiga dispositionsnycklar](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) under installationen av tillägget förhindrar användaren från att [autentisera](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) med rätt `MAGEID`.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] rapporter [kan inte synkroniseras omedelbart](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2475 --> Dina [PayPal-sandlådekonto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) for [!DNL Payment Services] kan inte verifieras om du skapar det kontot under introduktionen.
