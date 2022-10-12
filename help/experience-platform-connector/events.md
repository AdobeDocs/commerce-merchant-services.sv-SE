---
title: Händelser
description: Lär dig vilka data varje händelse hämtar.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: aaaab3d11c15a69856711a41e889a5d0208aedd2
workflow-type: tm+mt
source-wordcount: '1977'
ht-degree: 0%

---

# Experience Platform Connector Events

Nedan visas de Commerce-händelser som är tillgängliga när du installerar anslutningstillägget för Experience Platform. De data som dessa händelser samlar in skickas till Adobe Experience Platform. Du kan också skapa [anpassade händelser](custom-events.md) för att samla in ytterligare uppgifter som inte lämnats ut.

Förutom de data som följande händelser samlar in får du också [övriga uppgifter](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) från Adobe Experience Platform Web SDK.

>[!NOTE]
>
>Alla butikshändelser innehåller `personID` -fält, som är en unik identifierare för personen.

## addToCart

Utlöses när en produkt läggs till i varukorgen eller när kvantiteten av en produkt i varukorgen ökas.

### XDM-händelsenamn

`commerce.productListAdds`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `productListAdds` | Anger om en produkt har lagts till i en kundvagn. Värdet för `1` anger att en produkt har lagts till. |
| `productListItems` | En array med produkter som lagts till i kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `quantity` | Antal produktenheter som lagts till i kundvagnen |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) produktvaluta |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |
| `cartID` | Det unika ID som identifierar kundens kundvagn |

## openCart

Utlöses när en ny kundvagn skapas, det vill säga när en produkt läggs till i en tom kundvagn.

### XDM-händelsenamn

`commerce.productListOpens`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `productListOpens` | Anger om en vagn skapades. Värdet för `1` anger att en kundvagn skapades. |
| `productListItems` | En array med produkter som lagts till i kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `quantity` | Antal produktenheter som lagts till i kundvagnen |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) produktvaluta |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |
| `cartID` | Det unika ID som identifierar kundens kundvagn |

## removeFromCart

Utlöses varje gång en produkt tas bort eller varje gång som kvantiteten av en produkt i vagnen minskas.

### XDM-händelsenamn

`commerce.productListRemovals`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `productListRemovals` | Anger om en produkt har tagits bort från vagnen. Värdet för `1` anger att en produkt har tagits bort från varukorgen. |
| `productListItems` | En array med produkter som tagits bort från kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `quantity` | Antal produktenheter som tagits bort från vagnen |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) produktvaluta |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |
| `cartID` | Det unika ID som identifierar kundens kundvagn |

## shoppingCartView

Utlöses när en kundvagnssida läses in.

### XDM-händelsenamn

`commerce.productListViews`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `productListViews` | Anger om en produktlista har visats |
| `productListItems` | En uppsättning produkter i kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `quantity` | Antalet produktenheter i kundvagnen |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) produktvaluta |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |
| `cartID` | Det unika ID som identifierar kundens kundvagn |

## pageView

Utlöses när någon sida läses in.

### XDM-händelsenamn

`web.webpagedetails.pageViews`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `pageViews` | Anger om en sida har lästs in. A `value` av `1` anger att sidan lästes in. |

## productPageView

Utlöses när någon produktsida läses in.

### XDM-händelsenamn

`commerce.productViews`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `productViews` | Anger om produkten visades |
| `productListItems` | En uppsättning produkter i kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) produktvaluta |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |

## startCheckout

Utlöses när kunden klickar på en utcheckningsknapp.

### XDM-händelsenamn

`commerce.checkouts`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `checkouts` | Anger om en åtgärd inträffade under utcheckningsprocessen |
| `productListItems` | En uppsättning produkter i kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `quantity` | Antalet produktenheter i kundvagnen |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) produktvaluta |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |
| `cartID` | Det unika ID som identifierar kundens kundvagn |

## completeCheckout

Utlöses när kunden lägger en order.

### XDM-händelsenamn

`commerce.order`

### Typ

Storefront

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `purchases` | Anger om en order har godkänts |
| `order` | Innehåller information om den placerade ordern för en eller flera produkter |
| `purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `orderType` | Anger den typ av order som har lagts, till exempel Checka ut eller Direktköp |
| `payments` | Listan över betalningar för den här ordern |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för denna betalningsartikel. Till exempel: `USD` eller `EUR`. |
| `paymentAmount` | Betalningens värde |
| `paymentType` | Betalningsmetoden för den här ordern. Alternativen är: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | Den unika transaktionsidentifieraren för den här betalningsartikeln |
| `shipping` | Leveransinformation för en eller flera produkter. |
| `shippingMethod` | Leveranssätt som kunden väljer, t.ex. standardleverans, snabbare leverans, upphämtning i butik osv. |
| `shippingAmount` | Den totala leveranskostnaden för artiklarna i vagnen |
| `promotionID` | Unik identifierare för kampanjen, om sådan finns |
| `productListItems` | En uppsättning produkter i kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `quantity` | Antalet produktenheter i kundvagnen |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för ordersummor. |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |

## signIn

Utlöses när en kund försöker logga in.

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

### XDM-händelsenamn

`userAccount.login`

### Typ

Profil

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `eventType` | Den primära händelsetypen för den här tidsserieposten, till exempel: `userAccount.login` |
| `person` | En enskild aktör, kontakt eller ägare |
| `accountID` | Hämtar användar-ID:t |
| `personalEmailID` | Anger den unika identifieraren för den personliga e-postadressen |
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `login` | Anger om en besökare försökte logga in |

## signOut

Utlöses när en kund försöker logga ut.

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

### XDM-händelsenamn

`userAccount.logout`

### Typ

Profil

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `eventType` | Den primära händelsetypen för den här tidsserieposten, till exempel: `userAccount.logout` |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `logout` | Anger om en besökare försökte logga ut |

## createAccount

Utlöses när en kund försöker skapa ett konto.

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

### XDM-händelsenamn

`userAccount.createProfile`

### Typ

Profil

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `eventType` | Den primära händelsetypen för den här tidsserieposten, till exempel: `account.createProfile` |
| `person` | En enskild aktör, kontakt eller ägare |
| `accountID` | Hämtar användar-ID:t |
| `accountType` | Hämtar typ av användarkonto, t.ex. `Personal` eller `Company`, om tillämpligt |
| `personalEmailID` | Anger den unika identifieraren för den personliga e-postadressen |
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `createProfile` | Anger om en användare har skapat en kontoprofil |

## editAccount

Utlöses när en kund försöker redigera ett konto.

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

### XDM-händelsenamn

`userAccount.updateProfile`

### Typ

Profil

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `eventType` | Den primära händelsetypen för den här tidsserieposten, till exempel: `account.updateProfile` |
| `person` | En enskild aktör, kontakt eller ägare |
| `accountID` | Hämtar användar-ID:t |
| `accountType` | Hämtar typ av användarkonto, t.ex. `Personal` eller `Company`, om tillämpligt |
| `personalEmailID` | Anger den unika identifieraren för den personliga e-postadressen |
| `personalEmail` | Anger den personliga e-postadressen |
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `updateProfile` | Anger om en användare har uppdaterat sin kontoprofil |

## searchRequestSent

Utlöses av följande händelser i porten &quot;search as you type&quot;:

- Tryck på Retur
- Klicka _Visa alla_

Utlöses av följande händelser på sökresultatsidor:

- Markera ett filter
- Ändra sorteringsordningen (_Sortera efter_)
- Ändra sorteringsriktning (stigande eller fallande)
- Ändra antalet resultat per sida (_Visa antal per sida_)
- Navigera till nästa sida
- Navigera till föregående sida
- Navigera till en annan sida

>[!NOTE]
>
>Sökhändelser stöds inte på Adobe Commerce Enterprise Edition med B2B-modulen installerad.

### XDM-händelsenamn

`searchRequest`

### Typ

Sök

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `searchRequest` | Anger om en sökbegäran har skickats |
| `filter` | Anger om några filter har använts för att begränsa sökresultaten |
| `attribute` (filter) | Faktorn för ett objekt som används för att avgöra om det ska tas med i sökresultaten |
| `value` | Attributvärden som används för att bestämma vilka objekt som ska tas med i sökresultaten |
| `isRange` | När true anger värden slutpunkter i ett godkänt värdeintervall |
| `sort` | Anger hur sökresultat ska sorteras |
| `attribute` (sortera) | Ett attribut som används för att sortera objekt i sökresultat |
| `order` | Den ordning i vilken sökresultaten ska returneras |
| `query` | De sökbara termerna |

## searchResponseReceived

Utlöses när Live Search returnerar resultat för&quot;sökningen när du skriver&quot;-porten eller sökresultatsidan.

>[!NOTE]
>
>Sökhändelser stöds inte på Adobe Commerce Enterprise Edition med B2B-modulen installerad.

### XDM-händelsenamn

`searchResponse`

### Typ

Sök

### Insamlade data

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `searchResponse` | Anger om ett söksvar har tagits emot |
| `suggestions` | En matris med strängar som innehåller namnen på de produkter och kategorier som finns i katalogen och som liknar sökfrågan |
| `numberOfResults` | Antal returnerade produkter |
| `productListItems` | En uppsättning produkter i kundvagnen. Innehåller `SKU`(lagerhållningsenhet) och `name` av produkten (visningsnamn eller läsbart namn). |
