---
title: Anslut handelsdata till Adobe Experience Platform
description: Lär dig hur du ansluter dina Commerce-data till Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: dead0b8dae69476c196652abd43c4966a38c4141
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Anslut handelsdata till Adobe Experience Platform

När du installerar Experience Platform-anslutningen visas två nya konfigurationssidor i **System** meny under **Tjänster** i handeln _Administratör_.

- Commerce Services Connector
- Experience Platform Connector

Om du vill ansluta din Adobe Commerce-instans till Adobe Experience-plattformen måste du konfigurera båda anslutningarna, med början från Commerce Services-kontakten och sedan med koppling till Experience Platform.

## Uppdatera Commerce Services-kopplingen

Om du tidigare har installerat en Adobe Commerce-tjänst har du förmodligen redan konfigurerat Commerce Services-kopplingen. Annars måste du utföra följande uppgifter på [Commerce Services-koppling](../landing/saas.md) sida:

1. Logga in på ditt Commerce-konto för att [hämta produktions- och sandbox-API-nycklar](../landing/saas.md#credentials).
1. Välj en [SaaS-datautrymme](../landing/saas.md#saas-configuration).
1. Logga in på ditt Adobe-konto för att [hämta ditt organisations-ID](../landing/saas.md#ims-organization-optional).

När du har konfigurerat Commerce Services-kopplingen konfigurerar du Experience Platform-kopplingen.

## Uppdatera Experience Platform-kontakten

I det här avsnittet ansluter du din Adobe Commerce-instans till Adobe Experience Platform med ditt företags-ID. Du kan sedan ange vilken typ av data - butiker eller bakkontor - som ska skickas till Experience Platform.

![Konfiguration av Experience Platform-anslutning](assets/epc-config-dc.png)

## Allmänt

1. Logga in på ditt Adobe-konto på [Commerce Services Connector](../landing/saas.md#organizationid) och välj ditt företags-ID.

   >[!NOTE]
   >
   >Om du redan har konfigurerat Commerce Services-kopplingen kan du hoppa över det här steget eftersom ditt organisations-ID redan har valts.

1. Gå till Admin **System** > Tjänster > **Experience Platform Connector**.

1. I **Omfång** nedrullningsbar meny, ange kontexten som **Webbplats**.

1. I **Organisations-ID** verifiera det ID som är kopplat till ditt Adobe Experience Platform-konto, enligt konfigurationen i [Commerce Services Connector](../landing/saas.md#organizationid). Organisations-ID:t är globalt. Endast ett organisations-ID kan associeras per Adobe Commerce-instans.

1. (Valfritt) Om du redan har en [AEP Web SDK (legering)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) aktivera kryssrutan och lägg till namnet på din AEP Web SDK. Annars lämnar du dessa fält tomma och Experience Platform-anslutningen distribuerar ett åt dig.

   >[!NOTE]
   >
   >Om du anger ditt eget AEP Web SDK använder Experience Platform-kopplingen det datastream-ID som är kopplat till SDK och inte det datastream-ID som är angivet på den här sidan (om det finns något).

## Datainsamling

I **Datainsamling** markerar du de data för butiker och/eller kontor som ska skickas till Experience Platform. För att vara säker på att din Adobe Commerce-instans kan börja datainsamlingen går du igenom [krav](overview.md#prerequisites).

Läs mer om eventämnen [storefront](events.md#storefront-events) och [back office](events.md#back-office-events) händelser.

>[!NOTE]
>
>Alla fält i **Datainsamling** -avsnittet gäller för **Webbplats** omfång eller högre.

1. Välj **Storefront-händelser** om du vill skicka beteendedata för butiken.

   >[!NOTE]
   >
   >The **Storefront-händelser** kryssrutan aktiveras automatiskt om AEP Web SDK och organisations-ID är giltiga.

1. Välj **Back office-händelser** om du vill skicka information om orderstatus, t.ex. om en order har placerats, annullerats, återbetalats eller skickats.

   >[!NOTE]
   >
   >Om du väljer **Back office-händelser**, skickas all backoffice-information till Experience Platform. Om en kund väljer att avanmäla sig från datainsamlingen måste ni uttryckligen ange kundens personuppgiftsinställning i Experience Platform. Detta skiljer sig från butikshändelser där insamlaren redan hanterar samtycke baserat på kundernas önskemål. [Läs mer](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) om att ställa en köpares integritetspolicy i Experience Platform.

1. För att säkerställa att data för back office-händelser uppdateras baserat på ett schema enligt en [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) måste du ändra `Sales Orders Feed` indexera till `Update by Schedule`.

   1. På _Administratör_ sidebar, gå till **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Markera kryssrutan för `Sales Orders Feed` indexerare.

   1. Ange **[!UICONTROL Actions]** till `Update by Schedule`.

   1. Om du aktiverar backoffice-data för första gången kör du följande kommandon för att indexera om och utlösa en omsynkronisering. Efterföljande omsynkronisering sker automatiskt så länge [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) jobbet är korrekt konfigurerat.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

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
| Back Office-händelser | Om det här alternativet är markerat innehåller händelsenyttolasten anonymiserad orderstatusinformation, t.ex. om en order har placerats, annullerats, återbetalats eller levererats. |
| Dataström-ID (webbplats) | ID som gör att data kan flöda från Adobe Experience Platform till andra Adobe DX-produkter. Detta ID måste kopplas till en specifik webbplats i din specifika Adobe Commerce-instans. Om du anger ett eget Experience Platform Web SDK ska du inte ange ett datastream-ID i det här fältet. Experience Platform-kopplingen använder det datastream-ID som är associerat med SDK och ignorerar eventuella datastream-ID som anges i detta fält (om sådana finns). |

## Verifiera att data skickas till Experience Platform

Efter introduktionen börjar butiksdata flöda till Experience Platform. Back office-data tar ca 5 minuter efter introduktionen för att data ska visas i kanten. Efterföljande uppdateringar visas i kanten baserat på kronschemat.

När Commerce-data skickas till Experience Platform kan du skapa rapporter enligt följande:

![Commerce Data in Adobe Experience Platform](assets/aem-data-1.png)
_Commerce Data in Adobe Experience Platform_
