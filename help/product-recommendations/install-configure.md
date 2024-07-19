---
title: Installera och konfigurera
description: Lär dig hur du installerar, uppdaterar och avinstallerar  [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 0b0bc88c13d8c90a6209d9156f6fd6a7ce040f72
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Installera och konfigurera

För att distribuera [!DNL Product Recommendations] till din butik och administratör måste du installera modulen och konfigurera [Commerce Services Connector](../landing/saas.md). När uppdateringarna släpps kan du enkelt uppdatera din installation med den senaste versionen.

- [Installera](#install)
- [Konfigurera](#configure)
- [Uppdatera](#update)
- [Avinstallera](#uninstall)

## Installera [!DNL Product Recommendations] {#install}

Eftersom modulen [!DNL Product Recommendations] är ett fristående metapaket, kommer uppdateringar att släppas oftare än Adobe Commerce. Information om hur du kontrollerar att du är uppdaterad med de senaste felkorrigeringarna och funktionerna finns i [versionsinformationen](release-notes.md).

Installera modulen `magento/product-recommendations` med Composer:

```bash
composer require magento/product-recommendations
```

### Stöd för Page Builder {#pbsupport}

[!DNL Product Recommendations] för Page Builder är en valfri modul som installeras separat. Installera modulen genom att köra följande kommando om du vill använda [!DNL Product Recommendations] med Page Builder:

```bash
composer require magento/module-page-builder-product-recommendations
```

Genom att aktivera [!DNL Product Recommendations] i Page Builder kan du lägga till en befintlig, aktiv [rekommendationsenhet](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) i allt innehåll som skapas i Page Builder, till exempel sidor, block och dynamiska block.

Mer information finns i [Använda [!DNL Product Recommendations] med Page Builder-innehåll](page-builder.md).

### Lägg till rekommendationstyp för visuell likhet {#vissimsupport}

Rekommendationstypen _Visuell likhet_ gör att du kan distribuera en rekommendationsenhet till produktinformationssidan som visar produkter som [visuellt liknar ](type.md#visualsim) den produkt som visas. Rekommendationstypen är mest användbar när bilder och visuella aspekter av produkterna är viktiga delar av shoppingupplevelsen. Installera rekommendationstypen _Visuell likhet_ genom att köra följande kommando:

```bash
composer require magento/module-visual-product-recommendations
```

## Konfigurera [!DNL Product Recommendations] {#configure}

1. När du har installerat modulen `magento/product-recommendations` konfigurerar du [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) genom att ange API-nycklar och välja ett SaaS-datautrymme.

   Om du konfigurerar den här anslutningen aktiveras datasynkronisering och kommunikation mellan Commerce-instansen, katalogtjänsten och andra stödtjänster. Datasynkronisering hanteras av [SaaS-tillägget för dataexport](../data-export/overview.md).

1. Om du vill vara säker på att katalogexporten kan köras korrekt kontrollerar du att [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) -jobben och [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) körs och att `Product Feed`-indexeraren är inställd på `Update by Schedule`.

När du har länkat Commerce-programmet till Commerce Services och angett SaaS-dataområdet börjar katalogsynkroniseringen. Du kan sedan [verifiera](verify.md) att beteendedata skickas till din butik.

## Övervaka och felsöka datasynkronisering

Från Commerce Admin kan du övervaka synkroniseringsprocessen med [Dashboard för datahantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Använd [Commerce CLI](../data-export/data-export-cli-commands.md#troubleshooting) och loggar för att hantera och felsöka processen.

Du kan sedan [verifiera](verify.md) att beteendedata skickas till din butik.

## Uppdatera din [!DNL Product Recommendations]-installation {#update}

Precis som alla Adobe Commerce använder [!DNL Product Recommendations] Composer för installation och uppdateringar. Kör följande om du vill uppdatera modulen `magento/product-recommendations`:

```bash
composer update magento/product-recommendations --with-dependencies
```

Om du vill uppdatera till en huvudversion, till exempel från 3.0 till 4.0, måste du redigera rotfilen `composer.json` för ditt projekt. (Mer information om den senaste versionen finns i [versionsinformationen](release-notes.md).) Låt oss till exempel öppna huvudfilen `composer.json` och söka efter modulen `magento/product-recommendations`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Låt oss bump the major version from `3.0` to `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Spara filen `composer.json` och kör:

```bash
composer update magento/product-recommendations --with-dependencies
```

Eller om du har installerat modulerna `magento/module-visual-product-recommendations` och `magento/module-page-builder-product-recommendations`:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> I version 3.x.x av Product Recommendations behövde du bara en API-nyckel. I version 4.x.x och senare måste du ange offentliga och privata API-nycklar för Production samt offentliga och privata API-nycklar för Sandbox. Om du inte anger båda par API-nycklar kan du inte komma åt Recommendations-funktionen Product i Admin. Datainsamlingen fortsätter dock i er butik och befintliga rekommendationer visas även fortsättningsvis för era kunder.

## Brandväggar

Lägg till `commerce.adobe.io` i tillåtelselista om du vill låta Product Recommendations gå igenom en brandvägg.

## Avinstallera [!DNL Product Recommendations] {#uninstall}

Om det behövs kan du [avinstallera](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) produktrekommendationsmodulen.
