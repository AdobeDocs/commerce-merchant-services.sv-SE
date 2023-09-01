---
title: '[!DNL Catalog Service] Versionsinformation'
description: Den senaste versionsinformationen för [!DNL Catalog Service] för Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 822108fb92b2cac7cc62d00db035faed81ae9e25
workflow-type: tm+mt
source-wordcount: '496'
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

### Version V1.11

_18 juli 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten har nu stöd för [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) GraphQL query for Product Recommendations.

#### Kända begränsningar

Dessa funktioner stöds ännu inte:

* Paketprodukter med fast pris
* Maximal storlek för nyttolasten för dynamiska attribut är 9 MB.
* Gruppproduktpris. Kan beräknas med enkla produktpriser.
* I en bildarray innehåller endast den första bilden roller.

Följande begränsningar kan åtgärdas med API Mesh och Core GraphQL API:

* Lägsta kampanjpris
* [Nivåpriser](mesh.md)
* Nedladdningsbara produkter och presentkort

### Version V1.10

_27 juni 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten kan nu visa relaterade produkter i widgeten Produktinformationssida.

### Version V1.7

_12 april 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Katalogtjänsten rensar nu borttagna produktvarianter.
![Korrigera](../assets/fix.svg) Infrastrukturskalbarhet och prestandaförbättringar.

### Version V1.6

_28 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Lagt till färgrutor i [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) fråga.
![Nytt](../assets/new.svg) Lagt till möjlighet att få `entityId` använda [API-nät](mesh.md).

### Version V1.5

_6 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) Tillagd [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL funktionalitet.
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

## Tidigare versioner

+++betaversioner

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

+++
