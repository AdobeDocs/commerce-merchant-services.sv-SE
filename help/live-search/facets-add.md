---
title: Lägg till ansikten
description: "Lär dig hur du lägger till filterbara produktattribut som [!DNL Live Search] facets."
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Lägg till ansikten

Alla filterbara produktattribut kan användas som en fasett. The *Lägg till ansikten* På panelen visas de aktuella faktorerna och det blir enkelt att tilldela ytterligare produktattribut som facets. Under den här trestegsprocessen väljs ett attribut som ska användas som en fasett, egenskaperna redigeras vid behov och ändringarna publiceras i butiken.

![Lägg till ansikten](assets/facets-add.png)

## Steg 1: Lägg till en fasett

1. Gå till Admin **Marknadsföring** > SEO &amp; Search > **[!DNL Live Search]**.
1. På *Motsatthet* flik, klicka **Lägg till ansikten**.
1. I *Lägg till ansikten* list, each available attribute has a separate ![Knappen Lägg till](assets/btn-add.png). Fyll i något av följande:

   * I *Motsvarande attribut* väljer du det produktattribut som du vill använda som fasett och klickar på **Lägg till**.
   * Om du vill hitta ett visst produktattribut anger du de första tecknen i attributnamnet i dialogrutan *Sök* box. Klicka sedan på **Lägg till**.

     Om du vill konfigurera intervall och grupperingar för prisfakturor går du till [Inställningar](settings.md). Om du vill veta mer går du till [Fasetttyper](facets-type.md).
Fettet läggs till längst ned i *Dynamiska ansikten* -listan och *Publicera ändringar* knappen blir tillgänglig.

1. Om det inte går att hitta den aspekt du vill lägga till går du till **Lager** > Attribut > **Produkt** och verifiera att attributet har [obligatoriska egenskaper](facets.md) som ska användas som en fasett. Uppdatera vid behov följande storefront-egenskaper för attributet:

   * Använd i sökning - `Yes`
   * Använd i Sökresultat vid navigering i lager - `Yes`
   * Använd i navigering i lager - `Filterable (with results)`

1. Uppdatera cacheminnet när du uppmanas till detta.

   Faktorn blir tillgänglig i butiken nästa gång som katalogen synkroniseras med [!DNL Live Search]. Om ansiktet inte är tillgängligt inom två timmar finns mer information i [Synkronisera katalogdata](install.md#synchronize-catalog-data).

## Steg 2: Redigera fasettegenskaper (valfritt)

1. Om du vill redigera ansiktsegenskaperna klickar du på **Mer** (![Fler väljare](assets/btn-more.png)) i kolumnen längst till höger.
1. Klicka på **Redigera**. Justera sedan följande egenskaper efter behov.

   * Etikett - ([Headless](facets-type.md) bara) Ange den ansiktsetikett som du vill använda.
   * Sorteringstyp - ansikten sorteras i bokstavsordning för alla [!DNL Commerce] storefronts. För headless-implementationer kan ansiktena sorteras antingen i bokstavsordning eller efter antal. Alternativ: Alfabetisk, Antal (endast headless)
   * Maxvärde - Ange det maximala antalet fasettvärden som visas i butiken. Giltiga poster: 0 - 30; Standard: 8

1. När du är klar klickar du på **Spara**.

   ![Redigera ansikten](assets/facet-edit.png)

1. Så här fäster du ansiktet högst upp på sidan *Filter* klickar du på det grå kartnålen (![Fästväljare](assets/btn-pin-gray.png)).
1. Om du vill ändra ordningen på den fästa aspekten klickar du på **Flytta** (![Flytta väljare](assets/btn-move.png)) och dra raden till en ny plats i *Fasta ansikten* -avsnitt.

## Steg 3: Publicera ändringar

1. När ansiktet är klart klickar du **Publicera ändringar**.
1. Vänta tills ansiktet visas i butiken.
Om ansiktet inte är tillgängligt inom två timmar finns mer information i [Verifiera export](install.md#synchronize-catalog-data) i installationsanvisningarna.

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| Etikett | ([Headless](facets-type.md) only) [fasettetikett](facets-type.md) som syns i butiken kan redigeras för att vara konsekvent med ert varumärke. |
| Sorteringstyp | Den metod som används för [sortera](facets-type.md) ansikten. Alla [!DNL Commerce] storefront sorterar endast ansikten i bokstavsordning. Headless-implementationer kan också sorteras efter `Count`. Alternativ:<br />Alfabetiskt - Sorterar ansikten i bokstavsordning.<br />Antal - (endast Headless) Sorterar facet baserat på antalet träffar. |
| Maxvärde | Det maximala antalet värden som kan visas i butiken för varje aspekt. Ansikten som representerar ett värdeintervall fördelas jämnt. Giltiga poster: 0 - 30; Standard: 8 |

### Kontroller

| Kontroll | Beskrivning |
|--- |--- |
| ![Fästväljare](assets/btn-pin-blue.png) | Fäster eller häftar upp ett ansikte längst upp på sidan *Filter* lista. |
| ![Fler väljare](assets/btn-more.png) | Visar en meny med fler åtgärder som kan tillämpas på den valda aspekten. Alternativ: Redigera, Ta bort |
| ![Flytta väljare](assets/btn-move.png) | Använd *Flytta* om du vill dra en fäst yta till en annan plats i dialogrutan *Fästa ansikten* -avsnitt. |
