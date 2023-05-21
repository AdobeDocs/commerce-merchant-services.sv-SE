---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] for Adobe Commerce är ett sätt att integrera flera datakällor via en gemensam GraphQL-slutpunkt."'
exl-id: cdda4a83-3c5f-4a69-8279-b90464e16c0e
source-git-commit: 368059d50133d8b01be83e1616044a61ab094e3c
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

The [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) gör det möjligt för utvecklare att integrera privata eller tredjeparts-API:er och andra gränssnitt med Adobe-produkter med Adobe I/O Runtime.

![Katalogarkitektur - diagram](assets/catalog-service-architecture-mesh.png)

Det första steget för att använda API-nät med katalogtjänst är att ansluta API-nät till din instans. Se detaljerade instruktioner i [Skapa ett nät](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Installera [Adobe Developer CLI-paket](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

När Nät har konfigurerats på Adobe I/O Runtime kör du följande kommando som lägger till en `CommerceCatalogServiceGraph` till nätet.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

Plats `variables.json` är en separat fil som lagrar de vanligaste värdena för Adobe I/O Runtime.
API-nyckeln kan till exempel sparas i filen:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

När du har kört det här kommandot bör katalogtjänsten köras via API-nätet. Du kan köra `aio api-mesh:get` om du vill visa konfigurationen för det uppdaterade nätet.

## Exempel på API-nät

Med API Mesh kan användare använda andra datakällor för att förbättra din Adobe Commerce-instans. Den kan också användas för att konfigurera befintliga Commerce-data för att aktivera nya funktioner.

### Aktivera nivåpriser

I det här exemplet används API-nät för att aktivera nivåpriser i Adobe Commerce.
Ersätt `name `, `endpoint`och `x-api-key` värden.

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

Fråga Mesh efter nivåpriser när konfigurationen är klar:

```graphql
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```

### Hämta ett enhets-ID

Det här nätet lägger till `entityId` till gränssnittet ProductView. Ersätt `name `, `endpoint`och `x-api-key` värden.

```json
{
    "meshConfig": {
      "sources": [
        {
          "name": "<Commerce Instance Name>",
          "handler": {
            "graphql": {
              "endpoint": "<Adobe Commerce GraphQL endpoint>"
            }
          },
          "transforms": [
              {
                  "prefix": {
                      "includeRootOperations": true,
                        "value": "Core_"
                  }
              }
          ]
        },
        {
          "name": "CommerceCatalogServiceGraph",
          "handler": {
            "graphql": {
              "endpoint": "https://catalog-service.adobe.io/graphql",
              "operationHeaders": {
                "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
                "Magento-Website-Code": "{context.headers['magento-website-code']}",
                "Magento-Store-Code": "{context.headers['magento-store-code']}",
                "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>",
                "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
              },
              "schemaHeaders": {
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>"
              }
            }
          }
        }
      ],
      "additionalTypeDefs": "extend interface ProductView {\n  entityId: String\n}\n extend type SimpleProductView {\n  entityId: String\n}\n extend type ComplexProductView {\n  entityId: String\n}\n",
      "additionalResolvers": [
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n    items {\n  sku\n uid\n  }\n    }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          },
          {
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n items {\n  sku\n uid\n }}",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          }
      ]
    }
  }
```

`entityId` kan nu frågas:

```graphql
query {
  products(skus: ["MH07"]){
    sku
    name
    id
    entityId
  }
}
```
