---
title: Uppdatera händelsescheman för tidsserie för Commerce Data Ingessing
description: Lär dig hur du skapar ett schema, en datauppsättning och en datastream för att samla in och skicka händelsedata för tidsserier för dataöverföring i Commerce.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# Uppdatera händelsescheman för tidsserie för Commerce Data Ingessing

En av [introduktionssteg](overview.md#onboarding-steps) för att använda [!DNL Data Connection] tillägget ger åtkomst till arbetsytan för datastream och [skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) som är specifikt för Adobe Commerce. När du skapar den dataströmmen måste du också välja ett schema som beskriver de data som du planerar att importera. Schemat måste innehålla handelsspecifika fältgrupper.

I den här artikeln finns de fältgrupper som schemat måste innehålla för att följande tidsseriedata från Adobe Commerce-händelserna ska kunna samlas in:

- [Beteende](events.md) - Innehåller händelser för butiker, profiler, sökningar och B2B.
- [Back office](events-backoffice.md) - Inkluderar orderstatus och profilhändelser.

Läs mer om [tidsseriedata](data-ingestion.md).

Läs mer om [grunderna för schemakomposition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Uppdatera schema med tidsseriens beteendedata och händelsedata för back office

I det här avsnittet får du lära dig hur du uppdaterar ditt befintliga schema eller skapar ett schema som innehåller beteendedata och händelsedata för back office.

>[!NOTE]
>
>Se [händelsedata för tidsserieprofil](#time-series-profile-event-data) om du vill lära dig hur du lägger till profilspecifika fält.

1. Om du inte redan har ett schema [skapa](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) en med klassen inställd på **Experience Event**.

1. [Lägg till](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) följande handelsspecifika fältgrupper (eller redigera ditt befintliga schema och lägg till dessa fältgrupper):

   - Webbplatssökning
   - Besök webbsidan
   - Användarinloggningsprocess
   - Referensnycklar
   - Kontaktinformation, privat
   - Kanalinformation
   - Handelsinformation
   - Adobe Analytics ExperienceEvent Commerce (om du vill skicka data till Adobe Analytics)

   >[!NOTE]
   >
   > Ange inte några handelsspecifika fältgrupper som `Primary identity`. När du gör det identifieras fältet som obligatoriskt och Experience Platform förväntar sig det fältet i varje händelse. Om det fältet saknas misslyckas dataimporten.

   Ditt schema innehåller nu handelsspecifika fältgrupper så att tidsseriedata som samlats in från Commerce [beteenden](events.md) och [back office](events-backoffice.md) -händelser representeras i schemat.

1. [Aktivera](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) schemat för profilen.

   När ett schema är aktiverat för profilen, deltar alla datauppsättningar som skapats från det här schemat i Real-Time CDP, som sammanfogar data från olika källor för att skapa en fullständig bild av varje kund.

1. [Skapa en datauppsättning](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) baserat på det schema du skapade eller uppdaterade.

   En datauppsättning är en lagrings- och hanteringskonstruktion för en datamängd, vanligtvis en tabell som innehåller ett schema (kolumner) och fält (rader). Datauppsättningar innehåller också metadata som beskriver olika aspekter av de data som lagras.

1. [Skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) och välj det schema som innehåller de handelsspecifika fältgrupperna och motsvarande datamängd.

   Datastream skickar insamlade data till datauppsättningen. Data representeras i datauppsättningen baserat på det valda schemat.

1. **Beta** (Valfritt) Du kan använda anpassade attribut om du vill skicka anpassade Office-händelsedata från din Commerce-instans till Experience Platform. Den här funktionen är i betaversion. Om du vill gå med i betaprogrammet skickar du en förfrågan till [dataconnection@adobe.com](mailto:dataconnection@adobe.com). Ange följande i din begäran:

   - Dina [Adobe organisation-ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Till exempel `organization_id@AdobeOrg`.
   - Lista över anpassade attribut på ordernivå.
   - Lista över attribut på orderartikelnivå.

   Adobe Commerce-teamet kommer att kontakta dig med mer information och nästa steg.

Med scheman, datauppsättningar och datastreams konfigurerade för beteendedata och backoffice-data kan ni [konfigurera](connect-data.md#data-collection) din Commerce-instans för att samla in och skicka data till Experience Platform.

Om du vill inkludera kundens profilinformation kan du gå till nästa avsnitt.

## Händelsedata för tidsserieprofil

>[!NOTE]
>
>Den här funktionen är i betaversion. Om du vill gå med i betaprogrammet skickar du en förfrågan till [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Händelsedata för tidsserieprofil genereras från följande händelser:

- [&quot;accountCreated&quot;](events-backoffice.md#accountcreated)
- [&quot;accountUpdated&quot;](events-backoffice.md#accountupdated)
- [&quot;accountDeleted&quot;](events-backoffice.md#accountdeleted)

Om du vill importera dina kunders profilhändelsedata till Experience Platform kan du uppdatera ditt befintliga Commerce-schema och använda samma dataström som redan konfigurerats, eller skapa ett profilspecifikt dataström och schema. Det beslutet baseras på företagets datastyrning. De följande två avsnitten leder dig genom båda fallen.

### Skicka händelsedata för tidsserieprofiler till Experience Platform med ditt befintliga datastream

Om du vill lägga till tidsserier [data för profilevenemang på serversidan](events-backoffice.md#customer-profile-events-server-side) till din befintliga Commerce-datastream lägger du till `Demographic Details` fältgrupp till ditt schema. Schemat innehåller nu följande handelsspecifika fältgrupper:

- Webbplatssökning
- Besök webbsidan
- Användarinloggningsprocess
- Referensnycklar
- Kontaktinformation, privat
- Kanalinformation
- Handelsinformation
- Adobe Analytics ExperienceEvent Commerce (om du vill skicka data till Adobe Analytics)
- Nytt: **Demografiska detaljer**

Med tillägget `Demographic Details` fältgrupp i ditt befintliga Commerce-schema, används den datauppsättning och det datastream som redan är associerat med ditt Commerce-schema för den här tidsseriens profildata.

### Skicka händelsedata för tidsserieprofiler till Experience Platform i ett separat datastream

Om du vill lägga till [data för profilevenemang på serversidan](events-backoffice.md#customer-profile-events-server-side) till ett nytt profilspecifikt dataflöde och schema utför du följande steg.

1. [Skapa](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) ett schema och ange klassen som **Experience Event**.

1. [Lägg till](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) följande profilspecifika fältgrupper:

   - Demografiska detaljer
   - Kontaktinformation, privat
   - Kanalinformation
   - Handelsinformation

1. [Aktivera](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) schemat för profilen.

   När ett schema är aktiverat för profilen, deltar alla datauppsättningar som skapats från det här schemat i Real-Time CDP, som sammanfogar data från olika källor för att skapa en fullständig bild av varje kund.

1. [Skapa en datauppsättning](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) baserat på det schema som du skapade.

   En datauppsättning är en lagrings- och hanteringskonstruktion för en datamängd, vanligtvis en tabell som innehåller ett schema (kolumner) och fält (rader). Datauppsättningar innehåller också metadata som beskriver olika aspekter av de data som lagras.

1. [Skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) och välj det XDM-schema som innehåller de handelsspecifika fältgrupperna och motsvarande datamängd.

   Datastream skickar insamlade data till datauppsättningen. Data representeras i datauppsättningen baserat på det valda schemat.

Med scheman, datauppsättningar och datastreams konfigurerade för kundprofildata kan ni [konfigurera](connect-data.md#data-collection) din Commerce-instans för att samla in och skicka data till Experience Platform.

Information om hur du skapar ett schema, en datauppsättning och ett datastream för profilpostdata finns i [skicka profilpostdata till Experience Platform](profile-data.md).
