---
title: Anslut handelsdata till Adobe Experience Platform
description: Lär dig hur du ansluter dina Commerce-data till Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Anslut handelsdata till Adobe Experience Platform {#connectaep}

Om du vill ansluta din Adobe Commerce-instans till Adobe Experience Platform måste du ange ett organisations-ID och ett datastream-ID.

![Konfiguration av Experience Platform-anslutning](assets/epc-config.png)

1. Logga in på ditt Adobe-konto på [Commerce Services Connector](../landing/saas.md#organizationid) och välj ditt företags-ID.

1. Gå till Admin **System** > Tjänster > **Experience Platform Connector**.

1. I **Omfång** väljer du butiksvyns kontext eller omfång.

1. I **Organisations-ID** visas det ID som är kopplat till ditt Adobe Experience Platform-konto enligt konfigurationen i [Commerce Services Connector](../landing/saas.md#organizationid). Organisations-ID:t är globalt. Endast ett organisations-ID kan associeras per Adobe Commerce-instans.

1. I **Datastream-ID** fält, klistra in ID:t för det datastream du [skapad](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) i Adobe Experience Platform.

## Relation mellan dataström-ID och butiksgranskning av handelsinstans

DataStream ID möjliggör vidarebefordran av händelser från Adobe Experience Platform till andra Adobe DX-produkter och kan kopplas till en viss butiksvy i din specifika Adobe Commerce-instans. Du kan även koppla flera butiksvyer till samma DataStream ID. Det beror på vad som är bäst för er verksamhet. [Läs mer](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) om vidarebefordran av händelser.

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| Omfång | Specifik butiksvy där du vill att konfigurationsinställningarna ska gälla. |
| Organisations-ID (globalt) | ID som tillhör organisationen som köpte Adobe DX-produkten. Detta ID länkar din Adobe Commerce-instans till Adobe Experience Platform. |
| Dataström-ID (butiksvy) | ID som gör att data kan flöda från Adobe Experience Platform till andra Adobe DX-produkter. Detta ID kan kopplas till en viss butiksvy i din specifika Adobe Commerce-instans. |

Med anslutningstillägget för Experience Platform installerat, länken mellan Adobe Commerce och Adobe Experience Platform och det angivna dataström-ID:t börjar Commerce-data flöda till Adobe Experience Platform och till andra Adobe DX-produkter.

>[!NOTE]
>
> Hur lång tid det tar för data att flöda från kanten till andra Adobe DX-produkter kan variera.

## Handel med data

När Commerce-data skickas till Adobe Experience Platform edge kan du skapa rapporter enligt följande:

![Commerce Data in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce Data in Adobe Experience Manager_
