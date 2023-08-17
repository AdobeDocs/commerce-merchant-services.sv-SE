---
title: Katalogsynkronisering
description: Lär dig hur du exporterar produktdata från [!DNL Commerce] server till [!DNL Commerce Services] fortlöpande för att hålla tjänsterna uppdaterade.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalogs, Data Import/Export, Catalog Service
source-git-commit: d803cd9c78ac8c5529eadf39f361d7e46045359e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Katalogsynkronisering

Adobe Commerce och Magento Open Source använder indexerare för att kompilera katalogdata till tabeller. Processen aktiveras automatiskt av [händelser](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) till exempel en ändring av ett produktpris eller lagernivå.

Katalogsynkroniseringsprocessen körs en timme för att tillåta [!DNL Commerce] tjänster för att använda katalogdata. Katalogsynkronisering exporterar produktdata från [!DNL Commerce] server till [!DNL Commerce] fortlöpande tjänster för att hålla tjänsterna uppdaterade. Till exempel: [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) behöver aktuell kataloginformation för att kunna returnera rekommendationer med korrekta namn, priser och tillgänglighet. Du kan använda _Katalogsynkronisering_ kontrollpanel för att observera och hantera synkroniseringsprocessen eller [kommandoradsgränssnitt](#resynccmdline) för att aktivera katalogsynkronisering och indexera om produktdata för förbrukning med [!DNL Commerce] tjänster.

>[!NOTE]
>
> Använd _Katalogsynkronisering_ kontrollpanelen eller kommandoradsgränssnittet måste du ha ett [API-nyckel och ett konfigurerat SaaS-dataområde](saas.md).

## Åtkomst till kontrollpanelen för katalogsynkronisering

>[!NOTE]
>
> The _Katalogsynkronisering_ instrumentpanelen är bara tillgänglig när _Recommendations_ -moduler installeras och återspeglar dataprognoser som endast avser den funktionen. Stöd för andra Commerce Services som _Live Search_ och _Katalogtjänst_ planeras för framtiden.

Om du vill komma åt kontrollpanelen för katalogsynkronisering väljer du **System** > _Dataöverföring_ > **Katalogsynkronisering**.

Med **Katalogsynkronisering** kontrollpanel:

- Visa synkroniseringsstatus (**Pågår**, **Lyckades**, **Misslyckades**)
- Visa det totala antalet synkroniserade produkter, om det lyckas
- Sök efter synkroniserade produkter för att visa deras aktuella tillstånd
- Sök i butikskatalogen efter namn, SKU och så vidare
- Visa synkroniserad produktinformation i JSON för att hjälpa till att diagnostisera en synkroniseringsdiskrepans
- Starta om synkroniseringsprocessen

### Senaste synkronisering

Rapporterar synkroniseringsstatus för:

- **Lyckades** - Visar datum och tid då synkroniseringen slutfördes och antalet produkter som uppdaterades
- **Misslyckades** - Visar datum och tid då synkroniseringsförsöket gjordes
- **Pågår** - Visar datum och tid för den senaste lyckade synkroniseringen

>[!NOTE]
>
> Katalogsynkroniseringsprocessen körs automatiskt varje timme. Om du inte ser produkter i din butik, eller om produkterna inte återspeglar de senaste ändringarna du gjort, kan du lösa problemet [katalogsynkroniseringsproblem](#resolvesync).

### Synkroniserade produkter

Visar det totala antalet produkter som synkroniseras från din [!DNL Commerce] katalog. Efter den första synkroniseringen bör du bara förvänta dig att ändrade produkter synkroniseras.

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
| Typ | Identifierar produkttypen, t.ex. enkel, konfigurerbar, nedladdningsbar osv. |
| Senast exporterad | Datum när produkten senast exporterades från katalogen |
| Senast ändrad | Datum när produkten senast ändrades i katalogen |
| SKU | Visar produktens lagerställeenhet |
| Pris | Produktpris |
| Synlighet | En produkts synlighetsinställning enligt definitionen i [!DNL Commerce] katalog |

## Lös problem med katalogsynkronisering {#resolvesync}

När du utlöser en omsynkronisering av data kan det ta upp till en timme innan data uppdateras och återspeglas i gränssnittskomponenter, till exempel rekommendationsenheter. Om du efter att ha väntat i en timme fortfarande upptäcker diskrepanser mellan katalogen och vad som visas i butiken, eller om katalogsynkroniseringen misslyckades, se följande:

### Datamatchningsavvikelse

1. Visa detaljerad vy för produkten i fråga i sökresultaten.
1. Kopiera JSON-utdata och verifiera att innehållet matchar det du har i [!DNL Commerce] katalog.
1. Om innehållet inte stämmer överens gör du en mindre ändring i produkten i katalogen, till exempel lägger till ett mellanslag eller en punkt.
1. Vänta på omsynkronisering eller [aktivera en manuell omsynkronisering](#resync).

### Synkronisering körs inte

Om synkroniseringen inte körs enligt ett schema eller om inget synkroniseras, se [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### Synkroniseringen misslyckades

Om katalogsynkroniseringen har statusen **Misslyckades**, skicka [supportbiljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Kommandoradsgränssnitt {#resynccmdline}

The `saas:resync` kommandot är en del av `magento/saas-export` paket. Du kan installera det här paketet med [!DNL Commerce Services] produkter, som [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) eller [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> När du kör en datasynkronisering för första gången är det viktigt att du kör `productattributes` feed first, följt av `productoverrides`innan du kör `products` mata.

Kommandoalternativ:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

I följande tabell beskrivs `saas:resync` parametrar och beskrivningar.

| Parameter | Beskrivning | Obligatoriskt? |
|---| ---| ---|
| `feed` | Anger vilken entitet som ska synkroniseras om, till exempel `products` | Ja |
| `no-reindex` | Skickar befintliga katalogdata igen till [!DNL Commerce Services] utan omindexering. Om den här parametern inte anges kör kommandot en fullständig omindexering innan data synkroniseras. | Nej |

Feed-namnet kan vara något av följande:

- `products`— Produkter i din katalog
- `categories`— Kategorier i katalogen
- `variants`— Produktvariationer för en konfigurerbar produkt, som färg och storlek
- `productattributes`— Produktattribut som `activity`, `gender`, `tops`, `bottoms`och så vidare
- `productoverrides`— Kundspecifika regler för prissättning och katalogsynlighet, t.ex. sådana som baseras på kategoribehörigheter

När du utlöser en omsynkronisering av data från kommandoraden kan det ta upp till en timme innan data uppdateras.

Om du använder [SaaS-prisindexering](../price-index/index.md) och du behöver synkronisera om kör du följande kommando:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### Exempel

I följande exempel omindexeras produktdata från [!DNL Commerce] katalogisera och synkronisera om den till Commerce Services:

```bash
bin/magento saas:resync --feed products
```

Om du inte vill köra ett fullständigt indexvärde för produkterna kan du i stället synkronisera de produktdata som redan har genererats:

```bash
bin/magento saas:resync --feed products --no-reindex
```
