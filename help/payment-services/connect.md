---
title: Anslut instansen
description: Anslut Commerce-instansen med en API-nyckel och en privat nyckel och ange datamallen i konfigurationen.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Anslut instansen

[!DNL Payment Services] drivs av Commerce Services och distribueras som SaaS (programvara som tjänst). Du ansluter Commerce-instansen med en API-nyckel och en privat nyckel och anger datamallen i konfigurationen med hjälp av [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Du konfigurerar den här anslutningen endast en gång.**

* Om du har *har redan anslutit till din instans* genom att hämta och använda dina API-autentiseringsuppgifter och konfigurera Commerce Services kan du fortsätta med att [konfigurera din testsandlåda](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Om du fortfarande *måste ansluta instansen* finns mer information om [hämta API-autentiseringsuppgifter](#obtain-api-credentials) och [konfigurera Commerce Services](#configure-commerce-services).
* Om du *osäker på om din instans är ansluten*, navigera till **System** > Tjänster > **Commerce Services Connector** och visa nyckelvärdena för offentlig och privat API i [!UICONTROL Sandbox Keys] och [!UICONTROL Production Keys] och *Projekt* och *Datautrymme* fälten i [!UICONTROL SaaS Identifier] -avsnitt. Om dessa värden finns är instansen ansluten.

## Hämta API-autentiseringsuppgifter

Om du vill använda en Commerce SaaS-tjänst måste du använda instansens API-nycklar (Commerce public API-nyckel och en privat nyckel) för både sandlådan och produktionen, som skapas och hanteras i din [Kontrollpanel för mitt konto](https://account.magento.com/customer/account/login). [Nyckelparet](https://docs.magento.com/user-guide/configuration/services/saas.html) kan skapas för ett Commerce-konto - ett för sandbox och ett för produktion - men bara ett par kan användas aktivt åt gången.

>[!NOTE]
>
>Behöver du hjälp med att komma åt [!UICONTROL My Account] instrumentpanel? Se [Skapa ett handelskonto](https://docs.magento.com/user-guide/magento/magento-account-create.html).

När en offentlig API-nyckel har skapats är den alltid tillgänglig på instrumentpanelen för Mitt konto. Den kan kopieras eller tas bort efter behov. Den privata API-nyckeln blir synlig när du skapar en offentlig API-nyckel för antingen sandlåda eller produktion. Den är bara tillgänglig för kopiering eller sparande från den efterföljande dialogrutan och kan inte nås senare.

Ett givet API-nyckelpar är giltigt för alla Commerce Services i en miljö, så om du redan har konfigurerat Commerce Services för din instans finns API-nyckelparet redan i Commerce Services Connector.

Om API-nyckeln försvinner måste ett nytt API-nyckelpar anges [genererad](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) och [använd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) till konfigurationen för Commerce Services Connector i Admin. Om fel nycklar är konfigurerade eller om det inte finns några i konfigurationen visas en dialogruta med kontoverifieringsfel i Betalningstjänster som meddelar dig om att kontot inte har verifierats.

Se en [lista över tillgängliga Commerce Services som använder API](https://docs.magento.com/user-guide/system/saas.html#available-services).

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

1. Följ stegen som beskrivs i [SaaS-konfiguration](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
