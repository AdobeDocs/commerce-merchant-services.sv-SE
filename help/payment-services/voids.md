---
title: Voids
description: Med Voids kan du frigöra medel på ett kredit- eller betalkortskonto som blockeras eller hålls isär genom en auktorisering för beloppet av ett inköp.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Voids

Med [!DNL Payment Services]kan du använda befintlig Commerce-funktion för att annullera transaktioner. Med Voids kan du frigöra medel på ett kredit- eller betalkortskonto som blockeras eller hålls isär genom en auktorisering för beloppet av ett inköp.

>[!NOTE]
>
>Du kan bara annullera en transaktion om betalningen ännu inte har hämtats.

Om din butik [konfigurerad](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} om du bara vill auktorisera (inte inhämta) medel på försäljningsstället, leder ett köp från din butik till en beställning med `Processing` status i Commerce Admin.

Du kan också [avbryta en beställning](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} som inte faktureras. Alla ej inhämtade auktoriseringar annulleras också som en del av den annulleringsprocessen.

>[!NOTE]
>
>Om du avbryter en order skapas också en void, men om du annullerar en order utlöses ingen annullering.

Om du vill veta mer om de grundläggande stegen som en order går igenom kan du läsa [Orderarbetsflöde](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} i användarhandboken.

Mer information om funktionen void och hur du annullerar en ordertransaktion finns i [Bearbeta en beställning](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} i användarhandboken.
