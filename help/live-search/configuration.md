---
title: "Inställningar för Commerce Configurations och [!DNL Live Search] "
description: "Beskriver de konfigurationsinställningar för Adobe Commerce som [!DNL Live Search] kan läsa."
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Live Search] och konfigurationsinställningar för Adobe Commerce

Det finns konfigurationsinställningar för Commerce som [!DNL Live Search] stöder. I det här avsnittet listas dessa konfigurationsvärden.

## Konfigurationsvärden som stöds

| Inställningar för Commerce-konfiguration | Stöds av Popover | Stöds av kortet |
|---|---|---|
| Lagrar -> Konfiguration -> Katalog -> Katalog -> Katalogsökning -> Minimal frågelängd | Ja | Ja |
| Stores -> Configuration -> Catalog -> Inventory -> Display Out of Stock Products | Ja w/ v2.0.4+ | Ja w/ v2.0.4+ |
| Stores -> Configuration -> General -> Currency Setup -> Currency Options -> Base Currency Options | Ja | Ja |

## Konfigurationsvärden som inte stöds

[!DNL Live Search] kan inte läsa alla konfigurationsvärden. I den här tabellen visas värden som kan vara av större intresse för utvecklare.

| Konfigurationsinställning för Magento | Anteckningar |
|---|---|
| Stores -> Configuration -> Catalog -> Storefront -> List Mode | Återger korrekt, men händelser skickas inte för vissa sidinteraktioner |
| Stores -> Configuration -> Catalog -> Storefront -> Allow All Products per Page | Ej implementerat. skickar begäran till söktjänsten utan sidstorlek och [!DNL Live Search] returnerar standardsidstorleken 20 |
| Lagrar -> Konfiguration -> Katalog -> Katalog -> Katalogsökning -> Maximal frågelängd | Ej implementerat. Search Services kan innehålla upp till 255 tecken |
| Lagrar -> Konfiguration -> Allmänt -> Valutainställning -> Valutaalternativ -> Standardvisningsvaluta | Ej implementerat. [!DNL Live Search] har endast åtkomst till basvalutan |
| Konfiguration -> Försäljning -> Moms -> Prisvisningsinställningar -> Visa produktpriser i katalog |  |
