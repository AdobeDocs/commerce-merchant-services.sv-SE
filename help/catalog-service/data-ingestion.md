---
title: Dataöverföringstjänst
description: Läs mer om datainmatningstjänsten för Adobe Commerce
exl-id: bb5aec74-faca-42ec-9fdb-3261677d451e
source-git-commit: a2f933151481cbdd39d66a0dfbd36e6c339ede62
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Dataöverföringstjänst

Med datainmatningstjänsten kan kunder med stora och/eller komplexa kataloger skicka data direkt till Adobe Commerce-tjänster.

Med datainmatningstjänsten kan du minska tiden det tar att bearbeta produktändringar (prisuppdateringar, lägga till nya attribut) genom att kringgå Adobe Commerce-instansen och flytta katalogdata från en tredjepartsleverantör av resursplanering (ERP) direkt till Adobe Commerce-tjänster.

Den här tjänsten är avsedd för kunder som lagrar och hanterar sina produktkataloger i ett system som inte är kopplat till Adobe Commerce centrala program. Det tillhandahålls som ett API, så att kunderna kan integrera det i sina befintliga system, vilket ger ökad flexibilitet i hur det distribueras.

Kunder som har stora, komplexa kataloger eller kataloger som får regelbundna uppdateringar är bekymrade över att nya data kan ta längre tid än vad som önskas att de visas i livebutiken. Eftersom katalogtjänsten vet vilka data som behövs för att bearbeta uppdateringarna behöver de inte skickas via den centrala Commerce-produkten, utan endast vidarebefordras till katalogtjänsten. Om du tar bort det här mellansteget görs effektivitetsvinster.

## Dataöverföringsflöden

Beroende på Adobe Commerce konfiguration kan datalagring och dataflöden ta olika vägar.

* I en standardinstans av Adobe Commerce lagras produktkatalogen i kärndatabasen.
* När du använder Adobe Commerce Services kopieras katalogdata från huvuddatabasen till tjänsten och bearbetas och levereras därifrån.
* När katalogdata lagras i ett tredjepartssystem (ERP, MDM, PIM) flödar data genom kärnhandelsprogrammet och sedan till Commerce Services.
* Med datainmatningstjänsten går produktdata direkt från tredjepartssystemet till infrastrukturen för Commerce Services.

![Dataöverföringstjänst](assets/data-ingestion.png)

Genom att kringgå centrala Commerce-programmet och flytta data direkt till Commerce Services återspeglas produktuppdateringar i butiken snabbare. Huvudkatalogdata, t.ex. SKU:er, skickas till kärnhandelsprogrammet för separat bearbetning.

## API

The [API-dokumentation för datainmatningstjänsten](https://developer.adobe.com/commerce/services/data-ingestion) innehåller information om hur du implementerar tjänsten.
