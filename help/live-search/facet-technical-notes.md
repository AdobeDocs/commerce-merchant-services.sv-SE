---
title: "Tekniska anmärkningar för ansiktet"
description: "Teknisk information om att använda [!DNL Live Search] facets."
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Tekniska anteckningar för Fasett

Faceting är en högpresterande filtreringsmetod som använder flera dimensioner av sökbara statiska och dynamiska attributvärden som sökvillkor.

[!DNL Live Search] använder `productSearch` fråga som returnerar faceting och andra data som är specifika för [!DNL Live Search]. Se [`productSearch` fråga](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) för kodexempel.

## Fasettaggregering

Faktoraggning utförs så här: om butiken har tre aspekter (kategorier, färg och pris) och shopparfiltren på alla tre (färg = blå, priset är från 10,00-50,00, kategorier = `promotions`).

* `categories` aggregering - aggregat `categories`använder sedan `color` och `price` filter, men inte `categories` filter.
* `color` aggregering - aggregat `color`använder sedan`price` och `categories` filter, men inte `color` filter.
* `price` aggregering - aggregat `price`använder sedan `color` och `categories` filter, men inte `price` filter.
