---
title: Anpassa
description: Lär dig hur du anpassar dina produktrekommendationer.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: acfaa1d72265e42b973677a7e014ba4b350ec56b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Anpassa

När du installerar produktmodulen Recommendations skapar Adobe Commerce `ProductRecommendationsLayout` katalog. Den här katalogen innehåller mallfiler som du kan anpassa för att ändra hur rekommendationerna visas i din butik. Du kan ändra eller åsidosätta följande mall:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Mer information om hur du ändrar mallfiler finns i [Mallanpassning](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) i Utvecklarhandbok för Adobe.

Om du ändrar `recommendations.html` måste du bevara följande taggar i filen för att vara säker på att Adobe Commerce kan samla in rekommendationer från din butik:

| Tagg | Använd |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Samlar in visningshändelser. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Samlar in klickningshändelser. <br/>**Obs!** Om du lägger till ankartaggar måste du ta med dessa attribut. |

Förutom `recommendations.html` -filen, `ProductRecommendationsLayout` katalogen innehåller följande underkataloger:

| Katalog | Syfte |
|---|---|
| `layout` | Innehåller `*.xml` filer för varje sidtyp |
| `templates` | Innehåller filer som anropar hämtningen och återger skript |
| `web/js` | Innehåller JavaScript-filer som hämtar och återger rekommendationer för din butik |
| `web/template` | Innehåller mallen för `magento/product-recommendations` modul |

## Placering av rekommendationsenhet

När du [skapa](create.md) en rekommendation anger du [plats](placement.md) där den visas på sidan. En rekommendationsenhet kan placeras antingen högst upp eller längst ned i behållaren med huvudinnehåll. Du kan dock anpassa den här placeringen. Om du skapar en innehållstyp för en rekommendation i Page Builder använder du verktygen i Page Builder för att placera rekommendationsenheten på sidan. För alla andra sidtyper redigerar du `*.xml` filer som genereras när rekommendationen skapas.

1. Ändra till `layout` katalog:

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   I följande tabell visas de XML-filer som finns i den här katalogen:

   | Filnamn | Sida |
   |---|---|
   | `catalog_category_view.xml` | Kategori |
   | `catalog_product_view.xml` | Produktinformation |
   | `checkout_cart_index.xml` | Kundvagn |
   | `checkout_onepage_success.xml` | Utcheckning |
   | `cms_index_index.xml` | Startsida |

   >[!NOTE]
   >
   >Filnamnen i `layout` katalogen kan vara annorlunda om din butik använder tillägg från tredje part.

1. Ändra `catalog_product_view.xml` så att rekommendationsenheten visas efter produktbilden på produktinformationssidan. Innan du anpassar XML-filen bör du ta en titt på filen och förstå vilka avsnitt du behöver ändra:

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   I ovanstående utdrag visas `main.content` referensblock anger att rekommendationsenheten kommer att placeras någonstans i förhållande till det elementet. dess `block` -elementet innehåller `after="-"` -attribut, som anger att rekommendationsenheten ska visas på sidan efter huvudinnehållsblocket.

1. Låt oss ändra den här filen genom att ange ett annat innehållsblock.

   Ändra referensblocket `name` från `main.content` till `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Ändringen resulterar i att din rekommendationsenhet visas efter produktbilden på produktinformationssidan. Om du vill att rekommendationsenheten ska visas före `product.info.media`, ändra `after="-"` attribut till `before="-"`. The `pagePlacement` argument är ett internt argument som inte ska ändras.

Se [layoutöversikt](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) om du vill ha mer information om de olika blocktyperna på sidan.

## Anpassade produktattribut

Utvecklare behöver ofta tillgång till anpassade produktattributvärden i rekommendationsenheter på butiker så att de kan lägga till visuella behandlingar till produkter som baseras på dessa attribut.

Om din butik till exempel säljer vissa ekologiska produkter kan du ha ett anpassat attribut för de produkter som anger dem som `Organic = Yes`. Du kan behöva ha tillgång till det här attributvärdet i butiken så att du kan ge dessa produkter visuell specialbehandling när de visas i Recommendations. På samma sätt kan du få tillgång till dessa anpassade produktattributvärden för att märka produkter eller skapa en egen logik i webbplatsens presentationsskikt.

![Lägg till märke](assets/unit-custom.png)

Om du vill vara säker på att ett anpassat produktattribut är tillgängligt när du återger rekommendationsenheten på sidan anger du `Used in Product Listing` egenskap till `Yes` i [Produktattribut](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) i Admin.

När den här egenskapen är angiven innehåller JSON-nyttolasten en `attributes` objekt som innehåller en array med attributkoder och värden. Du kan sedan använda en anpassad storefront-formatering som baseras på dessa attributvärden, som att lägga till speciella visuella behandlingar eller emblem som nämns ovan.

>[!NOTE]
>
>Det kan ta upp till en timme innan produktattributändringar visas i JSON-nyttolasten.
