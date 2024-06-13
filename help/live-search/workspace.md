---
title: Konfigurera Live Search
description: The [!DNL Live Search] används för att konfigurera, hantera och övervaka sökningsprestanda.
exl-id: fb85974a-a5f9-4e6c-bd03-451e6457f2d2
source-git-commit: 099a4b9ce3ab71bc3c7ae181be242863a55d0ca9
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Konfigurera Live Search

På arbetsytan kan du konfigurera, hantera och övervaka prestanda för [!DNL Live Search]. Menyn längst upp ger åtkomst till verktygen i varje funktionsområde. De tillgängliga funktionerna återspeglar det aktuella menyvalet.

![Arbetsyta](assets/workspace.png)

## Ange omfånget

Inledningsvis [omfång](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) alla [!DNL Live Search] inställningarna är inställda på `Default Store View`. Om [!DNL Commerce] installationen innehåller flera butiksvyer, uppsättning **Omfång** till [butiksvy](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) där dina facet-inställningar gäller.

## Menyalternativ

| Alternativ | Beskrivning |
|--- |--- |
| [Prestanda](performance.md) | Instrumentpanelen ger dig insikt i hur produktsökningar fungerar. |
| [Motsatthet](facets.md) | Högpresterande filtrering som använder flera dimensioner av attributvärden för att förfina sökvillkoren. |
| [Synonymer](synonyms.md) | Utvidga sökräckvidden och inkludera ord som kunderna kan använda för att hitta produkter som skiljer sig från dem i katalogen. |
| [Search Merchandising](rules.md) | Formge sökupplevelsen med logiska regler som utlöser schemalagda åtgärder. Öka, begrava, fästa eller dölj produkter för att kalibrera sökresultaten efter era affärsmål. |
| [Kategorimarknadsföring](category-merch.md) | Använd regler och intelligent marknadsföring på kategorinivå. |
| [GraphQL](graphql.md) | Utvecklare som är inloggade i administratören för din butik kan skapa och testa frågor med faktiska katalogdata. Om du vill veta mer går du till [GraphQL - översikt](https://developer.adobe.com/commerce/webapi/graphql/) i [!DNL Live Search] dokumentation för utvecklare. |
| [Inställningar](settings.md) | Bestäm hur prisfaktavärden grupperas efter prisintervall i butiken och ställ in indexeringsspråket. |

## Ange attribut som sökbara

Om du vill skapa målinriktade resultat ska du granska [sökbar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`). Gör attributen sökbara för att säkerställa relevans om de innehåller innehåll som har en tydlig och koncis betydelse. Undvik att använda attribut som innehåller mindre exakt, lång text, till exempel `description`, som även om sökfunktionen är aktiverad som standard, kan minska precisionen i sökresultaten. Om en person t.ex. söker efter &quot;kortfilmer&quot; och det finns skjortor med en beskrivning som innehåller ordet &quot;kortärmar&quot;, kommer skjortorna att inkluderas i sökresultaten.

Om du vill tillåta att attribut kan sökas igenom utför du följande steg:

1. Gå till Admin **Lager** > *Attribut* > **Produkt**.
1. Välj det attribut som du vill ska vara sökbart, till exempel `color`.
1. Välj **Egenskaper för Storefront** och ange **Använd i sökning** till `yes`.

   ![Arbetsyta](assets/attribute-searchable.png)

[!DNL Live Search] även respekterar [vikt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) för ett produktattribut, enligt Adobe Commerce. Attribut med högre vikt visas högre i sökresultatet.

Följande attribut är alltid sökbara:

* `sku`
* `name`
* `categories`

[Fasetter](facets.md) är produktattribut som definieras i [!DNL Live Search] som ska kunna filtreras. Du kan ange alla filterbara attribut som en aspekt i [!DNL Live Search], men det finns [gränser](boundaries-limits.md) om du vill veta hur många aspekter du kan söka efter samtidigt.

[Synonymer](synonyms.md) är termer som du kan definiera för att hjälpa användarna att hitta rätt produkt. Användare som söker efter byxor kan skriva in &quot;byxor&quot; eller &quot;slacks&quot;. Du kan ställa in synonymer så att de här söktermerna får användarna att se resultatet.

## Konfigurationsinställningar för Commerce

I följande avsnitt beskrivs de Commerce-konfigurationsinställningar som stöds och inte stöds för [!DNL Live Search].

### Konfigurationsvärden som stöds

| Konfigurationsinställning för Commerce | Beskrivning | Stöds av Popover | Stöds av kortet |
|---|---|---|---|
| Stores > Configuration > Catalog > Catalog > Catalog Search > Allow All Products per Page | Om inställt på `Yes`, innehåller `ALL` i kontrollen &quot;Visa per sida&quot;. | Ja. Max 500 produkter | Ja. Max 500 produkter |
| Lagrar > Konfiguration > Katalog > Katalog > Katalogsökning > Minimal frågelängd | Det minsta antalet tecken som tillåts i en katalogsökning. | Ja | Ja |
| Stores > Configuration > Catalog > Catalog > Catalog Search > Products per Page on Grid Allowed Valowed | Anger hur många produkter som visas i stödrastervyn. | Ja | Ja |
| Stores > Configuration > Catalog > Catalog > Catalog Search > Products per Page on Grid Default Value | Anger hur många produkter som visas per sida som standard i stödrastervyn. | Ja. Max 500 produkter | Ja. Max 500 produkter |
| Stores > Configuration > Catalog > Inventory > Display out of Stock Products | Visar produkter som inte finns i lager. | Ja w/ v2.0.4+ | Ja w/ v2.0.4+ |
| Lager > Konfiguration > Valuta > Standardvisningsvaluta | Den primära valuta som används för att visa priser. | Ja w/3.1.0+ | Ja w/3.1.0+ |
| Stores > Configuration > General > Currency Setup > Currency Options > Base Currency Options | Den primära valutan som används för alla onlinebetalningstransaktioner. | Ja | Ja |

Priserna på Widget Product Listing Page och Popover konverteras till standardvisningsvalutan med de konfigurerade valutakurserna.

### Konfigurationsvärden som inte stöds

| Konfigurationsinställning för Commerce | Beskrivning | Anteckningar |
|---|---|---|
| Stores > Configuration > Catalog > Storefront > List Mode | Bestämmer formatet för sökresultatlistan. | Återger korrekt, men händelser skickas inte för vissa sidinteraktioner |
| Stores > Configuration > Catalog > Catalog > Catalog Search > Maximum Query Length | Det maximala antalet tecken som tillåts i en katalogsökning. | Inte implementerad; Search Services kan innehålla upp till 255 tecken |
| Configuration > Sales > Tax > Price Display Settings > Display Product Prices in Catalog | Avgör om produktpriser som publiceras i katalogen innehåller eller exkluderar moms eller visar två versioner av priset; den ena med och den andra utan moms |  |
| Stores > Configuration > Catalog > Storefront > Product Listing Sort By | Bestämmer sorteringsordningen i sökresultatlistan. | Gäller inte [!DNL Live Search] [Sidwidget för produktlista](plp-styling.md) |

### Sökvillkor

[!DNL Live Search] supports [omdirigering av söktermer](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) på implementeringar där Adobe Commerce hanterar routningen, som Luma och andra PHP-baserade teman.
