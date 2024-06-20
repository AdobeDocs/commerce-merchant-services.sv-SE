---
title: "[!DNL Storefront Popover]"
description: "Den [!DNL Live Search storefront popover] returnerar dynamiskt föreslagna produkter och miniatyrbilder."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

När [!DNL Live Search] är [installerat](install.md), a [!DNL popover] visas i butiken när kunderna skriver i [Sök](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) box. För varje tecken som skrivs visas [!DNL popover] uppdateras med förslag på produkter och miniatyrbilder av de bästa sökresultaten.

[!DNL Live Search] returnerar resultat för en fråga med minst två tecken. För en partiell matchning är det maximala antalet tecken per ord 20. Det går inte att konfigurera antalet tecken i en sökfråga.

Som standard [!DNL Live Search] supports [omdirigering av söktermer](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>Lär dig hur du anger produktattribut som sökbara i [Konfigurera Live Search](workspace.md) artikel.

## [!DNL Popover] sidstorlek

Sidstorleken för [!DNL popover] anger hur många rader med automatiskt slutförda produkter som kan returneras. Under installationen av Live Search `page_size` värdet ändras till det aktuella värdet för [Katalogsökning](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` inställning.

Som standard är värdet för Katalogsökning - Gräns för automatisk komplettering satt till åtta rader (eller rader). Ändra sidstorleken för [!DNL popover]gör du följande:

1. På *Administratör* sidebar, gå till **Lager** > Inställningar > **Konfiguration**.
1. Expandera på den vänstra panelen **Katalog** och välja **Katalog** i listan med inställningar.
1. Expandera *Katalogsökning* -avsnitt.
1. Ange **Gräns för automatisk komplettering** till antalet rader som du vill tillåta i [!DNL popover].
1. När du är klar klickar du på **Spara konfiguration**.

## Stilar [!DNL Popover] exempel

Du kan anpassa utseendet och känslan för [!DNL Popover] för att matcha företagets grafiska profil och varumärkesriktlinjer.

The [!DNL storefront popover] visar alltid produkten `name` och `price`och valet av fält kan inte konfigureras. Men [!DNL popover] kan formateras med [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) -klasser. Följande deklarationer ändrar till exempel bakgrundsfärgen för [!DNL popover] behållare och sidfot.

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

Du kan använda följande klassväljare för att formatera behållaren och produktelementen i [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

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

#### .livesearch-produktlänk

![Produktresultat](assets/livesearch-product-link.png)

## Arbeta med ett ändrat tema {#working-with-modified-theme}

Du kan använda [!DNL storefront popover] med en skräddarsydd [tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/) som ärver de nödvändiga filerna från *Luma*. The `top.search` -block i `header-wrapper` i `Magento_Search` får inte ändras.

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

## Headless-implementationer

För dem med headless-implementeringar kan du installera [!DNL Live Search popover] med [npm-paket](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
