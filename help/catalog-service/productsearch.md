---
title: productSearch-fråga
description: '"En referensguide för GraphQL-frågan "productSearch" för Adobe Commerce Catalog Service."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 2%

---


# productSearch-fråga

Katalogtjänsten för Adobe Commerce `productSearch` kan använda LiveSearch för att returnera information om de SKU:er som angetts som indata. Frågan är densamma som [`productSearch` fråga](https://devdocs.magento.com//live-search/product-search.html)returnerar LiveSearch en `productView` -objekt. Se [`productSearch` fråga](https://devdocs.magento.com//live-search/product-search.html) ämne för referensinformation.

## Syntax

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
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

I följande exempel returnerar frågan information om samma produkter som i föregående exempel. Den har dock konstruerats för att returnera artikelinformation i katalogtjänsten `productView` objekt i stället för kärna `product` -objekt. Observera att prisinformationen varierar beroende på produkttyp. Av praktiska skäl visas inte ansiktsinformation.

**Begäran:**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
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
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
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
    }
  }
}
```

**Svar:**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
