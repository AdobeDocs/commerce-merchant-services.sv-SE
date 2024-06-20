---
title: Katalogsynkronisering
description: Lär dig hur du exporterar produktdata från [!DNL Commerce] server till [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# Katalogsynkronisering

>[!NOTE]
>
> Kontrollpanelen för katalogsynkronisering är nu Dashboard för datahantering. Den här förbättrade instrumentpanelen har nu stöd för [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md)och [[!DNL Catalog Service]](../catalog-service/overview.md). Kunderna kan hämta Dashboard för datahantering genom att uppdatera till den senaste versionen av någon av dessa tjänster. Läs mer om det i [Instrumentpanel för datahantering](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) dokumentation. Det här avsnittet gäller även för användare som ännu inte har uppgraderat och fortfarande har kontrollpanelen för katalogsynkronisering.

Adobe Commerce använder indexerare för att kompilera katalogdata till tabeller. Processen aktiveras automatiskt av [händelser](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) till exempel en ändring av ett produktpris eller lagernivå.

Katalogsynkroniseringstjänsten flyttar produktdata från en [!DNL Adobe Commerce] -instans till [!DNL Commerce Services] plattformen fortlöpande för att hålla informationen uppdaterad. Till exempel: [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) kräver att den aktuella kataloginformationen returnerar rekommendationer med korrekta namn, priser och tillgänglighet. Använd _Katalogsynkronisering_ kontrollpanel för att observera och hantera synkroniseringsprocessen eller kommandoradsgränssnittet för att aktivera en katalogsynkronisering och indexera om produktdata för användning via [!DNL Commerce Services]. Se [Referens för kommandoradsgränssnitt](../data-export/data-export-cli-commands.md) i _SaaS-dataexport_ Guide.

## Åtkomst till kontrollpanelen för katalogsynkronisering

Om du vill komma åt kontrollpanelen för katalogsynkronisering väljer du **System** > _Dataöverföring_ > **Katalogsynkronisering**.

Med **Katalogsynkronisering** kontrollpanel:

- Visa synkroniseringsstatus (**Pågår**, **Lyckades**, **Misslyckades**)
- Visa det totala antalet synkroniserade produkter
- Sök efter synkroniserade produkter för att visa deras aktuella tillstånd
- Sök i butikskatalog efter namn, SKU, osv.
- Visa synkroniserad produktinformation i JSON för att hjälpa till att diagnostisera en synkroniseringsdiskrepans
- Starta om synkroniseringsprocessen

### Senaste synkronisering

Rapporterar synkroniseringsstatus för:

- **Lyckades** - Visar datum och tid då synkroniseringen slutfördes och antalet produkter som uppdaterades
- **Misslyckades** - Visar datum och tid då synkroniseringsförsöket gjordes
- **Pågår** - Visar datum och tid för den senaste lyckade synkroniseringen

Katalogsynkroniseringsprocessen körs automatiskt varje timme. Om du inte ser förväntade produkter i butiken, eller om produkterna inte återspeglar de senaste ändringarna du gjort, kan du lösa problemet [katalogsynkroniseringsproblem](#resolvesync).

### Synkroniserade produkter

Visar det totala antalet produkter som synkroniseras från din [!DNL Commerce] katalog. Efter den första synkroniseringen bör endast ändrade produkter synkroniseras.

## Synkronisera igen {#resync}

Om du måste initiera en omsynkronisering av katalogen innan den schemalagda timsynkroniseringen inträffar, kan du tvinga fram en omsynkronisering.

>[!NOTE]
>
> Om du tvingar en omsynkronisering utlöses en omsynkronisering av hela produktkatalogen, vilket kan öka belastningen på maskinvaruresurserna.

1. Från _Katalogsynkronisering_ kontrollpanel, välja **Inställningar**.

   The _Inställningar för katalogsynkronisering_ visas.

1. I _Synkronisera om data_ avsnitt, klicka [!UICONTROL Resync].

   [!DNL Commerce] synkroniserar katalogen under nästa schemalagda synkroniseringsfönster. Beroende på storleken på katalogen kan den här åtgärden ta lång tid.

## Synkroniserade katalogprodukter

The **Synkroniserade katalogprodukter** tabellen visar följande information.

| Fält | Beskrivning |
|---|---|
| ID | Unik identifierare för produkten |
| Namn | Produktens butiksnamn |
| Typ | Identifierar produkttypen, till exempel enkel, konfigurerbar eller nedladdningsbar |
| Senast exporterad | Datum när produkten senast exporterades från katalogen |
| Senast ändrad | Datum när produkten senast ändrades i katalogen |
| SKU | Visar produktens lagerställeenhet |
| Pris | Produktpris |
| Synlighet | En produkts synlighetsinställning enligt definitionen i [!DNL Commerce] katalog |

## Lös problem med katalogsynkronisering {#resolvesync}

Se [Loggar och felsökning](../data-export/troubleshooting-logging.md#troubleshooting) i _Exportguide för SaaS-data_.
