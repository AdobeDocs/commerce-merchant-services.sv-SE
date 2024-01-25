---
title: '''[!DNL Live Search] Händelser'
description: Lär dig hur händelser samlar in data för [!DNL Live Search].
feature: Services, Eventing
source-git-commit: c14ba55bee54954ffcfe760e26dc1d69646ecd69
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# [!DNL Live Search] Händelser

[!DNL Live Search] använder händelser för att driva sökalgoritmer som&quot;Mest visade&quot; och&quot;Visat det här&quot;. Medan LUMA-användare får ut sin egen händelsehantering måste headless och andra anpassade implementeringar implementera händelsehantering för sina egna behov.

Sedan [!DNL Live Search] och [!DNL Product Recommendations] använder samma backend-algoritm. Vissa händelser delas av båda tjänsterna. Vissa Recommendations-produkthändelser krävs för att fylla i Recommendations Dashboard.

## Händelser

I den här tabellen beskrivs de händelser som används av [!DNL Live Search] strategier.

| Strategi | Produkter | Händelser | Sida |
| --- | --- | --- | ---|
| Mest visade | Live Search<br>Produktrecept | sidvy<br>produktvy | Produktinformationssida |
| Mest köpta | Live Search<br>Produktrecept | sidvy<br>fullständig utcheckning | Kassa/kassa |
| Mest tillagt i kundvagn | Live Search<br>Produktrecept | sidvy<br>lägg till i kundvagn | Produktinformationssida<br>Produktlistsida<br>Kundvagn<br>Önsklista |
| Visade det här, såg du att | Live Search<br>Produktrecept | sidvy<br>produktvy | Produktinformationssida |
| Trender | Live Search<br>Produktrecept | sidvy<br>produktvy | Produktinformationssida |
| En titt på det här, köpte det | Produktrecept | sidvy<br>produktvy | Produktinformationssida<br>Kassa/kassa |
| Köpte den här, köpte den där | Produktrecept | sidvy<br>produktvy | Produktinformationssida |
| Konvertering: Visa för köp | Produktrecept | sidvy<br>produktvy | Produktinformationssida |
| Konvertering: Visa för köp | Produktrecept | sidvy<br>fullständig utcheckning | Kassa/kassa |
| Konvertering: Visa i kundvagn | Produktrecept | sidvy<br>produktvy | Produktinformationssida |
| Konvertering: Visa i kundvagn | Produktrecept | sidvy<br>lägg till i kundvagn | Produktinformationssida<br>Produktlistsida<br>Kundvagn<br>Önsklista |

>[!NOTE]
>
>Datainsamling för [!DNL Live Search] inte innehåller personligt identifierbar information. Alla användaridentifierare, som cookie-ID:n och IP-adresser, är strikt anonymiserade. [Läs mer](https://www.adobe.com/privacy/experience-cloud.html).

## Nödvändiga instrumentpanelshändelser

Vissa händelser krävs för att fylla i [Kontrollpanel för Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/performance.html)

| Kontrollpanelsområde | Händelser |
| ----- | ---- | 
| Unika sökningar | `search-request-sent`,`search-response-received` |
| Inga resultatsökningar | `search-request-sent`,`search-response-received` |
| Nollresultatfrekvens | `search-request-sent`,`search-response-received` |
| Vanliga sökningar | `search-request-sent`,`search-response-received` |
| Medel. klickningsposition | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click` |
| Genomklickningsfrekvens | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click` |
| Konverteringsgrad | `search-request-sent`,`search-response-received`, `search-results-view`, `search-product-click`,`product-view`,`add-to-cart`,`place-order` |

### Nödvändiga sammanhang

Alla händelser kräver `Page` och `Storefront` kontexter. Detta bör ske på sidnivå/butiksprogramlager i stället för när enskilda händelser genereras (i en PHP-butik ansvarar PHP-programbehållaren för att ställa in dem vid körning).

## Användning

Här följer ett exempel på implementering av `search-request-sent` händelse:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Caveats

Annonsblockerare och sekretessinställningar kan förhindra att händelser fångas in och kan leda till engagemang och intäkter [mått](workspace.md) vara underrapporterade.

Händelser fångar inte upp alla transaktioner som sker på handlarens webbplats. Händelser är avsedda att ge handlaren en allmän uppfattning om händelser som inträffar på webbplatsen.

Headless-implementationer måste implementera händelser för att ge [Recommendations Dashboard](../product-recommendations/events.md).

>[!NOTE]
>
>If [Begränsningsläge för cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) är aktiverat samlar Adobe Commerce inte in beteendedata förrän kunden samtycker till att använda cookies. Om läget för cookie-begränsning är inaktiverat samlar Adobe Commerce in beteendedata som standard.