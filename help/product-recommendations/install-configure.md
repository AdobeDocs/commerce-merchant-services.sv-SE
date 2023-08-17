---
title: Installera och konfigurera
description: Lär dig installera, uppdatera och avinstallera [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# Installera och konfigurera

Distribuerar [!DNL Product Recommendations] till din butik och administratören kräver att du installerar modulen och konfigurerar [Commerce Services Connector](../landing/saas.md). När uppdateringarna släpps kan du enkelt uppdatera din installation med den senaste versionen.

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

### Stöd för Page Builder {#pbsupport}

[!DNL Product Recommendations] för Page Builder är en valfri modul som installeras separat. Används [!DNL Product Recommendations] Installera modulen med Page Builder genom att köra följande kommando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Genom att aktivera [!DNL Product Recommendations] i Page Builder kan du lägga till en befintlig, aktiv [rekommendationsenhet](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) till allt innehåll som skapas i Page Builder, t.ex. sidor, block och dynamiska block.

Se [Använda [!DNL Product Recommendations] med Page Builder-innehåll](page-builder.md) för ytterligare instruktioner.

### Lägg till rekommendationstyp för visuell likhet {#vissimsupport}

The _Visuell likhet_ rekommendationstypen gör att du kan distribuera en rekommendationsenhet till produktinformationssidan som visar produkter som [visuellt liknande](type.md#visualsim) till den produkt som ska visas. Rekommendationstypen är mest användbar när bilder och visuella aspekter av produkterna är viktiga delar av shoppingupplevelsen. Installera _Visuell likhet_ rekommendationstyp genom att köra följande kommando:

```bash
composer require magento/module-visual-product-recommendations
```

## Konfigurera [!DNL Product Recommendations] {#configure}

När du har installerat `magento/product-recommendations` -modulen måste du konfigurera [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) genom att ange API-nycklar och välja ett SaaS-dataområde.

För att katalogexporten ska fungera på rätt sätt måste du kontrollera att [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) jobb och [indexerare](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) körs och `Product Feed` indexeraren har värdet `Update by Schedule`.

När du har länkat till Commerce Services via API-nycklar och angett SaaS-datamängd börjar katalogsynkroniseringen. Då kan du [verifiera](verify.md) att beteendedata skickas till butiken.

## Uppdatera dina [!DNL Product Recommendations] installation {#update}

Som alla Adobe Commerce, [!DNL Product Recommendations] använder Composer för installation och uppdateringar. Uppdatera `magento/product-recommendations` kör du följande:

```bash
composer update magento/product-recommendations --with-dependencies
```

Om du vill uppdatera till en huvudversion, som 3.0 till 4.0, måste du redigera roten `composer.json` -fil för ditt projekt. (Se [versionsinformation](release-notes.md) för information om den senaste versionen.) Låt oss till exempel öppna huvudsidan `composer.json` och sök efter `magento/product-recommendations` modul:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Låt oss bump the major version from `3.0` till `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Spara `composer.json` och köra:

```bash
composer update magento/product-recommendations --with-dependencies
```

Eller om du har installerat `magento/module-visual-product-recommendations` och `magento/module-page-builder-product-recommendations` moduler:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> I version 3.x.x av Product Recommendations behövde du bara en API-nyckel. I version 4.x.x och senare måste du ange offentliga och privata API-nycklar för Production samt offentliga och privata API-nycklar för Sandbox. Om du inte anger båda par API-nycklar kan du inte komma åt Recommendations-funktionen Product i Admin. Datainsamlingen fortsätter dock i er butik och befintliga rekommendationer visas även fortsättningsvis för era kunder.

## Brandväggar

Om du vill låta Product Recommendations gå igenom en brandvägg lägger du till `commerce.adobe.io` till tillåtelselista.

## Avinstallera [!DNL Product Recommendations] {#uninstall}

Du kan [avinstallera](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) modulen för produktrekommendationer.
