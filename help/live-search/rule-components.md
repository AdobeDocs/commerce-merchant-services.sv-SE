---
title: "Regelkomponenter"
description: "Läs mer om [!DNL Live Search] regelkomponenter och operatorer."
exl-id: 4065aec3-a8d4-4d55-b939-16ad7b0f33ee
source-git-commit: 0a1d70465247422db44daee302c67fe1a5a29d32
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Regelkomponenter

En regel beskriver villkoren som krävs för att utlösa händelser som ändrar sökresultaten som returneras som svar på en kunds fråga.

## Krav

En enkel regel kan ha ett enda villkor och en enda händelse, medan en komplex regel kan ha upp till tio villkor som utlöser upp till 25 händelser.
Regler kan ha:

* Upp till tio villkor
* Upp till 25 händelser

Frågetext kan innehålla:

* Alfanumeriska tecken (bokstäver och siffror)
* Antingen versala tecken eller gemena tecken

## Logiska operatorer

De logiska operatorerna `AND` och `OR` förena två villkor och returnera olika resultat. Alla logiska operatorer som används i en regel med flera villkor är desamma. Det går inte att använda båda `AND` och `OR` i samma regel.

### Matcha operatorer

Operatorerna Matcha `All` och `Any` fastställer den logiska operatorn som används för att koppla flera villkor i regeln och kan användas för att ändra den befintliga operatorn.

* `All` - Använder `AND` logisk operator för att koppla flera villkor. En regel som använder `All` Matchningsoperatorn får bara ha en `Search query is` villkor.
* `Any` - Använder `OR` logisk operator för att koppla flera villkor.

När du komponerar en komplex regel kan det hjälpa till att skriva ut den med indrag för att beskriva de villkor, associerade händelser och produktnamn eller SKU:er som behövs för att returnera de resultat du vill uppnå. Bygg sedan regeln och testa resultatet.
