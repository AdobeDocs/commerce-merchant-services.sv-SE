---
title: Konfiguration av flera webbplatser och omfattningar
description: Konfigurera lager och leveransmetoder för flera webbplatser och butiksomfång.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Konfiguration av flera webbplatser och omfattningar

Du kan ange [scopet](https://experienceleague.adobe.com/en/docs/commerce-admin/start/setup/websites-stores-views#scope-settings) för ett fåtal element så att du kan hantera flera olika vyer för webbplatser, butiker och arkiv:

- [Hantera Stock](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage) per scope

- Hantera [!DNL Delivery Methods] per scope

Du kan tilldela Stock till en webbplats eller ett butiksområde. Uppdatera sedan butikskällorna för att ange tillgängliga leveransmetoder (hemleverans, butiksupphämtning).

När konfigurationen har uppdaterats kan alternativen för butiksupphämtning på produktinformationssidan (PDP) i Adobe Commerce Store endast väljas för produkter som är tillgängliga från en Stock-källa som tillåter butiksupphämtning.

## Hantera inställningar för butiksinhämtning

Aktivera eller inaktivera [!UICONTROL In-Store Pickup]-alternativen för varje webbplats eller butiksområde i [Leveransmetodkonfigurationer](enable-general.md#delivery-methods) i Admin.

1. Navigera till **[!UICONTROL Stores > Configuration]**.

1. Välj det scope (den webbplats som ska lagras) som ska konfigureras.

1. Navigera till **[!UICONTROL Sales > Delivery Methods]** när omfånget är valt.

1. Inaktivera eller aktivera leveransmetoden **[!UICONTROL In-Store Pickup]**.

Du kan också ange om utfall eller butiksupphämtning ska vara tillgänglig globalt i det här avsnittet.

Hantera inställningarna [!UICONTROL In-Store Pickup] och [!UICONTROL Delivery Method] per Stock-källa. Det finns många andra konfigurationer som ger full flexibilitet i implementeringen.
