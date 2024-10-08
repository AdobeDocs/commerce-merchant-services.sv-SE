---
title: Utöka och anpassa dataexportdata för SaaS
description: Lär dig hur du utökar och anpassar  [!DNL SaaS Data Export] feed-data.
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Utöka och anpassa dataexportdata för SaaS

Tillägget [!DNL Commerce Data Export] erbjuder ett sätt att exportera data från programmet [!DNL Commerce] till Commerce Services som Live Search, Catalog Service och Recommendations. Om det behövs kan du utöka och anpassa feed-data för att inkludera ytterligare data eller ändra insamlade data genom att uppdatera `Magento\CatalogDataExporter`-modulen.

>[!NOTE]
>
>Om du lägger till nya data i feeden eller ändrar befintliga data kan detta påverka prestanda för feedinsamlingen och orsaka problem i bearbetningslogiken på Adobe Commerce-sidan. Testa den anpassade koden innan du sammanfogar den i en produktionsmiljö.

## Utöka attributdata i produktflödet

Produkterna innehåller standardattribut som krävs för produktbearbetning eller som ofta används av konsumenterna. Du kan inkludera ytterligare systemattribut i produktflödet genom att lägga till dem i flödet.

Slutför den här åtgärden genom att uppdatera modulen `magento/catalog-data-exporter` och lägga till ytterligare systemattribut i konfigurationsfilen [för beroendeinjicering](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`). Lägg till attributen i produktattributfrågan (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`).

**Exempel**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
