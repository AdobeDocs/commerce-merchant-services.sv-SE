---
title: '"[!DNL Catalog Service]"'
description: '"[!DNL Catalog Service] för Adobe Commerce är ett sätt att hämta innehåll från produktvisningssidor och produktlistsidor mycket snabbare än med Adobe Commerce GraphQL-frågor."'
source-git-commit: eb2242ac99cfaef4ed75936a1b5cc800cc451c83
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# [!DNL Catalog Service] för Adobe Commerce

{{catalog-service-beta}}

The [!DNL Catalog Service] för Adobe Commerce-tillägg innehåller omfattande katalogdata för visningsmodell (skrivskyddad) för att snabbt och fullständigt återge produktrelaterade butiksupplevelser, inklusive:

* Produktinformationssidor
* Produktlista och kategorisidor
* Sökresultatsidor
* Produktkaruseller
* Produktjämförelsesidor
* Andra sidor som återger produktdata, t.ex. kundvagn, beställning och önskelistesidor

The [!DNL Catalog Service] använder [GraphQL](https://graphql.org/) för att begära och ta emot produktdata. GraphQL är ett frågespråk som en klientklient använder för att kommunicera med API:t som definierats på en serverdel som Adobe Commerce. GraphQL är en populär kommunikationsmetod eftersom den är lätt att använda och en systemintegratör kan ange innehåll och ordning för varje svar.

Adobe Commerce har två GraphQL-system. Det centrala GraphQL-systemet har ett brett urval av frågor (läsåtgärder) och mutationer (skrivåtgärder) som gör att en kund kan interagera med många olika typer av sidor, bland annat produkt, kundkonto, kundvagn, utcheckning med mera. De frågor som returnerar produktinformation är dock inte optimerade för snabbhet. Tjänsterna GraphQL-systemet kan bara utföra frågor för produkter och relaterad information. De här frågorna är mer prestandavänliga än liknande kärnfrågor.

## Arkitektur

I följande diagram visas de två GraphQL-systemen:

![Katalogarkitektur - diagram](assets/catalog-service-architecture.png)

I det centrala GraphQL-systemet skickar PWA en begäran till Commerce-programmet, som tar emot varje begäran, bearbetar den, skickar eventuellt en begäran via flera delsystem och returnerar sedan ett svar till butiken. Denna rundtur kan orsaka långsam sidinläsning vilket kan leda till lägre konverteringsgrader.

[!DNL Catalog Service] skickar frågor till en separat GraphQL-gateway. Tjänsten har åtkomst till en separat databas som innehåller produktinformation och relaterad information, t.ex. produktattribut, varianter, priser och kategorier. Tjänsten synkroniserar databasen med Adobe Commerce genom indexering.
Eftersom tjänsten åsidosätter direkt kommunikation med programmet kan den minska fördröjningen för begäran- och svarscykeln.

>[!NOTE]
>
>Gatewayen är till för framtida integrering med [!DNL Live Search] och [!DNL Product Recommendations]. I den här versionen har du åtkomst [!DNL Catalog Service] och Live Search-frågor från samma slutpunkt, om du har en giltig licensnyckel för båda produkterna. Frågorna från de två produkterna delar dock för närvarande inga svarsdata.

GraphQL-systemen för kärna och tjänster kommunicerar inte direkt med varandra. Du kommer åt alla system från olika URL-adresser och anrop kräver olika rubrikinformation. De två GraphQL-systemen är utformade för att användas tillsammans. The [!DNL Catalog Service] GraphQL-systemet utökar huvudsystemet för att göra produktbutiksupplevelserna snabbare.

Du kan också implementera [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) för att integrera de två Adobe Commerce GraphQL-systemen med privata och tredjeparts-API:er och andra programgränssnitt med Adobe Developer. Nätet kan konfigureras så att anrop som dirigeras till varje slutpunkt innehåller rätt auktoriseringsinformation i rubrikerna.

## Implementering

Installationsprocessen kräver att [Commerce Services Connector](../landing/saas.md). När det är klart är nästa steg att en systemintegratör ska uppdatera storefront-koden så att den innehåller [!DNL Catalog Service] frågor. Alla [!DNL Catalog Service] frågor dirigeras till GraphQL-gatewayen. URL:en anges under introduktionsprocessen.

[Adobe Commerce Devdocs](https://devdocs.magento.com/catalog-service/index.html) beskriver skillnaderna mellan kärnan och [!DNL Catalog Service] frågor. Referensinformation för varje fråga inkluderas också.
