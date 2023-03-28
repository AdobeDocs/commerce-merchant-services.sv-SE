---
title: '''[!DNL Catalog Service] Versionsinformation'
description: Den senaste versionsinformationen för [!DNL Catalog Service] för Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: c65717c449793dccfed101e1411b22c69fba308d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionsinformation

I versionsinformationen beskrivs de senaste versionerna av [!DNL Catalog Service] och innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigera](../assets/fix.svg) Korrigeringar och förbättringar
![Fel](../assets/bug.svg) Kända fel

## Aktuell huvudversion

### Version V1.6

_28 mars 2023_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Lagt till färgrutor i [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) fråga.
![Nytt](../assets/new.svg) Lagt till möjlighet att få `entityId` använda [API-nät](mesh.md).

#### Kända begränsningar

Dessa funktioner stöds ännu inte:

* Paketprodukter med fast pris
* Inga uppdateringar tas emot när varianter tas bort från katalogen.
* Maximal storlek för nyttolasten för dynamiska attribut är 9 MB.
* Gruppproduktpris. Kan beräknas med enkla produktpriser.
* I en bildarray innehåller endast den första bilden roller.

Följande begränsningar kan åtgärdas med API Mesh och Core GraphQL API:

* Lägsta kampanjpris
* [Nivåpriser](mesh.md)
* Nedladdningsbara produkter och presentkort

### Version V1.5

_6 mars 2023_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Tillagd [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL funktionalitet.
![Korrigera](../assets/fix.svg) Förbättrade prestanda och API-skalbarhet.

### Version V1.4

_7 februari 2023_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Publicerat katalogtjänstpaket för att förenkla installationen.
![Korrigera](../assets/fix.svg) API-skalbarhet och prestandaförbättringar.

### Version V1.3

_17 januari 2023_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Förenklad och förbättrad startupplevelse.
![Nytt](../assets/new.svg) Nya slutpunkter för kundsandlådor finns tillgängliga för testning före produktion.
![Nytt](../assets/new.svg) Stöd tillagt för virtuella produkter.
![Korrigera](../assets/fix.svg) API-skalbarhet och prestandaförbättringar.

### Version V1.1

_18 november 2022_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Katalogtjänsten har nu stöd för Adobe [API-nät](https://developer.adobe.com/graphql-mesh-gateway/).
![Korrigera](../assets/fix.svg) Förbättrad API-skalbarhet och övergripande prestanda.

### Version V1.0

_4 oktober 2022_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Nu support för paketerade och grupperade produkter.
![Nytt](../assets/new.svg) B2B-synlighetsåsidosättningar har lagts till. Produkterna är nu sökbara och kan läggas till i kundvagnen för specifika kundgrupper.
![Korrigera](../assets/fix.svg) Tjänsten är nu stabilare och har förbättrat prestandan.

## Tidigare versioner

+++betaversioner

### 0.3-versionen - Beta+

_12 september 2022_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) Bilder för varianter som stöds: produktbilder returneras baserat på de valda alternativen
![Nytt](../assets/new.svg) Roller för prisstöd: tillåt endast medlemmar i specifika kundgrupper att se priset på produkterna
![Korrigera](../assets/fix.svg) Förbättrad stabilitet och prestanda för tjänsten
![Nytt](../assets/new.svg) Uppdateringar tas emot när produkter tas bort från katalogen

### Betaversion

_9 augusti 2022_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) The `products` och `refineProduct` frågor returnerar följande data:

* Fördefinierade produktattribut (system).
* Dynamiska produktattribut och filtrera dem efter roll (produktvisningssida/produktlistsida).
* Produktalternativ.
* Produktbilder och filtrera dem efter roll (PDP/PLP).
* Ett specifikt pris för enkla produkter och prisintervall för konfigurerbara produkter.
* Kundgruppspriser och prisintervall. De returnerar ett standardgrundpris för kunderna utan någon kundgrupp.
* Produkttyper där B2B-kundspecifika priser används.

+++
