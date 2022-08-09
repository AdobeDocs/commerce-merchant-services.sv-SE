---
title: Lägg till fältgrupper i XDM-schema
description: Lär dig hur du lägger till Adobe Commerce-specifika fältgrupper i ett XDM-schema.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Lägg till fältgrupper i XDM-schema

En av [krav](overview.md#prereqs) för att använda Experience Platform-anslutningen är att få åtkomst till arbetsytan för datastream och [skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) som är specifikt för Adobe Commerce. När du skapar den dataströmmen måste du också välja ett XDM-schema som representerar de data som du planerar att importera. Det här avsnittet innehåller fältgrupper som XDM-schemat måste innehålla för att kunna samla in data från Adobe Commerce storefront [händelser](events.md).

1. Om du inte redan har ett XDM-schema [skapa](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) en. I annat fall [redigera](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) ditt befintliga XDM-schema i Adobe Experience Platform-gränssnittet.

1. [Lägg till](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) följande handelsspecifika fältgrupper:

   - Handel
   - Webbplatssökning
   - Besök webbsidan
   - Användarinloggningsprocess
   - Referensnycklar
   - Kontaktinformation, privat
   - Handelsinformation
   - Adobe Analytics Experience event Commerce (om du vill skicka data till Adobe Analytics)
   - Personidentifierare

   >[!NOTE]
   >
   > Ange inte några handelsspecifika fältgrupper som `Primary identity`. När du gör det identifieras fältet som obligatoriskt och Experience Platform förväntar sig det fältet i varje händelse. Om det fältet saknas misslyckas dataimporten.

   Ditt XDM-schema innehåller nu handelsspecifika fältgrupper så att data som samlas in från Commerce Store [händelser](events.md) är representerat i XDM.

1. [Skapa ett datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) och välj det XDM-schema som innehåller de handelsspecifika fältgrupperna.
