---
title: SaaS - prisindexering
description: Förbättra prestanda med prisindexering i SaaS
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
source-git-commit: c13e836541c8f04c9621802e482754a483ef0a21
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# SaaS - prisindexering

SaaS prisindexering snabbar upp tiden det tar för prisändringar att återspeglas på en kunds webbplats efter att de har skickats in. Med den här valfria modulen kan handlare med stora, komplexa kataloger, eller med flera webbplatser eller kundgrupper, bearbeta prisändringar snabbare och mer kontinuerligt.

Ledningens största flaskhals: stora datorprocesser som indexering och prisberäkning har flyttats från PHP-kärnan till Adobe Cloud-infrastrukturen. På så sätt kan handlarna snabbt skala upp resurser för att öka prisindexeringstiden och spegla dessa ändringar av webbplatser med mycket snabbare hastighet.

Alla handlare som uppfyller kraven kan dra nytta av dessa förbättringar, men de som kommer att se de största fördelarna är kunder med:

* ständiga prisändringar: Marknadsförare som behöver ändra sina priser upprepade gånger för att uppnå strategiska mål, som frekventa kampanjer, säsongsrabatter eller lagerpålägg.
* Flera webbplatser och/eller kundgrupper: Handlare med delade produktkataloger på flera webbplatser (domäner/varumärken) och/eller kundgrupper.
* Ett stort antal unika priser för olika webbplatser eller kundgrupper: Handlare med omfattande gemensamma produktkataloger som innehåller unika priser på olika webbplatser eller kundgrupper, t.ex. B2B-handlare med förförhandlade priser, varumärken med olika prisstrategier.

Om du har program från tredje part som är beroende av PHP:s huvudprisindexerare läser du dokumentationen och rådfrågar leverantören innan du gör några ändringar.

Prisindexering för SaaS är kostnadsfritt för kunder som använder Adobe Commerce tjänster.

Den här miniguiden beskriver hur prisindexering i SaaS fungerar och hur du aktiverar den.

## Systemkrav

Om du vill använda prisindexering för SaaS behöver du:

* Adobe Commerce 2.4.4+
* Minst en av följande SaaS-tjänster är installerad:

   * [Katalogtjänst](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations](../product-recommendations/guide-overview.md)

## Moduler

Prisindexering för SaaS använder en uppsättning moduler för att tillhandahålla funktioner. Listan med nödvändiga moduler kan vara något annorlunda beroende på butiksinställningarna.

Dessa två moduler lägger till de nya flödena i administratören. Dessa flöden överför data som krävs för prisberäkningar till SaaS-indexeraren och ignorerar PHP:s kärnprisindexerare.

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Kunder som använder Luma och Adobe Commerce Core GraphQL kan installera en modul som är kompatibel med Luma och som inaktiverar PHP:s basprisindexerare:

```
adobe-commerce/catalog-adapter
```

The `catalog-adapter` är endast kompatibelt med 2.4.5. Stöd för 2.4.4 och 2.4.6 kommer inom kort.
PHP:s huvudprisindexerare kan återaktiveras om det behövs av ett tillägg från tredje part eller av någon annan anledning.

## Caveats

Beroende på faktorer som produkttyper, priskomplexitet och katalogstorlek kan prisindexeringen i SaaS vara den rätta lösningen för din butik. Läs mer om följande begränsningar och se om detta är en bra lösning för din webbplats.

För närvarande har prisindexering i SaaS stöd för produkttyperna Simple, Grouped, Virtual, Configurable och Bundle Dynamic.
Stöd för nedladdningsbara produkter, presentkort och paket med fasta produkter kommer snart.

SaaS-prisindexering stöder baspriser:

* Minsta/högsta ordinarie pris
* Minsta/högsta slutpris
* Specialpriser
* Kundgruppspriser
* Priser för katalogregel

När du har valt att använda det nya prisflödet kan du kontakta [Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) för att du ska kunna ångra det.

Nya feeds ska synkroniseras manuellt med `resync` [CLI, kommando](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Annars uppdateras data i standardsynkroniseringsprocessen. Hämta mer information om [Katalogsynkronisering](../landing/catalog-sync.md) -processen.

## Användningsscenarier

### Luma utan tilläggsberoenden

* En Luma- eller Adobe Commerce Core-GraphQL-handlare som har en obligatorisk tjänst installerad (Live Search, Product Recommendations, Catalog Service)
* Inga tillägg från tredje part som är beroende av PHP:s huvudprisindexerare
* Sälja enkla, konfigurerbara, grupperade, virtuella och paketerade dynamiska produkter

1. Aktivera nya flöden.
1. Installera katalogadaptern.

### Luma och Abode Commerce Core GraphQl med PHP Core price indexer-beroenden

* En Luma- eller Adobe Commerce Core-GraphQL-handlare som har en tjänst som stöds installerad (Live Search, Product Recommendations, Catalog Service)
* Med ett tillägg från tredje part som är beroende av PHP:s huvudprisindexerare
* Sälja enkla, konfigurerbara, grupperade, virtuella och paketerade dynamiska produkter

1. Aktivera de nya flödena
1. Installera katalogadaptern.
1. Återaktivera PHP:s huvudprisindexerare.
1. Använd nya feeds och Luma-kompatibilitetskoden i `catalog-adapter` -modul.

### Huvudlös handlare

* En återförsäljare utan huvud som har en tjänst som stöds installerad (Live Search, Product Recommendations, Catalog Service)
* Inget beroende av PHP:s basprisindexerare
* Sälja enkla, konfigurerbara, grupperade, virtuella och paketerade dynamiska produkter

1. Aktivera nya flöden
1. Installera katalogadaptern, vilket inaktiverar PHP-kärnprisindexeraren.

### Luma/Core GraphQL/Headless med produkttyper som inte stöds

* Luma/Headless handlant
* Sälja presentkort, nedladdningsbara eller paketerade produkter

Om det för närvarande inte finns stöd för vissa produkttyper väntar du på fullständigt stöd för dessa.
