---
title: Anslut instansen
description: Koppla din Commerce-instans med en API-nyckel och en privat nyckel och ange datautrymmet i konfigurationen.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 5d3a89b2ef06b2c67ec715ce4f31f22249b336e0
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Anslut instansen

[!DNL Payment Services] drivs av Commerce Services och distribueras som SaaS (programvara som tjänst). Du ansluter din Commerce-instans med en API-nyckel och en privat nyckel, och anger datautrymmet i konfigurationen med [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Du konfigurerar den här anslutningen endast en gång.**

>[!INFO]
>
> Se vår [[!DNL Adobe Commerce] Services Connector](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en) video om du vill ha mer information.

* Om du har *har redan anslutit till din instans* genom att hämta och använda dina API-uppgifter och konfigurera Commerce Services kan du fortsätta med [konfigurera din testsandlåda](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Om du fortfarande *måste ansluta instansen* finns mer information om [hämta API-autentiseringsuppgifter](#obtain-api-credentials) och [konfigurera Commerce Services](#configure-commerce-services).
* Om du *osäker på om din instans är ansluten*, navigera till **System** > Tjänster > **Commerce Services Connector** och visa nyckelvärdena för offentlig och privat API i [!UICONTROL Sandbox Keys] och [!UICONTROL Production Keys] och *Projekt* och *Datautrymme* fälten i [!UICONTROL SaaS Identifier] -avsnitt. Om dessa värden finns är instansen ansluten.

>[!NOTE]
>
>Alla handlare som är berättigade till betaltjänster kan använda ett produktionsdatautrymme och två testdatamallar.

## Hämta API-autentiseringsuppgifter

Om du vill använda en Commerce SaaS-tjänst måste du använda instansens API-nycklar (Commerce publika API-nyckel och en privat nyckel) för både sandlådan och produktionen, som skapas och hanteras i din [Kontrollpanel för mitt konto](https://account.magento.com/customer/account/login). [Nyckelparet](https://docs.magento.com/user-guide/configuration/services/saas.html) kan skapas för ett Commerce-konto - ett för sandlåda och ett för produktion - men endast ett par kan användas aktivt åt gången.

>[!NOTE]
>
>Behöver du hjälp med att komma åt [!UICONTROL My Account] instrumentpanel? Se [Skapa ett Commerce-konto](https://docs.magento.com/user-guide/magento/magento-account-create.html).

När en offentlig API-nyckel har skapats är den alltid tillgänglig på instrumentpanelen för Mitt konto. Den kan kopieras eller tas bort efter behov. Den privata API-nyckeln blir synlig när du skapar en offentlig API-nyckel för antingen sandlåda eller produktion. Den är bara tillgänglig för kopiering eller sparande från den efterföljande dialogrutan och kan inte nås senare.

Ett givet API-nyckelpar är giltigt för alla Commerce-tjänster i en miljö, så om du redan har konfigurerat Commerce Services för din instans finns API-nyckelparet redan i Commerce Services Connector.

Om API-nyckeln försvinner måste ett nytt API-nyckelpar anges [genererad](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) och [använd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) till Commerce Services Connector-konfigurationen i Admin. Om fel nycklar är konfigurerade eller om det inte finns några i konfigurationen visas en dialogruta med kontoverifieringsfel i Betalningstjänster som meddelar dig om att kontot inte har verifierats.

Se en [lista över tillgängliga Commerce-tjänster som använder API:t](https://docs.magento.com/user-guide/system/saas.html#available-services).

Mer information om hur du genererar en API-nyckel för antingen sandbox- eller produktionsmiljöer finns i [Referenser](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>Vi rekommenderar att du inte genererar om ett API-nyckelpar *och* ändra SaaS-identifieraren och/eller datautrymmet för en aktiv produktionsinstans. Du förlorar data för instansen om de ändras.

## Konfigurera Commerce Services

Samma API-nyckel kan användas för alla instanser, men varje instans måste ha sin egen [SaaS-datautrymme](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>Handläggarna måste använda samma nycklar som genererats för MageID för sina stödrättigheter.

Nu när du har fått dina inloggningsuppgifter kan du konfigurera ditt SaaS-projekt och Saas Data Space.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Klicka på **[!UICONTROL Configure Commerce Services]**.

   Det här alternativet är synligt om du ännu inte har konfigurerat Commerce Services för ditt konto.

   Du dirigeras till konfigurationsområdet i Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, för att konfigurera din Commerce Services Connector.

1. Så här konfigurerar du dina Commerce-tjänster: [SaaS-konfiguration](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).

   >[!INFO]
   >
   > Se vår [[!DNL Adobe Commerce] Services Connector](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en#configuration-faqs) video om du vill ha mer information.

## Slutpunkt

[!DNL Payment Services] använder [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html) för att ansluta till Commerce Services och driftsätta som SaaS. Detta [!DNL Commerce Services Connector] kommunicerar via slutpunkten vid:

* `commerce-beta.adobe.io` för sandlådemiljöer.
* `commerce.adobe.io for` för miljöer.
