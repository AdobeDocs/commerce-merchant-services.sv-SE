---
title: Konfiguration av flera webbplatser och omfattningar
description: Konfigurera lager och leveransmetoder för flera webbplatser och butiksomfång.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 1%

---


# Konfiguration av flera webbplatser och omfattningar

Du kan ange [Omfång](https://docs.magento.com/user-guide/configuration/scope.html) för ett fåtal element som kan användas för olika vyer av webbplatser, butiker och butiker:

- [Hantera Stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html) per omfång

- Hantera [!DNL Delivery Methods] per omfång

Du kan tilldela Stock till en webbplats eller ett butiksomfång. Uppdatera sedan butikskällorna för att ange tillgängliga leveransmetoder (hemleverans, butiksupphämtning).

När konfigurationen har uppdaterats kan alternativen för butiksupphämtning på produktinformationssidan (PDP) i Adobe Commerce Store endast väljas för produkter som är tillgängliga från en Stock-källa som tillåter butiksupphämtning.

## Hantera inställningar för butiksinhämtning

Aktivera eller inaktivera [!UICONTROL In-Store Pickup] alternativ för varje webbplats eller lagringsomfång på [Konfigurationer för leveranssätt](enable-general.md#delivery-methods) i Admin.

1. Navigera till **[!UICONTROL Stores > Configuration]**.

1. Välj det scope (den webbplats som ska lagras) som ska konfigureras.

1. Navigera till med omfång valt **[!UICONTROL Sales > Delivery Methods]**.

1. Inaktivera eller aktivera **[!UICONTROL In-Store Pickup]** Leveranssätt.

Du kan också ange om utfall eller butiksupphämtning ska vara tillgänglig globalt i det här avsnittet.

Hantera [!UICONTROL In-Store Pickup] och [!UICONTROL Delivery Method] inställningar per Stock-källa. Det finns många andra konfigurationer som ger full flexibilitet i implementeringen.