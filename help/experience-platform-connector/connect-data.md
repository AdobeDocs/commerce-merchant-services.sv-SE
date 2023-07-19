---
title: Anslut handelsdata till Adobe Experience Platform
description: Lär dig hur du ansluter dina Commerce-data till Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '1952'
ht-degree: 0%

---

# Anslut handelsdata till Adobe Experience Platform

När du installerar Experience Platform-anslutningen visas två nya konfigurationssidor i **System** meny under **Tjänster** i handeln _Administratör_.

- Commerce Services Connector
- Experience Platform Connector

Om du vill ansluta din Adobe Commerce-instans till Adobe Experience Platform måste du konfigurera båda anslutningarna, med början med Commerce Services-kopplingen och sedan med koppling Experience Platform.

## Uppdatera Commerce Services-kopplingen

Om du tidigare har installerat en Adobe Commerce-tjänst har du förmodligen redan konfigurerat Commerce Services-kopplingen. Annars måste du utföra följande uppgifter på [Commerce Services-koppling](../landing/saas.md) sida:

1. Logga in på ditt Commerce-konto för att [hämta produktions- och sandbox-API-nycklar](../landing/saas.md#credentials).
1. Välj en [SaaS-datautrymme](../landing/saas.md#saas-configuration).
1. Logga in på ditt Adobe-konto för att [hämta ditt organisations-ID](../landing/saas.md#ims-organization-optional).

När du har konfigurerat Commerce Services-kopplingen konfigurerar du Experience Platform-kopplingen.

## Uppdatera Experience Platform-kontakten

I det här avsnittet ansluter du din Adobe Commerce-instans till Adobe Experience Platform med ditt företags-ID. Du kan sedan ange vilken typ av data - butiker och bakkontor - som ska skickas till Experience Platform.

![Konfiguration av Experience Platform-anslutning](assets/epc-config-dc.png)

## Allmänt

1. Gå till Admin **System** > Tjänster > **Experience Platform Connector**.

1. På **Inställningar** flik under **Allmänt** verifierar du det ID som är kopplat till ditt Adobe Experience Platform-konto enligt konfigurationen i [Commerce Services Connector](../landing/saas.md#organizationid). Organisations-ID:t är globalt. Endast ett organisations-ID kan associeras per Adobe Commerce-instans.

1. I **Omfång** nedrullningsbar meny, ange kontexten som **Webbplats**.

1. (Valfritt) Om du redan har en [AEP Web SDK (legering)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) aktivera kryssrutan och lägg till namnet på din AEP Web SDK. Annars lämnar du dessa fält tomma och Experience Platform-anslutningen distribuerar ett åt dig.

   >[!NOTE]
   >
   >Om du anger ditt eget AEP Web SDK använder Experience Platform-kopplingen det datastream-ID som är kopplat till SDK och inte det datastream-ID som är angivet på den här sidan (om det finns något).

## Datainsamling

I det här avsnittet anger du vilken typ av data du vill skicka till Experience Platform. Det finns två typer av data: klient- och serversidan.

Data på klientsidan hämtas in i butiken. Detta inkluderar interaktioner med kunderna, som `View Page`, `View Product`, `Add to Cart`och [rekvisitionslista](events.md#b2b-events) information (för B2B-handlare). Data på serversidan, eller backoffice-data, är data som samlas in i Commerce-servrarna. Här finns information om status för en order, t.ex. om en order har placerats, annullerats, återbetalats, skickats eller slutförts.

För att vara säker på att din Adobe Commerce-instans kan börja datainsamlingen går du igenom [krav](overview.md#prerequisites).

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
| Dataström-ID (webbplats) | ID som gör att data kan flöda från Adobe Experience Platform till andra Adobe DX-produkter. Detta ID måste kopplas till en specifik webbplats i din specifika Adobe Commerce-instans. Om du anger ett eget Experience Platform Web SDK ska du inte ange något datastream-ID i det här fältet. Experience Platform-kopplingen använder det datastream-ID som är associerat med SDK och ignorerar eventuella datastream-ID som anges i detta fält (om sådana finns). |

>[!NOTE]
>
>Efter introduktionen börjar butiksdata flöda till Experience Platform. Det tar cirka fem minuter att få information från det bakre kontoret. Efterföljande uppdateringar visas i kanten baserat på kronschemat.

## (Beta) Skicka historiska orderdata

>[!NOTE]
>
>Den här funktionen är endast tillgänglig för betatestare. Du kan gå med i betaversionen genom att skicka ett e-postmeddelande till följande adress: [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Adobe Commerce samlar in upp till fem års historiska orderdata och orderstatus. Ni kan använda Experience Platform-kontakten för att skicka historiska data till Experience Platform för att berika era kundprofiler baserat på tidigare order. Data lagras i en datauppsättning i Experience Platform.

Commerce samlar redan in historiska orderdata, men det finns flera uppgifter som du måste slutföra för att skicka dessa data till Experience Platform. I följande avsnitt får du hjälp med processen.

### Installera betaversion av historisk order

Om du vill aktivera insamling av historiska orderdata för beta måste du uppdatera projektets rot [!DNL Composer] `.json` på följande sätt:

1. Öppna roten `composer.json` fil och sök efter `magento/experience-platform-connector`.

1. I `require` uppdaterar du versionsnumret enligt följande:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0.0-beta1",
      ...
    }
   ```

1. För B2B-handlare uppdaterar du `.json` på följande sätt:

   ```json
   "require": {
     ...
     "magento/experience-platform-connector-b2b": "^2.0.0-beta1"
     ...
   }
   ```

1. **Spara** `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   eller, för B2B-handlare:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

### Konfigurera betaversion av historisk order

För att dina kunders orderhistorik ska kunna skickas till Experience Platform måste du ange autentiseringsuppgifter som länkar din Commerce-instans till Experience Platform. Om du redan har installerat och aktiverat [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) har du redan angett de inloggningsuppgifter som behövs och du kan hoppa över det här steget. Om du inte redan har installerat och aktiverat tillägget Audience Activation utför du följande steg:

>[!NOTE]
>
>I det här avsnittet anger du autentiseringsuppgifter från utvecklarkonsolen. Se till att ditt utvecklarkonsolprojekt har rätt [roller och behörigheter har konfigurerats](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.

1. Expandera **[!UICONTROL Services]** och markera **[!UICONTROL Experience Platform Connector]**.

1. Ange de konfigurationsuppgifter som finns i [utvecklarkonsol](https://developer.adobe.com/console/home).

   ![Administratörskonfiguration för Experience Platform Connector](./assets/epc-admin-config.png){width="700" zoomable="yes"}

   >[!NOTE]
   >
   >För betaversion använder Commerce JSON Web Tokens (JWT)-autentiseringsuppgifter i utvecklarkonsolen. Efter betaversion kommer Commerce att använda OAuth 2.0 i utvecklarkonsolen.

1. Klicka **Spara konfiguration**.

### Konfigurera tjänsten Ordersynkronisering

När du har angett autentiseringsuppgifter för utvecklare kan du konfigurera tjänsten för ordersynkronisering. Ordersynkroniseringstjänsten använder [Message Queue Framework](https://developer.adobe.com/commerce/php/development/components/message-queues/) och RabbitMQ. När du har utfört dessa steg kan orderstatusdata synkroniseras till SaaS, vilket krävs innan det skickas till Experience Platform.

1. [Aktivera](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ.

   >[!NOTE]
   >
   >RabbitMQ har redan konfigurerats för Commerce version 2.4.7 och senare, men du måste aktivera konsumenterna.

1. Aktivera användare av meddelandekö via cron-jobb i `.magento.env.yaml` använda `CRON_CONSUMERS_RUNNER` systemvariabel.

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >Se [dokumentation för driftsättningsvariabler](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) om du vill veta mer om alla tillgängliga konfigurationsalternativ.

När ordersynkroniseringstjänsten är aktiverad kan du sedan ange det historiska datumintervallet för beställningar på anslutningssidan för Experience Platform.

### Ange datumintervall för orderhistorik

I det här avsnittet anger du datumintervallet för de historiska order som du vill skicka till Experience Platform.

![Synkronisera orderhistorik](./assets/order-history.png){width="700" zoomable="yes"}

1. Gå till Admin **System** > Tjänster > **Experience Platform Connector**.

1. Välj **Orderhistorik** -fliken.

1. Under **Synkronisering av orderhistorik**, anger **Datauppsättnings-ID**. Detta ska vara samma datauppsättning som är kopplad till den datastream som du angav i [datainsamling](#data-collection) ovan.

   1. Öppna användargränssnittet i Experience Platform och välj **Datauppsättningar** i den vänstra navigeringen för att öppna **Datauppsättningar** kontrollpanel. Kontrollpanelen visar alla tillgängliga datauppsättningar för din organisation. Information visas för varje datamängd som anges, inklusive namn, schema som datauppsättningen följer och status för den senaste importen.
   1. Öppna den datauppsättning som är associerad med din datastream.
   1. I den högra rutan visas information om datauppsättningen. Kopiera datauppsättnings-ID:t.

   ![Kopiera datauppsättnings-ID](./assets/retrieve-dataset-id.png){width="700" zoomable="yes"}

1. I **Från** och **Till** -fälten anger dataområdet för historikorderdata som du vill skicka. Du kan inte välja ett datumintervall som överskrider fem år.

1. Välj [!UICONTROL Start Sync] för att starta synkroniseringen. Historiska orderdata batchas till data i motsats till butiks- och back office-data som är strömmande data. Det tar ca 45 minuter att få fram gruppdata i Experience Platform.

   >[!NOTE]
   >
   >Om du aktiverar en synkronisering flera gånger i samma eller överlappande tidsintervall för beta, visas dubbletthändelser i datauppsättningen.

## Bekräfta att händelsedata samlas in

Använd [Adobe Experience Platform debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) för att undersöka er Commerce-webbplats. När du har bekräftat att data samlas in kan du verifiera att data för butiks- och back office-händelser visas i kanten genom att köra en fråga som returnerar data från [datauppsättning som du skapade](overview.md#prerequisites).

1. Välj **Frågor** till vänster i Experience Platform och klicka [!UICONTROL Create Query].

   ![Frågeredigeraren](assets/query-editor.png)

1. När Frågeredigeraren öppnas anger du en fråga som markerar data från datauppsättningen.

   ![Skapa fråga](assets/create-query.png)

   Frågan kan till exempel se ut så här:

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. När frågan har körts visas resultaten i **Resultat** -flik, bredvid **Konsol** -fliken. I den här vyn visas frågans tabellutdata.

   ![Frågeredigeraren](assets/query-results.png)

I det här exemplet ser du händelsedata från [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview)och så vidare. I den här vyn kan du verifiera att dina Commerce-data har kommit i framkanten.

Om resultaten inte är vad du förväntar dig kan du öppna datauppsättningen och leta efter misslyckade batchimporter. Läs mer om [felsöka batchimport](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
