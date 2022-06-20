---
title: Anslut handelsdata till Adobe Experience Platform
description: Lär dig hur du ansluter dina Commerce-data till Adobe Experience Platform.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Anslut handelsdata till Adobe Experience Platform {#connectaep}

Innan du ansluter dina Adobe Commerce-data till Adobe Experience Platform måste du logga in på ditt Adobe-konto på [Commerce Services Connector](../landing/saas.md#organizationid). När du har loggat in och valt ditt organisations-ID kan du sedan ange omfång och datastream-ID på **Experience Platform Connector** i Admin.

1. Gå till Admin **System** > Tjänster > **Experience Platform Connector**.

1. I **Omfång** väljer du butiksvyns kontext eller omfång.

   Organisations-ID:t är globalt. Endast ett organisations-ID kan associeras per Adobe Commerce-instans.

1. I **IMS-organisation** visas det ID som är kopplat till ditt Adobe Experience Platform-konto enligt konfigurationen i [Commerce Services Connector](../landing/saas.md#organizationid).

1. I **Datastream-ID** fält, klistra in ID:t för dataströmmen du [skapad](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) i Adobe Experience Platform.

## Relation mellan dataström-ID och din Commerce Instance Storeview

DataStream ID möjliggör vidarebefordran av händelser från Adobe Experience Platform till andra Adobe DX-produkter och kan kopplas till en viss butik i din specifika Adobe Commerce-instans. Du kan även koppla flera olika butiksgranskningar till samma DataStream ID. Det beror på vad som är bäst för er verksamhet.

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| Omfång | En särskild butiksgranskning där du vill att konfigurationsinställningarna ska gälla. |
| IMS-organisation (global) | ID som tillhör organisationen som köpte Adobe DX-produkten. Detta ID länkar din Adobe Commerce-instans till Adobe Experience Platform. |
| Dataström-ID (Storeview) | ID som gör att data kan flöda från Adobe Experience Platform till andra Adobe DX-produkter. Detta ID kan kopplas till en viss storeView i din specifika Adobe Commerce-instans. |

När anslutningstillägget för Experience Platform är installerat skapas länken mellan Adobe Commerce och Adobe Experience Platform och det angivna dataström-ID:t, [!DNL Commerce] data börjar flöda till Adobe Experience Platform och till andra Adobe DX-produkter.

## Handel med data

När Commerce-data skickas till Adobe Experience Platform edge kan du skapa rapporter enligt följande:

![Commerce Data in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce Data in Adobe Experience Manager_
