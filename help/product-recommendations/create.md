---
title: Skapa ny rekommendation
description: Lär dig hur du skapar en produktrekommendationsenhet.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 0%

---

# Skapa ny rekommendation

När du skapar en rekommendation skapar du en _rekommendationsenhet_ som innehåller den rekommenderade produkten _objekt_.

![Rekommendationsenhet](assets/unit.png)
_Rekommendationsenhet_

När du aktiverar rekommendationsenheten börjar Adobe Commerce att [samla in data](workspace.md) för att mäta visningar, vyer, klick och så vidare. The [!DNL Product Recommendations] tabellen visar måtten för varje rekommendationsenhet så att ni kan fatta välgrundade affärsbeslut.

1. På _Administratör_ sidebar, gå till **Marknadsföring** > _Erbjudanden_ > **Recommendations** för att visa _Recommendations_ arbetsyta.

1. Ange [Butiksvy](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) där du vill att rekommendationerna ska visas.

   >[!NOTE]
   >
   > Rekommendationsenheter för Page Builder kan bara skapas för standardbutiksvyn. Mer information om hur du skapar produktrekommendationer med Page Builder finns i [Lägg till innehåll - Produkt-Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Klicka **Skapa rekommendation**.

1. I _Namnge din rekommendation_ anger du ett beskrivande namn för intern referens, som `Home page most popular`.

1. I _Välj sidtyp_ väljer du den sida där du vill att rekommendationen ska visas bland följande alternativ:

   - Hemsida
   - Kategori
   - Produktinformation
   - Kundvagn
   - Bekräftelse
   - [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   Du kan skapa upp till fem aktiva rekommendationsenheter för varje sidtyp och upp till 25 för Page Builder. Sidtypen är nedtonad när gränsen nås.

   ![Rekommendationsnamn och -sida](assets/create-recommendation.png)
   _Rekommendationsnamn och sidplacering_

1. I _Välj rekommendationstyp_ -avsnittet, ange [typ av rekommendation](type.md) som du vill ska visas på den markerade sidan. För vissa sidor är [placering](placement.md) Rekommendationerna är begränsade till vissa typer.

   Vissa rekommendationstyper använder beteendedata från era kunder till [utbildningsmodeller för tågmaskiner](behavioral-data.md) att bygga personaliserade rekommendationer. I det här avsnittet visas ett mått på beredskap för varje typ av rekommendation, så att du lättare kan se utbildningsförloppet för varje rekommendationstyp. Dessa beredskapsindikatorer beräknas utifrån några faktorer:

   - Tillräcklig storlek för resultatuppsättning: Finns det tillräckligt många resultat som returneras i de flesta scenarier för att undvika att använda [rekommendationer för säkerhetskopiering](behavioral-data.md#backuprecs)?

   - Tillräcklig mängd resultat: Representerar de returnerade produkterna en mängd olika produkter från din katalog? Målet med den här faktorn är att undvika att en liten andel produkter är de enda objekt som rekommenderas på webbplatsen.

   Baserat på ovanstående faktorer beräknas och visas ett beredskapsvärde. En rekommendationstyp anses vara redo att distribueras när dess beredskapsvärde är 75 % eller högre. En rekommendationstyp anses vara delvis klar när dess beredskap är minst 50 %. Slutligen anses en rekommendationstyp inte vara redo att distribueras när dess beredskapsvärde är mindre än 50 %.

   ![Rekommendationstyp](assets/create-recommendation-select-type.png)
   _Rekommendationstyp_

1. I _Etikett för butiksvisning_ anger du [label](placement.md#recommendation-labels) som är synligt för era kunder, till exempel&quot;bästsäljare&quot;.

1. I _Välj antal produkter_ använder du skjutreglaget för att ange hur många produkter som ska visas i rekommendationsenheten.

   Standardvärdet är `5`, med högst `20`.

1. I _Välj placering_ anger du platsen där rekommendationsenheten ska visas på sidan.

   - Längst ned i huvudinnehållet
   - Överst i huvudinnehållet

1. (Valfritt) Om du vill ändra ordningen på rekommendationerna markerar du och flyttar raderna i _Välj position_ tabell.

   The _Välj position_ I visas alla rekommendationer (om sådana finns) som har skapats för den sidtyp du valde.

   ![Rekommendationsorder](assets/create-recommendation-select-placement.png)
   _Rekommendationsordning på sidan_

1. (Valfritt) I dialogrutan _Filter_ sektion, [använda filter](filters.md) för att styra vilka produkter som ska visas i rekommendationsenheten.

   ![Rekommendationsfilter](assets/create-recommendation-filter-products.png)
   _Rekommendationsproduktfilter_

1. När du är klar klickar du på något av följande:

   - **Spara som utkast** för att redigera rekommendationsenheten senare. Du kan inte ändra sidtypen eller rekommendationstypen för en rekommendationsenhet i ett utkastläge.

   - **Aktivera** för att aktivera rekommendationsenheten i butiken.

## Förhandsgranska Recommendations {#preview}

The _Förhandsgranskning av rekommenderade produkter_ Panelen är alltid tillgänglig med ett urval produkter som kan visas i rekommendationsenheten när den distribueras till butiken.

Om du vill testa en rekommendation när du arbetar i en icke-produktionsmiljö kan du hämta rekommendationsdata från en [annan källa](settings.md). På så sätt kan handlare experimentera med regler och förhandsgranska rekommendationerna innan de distribuerar till produktionen.

| Fält | Beskrivning |
|---|---|
| Namn | Produktens namn. |
| SKU | Den lagerhållningsenhet som tilldelats produkten |
| Pris | Produktens pris. |
| Resultattyp | Primär - anger att det finns tillräckligt med utbildningsdata för att visa en rekommendation.<br />Säkerhetskopiering - anger att det inte finns tillräckligt med utbildningsdata insamlade så en rekommendation för säkerhetskopiering används för att fylla platsen. Gå till [Beteendedata](behavioral-data.md) om du vill veta mer om maskininlärningsmodeller och rekommendationer för säkerhetskopiering. |

När du skapar rekommendationsenheten kan du experimentera med sidtyp, rekommendationstyp och filter för att få omedelbar feedback i realtid om de produkter som ska ingå. När du börjar förstå vilka produkter som visas kan du konfigurera rekommendationsenheten så att den uppfyller dina affärsbehov.

Adobe Commerce [filter](filters.md) rekommendationer för att undvika att visa duplicerade produkter när flera rekommendationsenheter distribueras på en sida. Det innebär att de produkter som visas på förhandsvisningspanelen kan skilja sig från de som visas i butiken.

>[!NOTE]
>
> Du kan inte förhandsgranska `Recently viewed` rekommendationstyp eftersom data inte är tillgängliga i Admin.
