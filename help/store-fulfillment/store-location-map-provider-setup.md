---
title: Konfiguration av lagringsplats och mappningssystem
description: Konfigurera en distansleverantör som har stöd för mappning av lagringsplats i butikens gränssnitt. Butiksuppfyllelselösningarna kräver en distansleverantör för att möjliggöra butikssökning och andra mappnings- och schemaläggningsfunktioner för hela arbetsflödet.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 1%

---

# Lagringsplats och mappningsinställningar

Aktivera butikens plats och mappningsfunktioner för arkivuppfyllelse genom att konfigurera en [distansleverantör](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) för att söka efter butiksplatser.

**Krav**

Under konfigurationsprocessen anger du en Google API-nyckel för Google Maps-plattformen. Om du inte har någon [genererar du en från Google Maps-plattformen](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Så här konfigurerar du distansprovidern:

1. Lägg till Google Maps-integreringen för innehållstypen Karta från konfigurationen **[!UICONTROL Stores > General]** i Admin.

   - Gå till **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Lägg till din Google API-nyckel i fältet **[!UICONTROL Google Maps API Key]**.

1. I konfigurationen **[!UICONTROL Stores > Inventory]** i Admin väljer du distansprovidern för arkivuppfyllelse.

   - Gå till **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expandera avsnittet **[!UICONTROL Distance Provider for Distance Based SSA]**.

   - Ange **Provider** till **Google Map**.

1. Konfigurera inställningar för **[!UICONTROL Google Distance Provider]**.

   - Lägg till din **Google API-nyckel**.

   - Ange **[!UICONTROL Computation Mode]** till `Driving` och **[!UICONTROL Value]** till `Distance`
