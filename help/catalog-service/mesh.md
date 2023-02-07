---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] for Adobe Commerce är ett sätt att integrera flera datakällor via en gemensam GraphQL-slutpunkt."'
source-git-commit: dd9ba7171cf6a199701b1abb8083a65326e89f5d
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

The [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) gör det möjligt för utvecklare att integrera privata eller tredjeparts-API:er och andra gränssnitt med Adobe-produkter med hjälp av Adobe IO.

![Katalogarkitektur - diagram](assets/catalog-service-architecture-mesh.png)

Det första steget för att använda API-nät med katalogtjänst är att ansluta API-nät till din instans. Se detaljerade instruktioner i [Skapa ett nät](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

För att slutföra installationen behöver du [Adobe IO CLI-paket](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) installerade.

När nätet har konfigurerats för Adobe iO kör du följande kommando som lägger till en `CommerceCatalogServiceGraph` till nätet.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

där `variables.json` är en separat fil som lagrar värden som används ofta för Adobe i/O.
API-nyckeln kan till exempel sparas i filen:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

När du har kört det här kommandot bör katalogtjänsten köras via API-nätet. Du kan köra `aio api-mesh:get` om du vill visa konfigurationen för det uppdaterade nätet.

## Använda API-nät

Med API Mesh kan användare använda andra datakällor för att förbättra din Adobe Commerce-instans. Den kan också användas för att konfigurera befintliga Commerce-data för att aktivera nya funktioner.

I det här exemplet används API-nät för att aktivera nivåpriser i Adobe Commerce.
Ersätt `name `, `endpoint` och `x-api-key` värden.

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
              "x-api-key": "storefront-catalog-apollo",
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

```json
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
