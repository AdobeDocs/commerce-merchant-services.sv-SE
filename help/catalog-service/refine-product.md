---
title: refineProduct query
description: '"En referenshandbok för GraphQL-frågan "refineProduct" för Adobe Commerce Catalog Service."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---


# refineProduct query

The `refineProduct` frågan begränsar resultatet av en `products` fråga som kördes mot en komplex produkt. Innan du kör `refineProduct` frågan måste du köra `products` fråga och konstruera svaret så att det returnerar en lista med `options` inom en `ComplexProductView` textbundet fragment. När en kund väljer ett produktalternativ (till exempel storlek eller färg) i butiken kör du `refineProduct` fråga, ange SKU och ID:n för valda alternativvärden som indata. Beroende på hur många produktalternativ den komplexa produkten har kan du behöva köra `refineProduct` fråga flera gånger tills kunden har valt en viss variant.

Du bör konstruera svaret på din fråga så att det innehåller både `ComplexProductView` och `SimpleProductView` textbundna fragment. Om kunden inte har valt alla alternativ som krävs returnerar frågan ID:n för de omarkerade alternativen och produktens lägsta och högsta pris, baserat på de valda alternativen och möjliga återstående alternativ. Om kunden har valt alla alternativ som krävs returnerar frågan information om en enkel produkt, som innehåller ett fast pris.

## Syntax

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
```

## Obligatoriska rubriker

Du måste ange följande HTTP-huvuden för att köra frågan.

| Sidhuvud | Beskrivning |
|--- | ---|
| `Magento-Customer-Group` | För butiksklienter är det här värdet tillgängligt i butiken på `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | Det här värdet visas på **System** > **Commerce Services Connector** > **SaaS-identifierare** > **ID för datautrymme** eller kan hämtas genom att köra `bin/magento config:show services_connector/services_id/environment_id` -kommando. |
| `Magento-Store-Code` | Koden som tilldelats det arkiv som är associerat med den aktiva butiksvyn. Exempel, `main_website_store`. |
| `Magento-Store-View-Code` | Koden som tilldelats den aktiva butiksvyn. Exempel, `default`. |
| `Magento-Website-Code` | Koden som tilldelats den webbplats som är associerad med den aktiva butiksvyn. Exempel, `base`. |
| `X-Api-Key` | En unik nyckel som genereras under introduktionsprocessen. |

## Exempel på användning

### Returnera information om en delvis vald komplex produkt

Följande fråga returnerar information om de färgalternativ som är tillgängliga för en medelstor produktvariant `MH12`. Värdet för `optionIDs` parametern input hämtas från `products` fråga [Returnera information om en komplex produkt](products.md#complex-product-example) exempel.

**Begäran:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
                    }
                }
            }
        }
        ... on ComplexProductView {
            options {
                id
                title
                required
                values {
                    id
                    title

                }
            }
            priceRange {
                maximum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### Returnera information om en helt vald komplex produkt

I följande fråga har kunden valt alternativ för både storlek och färg. Svaret innehåller information om motsvarande enkla produkt.

**Begäran:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
                    }
                }
            }
        }
        ... on ComplexProductView {
            options {
                id
                title
                required
                values {
                    id
                    title

                }
            }
            priceRange {
                maximum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## Indatafält

Du måste ange ett SKU-värde och minst ett alternativ-ID som indata.

| Fält | Datatyp | Beskrivning |
|--- | --- | ---|
| `optionIds` | [Sträng!]! | En lista över ID:n som tilldelats de produktalternativ som kunden har valt, till exempel specifika färger och storlekar. |
| `sku` | Sträng! | SKU för en komplex produkt. |

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
