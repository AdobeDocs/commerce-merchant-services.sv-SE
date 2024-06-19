---
title: "[!DNL SaaS Data Export Guide]"
description: "Läs mer om hur du använder [!DNL data export] för Adobe Commerce SaaS-tjänster som synkroniserar data mellan Adobe Commerce och anslutna Commerce-tjänster."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Användarhandbok

[!DNL SaaS data export] förbättrar frontend-prestanda genom att optimera datasynkroniseringen mellan en Adobe Commerce-instans och anslutna Commerce-tjänster. När du lägger till Live Search, Product Recommendations eller Catalog Service i en Adobe Commerce-installation visas [!DNL Data export] tillägg installeras automatiskt.

SaaS-dataexporten samlar in och exporterar olika typer av data, så kallade _feeds_, som sammanställer specifika typer av information. Beroende på vilka Commerce-tjänster som är installerade inkluderar dataexportflödena för SaaS:

- **Katalogentitetsfeeds** sammanställd produktinformation. Data omfattar produkter, produktattribut, produktpriser, produktvariationer, kategorier, kategoribehörigheter och produktbehörigheter.
- The **Omfångsfeed** samlar in data för kundgrupper, webbplatser, butiker och butiksvyer.
- The **Försäljningsorderfeed** lägger samman orderdata inklusive relaterade enheter som fakturor, leveranser, kreditnotor och så vidare.
- The **Multi-Source Inventory feed** aggregerar data om lagerlagerstatusartiklar.

Tillägget för dataexport stöder flera metoder för att initiera och hantera datasynkroniseringsprocessen.

- **Manuell synkronisering från administratören eller kommandoraden**

   - The [Kontrollpanel för datahantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) i Commerce Admin ger en grafisk vy över synkroniseringsstatusen. Du kan använda kontrollpanelen för att utföra en fullständig omsynkronisering (_fullständig synkronisering_) av alla feeds. Adobe rekommenderar dock att du bara utför en fullständig synkronisering första gången du ansluter Adobe Commerce till en Commerce-tjänst. Se [Synkroniseringsprocess](data-synchronization.md).

   - The [Adobe Commerce kommandoradsverktyg](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) innehåller kommandon för att synkronisera specifika flöden och ytterligare alternativ för att anpassa flödeshanteringen.

- **Automatisk synkronisering med kundjobb**

   - [Partiell datasynkronisering](data-synchronization.md#partial-synchronization-with-cron-jobs)—Kronjobb utlöser en partiell datasynkronisering när en Commerce Admin-användare uppdaterar en enhet. Dataexportprocessen skickar endast dessa uppdateringar till anslutna Commerce-tjänster. Den partiella synkroniseringsprocessen baseras på MView-mekanismen och kräver inga åtgärder från Admin-användaren eller systemintegratorn.

   - [Automatiskt återförsök för synkroniseringsfel](data-synchronization.md#failed-items-sync-for-error-recovery)- Kronjobb utlöser automatiskt återförsök av synkroniseringsprocessen när fel uppstår under datasynkroniseringsprocessen.

- **Exportera planering och prestanda**

   - Utvecklare och systemintegratörer kan uppskatta hur lång tid SaaS-dataexporten tar att synkronisera data mellan Adobe Commerce och anslutna tjänster. Den här uppskattningen kan hjälpa till att schemalägga dataexportbearbetning för att förhindra platsavbrott. Se [Beräkna datavolym och överföringstid](estimate-data-volume-sync-time.md).

   - I de fall där synkroniseringen behöver ske snabbare, erbjuder SaaS-dataexport anpassade alternativ för att förbättra exportbearbetningens prestanda. Se [Förbättra prestanda vid dataexport](customize-export-processing.md).

- **Spåra och felsöka dataexportaktiviteter**—Använd data-export- och saas-export-loggar för att granska synkroniseringsstatus och feed-nyttolaster under synkroniserings- och indexeringsprocessen. Se [Loggning och felsökning](troubleshooting-logging.md).



