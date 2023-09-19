---
title: "Styla [!DNL Popover] Elements"
description: "Teknisk information om anpassning av [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Stilar [!DNL Popover] Element

The [[!DNL storefront popover]](storefront-popover.md) visar alltid produkten `name` och `price`och valet av fält kan inte konfigureras. Men [!DNL popover] kan formateras med CSS-klasser. Följande deklarationer ändrar till exempel bakgrundsfärgen för [!DNL popover] behållare och sidfot.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Synlighet för behållare

Den överordnade komponenten för `.livesearch.popover-container` är `.search-autocomplete`.  The `.active` -klassen anger behållarens synlighet. The `.active` -klassen läggs till villkorligt när [!DNL popover] är öppen.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Mer information om hur du formaterar butikselement finns i [CSS (Cascading Style Sheets)](https://developer.adobe.com/commerce/frontend-core/guide/css/) i [Utvecklarhandbok för Edge](https://developer.adobe.com/commerce/frontend-core/guide/).

## Klassväljare

Följande klassväljare kan användas för att formatera behållar- och produktelementen i [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### Väljare för behållarklass

#### .livesearch.popover-container

![[!DNL Popover] container](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![Visa alla sidfötter](assets/livesearch-view-all-footer.png)

### Produktklassväljare

#### .livesearch.products-container

![Produktbehållare](assets/livesearch-product-container.png)

#### .livesearch.product-result

![Produktresultat](assets/livesearch-product-result.png)

#### .livesearch.product-name

![Produktnamn](assets/livesearch-product-name.png)

#### .livesearch.product-price

![Produktpris](assets/livesearch-product-price.png)

## Arbeta med ett ändrat tema {#working-with-modified-theme}

The [!DNL storefront popover] kan användas med en anpassad [tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/) som ärver de nödvändiga filerna från *Luma*. The `top.search` -block i `header-wrapper` i `Magento_Search` får inte ändras.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Inaktiverar [!DNL popover]

Så här inaktiverar du [!DNL popover] och återställa standardinställningarna [Snabbsökning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) anger du följande kommando:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
