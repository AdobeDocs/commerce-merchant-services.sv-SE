---
title: '''[!DNL Catalog Service] Versionsinformation'
description: Den senaste versionsinformationen för [!DNL Catalog Service] för Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 72913e0c0b7364e38d37fe1a8279c40a4e849c02
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# [!DNL Catalog Service] Versionsinformation

{{catalog-service-beta}}

I versionsinformationen beskrivs de senaste versionerna av [!DNL Catalog Service] och innehåller:

* ![Nytt](../assets/new.svg) - Nya funktioner
* ![Korrigera](../assets/fix.svg) - Korrigeringar och förbättringar
* ![Fel](../assets/bug.svg) - Kända fel

## Betaversion

* ![Nytt](../assets/new.svg) - `products` och `refineProduct` frågor returnerar följande data:
   * Fördefinierade produktattribut (system).
   * Dynamiska produktattribut och filtrera dem efter roll (produktvisningssida/produktlistsida).
   * Produktalternativ.
   * Produktbilder och filtrera dem efter roll (PDP/PLP).
   * Ett specifikt pris för enkla produkter och prisintervall för konfigurerbara produkter.
   * Kundgruppspriser och prisintervall. De returnerar ett standardgrundpris för kunderna utan någon kundgrupp.
   * Produkttyper där B2B-kundspecifika priser används.

## Kända begränsningar

* Paket och grupperade produkter stöds inte.
* Prisnivån stöds inte.
* I en array med bilder innehåller bara den första bilden roller.
* Bilder för varianter hämtas inte.
* Uppdateringar tas inte emot när produkter eller varianter tas bort från katalogen.
