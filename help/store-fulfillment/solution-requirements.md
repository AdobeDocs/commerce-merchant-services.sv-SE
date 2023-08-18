---
title: Uppfyllandekrav för butik
description: Krav för etablering och introduktion av [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Lagra uppfyllandekrav för Adobe Commerce

I följande avsnitt beskrivs de tekniska och affärsmässiga kraven för installation och aktivering av Store Fulfillment-lösningen för Adobe Commerce.

## Plattforms- och programvarukrav

The [!DNL Store Fulfillment] för Adobe Commerce-kunder på följande plattformar.

- Adobe Commerce om molninfrastruktur (ECE)
- Adobe Commerce lokalkontor

Innan du installerar eller uppgraderar bör du läsa versionsinformationen och Adobe Commerce systemkrav för att få den senaste informationen om versionskompatibilitet, uppdateringar eller ändringar som kan påverka installations- eller uppgraderingskraven.

- [Lagra versionsinformation för uppfyllelse](release-notes.md)

- [Versionsinformation för Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/release/versions.html) i *Adobe Commerce versionsinformation*.

- [Systemkrav för Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) i *Installationshandbok för Adobe Commerce*.


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
