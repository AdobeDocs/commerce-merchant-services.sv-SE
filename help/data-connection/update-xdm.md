---
title: Lägg till fältgrupper i XDM-schema
description: Lär dig hur du lägger till Adobe Commerce-specifika fältgrupper i ett XDM-schema.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Lägg till fältgrupper i XDM-schema

En av [introduktionssteg](overview.md#onboarding-steps) för att använda [!DNL Data Connection] tillägget ger åtkomst till arbetsytan för datastream och [skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) som är specifikt för Adobe Commerce. När du skapar den dataströmmen måste du också välja ett XDM-schema som representerar de data som du planerar att importera. Det här avsnittet innehåller fältgrupper som XDM-schemat måste innehålla för att kunna samla in data från Adobe Commerce [händelser](events.md).

1. Om du inte redan har ett XDM-schema [skapa](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) en. I annat fall [redigera](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) ditt befintliga XDM-schema i Adobe Experience Platform-gränssnittet.

1. [Lägg till](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) följande handelsspecifika fältgrupper:

   - Webbplatssökning
   - Besök webbsidan
   - Användarinloggningsprocess
   - Referensnycklar
   - Kontaktinformation, privat
   - Handelsinformation
   - Adobe Analytics ExperienceEvent Commerce (om du vill skicka data till Adobe Analytics)
   - Identitetskarta

   >[!NOTE]
   >
   > Ange inte några handelsspecifika fältgrupper som `Primary identity`. När du gör det identifieras fältet som obligatoriskt och Experience Platform förväntar sig det fältet i varje händelse. Om det fältet saknas misslyckas dataimporten.

   Ditt XDM-schema innehåller nu handelsspecifika fältgrupper så att data som samlas in från Commerce [händelser](events.md) är representerat i XDM.

1. [Skapa en datauppsättning](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) baserat på det schema du skapade eller uppdaterade.

   En datauppsättning är en lagrings- och hanteringskonstruktion för en datamängd, vanligtvis en tabell, som innehåller ett schema (kolumner) och fält (rader). Datauppsättningar innehåller också metadata som beskriver olika aspekter av de data som lagras.

1. [Skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) och välj det XDM-schema som innehåller de handelsspecifika fältgrupperna och motsvarande datamängd.

   Datastream skickar insamlade data till datauppsättningen. Data representeras i datauppsättningen baserat på det valda schemat.