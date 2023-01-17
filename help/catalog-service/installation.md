---
title: Onboarding och installation
description: Så här installerar du [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: e11b4e86efe3483717cf4484a7fcce6e23015f4c
workflow-type: tm+mt
source-wordcount: '575'
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

## Miljö

Det finns två tillgängliga miljöer för katalogtjänsten:

- Sandbox (https://catalog-service-sandbox.adobe.io/graphql) - används för testning och validering innan live
- Produktion (https://catalog-service.adobe.io/graphql)- används för Live-trafik för handlare och webbplatser

## Installation och konfiguration

Följande steg krävs för att komma igång med katalogtjänsten för Adobe Commerce:

- Installera tilläggen för dataexport
- Konfigurera tjänsten och dataexporten
- Åtkomst till tjänsten

### Installera tilläggen för dataexport

Startprocessen för katalogtjänsten kräver åtkomst till serverns kommandorad.

Katalogtjänsttillägget kan installeras både i Adobe Commerce molninfrastruktur och på lokala instanser.

Katalogtjänsten installeras med Composer-nycklar som är länkade till Commerce-kontot [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) som tillhandahålls under registreringsprocessen. I Composer används dessa nycklar vid den första installationen av Adobe Commerce, eller i situationer där Composer-nycklarna inte tidigare sparats i en extern `auth.json` -fil.

Se [Hämta dina autentiseringsnycklar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) om du vill ha mer information om hur du hämtar Composer-nycklar.

#### Adobe Commerce i molninfrastruktur

Använd den här metoden för att installera katalogtjänsttillägget för en Commerce Cloud-instans.

1. Öppna `<Commerce_root>/composer.json` i en textredigerare och uppdatera kravavsnittet enligt följande:

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
     "magento/services-connector": "1.2.1",
     "magento/module-catalog-service-installer": "1.0.1"
   }
   ```

1. Testa den nya konfigurationen lokalt och uppdatera beroenden:

```bash
composer update
```

Kommandot uppdaterar alla beroenden.

1. Genomför och skicka ändringarna för `composer.json` och `composer.lock`.

#### Lokalt

Använd den här metoden för att installera katalogtjänsttillägget för en lokal instans.

1. Öppna `<Commerce_root>/composer.json` i en textredigerare och uppdatera kravavsnittet enligt följande:

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
 "magento/services-connector": "1.2.1",
 "magento/module-catalog-service-installer": "1.0.1"
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

### Konfigurera tjänsten och dataexporten

När du har installerat katalogtjänsten måste du konfigurera [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) genom att ange API-nycklar och välja ett SaaS-datautrymme.

När SaaS-konfigurationen är klar utför du en inledande datasynkronisering enligt guiden Katalogsynkronisering.

Så här ser du till att katalogexporten körs som den ska:

- Bekräfta att cron-jobb körs.
- Kontrollera att indexerarna körs.
- Se till att `Catalog Attributes Feed, Product Feed, Product Overrides Feed`och `Product Variant Feed` indexerare är inställda på &quot;Update by Schedule&quot;.

Den inledande synkroniseringen kan ta från några minuter till timmar beroende på katalogstorleken. Efter den första synkroniseringen exporterar katalogen kontinuerligt produktdata från Commerce-servern till Commerce Services för att hålla tjänsterna uppdaterade.

### Åtkomst till tjänsten

Katalogtjänstens API är tillgängligt med POST-kommandon via HTTPS.

Om du vill hämta API-nyckeln går du till Commerce Service Connector-området i administratören och kopierar den offentliga API-nyckeln.

Läs [GraphQL-dokumentation](https://developer.adobe.com/commerce/webapi/graphql/) för att förstå hur du frågar efter och skickar de huvuden som behövs för att generera API-begäranden.

## Katalogtjänst och API-nät

The [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) gör det möjligt för utvecklare att integrera privata eller tredjeparts-API:er och andra gränssnitt med Adobe-produkter med hjälp av Adobe IO.

Se  [Katalogtjänst och API-nät](mesh.md) för information om installation och konfiguration.
