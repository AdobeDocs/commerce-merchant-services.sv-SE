---
title: Onboarding och installation
description: Så här installerar du [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Onboarding och installation

## Förutsättningar

Startprocessen för [!DNL Catalog Service] kräver åtkomst till serverns kommandorad. Om du inte är van vid att arbeta via kommandoraden ber du en utvecklare eller systemintegratör att hjälpa till.

### Programvarukrav

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- Disposition: 2.x, 1.x

### Plattformar som stöds

- Adobe Commerce om molninfrastruktur: 2.4.x
- Adobe Commerce lokalkontor: 2.4.x

## Installera tillägget

Du kan installera [!DNL Catalog Service] för både Adobe Commerce i molninfrastrukturen och lokala instanser.

The [!DNL Catalog Service] installeras med Composer-nycklar som är länkade till Commerce-kontot [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) anges i registreringsprocessen. I dispositionen används dessa nycklar vid den första installationen av [!DNL Adobe Commerce]eller i situationer där dispositionsnycklarna inte tidigare sparats i `auth.json` -fil.

Se [Hämta dina autentiseringsnycklar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) om du vill ha mer information om hur du hämtar Composer-nycklar.

### Adobe Commerce i molninfrastruktur

Använd den här metoden för att installera [!DNL Catalog Service] tillägg för en Commerce Cloud-instans.

1. Öppna `<Commerce_root>/composer.json` i en textredigerare och uppdatera `require` enligt följande:

   ```json
   "require": {
      "magento/module-saas-catalog": "^101.4.0",
      "magento/module-saas-product-override": "^101.4.0",
      "magento/module-saas-product-variant": "^101.4.0",
      "magento/module-bundle-product-data-exporter": "^101.3.1",
      "magento/module-catalog-data-exporter": "^101.3.1",
      "magento/module-catalog-inventory-data-exporter": "^101.3.1",
      "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
      "magento/module-configurable-product-data-exporter": "^101.3.1",
      "magento/module-data-exporter": "^101.3.1",
      "magento/module-parent-product-data-exporter": "^101.3.1",
      "magento/module-product-override-data-exporter": "^101.3.1",
      "magento/data-services": "^7.0.11",
      "magento/services-id": "^3.0.1",
      "magento/services-connector": "1.2.1"
    }
   ```

1. Testa den nya konfigurationen lokalt och uppdatera beroenden:

   ```bash
   composer update
   ```

   Kommandot uppdaterar alla beroenden.

1. Genomför och skicka ändringarna för `composer.json` och `composer.lock`.

### Lokalt

Använd den här metoden för att installera [!DNL Catalog Service] tillägg för en lokal instans.

1. Öppna `<Commerce_root>/composer.json` i en textredigerare och uppdatera `require` enligt följande:

   ```json
   "require": {
    "magento/module-saas-catalog": "^101.4.0",
    "magento/module-saas-product-override": "^101.4.0",
    "magento/module-saas-product-variant": "^101.4.0",
    "magento/module-bundle-product-data-exporter": "^101.3.1",
    "magento/module-catalog-data-exporter": "^101.3.1",
    "magento/module-catalog-inventory-data-exporter": "^101.3.1",
    "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
    "magento/module-configurable-product-data-exporter": "^101.3.1",
    "magento/module-data-exporter": "^101.3.1",
    "magento/module-parent-product-data-exporter": "^101.3.1",
    "magento/module-product-override-data-exporter": "^101.3.1",
    "magento/data-services": "^7.0.11",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
   }
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update
   ```

   Kommandot uppdaterar alla beroenden.

1. Uppgradera Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cacheminnet:

   ```bash
   bin/magento cache:clean
   ```

## Konfigurera katalogexport

Efter installationen [!DNL Catalog Service]måste du konfigurera [Commerce Services Connector](../landing/saas.md) genom att ange API-nycklar och välja ett SaaS-dataområde.

Så här ser du till att katalogexporten körs som den ska:

- Bekräfta att [cron-jobb](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) är igång.
- Verifiera [indexerare](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) är igång.
- Se till att `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`och `Product Variant Feed` indexerare är inställda på `Update by Schedule`.

## Katalogtjänst och API-nät

The [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) gör det möjligt för utvecklare att integrera privata eller tredjeparts-API:er och andra gränssnitt med Adobe-produkter med hjälp av Adobe IO.

Det första steget för att använda API-nät med katalogtjänst är att ansluta API-nät till din instans. Se detaljerade instruktioner i [Skapa ett nät](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

För att slutföra installationen behöver du [Adobe IO CLI-paket](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) installerade.

När nätet har konfigurerats för Adobe iO kör du följande kommando som lägger till en `CommerceCatalogServiceGraph` till nätet.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

där `variables.json` är en separat fil som lagrar värden som används ofta för Adobe i/O.
API-nyckeln kan till exempel sparas i filen:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

När du har kört det här kommandot bör katalogtjänsten köras via API-nätet. Du kan köra `aio api-mesh:get` om du vill visa konfigurationen för det uppdaterade nätet.

## [!DNL Catalog Service] demo

Titta på den här videon om du vill veta mer om [!DNL Catalog Service] installation och testning:

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
