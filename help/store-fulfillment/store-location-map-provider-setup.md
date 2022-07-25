---
title: Konfiguration av lagringsplats och mappningssystem
description: Konfigurera en distansleverantör som har stöd för mappning av lagringsplats i butikens gränssnitt. Butiksuppfyllelselösningarna kräver en distansleverantör för att möjliggöra butikssökning och andra mappnings- och schemaläggningsfunktioner för hela arbetsflödet.
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 556cbf803a0f8569e8561d2b33b7a976065ae814
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Inställningar för butiksplats och mappning

Aktivera lagringsplats och mappningsfunktioner för arkivuppfyllelse genom att konfigurera en [distansleverantör](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) om du vill söka efter butiksplatser.

**Krav**

Under konfigurationsprocessen anger du en Google API-nyckel för Google Maps-plattformen. Om du inte har någon, [generera en från Google Maps-plattformen](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Så här konfigurerar du distansprovidern:

1. Från **[!UICONTROL Stores > General]** i Admin lägger du till Google Maps-integrering för innehållstypen Karta.

   - Gå till **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Lägg till Google API-nyckeln i **[!UICONTROL Google Maps API Key]** fält.

1. Från **[!UICONTROL Stores > Inventory]** i Admin väljer du distansleverantör för Lagra uppfyllelse.

   - Gå till **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expandera avsnittet **[!UICONTROL Distance Provider for Distance Based SSA]**.

   - Ange **Provider** till **Google Map**.

1. Konfigurera inställningar för **[!UICONTROL Google Distance Provider]**.

   - Lägg till **Google API-nyckel**.

   - Ange **[!UICONTROL Computation Mode]** till `Driving` och **[!UICONTROL Value]** till `Distance`