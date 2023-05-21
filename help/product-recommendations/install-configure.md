---
title: Installera och konfigurera
description: Lär dig hur du installerar, uppdaterar och avinstallerar [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '501'
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

### Stöd för Lägg till Page Builder {#pbsupport}

[!DNL Product Recommendations] för Page Builder är en valfri modul som installeras separat. Används [!DNL Product Recommendations] Installera modulen med Page Builder genom att köra följande kommando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Genom att aktivera [!DNL Product Recommendations] i Page Builder kan du lägga till en befintlig, aktiv [rekommendationsenhet](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) till allt innehåll som skapas i Page Builder, t.ex. sidor, block och dynamiska block.

Se [Använda [!DNL Product Recommendations] med Page Builder-innehåll](page-builder.md) för ytterligare instruktioner.

### Lägg till rekommendationstyp för visuell likhet {#vissimsupport}

The _Visuell likhet_ rekommendationstypen gör att du kan distribuera en rekommendationsenhet till produktinformationssidan som visar produkter som [visuellt liknande](type.md#visualsim) till den produkt som visas. Rekommendationstypen är mest användbar när bilder och visuella aspekter av produkterna är viktiga delar av shoppingupplevelsen. Installera _Visuell likhet_ rekommendationstyp genom att köra följande kommando:

```bash
composer require magento/module-visual-product-recommendations
```

## Konfigurera [!DNL Product Recommendations] {#configure}

När du har installerat `magento/product-recommendations` -modulen måste du konfigurera [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) genom att ange API-nycklar och välja ett SaaS-dataområde.

För att katalogexporten ska fungera på rätt sätt måste du kontrollera att [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) jobb och [indexerare](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) körs och `Product Feed` indexeraren är inställd på `Update by Schedule`.

När du har länkat till Commerce Services via API-nycklar och angett SaaS-datamängd börjar katalogsynkroniseringen. Då kan du [verifiera](verify.md) att beteendedata skickas till butiken.

## Uppdatera dina [!DNL Product Recommendations] installation {#update}

Som alla Adobe Commerce [!DNL Product Recommendations] använder Composer för installation och uppdateringar. Så här uppdaterar du `magento/product-recommendations` kör du följande:

```bash
composer update magento/product-recommendations --with-dependencies
```

Om du vill uppdatera till en huvudversion, som 3.0 till 4.0, måste du redigera roten `composer.json` -fil för ditt projekt. (Se [versionsinformation](release-notes.md) om du vill ha information om den senaste versionen.) Låt oss till exempel öppna huvudsidan `composer.json` och sök efter `magento/product-recommendations` modul:

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

## Avinstallera [!DNL Product Recommendations] {#uninstall}

Om det behövs kan du [avinstallera](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) modulen för produktrekommendationer.
