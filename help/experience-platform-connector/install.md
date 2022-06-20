---
title: Installera och konfigurera Adobe Experience Platform Connector från Adobe Commerce
description: Lär dig hur du installerar, konfigurerar, uppdaterar och avinstallerar Adobe Experience Platform Connector från Adobe Commerce.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Installera och konfigurera Experience Platform-anslutning

Innan du installerar tillägget [Granska förutsättningarna](overview.md#prereqs).

## Installera tillägget

1. Installera metapaketet för anslutningsprogrammet för Experience Platform.

   ```bash
   composer require magento/platform-connector
   ```

   Det här metapaketet innehåller följande moduler:

   * `module-platform-connector-admin` - Uppdaterar administratörsgränssnittet
   * `module-platform-connector` - Anger `ImsOrgId` och `datastreamId` i Magento Storefront Events SDK

1. Installera tillägget Commerce Data Services om du vill inkludera profil- och utcheckningshändelser.

   ```bash
   composer require magento/data-services
   ```

   Tillägget Commerce Data Services tillhandahåller attributkontext för butikshändelser. När till exempel en utcheckningshändelse inträffar inkluderas information om hur många artiklar som fanns i kundvagnen och produktattributsdata för dessa objekt.

1. Installera Commerce Service Connector.

   ```bash
   composer require magento/commerce-services
   ```

   Med Commerce Service Connector kan du ansluta din Adobe Commerce-instans till [Adobe Commerce SaaS](../landing/saas.md) och Adobe Experience Platform.

1. (Valfritt) Inkludera [!DNL Live Search] data, som omfattar sökhändelser, installerar [[!DNL Live Search]](../live-search/install.md) tillägg.

## Uppdatera Experience Platform-kontakten {#update}

Om du vill uppdatera Experience Platform-kopplingen kör du följande från kommandoraden:

```bash
composer update magento/platform-connector --with-dependencies
```

Om du vill uppdatera till en större version, som 1.0.0 till 2.0.0, redigerar du projektets rot [!DNL Composer] `.json` på följande sätt:

1. Öppna roten `composer.json` fil och sök efter `magento/platform-connector`.

1. I `require` uppdaterar du versionsnumret enligt följande:

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **Spara** `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Avinstallera Experience Platform-anslutningen {#uninstall}

Information om hur du avinstallerar Experience Platform-anslutningen finns i [avinstallera moduler](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
