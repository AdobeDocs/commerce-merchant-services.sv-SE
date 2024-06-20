---
title: Granska loggar och felsök
description: "Lär dig hur du felsöker [!DNL data export] fel vid export av data och export av saas."
feature: Services
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# Granska loggar och felsök

The [!DNL data export] tillägg innehåller loggar för att spåra datainsamling och synkroniseringsprocesser.

## Loggar

Loggar finns i `var/log` på Commerce programserver.

| loggnamn | filnamn | description |
|-----------------| ----------| -------------|
| SaaS dataexportlogg | `commerce-data-export.log` | Tillhandahåller information om dataexportaktiviteter som entitetshändelser och fullständiga omsynkroniseringsutlösare.  Varje loggpost har en särskild struktur och innehåller information om feed, operation, status, förfluten tid, process-id och anroparen. |
| fellogg för SaaS-dataexport | `data-export-errors.log` | Visar felmeddelanden och stackspårningar för fel som inträffar under datasynkroniseringsprocessen. |
| SaaS-exportlogg | `saas-export.log` | Tillhandahåller information om data som skickas till Commerce SaaS-tjänster. |
| SaaS-exportfellogg | `saas-export-errors.log` | Innehåller information om fel som inträffar när data skickas till Commerce SaaS-tjänster. |

Om du inte ser förväntade data för en Adobe Commerce-tjänst använder du felloggarna för dataexporttillägget för att avgöra var problemet uppstod.

Du kan utöka loggar med ytterligare data för spårning och felsökning. Se [Utökad loggning](#extended-logging).

### Loggformat

Varje loggpost har följande struktur.

```
[<log record datetime>] report.<log level>:
{
   "feed": "<feed name>",
   "operation": "<executed operation>",
   "status": "<status of operation>",
   "elapsed": "<time elaspsed from script run>",
   "pid": "<proccess id who executed `operation`>",
   "caller": "<who called this `operation`>"
} [] []
```

>[!NOTE]
>
>Den JSON-baserade strängen är vacker för bättre läsbarhet.

I följande tabell beskrivs de åtgärdstyper som kan registreras i loggarna.

| Åtgärd | Beskrivning | Exempel på anropare |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| fullständig synkronisering | Fullständig synkronisering samlar in och skickar alla data till SaaS för en given feed. | `bin/magento saas:resync --feed=products` |
| partiell omindexering | Delvis synkronisering samlar in och skickar data till SaaS endast för uppdaterade enheter i en given feed. Den här loggen finns bara om det finns uppdaterade entiteter. | `bin/magento cron:run --group=index` |
| försök igen med misslyckade objekt | Skickar om objekt för en given feed till SaaS om den tidigare synkroniseringsåtgärden misslyckades på grund av ett Commerce-program eller serverfel. Den här loggen finns bara om det finns misslyckade objekt. | `bin/magento cron:run --group=saas_data_exporter`  (en cron-grupp av typen &quot;*_data_exporter&quot;) |
| fullständig synkronisering (äldre) | Fullständig synkronisering för en given feed i äldre exportläge. | `bin/magento saas:resync --feed=categories` |
| partiell omindexering (äldre) | Skickar uppdaterade entiteter till SaaS för en given feed i äldre exportläge. Den här loggen finns bara om det finns uppdaterade entiteter. | `bin/magento cron:run --group=index` |
| partiell synkronisering (äldre) | Skickar uppdaterade entiteter till SaaS för en given feed i äldre exportläge. Den här loggen finns bara om det finns uppdaterade entiteter. | `bin/magento cron:run --group=saas_data_exporter` (en cron-grupp av typen &quot;*_data_exporter&quot;) |


### Exempel på loggning

Under en fullständig omsynkronisering spåras förloppet och loggas var 30:e sekund som standard. Här är ett exempel på en loggpost.

```json
{
   "feed": "prices",
   "operation": "full sync",
   "status": "Progress: 2/5, processed: 200, synced: 100",
   "elapsed": "00:00:00 190 ms",
   "pid": "12824",
   "caller": "bin/magento saas:resync --feed=products"
}
```

I det här exemplet `status` värden ger information om synkroniseringsåtgärden:

- **`"Progress 2/5"`** visar att 2 av 5 iterationer har slutförts. Antalet iterationer beror på antalet exporterade enheter.
- **`"processed: 200"`** visar att 200 objekt har bearbetats.
- **`"synced: 100"`** anger att 100 objekt skickades till SaaS. Det förväntas att `"synced"` är inte lika med `"processed"`. Här är ett exempel:
   - **`"synced" < "processed"`** betyder att flödestabellen inte upptäckte några ändringar i objektet jämfört med den tidigare synkroniserade versionen. Sådana objekt ignoreras under synkroniseringsåtgärden.
   - **`"synced" > "processed"`** samma enhets-ID (till exempel `Product ID`) kan ha flera värden i olika omfång. En produkt kan till exempel tilldelas fem webbplatser. I det här fallet kan du ha&quot;1 bearbetat&quot; objekt och&quot;5 synkroniserade&quot; objekt.

+++ Exempel: Fullständig omsynkroniseringslogg för prisfeed

```
Price feed full resync:

[2024-03-05T21:00:51.754687+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Initialize","elapsed":"383 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.803178+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Creating batch table `catalog_data_exporter_product_prices_index_batches`. Start position: 30515","elapsed":"434 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.851878+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Batch table `catalog_data_exporter_product_prices_index_batches` created. Total Items: 500, batches: ~1","elapsed":"482 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.852548+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"start processing `500` items in `1` threads with `500` batch size","elapsed":"483 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:52.288369+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 0","elapsed":"919 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.994249+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 100","elapsed":"00:00:02 625 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.995168+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Complete","elapsed":"00:00:02 626 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
```

+++

## Visa och felsöka loggar med New Relic

Om du lagrar Adobe Commerce-loggar i New Relic kan du lägga till tolkningsregler för att förbättra läsbarheten och frågeupplevelsen.

1. Logga in på New Relic.

1. Gå till `Logs => Parsing`.

1. Klicka på `Create parsing rule`.

1. Konfigurera tolkningsregeln genom att lägga till följande värden.

   - **Filterloggar baserade på NRQL**

     `filePath LIKE '%commerce-data-export%.log'`

   - **Tolkningsregel**

     `\[%{DATA:timestamp}\] report.%{DATA:logLevel} %{GREEDYDATA:feed:json}`

I det här exemplet läggs en regel till som gör att du kan söka efter New Relic-loggar efter en viss flödestyp, åtgärd o.s.v.

**Exempelfrågesträng**—`feed.feed:"products" and feed.status:"Complete"`

## Utökad loggning

Du kan använda miljövariabler för att utöka loggar med ytterligare data för spårning och felsökning.

### Kontrollera flödets nyttolast

Inkludera flödets nyttolast i SaaS-exportloggen genom att lägga till `EXPORTER_EXTENDED_LOG=1` miljövariabel när du synkroniserar om feeden.

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

När åtgärden har slutförts är flödets nyttolast tillgänglig för granskning i SaaS-exportloggen (`var/.log/saas-export.log`).

### Bevara nyttolast i feed-indexregistret

För dataexporttillägget Commerce SaaS (`magento/module-data-exporter`) 103.3.0 och senare innehåller flöden för omedelbar export endast de minimidata som krävs i indextabellen. I flödena ingår alla katalog- och lagerstatusflöden.

Att bevara nyttolastdata i indextabellen rekommenderas inte i produktionsmiljöer, men det kan vara användbart i en utvecklarmiljö. Inkludera flödets nyttolast i indexet genom att lägga till `PERSIST_EXPORTED_FEED=1` miljövariabel när du synkroniserar om feeden.

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### Kör profileraren för att felsöka långsamma prestanda

Om omindexeringsprocessen för ett specifikt flöde tar en orimlig tid, kör du profileraren för att samla in ytterligare data som kan vara användbara för supportteamet.

Kör profileraren genom att lägga till `EXPORTER_PROFILER=1` miljövariabel när du kör kommandot reindex.

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Profileringsdata lagras i dataexportloggen (`var/log/commerce-data-export.log`) i följande format:

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```



