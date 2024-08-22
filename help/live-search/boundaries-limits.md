---
title: 'Gränser och gränser'
description: Lär dig mer om gränserna och gränserna för  [!DNL Live Search] så att du kan vara säker på att det uppfyller behoven i din verksamhet.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: ffbb41ef2bc940982b4acb33623ef689542617c1
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Gränser och begränsningar

När det gäller webbplatssökningar har Adobe Commerce fler alternativ. Granska följande gränser och gränser för att säkerställa att [!DNL Live Search] och [!DNL Catalog Service] uppfyller ditt företags behov. Om du behöver avancerade sökfunktioner som innehållssökning, BYOA (Bring-your-own-algorithm) eller attributbaserad marknadsföring bör du överväga en tredjepartslösning.

## Allmänt

- Modulen [Avancerad sökning](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) är inaktiverad när [!DNL Live Search] är installerat och länken Avancerad sökning i sidfoten i förgrunden har tagits bort.
- [Nivåpriser](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) och [specialpriser](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) stöds inte i fältet [!DNL Live Search] och i widgeten Produktlistningssida.
- Priserna inkluderar inte moms.
- Innehållssökning stöds inte.
- Det finns en gräns på 10 000 produkter som kan sidnumreras.
- Det finns en hård gräns på 1 MB per attribut, inklusive beskrivning och anpassade attribut.
- Sökadaptern stöder inte produktattribut som har skapats med en anpassad källmodell och används som facets. Om du vill ha stöd för den här funktionen måste du använda [widgeten Produktlistsida](plp-styling.md).

## Indexering

- [!DNL Live Search] [index](indexing.md) upp till totalt 450 produktattribut per butiksvy. Dessa fördelas enligt följande:
   - 50 sorterbara attribut
   - 200 filterbara attribut
   - 200 sökbara attribut
- [!DNL Live Search] indexerar bara produkter från Adobe Commerce-databasen.
- CMS-sidor är inte indexerade.
- SKU-, namn- och kategoriattribut går att söka i som standard och kan inte uteslutas från sökningen. Se till att du tar bort tilldelningen av produkterna från kategorierna om de inte ska ingå i dessa kategorier.

## Fasetter

- Högst 100 attribut kan konfigureras som facets från de 200 filterbara attribut som kan indexeras.
- Inom ett facet kan högst 30 hinkar returneras. Om fler än 30 bucklor behöver returneras [skapar du en supportbiljett](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) så att Adobe kan analysera prestandapåverkan och avgöra om det är möjligt att öka den här gränsen för din miljö.
- Dynamiska aspekter kan orsaka prestandaproblem i stora index och index med hög ordningstalsgrad. Om du har skapat dynamiska ansikten och observerar prestandaförsämringar eller sidor som inte läses in med timeoutfel, kan du försöka ändra dina facets till fäst för att avgöra om detta löser ditt prestandaproblem.
- Stock-status (`quantity_and_stock_status`) stöds inte som en fasett. Du kan använda `inStock: 'true'` för att filtrera bort från Stock-produkter. Detta stöds inte i rutan i modulen `LiveSearchAdapter` när &quot;Visa utanför stockprodukter&quot; är inställt på &quot;Sant&quot; i [!DNL Commerce] Admin.
- Datumtypsattribut stöds inte som en faktor.

## Fråga

- [!DNL Live Search] använder en unik [GraphQL-slutpunkt](https://developer.adobe.com/commerce/services/graphql/live-search/) för frågor för att stödja funktioner som dynamisk Faceeting och sökning-som-du-typ. Även om det liknar [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) finns det vissa skillnader och vissa fält är kanske inte helt kompatibla.
- Det maximala antalet resultat som kan returneras i en sökfråga är 10 000.
- Det går inte att filtrera resultat med ett datumtypsattribut.

## Regler

- Det högsta antalet [regler](rules.md) för sökmarknadsföring per butiksvy är 50.
- Kategorimarknadsföring kan ha en regel per kategori.
- Det högsta antalet villkor per regel är 10.
- Det högsta antalet händelser per regel är 25.
- För att undvika oförutsägbara resultat i sidnumrerade svar bör antalet fästa produkter inte överskrida den begärda sidstorleken.

## Synonymer

- [!DNL Live Search] kan hantera upp till 200 [synonymer](synonyms.md) per butiksvy.
- Det är inte säkert att flerordssynonymer alltid fungerar som förväntat. Testa dessa synonymer i testmiljön innan du använder dem i produktionen, eftersom de kan ha en negativ effekt på relevansen.

## Kategoriförsäljning

- En regel per kategori kan skapas för varje butiksvy. Varje regel kan ha:
   - Upp till tio villkor
   - Upp till 25 händelser

## B2B- och kategoribehörigheter

- Produkter visas inte om de inte har lagts till i en delad standardkatalog.
- Så här begränsar du kundgrupper med [kategoribehörigheter](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions):
   - Produkter måste tilldelas till rotkategorin.
   - Kundgruppen &quot;Inte inloggad&quot; måste ha behörigheten &quot;Tillåt&quot; för bläddring.
   - Om du vill begränsa produkter till kundgruppen Inte inloggad går du till varje kategori och anger behörigheter för varje [kundgrupp](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- Det finns för närvarande inget stöd för B2B med PLP-widgeten i PWA Studio. Du kan [använda API](install.md#pwa-support) för att implementera den här funktionen.
- Kategorifacet i [!DNL Live Search] kan visa kategorier som inte kan visas för en specifik [kundgrupp](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- [!DNL Live Search] har stöd för upp till 1 000 kundgrupper.

## [!DNL Storefront popover]

- [[!DNL popover]](storefront-popover.md) är bara tillgängligt för butiker som använder *Luma*-temat, eller ett anpassat tema som baseras på *Luma*. Sidan med vägbeskrivningar på sökresultatsidan kommer inte att ha formatet *Luma*.
- [!DNL popover] stöder inte temat *Tom*.
- [!DNL popover] stöds inte i snabbbeställningsformuläret.
- Önsklistorna och produktjämförelserna stöds inte.
