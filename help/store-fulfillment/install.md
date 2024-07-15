---
title: Installation
description: "Installera  [!DNL Store Fulfillment solution] för en Adobe Commerce-butik med Composer för PHP."
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Installation

Slutför den inledande installationen av tillägget [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] i en icke-produktionsmiljö med köhanteraren igång och cachelagring konfigurerad för att tillåta undantagshantering. Se till att utvecklingsmiljön innehåller utvecklingsverktyg som säkerställer bästa praxis för att hantera och underhålla din Adobe Commerce-instans.

>[!TIP]
>
>Uppgradera Store Fulfillment-tillägget för Adobe Commerce lokalt genom att följa [uppgraderingsinstruktionerna](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html) i _Adobe Commerce Upgrade Guide_. Information om Adobe Commerce molninfrastruktur finns i [Uppgradera ett tillägg](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html#upgrade-an-extension) i *Commerce on Cloud Infrastructure Guide*.

## Förutsättningar

Granska [kraven](solution-requirements.md) för Store Fulfillment-lösningen och samla in nödvändig information innan du installerar eller uppgraderar [!DNL Store Fulfillment]-tillägget för Adobe Commerce.

Om du har installerat en förhandsversion eller betaversion av tillägget Store Fulfillment for Adobe Commerce använder du följande kommando för att ta bort den innan du installerar den aktuella versionen.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Installationskrav

- **Åtkomst till Store Fulfillment från Walmart Commerce Technologies software archive (.zip-fil)** - Under introduktions- och aktiveringsprocessen arbetar du med din Account Manager för att få åtkomst till installationsfilen för Store Fulfillment-tillägget.

- **Adobe Commerce-kontoinformation**-Installation av lösningen [!DNL Store Fulfillment] kräver ett [[!DNL Commerce] konto](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. Du behöver ett konto-ID och autentiseringsuppgifter med ägar- eller administratörsåtkomst till projektet [!DNL Adobe Commerce].

- För [!DNL Adobe Commerce] i molninfrastrukturprojekt måste programinstallerare ha administratörsåtkomst till molnprojektet. Se [Hantera användaråtkomst](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Upplevelse med Composer och[!DNL Commerce CLI]** - Se [Allmän CLI-installation](https://devdocs.magento.com/extensions/install/){target="_blank"} för information om hur du använder dessa verktyg för att installera och hantera tillägg på [!DNL Adobe Commerce] -plattformen.

- **Installera tillägg från tredje part på Adobe Commerce** - Se Adobe Commerce-dokumentationen för mer information.

   - [Installera ett tillägg för en instans av en Adobe Commerce i molninfrastruktur](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [Installera ett tillägg för en lokal Adobe Commerce-instans](https://devdocs.magento.com/extensions/install/).

### Steg 1: Hämta tilläggspaketet

Följ instruktionerna från din kontorepresentant för att hämta arkivfilen som innehåller Composer-paketen för installation av Store Fulfillment Services-tillägget.

### Steg 2: Extrahera tilläggsartefakter till programmet

Extrahera arkivfilen som innehåller integreringspaketet för att installera tillägget Store Fulfillment Services.

1. Skapa en målkatalog för de extraherade filerna.

   - Gå till webbserverdokumentets rotkatalog från kommandoraden.

   - Skapa en `artifacts`-katalog.

1. Extrahera arkivfilen till den nya katalogen.

1. Kontrollera att filerna har extraherats genom att granska fillistan.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Steg 3: Konfigurera din app med Composer

Använd Composer för att konfigurera källkatalogen för installationen och installera tillägget Store Fulfillment Services.

1. Konfigurera källdatabasen för Composer-installationen.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Lägg till tillägget Store Fulfillment Services i `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>För bättre prestanda på lokala Adobe Commerce-instanser kan du [uppdatera automatisk inläsning](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Steg 4: Uppgradera databasschemat och data

Slutför installationen genom att använda `bin/magento setup:upgrade` för att uppdatera databasschemat och data med de ändringar som har gjorts för att ge stöd åt Store Fulfillment-lösningen.

>[!NOTE]
>
>För Adobe Commerce-projekt för molninfrastruktur behöver du inte registrera tillägget. Genomför i stället kodändringarna från föregående steg och skicka dem till din miljögren. Kommandona för att uppdatera databasschemat och data körs automatiskt under molnbygge- och distributionsprocessen.

### Steg 5: Slutför installationen

1. Registrera tillägget hos Adobe Commerce med hjälp av CLI-kommandot `setup:upgrade` Magento.

   ```terminal
   bin/magento setup:upgrade
   ```

1. Kompilera om ditt [!DNL Commerce]-projekt om du uppmanas till det.

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

   För installationer på Adobe Commerce i molninfrastruktur [använder du SSH för att logga in i fjärrmiljön](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

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

Använd CLI-kommandot [setup:static-content:deploy](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} om det behövs för att distribuera statiska vyfiler till produktionsmiljön.

```terminal
php bin/magento setup:static-content:deploy -f
```

Alternativet `-f` krävs om du använder ett tomt tema.

>[!NOTE]
>
>Mer information finns i artikeln [Statiskt innehåll distribuera metodtips i Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) i Adobe Commerce Help Center.


