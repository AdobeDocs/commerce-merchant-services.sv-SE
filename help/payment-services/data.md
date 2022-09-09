---
title: Tillgängliga data
description: Använd finansiella rapporteringsdata för att stämma av mot rapporter med andra system än handelssystem.
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Tillgängliga data

Vissa beställnings- och utbetalningsdata är tillgängliga för er så att ni kan samordna Adobe Commerce ekonomiska rapporter över externa system.

## Stäm av med ERP-system

Du kan stämma av Adobe Commerce ekonomiska rapporter med det ERP-system (Enterprise Resource Planning) som inte finns i Adobe med det inkrement-ID som är kopplat till en viss order.

När betalningstjänster skickar handelsordern till PayPal inkluderas öknings-ID som `custom_id`. The `custom_id` är synlig i detaljerna om handlaraktivitet för en utbetalning och på PayPals webbkrok.

`custom_id` Längst ned i detaljerna om handlaraktivitet för en utbetalning:

![`custom_id` i information om försäljningsaktivitet](assets/merchant-activity.png)

`custom_id` Information om PayPals webkrok:

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

Mer information finns i dokumentationen för PayPals REST API:er:

* [`purchase_unit` som `custom_id` resides](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-Collapse)
* [Visa orderinformation](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
