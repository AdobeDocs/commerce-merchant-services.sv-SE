---
title: "Performance Dashboard"
description: "Den [!DNL Live Search] Prestandakontrollpanelen ger insikt i de söktermer som kunderna använder."
exl-id: ee2053fc-98c5-4d2c-9345-4d1f9a3180fb
source-git-commit: 289ac6ac464955f18f3a2448099ad459e6264941
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Instrumentpanel för prestanda

The [!DNL Live Search] Prestandakontrollpanelen ger insikt i de söktermer som kunderna använder. Informationen kan användas för att identifiera trender, öka klickfrekvensen och förbättra konverteringsgraden. Kontrollpanelen för prestanda innehåller en ögonblicksbild av sökstatistik för ett visst datumintervall och följande rapporter:

* Unika sökningar
* Nollresultat
* Populära resultat

![Prestanda](assets/performance-unique-searches.png)

Du kan även använda [Instrumentpanel för datahantering](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) för mer information om datasynkronisering.

## Visa en rapport

1. Ange **Datumintervall** klickar du på kalendern (![Kalender](assets/btn-calendar.png)) och gör något av följande:

   * Om du vill ange ett enstaka datum dubbelklickar du på datumet i kalendern.
   * Om du vill ange ett datumintervall klickar du på det första och det sista datumet i kalendern.

>[!NOTE]
>
>Kontrollpanelen för prestanda uppdateras var 12:e timme.

## Fältbeskrivningar

| Ögonblicksbildsdata | Beskrivning |
|--- |--- |
| Unika sökningar | Det totala antalet unika sökningar för det angivna datumintervallet. Flera sökningar av samma kund, även om de avser samma fråga, anses unika om de skickas med mer än en timmes mellanrum. |
| Genomklickningsfrekvens | Hur många procent av sökningarna som avslutas när kunden klickar på en produkt. Klickfrekvensen är till exempel 50 % om kunden söker efter &quot;byxor&quot; och &quot;skjorta&quot; och sedan klickar på ett resultat i &quot;skjortsökningen&quot;. |
| Konverteringsgrad | Procentandelen produkter som kunden köper jämfört med antalet produkter som kunden klickar på för det angivna datumintervallet. Konverteringsgraden för interaktionen är till exempel 100 % om kunden tittar på sex produkter i povern, klickar på en och gör ett köp. <br /><br />Konverteringsgraden påverkas inte av antalet visningar för en viss produkt. Konverteringsgraden är till exempel densamma om kunden använder sökfunktionen, men klickar inte på några produkter. |
| Nollresultatfrekvens | Procentandelen unika sökningar som inte returnerar några resultat för det angivna datumintervallet. Exempelvis är nollresultatfrekvensen 66,67 % om användaren söker efter &quot;fjajfjjfjf&quot; två gånger (utan resultat) och efter &quot;byxor&quot; en gång (med resultat). |
| Medel. klickningsposition | Den relativa positionen för den genomsnittliga klickfrekvensen baserat på unika sökningar för det angivna datumintervallet. |

| Rapporter | Beskrivning |
|--- |--- |
| Unika sökningar | Visar en lista med unika sökfrågor som används under det angivna datumintervallet. Rapportdata beräknas på samma sätt som unika data för ögonblicksbilder av sökningar. Om en kund skriver samma sökfråga två gånger, men med mer än en timmes mellanrum, betraktas sökningen som två unika sökningar. Rapportgräns: De 500 vanligaste villkoren |
| Nollresultat | Visar en lista över sökfrågor som inte returnerar några resultat och det antal gånger som används under det angivna datumintervallet. Rapportgräns: De 500 vanligaste villkoren |
| Populära resultat | Visar namnen på de produkter som har fått flest vyer under det angivna datumintervallet. Populära resultat beräknas endast utifrån visningar och påverkas inte av antalet klick eller genererade intäkter. Rapportgräns: De 500 vanligaste villkoren |
