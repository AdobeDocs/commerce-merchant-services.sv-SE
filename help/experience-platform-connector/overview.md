---
title: Stödlinjeöversikt
description: Lär dig hur du integrerar Adobe Commerce-data med Adobe Experience Platform via Experience Platform-kontakten.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Experience Platform-anslutning - översikt

Experience Platform-anslutningstillägget tillåter Adobe Commerce handlare att skicka [storefront](events.md#storefront-events) och [back office](events.md#back-office-events) data till Adobe Experience Platform så att andra Adobe Experience Cloud-produkter, som Adobe Analytics och Adobe Target, kan använda dessa Commerce-data. Genom att ansluta era Commerce-data till andra produkter i Adobe Experience Cloud kan ni utföra uppgifter, till exempel analysera användarbeteenden på er webbplats, utföra AB-tester och skapa personaliserade kampanjer.

[Storefront-händelser](events.md#storefront-events) fånga kundinteraktioner, som `View Page`, `View Product`, `Add to Cart`och [rekvisitionslista](events.md#b2b-events) information (för B2B-handlare). [Back Office](events.md#back-office-events) händelser samlar in information om status för en beställning, t.ex. om en beställning har placerats, annullerats, återbetalats, skickats eller slutförts. Insamlade data innehåller inte personligt identifierbar information. Alla användaridentifierare, som cookie-ID:n och IP-adresser, är strikt anonymiserade. [Läs mer](https://www.adobe.com/privacy/experience-cloud.html).

Kopplingen Experience Platform visas i Commerce Admin under **System** > Tjänster > **Experience Platform Connector**.

![Administratörsvy för tillägget Experience Platform](assets/epc-adminui.png)

## Förutsättningar {#prereqs}

Om du vill använda Experience Platform-kontakten måste du ha följande:

- Adobe Commerce 2.4.3 eller senare
- Adobe ID och organisations-ID
- [Adobe-klientdatalager (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). ACDL krävs för att samla in data om butikshändelser.
- Tillstånd till andra Adobe DX-produkter

## Inledande steg

1. [Installera](install.md) Experience Platform-kontakten.
1. [Logga in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) till ditt Adobe-konto och [visa för att bekräfta](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) ditt företags-ID. Organisations-ID är det ID som är kopplat till ditt tilldelade Experience Cloud-företag. Detta ID är en 24 tecken lång alfanumerisk sträng, följt av (och måste innehålla) `@AdobeOrg`.
1. [Skapa eller uppdatera](update-xdm.md) XDM-schemat med handelsspecifika fältgrupper.
1. [Skapa en datauppsättning](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) baserat på det schema du skapade eller uppdaterade. Den här datauppsättningen innehåller de Commerce-data som du skickar.
1. [Skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) och välj det XDM-schema som innehåller de handelsspecifika fältgrupperna.
1. [Anslut till Commerce Services](../landing/saas.md).
1. [Anslut till Adobe Experience Platform](connect-data.md).

## Målgrupp

Den här guiden är avsedd för den Adobe Commerce-handlare som vill koppla sina Adobe Commerce-data till andra Adobe DX-produkter.

### Stöd för PWA Studio

Se [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) dokumentation om hur du använder Experience Platform-kontakten i en PWA Studio storefront.

### AEM {#aem-support}

Se [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) dokumentation som visar hur du skickar händelsedata för butiker från en AEM produktsida till Experience Platform med CIF-anslutningen Experience Platform.

Om du behöver information eller har frågor som inte ingår i den här handboken använder du följande resurser:

- [Hjälpcenter](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Supportärenden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Skicka in en biljett för att få ytterligare hjälp.
