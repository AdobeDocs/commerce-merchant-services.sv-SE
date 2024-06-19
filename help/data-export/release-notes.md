---
title: "[!DNL SaaS Data Export Extension] Versionsinformation"
description: Den senaste versionsinformationen för [!DNL Data Export Extension] för Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Versionsinformation om tillägg

I versionsinformationen beskrivs de senaste versionerna av [!DNL SaaS data export] tillägg. Support ges för den aktuella större versionen. Versionsinformation för äldre versioner finns som referens.

Bland uppdateringarna finns:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigera](../assets/fix.svg) Korrigeringar och förbättringar
![Fel](../assets/bug.svg) Kända fel


>[!NOTE]
>
>SaaS-tillägget för dataexport är en samling moduler som installeras automatiskt med Live Search, Product Recommendations och Catalog Service. Du kan kontrollera vilken version som är installerad på datorn med Composer. I vissa fall kanske du vill uppgradera dataexporttillägget på datorn för att kunna hämta korrigeringar eller nya funktioner utan att uppdatera Commerce tjänstversion.

## Aktuell huvudversion

## 103.3.5 Utgåva

![Korrigera](../assets/fix.svg) Ange beroende för den senaste kompatibla dataexportversionen för SaaS gemensamma modul.

![Korrigera](../assets/fix.svg) Ersatt `ScopeConfig` instans med `ServiceConfigInterface` för olika tjänstkonfigurationer.

## 103.3.4 Utgåva

![Korrigera](../assets/fix.svg) Förbättra loggningen av dataexport i Commerce SaaS genom att lägga till mer information om omindexeringsprocessen.

## 103.3.3 Release

![Nytt](../assets/new.svg) SaaS-dataexport cachelagrar nu EAV-attribut (Entity-Attribute-Value) för attributmetadatafrågan.

![Korrigera](../assets/fix.svg) Ett problem där `InventoryStockStatus` feed sparades inte vid återförsök om produkten togs bort.

## 103.3.2 Utgåva

![Korrigera](../assets/fix.svg) Ett problem där `modifiedAt` fältet saknades i borttagna entitetsfeeds.

## 103.3.1 Utgåva

![Korrigera](../assets/fix.svg) Ett problem som orsakade ett `Invalid Template File` meddelande som ska visas vid omindexering av produktflöden när Page Builder är installerat.

## 103.3.0-utgåvan

![Nytt](../assets/new.svg) Migrerade tabeller för omedelbar export av feed till den enhetliga strukturen:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Nytt](../assets/new.svg) Migrerade katalog- och lagerflöden till lösningen för omedelbar export.

![Nytt](../assets/new.svg) Omdöpt direkt export av cron-jobb till `*_feed_resend_failed_items`.

![Nytt](../assets/new.svg) Namnet på direkt exportfeed och loggtabeller har ändrats.

![Korrigera](../assets/fix.svg) Ange `modified_at` fält i feed-data endast för feeds som kräver det.

![Korrigera](../assets/fix.svg) Ändra `productAttributes` fråga om du bara vill hämta produktattribut.

## 103.2.6 Utgåva

![Korrigera](../assets/fix.svg) Korrigerade ett problem som förhindrade att feeds indexerades om när tabeller har ett prefix.

## 103.2.5 Utgåva

![Korrigera](../assets/fix.svg) Optimerade prisfrågan.

## 103.2.4 Utgåva

![Korrigera](../assets/fix.svg) Korrigerat felaktig Stock-status som visas för en produkt när Commerce Inventory management är aktiverat.

## 103.2.3 Version

![Korrigera](../assets/fix.svg) Specialpris på fast webbplatsnivå.
![Korrigera](../assets/fix.svg) Tillagd mutex för alla feeds som bearbetas.


## 103.2.2 Utgåva

![Korrigera](../assets/fix.svg) Förbättrad batchstrategi för stora kataloger. Batchtabellen är nu ifylld med ett begränsat antal ID:n för att minska minnesanvändningen.

![Korrigera](../assets/fix.svg) Eliminerade det hårda beroendet av CommerceInventoryDataExporter till MSI-moduler.

![Korrigera](../assets/fix.svg) Förbättrat `commerce-data-exporter` loggar för att samla in mer information och organisera i olika exportsteg.

## 103.2.1 Utgåva

- Frisläppt uppdaterad version.

## 103.2.0-utgåvan

- Datasynkronisering med flera trådar har lagts till för produkter och priser.

