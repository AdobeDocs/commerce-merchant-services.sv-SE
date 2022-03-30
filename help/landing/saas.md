---
title: Commerce Services Connector
description: Lär dig hur du integrerar din Adobe Commerce- eller Magento Open Source-instans med tjänster med en API-nyckel och en privat nyckel.
source-git-commit: 8789bd21362109325d0d7b23d9b130067390eeae
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Vissa Adobe Commerce- och Magento Open Source-funktioner drivs av [!DNL Commerce Services]  och distribueras som SaaS (programvara som tjänst). Om du vill använda dessa tjänster måste du ansluta [!DNL Commerce] -instans med en API-nyckel och en privat nyckel, och ange datautrymmet i [konfiguration](https://docs.magento.com/user-guide/configuration/services/saas.html). Du behöver bara konfigurera det här en gång.

## Tillgängliga tjänster

Följande listar [!DNL Commerce] funktioner som du kommer åt via [!DNL Commerce Services Connector]:

| Tjänst | Tillgänglighet |
| ---|--- |
| [!DNL Product Recommendations] som drivs av Adobe Sensei | Adobe Commerce |
| [!DNL Live Search] som drivs av Adobe Sensei | Adobe Commerce |
| [!DNL Payment Services] | Adobe Commerce och Magento Open Source |

## Arkitektur

På en hög nivå [!DNL Commerce Services Connector] består av följande kärnelement:

![Kopplingsarkitektur för Commerce Services](assets/saas-config-sync-workflow.png)

I följande avsnitt beskrivs dessa element mer ingående.

## Autentiseringsuppgifter {#apikey}

API-nyckeln och den privata nyckeln genereras från [!DNL Commerce] licensinnehavarens konto, som identifieras av ett unikt [!DNL Commerce] ID (MageID). Att godkänna berättigandevalidering för tjänster som [!DNL Product Recommendations] eller [!DNL Live Search], kan licenshavaren för handlarens organisation generera uppsättningen API-nycklar så länge som kontot är i gott skick. Nycklarna kan delas på behovsbasis med systemintegratören eller utvecklingsteamet som hanterar projekt och miljöer för licenshavarens räkning. Dessutom har lösningens integratörer rätt att använda [!DNL Commerce Services]. Om du är en lösningsintegratör, signeraren av [!DNL Commerce] partnerkontrakt ska generera API-nycklar.

### Generera en API-nyckel och en privat nyckel {#genapikey}

1. Logga in på [!DNL Commerce] konto [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Under **Magento** flik, välja **API-portal** på sidofältet.

1. Från _Miljö_ meny, välja **Produktion** eller **Sandbox**.

   >[!NOTE]
   >
   > För [!DNL _Recommendations_] och [!DNL _Live Search_], markera **Produktion**. Produktionsnycklar ger åtkomst till produktionsutrymmen och icke-produktionsdatamallar. Sandlådenycklar används inte för dessa tjänster.

1. Ange ett namn i dialogrutan _API-nycklar_ och klicka **Lägg till ny**.

   Då öppnas en dialogruta där du kan ladda ned den nya tangenten.

   ![Hämta privat nyckel](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Det här är den enda möjligheten att kopiera eller hämta nyckeln.

1. Klicka **Hämta** sedan klicka **Avbryt**.

   The **API-nycklar** visas nu din API-nyckel. Du behöver både API-nyckeln och den privata nyckeln när du [välja eller skapa ett SaaS-projekt](#createsaasenv).

## SaaS-konfiguration {#saasenv}

[!DNL Commerce] -instanser måste konfigureras med ett SaaS-projekt och ett SaaS-datautrymme så att [!DNL Commerce Services] kan skicka data till rätt plats. Ett SaaS-projekt grupperar alla SaaS-datautrymmen. SaaS-datautrymmen används för att samla in och lagra data som möjliggör [!DNL Commerce Services] till jobbet. Vissa av dessa data kan exporteras från [!DNL Commerce] och en del kan samlas in från shoppingbeteenden på butiken. Dessa data lagras sedan för att skydda molnlagringen.

För [!DNL Product Recommendations], innehåller SaaS-datautrymmet katalog- och beteendedata. Du kan peka en [!DNL Commerce] -instans till ett SaaS-datautrymme av [markera](https://docs.magento.com/user-guide/configuration/services/saas.html) i [!DNL Commerce] konfiguration.

>[!WARNING]
>
> Använd endast SaaS-datautrymmet i produktionen [!DNL Commerce] installation för att undvika datakonflikter. Annars riskerar du att förorena data från produktionsplatsen med testdata, vilket orsakar förseningar i driftsättningen. Produktionsproduktdata kan till exempel skrivas över av misstag från mellanlagringsdata, som mellanlagrings-URL:er.

### Välja eller skapa ett SaaS-projekt {#createsaasenv}

>[!NOTE]
>
> Om du inte ser **Commerce Services Connector** i [!DNL Commerce] måste du installera [!DNL Commerce] för dina behov [!DNL Commerce Service], till exempel [!DNL Product Recommendations].

Om du vill välja eller skapa ett SaaS-projekt begär du [!DNL Commerce] API-nyckel från [!DNL Commerce] licensinnehavare för din butik.

1. På _Administratör_ sidebar, gå till **Lager** > _Inställningar_ > **Konfiguration**.

1. Expandera på den vänstra panelen **Tjänster** och välja **Commerce Services Connector**.

1. I _API-nycklar_ -avsnittet, klistra in dina nyckelvärden för **API-nyckel för produktion** och **Privat produktionsnyckel**.

   Privata nycklar måste innehålla `----BEGIN PRIVATE KEY---` i början av tangenten och `----END PRIVATE KEY----` i slutet av den privata nyckeln.

1. Klicka **Spara konfiguration**.

Alla SaaS-projekt som är kopplade till din API-nyckel visas i **SaaS-projekt** fält.

1. Om det inte finns några SaaS-projekt klickar du på **Skapa projekt**. Sedan i **Projektnamn** anger du ett namn för ditt SaaS-projekt.

   När du skapar ett SaaS-projekt [!DNL Commerce] genererar ett eller flera SaaS-datamallar beroende på [!DNL Commerce] licens:
   - Adobe Commerce - ett produktionsdatautrymme två testdatamallar
   - Magento Open Source - Ett dataområde för produktion. inga testdatamallar

1. Välj **SaaS-datautrymme** för den aktuella konfigurationen av [!DNL Commerce] butik.

>[!WARNING]
>
> Om du genererar nya nycklar i API-portalavsnittet för Mitt konto ska du omedelbart uppdatera API-nycklarna i Admin-konfigurationen. Om du genererar nya nycklar och inte uppdaterar dem i Admin, fungerar inte längre dina SaaS-tillägg och du förlorar värdefulla data.

Klicka på knappen **Byt namn på det här projektet** eller **Byt namn på dataområde** respektive.

## Katalogsynkronisering

När [!DNL Commerce] instansen har anslutits till [!DNL Commerce Services], exporterar katalogsynkroniseringsprocessen produktdata från [!DNL Commerce] server till [!DNL Commerce Services]. [Läs mer](catalog-sync.md) om katalogsynkroniseringsprocessen.
