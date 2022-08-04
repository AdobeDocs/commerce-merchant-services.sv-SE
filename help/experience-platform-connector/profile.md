---
title: Överför köpprofiler till Adobe Experience Platform
description: Lär dig hur du överför kundprofiler till Adobe Experience Platform.
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Överför kundprofil till Adobe Experience Platform

Adobe Commerce handlare kan överföra kundprofildata till [Kundprofil i realtid](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html), som ingår i Adobe Experience Platform. Med hjälp av profilen kan ni sammanställa kunddata i en enhetlig vy och erbjuda ett användbart och tidsstämplat konto för varje kundinteraktion.

>[!NOTE]
>
> Profildata måste innehålla en e-postadress, eftersom det är så länken mellan en kund och deras butiksbeteendedata skapas.

När du har överfört kundens profiler skickas händelsedata som är kopplade till eventuella interaktioner som kunderna gör på webbplatsen till en profil via Experience Platform-kontakten och kopplas till kundens profil.

>[!NOTE]
>
> The `createAccount` [storefront-händelse](events.md) skapar inte automatiskt en kundprofil i Profil. Detta begränsas av säkerhetsskäl och är avsiktligt.

I det här avsnittet får du lära dig hur du överför dina Adobe Commerce-kundprofiler till kundprofilen i realtid i Experience Platform.

1. Bestäm var ni lagrar era kunddata. För vissa handlare lagras dessa data i Adobe Commerce och kan [exporterad](https://docs.magento.com/user-guide/system/data-export.html) som en CSV-fil. För andra kan det finnas i ett separat CRM-system (Customer relationship management).

1. När du har bestämt var du ska lagra dina kunddata hittar du [källkoppling](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en) baserat på var era kunddata lagras. Om du inte ser någon lämplig källanslutning använder du [lokal filöverföring](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) koppla samman och importera kundprofiler från en CSV-fil.

   >[!NOTE]
   >
   > Om du använder den lokala filöverföringskopplingen måste du aktivera **Profildatamängd** alternativ när [definiera datauppsättningen](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). Detta identifierar datauppsättningen som profildata.

När du har skapat kundprofilerna i profilen länkas alla butiksdata som är kopplade till den kunden till deras profil.

## Överför profiler ofta

För att få en bättre kundupplevelse bör du importera profildata regelbundet. Vissa källanslutningar tillåter att du importerar profildata enligt ett schema.
