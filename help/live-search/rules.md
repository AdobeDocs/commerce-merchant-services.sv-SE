---
title: "Regler"
description: "[!DNL Live Search] regler kombinerar logik med åtgärder för att forma shoppingupplevelsen."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 7307702a62a6b2c3e6c6083a59f2ac3587b0985e
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Regler

[!DNL Live Search] regler kombinerar logik med åtgärder för att forma en kunds sökupplevelse i din butik. Du kan använda regler för att lyfta, begrava, fästa eller dölja produkter och kalibrera sökresultaten i realtid för att uppnå dina affärsmål.

Varje regel har tre huvudkomponenter:

* Villkor - De villkor som utlöser en åtgärd.
* Händelser - De åtgärder som utförs när villkoren uppfylls.
* Detaljer - Namnet på regeln samt valfri tidsram och beskrivning.

Du kan kombinera flera villkor och åtgärder och schemalägga en regel som aktiv under en period.

## Krav

En enkel regel kan ha ett enda villkor och en enda händelse, medan en komplex regel kan ha upp till tio villkor som utlöser upp till 25 händelser.
Regler kan ha:

* Upp till tio villkor
* Upp till 25 händelser

Frågetext kan innehålla:

* Alfanumeriska tecken (bokstäver och siffror)
* Versaler eller gemener. Versaler ignoreras.

## Logiska operatorer

De logiska operatorer `AND` och `OR` förena två villkor och returnera olika resultat. Alla logiska operatorer som används i en regel med flera villkor är desamma. Det går inte att använda båda `AND` och `OR` i samma regel.

### Matcha operatorer

Operatorerna Matcha `All` och `Any` fastställer den logiska operatorn som används för att koppla flera villkor i regeln och kan användas för att ändra den befintliga operatorn.

* `All` - Använder `AND` logisk operator för att koppla flera villkor. En regel som använder `All` Matchningsoperatorn får bara ha en `Search query is` villkor.
* `Any` - Använder `OR` logisk operator för att koppla flera villkor.

När du komponerar en komplex regel kan det hjälpa till att skriva ut den med indrag för att beskriva de villkor, associerade händelser och produktnamn eller SKU:er som behövs för att returnera de resultat du vill uppnå. Bygg sedan regeln och testa resultatet.

## Prioritetsordning med flera regler

Endast en regel tillämpas på en sökterm åt gången.
Om flera regler är tillämpliga på en sökfras, tillämpas alla dessa regler. Om det är en kollision mellan två regler—`rule 1` som ökar sku1 men `rule 2` döljer samma SKU - då den senast använda regeln (`rule 2`) har företräde.

* Regler ordnas med tidsstämpeln&quot;Senast ändrad&quot;. Den senast ändrade regeln tillämpas först och sedan äldre regler i tidsstämpelordning.
* The `query is` villkor har företräde framför andra villkor. Om en nyare regel innehåller en `query contains` villkor, men en äldre regel har `query is` villkor, `query is` regeln används.

### Förfrågningar från Storefront

Om en aktiv regel innehåller en `query is` villkoret matchar sökfrasen, som används. Om det finns flera matchande regler med en `query is` villkor används den senast uppdaterade aktiva regeln.
I annat fall används den senast uppdaterade aktiva regeln.

### Förhandsgranska begäranden

Begäran som gjorts i Admin fungerar något annorlunda. När du förhandsgranskar i Admin tillämpas alla regler, inklusive de som har upphört att gälla och schemalagts.

* Om regeln som förhandsgranskas har en `query is` -villkoret, används det.
* Om regeln som förhandsgranskas inte har `query is` villkor och en efterföljande aktiv, matchande regel med `query is` -villkoret finns, `query is` regeln används.
* Om regeln som förhandsgranskas inte har `query is` villkor och ingen annan regel med `query is` om ett villkor hittas och regeln som förhandsgranskas tillämpas.

## Kategoriregler och produkttilldelningar för kategorier

[!DNL Live Search] använder du för att filtrera efter kategorier.
I Adobe Commerce kan du dock skapa en virtuell kategori med [Kategoriprodukttilldelningar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Den här typen av kategori skapas vid körning och finns inte i kategoridatabasen. Därför bör [!DNL Live Search] kan inte läsa eller använda den här kategoritypen.
