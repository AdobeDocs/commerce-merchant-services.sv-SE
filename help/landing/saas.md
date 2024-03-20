---
title: Commerce Services Connector
description: Lär dig hur du integrerar din Adobe Commerce- eller Magento Open Source-instans med tjänster med hjälp av API-nycklar för produktion och sandlåda.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: 2d6b80b5133eb00ac42a5f2b64c5846ad30e56c4
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Vissa Adobe Commerce- och Magento Open Source-funktioner drivs av [!DNL Commerce Services]  och distribueras som SaaS (programvara som tjänst). Om du vill använda dessa tjänster måste du ansluta [!DNL Commerce] -instans med produktions- och sandbox-API-nycklar, och ange datautrymmet i [konfiguration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). Du behöver bara konfigurera det här en gång.

## Tillgängliga tjänster {#availableservices}

Följande listar [!DNL Commerce] funktioner som du kommer åt via [!DNL Commerce Services Connector]:

| Tjänst | Tillgänglighet |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) som drivs av Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) som drivs av Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce och Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce och Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Arkitektur

På en hög nivå [!DNL Commerce Services Connector] består av följande kärnelement:

![Kopplingsarkitektur för Commerce Services](assets/saas-config-sync-workflow.png)

I följande avsnitt beskrivs dessa element mer ingående.

## Referenser {#apikey}

Produktions- och sandbox-API-nycklar genereras från [!DNL Commerce] licensinnehavarens konto, som identifieras av ett unikt [!DNL Commerce] ID (MageID). Att godkänna berättigandevalidering för tjänster som [!DNL Product Recommendations] eller [!DNL Live Search], kan licenshavaren för handlarens organisation generera uppsättningen API-nycklar så länge som kontot är i gott skick. Nycklarna kan delas på behovsbasis med systemintegratören eller utvecklingsteamet som hanterar projekt och miljöer för licenshavarens räkning. Dessutom har lösningens integratörer rätt att använda [!DNL Commerce Services]. Om du är en lösningsintegratör, signeraren av [!DNL Commerce] partnerkontrakt ska generera API-nycklar.

### Generera API-nycklar för produktion och sandlåda {#genapikey}

1. Logga in på [!DNL Commerce] konto på [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Under **Magento** flik, välja **API-portal** på sidofältet.

1. Från _Miljö_ meny, välja **Produktion** eller **Sandbox**.

1. Ange ett namn i dialogrutan _API-nycklar_ och klicka **Lägg till ny**.

   Då öppnas en dialogruta där du kan ladda ned den nya tangenten.

   ![Hämta privat nyckel](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Det här är den enda möjligheten att kopiera eller hämta dina nycklar.

1. Klicka **Ladda ned** klicka sedan på **Avbryt**.

1. Upprepa stegen ovan för varje miljö (produktion och sandlåda).

   The **API-nycklar** visas dina API-nycklar. Du behöver både produktions- och sandlådetangenter när du [välja eller skapa ett SaaS-projekt](#createsaasenv).

## SaaS-konfiguration {#saasenv}

[!DNL Commerce] -instanser måste konfigureras med ett SaaS-projekt och ett SaaS-datautrymme så att [!DNL Commerce Services] kan skicka data till rätt plats. Ett SaaS-projekt grupperar alla SaaS-datautrymmen. SaaS-datautrymmen används för att samla in och lagra data som gör att [!DNL Commerce Services] till jobbet. Vissa av dessa data kan exporteras från [!DNL Commerce] och en del kan samlas in från shoppingbeteenden på butiken. Dessa data lagras sedan för att skydda molnlagringen.

För [!DNL Product Recommendations], innehåller SaaS-datautrymmet katalog- och beteendedata. Du kan peka en [!DNL Commerce] -instans till ett SaaS-datautrymme av [markera](https://docs.magento.com/user-guide/configuration/services/saas.html) i [!DNL Commerce] konfiguration.

>[!WARNING]
>
> Använd endast SaaS-datautrymmet i produktionen [!DNL Commerce] installation för att undvika datakonflikter. Annars riskerar du att förorena data från produktionsplatsen med testdata, vilket orsakar förseningar i driftsättningen. Produktionsproduktdata kan till exempel skrivas över av misstag från mellanlagringsdata, som mellanlagrings-URL:er.

### Välja eller skapa ett SaaS-projekt {#createsaasenv}

>[!NOTE]
>
> Om du inte ser **[!UICONTROL Commerce Services Connector]** i [!DNL Commerce] måste du installera [!DNL Commerce] för dina behov [[!DNL Commerce] service](#availableservices).

Om du vill välja eller skapa ett SaaS-projekt begär du [!DNL Commerce] API-nyckel från [!DNL Commerce] licensinnehavare för din butik.

1. På _Administratör_ sidebar, gå till **System** > Tjänster > **Commerce Services Connector**.

1. I _API-nycklar för sandlåda_ och _API-nycklar för produktion_ -avsnitt, klistra in dina nyckelvärden.

   Privata nycklar måste innehålla `----BEGIN PRIVATE KEY---` i början av tangenten och `----END PRIVATE KEY----` efter den privata nyckeln.

1. Klicka **Spara**.

Alla SaaS-projekt som är kopplade till dina nycklar visas i **Projekt** fältet i **SaaS-identifierare** -avsnitt.

1. Om det inte finns några SaaS-projekt klickar du på **Skapa projekt**. Sedan i **Projekt** anger du ett namn för ditt SaaS-projekt.

   När du skapar ett SaaS-projekt [!DNL Commerce] genererar ett eller flera SaaS-datamallar beroende på [!DNL Commerce] licens:
   - Adobe Commerce - ett produktionsdatautrymme; två testdatautrymme
   - Magento Open Source - Ett produktionsdatautrymme utan testdatautrymme

1. Välj **Datautrymme** för den aktuella konfigurationen av [!DNL Commerce] butik.

>[!WARNING]
>
> Om du genererar nya nycklar i API-portalavsnittet för Mitt konto ska du omedelbart uppdatera API-nycklarna i Admin-konfigurationen. Om du genererar nya nycklar och inte uppdaterar dem i Admin, fungerar inte längre dina SaaS-tillägg och du förlorar värdefulla data.

Om du vill ändra namnen på ditt SaaS-projekt eller -datautrymme klickar du på **Byt namn** bredvid någon av dem. Om du ändrar namnet påverkas inte tjänsten eftersom namnet bara är en etikett som hjälper dig att identifiera och skilja mellan projekt och datautrymme.

## IMS-organisation (valfritt) {#organizationid}

Om du vill ansluta din Adobe Commerce-instans till Adobe Experience Platform loggar du in på ditt Adobe-konto med din Adobe ID. När du har loggat in visas den IMS-organisation som är kopplad till ditt Adobe-konto i det här avsnittet.

## Katalogsynkronisering

När [!DNL Commerce] instansen har anslutits till [!DNL Commerce Services], exporterar katalogsynkroniseringsprocessen produktdata från [!DNL Commerce] server till [!DNL Commerce Services]. För närvarande använder endast Product Recommendations katalogsynkroniseringstjänsten. [Läs mer](catalog-sync.md) om katalogsynkroniseringsprocessen.
