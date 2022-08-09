---
title: Stödlinjeöversikt
description: Adobe Experience Platform Connector for Adobe Commerce kopplar din Commerce-instans till andra Adobe Experience Cloud-produkter.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Experience Platform-anslutning - översikt

Med Experience Platform-anslutningstillägget kan Adobe Commerce handlare skicka data till Adobe Experience Platform så att andra Adobe Experience Cloud-produkter, som Adobe Analytics och Adobe Target, kan använda dessa Commerce-data. Genom att ansluta era Commerce-data till andra produkter i Adobe Experience Cloud kan ni utföra uppgifter, till exempel analysera användarbeteenden på er webbplats, utföra AB-tester och skapa personaliserade kampanjer.

Händelser i Adobe Storefront fångar upp kundinteraktioner, som `View Page`, `View Product`, `Add to Cart`och så vidare. Insamlade data innehåller inte personligt identifierbar information. Alla användaridentifierare, som cookie-ID:n och IP-adresser, är strikt anonymiserade. [Läs mer](https://www.adobe.com/privacy/experience-cloud.html). Se hela listan med [storefront-händelser](events.md).

## Krav för att använda Experience Platform-anslutningen {#prereqs}

Om du vill använda Experience Platform-kontakten måste du först:

- Fyll i följande [formulär](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) och Adobe ger dig tillgång till dataströmmar och Adobe Experience Platform (om det behövs).

När åtkomst beviljas:

1. [Logga in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) till ditt Adobe-konto.
1. Titta på dina [organisation](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Organisations-ID är det ID som är kopplat till ditt tilldelade Experience Cloud-företag. Detta ID är en 24 tecken lång alfanumerisk sträng, följt av (och måste innehålla) `@AdobeOrg`.
1. Skapa eller uppdatera [XDM-schema](update-xdm.md) med handelsspecifika fältgrupper.
1. [Skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) och välj det XDM-schema som innehåller handelsspecifika **Fältgrupper**.

>[!NOTE]
>
> Organisations-ID och datastream används för att ansluta din Adobe Commerce-instans till Adobe Experience Platform.

## Nästa steg

- Installera [Experience Platform-anslutningstillägg](install.md).

   Tillägget för anslutningsprogrammet Experience Platform installeras från serverns kommandorad och ansluts till din Adobe Commerce-installation som en [service](../landing/saas.md). När processen är klar visas Experience Platform-anslutningen på **System** meny under **Tjänster** i handeln _Administratör_.
- [Ladda upp kundprofiler](profile.md) till Adobe Experience Platform så att butiksdata kan tillskrivas specifika kunder för att förbättra deras shoppingupplevelse.

## Målgrupp

Den här guiden är avsedd för Adobe Commerce-handlare som måste koppla sina Adobe Commerce-butiksdata till andra Adobe DX-produkter.

### Stöd för PWA Studio

Se [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) dokumentation om hur du använder Experience Platform-kontakten i en PWA Studio storefront.

## Kända fel

För närvarande har Experience Platform-kopplingen följande kända problem:

- Sökhändelser stöds inte på Adobe Commerce Enterprise Edition med B2B-modulen installerad.
- Det tar ca en timme att hämta data från Storefront från Adobe Commerce till olika destinationer efter att ha anslutit till Adobe Experience Platform kant.

Om du behöver information eller har frågor som inte ingår i den här handboken använder du följande resurser:

- [Hjälpcenter](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [Supportärenden](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} - Skicka in en biljett för att få ytterligare hjälp.
- På Slack: `#beacon-ama`
