---
title: "Arbetsytan Sökregler"
description: "Lär dig mer om [!DNL Live Search] regelarbetsyta."
exl-id: a52839fb-2264-4443-83c3-9eaa2ccb6996
source-git-commit: 40bcae7a792660f02390f4d55967767b15c84f38
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Arbetsytan Sökregler

På arbetsytan Sökregler visas det aktuella urvalet av regler och deras status. Här finns även verktyg som du behöver för att skapa och hantera regler. Från arbetsytan kan du:

* Sök efter regler
* Visa regelinformation
* Aktivera/inaktivera regler
* Ta bort regler
* Åtkomst till regelredigeraren

![Arbetsytan Regler](assets/rules-workspace.png)

## Ange omfånget

Om din Adobe Commerce-installation innehåller flera butiksvyer ställer du in **Omfång** till [butiksvy](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) var reglerna gäller.

## Visa/dölj kolumner

1. Klicka på i det övre högra hörnet **Visa/dölj** ![Kolumnväljare](assets/btn-show-hide-columns.png) kolumner.
De synliga kolumnerna har en blå bockmarkering på alternativmenyn. Regelnamnet är den enda kolumnen som inte kan döljas.

1. Gör något av följande på menyn:

   * Om du vill visa en dold kolumn klickar du på ett kolumnnamn utan bockmarkering.
   * Om du vill dölja en synlig kolumn klickar du på ett kolumnnamn med en bock.

## Filtrera regler efter status

1. Om din butik har många regler kan du filtrera reglerna efter status för att förkorta listan. Som standard visas alla regler i listan Regler.

1. Om du bara vill visa regler med en viss statusinställning anger du **Status** till något av följande:

   * Alla
   * Aktiv
   * Inaktiv
   * Schemalagd

## Sök efter sökregler efter namn

Börja skriva regelns namn eller något ord i regelnamnet.
Sökfunktionen hittar matchande regler när du skriver. Strängen med matchande tecken markeras i namnet på varje regel som hittas.

![Regler - hitta efter namn](assets/rules-workspace-search-name.png)

## Visa detaljer

På informationspanelen visas regelnamn, status, villkor och händelser, start- och slutdatum, beskrivning och datum för senaste redigering. Regler kan aktiveras, redigeras och tas bort från informationspanelen.

1. På *Sökregler* söker du efter regeln i rutnätet som du vill visa och klickar på **Mer** (...).
1. Klicka **Visa detaljer**.
Du kan göra något av följande från panelen Visa information:

   * Redigera regel
   * Ta bort regel
   * Aktivera/inaktivera regel

1. Stäng *Visa detaljer* panel, klicka **Stäng** (X) längst upp till höger.

   ![Regel - detaljer](assets/rules-workspace-details.png)

## Kolumnbeskrivningar

| Kolumn | Beskrivning |
|--- |--- |
| Namn | Regelns namn. |
| Senast uppdaterad | Det datum då regeln senast uppdaterades. |
| Startdatum | Startdatumet för en schemalagd regel. |
| Slutdatum | Slutdatumet för en schemalagd regel. |
| Status | Den färgkodade statusen anger regelns aktuella läge. Använd statuskontrollen ovanför rutnätet för att filtrera regler efter status. Värden:<br />All status - Visar alla regler oavsett status.<br />Aktiv (blå) - Visar endast aktiva regler.<br />Schemalagd (orange) - visar endast schemalagda regler.<br />Inaktiv (grå) - visar endast inaktiva regler. |

## Kontroller

| Kontroll | Beskrivning |
|--- |--- |
| Lägg till regel | Öppnar [regelredigerare](rules-add.md). |
| Status | Filtrerar listan med regler efter status. Alternativ: Alla, Aktiva, Inaktiva, Schemalagda |
| ![Kolumnväljare](assets/btn-show-hide-columns.png) | Anger vilka kolumner som visas i rutnätet. Alternativ: Senast uppdaterad, Startdatum, Slutdatum, Status |
| Sök | Söker efter en regel efter fullständigt namn eller partiell matchning. |
| ![Fler väljare](assets/btn-more.png) | Visar en meny med fler åtgärder som kan tillämpas på den valda regeln. Alternativ: Redigera, Visa information, Ta bort |

## Regelinformation

| Fält | Beskrivning |
|--- |--- |
| Status | Regelns aktuella status. |
| Villkor | Sökfrågan som beskriver villkoren som är kopplade till regeln. |
| Startdatum | Det datum då regeln träder i kraft, om den är schemalagd. |
| Slutdatum | Det datum då regeln förfaller, om den är schemalagd. |
| Beskrivning | En kort beskrivning av regeln. |
| Senast uppdaterad | Datum och tid då regeln senast uppdaterades. |
| Aktiverad | En kontroll som ändrar regelns status. Alternativ: Aktiverad/Inaktiverad |
