---
title: Arbetsyta
description: Lär dig hur du konfigurerar, hanterar och övervakar prestandan för produktrekommendationer.
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Arbetsyta

The [!DNL Product Recommendations] arbetsytan innehåller en lista med tidigare konfigurerade rekommendationer med mätvärden som hjälper dig att spåra varje rekommendations framgång. Listan kan konfigureras för att beräkna mätvärden för den sista dagen, veckan eller månaden. Du kan använda mätvärdena för att skapa användbara insikter baserat på hur ofta en rekommendationsenhet visas eller klickas, eller för att analysera hur bra dina rekommendationer fungerar.

![Recommendations arbetsyta](assets/workspace.png)
_Recommendations Workspace_

## Ange omfånget

Inledningsvis [omfång](https://docs.magento.com/user-guide/stores/websites-stores-views.html) för alla rekommendationsinställningar är inställda på `Default Store View`. Om din Commerce-installation innehåller flera butiksvyer anger du **Omfång** till [butiksvy](https://docs.magento.com/user-guide/configuration/scope.html) var dina rekommendationer gäller.

## Ange datumintervall för mätvärden

1. Klicka på **Kalender** ![Kalenderväljare](assets/icon-calendar.png) kontroll.

1. Välj något av följande:

   - De senaste 24 timmarna
   - De senaste 7 dagarna
   - De senaste 30 dagarna

   De beräknade värdena i måttkolumnerna ändras för att återspegla det aktuella datumintervallet.

## Visa/dölj kolumner

1. Klicka på i det övre vänstra hörnet **Visa/dölj** ![Kolumnväljare](assets/icon-show-hide-columns.png) kolumner.

   De synliga kolumnerna har en blå bockmarkering.

1. Gör något av följande på menyn:

   - Om du vill visa en dold kolumn klickar du på ett kolumnnamn utan bockmarkering.
   - Om du vill dölja en synlig kolumn klickar du på ett kolumnnamn med en bockmarkering.

   Tabellen uppdateras så att den endast innehåller de markerade kolumnerna.

   ![Recommendations arbetsyta](assets/workspace-select-columns.png)
   _Visa/dölj kolumner_

## Inställningar

Inställningarna bestämmer det SaaS-datautrymme som innehåller data för rekommendationer och beteenden.

- Om du vill ändra var rekommendationsbeteendedata kommer från väljer du ett annat SaaS-datautrymme.

- Om du vill konfigurera ett nytt SaaS-dataområde klickar du på **Redigera konfiguration**. Mer information finns på [Inställningar](settings.md).

![Recommendations-inställningar](assets/settings.png)
_Recommendations-inställningar_

## Visa detaljer

1. Klicka i tabellen på den rekommendation som du vill granska.

   ![Recommendations arbetsyta](assets/recommendation-detail.png)
   _Information om konverteringsgrad för startsida_

1. Om du vill ändra rekommendationens status klickar du på **Aktivera** eller **Inaktivera**.

## Redigera rekommendation

På sidan Rekommendationsinformation klickar du på **Redigera**. Om du vill veta mer går du till [Redigera Recommendations](edit.md).

## Skapa rekommendation

På sidan Rekommendationsinformation klickar du på **Skapa**. Om du vill veta mer går du till [Skapa Recommendations](create.md).

## Arbetsytekontroller

| Kontroll | Beskrivning |
|---|---|
| ![Kalenderväljare](assets/icon-calendar.png) | Anger det tidsintervall som används för måttberäkningar. Alternativ: 24 timmar/7 dagar/30 dagar |
| ![Kolumnväljare](assets/icon-show-hide-columns.png) | Bestämmer vilka kolumner som visas i dialogrutan [!DNL Product Recommendations] tabell. |
| Inställningar | Avgör det SaaS-datautrymme där rekommendationsbeteendedata hämtas, och aktiverar även rekommenderad typ för visuell likhet. |
| Skapa rekommendation | Öppnar [Skapa ny rekommendation](create.md) sida. |

## Kolumnbeskrivningar

| Kolumn | Beskrivning |
|---|---|
| Namn | Rekommendationens namn. |
| Sida | Sidan där rekommendationen visas. |
| Typ | Rekommendationstypen. |
| Status | Rekommendationsstatus. Alternativ: Inaktiv/aktiv/utkast |
| Skapad | Det datum då rekommendationen skapades. |
| Senast redigerad | Det datum då rekommendationen senast redigerades. |
| Impressions | Antalet gånger som en rekommendationsenhet läses in och återges på en sida. En rekommendationsenhet som ligger under förskjutningen av webbläsarens visningsruta återges på sidan, men visas inte av användaren. I det här fallet räknas den återgivna enheten som ett intryck, men en vy räknas bara om användaren rullar enheten så att den syns. |
| vImpressions | (Synliga exponeringar) Antal rekommendationsenheter som registrerar minst en vy. |
| Vyer | Antalet rekommendationsenheter som visas i visningsrutan i kundens webbläsare. Den här händelsen kan utlösas flera gånger på en sida. |
| Klickningar | Summan av det antal gånger en kund klickar på en artikel i rekommendationsenheten och det antal gånger som kunden klickar på **Lägg i kundvagnen** i rekommendationsenheten |
| Intäkter | Den intäkt som rekommenderas för det aktuella tidsintervallet. |
| Intäkt | (Livstidsintäkt) Den livstidsintäkt som drivs av en rekommendation. |
| Synlighet | Procentandel av rekommendationsenheter som registreras för vyn. |
| Ctrl | (Procent för registrerat klick) Procentandel av enhetsvisningar för den rekommendation som registrerar ett klick. |
| vCtr | (Synligt registrerat klickningsprocentvärde) Procentandel av visningar som kan visas för rekommendationsenheten som registrerar ett klick. |
