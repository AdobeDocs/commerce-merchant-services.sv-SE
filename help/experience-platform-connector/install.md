---
title: Installera och konfigurera Adobe Experience Platform Connector från Adobe Commerce
description: Lär dig hur du installerar, konfigurerar, uppdaterar och avinstallerar Adobe Experience Platform Connector från Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: ce437d7a991affd2665c86c9e91bb7f39ec626c0
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Installera och konfigurera Experience Platform-anslutning

Innan du installerar tillägget [Granska förutsättningarna](overview.md#prereqs).

## Installera tillägget

1. Installera metapaketet för anslutningsprogrammet för Experience Platform.

   ```bash
   composer require magento/experience-platform-connector
   ```

   Det här metapaketet innehåller följande moduler och tillägg:

   * `module-platform-connector-admin` - Uppdaterar administratörsgränssnittet så att du kan konfigurera dataström-ID:t
   * `module-platform-connector` - Anger `ImsOrgId` och `datastreamId` i Adobe Commerce Storefront Event SDK
   * `data-services` - Anger attributkontext för storefront-händelser. När till exempel en utcheckningshändelse inträffar inkluderas information om hur många artiklar som fanns i kundvagnen och produktattributsdata för dessa objekt.
   * `commerce-services` - Ansluter din Adobe Commerce-instans till [Adobe Commerce SaaS](../landing/saas.md) med API-nycklar för sandlåda och produktion och till Adobe Experience Platform med IMS Organization ID.

1. (Valfritt) Inkludera [!DNL Live Search] data, som omfattar sökhändelser, installerar [[!DNL Live Search]](../live-search/install.md) tillägg.

## Uppdatera Experience Platform-kontakten {#update}

Om du vill uppdatera Experience Platform-kopplingen kör du följande från kommandoraden:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Om du vill uppdatera till en större version, som 1.0.0 till 2.0.0, redigerar du projektets rot [!DNL Composer] `.json` på följande sätt:

1. Öppna roten `composer.json` fil och sök efter `magento/platform-connector`.

1. I `require` uppdaterar du versionsnumret enligt följande:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **Spara** `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

## Avinstallera Experience Platform-anslutningen {#uninstall}

Information om hur du avinstallerar Experience Platform-anslutningen finns i [avinstallera moduler](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
