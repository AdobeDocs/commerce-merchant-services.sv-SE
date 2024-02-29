---
title: Uppdatera profilpostschema för inmatning av handelsdata
description: Lär dig hur du skapar ett schema, en datauppsättning och en datastream för att samla in och skicka data från Commerce-profilposter till Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Uppdatera profilpostschema för inmatning av handelsdata

När era kunder skapar en profil på er Commerce-webbplats skapas en profilpost och data hämtas. Du måste skapa ett schema och en datauppsättning som är specifik för den profilposten innan du kan strömma profildata till Experience Platform.

1. [Skapa](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) ett schema och ange klassen som **Individuell profil**.

1. [Lägg till](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) följande profilspecifika fältgrupper:

   - identityMap
   - Demografiska detaljer
   - Kontaktinformation, privat
   - Information om användarkonto

1. [Aktivera](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) schemat för profilen.

   När ett schema är aktiverat för profilen, deltar alla datauppsättningar som skapats från det här schemat i Real-Time CDP, som sammanfogar data från olika källor för att skapa en fullständig bild av varje kund.

1. [Skapa en datauppsättning](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) baserat på det schema du skapade eller uppdaterade.

   En datauppsättning är en lagrings- och hanteringskonstruktion för en datamängd, vanligtvis en tabell som innehåller ett schema (kolumner) och fält (rader). Datauppsättningar innehåller också metadata som beskriver olika aspekter av de data som lagras.

Med schemat och datauppsättningen konfigurerade för postdata för kundprofiler kan du [konfigurera](connect-data.md#data-collection) din Commerce-instans för att samla in och skicka data till Experience Platform.

Mer information om hur du skapar ett schema, en datauppsättning och ett datastam för beteendedata och data för back office-händelser finns i [uppdatera tidsseriehändelsescheman för Commerce-datainmatning](update-xdm.md).
