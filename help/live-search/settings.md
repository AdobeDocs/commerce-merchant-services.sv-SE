---
title: '"[!DNL Live Search] Inställningar"'
description: '"Konfigurera intervall och intervall för prisfaktorer för [!DNL Live Search] facets."'
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Inställningar

Använd *Inställningar* för att konfigurera de intervall och intervall för prisfaktorer som är tillgängliga som sökfilter i butiken. Prisnivåinställningarna är statiska och inte dynamiska och baseras inte på sökresultat.

Du kan ange antalet prisintervallgrupper och hur prisvärden fördelas mellan dem. Varje prisintervall överlappar den föregående gruppen med ett. Fem grupper med intervallet 20 skapar till exempel följande prisintervall: 0-20, 20-40, 40-60, 60-80 och >80. Om det inte finns tillräckligt många produkter i katalogen för att fylla alla definierade intervall justeras visningen av tillgängliga grupper därefter. Till exempel: 0-20, 60-80, >80.

![Inställningar](assets/settings.png)

## Konfigurera grupperingar av prisfaktorer

1. Gå till Admin **Marknadsföring** > *SEO &amp; Search* > **Live Search**.
1. På **Inställningar** flik under *Prisfakturor* gör du följande:
   * Ange **Antal markeringar** eller prisgrupperingar som ska vara tillgängliga. Upp till 50 prisgrupperingar kan definieras.
   * Ange **Intervallvärde** eller prisintervall för varje grupp. Maxvärdet är 10 000.
1. Klicka **Spara**.

   Det tar ca 15 minuter innan de uppdaterade inställningarna är tillgängliga i butiken.

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| Antal markeringar | Anger antalet prisintervallgrupperingar som kan användas som sökfilter i butiken. Standardvärde: 8, Maximalt värde: 50 |
| Intervallvärde | Anger prisintervallen för varje grupp. Fem markeringar med ett intervallvärde på tjugo skapar till exempel fem grupperingar av 0-20, 20-40, 40-60, 60-80 och >80. Standardvärde: 5, Maximalt värde: 10 000 |
