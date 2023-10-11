---
title: "[!DNL Storefront Popover]"
description: "Den [!DNL Live Search storefront popover] returnerar dynamiskt föreslagna produkter och miniatyrbilder."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: bf44c04771069fe6502257b35517c62a5161f81b
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# [!DNL Storefront Popover]

När [!DNL Live Search] är [installerat](install.md), a [!DNL popover] visas i butiken när kunderna skriver i [Sök](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) box. För varje tecken som skrivs visas [!DNL popover] uppdateras med förslag på produkter och miniatyrbilder av de bästa sökresultaten.

[!DNL Live Search] returnerar resultat för en fråga med minst två tecken. För en partiell matchning är det maximala antalet tecken per ord 20. Det går inte att konfigurera antalet tecken i en sökfråga.

Som standard [!DNL Live Search] supports [omdirigering av söktermer](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## Sökbara attribut

Om du vill skapa målinriktade resultat ska du granska [sökbar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`). Gör attributen sökbara för att säkerställa relevans om de innehåller innehåll som har en tydlig och koncis betydelse. Undvik att använda attribut som innehåller mindre exakt, lång text, till exempel `description`, som även om sökfunktionen är aktiverad som standard, kan minska precisionen i sökresultaten. Om en person t.ex. söker efter &quot;kortfilmer&quot; och det finns skjortor med en beskrivning som innehåller ordet &quot;kortärmar&quot;, kommer skjortorna att inkluderas i sökresultaten.

Följande attribut är alltid sökbara:

* `sku`
* `name`
* `categories`

## [!DNL Popover] sidstorlek

Sidstorleken för [!DNL popover] anger hur många rader med automatiskt slutförda produkter som kan returneras. Tidigare var sidstorleken hårdkodad som sex rader. Men `page_size` värdet är nu en inställning som kan konfigureras från *Administratör*. Under installationen av Live Search `page_size` värdet ändras till det aktuella värdet för [Katalogsökning](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` inställning.

Som standard är värdet för Katalogsökning - Gräns för automatisk komplettering satt till åtta rader (eller rader). Ändra sidstorleken för [!DNL popover]gör du följande:

1. På *Administratör* sidebar, gå till **Lager** > Inställningar > **Konfiguration**.
1. Expandera på den vänstra panelen **Katalog** och välja **Katalog** i listan med inställningar.
1. Expandera *Katalogsökning* -avsnitt.
1. Ange **Gräns för automatisk komplettering** till antalet rader som du vill tillåta i [!DNL popover].
1. När du är klar klickar du på **Spara konfiguration**.

## Katalogtjänst

The [Katalogtjänst för Adobe Commerce](../catalog-service/overview.md) tillägg innehåller omfattande katalogdata för visningsmodeller för att snabbt och fullständigt återge produktrelaterade butiksupplevelser. Katalogtjänsten kan användas tillsammans med Live Search för att tillhandahålla funktioner som för närvarande inte stöds av ANE-tillägget:

* Färgrutor
* Utökade attribut
* Annan produktinformation kan hämtas in

Handlare kan anpassa och utöka widgetar eller butikselement med hjälp av katalogtjänsten, men detta är inte tillåtet för Adobe supportteam.

## Headless-implementationer

För dem med headless-implementeringar är det möjligt att installera Live Search-drivrutinen med en [npm-paket](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## Begränsningar

* The [!DNL Live Search] [!DNL storefront popover] är bara tillgängligt för butiker som använder *Luma* eller ett anpassat tema som baseras på *Luma*. Brödraperier på sökresultatsidan kommer inte att ha *Luma* stil.
* The [!DNL popover] stöder inte *Tom* tema. Se [Stilar [!DNL Popover] Element](storefront-popover-styling.md) om du vill veta mer.
* The [!DNL popover] stöds inte i snabbbeställningsformuläret.
* Önsklistorna och produktjämförelserna stöds inte.
