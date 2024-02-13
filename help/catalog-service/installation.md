---
title: Onboarding och installation
description: "Lär dig hur du installerar [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 82ed90f48067d7daf20c1a9ebde318d428aad864
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Onboarding och installation

I följande videofilmer visas [!DNL Catalog Service] -processen.

**Del 1**: Onboarding och installation

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**Del 2**: Använda [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## Förutsättningar

Startprocessen för [!DNL Catalog Service] kräver åtkomst till serverns kommandorad. Om du inte är van vid att arbeta via kommandoraden ber du en utvecklare eller systemintegratör att hjälpa till.

**Programvarukrav**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Disposition: 2.x

**Plattformar som stöds**

- Adobe Commerce om molninfrastruktur: 2.4.4+
- Adobe Commerce lokalt: 2.4.4+

>[!ENDSHADEBOX]

## Slutpunkter

[!DNL Catalog Service] har två slutpunkter tillgängliga för introduktion:

- Sandlåda (`https://catalog-service-sandbox.adobe.io/graphql`) - används för testning och validering innan live
- Produktion (`https://catalog-service.adobe.io/graphql`) - används för live-trafik för handlare och webbplatser

Alla testinstanser av Commerce bör använda sandlådeslutpunkten.

Inläsningstestning bör endast utföras på sandlådeslutpunkten. Vi rekommenderar att du [Supportbiljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) öppnas vid inläsningstestning så att tjänstgruppen kan förutse den extra servertrafiken.

## Installation och konfiguration

Så här kommer du igång med [!DNL Catalog Service] för Adobe Commerce krävs följande steg:

- Installera tilläggen för dataexport
- Konfigurera tjänsten och dataexporten
- Åtkomst till tjänsten

### Installera tilläggen för dataexport

Startprocessen för [!DNL Catalog Service] kräver åtkomst till serverns kommandorad.

The [!DNL Catalog Service] tillägg kan installeras på både Adobe Commerce molninfrastruktur och lokala instanser.

The [!DNL Catalog Service] installeras med Composer-nycklar som är länkade till Commerce-kontot [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) som tillhandahålls under registreringsprocessen. I Composer används dessa nycklar vid den första installationen av Adobe Commerce, eller i situationer där Composer-nycklarna inte tidigare sparats i en extern `auth.json` -fil.

Se [Hämta dina autentiseringsnycklar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) om du vill ha mer information om hur du hämtar Composer-nycklar.

#### Adobe Commerce i molninfrastruktur

Använd den här metoden för att installera [!DNL Catalog Service] tillägg för en Commerce Cloud-instans.

1. Byt till din projektkatalog på din lokala arbetsstation.
1. Lägg till katalogtjänstmodulen.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Uppdatera paketberoenden.

   ```bash
   composer update
   ```

1. Verkställ och push-kodsändringar för `composer.json` och `composer.lock` filer.

#### Lokalt

Använd den här metoden för att installera [!DNL Catalog Service] tillägg för en lokal instans.

1. Använd Composer för att lägga till katalogtjänstmodulen i ditt projekt:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update
   ```

1. Uppgradera Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```

### Konfigurera tjänsten och dataexporten

Efter installationen [!DNL Catalog Service]måste du konfigurera [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) genom att ange API-nycklar och välja ett SaaS-datautrymme.

När SaaS-konfigurationen är klar utför du en inledande datasynkronisering genom att följa följande [Katalogsynkronisering](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) guide.

Så här ser du till att katalogexporten körs som den ska:

- Bekräfta att cron-jobb körs.
- Kontrollera att indexerarna körs.
- Se till att `Catalog Attributes Feed, Product Feed, Product Overrides Feed`och `Product Variant Feed` indexerare är inställda på &quot;Update by Schedule&quot;.

Den inledande synkroniseringen kan ta från några minuter till timmar beroende på katalogstorleken. Efter den första synkroniseringen exporterar katalogen kontinuerligt produktdata från Commerce-servern till Commerce Services för att hålla tjänsterna uppdaterade.

### Åtkomst till tjänsten

The [!DNL Catalog Service] API är tillgängligt med kommandon för POST över HTTPS.

Om du vill hämta API-nyckeln går du till Commerce Service Connector-området i administratören och kopierar den offentliga API-nyckeln.

Läs [GraphQL-dokumentation](https://developer.adobe.com/commerce/services/graphql/) för att förstå hur du frågar efter och skickar de huvuden som behövs för att generera API-begäranden.

Tillåt [!DNL Catalog Service] via en brandvägg lägger du till `commerce.adobe.io` till tillåtelselista.

## Katalogtjänst och API-nät

The [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) gör det möjligt för utvecklare att integrera privata eller tredjeparts-API:er och andra gränssnitt med Adobe-produkter med hjälp av Adobe IO.

Se  [[!DNL Catalog Service] och API Mesh](mesh.md) för information om installation och konfiguration.

## Instrumentpanel för datahantering

Användarna kan hänvisa till [Instrumentpanel för datahantering](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) om du vill ha mer information om [!DNL Catalog Service] datasynkronisering.
