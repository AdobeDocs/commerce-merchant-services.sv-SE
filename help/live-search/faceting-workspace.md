---
title: "Motstående arbetsyta"
description: "Lär dig mer om [!DNL Live Search] faceting workspace."
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: e166c8cb9d715dce573195a188b5335c02d8fd0c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Motstående arbetsyta

The [!DNL Live Search] arbetsytan innehåller en lista med alla funktioner som är tillgängliga och som ger tillgång till de verktyg du behöver för att konfigurera och hantera ansikten. Fästa ansikten visas först i listan med befintliga ansikten, följt av dynamiska ansikten. Listan kan filtreras så att den visar alla aspekter, eller bara de som är fästa eller dynamiska.

![Motstående arbetsyta](assets/faceting-workspace.png)

## Ange omfånget

Om din Adobe Commerce-installation innehåller flera butiksvyer ställer du in **Omfång** till [butiksvy](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) där dina facet-inställningar gäller.

## Filtrera listan

1. Klicka på **Filtrera efter** kontroll.
1. Välj något av följande alternativ:

   * Alla filter
   * Fastnålade
   * Dynamisk

## Lägg till en fasett

1. Klicka **Lägg till ansikten**.
1. Se [Lägg till ansikten](facets-add.md) för detaljerade anvisningar.

## Kolumnbeskrivningar

| Kolumn | Beskrivning |
|--- |--- |
| (första kolumnen) | Listar fästa och dynamiska aspekter av [label](facets-type.md) som är synligt för kunden. |
| Sorteringstyp | The [sorteringsordning](facets-type.md) av fasettvärden. Ansikten sorteras i bokstavsordning för alla [!DNL Commerce] storefronts. För [headless] implementeringar kan facets sorteras antingen i bokstavsordning eller efter antal. Alternativ: Alfabetisk, Antal (endast headless) |
| Maxvärde | Antalet facet-värden som är tillgängliga i butiken som filter, maximalt 10. |

## Kontroller

| Kontroll | Beskrivning |
|--- |--- |
| Lägg till ansikten | Öppnar [facet editor](facets-add.md). |
| Filtrera efter | Bestämmer [typ av faktablad](facets-type.md) som visas i listan. Alternativ: Alla, Fastnålade, Dynamiska |
