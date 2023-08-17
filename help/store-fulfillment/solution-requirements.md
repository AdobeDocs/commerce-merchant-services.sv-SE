---
title: Uppfyllandekrav för butik
description: Krav för etablering och introduktion av [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Lagra uppfyllandekrav för Adobe Commerce

I följande avsnitt beskrivs de tekniska och affärsmässiga kraven för installation och aktivering av Store Fulfillment-lösningen för Adobe Commerce.

## Plattforms- och programvarukrav

The [!DNL Store Fulfillment] för Adobe Commerce-kunder på följande plattformar.

- Adobe Commerce om molninfrastruktur (ECE)
- Adobe Commerce lokalkontor

Store Fulfillment solution is compatible with the software versions listed in the *Programkompatibilitet* tabell.

**Programvarukompatibilitet**

| **Programvara** | **Minimiversion** | **Maximal version** |
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

- B2C-återförsäljare, CPG-tillverkare (Consumer Packaged Goods) som säljer direkt till konsumenter (D2C) eller distributörer som säljer direkt till konsumenter eller småföretag

- Minst ett fysiskt lager eller lagerställe

- Hantera ert produktlager med Inventory management för Adobe Commerce (även MSI)

- Möjlighet att syndikera handelslagret

- Lagra Wi-Fi-tillgänglighet på alla platser som stöder upplösningen för att uppfylla kraven i Store: 3 Mbit/s lägsta internethastighet

- De som arbetar med butiker och lagerlokaler har tillgång till de mobila enheterna iOS eller Android under bytet, antingen personliga eller från handlaren

- Produkter som hanteras med Store Fulfillment-lösningen måste ha produktattribut som innehåller antingen en SKU eller UPC-produktkod
