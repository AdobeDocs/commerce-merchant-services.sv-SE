---
title: Onboarding och installation
description: "Lär dig hur du installerar [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: a2841b809cfc52798dc3f1bdcc033a77333bf0e5
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# Onboarding och installation

Installera katalogtjänsten för att begära och ta emot produktdata från en Commerce-instans med [GraphQL API för katalogtjänst](https://developer.adobe.com/commerce/services/graphql/catalog-service/). Katalogtjänsten levereras som ett dispositionsmetapaket från repo.magento.com.

>[!NOTE]
>
>Om din Commerce-instans använder Live Search eller Product Recommendations installeras eller uppdateras katalogtjänsten automatiskt när du registrerar eller uppgraderar dessa tjänster. Mer information finns i installationsanvisningarna för [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) och [Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).



## Systemkrav

**Programvarukrav**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3
- Disposition: 2.x

**Plattformar som stöds**

- Adobe Commerce om molninfrastruktur: 2.4.4+
- Adobe Commerce lokalt: 2.4.4+

## Slutpunkter

[!DNL Catalog Service] har två slutpunkter tillgängliga för introduktion:

- Sandlåda (`https://catalog-service-sandbox.adobe.io/graphql`) - används för testning och validering innan live
- Produktion (`https://catalog-service.adobe.io/graphql`) - används för direkttrafik för Commerce handlare och webbplatser

Alla Commerce-testinstanser använder sandlådeslutpunkten.

Utför alla inläsningstester på sandlådeslutpunkten. Innan du börjar ladda testningen skickar du en [Supportbiljett](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) så att serviceteamet kan förutse den extra servertrafiken.

## Installation och konfiguration

Så här kommer du igång med [!DNL Catalog Service] för Adobe Commerce krävs följande steg:

- Installera katalogtjänsttillägget (`magento/catalog-service`)
- Konfigurera tjänsten och dataexporten
- Åtkomst till tjänsten

### Installera katalogtjänsttillägget

>[!BEGINSHADEBOX]

**Förutsättning**

- Åtkomst [repo.magento.com](https://repo.magento.com) för att installera tillägget. För nyckelgenerering och för att erhålla nödvändiga rättigheter, se [Hämta dina autentiseringsnycklar](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). Information om molninstallationer finns i [Infrastrukturhandbok för Commerce on Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Åtkomst till kommandoraden på Adobe Commerce-programservern.

>[!ENDSHADEBOX]

Installera den senaste versionen av Catalog Services-tillägget (`magento/catalog-service`) på en Adobe Commerce-instans som kör Adobe Commerce version 2.4.4 eller senare. Katalogtjänsten levereras som ett dispositionsmetapaket från [repo.magento.com](https://repo.magento.com) databas.

>[!BEGINTABS]

>[!TAB Molninfrastruktur]

Använd den här metoden för att installera [!DNL Catalog Service] tillägg för en Commerce Cloud-instans.

1. På din lokala arbetsstation byter du till projektkatalogen för ditt Adobe Commerce i molninfrastrukturprojekt.

   >[!NOTE]
   >
   >Mer information om hur du hanterar Commerce projektmiljöer lokalt finns i [Hantera filialer med CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) i _Användarhandbok för infrastruktur i Adobe Commerce om molnet_.

1. Kolla in miljögrenen för att uppdatera med Adobe Commerce Cloud CLI.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Lägg till katalogtjänstmodulen.

   ```bash
   composer require "magento/catalog-service" "^3.0.1" --no-update
   ```

1. Uppdatera paketberoenden.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Verkställ och push-kodsändringar för `composer.json` och `composer.lock` filer.

1. Lägg till, implementera och skicka kodändringar för `composer.json` och `composer.lock` filer till molnmiljön.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   När uppdateringarna skickas initieras [Commerce molndistributionsprocess](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) för att tillämpa ändringarna. Kontrollera distributionsstatusen på [distributionslogg](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB Lokalt]

Använd den här metoden för att installera [!DNL Catalog Service] tillägg för en lokal instans.

1. Använd Composer för att lägga till katalogtjänstmodulen i ditt projekt:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"  --no-update
   ```

1. Uppdatera beroenden och installera tillägget:

   ```bash
   composer update  "magento/catalog-service"
   ```

1. Uppgradera Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >I vissa fall, särskilt när du distribuerar till produktion, kanske du vill undvika att rensa kompilerad kod eftersom det kan ta en stund. Se till att du säkerhetskopierar systemet innan du gör några ändringar.

>[!ENDTABS]

### Konfigurera tjänsten och dataexporten

När du har installerat [!DNL Catalog Service]utför du följande åtgärder för att integrera katalogtjänsten med din Adobe Commerce-instans. Integreringen möjliggör datasynkronisering och kommunikation mellan Commerce-instansen, katalogtjänsten och andra stödtjänster.

1. Konfigurera [Commerce Services Connector](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) genom att ange API-nycklar och välja ett SaaS-datautrymme.

   Installation av Commerce Services Connector är en engångsprocess som krävs för att använda Adobe Commerce-tjänster som Catalog Service, Live Search och Product Recommendations. Om du redan har konfigurerat anslutningen för en annan tjänst hoppar du över det här steget.

1. Utför en inledande datasynkronisering från [Instrumentpanel för datahantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   Den inledande synkroniseringen kan ta från några minuter till timmar beroende på katalogstorleken. Du kan övervaka synkroniseringsstatusen från kontrollpanelen för datahantering. Efter den första synkroniseringen exporterar katalogen produktdata fortlöpande för att hålla tjänsterna uppdaterade.

Så här ser du till att katalogexporten körs som den ska:

- [Bekräfta att cron-jobb körs](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Verifiera att indexerarna körs från [Administratör](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) eller med kommandot Commerce CLI `bin/magento indexer:info`.
- Verifiera att `Catalog Attributes Feed, Product Feed, Product Overrides Feed`och `Product Variant Feed` indexerare är inställda på `Update by Schedule`.

### Åtkomst till tjänsten

The [!DNL Catalog Service] GraphQL API är tillgängligt via ` https://catalog-service.adobe.io/graphql` slutpunkt med POST-kommandon över HTTPS.

I dina GraphQL-frågor måste du ange flera HTTP-huvuden, inklusive den offentliga API-nyckeln som du lade till i konfigurationen för Adobe Commerce Services Connector i Admin. Mer information finns i [Storefront Services GraphQL](https://developer.adobe.com/commerce/services/graphql/) dokumentation.

### Brandväggskonfiguration

Tillåt [!DNL Catalog Service] via en brandvägg lägger du till `commerce.adobe.io` till tillåtelselista.

## Katalogtjänst och API-nät

The [API-nät för Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) gör det möjligt för utvecklare att integrera privata eller tredjeparts-API:er och andra gränssnitt med Adobe-produkter med hjälp av Adobe IO.

Se [[!DNL Catalog Service] och API Mesh](mesh.md) för information om installation och konfiguration.

## Instrumentpanel för datahantering

Mer information om [!DNL Catalog Service] datasynkronisering, se [Instrumentpanel för datahantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
