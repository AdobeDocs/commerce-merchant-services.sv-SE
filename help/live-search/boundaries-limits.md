---
title: 'Gränser och gränser'
description: Läs om gränserna och gränserna för [!DNL Live Search] för att säkerställa att den uppfyller företagets behov.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Gränser och begränsningar

När det gäller webbplatssökningar har Adobe Commerce fler alternativ. Granska följande gränser och gränser för att säkerställa att [!DNL Live Search] och [!DNL Catalog Service] uppfyller företagets behov. Om du behöver avancerade sökfunktioner som innehållssökning, BYOA (Bring-your-own-algorithm) eller attributbaserad marknadsföring bör du överväga en tredjepartslösning.

## Allmänt

- The [Avancerad sökning](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) modulen är inaktiverad när [!DNL Live Search] installeras och länken Avancerad sökning i storefront-sidfoten tas bort.
- [Priser](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) och [Specialpris](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) stöds inte i [!DNL Live Search] fält och sidwidget för produktlista.
- [!DNL Live Search] kan inte samla in lagerdata från flera källor.
- Priserna inkluderar inte moms.
- Innehållssökning stöds inte.
- Det finns en gräns på 10 000 produkter som kan sidnumreras.

## Indexering

- [!DNL Live Search] [index](indexing.md) upp till totalt 450 produktattribut per butiksvy. Dessa fördelas enligt följande:
   - 50 sorterbara attribut
   - 200 filterbara attribut
   - 200 sökbara attribut
- [!DNL Live Search] indexerar endast produkter från Adobe Commerce-databasen.
- CMS-sidor är inte indexerade.

## Fasetter

- Högst 100 attribut kan konfigureras som facets från de 200 filterbara attribut som kan indexeras.
- Inom ett facet kan högst 30 hinkar returneras. Om fler än 30 bussar behöver returneras [skapa en supportanmälan](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) så att Adobe kan analysera prestandaeffekterna och avgöra om det är möjligt att höja denna miljögräns.
- Dynamiska aspekter kan orsaka prestandaproblem i stora index och index med hög ordningstalsgrad. Om du har skapat dynamiska ansikten och observerar prestandaförsämringar eller sidor som inte läses in med timeoutfel, kan du försöka ändra dina facets till fäst för att avgöra om detta löser ditt prestandaproblem.
- Lagerstatus (`quantity_and_stock_status`) stöds inte som en fasett. Du kan använda `inStock: 'true'` för att filtrera bort lagerprodukter. Det här stöds inte direkt i dialogrutan `LiveSearchAdapter` när&quot;Display out of stock products&quot; är inställd på&quot;True&quot; i [!DNL Commerce] Admin.

## Fråga

- [!DNL Live Search] har inte tillgång till den fullständiga taxonomin för kategoriträdet, vilket gör att vissa sökscenarier med lagerstyrd navigering inte är tillgängliga.
- [!DNL Live Search] använder ett unikt [GraphQL slutpunkt](https://developer.adobe.com/commerce/services/graphql/live-search/) för frågor som stöder funktioner som dynamisk ansiktsdesign och sökning efter text. Även om den liknar [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)finns det några skillnader och vissa fält kanske inte är helt kompatibla.
- Det maximala antalet resultat som kan reproduceras i en sökfråga är 10 000.

## Regler

- Maximalt antal sökmarknadsföringar [regler](rules.md) per butiksvy är 50.
- Kategorimarknadsföring kan ha en regel per kategori.
- Det högsta antalet villkor per regel är 10.
- Det högsta antalet händelser per regel är 25.

## Synonymer

- [!DNL Live Search] kan hantera upp till 200 [synonymer](synonyms.md) per butiksvy.
- Flerordssynonymer stöds inte.

## Kategoriförsäljning

- En regel per kategori kan skapas för varje butiksvy. Varje regel kan ha:
   - Upp till tio villkor
   - Upp till 25 händelser

## B2B- och kategoribehörigheter

- Produkter visas inte om de inte har lagts till i en delad standardkatalog.
- Så här begränsar du kundgrupper med katalogbehörigheter:
   - Produkter måste tilldelas till rotkategorin.
   - Kundgruppen &quot;Inte inloggad&quot; måste ha behörigheten &quot;Tillåt&quot; för bläddring.
   - Om du vill begränsa produkter till kundgruppen Inte inloggad går du till varje kategori och anger behörigheter för varje kundgrupp.
- Stöd för B2B med Live Search för PWA Studio stöds för närvarande inte.
