---
title: Förbättra prestanda vid export av SaaS-data
description: "Lär dig hur du kan förbättra SaaS-dataexportprestanda för Commerce Services genom att använda dataexportläge med flera trådar."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Förbättra prestanda vid export av SaaS-data

**Exportläge för flertrådsdata** snabbar upp exportprocessen genom att dela upp feed-data i grupper och bearbeta dem parallellt.

Utvecklare eller systemintegratörer kan förbättra prestanda genom att använda dataexportläget med flera trådar i stället för standardläget med en tråd. I entrådsläge finns det ingen parallellisering av feedbackprocessen. På grund av standardgränserna är dessutom alla klienter begränsade till att endast använda en tråd. I de flesta fall krävs ingen anpassning av konfigurationen.

## Att tänka på vid användning av flertrådsläge

När du arbetar med dataexporttjänster vill du optimera prestanda samtidigt som du ser till att synkroniseringen är korrekt.
Adobe rekommenderar att standardkonfigurationen för datainhämtning används, som vanligtvis uppfyller synkroniseringskraven för Commerce handlare. Det finns dock scenarier där anpassning kan snabba upp bearbetningstiden.

Tänk på följande när du bestämmer dig för om du vill anpassa dataexportkonfigurationen:

- **Inledande synkronisering**-Utvärdera antalet produkter och [uppskatta datavolym och överföringstid](estimate-data-volume-sync-time.md) baserat på standardkonfigurationen. Fråga dig själv: Kan du vänta på den här initiala datasynkroniseringen när du har startat en Commerce-tjänst?

- **Lägga till nya butiksvyer eller webbplatser**-Om du planerar att lägga till butiksvyer eller webbplatser med samma produktantal efter att du har publicerat, kan du beräkna datavolymen och överföringstiden. Kontrollera om synkroniseringstiden är godkänd med standardkonfigurationen eller om flertrådsbearbetning är nödvändig.

- **Vanlig import**-Förutse vanliga importer, till exempel prisuppdateringar eller förändringar av lagerstatus. Utvärdera om uppdateringarna kan tillämpas inom en acceptabel tidsram eller om snabbare bearbetning behövs.

- **Produktvikt**-Ta en titt på om dina produkter är lätta eller tunga. Justera batchstorleken därefter om produktbeskrivningar eller attribut ökar produktstorleken.

Tänk på att noggrann planering, inklusive beräkning av datavolym och synkroniseringstid, ofta kan eliminera behovet av anpassning. Schemalägg foderintag baserat på dessa uppskattningar för att uppnå optimala resultat.

>[!NOTE]
>
>Adobe rekommenderar att man är försiktig när man använder flertrådshantering. Funktionen är en funktion för tidig åtkomst som fortfarande förbättras. Om du konfigurerar flertrådning för snabbare prestanda kan du utlösa säkerhetsutkast för Adobe Commerce Services som ingår för att förhindra felanvändning av systemet vid dataöverföring. Dessa skyddsräcken hindrar även användare från att utlösa synkroniseringsändringar som kan överbelasta systemet. När skyddsräcken aktiveras blockeras förfrågningar och systemet returnerar 429 fel. Om du råkar ut för dessa fel justerar du konfigurationen och skickar in en supportanmälan för att få hjälp.

## Konfigurera multi-threading

Flertrådsläge stöds för alla [synkroniseringsmetoder](data-synchronization.md#synchronization-process)—fullständig synkronisering, partiell synkronisering och objektsynkronisering som misslyckades. Om du vill konfigurera flertrådning anger du antalet trådar och batchstorlek som ska användas under synkroniseringen.

- `threadCount` är antalet trådar som aktiveras för att bearbeta entiteter. Standardvärdet `threadCount` är `1`.
- `batchSize` är antalet enheter som bearbetas i en iteration. Standardvärdet `batchSize` är `100` poster för alla feeds utom prisfeeden. Standardvärdet för prismatningen är `500` poster.

Du kan konfigurera flertrådsteknik som ett tillfälligt alternativ när du kör ett omsynkroniseringskommando eller genom att lägga till flertrådskonfigurationen i Adobe Commerce-programkonfigurationen.

>[!NOTE]
>
>Se till att du justerar SaaS-dataexportens prestanda med den hastighetsgräns som har definierats för en kund på konsumentsidan.

### Konfigurera multi-threading vid körning

När du kör ett fullständigt synkroniseringskommando från kommandoraden anger du flertrådsbearbetning genom att lägga till kommandot `threadCount` och `batchSize` till CLI-kommandot.

```
bin/magento saas:resync --feed=products --threadCount=2 --batchSize=200
```

De alternativ som anges på kommandoraden åsidosätter den dataexportkonfiguration som anges i Adobe Commerce-programmet `config.php` -fil.

### Lägga till flertrådning i Commerce-konfigurationen

Om du vill bearbeta alla dataexportåtgärder med hjälp av multi-threading kan systemintegratörer eller utvecklare ändra antalet trådar och batchstorleken för varje feed i Commerce-programkonfigurationen.

Du kan använda dessa ändringar genom att lägga till anpassade värden i [systemsektion](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/config-reference-configphp#system) av konfigurationsfilen, `app/etc/config.php`.

**Exempel: Konfigurera flertrådning för produkter och priser**

```php
<?php
return [
    'system' => [
        'default' => [
            'commerce_data_export' => [
                'feeds' => [
                    'products' => [
                        'batch_size' => 100,
                        'thread_count' => 2,
                    ],
                    'prices' => [
                        'batch_size' => 400,
                        'thread_count' => 4,
                    ]
                ]
            ],
//   ...
```
