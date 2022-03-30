---
title: Installera och konfigurera
description: Lär dig hur du installerar, uppdaterar och avinstallerar [!DNL Product Recommendations].
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Installera och konfigurera

Distribuerar [!DNL Product Recommendations] till din butik och administratör kräver att du installerar modulen och konfigurerar Commerce Services Connector. När uppdateringarna släpps kan du enkelt uppdatera din installation med den senaste versionen.

- [Installera](#install)
- [Konfigurera](#configure)
- [Uppdatera](#update)
- [Avinstallera](#uninstall)

## Installera [!DNL Product Recommendations] {#install}

På grund av [!DNL Product Recommendations] är ett fristående metapaket, uppdateringar släpps oftare än Adobe Commerce. Om du vill vara säker på att du är uppdaterad med de senaste felkorrigeringarna och funktionerna kan du läsa [versionsinformation](release-notes.md).

Installera `magento/product-recommendations` med Composer:

```bash
composer require magento/product-recommendations
```

### Stöd för Lägg till Page Builder {#pbsupport}

[!DNL Product Recommendations] för Page Builder är en valfri modul som installeras separat. Används [!DNL Product Recommendations] Installera modulen med Page Builder genom att köra följande kommando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Genom att aktivera [!DNL Product Recommendations] i Page Builder kan du lägga till en befintlig, aktiv [rekommendationsenhet](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) till allt innehåll som skapas i Page Builder, t.ex. sidor, block och dynamiska block.

### Lägg till rekommendationstyp för visuell likhet {#vissimsupport}

The _Visuell likhet_ rekommendationstypen gör att du kan distribuera en rekommendationsenhet till produktinformationssidan som visar produkter som [visuellt liknande](type.md#visualsim) till den produkt som visas. Rekommendationstypen är mest användbar när bilder och visuella aspekter av produkterna är viktiga delar av shoppingupplevelsen. Installera _Visuell likhet_ rekommendationstyp genom att köra följande kommando:

```bash
composer require magento/module-visual-product-recommendations
```

## Konfigurera [!DNL Product Recommendations] {#configure}

När du har installerat `magento/product-recommendations` -modulen måste du konfigurera [Commerce Services Connector](https://docs.magento.com/user-guide/configuration/services/saas.html) genom att ange API-nyckeln och välja ett SaaS-dataområde.

För att katalogexporten ska fungera på rätt sätt måste du kontrollera att [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) jobb och [indexerare](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) körs och `Product Feed` indexeraren är inställd på `Update by Schedule`.

När du har länkat till Commerce Services via API-nyckeln och anger SaaS-dataområdet initieras katalogsynkroniseringen och [verifierar](verify.md) att beteendedata skickas till butiken.

## Uppdatera dina [!DNL Product Recommendations] installation {#update}

Som alla Adobe Commerce [!DNL Product Recommendations] använder Composer för installation och uppdateringar. Så här uppdaterar du `magento/product-recommendations` kör du följande:

```bash
composer update magento/product-recommendations --with-dependencies
```

Om du vill uppdatera till en större version, till exempel från 2.0 till 3.0, måste du redigera projektets rot `composer.json` -fil. (Se [versionsinformation](release-notes.md) om du vill ha information om den senaste versionen.) Låt oss till exempel öppna huvudsidan `composer.json` och sök efter `magento/product-recommendations` modul:

```json
"require": {
    ...
    "magento/product-recommendations": "^2.0",
    ...
}
```

Låt oss bump the major version from `2.0` till `3.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Spara `composer.json` och köra:

```bash
composer update magento/product-recommendations --with-dependencies
```

## Avinstallera [!DNL Product Recommendations] {#uninstall}

Om det behövs kan du [avinstallera](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) modulen för produktrekommendationer.
