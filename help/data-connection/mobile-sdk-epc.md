---
title: Integrera Adobe Experience Platform Mobile SDK med Commerce
description: Lär dig hur du använder Adobe Experience Platform Mobile SDK tillsammans med en headless eller anpassad Commerce Store.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 593e92ebf890bd7d9bfef1cd13be727ca6be172b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Integrera Adobe Experience Platform Mobile SDK med Commerce

>[!IMPORTANT]
>
>Adobe Experience Platform Mobile SDK för iOS har stöd för iOS 11 eller senare.

Integrera [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) med mobilappen Commerce kan handlare skicka Commerce  [händelsedata](events.md) till Experience Platform.

När data om Commerce-händelser är tillgängliga i kanten kan de nås av andra Adobe Experience Cloud-program. Du kan till exempel använda data för att skapa målgrupper i Real-Time CDP och sedan [använda dessa målgrupper](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) för att personalisera mobilappen Commerce.

## Konfiguration

Installera och konfigurera SDK i Experience Platform för att komma igång med Adobe Experience Platform Mobile SDK med Commerce. Slutför sedan konfigurationen i Commerce.

### Experience Platform

1. Läs mer om mobilappsfunktioner i [Självstudiekurs om Adobe Experience Cloud i mobilappar](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [Installera och konfigurera](https://developer.adobe.com/client-sdks/documentation/getting-started/) SDK i Experience Platform.

   >[!NOTE]
   >
   >Schemat som du skapar och konfigurerar i Experience Platform är samma schema som du använder i programkoden i din Commerce-mobilapp.

### Handel

När du har slutfört SDK-konfigurationen för Experience-plattformen lägger du till SDK-konfigurationen i Commerce.

1. Om du vill skicka Commerce-händelsedata till Experience Platform via SDK måste du ange ett XDM-schema i programkoden. Schemat måste matcha schemat [konfigurerad](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) för SDK i Experience Platform.

   I följande exempel visas hur du spårar `web.webpagedetails.pageViews` -händelsen och ange `identityMap` med hjälp av e-postfältet.

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Koppla upp dig till Commerce Cloud.

   Lägg till URL:en i Commerce GraphQL-slutpunkten i projektets bygginställningar. Till exempel:

   - Felsök: http://_debug_.commercialSite.cloud/graphql/
   - Version: http://_release_.commercialSite.cloud/graphql/

1. Om du vill hämta data från Commerce GraphQL-slutpunkterna måste du först generera de filer och kataloger som behövs i ditt projekt med hjälp av [Apollo Code Generator](https://www.apollographql.com/docs/ios/).

   1. Från projektkatalogen [installera](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apollo iOS.

   1. [Initiera](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) Apollo Codegen CLI.

      Detta skapar en `apollo-codegen-configuration.json` -fil.

   1. Generera nödvändiga GraphQL-filer och -kataloger i ditt projekt genom att ersätta innehållet i `apollo-codegen-configuration.json` fil med följande:

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [Hämta](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) Commerce GraphQL schema.

      Kontrollera att sökvägen är till `./apollo-codegen-config.json` som innehåller en referens till Commerce GraphQL-schemat.

   1. [Generera](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) källkoden.

      Kontrollera att sökvägen är till `./apollo-codegen-config.json` -fil, som innehåller konfigurationsinformationen för att generera nödvändiga filer och kataloger.

   1. Inuti den nyskapade **GraphQLGenerated** , lägga till eller redigera GraphQL-typer. Du kan till exempel lägga till en `DynamicBlocks.graphql` skriv med följande innehåll:

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   Du har nu integrerat Adobe Experience Platform Mobile SDK med mobilappen Commerce. Händelsedata flödar från appen till Experience Platform.

## Hur man skiljer på Commerce-händelser som genereras från mobilprogram

Alla [händelser](events.md) innehåller ett anropat fält `channel`. The `channel` fältet innehåller `channel._id` och `channel._type` som för en Luma storefront har namnutrymmesvärden för `"https://ns.adobe.com/xdm/channels/web"` och `"https://ns.adobe.com/xdm/channel-types/web"` respektive. I en mobilbutik är namnutrymmesvärdena `"https://ns.adobe.com/xdm/channels/mobile-app"` och `"https://ns.adobe.com/xdm/channel-types/mobile"` respektive.

## Nästa steg

Mer information om hur du hämtar Real-Time CDP-målgrupper från din mobilapp för att informera om kundvagnsregler, dynamiska block och relaterade produktregler finns i [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
