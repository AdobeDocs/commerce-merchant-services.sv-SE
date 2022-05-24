---
title: Anonboard "[!DNL Store Fulfillment]"
description: Anslut din Commerce-instans till [!DNL Store Fulfillment Manager] genom att utföra några steg.
role: User, Admin
level: Intermediate
source-git-commit: 24639b75d3c629856fbb8fc74e7eb072d4197815
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Fulfillment för butik inbyggt av Walmart Technologies

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

## Förutsättningar

* **Information om handelskonto**-Hämta och installera [!DNL Channel Manager] kräver [Handelskonto](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Du behöver ett konto-ID och autentiseringsuppgifter med ägar- eller administratörsåtkomst till [!DNL Adobe Commerce] eller [!DNL Magento Open Source] -instans.

* För [!DNL Adobe Commerce] i molninfrastrukturprojekt måste programinstallerare ha följande åtkomst till [!DNL Commerce] instans:

   * Superanvändaråtkomst till Cloud-projektet
   * Administratörsåtkomst till en viss miljö
   * An [!DNL Adobe Commerce] eller [!DNL Magento Open Source] konto med behörighet att komma åt Composer-databasen

      Se [Hantera användaråtkomst](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Tillgång till Store Fulfillment från Walmart Technologies programarkiv för installation av Store Fulfillment-lösningen på din Adobe Commerce-instans**-Din kundkontorepresentant kan ge åtkomst till installationsfilen för tillägget.

* **Upplevelse med Composer och[!DNL Commerce CLI]** -See [Allmän CLI-installation](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} om du vill ha information om hur du använder verktygen för att installera och hantera tillägg på [!DNL Adobe Commerce] och [!DNL Magento Open Source] -plattformar.

* [!DNL Inventory Management] tillägg för Adobe Commerce och Magento Open Source

   Du måste ha Inventory management-tillägget installerat och aktiverat på Adobe Commerce- och Magento Open Source-instansen. Det här tillägget installeras och aktiveras som standard i Adobe Commerce och Magento Open Source 2.3.x och senare. Mer information finns i [Installera Inventory management](https://devdocs.magento.com/extensions/inventory-management/) i Adobe Commerce Developer-dokumentationen.

## Krav

Store Fulfillment solution is available for Adobe Commerce and Magento Open Source customers. Du måste uppfylla följande system- och affärskrav för att installera, driftsätta och använda lösningen.

### Systemkrav

Tillägget Store Fulfillment från Walmart Technologies har testats för kompatibilitet med följande programversioner.

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

* USA-baserat företag

* B2C-återförsäljare, CPG-tillverkare som säljer D2C eller distributörer som säljer D2C eller till mindre företag

* Minst ett fysiskt lager eller lagerställe

* Hantera ditt produktlager med Inventory management för Commerce (var MSI)

* Möjlighet att syndikera handelslagret

* Lagra Wi-Fi-tillgänglighet på alla platser som stöder upplösningen för att uppfylla kraven i Store

* De som arbetar med butiker och lagerlokaler har tillgång till de mobila enheterna iOS eller Android under bytet, antingen personliga eller tillhandahållna av handlaren

* Produkter som hanteras med Store Fulfillment-lösningen måste ha produktattribut som innehåller antingen en SKU eller UPC-produkt.

### Plattformar som stöds

* Adobe Commerce on Cloud (ECE): 2.4.x
* Adobe Commerce lokalkontor: 2.4.x
* Magento Open Source 2.4.x
