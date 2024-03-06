---
title: "[!DNL Live Search] Indexering"
description: "Läs mer [!DNL Live Search] indexerar egenskaper för produktattribut."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Indexering

The [!DNL Live Search] indexeringsprocessen läser igenom katalogen efter produktattribut och skapar ett index så att produkterna kan sökas igenom, filtreras och presenteras snabbt.

Egenskaper för produktattribut (metadata) bestämmer:

* Hur ett attribut kan användas i katalogen
* Dess utseende och beteende i butiken
* De data som ingår i dataöverföringsoperationer

Omfånget för attributmetadata är `website/store/store view`.

The [!DNL Live Search] API tillåter en klient att sortera efter alla produktattribut som har [Egenskapen storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` ange till `Yes` i Adobe Commerce Admin. När det är aktiverat `Search Weight` och `Visible in Advanced Search` kan anges för attributet.

[!DNL Live Search] indexerar inte borttagna produkter eller produkter som är inställda på `Not Visible Individually`.

>[!NOTE]
>
> Handla kunder med [!DNL Live Search] kan dra nytta av snabbare prisändringar och synkroniseringstid på sina webbplatser med [SaaS prisindexerare](../price-index/price-indexing.md).

## Indexerar pipeline

Klienten anropar söktjänsten från butiken för att hämta (filterbara, sorterbara) indexmetadata. Bara sökbara produktattribut med *Använd i navigering i lager* egenskap inställd på `Filterable (with results)` och *Använd för sortering i produktlista* ange till `Yes` kan anropas av söktjänsten.
Om du vill skapa en dynamisk fråga måste söktjänsten känna till vilka attribut som är sökbara och deras [vikt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search). [!DNL Live Search] följer Adobe Commerce sökvikter (1-10, där 10 är den högsta prioriteten). Listan med data som synkroniseras och delas med katalogtjänsten finns i schemat, som definieras i:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] indexera klientsökdiagram](assets/indexing-pipeline.svg)

1. Sök efter handlare [!DNL Live Search] berättigande.
1. Hämta butiksvyer med ändringar i attributmetadata.
1. Lagra indexeringsattribut.
1. Indexera om sökindex.

### Fullständigt index

När [!DNL Live Search] är konfigurerat och synkroniserat under introduktionen, det kan ta upp till 30 minuter att skapa det inledande indexet. Stora kataloger kan ta längre tid att indexera. Processen börjar efter `cron` skickar flödet och slutför körningen.

Följande händelser utlöser en fullständig synkronisering och indexgenerering:

* Onboarding [synkronisering av katalogdata](install.md#synchronize-catalog-data)
* Ändringar av attributmetadata

Ändra till exempel `Use in Search` egenskapen för `color` attribut från `No` till `Yes` ändrar attributmetadata till `searchable=true`och aktiverar en fullständig synkronisering och omindexering. Följande attributmetadata utlöser en fullständig synkronisering och omindexering när de ändras:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Direktuppspelande produktuppdateringar

Efter att det inledande indexvärdet har skapats under [onboarding](install.md#synchronize-catalog-data)kommer följande stegvisa produktuppdateringar att kontinuerligt synkroniseras och indexeras om:

* Nya produkter som lagts till i katalogen
* Ändringar av produktattributvärden

Du kan till exempel lägga till ett nytt värde för färgrutan i `color` -attributet hanteras som en direktuppspelad produktuppdatering.
Arbetsflöde för direktuppspelning av uppdatering:

1. Uppdaterade produkter synkroniseras från Adobe Commerce-instansen till katalogtjänsten.
1. Indexeringstjänsten söker kontinuerligt efter produktuppdateringar från katalogtjänsten. Uppdaterade produkter indexeras allt eftersom de kommer in i katalogtjänsten.
1. Det kan ta upp till 15 minuter innan en produktuppdatering blir tillgänglig på [!DNL Live Search].

## Klientsökning

The [!DNL Live Search] API tillåter en klient att sortera efter ett sorterbart produktattribut genom att ställa in [Egenskapen storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Används för sortering i produktlistor* till `Yes`. Beroende på temat gör den här inställningen att attributet inkluderas som ett alternativ i [Sortera efter](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) sidnumreringskontroll på katalogsidor. Upp till 200 produktattribut kan indexeras av [!DNL Live Search], med [storefront-egenskaper](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) som är sökbara och filterbara.
Indexmetadata lagras i indexeringsflödet och är tillgängliga för söktjänsten.

![[!DNL Live Search] API-diagram för indexmetadata](assets/index-metadata-api.svg)

### Sorterbart attributarbetsflöde

1. Klientanropar söktjänsten.
1. Söktjänsten anropar Search Admin Service.
1. Söktjänsten anropar indexeringspipeline.

## Indexerad för alla produkter

Fältens ordning i den här listan återspeglar den typiska ordningen för kolumner i exporterade produktdata.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

Följande fält är indexerat för alla konfigurerbara produkter:

* `childrenSkus`
