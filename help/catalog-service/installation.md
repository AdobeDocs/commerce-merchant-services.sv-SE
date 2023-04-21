---
title: Onboarding och installation
description: Så här installerar du [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 3d7a38fc81265897615896812d49a164a21d1d84
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Onboarding och installation

Se en genomgång av katalogtjänstprocessen.

Del 1:

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

Del 2:

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## Förutsättningar

Startprocessen för [!DNL Catalog Service] kräver åtkomst till serverns kommandorad. Om du inte är van vid att arbeta via kommandoraden ber du en utvecklare eller systemintegratör att hjälpa till.

### Programvarukrav

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Disposition: 2.x

### Plattformar som stöds

- Adobe Commerce om molninfrastruktur: 2.4.4+
- Adobe Commerce lokalkontor: 2.4.4+

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
  "magento/catalog-service": "^2.1.0"
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
    "magento/catalog-service": "^2.1.0"
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

När du har installerat katalogtjänsten måste du konfigurera [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) genom att ange API-nycklar och välja ett SaaS-datautrymme.

När SaaS-konfigurationen är klar utför du en inledande datasynkronisering genom att följa följande [Katalogsynkronisering](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) guide.

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
