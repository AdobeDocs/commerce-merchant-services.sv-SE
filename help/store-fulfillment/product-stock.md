---
title: Product Stock Management
description: Konfigurera butiksmeddelanden och funktioner som är tillgängliga för kunderna.
role: User, Admin
level: Intermediate
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Produkthistorik

Som handlare kan du använda Adobe Commerce [Inventory management](https://docs.magento.com/user-guide/catalog/inventory-management.html) stock- och källalternativ. Dessutom kan du styra andra lagertillgänglighetsalternativ som relaterar till din handlarverksamhet med butikslösningen Fulfillment.

- Leveransalternativ i hemmet från Merchant Store

- Tillåt/Tillgängligt för butiksplockning

- UPC/SKU/andra unika produktidentifierare

- Tröskelvärdet slut

- Minska lager från specifika platser vid beställning

Konfigurera alternativ för Product Stock från administratören: **[!UICONTROL Catalog > Products > Select Product]**

## **ProduktStock-alternativ**

| **Fält** | **Beskrivning** | **Omfång** | **Obligatoriskt** |
|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Finns för hemleverans** | Anger tillgänglighet för hemleverans (leverans från butik) för produkten. När det här alternativet är aktiverat kan alla tilldelade butiksplatser med tillgängligt lager för produkten kvalificeras för alternativet Home Delivery. När produkten är inaktiverad är den aldrig berättigad till Home Delivery, även om en återförsäljarbutik har tillgängligt lager.</br></br>I de flesta fall räcker det att ange det här alternativet på handlarnivå. Det kan dock finnas unika fall för specifika produkter, t.ex. sådana som omfattas av statliga fraktbegränsningar, som inte bör omfattas av systemet för hemleverans. | Webbplats | Nej |
| **[!UICONTROL Available for Store Pickup]** | Ställ in butiksupphämtning för produkten. När det här alternativet är aktiverat är alla tilldelade butiksplatser med tillgängligt lager för produkten berättigade till alternativet Butiksplockning. När produkten är inaktiverad är den aldrig berättigad till Store Pickup, även om en handlarbutik har tillgängligt lager.</br></br>Det här alternativet kan vara användbart för fall där du spårar handelslager i systemet, men inte vill sälja det från e-handelskanalen. | Webbplats | Nej |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Attributet ska redan finnas som ett produktattribut och relateras till **[!UICONTROL Barcode Source / Barcode Type]** inställning. Det här attributet används för att spåra en skannerbar streckkod för dina produkter. Det här värdet kan skickas när en order skickas till dina butiker för plockning. Butikskollegister kan använda värdet i plocklistan för att matcha produkter på hyllan med en streckkodsskanner. | Butiksvy | Nej |

{style=&quot;table-layout:auto&quot;}

## Källor för produktnivålager

| **Fält** | **Beskrivning** | **Omfång** | **Obligatoriskt** |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | Ange lagertröskeln för artikeln inom varje källa. När lagret ligger under tröskelvärdet anses det vara utanför lagret vid källan.</br></br>Om du vill använda inställningen för global lagringskonfiguration ska du kontrollera **[!UICONTROL Use Default]** alternativ. | Global | Nej |
| **[!UICONTROL Allow Store Pickup]** | Ange uttryckligen om artikeln är tillgänglig för butiksupphämtning, oavsett vilken lagerplatskonfiguration som är tillgänglig eller vilken butiksplats som är tillgänglig.</br></br> Om du vill använda produktnivåinställningen avmarkerar du [!UICONTROL Use Default] och gör dina val. I annat fall väljs den här inställningen baserat på konfigurationen för **[!UICONTROL Allow In-Store Pickup]** som ställs in på Stock-källan. | Global | Nej |

{style=&quot;table-layout:auto&quot;}

