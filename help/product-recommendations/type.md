---
title: Rekommendationstyper
description: Lär dig mer om rekommendationer som du kan distribuera till olika sidor på din webbplats.
exl-id: c3b16307-479b-4736-968b-b6ab38233a48
source-git-commit: 42cb709f4699fcdd56df7ca02466ab416f01cab2
workflow-type: tm+mt
source-wordcount: '1575'
ht-degree: 0%

---

# Rekommendationstyper

Adobe Commerce tillhandahåller en stor uppsättning rekommendationer som du kan distribuera till olika sidor på din webbplats. Alla rekommendationstyper är datadrivna. De bygger på beteendedata, produktattributdata och mätvärden. Rekommendationstyperna grupperas enligt följande:

- [Personligt](#personalized)
- [Korsförsäljning och merförsäljning](#crossup)
- [Popularitet](#popularity)
- [Högpresterande](#highperf)

Som en god praxis rekommenderar Adobe följande riktlinjer när du använder rekommendationer:

- Diversifiera dina rekommendationstyper. Kunderna börjar ignorera rekommendationer om de föreslår samma produkter om och om igen.

- Distribuera inte samma rekommendationer till kundvagnssidan och orderbekräftelsesidan. Överväg att använda `Most Added to Cart` för kundvagnssidan och `Bought This, Bought That` för orderbekräftelsesidan.

- Håll sajten aktuell. Distribuera inte fler än tre rekommendationsenheter på samma sida.

- Om din butik säljer kläder, `More like this` Rekommendationen kan föreslå könsspecifika produkter som inte matchar genuset för den produkt som visas. Använd endast den här rekommendationstypen för kategorier som inte är kläder.

## Personligt {#personalized}

Dessa rekommendationstyper rekommenderar produkter som baseras på den specifika kundens beteendehistorik på er webbplats.

| Typ | Beskrivning |
|---|---|
| Rekommenderas för dig | Rekommenderar produkter baserat på varje kunds aktuella och tidigare beteende på plats. Visar ytterst relevanta rekommendationer baserat på kundens webbsurfnings- och inköpshistorik. Den här typen av rekommendationer är effektiv på hemsidan där de flesta shoppare börjar sin resa på en webbplats. För förstagångskunder på er webbplats som inte har genererat någon signal om att personalisera upplevelsen visar Adobe Commerce produkter baserat på den mest visade rekommendationstypen. När kunderna börjar interagera med produkterna på webbplatsen rekommenderar vi dock att produkterna anpassar sig i realtid till deras beteende.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori <br/><br/>**Föreslagna etiketter:**<br/> - Bara för dig<br/>- Rekommenderas för dig<br/>- Inspirerad av dina shoppingtrender |
| Nyligen visade | Visar produkter som kunden senast tittat på, baserat på webbläsarhistorik. Alla borttagna produkter tas bort av rekommendationsenheten. Rekommendationsenheten visas inte om det inte finns någon webbläsarhistorik eller om det inte finns tillräckligt med historik när filterregler tillämpas. Om resultatet innehåller färre produkter än vad som är konfigurerat, visar rekommendationsenheten endast de returnerade produkterna.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/>- Senast visade<br/>- Ta en titt till |

## Korsförsäljning och merförsäljning {#crossup}

Dessa rekommendationstyper är sociala bevis som hjälper kunderna att hitta det andra gillar eller produktdrivna för att hjälpa dem att hitta andra liknande produkter

| Typ | Beskrivning |
|---|---|
| Visade det här, såg du | Rekommenderar produkter som kunderna ser oproportionerligt oftare med den produkt de nu använder.<br/><br/>**Var används:**<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/>- Kunder som tittade på den här produkten fick också se (PDP) |
| En titt på det här, köpte det | Rekommenderar produkter som kunderna tenderar att köpa oproportionerligt oftare efter att ha tittat på den aktuella produkten. Hjälper kunderna att hitta produkter som de kanske inte har lagt märke till på annat sätt.<br/><br/>**Var används:**<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/>- Kunder som tittat på det här ultimata köpet<br/>- Kunder som slutligen köpts<br/>- Vad köper andra efter att ha tittat på den här produkten? |
| Köpte den här, köpte den där | Rekommenderar produkter som kunderna köper oproportionerligt oftare med den produkt de nu använder. Används oftast på korgen eller produktinformationssidan för att öka exponeringen för relaterade korsförsäljningsprodukter för att öka det genomsnittliga ordervärdet. Visar mycket relevanta produkter som kunderna kan lägga till i sina varukorgar genom att summera vad andra kunder har köpt med den aktuella produkten.<br/><br/>**Var används:**<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/>- Få allt du behöver<br/>- Glöm inte de här<br/>- Köps ofta tillsammans |
| Mer som detta | Rekommenderar produkter baserade på liknande metadata som namn, beskrivning, kategoritilldelning och attribut. Genom att utvärdera attributen för de produkter som visas rekommenderar vi liknande produkter i samma kategori. Om en kund till exempel surfar på yogamattor rekommenderas andra produkter i utrustningskategorin. Eftersom den här rekommendationstypen inte särskiljer gendrar rekommenderas inte kläder, mode eller andra könsspecifika vertikaler.<br/><br/>**Var används:**<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/> - Fler produkter som detta<br/>- Liknar detta |
| [Visuell likhet](#visualsim) | Rekommenderar produkter som ser ut ungefär som den produkt som visas. Den här rekommendationstypen är mest användbar om bilder och de visuella aspekterna av produkter är viktiga för shoppingupplevelsen. |

## Popularitet {#popularity}

Rekommendationstyperna rekommenderar produkter som är populäraste eller trendaste inom de senaste sju dagarna.

| Typ | Beskrivning |
|---|---|
| Mest visade | Rekommenderar produkter som har visats mest genom att räkna antalet sessioner där en visningsåtgärd har utförts under de senaste sju dagarna.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/>- Mest populära<br/>- Trender<br/>- Populärt just nu<br/>- Nyligen populärt<br/>- Populära produkter som inspirerats av denna produkt (PDP)<br/>- De viktigaste säljarna |
| Mest köpta | Rekommenderar de produkter som oftast köpts av kunder under de senaste sju dagarna.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/> - Mest populära<br/>- Trender<br/>- Populärt just nu<br/>- Nyligen populärt<br/>- Populära produkter som inspirerats av denna produkt (PDP)<br/>- De viktigaste säljarna |
| Mest tillagt i kundvagn | Rekommenderar produkter som oftast läggs till i varukorgar av shoppare under de senaste sju dagarna. Den här rekommendationstypen kan användas på alla sidor.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/> - Mest populära<br/>- Trender<br/>- Populärt just nu<br/>- Nyligen populärt<br/>- Populära produkter som inspirerats av denna produkt (PDP)<br/>- De viktigaste säljarna |
| Trender | Rekommenderar produkter baserat på den senaste tiden för en produkts popularitet på webbplatsen.<br/><br/>Adobe Sensei samlar ihop information om surfning och inköp på hela er webbplats för att avgöra vilka produkter som är mest populära hos era kunder och rangordna dem. Eftersom Trending analyserar den senaste produktutvecklingen är det en effektiv rekommendationstyp för kataloger med hög omsättning. Om din katalog är mer statisk kanske den inte är lika användbar om inte målgruppens shoppingmönster är mycket varierande.<br/><br/>När Trending används på startsidan rekommenderar vi produkter som nyligen är populära på hela webbplatsen. Trending visar inte produkter som är konsekvent populära, utan de som nyligen har blivit populära. Om du t.ex. har en e-postmarknadsföringskampanj som marknadsför vissa produkter ökar den popularitet som e-postmeddelandet genererar sannolikheten för att de produkter som marknadsförs klassificeras som trender.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/>- Trender<br/>- Trender nu<br/>- Aktuell trender<br/>- Varma produkter<br/>- Trending related products (PDP) |

## Högpresterande {#highperf}

Rekommendationstyperna rekommenderar högpresterande produkter baserat på kriterier för framgång, som tillägg till kundvagnen eller konverteringsgrader.

| Typ | Beskrivning |
|---|---|
| Visa för köpkonvertering | Rekommenderar produkter med den högsta konverteringsgraden mellan visningar och köp. Av alla kundsessioner som registrerade en produktvy, hur stor andel av kunderna till slut registrerade ett köp.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/> -De viktigaste säljarna<br/>- Populära produkter<br/>- Du kanske är intresserad av |
| Konvertering av vy till kundvagn | Rekommenderar produkter med den högsta konverteringsgraden för visning till kundvagn. Av alla kundsessioner som registrerade en produktvy, hur stor andel av kunderna som till slut registrerade ett tillägg i kundvagnen.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/> - De viktigaste säljarna<br/>- Populära produkter<br/>- Du kanske är intresserad av |
| Mest köpta | Den här rekommendationstypen kallas ofta&quot;Top Sellers&quot; och räknar antalet sessioner där en platsbeställningsåtgärd utfördes under de senaste sju dagarna. Den här rekommendationstypen kan användas på alla sidor.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/> - Mest populära<br/>- Trender<br/>- Populärt just nu<br/>- Nyligen populärt<br/>- Populära produkter som inspirerats av denna produkt (PDP)<br/>- De viktigaste säljarna |
| Mest tillagt i kundvagn | Rekommenderar produkter som oftast läggs till i varukorgar av shoppare under de senaste sju dagarna. Den här rekommendationstypen kan användas på alla sidor.<br/><br/>**Var används:**<br/>- Startsida<br/>- Kategori<br/>- Produktinformation<br/>- kundvagn<br/>- Bekräftelse <br/><br/>**Föreslagna etiketter:**<br/> - Mest populära<br/>- Trender<br/>- Populärt just nu<br/>- Nyligen populärt<br/>- Populära produkter som inspirerats av denna produkt (PDP)<br/>- De viktigaste säljarna |

## Visuell likhet {#visualsim}

The _Visuell likhet_ rekommendationstypen rekommenderar produkter som ser ut ungefär som den produkt som visas. Rekommendationstypen är mest användbar när bilder och visuella aspekter av produkterna är viktiga delar av shoppingupplevelsen.

### Så här fungerar det

The _Visuell likhet_ rekommendationstypen ger rekommendationer för andra produkter i katalogen som har en visuell likhet med de bilder som visas just nu. Visuell likhet omfattar aspekter som:

- Färg
- Form
- Storlek
- Textur
- Material
- Stil

Adobe Sensei använder AI för att bearbeta och analysera bilderna i din katalog och skapa attribut som används för att fastställa visuella likheter.

>[!NOTE]
>
> Om du testar den här rekommendationstypen i en icke-produktionsmiljö måste du se till att dina bild-URL:er är tillgängliga för alla.

>[!NOTE]
>
> För närvarande måste produktbilderna vara högst 10 MB stora.

Eftersom den här rekommendationstypen inte kan användas för de flesta kataloger är den inte aktiverad som standard. Du måste uttryckligen aktivera den här rekommendationstypen.

### Aktivera rekommendationstyp för visuell likhet

>[!NOTE]
>
> The _Visuell likhet_ rekommendationstypen är tillgänglig när du [installera](install-configure.md) som en valfri modul.

1. På _Administratör_ sidebar, gå till **Marknadsföring** > _Erbjudanden_ > **Recommendations** för att visa _Recommendations_ kontrollpanel.

1. Klicka **Inställningar** (kugghjulsikon) för att visa _Inställningar_ sida.

1. I _Visual Recommendations_ avsnitt, välja att **Aktivera Visual Recommendations**.

1. Klicka **Spara ändringar** när du är klar.

   The [Skapa ny rekommendation](create.md) sidan visas nu **Visuell likhet** som en valbar rekommendationstyp när sidtypen är **Produktinformation**.

När du har aktiverat visuella rekommendationer initierar Adobe Sensei bildbearbetningen. Hur lång tid det tar beror på storleken på katalogen.

### Används

- Produktinformation

### Föreslagna butiksetiketter

- Du kanske också gillar
- Vi hittade andra produkter du kanske gillar
- Inspirerad av den här stilen

### Exempel

Följande bild visar produktinformationssidan för _Klammerklocka_:

![Klammerklocka](assets/visual-sim-pdp.png)

Följande visar _Visuell likhet_ rekommendationsenhet för _Klammerklocka_:

![Visuell likhetsenhet](assets/visual-sim-unit.png)
