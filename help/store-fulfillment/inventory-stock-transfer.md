---
title: Inventory management Source Transfer
description: Konfigurera lager för lagerhantering genom att ställa in en ny aktie och överföra lager från standardlagret.
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Inventory management Source Transfer

The [!DNL Store Fulfillment] lösningen använder Adobe Commerce Inventory management. Som standard är [!DNL Commerce] I tilldelas allt webblager till standardlagret, som inte kan ha ytterligare källor tilldelade. Eftersom en webbplats bara kan tilldelas ett enda lager måste en handlare konfigurera ett nytt lager och eventuellt överföra sitt standardkällager till en källa som är tilldelad till rätt omfång. Sedan kan källan tilldelas den nya stammen.

Dessa konfigurationsändringar hjälper dig att uppnå tre saker:

1. [Överför lager till källa](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) om du vill flytta lager från standardlagret/standardkällan till den nya lagret/källan.

2. [Tilldelar källor gruppvis](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) för att lägga till nya källor för alla dina produkter.

3. [Slutför massuppdateringar av produktattribut](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) för att lägga till `Allow Store Pickup` och `Allow Home Delivery` attribut till befintliga produkter. När lösningen är installerad är attributen optimala *standard* värden. Men dessa attribut tillämpas inte på befintliga produkter förrän du slutför gruppuppdateringsprocessen.

Lager dras av från den valda källan (butiksplats eller handelslager). Källor som används som e-handelslager måste tilldelas samma lager som butiksupphämtningsplatsen och prioriteras före butiksplatserna. Mer information finns i [Prioritera källor för en Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).


Mer information om hur du hanterar lager, lager och källor finns i Adobe Commerce användardokumentation:

- [Hantera lager](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Hantera lagerkvantiteter](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Hantera Stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Hantera källor](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Prioritera källor för en Stock](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Massuppdateringar för produktattribut](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Om du ändrar konfigurationen för lager och Stock-källor kan det även påverka integrerade system längre fram i kedjan. Se till att du förstår hur ändringarna av lagerkonfigurationen påverkar dessa system.
