---
title: Storefront Poposer
description: Direktsökningen visar dynamiskt föreslagna produkter och miniatyrbilder.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Storefront Poposer

När [!DNL Live Search] är [installerat](install.md), visas en pover i butiken när kunderna skriver i [Sök](https://docs.magento.com/user-guide/catalog/search-quick.html) box. För varje tecken som skrivs uppdateras poseraren med förslag på produkter och miniatyrbilder av det översta sökresultatet.

[!DNL Live Search] returnerar resultat för en fråga med minst två tecken. För en partiell matchning är det maximala antalet tecken per ord 20. Det går inte att konfigurera antalet tecken i en sökfråga.

>[!NOTE]
>
>The [!DNL Live Search] storefront poser är bara tillgängligt för butiker som använder *Luma* eller ett anpassat tema som baseras på *Luma*. The *Luma* temat ingår i [!DNL Commerce] exempeldata. Pekaren stöder inte *Tom* tema. Se [Formatera popoposerelement](storefront-popover-styling.md) om du vill veta mer.

## Sökbara attribut

Om du vill skapa målinriktade resultat ska du granska [sökbar](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) produktattribut. Gör attributen sökbara för att säkerställa relevans om de innehåller innehåll som har en tydlig och koncis betydelse. Undvik att använda attribut som innehåller mindre exakt, lång text, t.ex. `description`, som även om sökfunktionen är aktiverad som standard, kan minska precisionen i sökresultaten. Om en person t.ex. söker efter &quot;kortfilmer&quot; och det finns skjortor med en beskrivning som innehåller ordet &quot;kortärmar&quot;, kommer skjortorna att inkluderas i sökresultaten.

Följande attribut är alltid sökbara:

* `sku`
* `name`
* `categories`

![Live Search poser](assets/storefront-search-as-you-type.png)

## Visa sidstorlek

Leveransens sidstorlek avgör hur många rader med automatiskt slutförda produkter som kan returneras. Tidigare var sidstorleken hårdkodad som sex rader. Men `page_size` värdet är nu en inställning som kan konfigureras från *Administratör*. Under installationen av Live Search `page_size` värdet ändras till det aktuella värdet för [Katalogsökning](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search) - `Autocomplete Limit` inställning.

Som standard är värdet för Katalogsökning - Gräns för automatisk komplettering satt till åtta rader (eller rader). Så här ändrar du sidstorlek för povern:

1. På *Administratör* sidebar, gå till **Lager** > Inställningar > **Konfiguration**.
1. Expandera på den vänstra panelen **Katalog** och välja **Katalog** i listan med inställningar.
1. Expandera *Katalogsökning* -avsnitt.
1. Ange **Gräns för automatisk komplettering** till antalet rader som du vill tillåta i poverteraren.
1. När du är klar klickar du på **Spara konfiguration**.
