---
title: Versionsinformation för [!DNL SaaS Data Export Extension]
description: Den senaste versionsinformationen för  [!DNL Data Export Extension]  för Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 7757cc382e306a6c074a815d5148a4dcd8fff284
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Versionsinformation om [!DNL SaaS Data Export] tillägg

De här versionsinformationen beskriver de senaste versionerna av tillägget [!DNL SaaS data export]. Support ges för den aktuella större versionen. Versionsinformation för äldre versioner finns som referens.

Bland uppdateringarna finns:

![Nya](../assets/new.svg) nya funktioner
![Korrigera ](../assets/fix.svg) Korrigeringar och förbättringar
![Fel](../assets/bug.svg) Kända fel


>[!NOTE]
>
>SaaS-tillägget för dataexport är en samling moduler som installeras automatiskt med Live Search, Product Recommendations och Catalog Service. Du kan kontrollera vilken version som är installerad på datorn med Composer. I vissa fall kanske du vill uppgradera dataexporttillägget på datorn för att kunna hämta korrigeringar eller nya funktioner utan att uppdatera Commerce tjänstversion.

## Aktuell huvudversion

## 103.3.8 Release

![Åtgärda](../assets/fix.svg) Inaktiverade konfigurationsalternativ exporteras inte längre som aktiva alternativ.<!--MDEE-812-->
![ Korrigera ](../assets/fix.svg) Alternativ och värden uppdateras nu för en konfigurerbar produkt när ändringar görs i en underordnad produkt. <!--MDEE-835-->
![ Nytt ](../assets/new.svg) Förbättrade möjligheten att inkludera ytterligare systemattributdata i produktattributsflödet.

## 103.3.7 Utgåva

![Korrigera](../assets/fix.svg) Onödiga beroenden har tagits bort från modulen InventoryDataExporter.
![Åtgärda](../assets/fix.svg) Ändrade obligatoriska versioner för lagermoduler som ingår i modulen CatalogInventoryDataExporter så att de stöder Adobe Commerce version 2.4.4.

## 103.3.6 Utgåva

![Korrigera](../assets/fix.svg) Dödlägen som inträffade under feed-omindexering i flertrådsläge har korrigerats. Frågorna delas nu upp i åtgärderna Infoga och Uppdatera.
![Korrigera](../assets/fix.svg) Optimerade prisfrågan för stora kataloger med många webbplatser.
![Ny](../assets/new.svg) Återförsökslogik har lagts till för att köra misslyckade transaktioner på nytt när tidsgränsen nås.

## 103.3.5 Utgåva

![Korrigera](../assets/fix.svg) Ange beroende för den senaste kompatibla dataexportversionen för SaaS gemensamma modul.

![Åtgärda](../assets/fix.svg) `ScopeConfig`-instansen med `ServiceConfigInterface` om du vill ha stöd för olika tjänstkonfigurationer.

## 103.3.4 Utgåva

![Korrigera](../assets/fix.svg) Förbättra loggningen av dataexport i Commerce SaaS genom att lägga till mer information om omindexeringsprocessen.

## 103.3.3 Release

![Ny](../assets/new.svg) SaaS-dataexport cachelagrar nu EAV-attribut (Entity-Attribute-Value) för attributmetadatafrågan.

![Korrigera](../assets/fix.svg) Ett fel har korrigerats där `InventoryStockStatus`-feeden inte sparades vid återförsök om produkten togs bort.

## 103.3.2 Utgåva

![Korrigera](../assets/fix.svg) Ett problem där fältet `modifiedAt` saknades i borttagna entitetsfeeds har korrigerats.

## 103.3.1 Utgåva

![Åtgärda](../assets/fix.svg) Ett problem som orsakade att ett `Invalid Template File`-meddelande visades under omindexering av produktflöden när Page Builder installerades har åtgärdats.

## 103.3.0-utgåvan

![Nytt](../assets/new.svg) Migrerade tabeller för omedelbar export av feed till den enhetliga strukturen:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Ny](../assets/new.svg) Migrerade katalog- och lagerfeeds till lösningen för omedelbar export.

![Nytt](../assets/new.svg) har bytt namn på direktexport av cron-jobb för feed till `*_feed_resend_failed_items`.

![Ny](../assets/new.svg) har bytt namn på direkt exportfeed och ändringsloggtabeller.

![Åtgärda](../assets/fix.svg) Ange `modified_at`-fält i feed-data endast för feeds som kräver det.

![Åtgärda](../assets/fix.svg) Ändra `productAttributes`-frågan om du bara vill hämta produktattribut.

## 103.2.6 Utgåva

![Korrigera](../assets/fix.svg) Ett problem som gjorde att feeds inte kunde indexeras om när tabeller har ett prefix har åtgärdats.

## 103.2.5 Utgåva

![Korrigera](../assets/fix.svg) Optimerade prisfrågan.

## 103.2.4 Utgåva

![Åtgärda](../assets/fix.svg) Korrigerade felaktig Stock-status som visades för en produkt när Commerce Inventory management är aktiverat.

## 103.2.3 Version

![Korrigera](../assets/fix.svg) Specialpriser på webbplatsnivå har korrigerats.
![Korrigera](../assets/fix.svg) har lagts till för alla feeds som bearbetas.


## 103.2.2 Utgåva

![Korrigera](../assets/fix.svg) Förbättrad batchstrategi för stora kataloger. Batchtabellen är nu ifylld med ett begränsat antal ID:n för att minska minnesanvändningen.

![Korrigera](../assets/fix.svg) Det hårda beroendet för CommerceInventoryDataExporter till MSI-moduler har tagits bort.

![Åtgärda](../assets/fix.svg) Förbättrade `commerce-data-exporter` loggar för att samla in mer information och ordna efter olika exportsteg.

## 103.2.1 Utgåva

- Frisläppt uppdaterad version.

## 103.2.0-utgåvan

- Datasynkronisering med flera trådar har lagts till för produkter och priser.
