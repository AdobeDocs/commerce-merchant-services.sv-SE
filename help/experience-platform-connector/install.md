---
title: Installera och konfigurera Adobe Experience Platform Connector från Adobe Commerce
description: Lär dig hur du installerar, konfigurerar, uppdaterar och avinstallerar Adobe Experience Platform Connector från Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 572df7558e825a7a7c442e47af787c209dbe4ee3
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Installera och konfigurera Experience Platform-anslutningen

Innan du installerar tillägget [Granska förutsättningarna](overview.md#prereqs).

## Installera tillägget

Anslutningstillägget Experience Platform är tillgängligt från [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). När du installerar det här tillägget från serverns kommandorad ansluts det till din Adobe Commerce-installation som en [service](../landing/saas.md). När processen är klar **Experience Platform Connector** och **Commerce Services Connector** visas på **System** meny under **Tjänster** i handeln _Administratör_.

>[!NOTE]
>
>![B2B för Adobe Commerce](../assets/b2b.svg) För B2B-handlare finns det ett separat tillägg som du måste installera. Det här tillägget lägger till stöd för B2B-specifika händelser. [Läs mer](#install-the-b2b-extension).

1. Ladda ned `experience-platform-connector` paketet, kör följande från kommandoraden:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Det här metapaketet innehåller följande moduler och tillägg:

   * `module-experience-connector-admin` - Uppdaterar administratörsgränssnittet så att du kan välja dataström-ID för en viss Adobe Commerce-instans.
   * `module-experience-connector` - Anger `Organization ID` och `datastreamId` i Store Events SDK.
   * `data-services` - Anger attributkontext för storefront-händelser. När till exempel en utcheckningshändelse inträffar inkluderas information om hur många artiklar som fanns i kundvagnen och produktattributsdata för dessa objekt.
   * `services-id` - Ansluter din Adobe Commerce-instans till [Adobe Commerce SaaS](../landing/saas.md) med sandbox- och produktions-API-nycklar och till Adobe Experience Platform för att hämta IMS-organisations-ID:t.
   * `orders-connector` - Ansluter orderstatustjänsten till din Adobe Commerce-instans.

1. (Valfritt) Inkludera [!DNL Live Search] data, som [sökhändelser](events.md#search-events), installera [[!DNL Live Search]](../live-search/install.md) tillägg.

### Konfigurera orderkopplingen

När du har installerat `experience-platform-connector`måste du slutföra installationen av `orders-connector` baserat på distributionstyp: lokalt eller Adobe Commerce i molninfrastrukturen.

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

I Adobe Commerce om Cloud-infrastrukturen aktiverar du `ENABLE_EVENTING` global variabel i `.magento.env.yaml`. [Läs mer](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

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

För B2B-handlare installerar du följande tillägg för att inkludera [rekvisitionslista](events.md#b2b-events) händelsedata.

Ladda ned `magento/experience-platform-connector-b2b` genom att köra följande från kommandoraden:

```bash
composer require magento/experience-platform-connector-b2b
```

## Uppdatera Experience Platform-kontakten {#update}

Om du vill uppdatera Experience Platform-kopplingen kör du följande från kommandoraden:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

eller, för B2B-handlare:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Om du vill uppdatera till en större version, till exempel från 1.0.0 till 2.0.0, redigerar du projektets rot [!DNL Composer] `.json` på följande sätt:

1. Öppna roten `composer.json` fil och sök efter `magento/experience-platform-connector`.

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

   eller, för B2B-handlare:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Avinstallera Experience Platform-anslutningen {#uninstall}

Information om hur du avinstallerar Experience Platform-anslutningen finns i [avinstallera moduler](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
