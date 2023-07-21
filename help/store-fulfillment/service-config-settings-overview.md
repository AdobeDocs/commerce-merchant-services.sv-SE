---
title: Konfigurationsöversikt för arkivuppfyllelse
description: Lär dig mer om vilka typer av konfigurationsinställningar som finns tillgängliga för att anpassa de utökade leveransfunktionerna i Store Fulfillment-lösningen och länka till instruktioner för hur du slutför konfigurationen.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Configuration
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '386'
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
| [Inställningar för Check-In Experience](check-in-experience-setup.md) | Konfigurera bilens färg och biltillverkare som ska vara tillgängliga under incheckningsprocessen | Ja |
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
