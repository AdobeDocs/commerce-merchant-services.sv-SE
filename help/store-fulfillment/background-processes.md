---
title: Konfiguration av bakgrundsprocess
description: "Konfigurera scheman för  [!DNL Store Fulfillment] bakgrundsprocesser som används vid synkronisering av data med sluttjänster."
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Konfiguration av bakgrundsprocess

Integreringen av Store Fulfillment använder bakgrundsprocesser och meddelandeköer för optimala prestanda och skalbarhet. Bygg miljöer för dina Adobe Commerce-butiker med [distributionsvariabler](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner) som automatiskt startar [meddelandekökörningar](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework).

Bakgrundsprocesser hanteras med Adobe Commerce standardfunktion [Schemalagda aktiviteter](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cron). Dessa processer ansvarar för synkronisering av konfigurationsdata för order och handlares butik med webbtjänster för arkivleveranser.

## Hantera schemalagda aktiviteter för uppfyllelse av butik

Gå till **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]** från administratören.

Granska standardkonfigurationen för Store Fulfillment services. Du kan anpassa de här inställningarna baserat på din orderbearbetningsvolym och resurstillgänglighet.
