---
title: Händelser
description: Lär dig vilka data varje händelse hämtar.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 1484a465f3ce5b5578a7c5cf3f5f3b7d68d69c41
workflow-type: tm+mt
source-wordcount: '4605'
ht-degree: 0%

---

# Experience Platform Connector Events

Nedan visas de Commerce-händelser som är tillgängliga när du installerar anslutningstillägget för Experience Platform. De data som dessa händelser samlar in skickas till Adobe Experience Platform. Du kan också skapa [anpassade händelser](custom-events.md) för att samla in ytterligare uppgifter som inte lämnats ut.

Förutom de data som följande händelser samlar in får du också [övriga uppgifter](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) från Adobe Experience Platform Web SDK.

## Storefront-händelser

Affärshändelserna samlar in anonyma beteendedata från era kunder när de surfar på er webbplats. Ni kan använda de data som dessa event samlar in för att skapa kampanjer och kampanjer som riktar sig till en viss uppsättning kunder. Händelsedata för Storefront inkluderar endast enkla och konfigurerbara produkter.

>[!NOTE]
>
>Alla butikshändelser innehåller [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) -fält, som innehåller kundens e-postadress, när den är tillgänglig, och ECID. Om du inkluderar dessa profildata i varje händelse behöver du inte importera något separat användarkonto från Adobe Commerce.

### addToCart

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en produkt läggs till i varukorgen eller när kvantiteten av en produkt i varukorgen ökas. | `commerce.productListAdds` |

#### Data insamlade från addToCart

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

### openCart

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en ny kundvagn skapas, det vill säga när en produkt läggs till i en tom kundvagn. | `commerce.productListOpens` |

#### Data som samlats in från openCart

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

### removeFromCart

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses varje gång en produkt tas bort eller varje gång som kvantiteten av en produkt i vagnen minskas. | `commerce.productListRemovals` |

#### Data som samlats in från removeFromCart

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

### shoppingCartView

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kundvagnssida läses in. | `commerce.productListViews` |

#### Data som samlats in från shoppingCartView

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

### pageView

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när någon sida läses in. | `web.webpagedetails.pageViews` |

#### Data som samlats in från pageView

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `pageViews` | Anger om en sida har lästs in. A `value` av `1` anger att sidan lästes in. |

### productPageView

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när någon produktsida läses in. | `commerce.productViews` |

#### Data som samlats in från productPageView

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

### startCheckout

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när kunden klickar på en utcheckningsknapp. | `commerce.checkouts` |

#### Data som samlats in från startCheckout

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

### completeCheckout

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när kunden lägger en order. | `commerce.order` |

#### Data som samlats in från completeCheckout

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
| `personalEmail` | Anger den personliga e-postadressen |
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `productListItems` | En uppsättning produkter i kundvagnen |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `priceTotal` | Det totala priset för produktartikeln |
| `quantity` | Antalet produktenheter i kundvagnen |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för ordersummor. |
| `productImageUrl` | Produktens huvudbild-URL |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |

## Profilhändelser

Profilhändelser innehåller kontoinformation, t.ex. `signIn`, `signOut`, `createAccount`och `editAccount`. Dessa data används för att fylla i viktig kundinformation som behövs för att bättre definiera segment eller genomföra marknadsföringskampanjer, till exempel om ni vill inrikta er på kunder som bor i New York.

### signIn

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund försöker logga in. | `userAccount.login` |

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

#### Data som samlats in från signIn

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `person` | En enskild aktör, kontakt eller ägare |
| `accountID` | Hämtar användar-ID:t |
| `accountType` | Hämtar typ av användarkonto, t.ex. `Personal` eller `Company`, om tillämpligt |
| `personalEmailID` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `personalEmail` | Hämtar kontaktinformation - ett e-postmeddelande och tillhörande information |
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `login` | Anger om en besökare försökte logga in |

### signOut

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund försöker logga ut. | `userAccount.logout` |

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

#### Data som samlats in från signOut

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `logout` | Anger om en besökare försökte logga ut |

### createAccount

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund försöker skapa ett konto. | `userAccount.createProfile` |

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

#### Data som samlats in från createAccount

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `person` | En enskild aktör, kontakt eller ägare |
| `accountID` | Hämtar användar-ID:t |
| `accountType` | Hämtar typ av användarkonto, t.ex. `Personal` eller `Company`, om tillämpligt |
| `personalEmailID` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `personalEmail` | Hämtar kontaktinformation - ett e-postmeddelande och tillhörande information |
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `createProfile` | Anger om en användare har skapat en kontoprofil |

### editAccount

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund försöker redigera ett konto. | `userAccount.updateProfile` |

>[!NOTE]
>
> Den här händelsen utlöses när ett försök görs att utföra den specifika åtgärden. Det indikerar inte att åtgärden lyckades.

#### Data som samlats in från editAccount

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `person` | En enskild aktör, kontakt eller ägare |
| `accountID` | Hämtar användar-ID:t |
| `accountType` | Hämtar typ av användarkonto, t.ex. `Personal` eller `Company`, om tillämpligt |
| `personalEmailID` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `personalEmail` | Hämtar kontaktinformation - ett e-postmeddelande och tillhörande information |
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar |
| `updateProfile` | Anger om en användare har uppdaterat sin kontoprofil |

## Sök efter händelser

Sökhändelserna innehåller data som är relevanta för kundens avsikter. Insikt i en köpares avsikter hjälper handlarna att se hur kunderna letar efter artiklar, vad de klickar på och slutligen köper eller överger. Ett exempel på hur ni kan använda dessa data är om ni vill rikta er till befintliga kunder som söker efter den bästa produkten, men aldrig köper produkten.

Använd `uniqueIdentifier` fält hittades i båda `searchRequestSent` och `searchResponseReceived` händelser som korsrefererar en sökbegäran till motsvarande söksvar.

### searchRequestSent

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses av följande händelser i porten &quot;search as you type&quot;:<br><br>Tryck på Retur, klicka _Visa alla_<br><br> Utlöses av följande händelser på sökresultatsidor:<br><br>Välj ett filter, Ändra sorteringsordningen (_Sortera efter_), Ändra sorteringsriktning (stigande eller fallande), Ändra antalet resultat per sida (_Visa antal per sida_), Navigera till nästa sida, Navigera till föregående sida, Navigera till en annan sida | `searchRequest` |

>[!NOTE]
>
>Sökhändelser stöds inte på Adobe Commerce Enterprise Edition med B2B-tillägget installerat.

#### Data som samlats in från searchRequestSent

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `searchRequest` | Anger om en sökbegäran har skickats |
| `id` | Unikt ID för den här särskilda sökbegäran |
| `filter` | Anger om några filter har använts för att begränsa sökresultaten |
| `attribute` (filter) | Faktorn för ett objekt som används för att avgöra om det ska tas med i sökresultaten |
| `value` | Attributvärden som används för att bestämma vilka objekt som ska tas med i sökresultaten |
| `isRange` | När true anger värden slutpunkter i ett godkänt värdeintervall |
| `sort` | Anger hur sökresultat ska sorteras |
| `attribute` (sortera) | Ett attribut som används för att sortera objekt i sökresultat |
| `order` | Den ordning i vilken sökresultaten ska returneras |
| `query` | De sökbara termerna |

### searchResponseReceived

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när Live Search returnerar resultat för&quot;sökningen när du skriver&quot;-porten eller sökresultatsidan. | `searchResponse` |

>[!NOTE]
>
>Sökhändelser stöds inte på Adobe Commerce Enterprise Edition med B2B-tillägget installerat.

#### Data som samlats in från searchResponseReceived

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `searchResponse` | Anger om ett söksvar har tagits emot |
| `id` | Unikt ID för det här speciella söksvaret |
| `suggestions` | En matris med strängar som innehåller namnen på de produkter och kategorier som finns i katalogen och som liknar sökfrågan |
| `numberOfResults` | Antal returnerade produkter |
| `productListItems` | En uppsättning produkter i kundvagnen. |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `productImageUrl` | Produktens huvudbild-URL |

## B2B-event

![B2B för Adobe Commerce](../assets/b2b.svg) För B2B-handlare måste du [installera](install.md#install-the-b2b-extension) den `experience-platform-connector-b2b` för att aktivera dessa händelser.

B2B-händelser innehåller [rekvisitionslista](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) information, t.ex. om en rekvisitionslista skapades, lades till eller togs bort från. Genom att spåra händelser som är specifika för rekvisitionslistor kan ni se vilka produkter era kunder köper ofta och skapa kampanjer baserade på dessa data.

### createRequisitionList

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund skapar en ny rekvisitionslista. | `commerce.requisitionListOpens` |

#### Data som samlats in från createRequisitionList

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `requisitionList` | Egenskaperna för den rekvisitionslista som skapats av kunden |
| `ID` | Unik identifierare för rekvisitionslistan |
| `name` | Namn på den rekvisitionslista som har angetts av kunden |
| `description` | Beskrivning av rekvisitionslistan som anges av kunden |

### addToRequisitionList

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund lägger till en produkt i en befintlig anbudslista eller när en ny lista skapas. | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` stöds inte på kategorivysidor eller för konfigurerbara produkter. Det stöds på produktvysidor och för enkla produkter.

#### Data som samlats in från addToRequisitionList

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `requisitionList` | Egenskaperna för den rekvisitionslista som skapats av kunden |
| `ID` | Unik identifierare för rekvisitionslistan |
| `name` | Namn på den rekvisitionslista som har angetts av kunden |
| `description` | Beskrivning av rekvisitionslistan som anges av kunden |
| `productListItems` | En array med produkter som har lagts till i rekvisitionslistan |
| `name` | Produktens visningsnamn eller läsbara namn |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `quantity` | Antal tillagda produktenheter |
| `priceTotal` | Det totala priset för produktartikeln |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för denna betalningsartikel |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |

### removeFromRequisitionList

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund tar bort en produkt från en rekvisitionslista. | `commerce.requisitionListRemovals` |

#### Data som samlats in från removeFromRequisitionList

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `requisitionList` | Egenskaperna för den rekvisitionslista som skapats av kunden |
| `ID` | Unik identifierare för rekvisitionslistan |
| `name` | Namn på den rekvisitionslista som har angetts av kunden |
| `description` | Beskrivning av rekvisitionslistan som anges av kunden |
| `productListItems` | En array med produkter som har lagts till i rekvisitionslistan |
| `name` | Produktens visningsnamn eller läsbara namn |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `quantity` | Antal tillagda produktenheter |
| `priceTotal` | Det totala priset för produktartikeln |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för denna betalningsartikel |
| `selectedOptions` | Fält som används för en konfigurerbar produkt. `attribute` identifierar ett attribut för den konfigurerbara produkten, som `size` eller `color` och `value` identifierar värdet på attributet som `small` eller `black`. |

## Back office-händelser

Back office-händelserna innehåller information om status för en beställning, till exempel om en beställning har placerats, annullerats, återbetalats, skickats eller slutförts. De data som dessa händelser på serversidan samlar in visar en 360-vy över kundordern. Den här vyn hjälper handlare att målinrikta eller analysera hela orderstatusen bättre när de utvecklar marknadsföringskampanjer. Du kan till exempel upptäcka trender i vissa produktkategorier som fungerar bra vid olika tidpunkter på året. Till exempel vinterkläder som säljer bättre under längre månader eller vissa produktfärger som kunderna är intresserade av under årens lopp. Dessutom kan orderstatusdata hjälpa er att beräkna kundens livslängdvärde genom att förstå en kunds benägenhet att konvertera baserat på tidigare order.

>[!NOTE]
>
>Alla back office-händelser inkluderar [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) som anger kundens e-postadress. Om du inkluderar dessa profildata i varje händelse behöver du inte importera något separat användarkonto från Adobe Commerce.

### orderPlaced

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund gör en beställning. | `commerce.backofficeOrderPlaced` |

#### Data som samlats in från orderPlacerade

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `address` | Den tekniska adressen, till exempel `name@domain.com` enligt den vanliga definitionen i RFC2822 och senare standarder |
| `productListItems` | En array med produkter i ordningen |
| `id` | Identifierare för radartikel för den här produktposten. Själva produkten identifieras via `product` fält. |
| `name` | Produktens visningsnamn eller läsbara namn |
| `SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `quantity` | Antalet produktenheter i kundvagnen |
| `priceTotal` | Det totala priset för produktartikeln |
| `discountAmount` | Anger vilket rabattbelopp som används |
| `order` | Innehåller information om ordern |
| `purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt |
| `priceTotal` | Det totala priset för den här ordern efter att alla rabatter och skatter har tillämpats |
| `currencyCode` | ISO 4217-valutakoden som används för ordersummor |
| `purchaseOrderNumber` | Unik identifierare som tilldelats av köparen för detta inköp eller kontrakt |
| `payments` | Listan över betalningar för den här ordern |
| `paymentType` | Betalningsmetoden för den här ordern. Uppräknade, anpassade värden tillåts. |
| `currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för denna betalningsartikel |
| `paymentAmount` | Betalningens värde |
| `taxAmount` | Det skattebelopp som köparen betalar som en del av den slutliga betalningen |
| `createdDate` | Tid och datum då en ny order skapas i handelssystemet. Till exempel: `2022-10-15T20:20:39+00:00` |
| `shipping` | Leveransinformation för en eller flera produkter |
| `shippingMethod` | Leveranssätt som kunden väljer, t.ex. standardleverans, snabbare leverans, upphämtning i butik osv. |
| `shippingAmount` | Det belopp som kunden måste betala för frakt. |
| `address` | Fysisk leveransadress |
| `street1` | Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn |
| `street2` | Ytterligare fält för gatuinformation |
| `city` | Namnet på staden |
| `state` | Namnet på läget. Det här är ett frihandsfält. |
| `postalCode` | Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret. |
| `country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `billingAddress` | Betalningsadress |
| `street1` | Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn |
| `street2` | Ytterligare fält för gatuinformation |
| `city` | Namnet på staden |
| `state` | Namnet på läget. Det här är ett frihandsfält. |
| `postalCode` | Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret. |
| `country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `personalEmail` | En personlig e-postadress |
| `address` | Den tekniska adressen, till exempel&quot;name@domain.com&quot;, såsom den är vanlig i RFC2822 och senare standarder |

### orderItemsShipped

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en order skickas. | `commerce.backofficeOrderItemsShipped` |

#### Data insamlade från orderItemsShipped

I följande tabell beskrivs de data som samlats in för den här händelsen.
|Fält|Beskrivning| |—|—| |`address`|Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder| |`productListItems`|En array med produkter i ordningen| |`id`|ID för radartikel för den här produktposten. Själva produkten identifieras via `product` fält.| |`name`|Produktens visningsnamn eller läsbara namn| |`SKU`|Lagringsenhet. Unik identifierare för produkten.| |`quantity`|Antal produktenheter i kundvagnen| |`priceTotal`|Det totala priset för produktartikeln| |`discountAmount`|Anger vilket rabattbelopp som används| |`order`|Innehåller information om beställningen| |`purchaseID`|Unik identifierare tilldelad av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt| |`priceTotal`|Orderns totalpris efter att alla rabatter och skatter har tillämpats| |`currencyCode`|ISO 4217-valutakoden som används för ordersummor| |`purchaseOrderNumber`|Unik identifierare tilldelad av köparen för detta inköp eller kontrakt| |`payments`|Lista över betalningar för den här ordern| |`paymentType`|Betalningsmetoden för den här ordern. Uppräknade, anpassade värden tillåts.| |`currencyCode`|Den [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för denna betalningsartikel| |`paymentAmount`|Betalningens värde| |`lastUpdatedDate`|Den tidpunkt då en viss orderpost senast uppdaterades i handelssystemet| |`shipping`|Leveransinformation för en eller flera produkter| |`shippingMethod`|Leveranssätt som valts av kunden, t.ex. standardleverans, snabbare leverans, upphämtning i butik o.s.v.| |`trackingNumber`|Spårningsnumret som fraktfirman angett för en orderartikelleverans| |`trackingURL`|URL:en som spårar leveransstatus för en orderartikel| |`shipDate`|Datumet då en eller flera artiklar från en order skickas| |`address`|Fysisk leveransadress| |`street1`|Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn| |`street2`|Ytterligare fält för gatuminivåinformation| |`city`|Namnet på staden| |`state`|Namnet på tillståndet. Det här är ett frihandsfält.| |`postalCode`|Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret.| |`country`|Namnet på det område som administreras av regeringen. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst.| |`shippingAmount`|Det belopp som kunden måste betala för frakt.| |`billingAddress`|Betalningsadress| |`street1`|Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn| |`street2`|Ytterligare fält för gatuminivåinformation| |`city`|Namnet på staden| |`state`|Namnet på tillståndet. Det här är ett frihandsfält.| |`postalCode`|Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret.| |`country`|Namnet på det område som administreras av regeringen. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst.| |`personalEmail`|En personlig e-postadress| |`address`|Den tekniska adressen, t.ex. &quot;name@domain.com&quot;, såsom den är definierad i RFC2822 och senare standarder|

### orderCanceled

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund annullerar en order. | `commerce.backofficeOrderCancelled` |

#### Data insamlade från orderAvbrutna

I följande tabell beskrivs de data som samlats in för den här händelsen.
|Fält|Beskrivning| |—|—| |`address`|Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder| |`productListItems`|En array med produkter i ordningen| |`id`|ID för radartikel för den här produktposten. Själva produkten identifieras via `product` fält.| |`name`|Produktens visningsnamn eller läsbara namn| |`SKU`|Lagringsenhet. Unik identifierare för produkten.| |`quantity`|Antal produktenheter i kundvagnen| |`priceTotal`|Det totala priset för produktartikeln| |`discountAmount`|Anger vilket rabattbelopp som används| |`order`|Innehåller information om beställningen| |`purchaseID`|Unik identifierare tilldelad av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt| |`purchaseOrderNumber`|Unik identifierare tilldelad av köparen för detta inköp eller kontrakt| |`cancelDate`|Datum och tid när en kund annullerar en order| |`lastUpdatedDate`|Den tidpunkt då en viss orderpost senast uppdaterades i handelssystemet| |`personalEmail`|En personlig e-postadress| |`address`|Den tekniska adressen, t.ex. &quot;name@domain.com&quot;, såsom den är definierad i RFC2822 och senare standarder|

### creditMemoIssued

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund returnerar ett objekt i en order. | `commerce.backofficeCreditMemoIssued` |

#### Data som samlats in från creditMemoIssued

I följande tabell beskrivs de data som samlats in för den här händelsen.
|Fält|Beskrivning| |—|—| |`address`|Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder| |`productListItems`|En array med produkter i ordningen| |`id`|ID för radartikel för den här produktposten. Själva produkten identifieras via `product` fält.| |`name`|Produktens visningsnamn eller läsbara namn| |`SKU`|Lagringsenhet. Unik identifierare för produkten.| |`quantity`|Antal produktenheter i kundvagnen| |`priceTotal`|Det totala priset för produktartikeln| |`discountAmount`|Anger vilket rabattbelopp som används| |`order`|Innehåller information om beställningen| |`purchaseID`|Unik identifierare tilldelad av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt| |`purchaseOrderNumber`|Unik identifierare tilldelad av köparen för detta inköp eller kontrakt| |`lastUpdatedDate`|Den tidpunkt då en viss orderpost senast uppdaterades i handelssystemet| |`personalEmail`|En personlig e-postadress| |`address`|Den tekniska adressen, t.ex. &quot;name@domain.com&quot;, såsom den är definierad i RFC2822 och senare standarder|

### orderShiEquipmentCompleted

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund returnerar ett objekt i en order. | `commerce.backofficeOrderShipmentCompleted` |

#### Data som samlats in från orderShiEquipmentCompleted

I följande tabell beskrivs de data som samlats in för den här händelsen.
|Fält|Beskrivning| |—|—| |`address`|Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder| |`productListItems`|En array med produkter i ordningen| |`id`|ID för radartikel för den här produktposten. Själva produkten identifieras via `product` fält.| |`name`|Produktens visningsnamn eller läsbara namn| |`SKU`|Lagringsenhet. Unik identifierare för produkten.| |`quantity`|Antal produktenheter i kundvagnen| |`priceTotal`|Det totala priset för produktartikeln| |`discountAmount`|Anger vilket rabattbelopp som används| |`order`|Innehåller information om beställningen| |`purchaseID`|Unik identifierare tilldelad av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt| |`priceTotal`|Orderns totalpris efter att alla rabatter och skatter har tillämpats| |`currencyCode`|ISO 4217-valutakoden som används för ordersummor| |`purchaseOrderNumber`|Unik identifierare tilldelad av köparen för detta inköp eller kontrakt| |`taxAmount`|Det skattebelopp som köparen betalar som en del av den slutliga betalningen.| |`createdDate`|Tid och datum då en ny order skapas i handelssystemet. Till exempel: `2022-10-15T20:20:39+00:00`| |`payments`|Lista över betalningar för den här ordern| |`paymentType`|Betalningsmetoden för den här ordern. Uppräknade, anpassade värden tillåts.| |`currencyCode`|Den [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används för denna betalningsartikel| |`paymentAmount`|Betalningens värde| |`shipping`|Leveransinformation för en eller flera produkter| |`shippingMethod`|Leveranssätt som valts av kunden, t.ex. standardleverans, snabbare leverans, upphämtning i butik o.s.v.| |`address`|Fysisk leveransadress| |`street1`|Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn| |`street2`|Ytterligare fält för gatuminivåinformation| |`city`|Namnet på staden| |`state`|Namnet på tillståndet. Det här är ett frihandsfält.| |`postalCode`|Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret.| |`country`|Namnet på det område som administreras av regeringen. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst.| |`shippingAmount`|Det belopp som kunden måste betala för frakt.| |`address`|Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder| |`billingAddress`|Betalningsadress| |`street1`|Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn| |`street2`|Ytterligare fält för gatuminivåinformation| |`city`|Namnet på staden| |`state`|Namnet på tillståndet. Det här är ett frihandsfält.| |`postalCode`|Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller uppgifterna endast en del av postnumret.| |`country`|Namnet på det område som administreras av regeringen. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst.| |`personalEmail`|En personlig e-postadress| |`address`|Den tekniska adressen, t.ex. &quot;name@domain.com&quot;, såsom den är definierad i RFC2822 och senare standarder|
