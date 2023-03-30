---
title: Versionsinformation
description: Den senaste versionsinformationen för Adobe Experience Platform Connector från Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 735fd14fad22826b04320644e120d296de19a211
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 1%

---

# Versionsinformation

Versionsinformationen innehåller uppdateringar för Experience Platform-anslutningen och innehåller:

* ![Nytt](../assets/new.svg) - Nya funktioner
* ![Korrigera](../assets/fix.svg) - Korrigeringar och förbättringar
* ![Fel](../assets/bug.svg) - Kända fel

Information om funktionsändringar och korrigeringar för tillägg som används av kopplingen för Experience Platform finns i **Uppdateringar av tjänster som stöds**.

Se [Kommande versioner](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) om du vill veta mer om releasescheman och support.

Läs utvecklardokumentationen för att [läs om produktkompatibilitet](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Uppdateringar av tjänster som stöds

I versionsinformationen beskrivs funktionsändringar och korrigeringar för tillägg som används av Experience Platform-anslutningen.

+++Supported service updates

_30 mars 2023_

* ![Nytt](../assets/new.svg) - Ett nytt tillägg har lagts till som kallas `data-services-b2b` som innehåller [rekvisitionslistehändelser](events.md#b2b-events) för B2B-handlare
* ![Nytt](../assets/new.svg) - Lade till `uniqueIdentifier` fält till [sök](events.md#search-events) händelser. I det här nya fältet kan handlare korsreferera till vilka sökförfrågningar som motsvarar vilka söksvar.

_12 oktober 2022_

* ![Nytt](../assets/new.svg) - Två har lagts till [storefront-händelser](events.md): `openCart` och `removeFromCart` till Adobe Commerce Storefront Events SDK och Collector
* ![Nytt](../assets/new.svg) - Stöd för [AEM](overview.md#aem-support)

+++

## 2.2.0

_30 mars 2023_

* ![Nytt](../assets/new.svg) - Paketerad `commerce-data-export` och `saas-export` beroenden med `experience-platform-connector` tillägg. Tidigare var du tvungen att installera dessa beroenden separat. Dessa beroenden, tillsammans med handelskonfigurationen, möjliggör bearbetning på serversidan av [back office-händelser](events.md#back-office-events).
* ![Nytt](../assets/new.svg) - En ny back office-händelse har lagts till [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 februari 2023_

* ![Nytt](../assets/new.svg) - Stöd för PHP 8.2 har lagts till för alla anslutningsmoduler för Experience Platform

## 2.1.0

_17 januari 2023_

* ![Nytt](../assets/new.svg) - Uppdaterade [Administratör för Experience Platform-anslutning](connect-data.md) så att du kan ange en egen AEP Web SDK (legering). Dessutom har en möjlighet för handlare som deltar i betaprogrammet att skicka [back office-händelsedata](connect-data.md#data-collection) till kanten. Dessa händelser innehåller [orderstatusinformation](events.md#beta-order-status-events) om en beställning, t.ex. om en beställning har placerats, annullerats, återbetalats eller skickats.
* ![Korrigera](../assets/fix.svg) Ändrad till att använda `identityMap` i stället för `personID` när du anger den primära identiteten för data som flyttas till kanten.

## 2.0.1

_10 november 2022_

* ![Korrigerat problem](../assets/fix.svg) - Nu ställs Adobe Experience Platform-kontexten in först efter att händelseinsamlaren i Storefront och Storefront Event SDK har lästs in.

## 2.0.0

_12 oktober 2022_

* ![Nytt](../assets/new.svg) - Möjlighet att ange egen AEP Web SDK när [koppla](connect-data.md) din Adobe Commerce-instans till Experience Platform
* ![Korrigera](../assets/fix.svg) - Uppdaterat datastream-omfångskrav så att dataStream ID:n måste omfång till webbplatsen i stället för att lagras

## 1.0.0

_9 augusti 2022_

* ![Nytt](../assets/new.svg) - Allmän tillgänglighetsrelease

## Dokumentation

Mer information:

* [Adobe Commerce Developer Documentation](https://devdocs.magento.com/)
* [Adobe Commerce Användarhandbok](https://docs.magento.com/user-guide/)
