---
title: Händelser
description: Lär dig vilka data varje händelse samlar in.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 9001cd24db0941b7c7edcfd5b10464dc90084fd7
workflow-type: tm+mt
source-wordcount: '6957'
ht-degree: 0%

---

# [!DNL Data Connection] Händelser

Följande visar vilka Commerce-händelser som är tillgängliga när du installerar [!DNL Data Connection] tillägg. De data som dessa händelser samlar in skickas till Adobe Experience Platform. Du kan också skapa [anpassade händelser](custom-events.md) för att samla in ytterligare uppgifter som inte lämnats ut.

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

#### Data som samlats in från addToCart

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.productListAdds` | Anger om en produkt har lagts till i en kundvagn. Värdet för `1` anger att en produkt har lagts till. |
| `commerce.cart.cartID` | Det unika ID som identifierar kundens kundvagn. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### openCart

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en ny kundvagn skapas, det vill säga när en produkt läggs till i en tom kundvagn. | `commerce.productListOpens` |

#### Data som samlats in från openCart

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.productListOpens` | Anger om en vagn skapades. Värdet för `1` anger att en kundvagn skapades. |
| `commerce.cart.cartID` | Det unika ID som identifierar kundens kundvagn. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### removeFromCart

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses varje gång en produkt tas bort eller varje gång som kvantiteten av en produkt i vagnen minskas. | `commerce.productListRemovals` |

#### Data som samlats in från removeFromCart

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.productListRemovals` | Anger om en produkt har tagits bort från kundvagnen. Värdet för `1` anger att en produkt har tagits bort från vagnen. |
| `commerce.cart.cartID` | Det unika ID som identifierar kundens kundvagn. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### shoppingCartView

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kundvagnssida läses in. | `commerce.productListViews` |

#### Data som samlats in från shoppingCartView

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.productListViews` | Anger om en produktlista har visats. |
| `commerce.cart.cartID` | Det unika ID som identifierar kundens kundvagn. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### pageView

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när någon sida läses in. | `web.webpagedetails.pageViews` |

#### Data som samlats in från pageView

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `web.webPageDetails.pageViews` | Anger om en sida har lästs in. A `value` av `1` anger att sidan lästes in. |
| `web.webPageDetails.URL` | Webbsidans normativa eller vanliga URL. Det här kan vara den faktiska URL-adressen som används för att nå sidan, som skulle spelas in med `Web Link`. |
| `web.webPageDetails.name` | Webbsidans normativa namn. Det här namnet är inte nödvändigtvis sidrubriken eller direkt kopplat till sidinnehållet, utan används för att ordna en webbplats sidor i klassificeringssyfte. |
| `web.webReferrer.URL` | URL-adressen till webbsidan som en kund besökte innan han/hon klickade på en länk till webbplatsen. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

### productPageView

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när någon produktsida läses in. | `commerce.productViews` |

#### Data som samlats in från productPageView

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.productViews` | Anger om produkten visades. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### startCheckout

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när kunden klickar på en utcheckningsknapp. | `commerce.checkouts` |

#### Data som samlats in från startCheckout

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.checkouts` | Anger om en åtgärd inträffade under utcheckningsprocessen. |
| `commerce.cart.cartID` | Det unika ID som identifierar kundens kundvagn. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### completeCheckout

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när kunden lägger en order. | `commerce.purchases` |

#### Data som samlats in från completeCheckout

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.purchases` | Anger om en order har godkänts. |
| `commerce.order` | Innehåller information om den placerade beställningen för en eller flera produkter. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.payments` | Listan över betalningar för den här ordern. |
| `commerce.order.payments.paymentTransactionID` | Unik identifierare för den här betalningstransaktionen. |
| `commerce.order.payments.paymentAmount` | Betalningens värde. |
| `commerce.order.payments.paymentType` | Betalningsmetoden för den här ordern. Alternativ: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.order.taxAmount` | Det skattebelopp som köparen betalar som en del av den slutliga betalningen. |
| `commerce.order.discountAmount` | Anger det rabattbelopp som tillämpas på hela ordern. |
| `commerce.order.createdDate` | Tid och datum då en ny order skapas i handelssystemet. Till exempel: `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Leveransinformation för en eller flera produkter. |
| `commerce.shipping.shippingMethod` | Leveranssätt som kunden väljer, t.ex. standardleverans, snabbare leverans, hämtning i butik osv. |
| `commerce.shipping.shippingAmount` | Det belopp som kunden måste betala för frakt. |  | `shipping` | Leveransinformation för en eller flera produkter. |
| `commerce.shipping.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

## Profilhändelser

Profilhändelser innehåller kontoinformation, som `signIn`, `signOut`, `createAccount`och `editAccount`. Dessa data används för att fylla i viktig kundinformation som behövs för att bättre definiera segment eller genomföra marknadsföringskampanjer, till exempel om ni vill inrikta er på kunder som bor i New York.

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
| `person` | En enskild aktör, kontakt eller ägare. |
| `person.accountID` | Hämtar användar-ID:t för kontot. |
| `person.accountType` | Hämtar typ av användarkonto, till exempel `Personal` eller `Company`, om tillämpligt. |
| `person.personalEmailID` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `personalEmail` | Hämtar kontaktinformation - ett e-postmeddelande och tillhörande information. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar. |
| `userAccount.login` | Anger om en besökare försökte logga in. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

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
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar. |
| `userAccount.logout` | Anger om en besökare försökte logga ut. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

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
| `person` | En enskild aktör, kontakt eller ägare. |
| `person.accountID` | Hämtar användar-ID:t för kontot. |
| `person.accountType` | Hämtar typ av användarkonto, till exempel `Personal` eller `Company`, om tillämpligt. |
| `person.personalEmailID` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `personalEmail` | Hämtar kontaktinformation - ett e-postmeddelande och tillhörande information. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar. |
| `userAccount.updateProfile` | Anger om en användare har uppdaterat sin kontoprofil. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

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
| `person` | En enskild aktör, kontakt eller ägare. |
| `person.accountID` | Hämtar användar-ID:t för kontot. |
| `person.accountType` | Hämtar typ av användarkonto, till exempel `Personal` eller `Company`, om tillämpligt. |
| `person.personalEmailID` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `personalEmail` | Hämtar kontaktinformation - ett e-postmeddelande och tillhörande information. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar. |
| `userAccount.updateProfile` | Anger om en användare har uppdaterat sin kontoprofil. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

## Sök efter händelser

Sökhändelserna innehåller data som är relevanta för kundens avsikter. Insikt i en köpares avsikter hjälper handlarna att se hur kunderna letar efter artiklar, vad de klickar på och slutligen köper eller överger. Ett exempel på hur ni kan använda dessa data är om ni vill rikta er till befintliga kunder som söker efter den bästa produkten, men aldrig köper produkten.

Använd `searchRequest.id` och `searchResponse.id` fält i båda `searchRequestSent` och `searchResponseReceived` -händelser för att korsreferera en sökbegäran till motsvarande söksvar.

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
| `searchRequest` | Anger om en sökbegäran har skickats. |
| `searchRequest.id` | Unikt ID för den här särskilda sökbegäran. |
| `searchRequest.value` | Begärans kvantifierbara värde. |
| `siteSearch` | Innehåller information om sökningen. |
| `siteSearch.filter` | Anger om några filter har använts för att begränsa sökresultaten. |
| `siteSearch.filter.attribute` (filter) | Faktablad för ett objekt som används för att avgöra om det ska inkluderas i sökresultaten. |
| `siteSearch.filter.isRange` | När värdet är true anger värden slutpunkter i ett godkänt värdeintervall. |
| `siteSearch.filter.value` | Attributvärde som används för att avgöra vilka objekt som ska tas med i sökresultatet. |
| `siteSearch.sort` | Anger hur sökresultat ska sorteras. |
| `siteSearch.sort.attribute` (sortera) | Ett attribut som används för att sortera objekt i sökresultat. |
| `siteSearch.sort.order` | Den ordning som sökresultaten ska returneras i. |
| `siteSearch.query` | De termer du sökte efter. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

### searchResponseReceived

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när Live Search returnerar resultat för&quot;sökningen när du skriver&quot;-povern eller sökresultatsidan. | `searchResponse` |

>[!NOTE]
>
>Sökhändelser stöds inte på Adobe Commerce Enterprise Edition med B2B-tillägget installerat.

#### Data som samlats in från searchResponseReceived

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `searchResponse` | Anger om ett söksvar har tagits emot. |
| `searchResponse.id` | Unikt ID för det här specifika söksvaret. |
| `searchResponse.value` | Responsens kvantifierbara värde. |
| `siteSearch.numberOfResults` | Antal returnerade produkter. |
| `siteSearch.suggestions` | En array med strängar som innehåller namnen på de produkter och kategorier som finns i katalogen som liknar sökfrågan. |
| `productListItems` | En array med produkter som lagts till i kundvagnen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

## B2B-event

![B2B för Adobe Commerce](../assets/b2b.svg) För B2B-handlare måste du [installera](install.md#install-the-b2b-extension) den `experience-platform-connector-b2b` för att aktivera dessa händelser.

B2B-händelser innehåller [rekvisitionslista](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) information, till exempel om en rekvisitionslista skapades, lades till eller togs bort från. Genom att spåra händelser som är specifika för rekvisitionslistor kan ni se vilka produkter era kunder köper ofta och skapa kampanjer baserade på dessa data.

### createRequisitionList

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund skapar en rekvisitionslista. | `commerce.requisitionListOpens` |

#### Data som samlats in från createRequisitionList

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.requisitionListOpens` | Anger initiering av en ny rekvisitionslista. |
| `commerce.requisitionList` | Egenskaperna för den rekvisitionslista som har skapats av kunden. |
| `commerce.requisitionList.ID` | Unik identifierare för rekvisitionslistan. |
| `commerce.requisitionList.name` | Namn på den rekvisitionslista som har angetts av kunden. |
| `commerce.requisitionList.description` | Beskrivning av rekvisitionslistan som anges av kunden. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

### addToRequisitionList

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund lägger till en produkt i en befintlig rekvisitionslista eller när en lista skapas. | `commerce.requisitionListAdds` |

#### Data som samlats in från addToRequisitionList

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.requisitionListAdds` | Anger tillägg av en eller flera produkter i en rekvisitionslista. |
| `commerce.requisitionList` | Egenskaperna för den rekvisitionslista som har skapats av kunden. |
| `commerce.requisitionList.ID` | Unik identifierare för rekvisitionslistan. |
| `commerce.requisitionList.name` | Namn på den rekvisitionslista som har angetts av kunden. |
| `commerce.requisitionList.description` | Beskrivning av rekvisitionslistan som anges av kunden. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som har lagts till i rekvisitionslistan. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### removeFromRequisitionList

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund tar bort en produkt från en rekvisitionslista. | `commerce.requisitionListRemovals` |

#### Data som samlats in från removeFromRequisitionList

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.requsitionListRemovals` | Anger borttagning av en eller flera produkter från en rekvisitionslista. |
| `commerce.requisitionList` | Egenskaperna för den rekvisitionslista som har skapats av kunden. |
| `commerce.requisitionList.ID` | Unik identifierare för rekvisitionslistan. |
| `commerce.requisitionList.name` | Namn på den rekvisitionslista som har angetts av kunden. |
| `commerce.requisitionList.description` | Beskrivning av rekvisitionslistan som anges av kunden. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `productListItems` | En array med produkter som har lagts till i rekvisitionslistan. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |

### deleteRequisitionList

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund tar bort en rekvisitionslista. | `commerce.requisitionListDeletes` |

#### Data som samlats in från deleteRequisitionList

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.requisitionListDeletes` | Anger att en rekvisitionslista har tagits bort. |
| `commerce.requisitionList` | Egenskaperna för den rekvisitionslista som har skapats av kunden. |
| `commerce.requisitionList.ID` | Unik identifierare för rekvisitionslistan. |
| `commerce.requisitionList.name` | Namn på den rekvisitionslista som har angetts av kunden. |
| `commerce.requisitionList.description` | Beskrivning av rekvisitionslistan som anges av kunden. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |

## Back office-händelser

Back office-händelser innehåller information om status för en order, t.ex. om en order [placerad](#orderplaced), [avbruten](#ordercancelled), [återbetald](#orderitemreturncompleted), [levererad](#ordershipmentcompleted), eller [slutförd](#ordershipmentcompleted). De data som dessa händelser på serversidan samlar in visar en 360-vy över kundordern. Den här vyn hjälper handlare att målinrikta eller analysera hela orderstatusen bättre när de utvecklar marknadsföringskampanjer. Du kan till exempel upptäcka trender i vissa produktkategorier som fungerar bra vid olika tidpunkter på året. Till exempel vinterkläder som säljer bättre under längre månader eller vissa produktfärger som kunderna är intresserade av under årens lopp. Dessutom kan orderstatusdata hjälpa er att beräkna kundens livslängdvärde genom att förstå en kunds benägenhet att konvertera baserat på tidigare order.

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
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.payments` | Listan över betalningar för den här ordern. |
| `commerce.order.payments.paymentTransactionID` | Unik identifierare för den här betalningstransaktionen. |
| `commerce.order.payments.paymentAmount` | Betalningens värde. |
| `commerce.order.payments.paymentType` | Betalningsmetoden för den här ordern. Räknade, anpassade värden tillåtna. |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.order.taxAmount` | Det skattebelopp som köparen betalar som en del av den slutliga betalningen. |
| `commerce.order.discountAmount` | Anger det rabattbelopp som tillämpas på hela ordern. |
| `commerce.order.createdDate` | Tid och datum då en ny order skapas i handelssystemet. Till exempel: `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | ISO 4217-valutakoden som används för ordersummor. |
| `commerce.shipping` | Leveransinformation för en eller flera produkter. |
| `commerce.shipping.shippingMethod` | Leveranssätt som kunden väljer, t.ex. standardleverans, snabbare leverans, hämtning i butik osv. |
| `commerce.shipping.shippingAmount` | Det belopp som kunden måste betala för frakt. |
| `commerce.shipping.currencyCode` | ISO 4217-valutakoden som används för leveranssumman. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `commerce.billing.address` | Betalningsadress. |
| `commerce.billing.address.street1` | Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn |
| `commerce.billing.address.street2` | Ytterligare fält för gatuminivåinformation. |
| `commerce.billing.address.city` | Namnet på staden. |
| `commerce.billing.address.state` | Namnet på läget. Det här är ett frihandsfält. |
| `commerce.billing.address.postalCode` | Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret. |
| `commerce.billing.address.country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter i ordningen. |
| `productListItems.id` | Identifierare för radartikel för den här produktposten. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |
| `productListItems.categories` | Innehåller information om en produkts kategori. |
| `productListItems.categories.id` | Kategorins unika identifierare. |
| `productListItems.categories.name` | Namnet på kategorin. |
| `productListItems.categories.path` | Sökvägen till kategorin. |
| `productListItems.productImageUrl` | Produktens huvudbild-URL. |

### orderFakturerad

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en handlare skickar en faktura för att begära betalning. | `commerce.backofficeOrderInvoiced` |

#### Data insamlade från orderFakturerade

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.priceTotal` | Det totala priset för den här ordern efter att alla rabatter och skatter har tillämpats. |
| `commerce.order.currencyCode` | ISO 4217-valutakoden som används för ordersummor. |
| `commerce.order.purchaseOrderNumber` | Unik identifierare som tilldelats av köparen för detta inköp eller kontrakt. |
| `commerce.order.payments` | Listan över betalningar för den här ordern. |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.order.payments.paymentType` | Betalningsmetoden för den här ordern. Räknade, anpassade värden tillåtna. |
| `commerce.order.payments.paymentAmount` | Betalningens värde. |
| `commerce.shipping` | Leveransinformation för en eller flera produkter. |
| `commerce.shipping.shippingMethod` | Leveranssätt som kunden väljer, t.ex. standardleverans, snabbare leverans, hämtning i butik osv. |
| `commerce.shipping.shippingAmount` | Det belopp som kunden måste betala för frakt. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter i ordningen. |
| `productListItems.id` | Identifierare för radartikel för den här produktposten. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.categories` | Innehåller information om en produkts kategori. |
| `productListItems.categories.id` | Kategorins unika identifierare. |
| `productListItems.categories.name` | Namnet på kategorin. |
| `productListItems.categories.path` | Sökvägen till kategorin. |

### orderItemsShipped

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en order skickas. | `commerce.backofficeOrderItemsShipped` |

#### Data som samlats in från orderItemsShipped

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.payments` | Listan över betalningar för den här ordern. |
| `commerce.order.payments.paymentTransactionID` | Unik identifierare för den här betalningstransaktionen. |
| `commerce.order.payments.paymentAmount` | Betalningens värde. |
| `commerce.order.payments.paymentType` | Betalningsmetoden för den här ordern. Räknade, anpassade värden tillåtna. |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.order.priceTotal` | Det totala priset för den här ordern efter att alla rabatter och skatter har tillämpats. |
| `commerce.order.purchaseOrderNumber` | Unik identifierare som tilldelats av köparen för detta inköp eller kontrakt. |
| `commerce.order.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.order.lastUpdatedDate` | Den tidpunkt då en viss orderpost senast uppdaterades i handelssystemet. |
| `commerce.shipping` | Leveransinformation för en eller flera produkter. |
| `commerce.shipping.shippingMethod` | Leveranssätt som kunden väljer, t.ex. standardleverans, snabbare leverans, hämtning i butik osv. |
| `commerce.shipping.shippingAmount` | Det belopp som kunden måste betala för frakt. |
| `commerce.shipping.address` | Den fysiska leveransadressen. |
| `commerce.shipping.address.street1` | Primär information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn. |
| `commerce.shipping.address.street2` | Ytterligare gatuinformation, andra raden. |
| `commerce.shipping.address.city` | Namnet på staden. |
| `commerce.shipping.address.state` | Statens namn. Det här är ett frihandsfält. |
| `commerce.shipping.address.postalCode` | Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret. |
| `commerce.shipping.address.country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `commerce.shipping.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.shipping.trackingNumber` | Spårningsnumret som fraktfirman anger för en orderartikelleverans. |
| `commerce.shipping.trackingURL` | URL:en som spårar leveransstatus för en orderartikel. |
| `commerce.shipping.shipDate` | Det datum då en eller flera artiklar från en order skickas. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `commerce.billing.address` | Betalningsadress. |
| `commerce.billing.address.street1` | Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn |
| `commerce.billing.address.street2` | Ytterligare fält för gatuminivåinformation. |
| `commerce.billing.address.city` | Namnet på staden. |
| `commerce.billing.address.state` | Namnet på läget. Det här är ett frihandsfält. |
| `commerce.billing.address.postalCode` | Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret. |
| `commerce.billing.address.country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter i ordningen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |
| `productListItems.categories` | Innehåller information om en produkts kategori. |
| `productListItems.categories.id` | Kategorins unika identifierare. |
| `productListItems.categories.name` | Namnet på kategorin. |
| `productListItems.categories.path` | Sökvägen till kategorin. |

### orderCanceled

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund annullerar en order. | `commerce.backofficeOrderCancelled` |

#### Data insamlade från orderAvbrutna

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.purchaseOrderNumber` | Unik identifierare som tilldelats av köparen för detta inköp eller kontrakt. |
| `commerce.order.cancelDate` | Datum och tid då en kund annullerar en order. |
| `commerce.order.lastUpdatedDate` | Den tidpunkt då en viss orderpost senast uppdaterades i handelssystemet. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |

### orderLineItemRefunded

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund återbetalas för en returartikel. | `commerce.backofficeCreditMemoIssued` |

#### Data insamlade från orderLineItemRefunded

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.lastUpdatedDate` | Den tidpunkt då en viss orderpost senast uppdaterades i handelssystemet. |
| `commerce.order.purchaseOrderNumber` | Unik identifierare som tilldelats av köparen för detta inköp eller kontrakt. |
| `commerce.refunds` | Listan över återbetalningar för den här ordern. |
| `commerce.refunds.transactionID` | Unik identifierare för denna återbetalning. |
| `commerce.refunds.refundAmount` | Återbetalningsvärdet. |
| `commerce.refunds.refundPaymentType` | Betalningsmetoden för den här ordern. Räknade, anpassade värden tillåtna. |
| `commerce.refunds.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter i ordningen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |
| `productListItems.categories` | Innehåller information om en produkts kategori. |
| `productListItems.categories.id` | Kategorins unika identifierare. |
| `productListItems.categories.name` | Namnet på kategorin. |
| `productListItems.categories.path` | Sökvägen till kategorin. |

### orderItemsReturnInitiated

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en kund begär att få returnera ett objekt. | `commerce.backofficeOrderItemsReturnInitiated` |

#### Data insamlade från orderItemsReturnInitiated

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.returns` | RMA-informationen (Return Merchandise Authorization) för den här beställningen. |
| `commerce.order.returns.returnID` | Unik identifierare för denna RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | Status för RMA (Return Merchandise Authorization), t.ex. Pending, Closed osv. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter i ordningen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |
| `productListItems.categories` | Innehåller information om en produkts kategori. |
| `productListItems.categories.id` | Kategorins unika identifierare. |
| `productListItems.categories.name` | Namnet på kategorin. |
| `productListItems.categories.path` | Sökvägen till kategorin. |
| `productListItems.returnItem` | RMA-informationen (Return Merchandise Authorization) för det här objektet. |
| `productListItems.returnItem.returnStatus` | Status för returnerat objekt, som Väntande, Godkänd och så vidare. |
| `productListItems.returnItem.returnReason` | Orsaken till varför en retur begärs för den här artikeln. |
| `productListItems.returnItem.returnItemCondition` | Villkoret för artikeln som returen begärs för. |
| `productListItems.returnItem.returnResolution` | Den begärda upplösningen för det objekt som returneras, till exempel Återbetalning, Exchange och så vidare. |
| `productListItems.returnItem.returnQuantityRequested` | Numret på det här objektet som kunden begärde att få returnera. |
| `productListItems.returnItem.returnQuantityAuthorized` | Numret på den här artikeln som är auktoriserad att returneras. |
| `productListItems.returnItem.eturnQuantityReceived` | Antalet returnerade artiklar som tagits emot. |
| `productListItems.returnItem.returnQuantityApproved` | Numret på det här objektet med fullständig och godkänd retur. |

### orderItemReturnCompleted

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när ett objekt som en kund har begärt att få returnera har slutförts. | `commerce.backofficeOrderItemsReturnCompleted` |

#### Data insamlade från orderItemReturnCompleted

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.returns` | RMA-informationen (Return Merchandise Authorization) för den här beställningen. |
| `commerce.order.returns.returnID` | Unik identifierare för denna RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | Status för RMA (Return Merchandise Authorization), t.ex. Pending, Closed osv. |
| `commerce.commerceScope` | Anger var en händelse inträffade (butiksvy, butik, webbplats och så vidare). |
| `commerce.commerceScope.environmentID` | Händelse-ID. Ett 32-siffrigt alfanumeriskt ID avgränsat med bindestreck. |
| `commerce.commerceScope.storeCode` | Den unika butikskoden. Du kan ha många butiker per webbplats. |
| `commerce.commerceScope.storeViewCode` | Den unika koden för butiksvyn. Du kan ha många butiksvyer per butik. |
| `commerce.commerceScope.websiteCode` | Den unika webbplatskoden. Du kan ha många webbplatser i en miljö. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter i ordningen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |
| `productListItems.categories` | Innehåller information om en produkts kategori. |
| `productListItems.categories.id` | Kategorins unika identifierare. |
| `productListItems.categories.name` | Namnet på kategorin. |
| `productListItems.categories.path` | Sökvägen till kategorin. |
| `productListItems.returnItem` | RMA-informationen (Return Merchandise Authorization) för det här objektet. |
| `productListItems.returnItem.returnStatus` | Status för returnerat objekt, som Väntande, Godkänd och så vidare. |
| `productListItems.returnItem.returnReason` | Orsaken till varför en retur begärs för den här artikeln. |
| `productListItems.returnItem.returnItemCondition` | Villkoret för artikeln som returen begärs för. |
| `productListItems.returnItem.returnResolution` | Den begärda upplösningen för det objekt som returneras, till exempel Återbetalning, Exchange och så vidare. |
| `productListItems.returnItem.returnQuantityRequested` | Numret på det här objektet som kunden begärde att få returnera. |
| `productListItems.returnItem.returnQuantityAuthorized` | Numret på den här artikeln som är auktoriserad att returneras. |
| `productListItems.returnItem.eturnQuantityReceived` | Antalet returnerade artiklar som tagits emot. |
| `productListItems.returnItem.returnQuantityApproved` | Numret på det här objektet med fullständig och godkänd retur. |

### orderShiEquipmentCompleted

| Beskrivning | XDM-händelsenamn |
|---|---|
| Utlöses när en leverans är slutförd. | `commerce.backofficeOrderShipmentCompleted` |

#### Data som samlats in från orderShiEquipmentCompleted

I följande tabell beskrivs de data som samlats in för den här händelsen.

| Fält | Beskrivning |
|---|---|
| `commerce.order` | Innehåller information om ordern. |
| `commerce.order.purchaseID` | Unik identifierare som tilldelats av säljaren för detta inköp eller kontrakt. Det finns ingen garanti för att ID:t är unikt. |
| `commerce.order.payments` | Listan över betalningar för den här ordern. |
| `commerce.order.payments.paymentTransactionID` | Unik identifierare för den här betalningstransaktionen. |
| `commerce.order.payments.paymentAmount` | Betalningens värde. |
| `commerce.order.payments.paymentType` | Betalningsmetoden för den här ordern. Räknade, anpassade värden tillåtna. |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `commerce.order.taxAmount` | Det skattebelopp som köparen betalar som en del av den slutliga betalningen. |
| `commerce.order.createdDate` | Tid och datum då en ny order skapas i handelssystemet. Till exempel: `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Leveransinformation för en eller flera produkter. |
| `commerce.shipping.shippingMethod` | Leveranssätt som kunden väljer, t.ex. standardleverans, snabbare leverans, hämtning i butik osv. |
| `commerce.shipping.shippingAmount` | Det belopp som kunden måste betala för frakt. |
| `commerce.shipping.shipDate` | Det datum då en eller flera artiklar från en order skickas. |
| `commerce.shipping.address` | Den fysiska leveransadressen. |
| `commerce.shipping.address.street1` | Primär information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn. |
| `commerce.shipping.address.street2` | Ytterligare gatuinformation, andra raden. |
| `commerce.shipping.address.city` | Namnet på staden. |
| `commerce.shipping.address.state` | Statens namn. Det här är ett frihandsfält. |
| `commerce.shipping.address.postalCode` | Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret. |
| `commerce.shipping.address.country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `commerce.billing.address` | Betalningsadress. |
| `commerce.billing.address.street1` | Information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn |
| `commerce.billing.address.street2` | Ytterligare fält för gatuminivåinformation. |
| `commerce.billing.address.city` | Namnet på staden. |
| `commerce.billing.address.state` | Namnet på läget. Det här är ett frihandsfält. |
| `commerce.billing.address.postalCode` | Postnumret för platsen. Postnummer är inte tillgängliga för alla länder. I vissa länder innehåller detta endast en del av postnumret. |
| `commerce.billing.address.country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `productListItems` | En array med produkter i ordningen. |
| `productListItems.SKU` | Lagerhållningsenhet. Unik identifierare för produkten. |
| `productListItems.name` | Produktens visningsnamn eller läsbara namn. |
| `productListItems.priceTotal` | Det totala priset för produktartikeln. |
| `productListItems.quantity` | Antalet produktenheter i kundvagnen. |
| `productListItems.discountAmount` | Anger vilket rabattbelopp som används. |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) valutakod som används, till exempel `USD` eller `EUR`. |
| `productListItems.selectedOptions` | Fält som används för en konfigurerbar produkt. |
| `productListItems.selectedOptions.attribute` | Identifierar ett attribut för den konfigurerbara produkten, till exempel `size` eller `color`. |
| `productListItems.selectedOptions.value` | Identifierar värdet för attributet som `small` eller `black`. |
| `productListItems.categories` | Innehåller information om en produkts kategori. |
| `productListItems.categories.id` | Kategorins unika identifierare. |
| `productListItems.categories.name` | Namnet på kategorin. |
| `productListItems.categories.path` | Sökvägen till kategorin. |
