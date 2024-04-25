---
title: '''[!DNL Catalog Service] Versionsinformation'
description: Den senaste versionsinformationen för [!DNL Catalog Service] för Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 0c4bd1aa58dced3d21edae529da367426c973034
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionsinformation

I versionsinformationen beskrivs de senaste versionerna av [!DNL Catalog Service].
Support ges för den aktuella större versionen. Versionsinformation för äldre versioner finns som referens.
Bland uppdateringarna finns:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigera](../assets/fix.svg) Korrigeringar och förbättringar
![Fel](../assets/bug.svg) Kända fel

## Aktuell huvudversion

### Version V1.18

_11 april 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Stöd för PHP 8.3 har lagts till.

![Nytt](../assets/new.svg) The [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) frågan returnerar nu anpassningsbara alternativdata för både enkla och komplexa produkter.<!--DATA-5538-->

### Version V1.17

_22 februari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) The [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) är nu tillgängligt. Den här förbättrade instrumentpanelen ger insikter i dataströmmar för [!DNL Product Recommendations], [!DNL Live Search]och [!DNL Catalog Service]. Stöd för den här funktionen introducerades i version 3.1.0 av `catalog-service` metapackage.

## Tidigare versioner

+++ Tidigare versioner

### Version V1.16

_13 februari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Produktvideor stöds nu av katalogtjänstens API.
![Korrigera](../assets/fix.svg) Stöd finns nu för paketprodukter med fasta priser.
![Korrigera](../assets/fix.svg) Alternativ utanför lagret visas nu i PDP-widgeten.

#### Kända begränsningar

Dessa funktioner stöds ännu inte:

* Maximal storlek för nyttolasten för dynamiska attribut är 9 MB.
* Gruppproduktpris. Detta värde kan beräknas med enkla produktpriser.
* I en bildarray innehåller endast den första bilden roller.

Följande begränsningar kan åtgärdas med API Mesh och Core GraphQL API:

* Lägsta kampanjpris
* [Nivåpriser](mesh.md)

### Version V1.13

_12 oktober 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten stöder `inStock` för produktvarianter.
![Nytt](../assets/new.svg) The `urlKey` och `externalId` fält har lagts till i GraphQL-schemat.
![Nytt](../assets/new.svg) Nu finns det stöd för nedladdningsbara produkter och presentkort.

### Version V1.12

_19 september 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten använder nu [SaaS-prisindexering](../price-index/price-indexing.md).
![Korrigera](../assets/fix.svg) Den här versionen innehåller felkorrigeringar och förbättringar på tjänstsidan.

### Version V1.11

_18 juli 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten har nu stöd för [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) GraphQL query for Product Recommendations.

### Version V1.10

_27 juni 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänstens API har nu stöd för `related products`.

### Version V1.7

_12 april 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten rensar nu borttagna produktvarianter.
![Korrigera](../assets/fix.svg) Infrastrukturskalbarhet och prestandaförbättringar.

### Version V1.6

_28 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Lagt till färgrutor i [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) fråga.
![Nytt](../assets/new.svg) Lagt till möjlighet att få `entityId` använda [API-nät](mesh.md).

### Version V1.5

_6 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Tillagd [`categories`](https://developer.adobe.com/commerce/services/graphql/schema/catalog-service/categories/) GraphQL funktionalitet.
![Korrigera](../assets/fix.svg) Förbättrade prestanda och API-skalbarhet.

### Version V1.4

_7 februari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Publicerat katalogtjänstpaket för att förenkla installationen.
![Korrigera](../assets/fix.svg) API-skalbarhet och prestandaförbättringar.

### Version V1.3

_17 januari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Förenklad och förbättrad startupplevelse.
![Nytt](../assets/new.svg) Nya slutpunkter för kundsandlådor finns tillgängliga för testning före produktion.
![Nytt](../assets/new.svg) Stöd tillagt för virtuella produkter.
![Korrigera](../assets/fix.svg) API-skalbarhet och prestandaförbättringar.

### Version V1.1

_18 november 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten har nu stöd för Adobe [API-nät](https://developer.adobe.com/graphql-mesh-gateway/).
![Korrigera](../assets/fix.svg) Förbättrad API-skalbarhet och övergripande prestanda.

### Version V1.0

_4 oktober 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Nu support för paketerade och grupperade produkter.
![Nytt](../assets/new.svg) B2B-synlighetsåsidosättningar har lagts till. Produkterna är nu sökbara och kan läggas till i kundvagnen för specifika kundgrupper.
![Korrigera](../assets/fix.svg) Tjänsten är nu stabilare och har förbättrat prestandan.

### 0.3-versionen - Beta+

_12 september 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Bilder för variantstöd: produktbilder returneras baserat på de valda alternativen
![Nytt](../assets/new.svg) Roller för prissupport: endast medlemmar i specifika kundgrupper kan se priset på produkter
![Korrigera](../assets/fix.svg) Förbättrad stabilitet och prestanda för tjänsten
![Nytt](../assets/new.svg) Uppdateringar tas emot när produkter tas bort från katalogen

### Betaversion

_9 augusti 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) The `products` och `refineProduct` frågor returnerar följande data:

* Fördefinierade produktattribut (system).
* Dynamiska produktattribut och filtrera dem efter roll (produktvisningssida/produktlistsida).
* Produktalternativ.
* Produktbilder och filtrera dem efter roll (PDP/PLP).
* Ett specifikt pris för enkla produkter och prisintervall för konfigurerbara produkter.
* Kundgruppspriser och prisintervall. De returnerar ett standardgrundpris för kunderna utan någon kundgrupp.
* Produkttyper där B2B-kundspecifika priser används.
