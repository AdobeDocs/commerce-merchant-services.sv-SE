---
title: '''[!DNL Catalog Service] Versionsinformation'
description: Den senaste versionsinformationen för [!DNL Catalog Service] för Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: bb557e130a7dbef96c625d65cbe191a4ccbe26d0
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionsinformation

I versionsinformationen beskrivs de senaste versionerna av [!DNL Catalog Service] och innehåller:

* ![Nytt](../assets/new.svg) - Nya funktioner
* ![Korrigera](../assets/fix.svg) - Korrigeringar och förbättringar
* ![Fel](../assets/bug.svg) - Kända fel

## Version V1.0

Releasedatum: 2022-10-04 Kompatibel med Adobe Commerce (EE): 2.4.x Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x Stabilitet: Allmän tillgänglighet

![Nytt](../assets/new.svg) - Nu support för paketerade och grupperade produkter.
![Nytt](../assets/new.svg) - B2B-synlighetsåsidosättningar har lagts till. Produkterna är nu sökbara och kan läggas till i kundvagnen för specifika kundgrupper.
![Korrigera](../assets/fix.svg) - Tjänsten är nu stabilare och har förbättrat prestandan.

### Kända begränsningar

Dessa funktioner stöds ännu inte:

* Nivåpriser
* Uppdateringar tas inte emot när varianter tas bort från katalogen
* Största storlek för nyttolasten för dynamiska attribut är &lt;9MB
* Fast pris för paketprodukter
* Totalt pris för grupperade produkter
* Stöd för virtuella, nedladdningsbara och presentkortsprodukter
* Lägsta kampanjpris (MAP)

## 0.3-versionen - Beta+

Releasedatum: 2022-09-12 Kompatibel med Adobe Commerce (EE): 2.4.x Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x Stabilitet: Beta

![Nytt](../assets/new.svg) - Bilder för varianter som stöds: produktbilder returneras baserat på de valda alternativen
![Nytt](../assets/new.svg) - Roller för prisstöd: tillåt endast medlemmar i specifika kundgrupper att se priset på produkterna
![Korrigera](../assets/fix.svg) - Förbättrad stabilitet och prestanda för tjänsten
![Nytt](../assets/new.svg) - Uppdateringar tas emot när produkter tas bort från katalogen

### Kända begränsningar

Dessa funktioner stöds ännu inte:

* Nivåpriser
* Paket och grupperade produkter
* Inga uppdateringar tas emot när varianter tas bort från katalogen
* B2B-synlighetsåsidosättningar: produkter kan vara sökbara eller läggas till i kundvagnen för specifika kundgrupper

## Betaversion

Releasedatum: 2022-08-09 Kompatibel med Adobe Commerce (EE): 2.4.x Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x Stabilitet: Beta

* ![Nytt](../assets/new.svg) - `products` och `refineProduct` frågor returnerar följande data:
* Fördefinierade produktattribut (system).
* Dynamiska produktattribut och filtrera dem efter roll (produktvisningssida/produktlistsida).
* Produktalternativ.
* Produktbilder och filtrera dem efter roll (PDP/PLP).
* Ett specifikt pris för enkla produkter och prisintervall för konfigurerbara produkter.
* Kundgruppspriser och prisintervall. De returnerar ett standardgrundpris för kunderna utan någon kundgrupp.
* Produkttyper där B2B-kundspecifika priser används.

### Kända begränsningar

* Paket och grupperade produkter stöds inte.
* Prisnivån stöds inte.
* I en array med bilder innehåller bara den första bilden roller.
* Bilder för varianter hämtas inte.
* Uppdateringar tas inte emot när produkter eller varianter tas bort från katalogen.
