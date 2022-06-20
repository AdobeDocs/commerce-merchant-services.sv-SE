---
title: Skapa anpassade händelser
description: Lär dig hur du skapar anpassade händelser för att koppla dina Adobe Commerce-data till andra Adobe DX-produkter.
source-git-commit: f167002e1aa401d223f0830954ab09b66017476e
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Skapa anpassade händelser

Du kan utöka [eventplattform](events.md) genom att skapa egna butiksevenemang för att samla in data som är unika för er bransch. När du skapar och konfigurerar en anpassad händelse skickas den till [Magento Storefront Event Collector](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

## Hantera anpassade händelser

Anpassade händelser stöds endast för Adobe Experience Platform. Anpassade data vidarebefordras inte till Adobe Commerce dashboards och metrics trackers.

För alla `custom` -händelse lägger insamlaren till en `personId` (`ecid`) till `customContext` och radbryter en `xdm` objektet runt det innan det vidarebefordras till Edge.

Exempel:

Anpassad händelse som publicerats via MSE SDK:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

Experience Platform:

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> Användning av anpassade händelser kan påverka OTB Adobe Analytics-rapporter.

## Hantera händelseåsidosättningar (anpassade attribut)

Attributåsidosättningar för standardhändelser stöds endast för Experience Platform. Anpassade data vidarebefordras inte till kontrollpaneler och mätmätare för Commerce.

För alla händelser med en uppsättning `customContext`, åsidosätter samlaren `personId` och Adobe Analytics-räknare, och vidarebefordrar alla andra attribut som anges i `customContext`.

Exempel:

Produktvy med åsidosättningar publicerade via MSE SDK:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

Experience Platform:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

Produktvy med Adobe Commerce-åsidosättningar som publicerats via MSE SDK:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

Experience Platform:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> Åsidosättande händelser med anpassade attribut kan påverka OTB Adobe Analytics-rapporter.
