---
title: "Lägg till regler"
description: "Lär dig skapa [!DNL Live Search] regler."
exl-id: c6b92ef5-3b08-47f9-8412-955a9c95a9ee
source-git-commit: 0b0e9a630162c4c98c6a3af969002def03155267
workflow-type: tm+mt
source-wordcount: '1419'
ht-degree: 0%

---

# Lägg till regler

För att skapa en regel är det första steget att använda regelredigeraren för att definiera villkoren i kundens frågetext som utlöser de associerade händelserna. Slutför sedan regelinformationen, testa resultatet och publicera regeln.

## Lägg till en regel

1. Gå till Admin **Marknadsföring** > SEO &amp; Search > **[!DNL Live Search]**.
1. Ange **Omfång** för att identifiera [butiksvy](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) där regeln gäller.
1. Klicka på **Regler** -fliken.
1. Klicka **Lägg till regel** för att starta regelredigeraren.

## Villkor

Villkor är krav för att utlösa en händelse. En regel kan ha upp till tio villkor och 25 händelser.

![Regel - Bygg din regel](assets/rules-add-workspace.png)

>[!NOTE]
>
>För närvarande går det inte att rikta regler mot en viss kundgrupp.

### Ett villkor

1. Under *Bygg din regel* väljer du **Villkor** som ska uppfyllas och följ instruktionerna för att slutföra satsen.

   * Sökfrågan innehåller - Ange den textsträng som måste finnas i kundens fråga. Inställningen Matcha avgör i vilken grad kundens fråga matchar katalogen. Alternativ:<br /> Valfritt - Alla delar av kundens frågetext kan matcha villkoret.<br />Alla - Alla kundens frågor måste matcha villkoret.
   * Sökfrågan är - Ange en textsträng som exakt matchar kundens fråga. Till exempel: &quot;yoga byxor&quot;. Regler med `Search query is` och Matcha `All` kan bara ha ett villkor.
   * Sökfrågan börjar med - Ange ett tecken eller en textsträng som måste vara i början av kundens fråga.
   * Sökfrågan avslutas med - Ange ett tecken eller en textsträng som måste vara i slutet av kundens fråga.

   Resultaten visas omedelbart i dialogrutan *Testa din regel* och numreras efter prioritet. Du kan använda *Resultat per rad* i det övre högra hörnet om du vill ändra antalet produkter i varje rad.

   ![Regel - enkel](assets/rule-simple-test.png)

1. Om du vill testa andra frågor ändrar du frågetexten i dialogrutan *Testa din regel* sökruta och tryck **Retur**.
Testfönstret återger först frågan från sökrutan Villkor. Men nu återges frågan från testfrågerutan. Testfönstret återger bara en fråga i taget.
1. Om du gillar resultatet kan du uppdatera texten i *Villkor* sökruta. Klicka sedan var som helst på sidan för att uppdatera resultatet i testfönstret.
1. Gå till steg 3 om du vill skapa en enkel regel med ett villkor: [Lägg till händelser](#events).

### Flera villkor

1. Om du vill skapa en regel med flera villkor klickar du på **Lägg till villkor**.
En regel kan ha upp till tio villkor. Den logiska operatorn som förenar två villkor baseras på den aktuella *Matcha* inställning. Som standard *Matcha* är `All` och den logiska operatorn är `AND`.

   ![Regler - sökfrågan innehåller](assets/rules-search-query-contains-and.png)

1. Markera det andra villkoret och ange den obligatoriska frågetexten.

1. Om du vill ändra logiken i regeln ändrar du **Matcha** för att bestämma hur nära kundens sökvillkor måste matcha frågevillkoret. Ange **Matcha** till något av följande:

   * Valfri - (standard) Alla logiska operatorer i regeln ställs in på `OR` och resultaten visas i testfönstret.
   * Alla - Alla logiska operatorer i regeln är inställda på `AND` och resultaten visas i testfönstret.

   The *Matcha* värdet bestämmer den logiska operatorn som används för att koppla flera villkor. Ändra *Matcha* inställning ändrar alla logiska operatorer i regeln. Det går inte att kombinera `AND` och `OR` i samma regel.

   I det här exemplet, i stället för att söka efter &quot;yoga-byxor&quot;, finns det två separata frågor som söker efter &quot;yoga&quot; eller &quot;byxor&quot;. Den här regeln är mindre specifik och utlöses oftare i butiken än i den andra.

   ![Regler - matchning](assets/rules-match.png)

1. Om du vill lägga till ytterligare ett villkor klickar du på **Lägg till villkor** och upprepa processen.

## Rankningstyp

Rankningen kombinerar användarbeteenden och webbplatsstatistik för att avgöra produktrankningen.
Butiksägare kan skapa följande typer av rankningsstrategier:

![Regler - matchning](assets/rules-ranking-type.png)

* Mest köpta: Detta rangordnar produkter efter totala inköp per SKU under de senaste 7 dagarna.
* Mest tillagda i kundvagnen - rangordnas efter den totala &quot;Lägg i kundvagnen&quot;-aktiviteten under de senaste 7 dagarna.
* Mest visade: Rankar min totala visning per SKU under de senaste 7 dagarna.
* Rekommenderas för dig - Använder `viewed-viewed` datapunkt - Handlare som tittade på denna SKU tittade också på dessa andra SKU:er
* Trending: Synkroniserar sidvyhändelser under de senaste 72 timmarna för bakgrundshändelser och 24 timmar för förgrundshändelser
* Ingen: Produkterna beställs efter relevans

1. Välj typ av strategi för regeln. Fönstret Testa din regel visar det förväntade resultatet.

>[!NOTE]
>
>Apostrofer och citattecken i frågor kan leda till vissa mindre problem med rankning och relevans på vissa språk.

## Lägga till händelser

Händelser är åtgärder som ändrar sökresultaten när definierade villkor uppfylls. En regel kan ha upp till 25 händelser.

* Öka - Flyttar en produkt högre i sökresultaten.
* Bury - Flyttar en SKU nedåt i sökresultaten.
* Fäst en produkt - Produkten visas i den valda positionen på sidan.
* Dölj en produkt - Utesluter en SKU från sökresultaten.

Det enklaste sättet att fästa en produkt är genom att dra och släppa.

1. Klicka och dra en produkt i testfönstret. Dra och släpp den på önskad plats. Fälten Produkt och Position fylls i automatiskt i rutan Händelser.

   ![Regler - matchning](assets/rule-event-pin-product.png)

Du kan också klicka på nålikonen för att fästa en produkt på dess aktuella plats. Använd snabbmenyn för ellipsen för att &quot;Fäst överst&quot; eller &quot;Fäst underst&quot;.

>[!NOTE]
>
>Du kan bara fästa produkter som returneras i frågan.

Eller så kan händelser anges manuellt:

1. Under *Händelser* väljer du **Händelse** att äga rum när de tillhörande villkoren är uppfyllda.

   Välj till exempel `Hide a product`. Ange sedan namnet på den produkt som du vill dölja. Produkter föreslås när du skriver.

1. För flera händelser väljer du andra händelser som du vill ska utlösas när villkoren uppfylls.

## Ytterligare information

Informationen som anges här visas i [Regelinformation](rules-workspace.md) -panelen.

1. Under *Detaljer*, ange **Namn** för regeln. Alla regelnamn måste vara unika.
1. Ange en kort beskrivning **Beskrivning** av regeln.
1. Ange **Startdatum** och **Slutdatum** för att regeln ska vara aktiv eller välj datum i kalendern.

   Om du vill markera ett datumintervall klickar du på det första datumet och drar för att markera intervallet.

   ![Regel - slutförd](assets/rule-add-details.png)

## Slutför regeln

1. Granska resultatet av regeln i testfönstret.
1. Om regeln har flera frågor testar du var och en som kan påverkas av regeln.
1. När du är klar klickar du på **Spara och publicera**.

   Regeln läggs till i listan på arbetsytan för regler.

1. Även om de aktiva reglerna börjar gälla omedelbart kan du behöva vänta upp till 15 minuter på att de cachelagrade frågeresultaten i butiken ska uppdateras.

## Fältbeskrivningar

### Villkor (om)

| Villkor | Beskrivning |
|--- |--- |
| Sökfrågan innehåller | Ett tecken eller en textsträng som ingår i kundens fråga. Köparens fråga behöver bara matcha en enda karaktär för att uppfylla det här villkoret. |
| Sökfrågan är | Ett tecken eller en textsträng som exakt matchar kundens fråga. Komplexa frågor med flera villkor kan inte disponeras när det här villkoret används. |
| Sökfrågan börjar med | Köparens fråga börjar med det här tecknet eller textsträngen. |
| Sökfrågan slutar med | Köparens fråga avslutas med det här tecknet eller textsträngen. |

### Logiska operatorer

| Operator | Beskrivning |
|--- |--- |
| ELLER | (Standard) Den logiska operatorn `OR` jämför två villkor och uppfyller kraven för att utlösa en händelse om minst ett villkor är sant. |
| OCH | Den logiska operatorn `AND` jämför två villkor och uppfyller kraven för att utlösa en händelse om båda villkoren är uppfyllda. |

### Matcha operatorer

| Operator | Beskrivning |
|--- |--- |
| Alla | Ändrar alla logiska operatorer i regeln till `OR` och returnerar uppsättningen med matchande produkter. |
| Alla | Ändrar alla logiska operatorer i regeln till `AND` och returnerar uppsättningen med matchande produkter. |

### Händelser

| Händelse | Beskrivning |
|--- |--- |
| Öka | Flyttar en SKU eller ett intervall med SKU:er högre i sökresultaten. Var och en markeras med ett&quot;boosted&quot; preview badge i testsökresultaten. |
| Bury | Flyttar en SKU eller ett intervall med SKU:er nedåt i sökresultaten. Var och en markeras med ett&quot;nedgrävt&quot; förhandsvisningsmärke i testsökresultaten. |
| Fäst en produkt | Kopplar en enskild SKU till en viss plats i sökresultaten. Produkten är markerad med ett&quot;fäst&quot; förhandsvisningsmärke i testsökresultaten. |
| Dölj en produkt | Utesluter en SKU, eller ett intervall med SKU:er, från sökresultatet. |

### Detaljer

| Fält | Beskrivning |
|--- |--- |
| Namn | Regelns namn. Regelnamn måste vara unika. |
| Startdatum | Regelns startdatum, om det är schemalagt. |
| Slutdatum | Regelns slutdatum, om det är schemalagt. |
| Beskrivning | En kort beskrivning av regeln. |
