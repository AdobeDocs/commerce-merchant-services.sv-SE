---
title: Bearbetning på nivå 2 och nivå 3
description: Bearbetningsnivåer för kortbetalningar inom [!DNL Payment Services] transaktioner.
role: Admin
feature: Payments
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Bearbetning på nivå 2 och nivå 3

Det finns tre nivåer av kortbearbetning tillgängliga via [!DNL Payment Services]:

* Nivå 1 är den vanligaste, kräver mindre information och medför därför i allmänhet högre förmedlingsavgifter jämfört med transaktioner som behandlas med data på Nivå 2 eller Nivå 3, som vanligtvis är kopplade till kreditkort för företag och inköp.

* Med nivå 2 och nivå 3 [!DNL Payment Services] kunder med utbytesavtal plus (IC++)-priser som tar emot många köp- eller kreditkortstransaktioner kan få en lägre handläggningstid genom att [!DNL Payment Services] om du vill skicka mer information om en transaktion. Om transaktionen uppfyller kraven kan handlaren få en lägre handläggningsfrekvens för en viss transaktion enligt kraven för kortnätverk.

>[!NOTE]
>
>Prisnivå 2 och nivå 3 gäller endast för Visa- och MasterCard-transaktioner. American Express erbjuder endast nivå 2-pris. Upptäck priser på nivå 2 och 3. Se [betalningshantering](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} i PayPal Developer-dokumentationen om du vill ha mer information.

Se [Vad är IC++?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} i dokumentationen för PayPal-utvecklare om du vill ha mer information.

Bearbetningsdata på nivå 2 och nivå 3 gör det möjligt för handlare att sänka sina IC++-priser om de ger ytterligare information om köpet som minskar processorriskerna och ger fördelar:

* Stora kunder betalar mindre genom att tillhandahålla dessa bearbetningsdata.

* Kunderna är mindre benägna att hamna i bedrägliga situationer eftersom beställningarna har mer information.

Kortnäten, som Visa och Mastercard, avgör dock i slutändan om en transaktion uppfyller kraven för nivå 2 eller nivå 3:

* Data på nivå 2 innehåller ytterligare information, t.ex. orderns momsbelopp eller kundkoden eller inköpsordernumret.

* Data på nivå 3 är mer detaljerad information om försäljningen, vilket gör det lättare att kvalificera sig för ännu lägre utbytesfrekvenser jämfört med nivå 2. Data på nivå 3 innehåller information som en beskrivning av den köpta artikeln, antalet köpta enheter, måttenhet för beställda artiklar och annan specifik information.

[!DNL Payment Services] samlar in dessa data och ger detaljerad rapportering om dina betalningstransaktioner.

## Betalningstransaktioner på nivå 2 och nivå 3 i [!DNL Payment Services]

För att vara berättigad till behandling på nivå 2 eller nivå 3 måste handlarna skicka den tidigare informationen, även om det är kortnätverken som bestämmer vilken nivå en transaktion kvalificerar sig för när den behandlas.

Se [Vanliga frågor om betalningshantering](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} i dokumentationen för PayPal-utvecklare om du vill ha mer information.

Bearbetning på nivå 2 och nivå 3 är inaktiverad som standard för [!DNL Payment Services] handlare på butiksnivå.

Nivå 2- och nivå 3-bearbetning är tillgänglig om du redan använder IC++-priser. Om du vill aktivera den här funktionen kan du göra det via [CLI (Command-line Interface)](configure-cli.md).

>[!IMPORTANT]
>
>Om du har frågor kan du kontakta [!DNL Payment Services] kontoansvarig.
