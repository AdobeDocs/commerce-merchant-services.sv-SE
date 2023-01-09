---
title: "Regler"
description: "[!DNL Live Search] regler kombinerar logik med åtgärder för att forma shoppingupplevelsen."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 941fdc25f93679593cb3c5db0d29d7a561fcce58
workflow-type: tm+mt
source-wordcount: '296'
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

De logiska operatorerna `AND` och `OR` förena två villkor och returnera olika resultat. Alla logiska operatorer som används i en regel med flera villkor är desamma. Det går inte att använda båda `AND` och `OR` i samma regel.

### Matcha operatorer

Operatorerna Matcha `All` och `Any` fastställer den logiska operatorn som används för att koppla flera villkor i regeln och kan användas för att ändra den befintliga operatorn.

* `All` - Använder `AND` logisk operator för att koppla flera villkor. En regel som använder `All` Matchningsoperatorn får bara ha en `Search query is` villkor.
* `Any` - Använder `OR` logisk operator för att koppla flera villkor.

När du komponerar en komplex regel kan det hjälpa till att skriva ut den med indrag för att beskriva de villkor, associerade händelser och produktnamn eller SKU:er som behövs för att returnera de resultat du vill uppnå. Bygg sedan regeln och testa resultatet.
