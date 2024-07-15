---
title: Voids
description: Med Voids kan du frigöra medel på ett kredit- eller betalkortskonto som blockeras eller hålls isär genom en auktorisering för beloppet av ett inköp.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Voids

Med [!DNL Payment Services] kan du använda den befintliga Commerce-funktionen för annullering av transaktioner. Med Voids kan du frigöra medel på ett kredit- eller betalkortskonto som blockeras eller hålls isär genom en auktorisering för beloppet av ett inköp.

>[!NOTE]
>
>Du kan bara annullera en transaktion om betalningen ännu inte har hämtats.

Om din butik är [konfigurerad](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} att endast auktorisera (inte hämta) medel vid försäljningstillfället, resulterar ett köp från din butik i en beställning med statusen `Processing` i Commerce Admin.

Du kan också [avbryta en beställning](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} som inte fakturerats. Alla ej inhämtade auktoriseringar annulleras också som en del av den annulleringsprocessen.

>[!NOTE]
>
>Om du avbryter en order skapas också en void, men om du annullerar en order utlöses ingen annullering.

Om du vill veta mer om de grundläggande steg som en order går igenom läser du avsnittet [Orderarbetsflöde](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} i huvudanvändarhandboken.

Mer information om funktionen void och hur du annullerar en ordertransaktion finns i [Bearbeta en beställning](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} i huvudanvändarhandboken.
