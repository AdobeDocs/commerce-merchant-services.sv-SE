---
title: '"Skapa en order med [!DNL Quick Checkout] i Admin"'
description: '"Administratören ger möjlighet att lägga en order med [!DNL Quick Checkout] direkt från administratören av en handlare för kunder som behöver hjälp."'
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 1%

---

# Skapa en order med [!DNL Quick Checkout]

Du kan konfigurera [!DNL Quick Checkout] efter dina behov med hjälp av alternativen i Adobe Commerce Admin.

[!DNL Quick Checkout] för Adobe Commerce och Magento Open Source kan ni göra en beställning direkt från administratören för era kunder som behöver hjälp. The **[!UICONTROL Create New Order]** blanketten innehåller all information som behövs för att slutföra den normala utcheckningsprocessen, inklusive säker kreditkortsblankett för att hämta kreditkortsinformationen. Se [Skapa en order](https://docs.magento.com/user-guide/customers/customer-account-create-order.html){target=&quot;_blank&quot;} om du vill ha detaljerad information om de steg som krävs.

## Värdbaserade kreditkortsfält

När man lägger beställningar för kundens räkning [!DNL Quick Checkout] visas som ett av de tillgängliga betalningsmetoderna:

1. På _Administratör_ sidlist, expandera **[!UICONTROL Sales]** och välja **[!UICONTROL Orders]**.
1. Klicka på **[!UICONTROL Create New Order]**.
1. Fyll i avsnitt efter behov för ordern (mer information finns i [Skapa en order](https://docs.magento.com/user-guide/customers/customer-account-create-order.html){target=&quot;_blank&quot;}).
1. I _[!UICONTROL Payment Method]_ska du kunna använda [!DNL Quick Checkout] som betalningsmetod.
1. Klicka på **[!UICONTROL Submit Order]**.

>[!IMPORTANT]
>
> Under EAP-programmet (Early Adobe Program) kan användare inte använda inloggningen med engångslösenord för att automatiskt fylla i information om frakt och betalning.
