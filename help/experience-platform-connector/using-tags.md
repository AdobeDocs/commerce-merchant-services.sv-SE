---
title: Samla in handelsdata med Adobe Experience Platform-taggar
description: Lär dig hur du samlar in Commerce-data med Adobe Experience Platform-taggar.
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '2126'
ht-degree: 0%

---

# Samla in handelsdata med Adobe Experience Platform-taggar

Även om du kan använda Experience Platform-anslutningen för att publicera och prenumerera på butikshändelser, kan det finnas handlare som redan använder en datainsamlingslösning, som [Adobe Experience Platform-taggar](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html?lang=en). För dessa handlare tillhandahåller Adobe Commerce ett alternativ för enbart publicering i Experience Platform-kopplingen som använder Adobe Commerce Event SDK.

![Dataflöde för Experience Platform Connector](assets/tags-data-flow.png)
_Dataflöde för Experience Platform Connector med taggar_

I det här avsnittet får du lära dig att mappa de värden för butikshändelser som tillhandahålls av Experience Platform-kopplingen till Adobe Experience Platform-tagglösningen som du redan använder.

## Samla in händelsedata från Adobe Commerce

Så här samlar du in händelsedata för Commerce:

- Installera [Adobe Commerce Event SDK](https://www.npmjs.com/package/@adobe/magento-storefront-events-sdk). Information om PHP-butiker finns i [installera](install.md) ämne. För PWA Studio storefront, se [PWA Studio guide](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/).

   >[!NOTE]
   >
   > Gör **not** [konfigurera](connect-data.md) Organisations-ID och DataStream-ID.

## Mappa Commerce-butiksdata till Adobe Experience Platform

Om du vill mappa Commerce storefront-data till Adobe Experience Platform konfigurerar och installerar du följande inifrån Adobe Experience Platform-taggar:

1. [Konfigurera en taggegenskap](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en) i Adobe Experience Platform Data Collection.

1. Under **Redigering**, markera **Tillägg** och installera och konfigurera följande tillägg:

   - [Adobe-klientdatalager](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/adobe/client-data-layer/overview.html)

   - [Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)

1. [Publiceringstagg](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) i er utvecklingsmiljö.

1. Följ **Händelsemappning** steg nedan för att konfigurera dataelement och regler för specifika händelser.

### Händelsemappning

Eftersom datainsamling med hjälp av taggar skiljer sig från användning av Adobe Commerce Event SDK är det viktigt att förstå de likvärdiga termer som används i båda ramverken.

| Adobe Experience Platform tagg term | Adobe Commerce Event SDK term |
|---|---|
| _dataelement_ | kontext |
| _regler_ | event |
|  | _regelvillkor_ - händelseavlyssnare (från ACDL)<br><br>_regelåtgärder_ - händelsehanterare (skicka till Adobe Experience Platform) |

När du uppdaterar dataelementen och reglerna i Adobe Experience Platform-taggar med Adobe Commerce-specifika händelsedata, finns det några vanliga åtgärder som du kommer att vidta.

Låt oss till exempel lägga till Adobe Commerce `signOut` till Adobe Experience Platform-taggar. Stegen som beskrivs nedan, förutom de värden du anger, beskriver hur du lägger till [dataelement](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#data-element) och [regler](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#create-a-rule)som gäller för alla Adobe Commerce-händelser som du lägger till i -taggar.

1. Skapa ett dataelement:

   ![Skapa nytt dataelement](assets/create-new-data-elements.png)
   _Skapa nytt dataelement_

1. Ange **Namn** till `Sign out`.

1. Ange **Tillägg** till `Adobe Experience Platform Web SDK`.

1. Ange **Dataelementtyp** till `XDM object`.

1. Välj **Sandbox** och **Schema** som du vill uppdatera.

1. Under **userAccount** > **utloggning**, ange **value** in **Logga ut som besökare** till `1`.

   ![Uppdatera utloggningsvärde](assets/signout-value.png)
   _Uppdatera utloggningsvärde_

1. Skapa en regel:

   ![Skapa ny regel](assets/create-new-rule.png)
   _Skapa ny regel_

1. Ange **Tillägg** till `Adobe Client Data Layer`.

1. Ange **Händelsetyp** till `Data Pushed`.

1. Välj **Specifik händelse** och ange **Event/Key to register for** till `sign-out`.

1. Lägg till en åtgärd.

1. Ange **Tillägg** till `Adobe Experience Platform Web SDK`.

1. Ange **Åtgärdstyp** till `Send Event`.

1. Ange **Instance** till `Alloy`.

1. Ange **Typ** till `userAccount.logout`.

1. Ange **XDM-data** till `%sign out%`.

1. Klicka **Spara**.

   Du skapade ett dataelement i ditt schema för `signOut` event från Adobe Commerce. Du har också skapat en regel med en specifik åtgärd som ska utföras när händelsen utlöses från Adobe Commerce store.

Upprepa stegen ovan i taggar för var och en av de Adobe Commerce-händelser som beskrivs nedan.

### Tillgängliga händelser

För var och en av följande händelser mappar du Adobe Commerce-händelserna till din XDM genom att följa stegen ovan.

- [&quot;signOut&quot;](#signout)
- [&quot;signIn&quot;](#signin)
- [&quot;createAccount&quot;](#createaccount)
- [`editAccount`](#editaccount)
- [`pageView`](#pageview)
- [&quot;productView&quot;](#productview)
- [`searchRequestSent`](#searchrequestsent)
- [`searchResponseReceived`](#searchresponsereceived)
- [`addToCart`](#addtocart)
- [&quot;viewCart&quot;](#viewcart)
- [`removeFromCart`](#removefromcart)
- [&quot;initieraUtcheckning&quot;](#initiatecheckout)
- [`placeOrder`](#placeorder)

### signOut {#signout}

#### Dataelement

Skapa följande dataelement:

1. Logga ut:

   - **Namn**: `Sign out`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `userAccount` > `logout`
   - **Logga ut som besökare**: **Värde** = `1`

#### Regler 

- **Namn**: `Sign out`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `sign-out`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `userAccount.logout`
- **XDM-data**: `%sign-out%`

### signIn {#signin}

#### Dataelement

Skapa följande dataelement:

1. E-postadress för konto:

   - **Namn**: `Account email`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `accountContext.accountEmail`

1. Kontotyp:

   - **Namn**: `Account type`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `accountContext.accountType`

1. Konto-ID:

   - **Namn**: `Account ID`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana***: `accountContext.accountId`

1. Logga in:

   - **Namn**: `Sign in`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `userAccount` > `login`
   - **Besökarinloggning**: **Värde** = `1`

#### Regler 

- **Namn**: `Sign in`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `sign-in`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `userAccount.login`
- **XDM-data**: `%sign-in%`

### createAccount {#createaccount}

#### Dataelement

Skapa följande dataelement:

1. E-postadress för konto:

   - **Namn**: `Account email`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `accountContext.accountEmail`

1. Kontotyp:

   - **Namn**: `Account type`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `accountContext.accountType`

1. Konto-ID:

   - **Namn**: `Account ID`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana***: `accountContext.accountId`

1. Skapa konto:

   - **Namn**: `Create account`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `userAccount` > `createProfile`
   - **Skapa kontoprofil**: **Värde** = `1`

#### Regler 

- **Namn**: `Create account`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `create-account`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `userAccount.createProfile`
- **XDM-data**: `%create account%`

### editAccount {#editaccount}

#### Dataelement

Skapa följande dataelement:

1. E-postadress för konto:

   - **Namn**: `Account email`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `accountContext.accountEmail`

1. Kontotyp:

   - **Namn**: `Account type`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `accountContext.accountType`

1. Konto-ID:

   - **Namn**: `Account ID`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana***: `accountContext.accountId`

1. Redigera konto:

   - **Namn**: `Edit account`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `userAccount` > `updateProfile`
   - **Skapa kontoprofil**: **Värde** = `1`

#### Regler

- **Namn**: `Edit account`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `edit-account`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `userAccount.updateProfile`
- **XDM-data**: `%edit account%`

### pageView {#pageview}

#### Dataelement

Skapa följande dataelement:

1. Sidnamn:

   - **Namn**: `Page name`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `pageContext.pageName`

#### Regler 

- **Namn**: `Page view`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `Core-Library Loaded`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `web.webPageDetails.pageViews`
- **XDM-data**: `%page view%`

### productView {#productview}

#### Dataelement

Skapa följande dataelement:

1. Produktnamn:

   - **Namn**: `Product name`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.name`

1. Produkt-SKU:

   - **Namn**: `Product sku`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.sku`

1. Valutakod:

   - **Namn**: `Currency code`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.currencyCode`

1. Specialpris:

   - **Namn**: `Special price`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.specialPrice`

1. Ordinarie pris:

   - **Namn**: `Regular price`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.regularPrice`

1. Produktpris:

   - **Namn**: `Product price`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**: `return _satellite.getVar('product regular price') || _satellite.getVar('product special price')`

1. Produktvy:

   - **Namn**: `Product view`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `productListItems`. Välj **Ange enskilda objekt** och klicka på **Lägg till objekt** -knappen. Eftersom den här vyn är för en PDP-fil kan du fylla med ett enstaka objekt.

#### Regler 

- **Namn**: `Product view`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `product-page-view`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `commerce.productViews`
- **XDM-data**: `%product view%`

### searchRequestSent {#searchrequestsent}

#### Dataelement

Skapa följande dataelement:

1. Sök indata

   - **Namn**: `Search input`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `searchInputContext.units[0]`

1. Sök inmatningsfras

   - **Namn**: `Search input phrase`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   `return _satellite.getVar('search input').phrase;`
   ```

1. Sortera indata

   - **Namn**: `Search input sort`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const sortFromInput = searchInput ? searchInput.sort : [];
   const sort = sortFromInput.map((searchSort) => {
       return {
           attribute: searchSort.attribute,
           order: searchSort.direction,
       };
   });
   return sort;
   ```

1. Indatafilter för sökning

   - **Namn**: `Search input filters`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const filtersFromInput = searchInput ? searchInput.filter : [];
   const filters = filtersFromInput.map(
       (searchFilter) => {
           let value = [];
           let isRange = false;
           if (searchFilter.eq) {
               value.push(searchFilter.eq);
           } else if (searchFilter.in) {
               value = searchFilter.in;
           } else if (searchFilter.range) {
               isRange = true;
               value.push(String(searchFilter.range.from));
               value.push(String(searchFilter.range.to));
           }
           return {
               attribute: searchFilter.attribute,
               value,
               isRange,
           };
       }
   );
   
   return filters;
   ```

1. Sökbegäran:

   - **Namn**: `Search request`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `siteSearch` > `phrase`
   - **value**: Inte tillgängligt ännu
   - **Fältgrupp**: `siteSearch` > `sort`. Välj **Ange hela objektet**.
   - **Fältgrupp**: `siteSearch` > `filter`. Välj **Ange hela objektet**.
   - **Fältgrupp**: `searchRequest` > `value`
   - **value**: **Värde** = `1`

#### Regler 

- **Namn**: `Search request sent`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `search-request-sent`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `searchRequest`
- **XDM-data**: `%search request%`

### searchResponseReceived {#searchresponsereceived}

#### Dataelement

Skapa följande dataelement:

1. Sökresultat:

   - **Namn**: `Search results`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `searchResultsContext.units[0]`

1. Resultatnummer för sökning:

   - **Namn**: `Search result number of products`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('search result').productCount;
   ```

1. Sökresultatprodukter:

   - **Namn**: `Search result products`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const productsFromResult = searchResult.products ? searchResult.products : [];
   const products = productsFromResult.map(
       (product) => {
           return { SKU: product.sku, name: product.name };
       }
   );
   return products;
   ```

1. Sökresultatförslag:

   - **Namn**: `Search result products`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
   const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
   return suggestions;
   ```

1. Söksvar:

   - **Namn**: `Search response`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `siteSearch` > `suggestions`. Välj **Ange hela objektet**.
   - **Fältgrupp**: `siteSearch` > `numberOfResults`
   - **value**: `%search result number of products%`
   - **Fältgrupp**: `productListItems`. Välj **Ange hela objektet**.
   - **Fältgrupp**: `searchResponse` > `value`
   - **value**: **Värde** = `1`

#### Regler 

- **Namn**: `Search Response Received`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `search-response-received`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `searchResponse`
- **XDM-data**: `%search response%`

### addToCart {#addtocart}

#### Dataelement

Skapa följande dataelement:

1. Produktnamn:

   - **Namn**: `Product name`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.name`

1. Produkt-sku:

   - **Namn**: `Product sku`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.sku`

1. Valutakod:

   - **Namn**: `Currency code`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.currencyCode`

1. Specialpris:

   - **Namn**: `Product special price`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.specialPrice`

1. Normalpris:

   - **Namn**: `Product regular price`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.regularPrice`

1. Produktpris:

   - **Namn**: `Product price`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Kundvagn:

   - **Namn**: `Cart`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `shoppingCartContext`

1. Kundvagn-id:

   - **Namn**: `Cart id`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Lägg i kundvagnen:

   - **Namn**: `Add to cart`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `productListItems`. Välj **Ange enskilda objekt** och klicka på **Lägg till objekt** -knappen. Eftersom den här vyn är för en PDP-fil kan du fylla med ett enstaka objekt.
   - **Fältgrupp**: `commerce` > `cart` > `cartID`
   - **Kundvagn-ID**: **Värde** = `%cart id%`
   - **Fältgrupp**: `commerce` > `productListAdds` > `id`
   - **Unik identifierare**: **value** = `1`

#### Regler 

- **Namn**: `Add to cart`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `add-to-cart`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `commerce.productListAdds`
- **XDM-data**: `%add to cart%`

### viewCart {#viewcart}

#### Dataelement

Skapa följande dataelement:

1. Storefront:

   - **Namn**: `Storefront`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `storefrontInstanceContext`

1. Kundvagn:

   - **Namn**: `Cart`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `shoppingCartContext`

1. Kundvagn-id:

   - **Namn**: `Cart id`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Produktlisteposter:

   - **Namn**: `Product list items:`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const searchResult = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Visa kundvagn:

   - **Namn**: `View cart`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `productListItems`. För `productListItems`kan det finnas flera artiklar som är förberäknade. Välj **productListItems** > **Fyll hela arrayen**.
   - **Fältgrupp**: `commerce` > `cart` > `cartID`
   - **Kundvagn-ID**: **Värde** = `%cart id%`
   - **Fältgrupp**: `commerce` > `productListAdds` > `id`
   - **Unik identifierare**: **value** = `1`

#### Regler 

- **Namn**: `View cart`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `shopping-cart-view`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `commerce.productListViews`
- **XDM-data**: `%view cart%`

### removeFromCart {#removefromcart}

#### Dataelement

Skapa följande dataelement:

1. Produktnamn:

   - **Namn**: `Product name`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.name`

1. Produkt-sku:

   - **Namn**: `Product sku`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.sku`

1. Valutakod:

   - **Namn**: `Currency code`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.currencyCode`

1. Specialpris:

   - **Namn**: `Product special price`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.specialPrice`

1. Normalpris:

   - **Namn**: `Product regular price`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `productContext.pricing.regularPrice`

1. Produktpris:

   - **Namn**: `Product price`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. Kundvagn:

   - **Namn**: `Cart`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `shoppingCartContext`

1. Kundvagn-id:

   - **Namn**: `Cart id`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Ta bort från kundvagn:

   - **Namn**: `Remove from cart`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `productListItems`. Välj **Ange enskilda objekt** och klicka på **Lägg till objekt** -knappen. Eftersom den här vyn är för en PDP-fil kan du fylla med ett enstaka objekt.
   - **Fältgrupp**: `commerce` > `cart` > `cartID`
   - **Kundvagn-ID**: **Värde** = `%cart id%`
   - **Fältgrupp**: `commerce` > `productListRemovals`
   - **Unik identifierare**: **value** = `1`

#### Regler 

- **Namn**: `Remove from cart`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `remove-from-cart`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `commerce.productListRemovals`
- **XDM-data**: `%remove from cart%`

### initialCheckout {#initiatecheckout}

#### Dataelement

Skapa följande dataelement:

1. Storefront:

   - **Namn**: `Storefront`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `storefrontInstanceContext`

1. Kundvagn:

   - **Namn**: `Cart`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `shoppingCartContext`

1. Kundvagn-id:

   - **Namn**: `Cart id`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Produktlisteposter:

   - **Namn**: `Product list items`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const searchResult = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Starta utcheckning:

   - **Namn**: `Initiate checkout`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `productListItems`. För `productListItems`kan det finnas flera artiklar som är förberäknade. Välj **productListItems** > **Fyll hela arrayen**.
   - **Fältgrupp**: `commerce` > `cart` > `cartID`
   - **Kundvagn-ID**: **Värde** = `%cart id%`
   - **Fältgrupp**: `commerce` > `checkouts`
   - **Unik identifierare**: **value** = `1`

#### Regler 

- **Namn**: `Initiate checkout`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `initiate-checkout`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `commerce.checkouts`
- **XDM-data**: `%initiate checkout%`

### placeOrder {#placeorder}

#### Dataelement

Skapa följande dataelement:

1. Storefront:

   - **Namn**: `Storefront`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `storefrontInstanceContext`

1. Kundvagn:

   - **Namn**: `Cart`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `shoppingCartContext`

1. Kundvagn-id:

   - **Namn**: `Cart id`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. Ordning:

   - **Namn**: `Order`
   - **Tillägg**: `Adobe Client Data Layer`
   - **Dataelementtyp**: `Data Layer Computed State`
   - **[Valfritt] bana**: `orderContext`

1. Handelsorder:

   - **Namn**: `Commerce order`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const order = _satellite.getVar('order');
   const storefront = _satellite.getVar('storefront');
   
   if (order.payments && order.payments.length) {
       payments = order.payments.map(payment => {
           return {
               paymentAmount: payment.total,
               paymentType: payment.paymentMethodCode,
               transactionID: order.orderId.toString(),
           };
       });
   } else {
       payments = [
           {
               paymentAmount: order.grandTotal,
               paymentType: order.paymentMethodCode,
               transactionID: order.orderId.toString(),
           },
       ];
   }
   
   return {
       purchaseID: order.orderId.toString(),
       currencyCode: storefront.storeViewCurrencyCode,
       payments,
   };
   ```

1. Orderleverans:

   - **Namn**: ` Order shipping`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const order = _satellite.getVar('order');
   return {
       shippingMethod: order.shipping.shippingMethod,
       shippingAmount: order.shipping.shippingAmount || 0,
   }
   ```

1. Kampanj-ID:

   - **Namn**: `Promotion id`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   return _satellite.getVar('order').appliedCouponCode
   ```

1. Produktlisteposter:

   - **Namn**: `Product list items`
   - **Tillägg**: `Core`
   - **Dataelementtyp**: `Custom Code`
   - **Öppna redigeraren**:

   ```bash
   const searchResult = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. Monteringsordning:

   - **Namn**: `Place order`
   - **Tillägg**: `Adobe Experience Platform Web SDK`
   - **Dataelementtyp**: `XDM object`
   - **Fältgrupp**: `productListItems`. För `productListItems`kan det finnas flera artiklar som är förberäknade. Välj **productListItems** > **Fyll hela arrayen**.
   - **Fältgrupp**: `commerce` > `order`
   - **Unik identifierare**: **Värde** = `%commerce order%`
   - **Fältgrupp**: `commerce` > `shipping`
   - **Unik identifierare**: **value** = ` %order shipping%`
   - **Fältgrupp**: `commerce` > `promotionID`
   - **Kampanj-ID**: **Värde** = `%promotion id%`
   - **Fältgrupp**: `commerce` > `purchases` > `value`
   - **Värde**: **Värde** = `1`

#### Regler 

- **Namn**: `Place order`
- **Tillägg**: `Adobe Client Data Layer`
- **Händelsetyp**: `Data Pushed`
- **Specifik händelse**: `place-order`

##### Åtgärder

- **Tillägg**: `Adobe Experience Platform Web SDK`
- **Åtgärdstyp**: `Send event`
- **Typ**: `commerce.order`
- **XDM-data**: `%place order%`

## Ange identitet

Kopplingsprofilerna för Experience Platform sammanfogas och skapas baserat på `personID` och `personalEmail` identitetsfält i XDM Experience-händelser. 

Om du har en tidigare konfiguration som är beroende av olika fält kan du fortsätta att använda dessa. Om du vill ange identitetsfält för anslutningsprofilen i Experience Platform måste du ange följande fält:

- `personalEmail` - Endast kontohändelser - följ stegen ovan för kontohändelser
- `personID` - Alla andra händelser:

   - Om du redan hämtar `ECID` i -taggar kan du ange `personID` i alla dina Adobe Experience Platform Web SDK-regler för `%ECID%`.
   - Att hämta `ECID` i -taggar måste du lägga till en **Egen kod** åtgärd i sändningshändelsereglerna efter [Dokumentation för taggar](https://experienceleague.adobe.com/docs/experience-platform/edge/extension/accessing-the-ecid.html). Se exemplet nedan.

### Exempel

I följande bilder visas hur du konfigurerar en `pageView` händelse med `personID` i Experience Platform:

1. Konfigurera dataelement med anpassad kod för ECID:

   ![Konfigurera dataelement med anpassad kod](assets/set-custom-code-ecid.png)
   _Konfigurera dataelement med anpassad kod_

1. Lägg till anpassad ECID-kod:

   ![Kod för att ange ECID i dataelement](assets/code-to-set-ecid.png)
   _Kod för att ange ECID i dataelement_

1. Uppdatera XDM-schema med personID angivet som ECID:

   ![Ange person-ID som ECID](assets/set-personid-as-ecid.png)
   _Ange person-ID som ECID_

1. Definiera regelåtgärder som hämtar ECID:

   ![Hämta ECID](assets/rule-retrieve-ecid.png)
   _Hämta ECID_

## Ange samtycke

Samlingsgodkännande av Adobe Commerce- och Experience Platform-anslutningsdata är aktiverat som standard. Avanmäl dig hanteras via [`mg_dnt` cookie](https://docs.magento.com/user-guide/stores/cookie-reference.html). Du kan följa de anvisningar som beskrivs här om du väljer att använda `mg_dnt` för att hantera samtycke. The [Adobe Experience Platform Web SDK-dokumentation](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=en) har flera alternativ för att hantera samtycke.

1. Skapa en **Anpassad kärnkod** dataelement (`%do not track cookie%`) för `mg_dnt` cookie:

   ![Skapa spårar inte dataelement](assets/element-dnt-cookie.png)
   _Skapa spårar inte dataelement_

1. Skapa en **Anpassad kärnkod** dataelement (`%consent%`) som returnerar `out` om cookie är inställd och `in` i annat fall:

   ![Skapa dataelement för samtycke](assets/element-consent-dnt-cookie.png)
   _Skapa dataelement för samtycke_

1. Konfigurera Adobe Experience Platform Web SDK-tillägg med `%consent%` dataelement:

   ![Uppdatera SDK med samtycke](assets/config-sdk-consent.png)
   _Uppdatera SDK med samtycke_

## Varningar

- Om du inte följer stegen för att stänga av Experience Platform-samlingen räknas händelser som dubbelt
- Om du inte konfigurerar mappningar/händelser enligt beskrivningen i det här avsnittet kan det påverka Adobe Analytics-ritningar
- Du kan inte konfigurera Target via Experience Platform-kopplingen om datainsamling är inaktiverad
