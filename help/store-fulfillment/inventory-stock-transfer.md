---
title: Inventory management Source Transfer
description: "Konfigurera stockar för  [!DNL Store Fulfillment solution] med Adobe Commerce Inventory management. Ställ in ett nytt lager och överför lager från standardlagret så att du kan tilldela det till källor som konfigurerats för att aktivera Store Pickup-funktioner som krävs av Store Fulfillment-lösningen."
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Inventory management Source Transfer

[!DNL Store Fulfillment]-lösningen använder Adobe Commerce Inventory management. Som standard tilldelar konfigurationen [!DNL Commerce] allt webblager till standardlagret, som inte kan ha ytterligare källor tilldelade. Eftersom en webbplats bara kan tilldelas ett enda lager måste en handlare konfigurera ett nytt lager och eventuellt överföra sitt standardkällager till en källa som är tilldelad till rätt omfång. Sedan kan källan tilldelas den nya stammen.

>[!IMPORTANT]
>
>Handlarna måste behålla standardkällan för alla produkter som ingår i grupp- och paketprodukttyperna. Produkterna behöver en lagerkvantitet som uppfyller tröskelvärdet för minsta kvantitet för lagerartiklar och innehåller lagerstatusen [!UICONTROL In Stock].

Dessa konfigurationsändringar hjälper dig att uppnå tre saker:

1. [Överför lager till källan](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) för att flytta lager från standardlagret/standardkällan till den nya lagret/källan.

1. [Tilldela källor](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) gruppvis för att lägga till nya källor för alla dina produkter.

1. [Slutför satsvisa uppdateringar för produktattribut](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) för att lägga till attributen `Allow Store Pickup` och `Allow Home Delivery` i befintliga produkter. När lösningen är installerad har attributen de optimala *standardvärdena*. Dessa attribut tillämpas dock inte på befintliga produkter förrän du slutför den satsvisa uppdateringsprocessen.

Lager dras av från den valda källan (butiksplats eller handelslager). Källor som används som e-handelslager måste tilldelas samma lager som butiksupphämtningsplatsen och prioriteras före butiksplatserna. Mer information finns i [Prioritera källor för en Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

Mer information om hur du hanterar lager, lager och källor finns i Adobe Commerce användardokumentation:

- [Hantera lager](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Hantera lagerkvantiteter](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Hantera Stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Hantera källor](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Prioriterar källor för en Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Massuppdateringar för produktattribut](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Om du ändrar konfigurationen för lager och Stock-källor kan det även påverka integrerade system längre fram i kedjan. Se till att du förstår hur ändringarna av lagerkonfigurationen påverkar dessa system.
