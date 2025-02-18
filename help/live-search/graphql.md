---
title: GraphQL
description: Med arbetsytan i  [!DNL Live Search] GraphQL kan du skapa frågor med dina livedata.
exl-id: f7b17c5a-a97b-4724-a50e-83e28a4c4c38
source-git-commit: cf94623fd4a87c13d15c81ac62243a508cb1d14d
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 0%

---

# GraphQL

Med arbetsytan *GraphQL* kan administratörer skapa och testa GraphQL-frågor med egna data.

Den här arbetsytan stöder frågorna [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) och [`attributeMetadata`](https://developer.adobe.com/commerce/services/graphql/live-search/attribute-metadata/).

![GraphQL-arbetsyta](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "a306") {
    total_count
    items {
      product {
        sku
		name
      }
    }
    facets {
      title
    }
  }
}
```

Variabler:

```json
{
  "Magento-Environment-Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "Magento-Website-Code": "base",
  "Magento-Store-Code": "base",
  "Magento-Store-View-Code": "default",
  "X-Api-Key": "search_gql"
}
```

