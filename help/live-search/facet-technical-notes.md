---
title: Tekniska anteckningar för Fasett
description: Teknisk information om Live Search-aspekter.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: e53fb13b98684757b8081b2e19dd33d925e8ce5d
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Tekniska anteckningar för Fasett

Faceting är en högpresterande filtreringsmetod som använder flera dimensioner av sökbara statiska och dynamiska attributvärden som sökvillkor.

[!DNL Live Search] använder `productSearch` fråga som returnerar faceting och andra data som är specifika för [!DNL Live Search]. Se [`productSearch` fråga](https://devdocs.magento.com/live-search/product-search.html) för kodexempel.

## Fasettaggregering

Aggregering av ansikten utförs så här om butiken har tre aspekter (kategorier, färg och pris) och shopparfiltren på alla tre (färg = blå, priset är från 10,00-50,00, kategorier = `promotions`).

* `categories` aggregering - aggregat `categories`, används `color` och `price` filter, men inte `categories` filter.
* `color` aggregering - aggregat `color`, används `price` och `categories` filter, men inte `color` filter.
* `price` aggregering - aggregat `price`, används `color` och `categories` filter, men inte `price` filter.
