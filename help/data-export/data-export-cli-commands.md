---
title: Kommandoradsgränssnitt för SaaS-dataexport
description: Lär dig hur du använder kommandoradskommandona för att hantera flöden och processer för [!DNL data export extension] för Adobe Commerce SaaS-tjänster.
recommendations: noCatalog
exl-id: f360d920-7d02-4317-8c56-c7d4c4ed2ff2
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Kommandoradsgränssnittsreferens för SaaS-dataexport

Utvecklare och systemadministratörer kan hantera synkroniseringsåtgärder för SaaS-dataexport med [Adobe Commerce kommandoradsverktyg](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) The `saas:resync` kommandot finns i `magento/saas-export` paket.

Adobe rekommenderar inte att du använder `saas:resync` kommandot regelbundet. Vanliga scenarier för kommandot är:

- Den inledande synkroniseringen
- The [SaaS-ID för datautrymme](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) har ändrats och du måste synkronisera data till det nya datamrådet.
- Felsökning

## Inledande synkronisering

>[!NOTE]
>Om du använder Live Search eller Product Recommendations behöver du inte köra den inledande synkroniseringen. Processen startas automatiskt när du har anslutit tjänsten till din Commerce-instans.

När du utlöser en `saas:resync` från kommandoraden, beroende på katalogstorleken, kan det ta från några minuter till några timmar innan data uppdateras.

För den första synkroniseringen rekommenderar Adobe att du kör kommandona i följande ordning:

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

## Exempel på kommandon

Innan du använder `saas:resync` kommandon, granska [alternativbeskrivningar](#command-options).

- Utför en fullständig omsynkronisering för en entitetsfeed.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Feeds som redan har exporterats synkroniseras inte om.

- Synkronisera om den angivna feeden och rensningsdata fullständigt

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Använd endast efter att ha utfört en [!DNL Data Space ID Cleanup] operation.

- Om du vill exportera feeds skickar du om alla data till anslutna Commerce-tjänster utan att trunkera indexdata i flödestabellen

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Visa tillgängliga kommandon och alternativ med beskrivningar.

  ```
  bin/magento saas:resync --help
  ```

## Kommandoalternativ

Följande alternativ är tillgängliga för att hantera `saas:resync` åtgärder.

>[!NOTE]
>
>The `saas:resync` -kommandot har också stöd för avancerade alternativ för att förbättra kommandon för dataexport genom att öka gruppstorleken och lägga till flertrådsbearbetning. Se [Anpassa exportbearbetning](customize-export-processing.md).

### `feed`

Det här obligatoriska alternativet anger vilken feed-entitet som ska synkroniseras om, till exempel `products`.

The `feed` alternativvärdet kan innehålla någon av de tillgängliga entitetsflödena:

- `products`: produktdatafeed
- `productAttributes`: datafeed för produktattribut
- `categories`: kategoridatafeed
- `variants`: datafeed för konfigurerbara produktvariationer
- `prices`: produktpriser, datafeed
- `categoryPermissions`: data feed för kategoribehörigheter
- `productOverrides`: datafeed för produktbehörigheter
- `inventoryStockStatus`: datafeed för lagerstatus
- `scopesWebsite`: webbplatser med butiker och lagring av dataflöden
- `scopesCustomerGroup`: kundgruppsdatafeed
- `orders`: datafeed för försäljningsorder

Beroende på vilket [Commerce Services](../landing/saas.md) är installerade kan du ha en annan uppsättning feeds tillgängliga för `saas:resync` -kommando.

### `no-reindex`

Det här alternativet skickar om befintliga katalogdata till [!DNL Commerce Services] utan omindexering. Om det här alternativet inte anges kör kommandot en fullständig omindexering innan data synkroniseras.

Hur det här alternativet fungerar beror på om feeden exporteras i [tidigare eller omedelbar exportläge](data-synchronization.md#synchronization-modes)

- För tidigare exportflöden trunkeras inte indexerade data i flödestabellen i synkroniseringsprocessen. I stället skickas alla data vidare till Adobe Commerce-tjänsten.
- För flöden med omedelbar export ignoreras det här alternativet om det anges. För dessa flöden trunkeras inte indexet av den omsynkroniserade processen och endast uppdateringar eller objekt som tidigare misslyckades synkroniseras igen.

### `cleanup`

Med det här alternativet rensas tabellen för flödesindexerare före en synkronisering. När SaaS-dataexporten anges körs en fullständig omsynkronisering för den angivna feeden och alla befintliga data i flödestabellen rensas.

Adobe rekommenderar att du bara använder det här kommandot efter att du har utfört [!DNL Data Space ID Cleanup] operation.

>[!WARNING]
>
>**Använd inte det här alternativet regelbundet**. Det kan orsaka problem med datasynkronisering i Adobe Commerce Services. Till exempel `delete product event` kanske inte kan spridas till Adobe Commerce om `cleanup` används.

## Felsökning

Om du inte ser förväntade data i anslutna Commerce-tjänster felsöker du problemen genom att kontrollera felloggarna för dataexport och använda `saas:resync` med miljövariabler för att granska nyttolaster och profileringsdata. Se [Granska loggar och felsök](troubleshooting-logging.md).
