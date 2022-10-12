---
title: Anslut handelsdata till Adobe Experience Platform
description: Lär dig hur du ansluter dina Commerce-data till Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Anslut handelsdata till Adobe Experience Platform {#connectaep}

Om du vill ansluta din Adobe Commerce-instans till Adobe Experience Platform måste du ange ett organisations-ID och ett datastream-ID.

![Konfiguration av Experience Platform-anslutning](assets/epc-config.png)

1. Logga in på ditt Adobe-konto på [Commerce Services Connector](../landing/saas.md#organizationid) och välj ditt företags-ID.

1. Gå till Admin **System** > Tjänster > **Experience Platform Connector**.

1. I **Omfång** nedrullningsbar meny, ange kontexten som **Webbplats**.

1. I **Organisations-ID** visas det ID som är kopplat till ditt Adobe Experience Platform-konto enligt konfigurationen i [Commerce Services Connector](../landing/saas.md#organizationid). Organisations-ID:t är globalt. Endast ett organisations-ID kan associeras per Adobe Commerce-instans.

1. I **Datastream-ID** fält, klistra in ID:t för det datastream du [skapad](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) i Adobe Experience Platform.

   >[!NOTE]
   >
   >Datastream-ID:t måste anges på webbplatsnivå eller högre. På den nivån används samma datastream-ID för varje webbplats i hierarkin. Du kan inte ange datastream ID-omfånget på lagringsnivån.

1. (Valfritt) Om du inte har någon AEP Web SDK distribuerad till din plats lämnar du det här fältet tomt och Experience Platform-anslutningen distribuerar en åt dig. I annat fall lägger du till namnet på din AEP Web SDK.

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| Omfång | Den specifika webbplats där du vill att konfigurationsinställningarna ska gälla. |
| Organisations-ID (globalt) | ID som tillhör organisationen som köpte Adobe DX-produkten. Detta ID länkar din Adobe Commerce-instans till Adobe Experience Platform. |
| Dataström-ID (webbplats) | ID som gör att data kan flöda från Adobe Experience Platform till andra Adobe DX-produkter. Detta ID måste kopplas till en specifik webbplats i din specifika Adobe Commerce-instans. |
| AEP Web SDK-namn (globalt) | Om du inte har någon AEP Web SDK distribuerad till din webbplats lämnar du det här fältet tomt och Experience Platform-anslutningen distribuerar ett åt dig. Om du redan har en AEP Web SDK distribuerad till din plats anger du namnet på SDK:n i det här fältet. Detta gör att händelsesamlingen Storefront och Storefront Event SDK kan använda din AEP Web SDK i stället för den version som distribueras av Experience Platform-kopplingen. |

Med anslutningstillägget för Experience Platform installerat, länken mellan Adobe Commerce och Adobe Experience Platform och det angivna dataström-ID:t börjar Commerce-data flöda till Adobe Experience Platform och till andra Adobe DX-produkter.

>[!NOTE]
>
> Hur lång tid det tar för data att flöda från kanten till andra Adobe DX-produkter kan variera.

## Handel med data

När Commerce-data skickas till Adobe Experience Platform edge kan du skapa rapporter enligt följande:

![Commerce Data in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce Data in Adobe Experience Manager_
