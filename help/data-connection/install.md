---
title: Installera [!DNL Data Connection]
description: Lär dig hur du installerar, uppdaterar och avinstallerar tillägget  [!DNL Data Connection] från Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 9001cd24db0941b7c7edcfd5b10464dc90084fd7
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# Installera [!DNL Data Connection]

[Granska förutsättningarna](overview.md#prereqs) innan du installerar tillägget.

## Installera tillägget

Tillägget [!DNL Data Connection] är tillgängligt från [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). När du installerar det här tillägget från serverns kommandorad ansluts det till din Adobe Commerce-installation som en [tjänst](../landing/saas.md). När processen är klar visas **[!DNL Data Connection]** och **Commerce Services Connector** på menyn **System** under **Tjänster** i Commerce _Admin_.

![[!DNL Data Connection] tilläggsadministratörsvy](assets/epc-adminui.png)

>[!IMPORTANT]
>
>Tilläggets namn har ändrats från Experience Platform till [!DNL Data Connection], men paketnamnet är fortfarande `experience-platform-connector` för att stödja bakåtkompatibilitet.

1. Om du vill hämta paketet `experience-platform-connector` kör du följande från kommandoraden:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Det här metapaketet innehåller följande moduler och tillägg:

   * `module-experience-connector-admin` - Uppdaterar administratörsgränssnittet så att du kan välja dataström-ID för en viss Adobe Commerce-instans.
   * `module-experience-connector` - Anger `Organization ID` och `datastreamId` i SDK för händelser i Storefront.
   * `data-services` - Anger attributkontext för butikshändelser. När till exempel en utcheckningshändelse inträffar inkluderas information om hur många artiklar som fanns i kundvagnen och produktattributsdata för dessa objekt.
   * `services-id` - Ansluter din Adobe Commerce-instans till [Adobe Commerce SaaS](../landing/saas.md) med API-nycklar för sandlåda och produktion och till Adobe Experience Platform för att hämta IMS-organisations-ID:t.
   * `orders-connector` - Ansluter orderstatustjänsten till din Adobe Commerce-instans.

1. (Valfritt) Installera tillägget [[!DNL Live Search]](../live-search/install.md) om du vill inkludera [!DNL Live Search]-data, som omfattar [sökhändelser](events.md#search-events).

1. (Valfritt) Om du vill inkludera B2B-data, som omfattar [rekvisitionshändelser](events.md#b2b-events), installerar du [B2B-tillägget](#install-the-b2b-extension).

### Installera Adobe I/O-händelser

När du har installerat tillägget `experience-platform-connector` måste du installera Adobe I/O Events för Adobe Commerce.

Följande steg gäller både för Adobe Commerce i molninfrastruktur och lokala installationer.

1. Om du kör Commerce 2.4.4 eller 2.4.5 använder du följande kommando för att läsa in händelsemodulerna:

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   Commerce 2.4.6 och senare laddar dessa moduler automatiskt.

1. Uppdatera projektberoenden.

   ```bash
   composer update
   ```

1. Aktivera de nya modulerna:

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

Slutför installationen baserat på distributionstyp: lokal eller Adobe Commerce i molninfrastrukturen.

#### Lokalt

I lokala miljöer måste du manuellt aktivera kodgenerering och Adobe Commerce Events:

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### On Cloud-infrastruktur

Aktivera den globala variabeln `ENABLE_EVENTING` i `.magento.env.yaml` i Adobe Commerce på Cloud-infrastrukturen. [Läs mer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

Implementera och skicka uppdaterade filer till molnmiljön. När distributionen är klar aktiverar du skicka händelser med följande kommando:

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### Installera B2B-tillägget

För B2B-handlare installerar du följande tillägg för att inkludera händelsedata för [rekvisitionslistan](events.md#b2b-events).

Hämta tillägget `magento/experience-platform-connector-b2b` genom att köra följande från kommandoraden:

```bash
composer require magento/experience-platform-connector-b2b
```

## Uppdatera tillägget [!DNL Data Connection] {#update}

Om du vill uppdatera tillägget [!DNL Data Connection] kör du följande från kommandoraden:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Eller, för B2B-handlare:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Om du vill uppdatera till en större version, till exempel från 2.0.0 till 3.0.0, redigerar du projektets rotfil [!DNL Composer] `.json` enligt följande:

1. Öppna rotfilen `composer.json` och sök efter `magento/experience-platform-connector`.

1. I avsnittet `require` ska du uppdatera versionsnumret på följande sätt:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
      ...
    }
   ```

1. **Spara** `composer.json`. Kör sedan följande från kommandoraden:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   Eller, för B2B-handlare:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Avinstallera tillägget [!DNL Data Connection] {#uninstall}

Information om hur du avinstallerar tillägget [!DNL Data Connection] finns i [avinstallationsmoduler](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
