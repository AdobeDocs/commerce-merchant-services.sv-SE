---
title: Skapa anpassade händelser
description: Lär dig hur du skapar anpassade händelser för att koppla dina Adobe Commerce-data till andra Adobe DX-produkter.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Skapa anpassade händelser

Du kan utöka [eventplattform](events.md) genom att skapa egna butiksevenemang för att samla in data som är unika för branschen. När du skapar och konfigurerar en anpassad händelse skickas den till [Adobe Commerce Events Collector](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-collector).

## Hantera anpassade händelser

Anpassade händelser stöds endast för Adobe Experience Platform. Anpassade data vidarebefordras inte till Adobe Commerce dashboards och metrics trackers.

För alla `custom` -händelsen, insamlaren:

- Lägger till `identityMap` med `ECID` som primär identitet
- Inkluderar `email` in `identityMap` som sekundär identitet _if_ `personalEmail.address` anges i händelsen
- Omsluter den fullständiga händelsen inuti en `xdm` objekt innan det vidarebefordras till Edge

Exempel:

Anpassade händelser som publicerats via Adobe Commerce Events SDK:

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

I Experience Platform:

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> Användning av anpassade händelser kan påverka Adobe Analytics standardrapporter.

## Hantera händelseåsidosättningar (anpassade attribut)

Attributåsidosättningar för standardhändelser stöds endast för Experience Platform. Anpassade data vidarebefordras inte till kontrollpaneler och mätmätare för Commerce.

För alla händelser med `customContext`, åsidosätter insamlaren sammanfogningsfält som anges i relevanta sammanhang med fält i `customContext`. Användbart för åsidosättningar är när en utvecklare vill återanvända och utöka kontexter som angetts av andra delar av sidan i händelser som redan stöds.

>[!NOTE]
>
>När du åsidosätter anpassade händelser bör händelsevidarebefordran till Experience Platform inaktiveras för den händelsetypen för att undvika dubbelräkning.

Exempel:

Produktvy med åsidosättningar publicerade via Adobe Commerce Events SDK:

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

I Experience Platform:

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> Om du åsidosätter händelser med anpassade attribut kan det påverka Adobe Analytics standardrapporter.
