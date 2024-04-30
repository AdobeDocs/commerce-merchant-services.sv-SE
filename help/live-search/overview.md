---
title: Vad är [!DNL Live Search]?
description: "[!DNL Live Search] från Adobe Commerce ger en snabb, relevant och intuitiv sökupplevelse."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 8aca09aba13e32afb191169729dfc1fbd0087262
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---

# Vad är [!DNL Live Search]?

[!DNL Live Search] är ett tillägg som ersätter standardsökfunktionerna i Adobe Commerce. The [!DNL Live Search] -tillägget installeras med Composer och ansluter [!DNL Commerce] installation i [!DNL Live Search] [service](../landing/saas.md). När det är konfigurerat ersätts standardtextfältet för sökning med [!DNL Live Search] textfält. [!DNL Live Search] Installerar också PLP-widgeten (Product Listing Page) som ger robusta filtreringsfunktioner när du bläddrar bland sökresultaten.

Med [!DNL Live Search]kan du:

- Skapa meningsfulla sökupplevelser som hjälper kunder och köpare att hitta det de vill ha med så lite ansträngning som möjligt.
- Utnyttja den AI-baserade dynamiska Faceeting-funktionen och omrankningen av sökresultaten som svar på beteenden hos besökare.
- Använd en lättviktig SaaS-baserad tjänst som ger enkla uppdateringar och ingår i licensen, vilket minskar den totala ägandekostnaden.
- Få teknisk information genom att aktivera graphQL API, headless flexibility, API sandbox environment och ultra fast SaaS.

>[!IMPORTANT]
>
>När det gäller webbplatssökningar har Adobe Commerce fler alternativ. Var noga med att läsa [Gränser och begränsningar](boundaries-limits.md) innan de implementeras, säkerställa [!DNL Live Search] passar ditt företags behov.

## Arkitektur

Adobe Commerce-sidan av arkitekturen innehåller värdtjänster för sökningen *Administratör*, synkroniserar katalogdata och kör frågetjänsten. Efter [!DNL Live Search] installeras och konfigureras, Adobe Commerce börjar dela söknings- och katalogdata med SaaS-tjänster. Nu kan administratörsanvändare konfigurera, anpassa och hantera sökningar [facets](facets.md), [synonymer](synonyms.md)och [försäljningsregler](category-merch.md).

![Dataflöde för Live Search](assets/ls-cs-data-flow.png)

## Snabbdemo

Med fokus på hastighet, relevans och användarvänlighet [!DNL Live Search] förändrar spelreglerna för både kunder och handlare. Följ med för en snabb genomgång av [!DNL Live Search] från butiken.

### Sök medan du skriver

[!DNL Live Search] svarar med föreslagna produkter och en miniatyrbild av de bästa sökresultaten i en [poppor](storefront-popover.md) som kunder skriver frågor i [Sök](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) box. The [produktinformation](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) visas när kunderna klickar på en föreslagen eller aktuell produkt. A _Visa alla_ -länken i portörens sidfot visar sökresultatsidan.

[!DNL Live Search] returnerar &quot;sökning när du skriver&quot; resultat för en fråga med två eller flera tecken. För en partiell matchning är det maximala antalet tecken per ord 20. Det går inte att konfigurera antalet tecken i frågan. Pekaren innehåller`name`, `sku`och `category_ids` fält.

![Exempelarkiv - sök medan du skriver](assets/storefront-search-as-you-type.png)

### Visa alla sökresultat

Om du vill visa en lista över alla produkter som returneras av frågan&quot;Sök när du skriver&quot; klickar du på _Visa alla_ i mapoverens sidfot.

![Exempel på storefront - prisfakturor](assets/storefront-view-all-search-results.png)

### Filtrerad sökning med fack

Vid filtrerad sökning används flera dimensioner av attributvärden, eller [facets](facets.md), som sökvillkor. Urvalet av filter definieras av handlaren och ändras beroende på vilka produkter som returneras, med de mest använda ansiktena fästa överst i listan.

Använd ansikten som URL-parametrar:`http://yourwebsite.com?color=red`och resultaten från direktsökningsfiltren baseras på dessa attributvärden.

### Synonymer

[Synonymer](synonyms.md) utöka räckvidden och skärpa fokus på frågor genom att inkludera ord som kunderna kan använda som skiljer sig från dem i katalogen. Du kan finjustera synonymordboken för att hålla kunderna engagerade och på köpvägen.

### Marknadsföringsregler

Merchandising [regler](rules.md) forma shoppingupplevelsen med&quot;if-then&quot;-satser som lägger till logik och händelser att söka efter. Du kan enkelt beskära eller begrava produkter för en kampanj, säsong eller annan tidsperiod.

### Stöd för söktermer

[!DNL Live Search] stöder Commerce [omdirigering av söktermer](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). Användarna kan t.ex. söka efter en term som &quot;Fraktsatser&quot; och direkt till sidan Leveransavgifter.

## Live Search-komponenter

- [!DNL Live Search] [poppwidget](storefront-popover.md) är den ruta som öppnas under sökfältet som innehåller sökresultaten.
- [Widgeten Produktlistsida](plp-styling.md) innehåller en sökbar produktlistsida med funktioner för ansikten och synonymer.
- [[!DNL Live Search] Administratör](workspace.md) är var regler, facets och synonymer konfigureras.

## [!DNL Live Search] arbetsyta

The [!DNL Live Search] [arbetsyta](workspace.md) är området i Admin där du konfigurerar [!DNL Live Search] funktioner som synonymer, facets och Category Merchandising.

## Händelser

[!DNL Live Search] använder [händelser](events.md) att beräkna [Intelligent marknadsföring](category-merch.md) och [prestanda](performance.md) instrumentpaneler. Händelser tillhandahålls med standardimplementeringar. Händelser för headless-butiker ska aktiveras manuellt.

## [!DNL Live Search] demo

I den här videon får du veta mer om [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

En mer ingående video om hur du använder och konfigurerar Live Search finns i [Fullständig demonstration på [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) ämne.
