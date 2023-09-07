---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Versionsinformation'
description: "Läs versionsinformationen för information om alla [!DNL Store Fulfillment by Walmart Commerce Technologies] releaser."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# Versionsinformation

I versionsinformationen beskrivs den första versionen av [!DNL Store Fulfillment Services by Walmart Commerce Technologies] och innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigerat problem](../assets/fix.svg) Korrigeringar och förbättringar
![Känt fel](../assets/bug.svg) Kända fel

Se [Kommande versioner](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) om du vill veta mer om releasescheman och support.

Se [Produkttillgänglighet](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) om du vill veta vilka Adobe Commerce-versioner som stöder det här tillägget.

## v1.5.0

*3 augusti 2023*

[!BADGE Stöds]{type=Informative tooltip="Stöds"}[Adobe Commerce 2.4.4 till 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), inklusive säkerhetsuppdateringarna 2.4.6-p1, 2.4.5-p3 och 2.4.4-p4

Den här versionen innehåller följande uppdateringar:

![Nytt](../assets/fix.svg) Tillägget har uppdaterats för att ge support [Adobe Commerce säkerhetsuppdateringar](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 och 2.4.4-p4.

![Nytt](../assets/new.svg)<!-- WMTP-918 --> Stöd för [Asynkron sändning](sales-emails.md) konfigurationsalternativ för säljmeddelanden. Handlare som uppgraderar till version 1.5.0 kan skicka e-postmeddelanden direkt (standard) eller asynkront.

![Nytt](../assets/new.svg)<!-- WMTP-916--> Uppdaterade [Källkonfiguration](merchant-store-configuration.md) som har stöd för internationella telefonnummerformat.

![Nytt](../assets/new.svg) Lagt till logik för att förhindra att återbetalningsbelopp överskrider det återstående eller fakturerade beloppet.

![Nytt](../assets/new.svg)<!-- WMTP-882 --> Ersatt `google.map.LatLng` objekt med JSON-litteraler som stöder kompatibilitet med äldre versioner av [!DNL Google Maps].

![Korrigerat problem](../assets/fix.svg)<!-- WMTP- --> Skriptet som skapar `[!DNL Available for Store Pickup]` och `[!DNL Available for Home Delivery]` produktattribut för att förhindra konflikter mellan attributkategorier.

![Korrigerat problem](../assets/fix.svg)<!-- WMTP-915 --> Korrigerade ett kompatibilitetsproblem som orsakade en oändlig loop när vissa entiteter lästes in och sparades.

![Korrigerat problem](../assets/fix.svg)<!-- WMTP-921 --> Korrigerade ett problem som förhindrade [!DNL Ship to Store] offertvalidering från att utlösa när en artikel läggs till i kundvagnen från en produktinformationssida (PDP).

![Korrigerat problem](../assets/fix.svg)<!-- WMTP- 932 --> Ett utcheckningsproblem har korrigerats som gjorde att kunder kunde välja hemleveransmetod för artiklar som inte är berättigade för hemleverans.

![Korrigerat problem](../assets/fix.svg) Installationsuppdateringar:

- <!-- WMTP-880--> Ett problem som orsakade att en felaktig webbplatskod returnerades vid installationen av [!DNL Store Fulfillment] tillägg.

- <!-- WMTP-878--> Korrigerade ett problem för SKU-heltal som krävde att datatypen skulle konverteras till strängtyp under installationen.

![Korrigerat problem](../assets/fix.svg)<!-- WMTP-915--> Korrigerade ett fel som orsakades av en felkod för saknad incheckning.

![Korrigerat problem](../assets/fix.svg)<!-- WMTP-932 --> Korrigerade ett fel relaterat till delvis avvisande under utdelningsåtgärder.

![Nytt](../assets/new.svg)<!-- WMTP-953 --> API-slutpunkten för Cancel har uppdaterats så att statusparametern används som ett valfritt objekt.

![Nytt](../assets/new.svg)<!-- WMTP-960 --> Förbättrad loggningsinformation för Dispense API-slutpunkten.

## v1.4.0

*13 april 2023*

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/fix.svg) [!DNL Store Fulfillment] är nu [kompatibel med [!DNL Adobe Commerce] 2.4.4 till 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27 februari 2023*

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

Den här versionen innehåller följande uppdatering:

![Nytt](../assets/fix.svg)<!-- WMTP-795 --> Lagt till möjlighet att inaktivera Store Fulfillment-lösningen för en specifik plats genom att ändra standardomfånget för systemkonfigurationsinställningen från webbplats till global.

## v1.2.0

*27 september 2022*

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

Den här versionen innehåller följande uppdatering:

![Nytt](../assets/fix.svg) [!DNL Store Fulfillment] är nu [kompatibel med [!DNL Adobe Commerce] 2.4.4 till 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15 juli 2022*

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

Stabilitet: Allmän tillgänglighet

![Nytt](../assets/fix.svg)<!-- WMTP-731 --> Förenklad [Konfiguration av incheckningsupplevelse](check-in-experience-setup.md) för Store Assist-appen genom att lägga till standardbilfabrikat och modellval. I den tidigare versionen var handlarna tvungna att konfigurera bilfabrikat och modellval manuellt.

## v1.0.0

*4 mars 2022*

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

Stabilitet: Allmän tillgänglighet

## App för Store Assist

Mer information om nya versioner av Store Assist-appen finns i appinformationen i [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
