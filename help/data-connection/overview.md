---
title: Översikt över användarhandbok
description: Lär dig integrera Adobe Commerce-data med Adobe Experience Platform med [!DNL Data Connection] tillägg.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 7d93b556881b3af5f6c8bceb5c9bb6af9ec0bc1c
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 0%

---

# [!DNL Data Connection] Introduktion

>[!IMPORTANT]
>
>Experience Platform-anslutningen har bytt namn till [!DNL Data Connection].

The [!DNL Data Connection] -tillägget ansluter din Adobe Commerce-webbinstans till Adobe Experience Platform och Edge Network. Lär dig hur [integrera](./mobile-sdk-epc.md) Adobe Experience Platform Mobile SDK med Commerce.

Din Commerce Store innehåller massor av data. Information om hur era kunder surfar, ser och till slut köper produkterna på er webbplats kan ge möjligheter att skapa en mer personaliserad shoppingupplevelse. Dessa data kan vara till hjälp för interna handelsfunktioner som kundprisregler och dynamiska block, men data ligger kvar på samma plats i din Commerce-instans.

Adobe Experience Platform erbjuder en serie tekniker som när de är uppkopplade med data från din Commerce Store kan distribuera dessa data via Edge Network till andra Adobe DX-produkter för att få insikter om kundens köpbeteende. Med dessa djupgående insikter kan ni skapa en mer personaliserad shoppingupplevelse i alla kanaler.

Följande bild visar hur dina Commerce-data flödar från din butik till andra Adobe DX-produkter:

![Hur data flödar till Experience Platform](assets/commerce-edge.png)

I bilden ovan skickas data från ditt butiks- och back office-kontor till Experience Platform med hjälp av en SDK, API och en källanslutning. Du behöver inte förstå hur dessa delar fungerar när tillägget hanterar komplexiteten i datadelningen för dig. När händelsedata finns i kanten kan du hämta dessa data till andra Experience Platform-program. Exempel:

| Program | Syfte | Användningsexempel |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html) | Profilhantering och segmenteringstjänst | **segmentering av inköpshistorik**: Handlare kan identifiera kunder som köper en artikel baserat på en viss tidsperiod (månatlig, kvartalsvis, årsvis och så vidare). Marknadsförare kan sedan skapa segment för dessa kunder och inrikta dem på kampanjer, kampanjer och som _trattens topp_ data för leads för prenumerationstjänster.<br> **Kategoribaserad segmentering**: Handlare kan se vilken produktkategori de köpt.<br> **Erbjudandebaserad segmentering**: Handlare kan identifiera kunder som konsekvent returnerar produkter. De erbjudanden och rabatter som ges till dem kan nu vara mer intelligenta. Kostnadsfri frakt kan till exempel tas bort för en kund som hela tiden returnerar produkter.<br> **Lookalike-målinriktning**: A _Lookalike Audience_ är en metod som en handlare använder för att nå ut till nya personer som sannolikt är intresserade av sin verksamhet eftersom de har liknande egenskaper som era befintliga kunder. Lookalike-segment kan skapas baserat på beteendedata och transaktionsdata.<br> **Kundbenägenhet**: Förändringar i kundbeteendet kan identifieras som ett resultat av de djupare kundprofiler som kan skapas utifrån transaktionsdata. Förtroendet ökar eftersom fler data flödar i beräkningarna, till exempel produktreturer och produktkonfigurationer.<br> **Korsförsäljning**: En handlare kan identifiera starka möjligheter till korsförsäljning och merförsäljning med hjälp av detaljinformation som hämtats in i Commerce. |
| [Kund [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | Djupanalys av hela Commerce-resan | **Säsongstrender**: En handlare kan identifiera säsongstrender, som hjälper dem att förbereda sig för den periodiska förändringen av efterfrågan på vissa produkter. Handlarna kan också identifiera förändringar i den totala populariteten för alla produkter under flera år.<br> **Konverteringsanalys**: Genom att veta när en produkt har köpts, tillsammans med tillgång till butiksintryckshändelser, kan handlarna generera en omfattande kundprofil för att utföra konverteringsanalys. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | Detaljerad analys av kundbeteende och kampanjresultat | **Orderreturer**: Handlare kan identifiera kunder och större kundsegment som har ett mönster för att returnera produkter. Detta hjälper handlarna att förbättra sin affärsstrategi när de förstår hur kundbasbeteendet ser ut.<br> **Orderadress**: Baserat på leveransadressen kan en handlare förstå om beställningarna görs av kunderna själva eller om det är till en annan person eller enhet.<br> **Säsongstrender**: En handlare kan identifiera säsongstrender, som hjälper dem att förbereda sig för den periodiska förändringen av efterfrågan på vissa produkter. Handlarna kan också identifiera förändringar i den totala populariteten för alla produkter under flera år.<br> **Konverteringsanalys**: Genom att veta när en produkt har köpts, tillsammans med tillgång till butiksintryckshändelser, kan handlarna generera en omfattande kundprofil för att utföra konverteringsanalys. **Anteckning** Adobe Analytics stöder bara beteendehändelsedata (storefront). Adobe Analytics stöder inte transaktionsdata (backoffice). |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | Kampanjsamordning över flera kanaler | **Beteendebaserade resor**: En kund som köpte en mobiltelefon för två år sedan kan inrikta sig på att köpa en ny mobiltelefon eftersom de troligen nu letar efter en ny mobiltelefon. Dessutom kan personaliserade kampanjer och kampanjer användas för att rikta sig till sådana kunder. [!DNL Journey Optimizer] kan använda sin e-post- och SMS-funktionalitet för att nå dessa kunder. Historiska orderdata tillsammans med beteendedata kan användas för att identifiera trender. En kund som har köpt en artikel med en viss konfiguration tidigare och nu funderar på att köpa samma produkt igen kan få en förbättrad köpresa genom att ge dem enkel synlighet/åtkomst till samma produktkonfigurationer.<br> **Personalisering**: Med tillgång till kundprofilinformation [!DNL Journey Optimizer] kan låsa upp mycket personaliserade resor så att handlarna kan nå ut till kunderna via flera olika kanaler.<br> **Ny profil har skapats**: Välkomstmeddelanden och reklamaktiviteter kan uppmuntra och påverka nya kunder på deras shoppingresor.<br> **Profilen har tagits bort**: Handlare kan välja att sluta skicka e-postreklam till kunder som har avslutat sitt konto. Alternativt kan handlarna också skapa kampanjer för att få tillbaka förlorade kunder. |

## Hämta tillbaka data från Experience Platform till Commerce

Skicka dina Commerce-data till Experience Platform med [!DNL Data Connection] tillägg är en del av Commerces funktioner för datadelning. Den andra sidan, som är ett valfritt tillägg, kallas [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). Med det här tillägget kan ni skapa målgrupper i Real-Time CDP och distribuera dessa målgrupper till er Commerce Store för att informera om kundprisregler och dynamiska block.

På en hög nivå ser dataflödet från din Commerce Store till Experience Platform och tillbaka genom Audience Activation-tillägget ut så här:

![[!DNL Data Connection] flöde](assets/data-connection.png)

När du har skapat anslutningen mellan Commerce till Experience Platform och Experience Platform till Commerce fortsätter data att flöda. Du behöver inte återansluta, såvida du inte måste göra det genom en uppgradering.

## Concepts

Att dela data mellan dessa två system kräver att du förstår flera koncept.

* **Data** - De data som delas med Experience Platform samlas in från webbläsarhändelser i din butik och back office-händelser på servern. Händelser i Adobe Storefront hämtas från kundernas interaktioner på webbplatsen och innehåller händelser som [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout)och så vidare. Se [storefront-händelser](events.md#storefront-events) för en fullständig lista över butikshändelser. Händelser på serversidan, eller på backoffice-sidan, inkluderar [orderstatus](events.md#back-office-events) information, som [`orderPlaced`](events.md#orderplaced), [`orderReturned`](events.md#orderitemreturncompleted), [`orderShipped`](events.md#ordershipmentcompleted), [`orderCancelled`](events.md#ordercancelled)och så vidare. Se [back office-händelser](events.md#back-office-events) för en fullständig lista över back office-händelser.

* **Experience Platform och Edge Network** - Datalagret för de flesta Adobe DX-produkter. Data som skickas till Experience Platform sprids sedan till Adobe DX-produkterna via Experience Platform Edge Network. Du kan till exempel starta Journey Optimizer, hämta specifika Commerce-händelsedata från kanten och skapa en övergiven kundvagn i Journey Optimizer. Journey Optimizer kan sedan skicka e-postmeddelandet om det finns övergivna varukorgar i din Commerce Store. Läs mer om [Experience Platform och Edge Network](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **Schema** - Schemat beskriver strukturen för de data som skickas. Innan Experience Platform kan importera dina Commerce-data måste du skapa ett schema som beskriver datastrukturen och anger begränsningar för den typ av data som kan finnas i varje fält. Scheman består av en basklass och noll eller flera schemafältgrupper. Schemat använder XDM-strukturen, som alla Adobe DX-produkter kan läsa. Så när du skickar data till Experience Platform kan du vara säker på att dina data är begripliga för alla DX-produkter. Läs mer om [scheman](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **Datauppsättning** - en lagrings- och hanteringskonstruktion för en datamängd, vanligtvis en tabell som innehåller ett schema (kolumner) och fält (rader). Datauppsättningar innehåller också metadata som beskriver olika aspekter av de data som lagras. Alla data som har importerats till Adobe Experience Platform finns i datauppsättningarna. Läs mer om [datauppsättningar](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Datastream** - ID som gör att data kan flöda från Adobe Experience Platform till andra Adobe DX-produkter. Detta ID måste kopplas till en specifik webbplats i din specifika Adobe Commerce-instans. När du skapar den här dataströmmen anger du XDM-schemat som du skapade ovan. Läs mer om [datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## Stödd arkitektur

The [!DNL Data Connection] finns för följande arkitekturer:

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## Förutsättningar

Använd [!DNL Data Connection] måste du ha följande:

* Adobe Commerce 2.4.4 eller senare
* Adobe ID och organisations-ID
* [Adobe-klientdatalager (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html), som krävs för att samla in data för butikshändelser
* Tillstånd till andra Adobe DX-produkter.

## Onboarding-steg

På en hög nivå kan du [!DNL Data Connection] omfattar följande steg:

1. [Installera](install.md) den [!DNL Data Connection] tillägg.
1. [Logga in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) till ditt Adobe-konto och [bekräfta](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) ditt företags-ID. Organisations-ID är det ID som är kopplat till ditt tilldelade Experience Cloud-företag. Detta ID är en 24 tecken lång alfanumerisk sträng, följt av (och måste innehålla) `@AdobeOrg`.
1. [Skapa eller uppdatera](update-xdm.md) XDM-schemat med handelsspecifika fältgrupper.
1. [Skapa en datauppsättning](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) baserat på det schema du skapade eller uppdaterade. Den här datauppsättningen innehåller de Commerce-data som du skickar.
1. [Skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) och välj det XDM-schema som innehåller de handelsspecifika fältgrupperna.
1. [Anslut till Commerce Services](../landing/saas.md).
1. [Anslut till Adobe Experience Platform](connect-data.md).

I resten av guiden går vi igenom alla dessa steg i detalj så att du kommer igång snabbt och kan börja använda Adobe DX-produkterna i din Commerce Store.

>[!NOTE]
>
>Läs om hur mobilutvecklare [integrera](./mobile-sdk-epc.md) Adobe Experience Platform Mobile SDK med Commerce.

## Målgrupp

Den här guiden är utformad för den Adobe Commerce-handlare som vill berika och personalisera sin Commerce Store för att förbättra shoppingupplevelsen för sina kunder.

## Support

Om du behöver information eller har frågor som inte ingår i den här handboken använder du följande resurser:

* [Hjälpcenter](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [Supportärenden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Skicka in en biljett för att få ytterligare hjälp.
