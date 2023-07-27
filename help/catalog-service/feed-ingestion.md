---
title: Inmatningstjänst
description: Läs mer om tjänsten Feed Ingestion för Adobe Commerce
source-git-commit: b484429a529acfa95f70c5a55b6a5fcdedc887b3
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Inmatningstjänst

>[!NOTE]
>
>Flödesmatningstjänsten är för närvarande en privat betaversion. Det finns ännu inte tillgängligt för allmänt bruk.

Flödesmatningstjänsten minskar tiden det tar att bearbeta produktändringar (prisuppdateringar, lägga till nya attribut) genom att kringgå Adobe Commerce-instansen och flytta katalogdata från en tredjepartsleverantör av resursplanering (ERP) direkt till Adobe Commerce-tjänster.

Den här tjänsten är avsedd för kunder som lagrar och hanterar sina produktkataloger i ett system som inte är kopplat till Adobe Commerce centrala program.

Kunder som har stora, komplexa kataloger eller kataloger som får regelbundna uppdateringar är bekymrade över att nya data kan ta längre tid än vad som önskas att de visas i livebutiken. Eftersom katalogtjänsten vet vilka data som behövs för att bearbeta uppdateringarna behöver de inte skickas via den centrala Commerce-produkten, utan endast vidarebefordras till katalogtjänsten. Om du tar bort det här mellansteget görs effektivitetsvinster.

## Flöden för foderintag

Beroende på Adobe Commerce konfiguration kan datalagring och dataflöden ta olika vägar.

* I en standardinstans av Adobe Commerce lagras produktkatalogen i kärndatabasen.
* När du använder Adobe Commerce Services kopieras katalogdata från huvuddatabasen till tjänsten och bearbetas och levereras därifrån.
* När katalogdata lagras i ett tredjepartssystem (ERP, MDM, PIM) flödar data genom kärnhandelsprogrammet och sedan till Commerce Services.
* Med tjänsten för matningsintag överförs produktdata direkt från tredjepartssystemet till infrastrukturen för Commerce Services.

![Inmatningstjänst](assets/feed-ingestion.png)

Genom att kringgå centrala Commerce-programmet och flytta data direkt till Commerce Services återspeglas produktuppdateringar i butiken snabbare. Huvudkatalogdata, t.ex. SKU:er, skickas till kärnhandelsprogrammet för separat bearbetning.

## Gå med i betaversionen

Flödet är avsett för

* Medelstora företagskunder med headless-implementeringar
* Kunder med stora, komplexa kataloger
* Kunder som inte använder Adobe Commerce Admin för att hantera katalogdata, i stället använda ett ERP- eller tredjepartssystem för att hantera katalogdata

Om du är intresserad av att delta i betaprogrammet kontaktar du teamet på XXXXX@adobe.com.
