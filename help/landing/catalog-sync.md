---
title: Katalogsynkronisering
description: Lär dig hur du exporterar produktdata från [!DNL Commerce] server till [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 6513fd6dce9648407b0878785f5f59f9f39cd5e1
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---


# Katalogsynkronisering

>[!NOTE]
>
> Kontrollpanelen för katalogsynkronisering är nu Dashboard för datahantering. Den här förbättrade instrumentpanelen har nu stöd för [!DNL Product Recommendations], [!DNL Live Search]och [!DNL Catalog Service]. Kunderna kan hämta Dashboard för datahantering genom att uppdatera till den senaste versionen av någon av dessa tjänster. Läs mer om det i [Instrumentpanel för datahantering](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) dokumentation. Det här avsnittet gäller även för användare som ännu inte har uppgraderat och fortfarande har kontrollpanelen för katalogsynkronisering.

Adobe Commerce använder indexerare för att kompilera katalogdata till tabeller. Processen aktiveras automatiskt av [händelser](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) till exempel en ändring av ett produktpris eller lagernivå.

Katalogsynkroniseringstjänsten flyttar produktdata från en [!DNL Adobe Commerce] -instans till [!DNL Commerce Services] plattformen fortlöpande för att hålla informationen uppdaterad. Till exempel: [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) kräver att den aktuella kataloginformationen returnerar rekommendationer med korrekta namn, priser och tillgänglighet. Använd _Katalogsynkronisering_ kontrollpanel för att observera och hantera synkroniseringsprocessen eller [kommandoradsgränssnitt](#resynccmdline) för att aktivera en katalogsynkronisering och indexera om produktdata för konsumtion med [!DNL Commerce Services].

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

Katalogsynkroniseringsprocessen körs genom din cron-process. Om du inte ser förväntade produkter i butiken, eller om produkterna inte återspeglar de senaste ändringarna du gjort, kan du lösa problemet [katalogsynkroniseringsproblem](#resolvesync).

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

När du utlöser en omsynkronisering av data kan det ta upp till en timme innan data uppdateras och återspeglas i gränssnittskomponenter som rekommendationsenheter. Om du fortfarande ser diskrepanser mellan katalogen och data i butiken, eller om katalogsynkroniseringen misslyckades, se följande:

### Datamatchningsavvikelse

1. Visa detaljerad vy för produkten i fråga i sökresultaten.
1. Kopiera JSON-utdata och verifiera att innehållet matchar det du har i [!DNL Commerce] katalog.
1. Om innehållet inte stämmer överens gör du en mindre ändring i produkten i katalogen, till exempel lägger till ett mellanslag eller en punkt.
1. Vänta på omsynkronisering eller [aktivera en manuell omsynkronisering](#resync).

### Synkronisering körs inte

Om synkroniseringen inte körs enligt ett schema eller inget synkroniseras, se det här [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) artikel.

### Synkroniseringen misslyckades

Om katalogsynkroniseringen har statusen **Misslyckades**, skicka [supportbiljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Kommandoradsgränssnitt {#resynccmdline}

The `saas:resync` kommandot är en del av `magento/saas-export` paketet och är tillgängligt direkt från paketet med en av [!DNL Commerce Services] produkter, som [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) eller [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> När en datasynkronisering körs för första gången kör du `productattributes` feed first, följt av `productoverrides`innan du kör `products` mata.

Kommandoalternativ:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

I följande tabell beskrivs `saas:resync` parametrar och beskrivningar.

| Parameter | Beskrivning | Obligatoriskt? |
|---| ---| ---|
| `feed` | Anger vilken entitet som ska synkroniseras om, till exempel `products` | Ja |
| `no-reindex` | Skickar befintliga katalogdata igen till [!DNL Commerce Services] utan omindexering. Om den här parametern inte anges kör kommandot en fullständig omindexering innan data synkroniseras. | Nej |
| `cleanup-feed` | Rensa tabellen för flödesindexerare före en synkronisering. | Nej |

Feed-namnet kan vara något av följande:

- `products`— Produkter i din katalog
- `productattributes`— Produktattribut som `activity`, `gender`, `tops`, `bottoms`och så vidare
- `variants`— Produktvariationer för en konfigurerbar produkt, som färg och storlek
- `prices` — Produktpriser
- `scopesCustomerGroup` — Kundgrupper
- `scopesWebsite` — Webbplatser med butiksvyer
- `categories`— Kategorier i katalogen
- `categoryPermissions` - Behörigheter för varje kategori
- `productoverrides`— Kundspecifika regler för prissättning och katalogsynlighet, t.ex. sådana som baseras på kategoribehörigheter

Beroende på vilket [Commerce Services](../landing/saas.md) är installerade kan du ha olika uppsättningar av feeds tillgängliga för `saas:resync` -kommando.

Du bör inte köra `saas:resync` kommando regelbundet. Du kan behöva köra kommandot manuellt i två scenarier:

- Den inledande synkroniseringen
- The [SaaS-ID för datautrymme](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) ändrades

### Inledande synkronisering

När du utlöser en `saas:resync` från kommandoraden, beroende på katalogstorleken, kan det ta från några minuter till några timmar innan data uppdateras.

För den första synkroniseringen rekommenderar vi att du kör kommandon i följande ordning:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### Felsökning

Om du inte ser förväntade data i [!DNL Commerce Service]kontrollerar du om ett problem uppstod under synkroniseringen från [!DNL Adobe Commerce] -instans till [!DNL Commerce Service] plattform.

Det finns två loggfiler i `var/log/` katalog:

- `commerce-data-export-errors.log` - om ett fel inträffar under _samla_ fas
- `saas-export-errors.log` - om ett fel inträffar under _överför_ fas

#### Kontrollera flödets nyttolast

Det kan vara praktiskt att se den flödesladdning som har skickats till [!DNL Commerce Service]. Detta kan du göra genom att skicka miljövariabeln `EXPORTER_EXTENDED_LOG=1`. The `no-reindex` flagga innebär att endast för närvarande insamlade data skickas.

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

Nyttolasten är tillgänglig i `var/log/saas-export.log`.

#### Bevara nyttolast i feed-indexregistret

Ange från `magento/module-data-exporter:103.0.0` vissa feeds: produktfeed, pris feeds, behåller endast de minimivärden som krävs i indextabellen.

Att bevara nyttolastdata i indextabellen rekommenderas inte i produktionen, men det kan vara användbart i en utvecklarinstans. Detta görs genom att skicka `PERSIST_EXPORTED_FEED=1` miljövariabel:

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### Profilering

Om omindexeringsprocessen för en viss feed tar en orimlig tid, kör du profileraren för att samla in ytterligare data som kan vara användbara för supportteamet. Om du vill göra det skickar du `EXPORTER_PROFILER=1`miljövariabel:

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Profileringsdata lagras i `var/log/commerce-data-export.log` med formatet:

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### Skicka en supportförfrågan

Om du ser fel som inte är relaterade till konfiguration eller tillägg från tredje part skickar du en [supportbiljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) med så mycket information som möjligt.
