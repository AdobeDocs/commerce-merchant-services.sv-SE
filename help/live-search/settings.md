---
title: "[!DNL Live Search] Inställningar"
description: "Konfigurera inställningar för [!DNL Live Search] service."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: eefae3c849545062012cea1a7092c27f7df56b58
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Inställningar

Använd *Inställningar* för att konfigurera intervall och intervall för prisfaktor och standardspråk för indexet.

Prisfakteting anger antalet prisintervallgrupper och hur prisvärden fördelas mellan dem.

Språkinställningarna anger [!DNL Live Search] anger vilket språk som ska förväntas när indexet skrivs.

![Inställningar](assets/settings.png)

## Prisfakturor

Du kan ange antalet prisintervallgrupper och hur prisvärden fördelas mellan dem. Varje prisintervall överlappar den föregående gruppen med ett. Fem grupper med intervallet 20 skapar till exempel följande prisintervall: 0-20, 20-40, 40-60, 60-80 och >80. Om det inte finns tillräckligt många produkter i katalogen för att fylla alla definierade intervall justeras visningen av tillgängliga grupper därefter. Exempel: 0-20, 60-80, >80.

1. Gå till Admin **Marknadsföring** > *SEO &amp; Search* > **[!DNL Live Search]**.
1. På **Inställningar** flik under *Prisfakturor* gör du följande:
   * Ange **Antal markeringar** eller prisgrupperingar som ska vara tillgängliga. Upp till 50 prisgrupperingar kan definieras.
   * Ange **Intervallvärde** eller prisintervall för varje grupp. Maxvärdet är 10 000.
1. Klicka **Spara**.

   Det tar ca 15 minuter innan de uppdaterade inställningarna är tillgängliga i butiken.

### Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| Antal markeringar | Anger antalet prisintervallgrupperingar som kan användas som sökfilter i butiken. Standardvärde: 8, maximalt värde: 50 |
| Intervallvärde | Anger prisintervallen för varje grupp. Fem markeringar med ett intervallvärde på 20 skapar till exempel fem grupperingar av 0-20, 20-40, 40-60, 60-80 och >80. Standardvärde: 5, maximalt värde: 10 000 |

<!-- ## Language

The Language setting tells [!DNL Live Search] which language to expect when reading the catalog and writing the index. 

Languages have different sets of rules for grammar: how words are separated, verb tenses and synonyms, for example.
The Language setting ensures that the correct set of rules are applied to the indexing mechanism.

The Language settings should be set to the primary language of the catalog. -->
