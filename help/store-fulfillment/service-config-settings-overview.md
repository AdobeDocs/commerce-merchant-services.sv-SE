---
title: Konfigurationsöversikt för arkivuppfyllelse
description: Lär dig mer om kategorierna med administratörskonfigurationsinställningar som finns för Store-lösningen och hur de är konfigurerade.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Konfigurationsöversikt för arkivuppfyllelse

I Adobe Commerce Admin kategoriseras konfigurationsinställningarna för Store Fulfillment Services av Walmart Commerce Technologies efter typ.

**Lagra konfigurationsinställningar för uppfyllelse efter typ**

| **Typ** | **Beskrivning** | **Konfigurerbar API** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Allmän konfiguration](enable-general.md) | Allmän integrering har konfigurerats för Store Fulfillment-lösningen, dess aktiva funktioner och autentiseringsuppgifter för att ansluta till sluttjänster. | Nej |
| [E-postkonfiguration för försäljning](sales-emails.md) | Skapa ytterligare e-postmallar för kundmeddelanden som skickas under incheckningsprocessen. | Nej |
| [Konfiguration av handelslager](merchant-store-configuration.md) | Konfigurera förbättrade Inventory management-källor som butiker. | Ja |
| [Product Stock Management](product-stock.md) | Konfigurera butiksmeddelanden och funktioner som är tillgängliga för kunderna. | Ja |
| [Inventory management Source Transfer](inventory-stock-transfer.md) | Ställ in ett nytt lager, överför lager från standardlager. | Ja |
| [Konfiguration av flera webbplatser/scope](multi-site-and-scope-config.md) | Konfigurera lager och leveransmetoder för flera webbplatser/butiksomfattningar. | Nej |
| [Systemkonfiguration för bakgrundsprocess](background-processes.md) | Konfigurera scheman för bakgrundsprocesser som används för att synkronisera data med sluttjänster. | Nej |
| [Lagringsplats och mappningsinställningar](store-location-map-provider-setup.md) | Konfigurera möjligheten att använda en distansleverantör för att söka efter butiker och visa den här informationen i SLS-kartan | Ja |
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
