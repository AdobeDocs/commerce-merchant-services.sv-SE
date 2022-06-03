---
title: Översikt över introduktion
description: '"Koppla samman [!DNL Commerce] till [!DNL Store Fulfillment Manager] genom att slutföra några steg i introduktionen."'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 1%

---

# Översikt över introduktion

Onboard Store Fulfillment genom att installera tillägget på din Commerce-instans och konfigurera API-anslutningarna. Dessa anslutningar möjliggör kommunikation och datasynkronisering mellan din Commerce-instans, tredjepartssystem för lagerhantering och appen Store Assist.

När du är klar med introduktionen konfigurerar och hanterar du lösningen från Commerce Admin

![[!DNL Store Fulfillment Service] konfiguration i administratörsvyn](assets/store-fulfillment-admin-home.png)

## Översikt över introduktion

1. Installera Store Fulfillment by Walmart Technologies-tillägget för Adobe Commerce.

1. Från Admin kan du aktivera lösningen och slutföra den allmänna konfigurationen för integreringen, dess aktiva funktioner och fylla i formuläret för registrering av introduktion för att ansluta till sluttjänster.

1. Konfigurera leveransmetoder.

1. Konfigurera källor som fysiska butiker och konfigurera produkter i katalogen.

1. Välj och konfigurera e-postmallarna för att hantera kundkommunikation för köp online- och upphämtningstransaktioner (BOPIS).

1. Skapa användare och roller för Store Assist-appen.

1. Konfigurera scheman för bakgrundsprocesser för att synkronisera data till sluttjänsten.

## Krav

Du måste uppfylla följande krav för att installera, distribuera och använda lösningen.

* **Information om handelskonto**-Installing [!DNL Channel Manager] kräver [Handelskonto](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Du behöver ett konto-ID och autentiseringsuppgifter med ägar- eller administratörsåtkomst till [!DNL Adobe Commerce] -instans.

* För [!DNL Adobe Commerce] i molninfrastrukturprojekt måste installationsprogram ha administratörsåtkomst till Cloud-projektet. Se [Hantera användaråtkomst](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Tillgång till Store Fulfillment från Walmart Technologies software archive (.zip file) för installation av Store Fulfillment solution**-Under introduktions- och aktiveringsprocessen kommer kundkontorepresentanten att ge nedladdningsåtkomst till installationsfilen.

* **Upplevelse med Composer och[!DNL Commerce CLI]**—Se [Allmän CLI-installation](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} om du vill ha information om hur du använder verktygen för att installera och hantera tillägg på [!DNL Adobe Commerce] och [!DNL Magento Open Source] -plattformar.

* [!DNL Inventory Management] tillägg för Adobe Commerce och Magento Open Source

   Du måste ha Inventory management-tillägget installerat och aktiverat på Adobe Commerce- och Magento Open Source-instansen. Det här tillägget installeras och aktiveras som standard i Adobe Commerce 2.3.x och senare. Mer information finns i [Installera Inventory management](https://devdocs.magento.com/extensions/inventory-management/) i Adobe Commerce Developer-dokumentationen.

## Plattforms- och versionskrav

The [!DNL Store Fulfillment] för Adobe Commerce-kunder på följande plattformar.

* Adobe Commerce om molninfrastruktur (ECE)
* Adobe Commerce lokalkontor

Store Fulfillment Solution is compatible with the following software versions.

**Programkompatibilitet**

| **Mjukvara** | **Minimiversion** | **Maximal version** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| Disposition | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Mer information finns i Adobe Commerce [Systemkrav](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) i utvecklardokumentationen.

### Krav

Företaget måste uppfylla följande minimikrav för att implementera Store Fulfillment-lösningen.

* Endast USA-baserade företag

* B2C-återförsäljare, CPG-tillverkare som säljer D2C eller distributörer som säljer D2C eller till mindre företag

* Minst ett fysiskt lager eller lagerställe

* Hantera ditt produktlager med Inventory management för Adobe Commerce (var MSI)

* Möjlighet att syndikera handelslagret

* Lagra Wi-Fi-tillgänglighet på alla platser som stöder upplösningen för att uppfylla kraven i Store

* De som arbetar med butiker och lagerlokaler har tillgång till de mobila enheterna iOS eller Android under bytet, antingen personliga eller tillhandahållna av handlaren

* Produkter som hanteras med Store Fulfillment-lösningen måste ha produktattribut som innehåller antingen en SKU eller UPC-produktkod
