---
title: Installation
description: Lägg till beskrivning
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Installation

Fullständig installation av [!DNL Store Fulfillment] tillägg i en icke-produktionsmiljö där köhanteraren körs och cachelagring har konfigurerats för att tillåta undantagshantering. Miljön bör innehålla alla andra utvecklingsverktyg för att säkerställa bästa praxis för drift och underhåll av din Adobe Commerce-instans.

## Förutsättningar

Granska [krav](solution-requirements.md) för lösningen Store Fulfillment och samla in nödvändig information innan du installerar [!DNL Store Fulfillment] för Adobe Commerce.

Om du har installerat en förhandsversion eller en betaversion av tillägget Store Fulfillment for Adobe Commerce tar du bort den innan du installerar den aktuella versionen.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Installationskrav

- **Tillgång till Store Fulfillment från Walmart Commerce Technologies software archive (.zip file)**-Under introduktions- och aktiveringsprocessen kan du samarbeta med din kontohanterare för att få tillgång till installationsfilen för tillägget Store Fulfillment.

- **Adobe Commerce-kontoinformation**-Installing [!DNL Channel Manager] kräver [Handelskonto](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Du behöver ett konto-ID och autentiseringsuppgifter med ägar- eller administratörsåtkomst till [!DNL Adobe Commerce] projekt.

- För [!DNL Adobe Commerce] i molninfrastrukturprojekt måste installationsprogram ha administratörsåtkomst till Cloud-projektet. Se [Hantera användaråtkomst](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Upplevelse med Composer och[!DNL Commerce CLI]**—Se [Allmän CLI-installation](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} om du vill ha information om hur du använder verktygen för att installera och hantera tillägg på [!DNL Adobe Commerce] plattform.

- **Installera tillägg från tredje part på Adobe Commerce**-Mer information finns i Adobe Commerce-dokumentationen.

   - [Installera ett tillägg för en instans av en Adobe Commerce i molninfrastruktur](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension)

   - [Installera ett tillägg för en lokal Adobe Commerce-instans](https://devdocs.magento.com/extensions/install/)

### Steg 1: Hämta tilläggspaketet

Följ instruktionerna från din kontorepresentant för att hämta arkivfilen som innehåller Composer-paketen för installation av Store Fulfillment Services-tillägget.

### Steg 2: Extrahera tilläggsartefakter till programmet

Extrahera arkivfilen som innehåller integreringspaketet för att installera tillägget Store Fulfillment Services.

1. Skapa en målkatalog för de extraherade filerna.

   - Gå till webbserverdokumentets rotkatalog från kommandoraden.

   - Skapa en `artifacts` katalog.

1. Extrahera arkivfilen till den nya katalogen.

1. Kontrollera att de extraherade filerna finns i fillistan.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Steg 3: Konfigurera appen med Composer

Använd Composer för att konfigurera källkatalogen för installationen och installera tillägget Store Fulfillment Services.

1. Konfigurera källdatabasen för Composer-installationen.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Lägg till tillägget Store Fulfillment Services i `composer.json`

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>För bättre prestanda på Adobe Commerce lokala instanser kan du [uppdatera konfigurationen för automatisk inläsning](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Steg 4: Uppgradera databasschemat och data

Slutför installationen med `bin/magento setup:upgrade` för att uppdatera databasschemat och data med ändringar som stöder lösningen för att uppfylla kraven i Store.

>Obs!
>För Adobe Commerce-projekt för molninfrastruktur behöver du inte registrera tillägget. Genomför i stället kodändringarna från föregående steg och skicka dem till din miljögren. Kommandona för att uppdatera databasschemat och data körs automatiskt under molnbygge- och distributionsprocessen.

### Steg 5: Slutför installationen

1. Registrera tillägget hos Adobe Commerce med `setup:upgrade` Magento CLI-kommando.

   ```terminal
   bin/magento setup:upgrade
   ```

1. Kompilera om [!DNL Commerce] projekt.

   ```bash
   bin/magento setup:di:compile
   ```

1. Rensa cachen.

   ```bash
   bin/magento cache:clean
   ```

1. Inaktivera underhållsläge.

   ```bash
   bin/magento maintenance:disable
   ```

### Steg 6: Verifiera installationen

Kontrollera att modulerna för tillägget Store Fulfillment Services är installerade och aktiverade på Adobe Commerce-servern.

1. Logga in på servern.

   För installationer på Adobe Commerce i molninfrastruktur använder du SSH för att logga in på fjärrmiljön.

1. Kontrollera att Butiksmodulerna för Fulfillment Services är aktiverade.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   Utdata ska omfatta följande moduler:

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Ytterligare steg

Använd [konfiguration:static-content: driftsätta](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#setupstatic-contentdeploy) CLI-kommando för att distribuera statiska vyfiler till produktionsmiljön.

```terminal
php bin/magento setup:static-content:deploy -f
```

The `-f` om du använder ett tomt tema.

>[!NOTE]
>
>Mer information finns i [Statiskt innehåll distribuerar metodtips i Adobe Commerce](https://support.magento.com/hc/en-us/articles/360031624091) i Adobe Commerce Help Center.

