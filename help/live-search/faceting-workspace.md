---
title: "Motstående Workspace"
description: "Lär dig mer om arbetsytan i  [!DNL Live Search] faceting."
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Motstående Workspace

På arbetsytan *Motstående* visas alla aspekter som för närvarande är tillgängliga och som ger tillgång till de verktyg du behöver för att konfigurera och hantera ansikten. Fästa ansikten visas först i listan med befintliga ansikten, följt av dynamiska ansikten. Listan kan filtreras så att den visar alla aspekter, eller bara de som är fästa eller dynamiska.

![Motstående arbetsyta](assets/faceting-workspace.png)

## Ange omfånget

Om din Adobe Commerce-installation innehåller flera butiksvyer anger du **Scope** till [butiksvyn](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) där dina facet-inställningar gäller.

## Filtrera listan

1. Klicka på kontrollen **Filter efter**.
1. Välj något av följande alternativ:

   * Alla filter
   * Fastnålade
   * Dynamisk

## Lägg till en fasett

1. Klicka på **Lägg till ansikten**.
1. Mer information finns i [Lägg till ansikten](facets-add.md).

## Kolumnbeskrivningar

| Kolumn | Beskrivning |
|--- |--- |
| (första kolumnen) | Visar fasta och dynamiska aspekter av den [etikett](facets-type.md) som är synlig för kunden. |
| Sorteringstyp | [sorteringsordningen](facets-type.md) för fasettvärden. Ansikten sorteras i bokstavsordning för alla [!DNL Commerce]-butiker. För [headless]-implementeringar kan facets sorteras antingen i bokstavsordning eller utifrån antal. Alternativ: Alfabetisk, Antal (endast headless) |
| Maxvärde | Antalet facet-värden som är tillgängliga i butiken som filter, maximalt 10. |

## Kontroller

| Kontroll | Beskrivning |
|--- |--- |
| Lägg till ansikten | Öppnar [facet-redigeraren](facets-add.md). |
| Filtrera efter | Avgör vilken [typ av facets](facets-type.md) som visas i listan. Alternativ: Alla, Fastnålade, Dynamiska |
