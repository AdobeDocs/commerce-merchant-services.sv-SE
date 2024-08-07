---
title: Konfiguration av bakgrundsprocess
description: "Konfigurera scheman för  [!DNL Store Fulfillment] bakgrundsprocesser som används vid synkronisering av data med sluttjänster."
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Konfiguration av bakgrundsprocess

Integreringen av Store Fulfillment använder bakgrundsprocesser och meddelandeköer för optimala prestanda och skalbarhet. Bygg miljöer för dina Adobe Commerce-butiker med [distributionsvariabler](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) som automatiskt startar [meddelandekökörningar](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Bakgrundsprocesser hanteras med Adobe Commerce standardfunktion [Schemalagda aktiviteter](https://docs.magento.com/user-guide/system/cron.html). Dessa processer ansvarar för synkronisering av konfigurationsdata för order och handlares butik med webbtjänster för arkivleveranser.

## Hantera schemalagda aktiviteter för uppfyllelse av butik

Gå till **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]** från administratören.

Granska standardkonfigurationen för Store Fulfillment services. Du kan anpassa de här inställningarna baserat på din orderbearbetningsvolym och resurstillgänglighet.
