---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] för Adobe Commerce är ett sätt att hämta innehållet på produktvisningssidor och produktlistsidor mycket snabbare än med de ursprungliga Adobe Commerce GraphQL-frågorna."'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
recommendations: noCatalog
source-git-commit: 8e349cb8cfba7c4d828a6f3666a3b27fecfdbd15
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# [!DNL Catalog Service] för Adobe Commerce

The [!DNL Catalog Service] för Adobe Commerce-tillägg innehåller omfattande katalogdata för visningsmodell (skrivskyddad) för att snabbt och fullständigt återge produktrelaterade butiksupplevelser, inklusive:

* Produktinformationssidor
* Produktlista och kategorisidor
* Sök på resultatsidor
* Produktkaruseller
* Produktjämförelsesidor
* Andra sidor som återger produktdata, t.ex. kundvagn, beställning och önskelistesidor

The [!DNL Catalog Service] använder [GraphQL](https://graphql.org/) för att begära och ta emot produktdata. GraphQL är ett frågespråk som en klientklient använder för att kommunicera med API:t som definierats på en serverdel som Adobe Commerce. GraphQL är ett populärt kommunikationssätt eftersom det är lätt och gör att en systemintegratör kan ange innehåll och ordning för varje svar.

Adobe Commerce har två GraphQL-system. GraphQL system innehåller ett stort antal frågor (läsoperationer) och mutationer (skrivåtgärder) som gör att en kund kan interagera med många olika typer av sidor, bland annat produkt, kundkonto, kundvagn, utcheckning med mera. De frågor som returnerar produktinformation är dock inte optimerade för snabbhet. De tjänster som GraphQL system kan bara utföra frågor om produkter och relaterad information. De här frågorna är mer prestandavänliga än liknande kärnfrågor.

Katalogtjänstkunder kan använda den nya [SaaS prisindexerare](../price-index/index.md), vilket ger snabbare prisförändringsuppdateringar och synkroniseringstid.

## Arkitektur

I följande diagram visas de två GraphQL-systemen:

![Katalogarkitektur - diagram](assets/catalog-service-architecture.png)

I GraphQL huvudsystem skickar PWA en begäran till Commerce-applikationen som tar emot varje begäran, bearbetar den, eventuellt skickar en begäran via flera delsystem och sedan returnerar ett svar till butiken. Denna rundtur kan orsaka långsam sidinläsning vilket kan leda till lägre konverteringsgrader.

[!DNL Catalog Service] är en Storefront Services Gateway. Tjänsten har åtkomst till en separat databas som innehåller produktinformation och relaterad information, t.ex. produktattribut, varianter, priser och kategorier. Tjänsten synkroniserar databasen med Adobe Commerce genom indexering.
Eftersom tjänsten åsidosätter direkt kommunikation med programmet kan den minska fördröjningen för begäran- och svarscykeln.

De centrala systemen och tjänsterna i GraphQL kommunicerar inte direkt med varandra. Du kommer åt alla system från olika URL-adresser och anrop kräver olika rubrikinformation. De två GraphQL-systemen är utformade för att användas tillsammans. The [!DNL Catalog Service] GraphQL system utökar bassystemet för att göra produktbutiksupplevelserna snabbare.

Du kan också implementera [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) för att integrera de två Adobe Commerce GraphQL-systemen med privata och tredjeparts-API:er och andra programgränssnitt med Adobe Developer. Nätet kan konfigureras så att anrop som dirigeras till varje slutpunkt innehåller rätt auktoriseringsinformation i rubrikerna.

## Arkitektinformation

I följande avsnitt beskrivs några av skillnaderna mellan de två GraphQL-systemen.

### Schemahantering

Eftersom katalogtjänsten fungerar som en tjänst behöver integratörer inte bekymra sig om den underliggande versionen av Commerce. Syntaxen för frågorna är densamma för alla versioner. Dessutom är schemat konsekvent för alla handlare. Den här konsekvensen gör det enklare att fastställa bästa praxis och ökar återanvändningen av widgetar för butiker avsevärt.

### Förenkling av produkttyper

Schemat minskar antalet olika produkttyper till två användningsområden:

* Enkla produkter är sådana som definieras med ett enda pris och en enda kvantitet. Katalogtjänsten mappar enkla, virtuella, hämtningsbara och presentkortsprodukter till `simpleProductViews`.

* Komplexa produkter består av flera enkla produkter. Komponentens enkla produkter kan ha olika priser. En komplex produkt kan också definieras så att kunden kan ange hur många av de enkla komponentprodukterna som ska ingå. Katalogtjänsten mappar konfigurerbara, paketerade och grupperade produkttyper till `complexProductViews`.

Komplexa produktalternativ förenas och särskiljs utifrån deras beteende, inte typ. Varje alternativvärde representerar en enkel produkt. Det här alternativvärdet ger tillgång till de enkla produktattributen, inklusive pris. När kunden väljer alla alternativ för en komplex produkt pekar kombinationen av de valda alternativen på en viss enkel produkt. Den enkla produkten är tvetydig tills kunden väljer ett värde för alla tillgängliga alternativ.

### Priser

Enkla produkter representerar den basförsäljningsenhet som har ett pris. Katalogtjänsten beräknar det ordinarie priset före rabatter samt det slutliga priset efter rabatter. Prisberäkningarna kan inkludera fasta produktskatter. De utesluter personaliserade kampanjer.

En komplex produkt har inget fast pris. Katalogtjänsten returnerar i stället priset för länkade exempel. Som exempel kan en handlare till en början tilldela samma priser till alla varianter av en konfigurerbar produkt. Om vissa storlekar eller färger är opopulära kan handlaren sänka priserna på dessa varianter. Priset på den komplexa (konfigurerbara) produkten visar alltså först ett prisintervall som återspeglar priset på både standardvarianter och impopulära varianter. När kunden har valt ett värde för alla tillgängliga alternativ visas ett pris i butiken.

>[!NOTE]
>
> Handla kunder med [!DNL Catalog Service] kan dra nytta av snabbare prisändringar och synkroniseringstid på sina webbplatser med [SaaS prisindexerare](../price-index/index.md).

## Implementering

Installationsprocessen kräver att [Commerce Services Connector](../landing/saas.md). När det är klart är nästa steg att en systemintegratör ska uppdatera storefront-koden så att den innehåller [!DNL Catalog Service] frågor. Alla [!DNL Catalog Service] frågor dirigeras till GraphQL gateway. URL:en anges under introduktionsprocessen.
