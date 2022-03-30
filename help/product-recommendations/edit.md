---
title: Redigera rekommendation
description: Lär dig hur du redigerar en produktrekommendation.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Redigera rekommendation

På sidan Redigera rekommendation kan du justera de enskilda inställningarna som utgör rekommendationen. Alla inställningar kan redigeras förutom sidtypen och rekommendationstypen. Följande inställningar kan redigeras:

- [Rekommendationsnamn](#name)
- [Etikett för butiken](#label)
- [Antal produkter](#number)
- [Placering och placering](#placement)
- [Filtrera produkter](#filters)

Förhandsgranskningen till höger på sidan visar hur rekommendationen med de aktuella inställningarna kan visas i butiken. The _Förhandsgranskning av rekommenderade produkter_ förblir synlig som referens när du rullar nedåt på sidan. I förhandsgranskningen visas en miniatyrbild av produkten, produktnamn, SKU, pris och resultattyp för varje returnerad produkt. Resultattypen anger om det finns tillräckligt med primära beteendedata för att generera rekommendationen, eller om den använder beteendedata för säkerhetskopiering.

![Redigera Recommendations](assets/edit-recommendation.png)

## Redigera en rekommendation

1. På _Administratör_ sidebar, gå till **Marknadsföring** > _Erbjudanden_ > **Recommendations**.

1. Markera den rekommendation som du vill redigera.

1. Klicka **Redigera**. Följ sedan instruktionerna nedan för att göra de ändringar du behöver.

1. När du är klar klickar du på **Spara ändringar**.

### Rekommendationsnamn {#name}

Välj ett beskrivande namn som anger syftet med rekommendationen. Namnet är för intern referens och visas inte i butiken.

![Redigera namn](assets/edit-name.png)

### Etikett för butiken {#label}

Ange den text som du vill använda som etikett för rekommendationsenheten i butiken.

![Redigera etikett](assets/edit-storefront-label.png)

### Antal produkter {#number}

Justera skjutreglaget för att visa upp till 20 produkter i rekommendationsenheten.

![Redigera antal produkter](assets/edit-number-of-products.png)

### Placering och placering {#placement}

1. Välj den plats på sidan där rekommendationsenheten ska visas i butiken.

   - Längst ned i huvudinnehållet
   - Överst i huvudinnehållet

   ![Redigera placering](assets/edit-placement.png)

1. Använd kommandot **Flytta** ![Flytta väljare](assets/icon-move.png) för att dra rekommendationerna till rätt position.

   ![Redigera position](assets/edit-position.png)

### Filtrera produkter {#filters}

Alla ändringar som gjorts i produkten [filter](filters.md) visas i _Förhandsgranskning av rekommenderade produkter_. Endast produkter som matchar inkluderingsfilter tillåts att rekommenderas. Produkter som matchar eventuella exkluderingsfilter rekommenderas inte.

The _Inkluderingar_ och _Undantag_ -flikarna listar de tillgängliga filtren för varje typ. I listan markeras varje aktivt filter med en blå punkt.

- Om du vill visa information om varje filter klickar du på filternamnet.
- Om du vill ändra filterstatus anger du **Aktivera filter** växla till `on` eller `off` position.

![Redigera filter](assets/edit-filters.png)

Filterinställningarna beskriver de produkter som ska inkluderas eller exkluderas i rekommendationsenheten. Till exempel _Kategori_ Inställningarna för filterinkludering talar om för systemet att endast inkludera produkter från de valda kategorierna.

![Redigera kategorifilter](assets/edit-filter-category.png)
