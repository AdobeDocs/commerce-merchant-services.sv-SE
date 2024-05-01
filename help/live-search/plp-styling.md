---
title: Sidwidget för produktlista
description: Aktivera och formatera [!DNL Live Search Product Listing Page Widget]
exl-id: f7346a06-a8c7-4a33-8437-ea4f61d9281f
source-git-commit: 1e0baa20defe4e50bd9e45c03ff7c5f758b24e5d
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Sidwidget för produktlista

The [!DNL Live Search Product Listing Page Widget] (PLP) använder Commerce Services-plattformen för att tillhandahålla en utförlig, sökbar och faktabaserad produktlistsida. I det här avsnittet beskrivs hur du aktiverar och formaterar PLP-widgeten.

## Aktivera PLP-widgeten

När [!DNL Live Search] tjänsten är installerad, standardsökfunktionen konverteras till [!DNL Live Search] automatiskt.

The [!DNL Live Search] PLP-widgeten är aktiverad som standard för nya installationer. Om du uppgraderar [!DNL Live Search] och PLP-widgeten redan har stängts av, kommer att förbli så.

>[!IMPORTANT]
>
>När [!DNL Live Search Product Listing Page Widget] är aktiverat går det inte att ändra sorteringsordningen på en produktlistsida.

## Inaktivera PLP-widgeten

Så här inaktiverar du PLP-widgeten:

1. Gå till **Lager** > Inställningar > **Konfiguration** > **[!DNL Live Search]** > **Adobe Storefront-funktioner** och ange **Aktivera widgetar för produktlistor** till &quot;Nej&quot;.
1. Välj **Spara konfiguration** för att spara inställningen.

## Widgetfunktioner

PLP-widgeten innehåller en rad funktioner som förväntas på en sökbar produktsida. Bland dessa finns:

* Filtrera efter attribut
* Stöd för färgrutor
* Lägg till i kundvagnen
* Stöd för flera språk
* Prisreglage

Mer information om hur du anpassar PLP-widgeten för att hantera ovanstående funktioner finns i `storefront-product-listing-page` Viktigt i följande [repo](https://github.com/adobe/storefront-product-listing-page/).

## Exempel på format

Du kan anpassa utseende och känsla för PLP-widgeten så att den passar din webbplats med [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Element med anpassade klasser inom ett Adobe Commerce-tema ärvs inte. Dessa element måste ha en specifik klass som mål för att matcha de anpassade klasserna. De primära åtgärdsklasserna fungerar inte med en widgetknapp.
>Allmänna målelement inom CSS ärvs. `button` används för widgetknappar.

De markerade diven innehåller målklassen `ds-sdk-product-item__product-name`.

![Sidnumrering](assets/plp-css-example.png)

Anpassa produktnamnet genom att lägga till en regel som gör dem till stora bokstäver.

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![Sidnumrering](assets/plp-css-example-after.png)

## CSS-klasser

### Produktlista

* `.ds-sdk-product-list`: Yttre div
* `.ds-sdk-product-list__grid`: Inre div

![Sidnumrering](assets/plp-css-product-list.png)

#### Sidnumrering av produktlista

* `.ds-plp-pagination`

![Sidnumrering](assets/plp-css-pagination.png)

* `.ds-plp-pagination_item`

![Sidnumreringsobjekt](assets/plp-css-pagination-item.png)

* `.ds-plp-pagination_item--current`

![Aktuellt sidnumreringsobjekt](assets/plp-css-pagination-item-current.png)

### Widgetar

* `.ds-widgets`: Yttre div
* `.ds-widgets__actions`: Inre div på vänster sida
* `.ds-widgets__results`: Inre div på höger sida

![Widgetresultat](assets/plp-css-widgets.png)

### Sortera-listrutan

* `.ds-sdk-sort-dropdown`

![Sortera-listrutan](assets/plp-css-dropdown.png)

* `.ds-sdk-sort-dropdown__button`

![Nedrullningsknapp](assets/plp-css-dropdown-button.png)

* `.ds-sdk-sort-dropdown__items`

![Listruteobjekt](assets/plp-css-dropdown-items.png)

* `.ds-sdk-sort-dropdown__items--item`

![Listruteobjekt](assets/plp-css-dropdown-item.png)

* `.ds-sdk-sort-dropdown__items--item-selected`

![Listruta för markerat objekt](assets/plp-css-dropdown-selected.png)

* `.ds-sdk-sort-dropdown__items--item-active`

![Aktiv markering i listrutan](assets/plp-css-dropdown-active.png)

### Fasetter

* `.ds-plp-facets`
* `.ds-plp-facets__header`
* `.ds-plp-facets__header_title`
* `.ds-plp-facets__header__clear-all`

![Rubrik för fack](assets/plp-css-facets-title-clear.png){width="350"}

* `.ds-plp-facets__pills`
* `.ds-sdk-pill`

![Faktablad](assets/plp-css-facets-pill.png){width="350"}

* `.ds-sdk-pill__label`
* `.ds-sdk-pill__cta`

![Etikett för ansikten](assets/plp-css-pill-label-cta.png){width="350"}

* `.ds-plp-facets__list`

![Fasettlista](assets/plp-css-facets-list.png){width="350"}

* `.ds-sdk-input`
* `.ds-sdk-input__label`
* `.ds-sdk-product-item__product-swatch-group`
* `ds-sdk-product-item__product-swatch-item`
* `.ds-sdk-input_fieldset_show-more`

![Indata](assets/plp-css-sdk-input.png)

* `.ds-sdk-labelled-input`

![Indata med etiketter](assets/plp-css-labelled-input.png)

* `.ds-sdk-labelled-input__input`
* `.ds-sdk-labelled-input__label`

![Indataetikett](assets/plp-css-labelled-input-label.png)

### Produktartikel

* `.ds-sdk-product-item`
* `.ds-sdk-product-item__image`
* `.ds-sdk-product-item__product-name`
* `.ds-sdk-product-item__product-options`
* `.ds-sdk-product-price`
   * `.ds-sdk-product-price--no-discount`
   * `.ds-sdk-product-price--grouped`
   * `.ds-sdk-product-price--bundle`
   * `.ds-sdk-product-price--discount`

![Produkt](assets/plp-css-product.png)

### Läser in

* `.ds-sdk-loading`
* `.ds-sdk-loading__spinner`
* `.ds-sdk-loading__spinner-label`

![Läser in indikator](assets/plp-css-loading.png)
