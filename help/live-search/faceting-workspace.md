---
title: "Motstående arbetsyta"
description: "Lär dig mer om [!DNL Live Search] faceting workspace."
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Motstående arbetsyta

The [!DNL Live Search] arbetsytan innehåller en lista med alla funktioner som är tillgängliga och som ger tillgång till de verktyg du behöver för att konfigurera och hantera ansikten. Fästa ansikten visas först i listan med befintliga facets, följt av dynamiska facets. Listan kan filtreras så att den visar alla aspekter, eller bara de som är fästa eller dynamiska.

![Motstående arbetsyta](assets/faceting-workspace.png)

## Ange omfånget

Om din Adobe Commerce-installation innehåller flera butiksvyer anger du **Omfång** till [butiksvy](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) där dina ansiktsinställningar gäller.

## Filtrera listan

1. Klicka på **Filtrera efter** kontroll.
1. Välj något av följande alternativ:

   * Alla filter
   * Fastnålade
   * Dynamisk

   ![Motstående arbetsyta](assets/facets-filter-by.png)

## Lägg till en fasett

1. Klicka **Lägg till ansikten**.
1. Se [Lägg till ansikten](facets-add.md) för detaljerade anvisningar.

## Kolumnbeskrivningar

| Kolumn | Beskrivning |
|--- |--- |
| (första kolumnen) | Listar fästa och dynamiska aspekter av [label](facets-type.md) som är synligt för kunden. |
| Välj typ | The [urvalsmetod](facets-type.md) som tilldelas motsvarande produktattribut. The `single select` type används för alla [!DNL Commerce] butiker. För headless-implementationer `multi-select` typ kan tilldelas med en logisk operator (`or` eller `and`) för att avgöra vilken uppsättning produkter som returneras. |
| Sorteringstyp | The [sorteringsordning](facets-type.md) av fasettvärden. Ansikten sorteras i bokstavsordning för alla [!DNL Commerce] butiker. För [headless] implementeringar kan facets sorteras antingen i bokstavsordning eller efter antal. Alternativ: Alfabetiskt, antal (endast headless) |
| Maxvärde | Antalet facet-värden som är tillgängliga i butiken som filter, maximalt 10. |

## Kontroller

| Kontroll | Beskrivning |
|--- |--- |
| Lägg till ansikten | Öppnar [facet editor](facets-add.md). |
| Filtrera efter | Bestämmer [typ av faktorer](facets-type.md) som visas i listan. Alternativ: Alla, fastnålade, dynamiska |
