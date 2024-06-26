---
title: Konfiguration av kommandorad
description: Efter installationen kan du konfigurera [!DNL Payment Services] med kommandoradsgränssnittet.
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
feature: Payments, Checkout, Configuration, Integration
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# Konfiguration av kommandorad

Efter installationen [!DNL Payment Services]kan du enkelt konfigurera det från [i hemmet](payments-home.md) eller via kommandoradsgränssnittet.

## Konfigurera dataexport

[!DNL Payment Services] kombinerar orderdata som exporteras från [!DNL Magento Open Source] och [!DNL Adobe Commerce] med aggregerade betalningsdata från betalningsleverantörer för att skapa användbara rapporter. The [!DNL Payment Services] tillägg använder indexerare för att effektivt samla in alla nödvändiga data för rapporterna.

Mer information om data som används i [!DNL Payment Services] rapporter, se [Statusrapport för orderbetalning](order-payment-status.md#data-used-in-the-report).

### Konfigurera kron på [!DNL Magento Open Source]

Om du vill använda en `BY SCHEDULE` indexläge på [!DNL Magento Open Source]måste du konfigurera cron. Se [Konfigurera och kör cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Ange indexerare

Beställningsdata exporteras och sparas i betalningstjänsten, med ett av två indexlägen -`ON SAVE` (standard) eller `BY SCHEDULE` (rekommenderas).

Följande index är för [!DNL Payment Services]:

| Code | Namn | Beskrivning |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Försäljningsorderfeed | Skapar index för orderdata |
| `sales_order_status_data_exporter` | Feed för försäljningsorderstatus | Skapar index för försäljningsorderstatusdata |
| `store_data_exporter` | Lagrar feed | Skapar index för butiksdata |

Om du vill ändra indexläge för alla tre indexerarna kör du:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Om du inte anger några indexerare i kommandot uppdateras alla indexerare till samma värde. Om du vill ändra en specifik indexerare måste du ange den i kommandot.

Mer information om hur du ändrar läget för en indexerare manuellt finns i [Konfigurera indexerare](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} i utvecklardokumentationen. Mer information om hur du ändrar det i Admin finns i [Indexhantering](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} i användarhandboken.

### Indexera om data manuellt

Du kan indexera om data manuellt i stället för att vänta på att det ska hända automatiskt. Se [Indexera om](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Hantera index](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} för mer information.

När `BY SCHEDULE` är inställt spåras ändrade enheter och cron-jobbet uppdaterar indexvärdet för dem baserat på ett angivet schema. Se [Kör cron från kommandoraden](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [Konfigurera och kör cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) för att lära dig hur du manuellt aktiverar indexering med hjälp av cron-jobb.

### Skicka omindexerade data till betalningstjänsten

När data har indexerats skickas de automatiskt till [!DNL Payment Services]. Med det här kommandot kan du även manuellt utlösa processen att skicka indexerade data:

```bash
bin/magento saas:resync --feed [feedName]
```

Använd följande kommandoalternativ:

| Kommando | Beskrivning |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Utför en omindexering av den angivna feeden och skickar den till motsvarande tjänst |
| `bin/magento saas:resync --no-reindex` | Hoppar över indexering och skickar osynkroniserade data från indexen |

The `--feed` kan du ange vilken feed du vill skicka:

| Feed | Beskrivning |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Beställer feed i produktionsläge |
| `paymentServicesOrdersSandbox` | Beställningsfeed i sandlådeläge |
| `paymentServicesOrderStatusesProduction` | Orderstatus i produktionsläge |
| `paymentServicesOrderStatusesSandbox` | Ordna statusvärden i sandlådeläge |
| `paymentServicesStoresProduction` | Lagrar i produktionsläge |
| `paymentServicesStoresSandbox` | Lagrar i sandlådeläge |

Alla data som behövs för rapporterna skickas till [!DNL Payment Services] automatiskt om cron har konfigurerats och installerats. Du kan också manuellt starta processen för att skicka kunddata till [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

Mer information om omindexering och indexering finns i [Hantera indexerare](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) i utvecklardokumentationen.

## Konfigurera L2/L3-bearbetning

[!DNL Payment Services] kan bearbeta data på nivå 2 och nivå 3 från kortbetalningstransaktioner för att ge ytterligare information till handlare.

>[!WARNING]
>
> Integrering med nivå 2 och nivå 3-bearbetning med PayPal är endast tillgängligt för handlare i USA. Se [betalningshantering](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} i PayPal Developer-dokumentationen om du vill ha mer information.

Om du vill använda L2/L3-bearbetningsdata för [!DNL Payment Services]eller om du har några frågor kan du kontakta [!DNL Payment Services] kontoansvarig.

Läs mer om L2- och L3-bearbetning som används i [!DNL Payment Services], se [Bearbetning på nivå 2 och nivå 3](levels-card-payment-transactions.md).
