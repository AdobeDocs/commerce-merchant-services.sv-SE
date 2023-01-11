---
title: Uppfyllandekrav för butik
description: Krav för etablering och introduktion av [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 842d5b7182d54a1aa5a715662503801816a24c24
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 2%

---

# Lagra uppfyllandekrav för Adobe Commerce

Du måste uppfylla följande tekniska och affärsmässiga krav för att kunna installera och aktivera Store Fulfillment-lösningen för Adobe Commerce.

## Plattforms- och programvaruversionskrav

The [!DNL Store Fulfillment] för Adobe Commerce-kunder på följande plattformar.

- Adobe Commerce om molninfrastruktur (ECE)
- Adobe Commerce lokalkontor

Store Fulfillment solution is compatible with the software versions listed in the *Programkompatibilitet* tabell.

**Programkompatibilitet**

| **Mjukvara** | **Minimiversion** | **Maximal version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Disposition | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Mer information finns i Adobe Commerce [Systemkrav](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) i *Installationshandbok för Adobe Commerce*.

## Appkrav för Store Assist

Hela processen för att hantera inköpsorder hanteras via Store Assist-appen som är installerad på mobila enheter. Dessa enheter - som tillhandahålls av återförsäljaren eller av butikspersonal som använder sina personliga smarttelefoner - måste uppfylla följande krav:

**Lägsta krav för operativsystem**

- Android 6
- iOS 12

**Lägsta maskinvarukrav**

- 1 GB RAM
- 600 MB ledigt hårddiskutrymme

## Affärskrav

Företaget måste uppfylla följande minimikriterier för att implementera Store Fulfillment-lösningen:

- Endast USA-baserade företag

- B2C-återförsäljare, CPG-tillverkare som säljer D2C eller distributörer som säljer D2C eller till mindre företag

- Minst ett fysiskt lager eller lagerställe

- Hantera ert produktlager med Inventory management för Adobe Commerce (även MSI)

- Möjlighet att syndikera handelslagret

- Lagra Wi-Fi-tillgänglighet på alla platser som stöder lösningen för att uppfylla kraven i Store: 3 Mbit/s lägsta internethastighet

- De som arbetar med butiker och lagerlokaler har tillgång till de mobila enheterna iOS eller Android under bytet, antingen personliga eller tillhandahållna av handlaren

- Produkter som hanteras med Store Fulfillment-lösningen måste ha produktattribut som innehåller antingen en SKU eller UPC-produktkod
