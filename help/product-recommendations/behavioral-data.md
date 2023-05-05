---
title: Beteendedata
description: Lär dig mer om beteendedata och när du kan börja använda dem.
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Beteendedata

Vissa rekommendationstyper använder beteendedata från era kunder för att utbilda maskininlärningsmodeller för att skapa personaliserade rekommendationer. Andra rekommendationstyper använder bara katalogdata och använder inga beteendedata. Om du snabbt vill börja kan du använda följande rekommendationstyper som bara finns i katalogen:

- `More like this`
- `Visual similarity`

När kan du börja använda rekommendationstyper som använder beteendedata? Det beror på. Detta kallas _Kall start_ problem.

The _Kall start_ problem är ett mått på hur mycket tid en modell behöver träna innan den kan anses vara av hög kvalitet. I produktrekommendationer innebär det att man väntar på att Adobe Sensei ska utbilda sina maskininlärningsmodeller innan rekommendationsenheter distribueras på er webbplats. Ju mer data dessa modeller har, desto mer exakt och användbar är rekommendationerna. Insamlingen av dessa data tar tid och varierar beroende på trafikvolym. Eftersom dessa data endast kan samlas in på en produktionsplats är det bäst för er att driftsätta datainsamlingen där så tidigt som möjligt. Du kan göra det här genom att [installera och konfigurera](install-configure.md) den `magento/production-recommendations` -modul.

I följande tabell visas några allmänna riktlinjer för hur lång tid det tar att samla in tillräckligt med data för varje rekommendationstyp:

| Rekommendationstyp | Utbildningstid | Anteckningar |
|---|---|---|
| Popularitetsbaserad (`Most viewed`, `Most purchased`, `Most added to cart`) | Varierar | Beroende på hur många händelser det rör sig om - vyerna är de vanligaste och därför lär sig snabbare. läggs sedan till i varukorgen, och sedan inköps |
| `Viewed this, viewed that` | Kräver mer utbildning | Produktvyerna är volymmässigt låga |
| `Viewed this, bought that`, `Bought this, bought that` | Kräver mest utbildning | Inköpshändelser är de mest ovanliga händelserna på e-handelsplatsen, särskilt jämfört med produktvisningar |
| `Trending` | Kräver tre dagars data för att fastställa en popularitetsbaslinje | Trendsättning är ett mått på den senaste tiden i en produkts popularitet jämfört med dess egen popularitetsbaslinje. En produkts trendpoäng beräknas med hjälp av en förgrundsuppsättning (färsk popularitet över 24 timmar) och en bakgrundsuppsättning (popularitetsbaslinje över 72 timmar). Om ett objekt har blivit mycket mer populärt de senaste 24 timmarna jämfört med dess popularitet i baslinjen får det ett högt trendresultat. Alla produkter har den här poängen, och de högsta när som helst utgör en uppsättning av de ledande trendprodukterna. |

Andra variabler som kan påverka den tid som krävs för att utbilda:

- Högre trafikvolym bidrar till snabbare inlärning
- Vissa rekommendationstyper tränar snabbare än andra
- Adobe Commerce beräknar om beteendedata var fjärde timme. Recommendations blir exaktare ju längre de används på er webbplats.

För att du ska få hjälp med att visualisera utbildningsförloppet för varje rekommendationstyp finns följande [skapa rekommendation](create.md) sidan visar beredskapsindikatorer.

Data samlas in om produktion och maskininlärningsmodeller har utbildats, men ni kan implementera [återstående uppgifter](implementation-workflow.md) som behövs för att driftsätta rekommendationer i butiken. När du är klar med testningen och konfigurationen av rekommendationerna har maskininlärningsmodellerna samlat in och beräknade tillräckligt med data för att skapa relevanta rekommendationer, så att du kan distribuera rekommendationerna till din butik.

Om det inte finns tillräckligt med trafik (visningar, köpta produkter, trender) för de flesta SKU:er kanske det inte finns tillräckligt med data för att slutföra inlärningsprocessen. Detta kan göra att beredskapsindikatorn i administratören ser ut som om den hade fastnat.
Beredskapsindikatorerna är avsedda att förse handlarna med en annan datapunkt när de väljer vilken typ av rekommendationer som är bäst för deras butik. Siffrorna är en stödlinje som kanske aldrig når 100 %.

## Rekommendationer för säkerhetskopiering {#backuprecs}

Om det inte finns tillräckligt med indata för att tillhandahålla alla begärda rekommendationsobjekt i en enhet ger Adobe Commerce säkerhetskopieringsrekommendationer för att fylla i rekommendationsenheter. Om du till exempel distribuerar `Recommended for you` rekommendationstyp på din hemsida, har en förstagångskund på din webbplats inte genererat tillräckligt många beteendedata för att korrekt rekommendera personaliserade produkter. I det här fallet ytor Adobe Commerce objekt baserat på `Most viewed` rekommendationstyp till den här kunden.

Följande rekommendationstyper återgår till `Most viewed` rekommendationstyp om det inte finns tillräckligt med indata insamlade:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
