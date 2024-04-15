---
title: Inställningar för Commerce Configurations och [!DNL Live Search] '
description: Beskriver de konfigurationsinställningar för Adobe Commerce som [!DNL Live Search] kan läsa.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: d1cd70e66e616c052418c719f6da23b010a22241
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# [!DNL Live Search] och konfigurationsinställningar för Adobe Commerce

Det finns konfigurationsinställningar för Commerce som [!DNL Live Search] stöder. I det här avsnittet listas dessa konfigurationsvärden.

## Konfigurationsvärden som stöds

| Konfigurationsinställning för Commerce | Stöds av Popover | Stöds av kortet |
|---|---|---|
| Stores > Configuration > Catalog > Catalog > Catalog Search > Allow All Products per Page Length | Ja. Max 500 produkter | Ja. Max 500 produkter |
| Lagrar > Konfiguration > Katalog > Katalog > Katalogsökning > Minimal frågelängd | Ja | Ja |
| Stores > Configuration > Catalog > Catalog > Catalog Search > Products per Page on Grid Allowed Valowed | Ja | Ja |
| Stores > Configuration > Catalog > Catalog > Catalog Search > Products per Page on Grid Default Value | Ja. Max 500 produkter | Ja. Max 500 produkter |
| Stores > Configuration > Catalog > Inventory > Display out of Stock Products | Ja w/ v2.0.4+ | Ja w/ v2.0.4+ |
| Lager > Konfiguration > Valuta > Standardvisningsvaluta | Ja w/3.1.0+ | Ja w/3.1.0+ |
| Stores > Configuration > General > Currency Setup > Currency Options > Base Currency Options | Ja | Ja |

Priserna på Widget Product Listing Page och Popover konverteras nu till standardvisningsvalutan med de konfigurerade valutakurserna.

## Sökvillkor

[!DNL Live Search] supports [omdirigering av söktermer](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) på implementeringar där Adobe Commerce hanterar routningen: Luma och andra PHP-baserade teman.

## Konfigurationsvärden som inte stöds

[!DNL Live Search] kan inte läsa alla konfigurationsvärden. I den här tabellen visas värden som kan vara av större intresse för utvecklare.

| Konfigurationsinställning för Commerce | Anteckningar |
|---|---|
| Stores > Configuration > Catalog > Storefront > List Mode | Återger korrekt, men händelser skickas inte för vissa sidinteraktioner |
| Stores > Configuration > Catalog > Catalog > Catalog Search > Maximum Query Length | Inte implementerad; Search Services kan innehålla upp till 255 tecken |
| Configuration > Sales > Tax > Price Display Settings > Display Product Prices in Catalog |  |
| Stores > Configuration > Catalog > Storefront > Product Listing Sort By | Gäller inte [!DNL Live Search] [Sidwidget för produktlista](plp-styling.md) |
