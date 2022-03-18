---
title: Voids
description: Med Voids kan du frigöra medel på ett kredit- eller betalkortskonto som blockeras eller hålls isär genom en auktorisering för beloppet av ett inköp.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Voids

Med [!DNL Payment Services]kan du använda befintlig Commerce-funktion för att annullera transaktioner. Med Voids kan du frigöra medel på ett kredit- eller betalkortskonto som blockeras eller hålls isär genom en auktorisering för beloppet av ett inköp.

>[!NOTE]
>
>Du kan bara annullera en transaktion om betalningen ännu inte har hämtats.

Om din butik [konfigurerad](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} om du bara vill auktorisera (inte hämta) medel vid försäljningstillfället resulterar ett köp från din butik i en order med en `Processing` status i Magento Admin.

Du kan också [avbryta en beställning](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target=&quot;_blank&quot;} som inte har fakturerats. Alla ej inhämtade auktoriseringar annulleras också som en del av den annulleringsprocessen.

>[!NOTE]
>
>Om du avbryter en order skapas också en void, men om du annullerar en order utlöses ingen annullering.

Om du vill veta mer om de grundläggande stegen som en order går igenom kan du läsa [Orderarbetsflöde](https://docs.magento.com/user-guide/sales/order-workflow.html){target=&quot;_blank&quot;} i användarhandboken.

Mer information om funktionen void och hur du annullerar en ordertransaktion finns i [Bearbeta en beställning](https://docs.magento.com/user-guide/sales/order-processing.html){target=&quot;_blank&quot;} i användarhandboken.
