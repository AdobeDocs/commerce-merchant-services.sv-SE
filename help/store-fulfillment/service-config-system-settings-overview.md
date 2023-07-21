---
title: Systemkonfigurationsöversikt
description: Lär dig mer om kategorierna med administratörskonfigurationsinställningar som finns för Store-lösningen och hur de är konfigurerade.
role: Admin
feature: Shipping/Delivery, System, Configuration
level: Intermediate
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Systemkonfigurationsöversikt

I Adobe Commerce Admin kategoriseras konfigurationsinställningarna för Store Fulfillment Services av Walmart Commerce Technologies efter typ.

**Lagra konfigurationsinställningar för uppfyllelse efter typ**

| **Typ** | **Beskrivning** | **Konfigurerbar API** |
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Inställningar för Check-In Experience](store-location-map-provider-setup.md) | Konfigurera bilens färg och biltillverkare som ska vara tillgängliga under incheckningsprocessen | Ja |
| [Användarinställningar](user-setup.md) | Hantera användarkonton, roller och behörigheter för butikskopplingar som använder appen Store Assist. omfång. | Ja |
| [Appinställningar](app-setup.md) | Granska tillgängliga konfigurationer för Store Assist App som krävs för att slutföra introduktionsprocessen. Dessa inställningar kan inte konfigureras från Adobe Commerce Admin. | Ja |


## Använd konfigurationsreferensen

Visa konfigurationsreferensen för varje inställningstyp genom att välja typnamnet i dialogrutan _Lagra konfigurationsinställningar för uppfyllelse efter typ_ tabell.

I konfigurationsreferensen för varje typ visas konfigurationsinformationen i en tabell med följande kolumnrubriker:

- **Fält** refererar till namnet på fältet som ska konfigureras

- **Beskrivning** innehåller viktig information om fältets syfte och beteende

- **Omfång** anger Adobe Commerce konfigurationsomfång för inställningen (global, webbplats, butik)

- **Obligatoriskt** värde anger om ett värde måste anges i fältet

För tekniska referenser kan du också hitta den interna konfigurationssökvägen för varje fält.

