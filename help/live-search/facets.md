---
title: '"Fasetter"'
description: '"[!DNL Live Search] används flera dimensioner av attributvärden som sökvillkor."'
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Fasetter

Faceting är en metod för högpresterande filtrering som använder flera dimensioner av attributvärden som sökvillkor. Fasetterad sökning är liknande, men avsevärt&quot;smartare&quot; än standarden [navigering i flera lager](https://docs.magento.com/user-guide/catalog/navigation-layered.html). Listan med tillgängliga filter avgörs av [filterbara attribut](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) av produkter som returneras i sökresultaten.

![Filtrerade sökresultat](assets/storefront-search-results-run.png)

## Motsvarande krav

Kategori- och produktattributkraven för faceting liknar de filterbara attribut som används för lagerstyrd navigering. Egenskaperna storefront för varje attribut måste anges till `filterable (with results)`.

* Upp till 100 attribut kan konfigureras som ansikten med [!DNL Live Search].
* [!DNL Live Search] indexerar upp till 300 attribut som filterbara/sökbara/sorterbara och synliga i sökningen.

| Inställning | Beskrivning |
|--- |--- |
| [Visningsinställningar för kategori](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | Ankarpunkt - `Yes` |
| [Attributegenskaper](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [Indatatyp för katalog](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| Egenskaper för attributarkiv | Använd i navigering i lager - `Filterable (with results)` |

## Standardattributvärden

Följande produktattribut har [storefront-egenskaper](https://docs.magento.com/user-guide/stores/attributes-product.html) som används av [!DNL Live Search] och som är aktiverat som standard.

| Egenskap | Storefront-egenskap | Attribut |
|---|---|---|
| Sorterbar | Används för sortering i produktlista | `price` |
| Sökbart | Använd i sökning | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Använd i navigering i lager - filtrerbar (med resultat) | `price`<br />`visibility`<br />`category_name` |

## Standardegenskaper för icke-systemattribut

I följande tabell visas standardegenskaperna för sökning och filtrering av attribut som inte finns i systemet, inklusive de som är specifika för Luma-exempeldata. Ange *Använd i sökning* attribute property to `Yes` gör attributet sökbart i båda [!DNL Live Search] och Adobe Commerce.

| Attributkod | Sökbart | Använd i navigering i lager |
|--- |--- |--- |
| aktivitet | Ja | Filterbar (med resultat) |
| attributes_brand | Ja | Nej |
| varumärke | Ja | Nej |
| klimat | Ja | Filterbar (med resultat) |
| räntekorridor | Ja | Filterbar (med resultat) |
| färg | Ja | Filterbar (med resultat) |
| kostnad | Ja | Nej |
| eco_collection | Ja | Filterbar (med resultat) |
| kön | Ja | Filterbar (med resultat) |
| tillverkare | Ja | Filterbar (med resultat) |
| material | Ja | Filterbar (med resultat) |
| syfte | Ja | Filterbar (med resultat) |
| strap_bag | Ja | Filterbar (med resultat) |
| style_general | Ja | Filterbar (med resultat) |

## Standardegenskaper för systemattribut

I följande tabell visas standardegenskaperna för sökning och filterbarhet för systemattribut.

| Attributkod | Sökbart | Använd i navigering i lager |
|--- |--- |--- |
| allow_open_amount | Ja | Filterbar (med resultat) |
| description | Ja | Nej |
| name | Ja | Nej |
| pris | Ja | Filterbar (med resultat) |
| short_description | Ja | Nej |
| sku | Ja | Nej |
| status | Ja | Nej |
| tax_class_id | Ja | Nej |
| url_key | Ja | Nej |
| vikt | Ja | Nej |
