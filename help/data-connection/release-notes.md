---
title: Versionsinformation
description: Den senaste versionsinformationen för [!DNL Data Connection] från Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: c95b1fc9393c507dd757c74c30473590760d47a6
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# Versionsinformation

>[!IMPORTANT]
>
>Experience Platform-anslutningen har bytt namn till [!DNL Data Connection].

Versionsinformationen innehåller uppdateringar av [!DNL Data Connection] och innehåller

![Nytt](../assets/new.svg) - Nya funktioner
![Korrigera](../assets/fix.svg) - Korrigeringar och förbättringar
![Fel](../assets/bug.svg) - Kända fel

För funktionsändringar och korrigeringar relaterade till tillägg som används av [!DNL Data Connection] tillägg, se **Uppdateringar av tjänster som stöds**.

Se [Kommande versioner](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) om du vill veta mer om releasescheman och support.

Läs utvecklardokumentationen för att [ta reda på vilka Commerce-versioner som stöder den här modulen](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Uppdateringar av tjänster som stöds

I versionsinformationen beskrivs funktionsändringar och korrigeringar för tillägg som används av [!DNL Data Connection] tillägg.

+++Supported service updates

_24 januari 2024_

![Nytt](../assets/new.svg) - Uppdaterade `data-services-b2b` tillägg som ska innehålla en ny rekvisitionshändelse som kallas [deleteRequisitionList](events.md#deleterequisitionlist) för B2B-handlare.

_16 november 2023_

![Korrigera](../assets/fix.svg) - Korrigerade ett problem där ett felmeddelande felaktigt visades när du gjorde en beställning med flera leveransadresser.
![Korrigera](../assets/fix.svg) - Korrigerade ett problem i [productPageView](events.md#productpageview) händelse där `productListItems.priceTotal` Händelsefältet konverterade inte priset efter växling av valutan i butiksvyn.
![Korrigera](../assets/fix.svg) - Korrigerade ett problem i `productListItems` händelsefält där valutakoden inte uppdaterades när handlaren växlade butiksvyn.

_10 oktober 2023_

![Nytt](../assets/new.svg) - Nya orderstatushändelser har lagts till: [Fakturerad order](events-backoffice.md#orderinvoiced), [Orderartikelretur initierad](events-backoffice.md#orderitemsreturninitiated)och [Orderartikelretur slutförd](events-backoffice.md#orderitemreturncompleted).
![Korrigera](../assets/fix.svg) - Korrigerade ett problem där ändringar i valutakonfigurationen inte återspeglades i händelserna efter att cachen uppdaterades.
![Korrigera](../assets/fix.svg) - Ett fel har korrigerats när orderbekräftelsemeddelandet inte visas om asynkron orderplacering är aktiverad.
![Nytt](../assets/new.svg) - Lagt till data i [addToRequisitionList](events.md#addtorequisitionlist) -händelse för enkla produkter på kategorivysidan.
![Korrigera](../assets/fix.svg) - Korrigerade ett problem i `selectedOptions` data i [addToRequisitionList](events.md#addtorequisitionlist) händelse när produkter läggs till från orderbekräftelsesidan.
![Nytt](../assets/new.svg) - Lagt till produktdata i [addToRequisitionList](events.md#addtorequisitionlist) händelse när produkter läggs till i rekvisitionslistan från kategorivysidan.
![Nytt](../assets/new.svg) - Tillagt [addToRequisitionList](events.md#addtorequisitionlist) händelse när konfigurerbara produkter läggs till i rekvisitionslistan från sidan Produktvy.
![Nytt](../assets/new.svg) - Tillagt [addToRequisitionList](events.md#addtorequisitionlist) och [removeFromRequisitionList](events.md#removefromrequisitionlist) händelser när produktkvantiteten ökas och/eller minskas från en rekvisitionslista.

_10 juni 2023_

![Korrigera](../assets/fix.svg) - Korrigerade ett problem när `orderId` skickades inte i kontexten på grund av prefix i identifieraren för handelsorder.
![Korrigera](../assets/fix.svg) - Uppdaterade säkerhetsprincipkonfigurationer.

_30 mars 2023_

![Nytt](../assets/new.svg) - Ett tillägg som anropades har lagts till `data-services-b2b` som innehåller [rekvisitionslistehändelser](events.md#b2b-events) för B2B-handlare.
![Nytt](../assets/new.svg) - Lade till `uniqueIdentifier` fält till [sök](events.md#search-events) händelser. I det nya fältet kan handlare korsreferera sökbegäranden och söksvar.

_12 oktober 2022_

![Nytt](../assets/new.svg) - Två har lagts till [storefront-händelser](events.md), `openCart` och `removeFromCart`, till Adobe Commerce Store Events SDK och Collector.
![Nytt](../assets/new.svg) - Stöd för en [AEM](overview.md#aem-support).

+++

## 3.2.0-beta2

_4 mars 2024_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) - Om du deltar i betatestningen bör du kontrollera att `composer.json` filen har följande på rotnivå: ` "minimum-stability": "beta"`.
![Nytt](../assets/new.svg) - Möjlighet att [lägg till anpassade attribut](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![Nytt](../assets/new.svg) - Möjlighet att [samla in och skicka profilposter](connect-data.md#send-customer-profile-data) och data till Experience Platform.

## 3.1.0

_16 november 2023_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

![Nytt](../assets/new.svg) - Experience Platform-anslutningen har bytt namn till [!DNL Data Connection].
![Korrigera](../assets/new.svg) - Möjlighet att logga felsvar har lagts till om Adobe IMS inte kan generera åtkomsttoken.
![Korrigera](../assets/new.svg) - Ett meddelande har lagts till om du försöker synkronisera historiska order men inte har angett kontoautentiseringsuppgifter.

## 3.0.0

_10 oktober 2023_

[!BADGE Kompatibilitet]{type=Informative tooltip="Kompatibilitet"}

Det här är en större version. [Redigera](install.md#update-the-data-connection) projektets rotfil Composer.json.

![Nytt](../assets/new.svg) - Allmän tillgänglighet för [skicka historikorder](connect-data.md#send-historical-order-data) data och status för Experience Platform.
![Nytt](../assets/new.svg) - Stöd för OAuth 2.0 har lagts till när du [konfigurera](connect-data.md#connect-commerce-data-to-adobe-experience-platform) den [!DNL Data Connection] tillägg.
![Nytt](../assets/new.svg) - Stöd för Adobe Commerce 2.4.3 har upphört.

## 2.3.0

_27 juni 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) - Möjlighet att [avaktivera sändning av butikshändelser](connect-data.md#data-collection) till Experience Platform.
![Korrigera](../assets/fix.svg) - Uppdaterade säkerhetsprincipkonfigurationer.
![Korrigera](../assets/fix.svg) - Fast stöd för back office-händelser i Commerce 2.4.7-versionen.
![Nytt](../assets/new.svg) - Ett meddelande om cacheogiltigförklaring har lagts till när du sparar ändringar i [!DNL Data Connection] tilläggsformulär.


## 3.0.0-beta1 (endast internt)

_13 juni 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) - (Beta) Lagt till möjlighet att [skicka historikorder](connect-data.md#beta-send-historical-order-data) data och status för Experience Platform.

## 2.2.0

_30 mars 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) - Paketerad `commerce-data-export` och `saas-export` beroenden med `experience-platform-connector` tillägg. Tidigare var du tvungen att installera dessa beroenden separat. Dessa beroenden, tillsammans med säljkonfiguration, möjliggör bearbetning på serversidan av [back office-händelser](events-backoffice.md).
![Nytt](../assets/new.svg) - En ny back office-händelse har lagts till som kallas [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_28 februari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) - Stöd för PHP 8.2 har lagts till för alla [!DNL Data Connection] tillägg.

## 2.1.0

_17 januari 2023_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) - Uppdaterade [[!DNL Data Connection] tilläggsadministratör](connect-data.md) så att du kan ange en egen AEP Web SDK (legering).
![Korrigera](../assets/fix.svg) Ändrad till att använda `identityMap` i stället för `personID` när du anger den primära identiteten för data som flyttas till kanten.

## 2.0.1

_10 november 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Korrigera](../assets/fix.svg) - Nu ställs Adobe Experience Platform-kontexten in först efter att händelseinsamlaren i Storefront och Storefront Event SDK har lästs in.

## 2.0.0

_12 oktober 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) - Möjlighet att ange egen AEP Web SDK när [koppla](connect-data.md) din Adobe Commerce-instans till Experience Platform.
![Korrigera](../assets/fix.svg) - Uppdaterat datastream-omfångskrav så att dataStream ID:n måste omfång till webbplatsen i stället för att lagras.

## 1.0.0

_9 augusti 2022_

[!BADGE Stöds]{type=Informative tooltip="Stöds"}

![Nytt](../assets/new.svg) - Allmän tillgänglighetsrelease.
