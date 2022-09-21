---
title: produktfråga
description: '"En referensguide för "products" GraphQL-frågan för Adobe Commerce Catalog Service."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---


# produktfråga

Katalogtjänsten för Adobe Commerce `products` frågan returnerar information om de SKU:er som angetts som indata. Frågan har samma namn som [`products` fråga](https://devdocs.magento.com//guides/v2.4/graphql/queries/products.html) som finns i Adobe Commerce och Magento Open Source finns det vissa skillnader.

Katalogtjänstfrågan kräver ett eller flera SKU-värden som indata. Frågan är främst utformad för att hämta information för att återge följande typer av innehåll:

* Produktinformationssidor - Du kan ge fullständig information om produkten som identifieras av den angivna SKU:n.

* Jämför produktsidor - Du kan hämta vald information om flera produkter, till exempel namn, pris och bild.

The `ProductView` utdataobjektet skiljer sig avsevärt från kärnan `products` fråga `Products` output-objekt. Viktiga skillnader är:

* Produkterna är enkla eller komplexa. Enkla, virtuella, nedladdningsbara och presentkortsprodukter mappas till `SimpleProductView`. Alla andra produkttyper mappas till `ComplexProductView`. Enkla produkter har definierade priser. Komplexa produkter har olika prisintervall. Eftersom komplexa produkter består av flera enkla produkter har de tillgång till enkla produktpriser.

* Marknadsföringsdefinierade attribut visas i en behållare på den översta nivån och anger deras butiksroller. Roller är Visa på PDP, Visa på PLP och Visa på sökresultat.

* Bilder är också tillgängliga som en behållare på den översta nivån och kan filtreras efter deras roll. En bild kan ha en grundläggande, liten eller miniatyrbildsroll.

## Syntax

```graphql
products (skus [String]) [ProductView]
```

## Obligatoriska rubriker

Du måste ange följande HTTP-huvuden för att köra frågan.

| Sidhuvud | Beskrivning |
| --- | --- |
| `Magento-Customer-Group` | För butiksklienter är det här värdet tillgängligt i butiken på `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | Det här värdet visas på **System** > **Commerce Services Connector** > **SaaS-identifierare** > **ID för datautrymme** eller kan hämtas genom att köra `bin/magento config:show services_connector/services_id/environment_id` -kommando. |
| `Magento-Store-Code` | Koden som tilldelats det arkiv som är associerat med den aktiva butiksvyn. Exempel, `main_website_store`. |
| `Magento-Store-View-Code` | Koden som tilldelats den aktiva butiksvyn. Exempel, `default`. |
| `Magento-Website-Code` | Koden som tilldelats den webbplats som är associerad med den aktiva butiksvyn. Exempel, `base`. |
| `X-Api-Key` | En unik nyckel som genereras under introduktionsprocessen. |

## Exempel på användning

### Returnera information om en enkel produkt

Följande fråga returnerar information om en enkel produkt.

**Begäran:**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
        regular {
          amount {
            value
            currency
          }
        }
      }
    }
  }
}
```

**Svar:**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### Returnera information om en komplex produkt {#complex-product-example}

Följande fråga returnerar information om en konfigurerbar produkt.

**Begäran:**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
        }
      }
    }
  }
}
```

**Svar:**

```json
{
  "data": {
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## Utdatafält

The `ProductView` return-objektet är ett gränssnitt som kan innehålla följande fält. Det implementeras av [`SimpleProductView`](#SimpleProductView-type) och [`ComplexProductView`](#ComplexProductView-type) typer.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | En lista över butiksdefinierade attribut som är avsedda för butiken. |
| `description` | Sträng | Detaljerad beskrivning av produkten. |
| `id` | ID! | Produkt-ID, som genereras som en sammansatt nyckel, unik per språkinställning. |
| `images(roles: [String])` | [ProductViewImage] | En lista med bilder som har definierats för produkten. |
| `metaDescription` | Sträng | En kort översikt över produkten för sökresultatlistor. |
| `metaKeyword` | Sträng | En kommaavgränsad lista med nyckelord som bara visas för sökmotorer. |
| `metaTitle` | Sträng | En sträng som visas i namnlisten och på fliken i webbläsaren och i sökresultatlistor. |
| `name` | Sträng | Produktnamn. |
| `shortDescription` | Sträng | En sammanfattning av produkten. |
| `sku` | Sträng | Produkt-SKU. |
| `url` | Sträng | Produktens kanoniska URL. |

### ComplexProductView-typ {#ComplexProductView-type}

The `ComplexProductView` -typen representerar paket, konfigurerbara och gruppprodukter. Komplexa produktpriser returneras som ett prisintervall, eftersom prisvärdena kan variera beroende på vilka alternativ du väljer. Typen implementeras `ProductView`.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | En lista över butiksdefinierade attribut som är avsedda för butiken. |
| `description` | Sträng | Detaljerad beskrivning av produkten. |
| `id` | ID! | Produkt-ID, som genereras som en sammansatt nyckel, unik per språkinställning. |
| `images(roles: [String])` | [ProductViewImage] | En lista med bilder som har definierats för produkten. |
| `metaDescription` | Sträng | En kort översikt över produkten för sökresultatlistor. |
| `metaKeyword` | Sträng | En kommaavgränsad lista med nyckelord som bara visas för sökmotorer. |
| `metaTitle` | Sträng | En sträng som visas i namnlisten och på fliken i webbläsaren och i sökresultatlistor. |
| `name` | Sträng | Produktnamn. |
| `options` | [ProductViewOption] | En lista med valbara alternativ. |
| `priceRange` | ProductViewPriceRange | En rad möjliga priser för en komplex produkt. |
| `shortDescription` | Sträng | En sammanfattning av produkten. |

### Pristyp

The `Price type` definierar priset på en enkel produkt eller en del av ett prisintervall för en komplex produkt. Den kan innehålla en lista med prisjusteringar.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `amount` | ProductViewMoney | Innehåller produktens monetära värde och valutakod. |

### PriceAdjustment-typ

The `PriceAdjustment` typ anger beloppet och typen för en prisjustering. Ett exempelkodvärde är `weee`.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `amount` | Float | Beloppet för prisjusteringen. |
| `code` | Sträng | Identifierar typen av prisjustering. |

### ProductViewAttribute-typ

The `ProductViewAttribute` type är en behållare för kunddefinierade attribut som visas i butiken.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `label` | Sträng | Attributets etikett. |
| `name` | Sträng! | Namn på en attributkod. |
| `roles` | [Sträng] | Roller som är avsedda för ett attribut på butiken, till exempel &quot;Visa på PLP&quot;, &quot;Visa i PDP&quot; eller &quot;Visa i sökning&quot;. |
| `value` | JSON | Attributvärde, godtycklig typ. |

### ProductViewImage-typ

The `ProductViewImage` type innehåller information om en produktbild.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `label` | Sträng | Produktbildens visningsetikett. |
| `roles` | [Sträng] | En lista som beskriver hur bilden används. Kan `image`, `small_image`, eller `thumbnail`. |
| `url` | Sträng! | URL:en till produktbilden. |

### ProductViewMoney-typ

The `ProductViewMoney` type definierar ett monetärt värde, inklusive ett numeriskt värde och en valutakod.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `currency` | ProductViewCurrency | En valutakod på tre bokstäver, t.ex. USD eller EUR. |
| `value` | Float | Ett tal som uttrycker ett monetärt värde. |

### ProductViewOption-typ

Med produktalternativen kan du konfigurera produkter genom att välja olika alternativvärden. Om du väljer ett eller flera alternativ visas en specifik enkel produkt.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `id` | ID | Alternativets ID. |
| `multi` | Boolean | Anger om alternativet tillåter flera alternativ. |
| `required` | Boolean | Anger om alternativet måste markeras. |
| `title` | Sträng | Alternativets visningsnamn. |
| `values` | [ProductViewOptionValue!] | Lista med tillgängliga alternativvärden. |

### Gränssnittet ProductViewOptionValue

The `ProductViewOptionValue` -gränssnittet definierar de produktfält som är tillgängliga för `ProductViewOptionValueProduct` och `ProductViewOptionValueConfiguration` typer.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `id` | ID | ID:t för ett alternativvärde. |
| `title` | Sträng | Alternativvärdets visningsnamn. |

### ProductViewOptionValueConfiguration-typ

The `ProductViewOptionValueConfiguration` type är en implementering av `ProductViewOptionValue` för konfigurationsvärden.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `id` | ID | ID:t för ett alternativvärde. |
| `title` | Sträng | Alternativvärdets visningsnamn. |

### ProductViewOptionValueProduct-typ

The `ProductViewOptionValueProduct` type är en implementering av `ProductViewOptionValue` som lägger till information om en enkel produkt.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `id` | ID | ID:t för ett alternativvärde. |
| `title` | Sträng | Alternativvärdets visningsnamn. |
| `product` | SimpleProductView | Information om en enkel produkt. |

### ProductViewPrice-typ

The `ProductViewPrice` type ger en grundläggande produktprisvy, som är inbyggd för enkla produkter.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `final` | Pris | Prisvärde efter rabatt, exklusive personliga kampanjer. |
| `regular` | Pris | Basproduktpris som anges av handlaren. |
| `roles` | [Sträng] | Anger om priset ska vara synligt eller dolt. |

### ProductViewPriceRange-typ

The `ProductViewPriceRange` typ anger det lägsta och högsta priset för en komplex produkt.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `maximum` | ProductViewPrice | Högsta pris. |
| `minimum` | ProductViewPrice | Minimipris. |

### SimpleProductView-typ {#SimpleProductView-type}

The `SimpleProductView` -typen representerar alla produkttyper, förutom paket, konfigurerbara och grupperade. De enkla produktpriserna innehåller inte prisintervall. `SimpleProductView` implements `ProductView`.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | En lista över butiksdefinierade attribut som är avsedda för butiken. |
| `description` | Sträng | Detaljerad beskrivning av produkten. |
| `id` | ID! | Produkt-ID, som genereras som en sammansatt nyckel, unik per språkinställning. |
| `images(roles: [String])` | [ProductViewImage] | En lista med bilder som har definierats för produkten. |
| `metaDescription` | Sträng | En kort översikt över produkten för sökresultatlistor. |
| `metaKeyword` | Sträng | En kommaavgränsad lista med nyckelord som bara visas för sökmotorer. |
| `metaTitle` | Sträng | En sträng som visas i namnlisten och på fliken i webbläsaren och i sökresultatlistor. |
| `name` | Sträng | Produktnamn. |
| `price` | ProductViewPrice | Prisvy för basprodukt. |
| `shortDescription` | Sträng | En sammanfattning av produkten. |
| `sku` | Sträng | Produkt-SKU. |
| `url` | Sträng | Produktens kanoniska URL. |
