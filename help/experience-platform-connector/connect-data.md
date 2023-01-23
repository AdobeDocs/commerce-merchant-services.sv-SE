---
title: Anslut handelsdata till Adobe Experience Platform
description: Lär dig hur du ansluter dina Commerce-data till Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 710a18a63c84f0ae0a5aa3b3ad50fdfce0358db6
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Anslut handelsdata till Adobe Experience Platform {#connectaep}

Om du vill ansluta din Adobe Commerce-instans till Adobe Experience Platform måste du ange ett organisations-ID och ett datastream-ID.

![Konfiguration av Experience Platform-anslutning](assets/epc-config-sf.png)

## Allmänt

1. Logga in på ditt Adobe-konto på [Commerce Services Connector](../landing/saas.md#organizationid) och välj ditt företags-ID.

1. Gå till Admin **System** > Tjänster > **Experience Platform Connector**.

1. I **Omfång** nedrullningsbar meny, ange kontexten som **Webbplats**.

1. I **Organisations-ID** visas det ID som är kopplat till ditt Adobe Experience Platform-konto enligt konfigurationen i [Commerce Services Connector](../landing/saas.md#organizationid). Organisations-ID:t är globalt. Endast ett organisations-ID kan associeras per Adobe Commerce-instans.

1. (Valfritt) Om du redan har en [AEP Web SDK (legering)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) aktivera kryssrutan och lägg till namnet på din AEP Web SDK. Annars lämnar du dessa fält tomma och Experience Platform-anslutningen distribuerar ett åt dig.

   >[!NOTE]
   >
   >Om du anger ditt eget AEP Web SDK använder Experience Platform-kopplingen det datastream-ID som är kopplat till SDK och inte det datastream-ID som är angivet på den här sidan (om det finns något).

## Datainsamling

>[!NOTE]
>
>För handlare som redan deltar i vårt betaprogram visas en kryssruta där du kan aktivera back office-händelser. Om du vill delta i betaprogrammet kontaktar du [drios@adobe.com](mailto:drios@adobe.com).

![Konfiguration av Beta Experience Platform-anslutning](assets/epc-config-beta.png)

I **Datainsamling** anger du vilka typer av data som ska samlas in och skickas till Experience Platform. Som standard skickas butikshändelser automatiskt så länge som AEP Web SDK och Organization ID är giltiga. Läs mer om eventämnen [storefront](events.md#storefront-events) och [back office](events.md#beta-order-status-events) händelser.

>[!NOTE]
>
>Alla fält i **Datainsamling** -avsnittet gäller för **Webbplats** omfång eller högre.

1. Välj **Back office-händelser** om du vill skicka information om orderstatus, t.ex. om en order har placerats, annullerats, återbetalats eller skickats.

   >[!NOTE]
   >
   >Som standard skickas all backoffice-information till Experience Platform. Om en kund väljer att avanmäla sig från datainsamlingen måste ni uttryckligen ange kundens personuppgiftsinställning i Experience Platform. Detta skiljer sig från butikshändelser där insamlaren redan hanterar samtycke baserat på kundernas önskemål. [Läs mer](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) om att ställa en köpares integritetspolicy i Experience Platform.

1. (Hoppa över det här steget om du använder din egen AEP Web SDK.) [Skapa](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) ett datastream i Adobe Experience Platform eller välj ett befintligt datastream som du vill använda för samlingen.

1. (Hoppa över det här steget om du använder din egen AEP Web SDK.) I **Datastream-ID** klistra in ID:t för det nya eller befintliga datastream-objektet.

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| Omfång | Den specifika webbplats där du vill att konfigurationsinställningarna ska gälla. |
| Organisations-ID (globalt) | ID som tillhör organisationen som köpte Adobe DX-produkten. Detta ID länkar din Adobe Commerce-instans till Adobe Experience Platform. |
| Är AEP Web SDK redan distribuerad till din webbplats? | Markera den här kryssrutan om du har distribuerat din egen AEP Web SDK till din webbplats |
| AEP Web SDK-namn (globalt) | Om du redan har en Experience Platform Web SDK distribuerad till din plats anger du namnet på SDK i det här fältet. Detta gör att händelsesamlingen Storefront och Storefront Event SDK kan använda din Experience Platform Web SDK i stället för den version som distribueras av Experience Platform-anslutningen. Om du inte har någon Experience Platform Web SDK distribuerad till din webbplats lämnar du det här fältet tomt och Experience Platform-anslutningen distribuerar en åt dig. |
| Storefront-händelser | Är markerat som standard så länge organisations-ID och datastream-ID är giltiga. I butikshändelser samlas anonyma beteendedata in från era kunder när de surfar på er webbplats. |
| Back Office-händelser (beta) | Om det här alternativet är markerat innehåller händelsenyttolasten anonymiserad orderstatusinformation, t.ex. om en order har placerats, annullerats, återbetalats eller levererats. |
| Dataström-ID (webbplats) | ID som gör att data kan flöda från Adobe Experience Platform till andra Adobe DX-produkter. Detta ID måste kopplas till en specifik webbplats i din specifika Adobe Commerce-instans. Om du anger ett eget Experience Platform Web SDK ska du inte ange något datastream-ID i det här fältet. Experience Platform-kopplingen använder det datastream-ID som är associerat med SDK och ignorerar eventuella datastream-ID som anges i detta fält (om sådana finns). |

Med anslutningstillägget för Experience Platform installerat, länken mellan Adobe Commerce och Adobe Experience Platform och det angivna dataström-ID:t börjar Commerce-data flöda till Adobe Experience Platform och till andra Adobe DX-produkter.

>[!NOTE]
>
> Hur lång tid det tar för data att flöda från kanten till andra Adobe DX-produkter kan variera.

## Handel med data

När Commerce-data skickas till Adobe Experience Platform edge kan du skapa rapporter enligt följande:

![Commerce Data in Adobe Experience Manager](assets/aem-data-1.png)
_Commerce Data in Adobe Experience Manager_
