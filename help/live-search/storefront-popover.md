---
title: Storefront Poposer
description: Direktsökningen visar dynamiskt föreslagna produkter och miniatyrbilder.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Storefront Poposer

När [!DNL Live Search] är [installerat](install.md), visas en pover i butiken när kunderna skriver i [Sök](https://docs.magento.com/user-guide/catalog/search-quick.html) box. För varje tecken som skrivs uppdateras poseraren med förslag på produkter och miniatyrbilder av det översta sökresultatet.

[!DNL Live Search] returnerar resultat för en fråga med minst två tecken. För en partiell matchning är det maximala antalet tecken per ord 20. Det går inte att konfigurera antalet tecken i en sökfråga.

>[!NOTE]
>
>The [!DNL Live Search] storefront poser är bara tillgängligt för butiker som använder *Luma* eller ett anpassat tema som baseras på *Luma*. The *Luma* temat ingår i [!DNL Commerce] exempeldata. Pekaren stöder inte *Tom* tema. Se [Arbeta med ett ändrat tema](#working-with-modified-theme) för mer information.

## Sökbara attribut

Om du vill skapa målinriktade resultat ska du granska [sökbar](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) produktattribut. Gör attributen sökbara för att säkerställa relevans om de innehåller innehåll som har en tydlig och koncis betydelse. Undvik att använda attribut som innehåller mindre exakt, lång text, t.ex. `description`, som även om sökfunktionen är aktiverad som standard, kan minska precisionen i sökresultaten. Om en person t.ex. söker efter &quot;kortfilmer&quot; och det finns skjortor med en beskrivning som innehåller ordet &quot;kortärmar&quot;, kommer skjortorna att inkluderas i sökresultaten.

Följande attribut är alltid sökbara:

* `sku`
* `name`
* `categories`

![Live Search poser](assets/storefront-search-as-you-type.png)
