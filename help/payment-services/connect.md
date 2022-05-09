---
title: Anslut instansen
description: Anslut Commerce-instansen med en API-nyckel och en privat nyckel och ange datamallen i konfigurationen.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---

# Anslut instansen

[!DNL Payment Services] drivs av Commerce Services och distribueras som SaaS (programvara som tjänst). Du ansluter din Commerce-instans med en API-nyckel och en privat nyckel och anger datamallen i konfigurationen. Du konfigurerar den här anslutningen endast en gång.

Se [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} i användarhandboken för mer information om den här tjänsten.

## Hämta API-autentiseringsuppgifter

Om du vill använda en Commerce SaaS-tjänst måste du använda instansens API-nycklar, som skapas och hanteras i din [Kontrollpanelen Mitt konto](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}. Två olika API-nyckelpar kan skapas för ett Commerce-konto - ett för sandlådan och ett för produktion (direktbetalningar) - men bara ett par kan användas aktivt åt gången.

>[!NOTE]
>
>Behöver du hjälp med att komma åt [!UICONTROL My Account] instrumentpanel? Se [Skapa ett handelskonto](https://docs.magento.com/user-guide/magento/magento-account-create.html){target=&quot;_blank&quot;} i användarhandboken.

Ett givet API-nyckelpar är giltigt för alla Commerce Services i en miljö, så om du redan har konfigurerat Commerce Services för din Commerce-instans finns API-nyckelparet redan i Admin. Om din privata API-nyckel förloras måste ett nytt API-nyckelpar skapas och tillämpas på Commerce Services-konfigurationen i Admin.

Mer information om hur du genererar en API-nyckel för antingen sandbox- eller produktionsmiljöer finns i [Commerce Services Connector](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} i användarhandboken.

>[!IMPORTANT]
>
>Om du genererar om ett API-nyckelpar och ändrar SaaS-identifieraren ansluter alla Commerce Services som används av den här instansen till ett annat datalager och din åtkomst (inklusive tidigare lagrade data) går förlorad. Vi rekommenderar att du inte genererar om ett API-nyckelpar och ändrar SaaS-identifieraren för en aktiv produktionsinstans.

### Commerce API-nyckel och privat nyckel

Några [!DNL Adobe Commerce] och [!DNL Magento Open Source] -funktioner distribueras som SaaS (programvara som en tjänst) - kallas Commerce Services. Om du vill använda dessa tjänster måste du ansluta din Commerce-instans till dessa tjänster med hjälp av en API-nyckel och en privat nyckel, och ange önskat datautrymme i dialogrutan [konfiguration](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}.

När du skapar ett Commerce-konto, som identifieras av ett MageID, kan du generera en Commerce API-nyckel och en privat nyckel. Så här använder du Commerce Services, som [!DNL Payment Services], [!DNL Product Recommendations], eller [!DNL Live Search]måste licensinnehavaren generera dessa nycklar för att kunna godkänna tillståndsvalideringen. Dessa nycklar kan sedan skickas till den systemintegratör eller det utvecklingsteam som för licensinnehavarens räkning hanterar projekten och miljöerna. Om du är en lösningsintegratör har du även rätt att använda dessa tjänster för dina egna behov. I så fall bör signeraren av handelspartnerkontraktet generera nycklarna.

### Generera en API-nyckel och en privat nyckel

1. Logga in på ditt Commerce-konto på [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. Under **[!UICONTROL Magento]** flik, välja **[!UICONTROL API Portal]** på sidofältet.
1. Från _[!UICONTROL Environment]_meny, välja **[!UICONTROL Sandbox]**sedan **[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >API-nycklar krävs för båda miljöerna.

1. Ange ett namn i dialogrutan _[!UICONTROL API Keys]_och klicka **[!UICONTROL Add New]**.

   Den här åtgärden öppnar en dialogruta där du kan hämta den nya tangenten.

   >[!IMPORTANT]
   >
   >Den här dialogrutan är den enda möjligheten att kopiera eller hämta nyckeln.

1. Klicka **[!UICONTROL Download]** sedan klicka **[!UICONTROL Cancel]**.

   The _[!UICONTROL API Keys]_visas nu din API-nyckel.

1. Kopiera både API-nyckeln och den privata nyckeln när du väljer eller skapar ett SaaS-projekt.

   Se [SaaS](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} i användarhandboken för mer detaljerad information.

Samma API-nyckel kan användas för alla instanser, men varje instans måste ha ett eget SaaS-dataminne.

När du skapar ett SaaS-projekt genererar Commerce ett eller flera SaaS-datamallar beroende på din Commerce-licens:

* [!DNL Adobe Commerce] - ett dataområde för produktionen, två testdatamallar
* [!DNL Magento Open Source] - ett dataområde för produktionen, inga testdatamallar

### Konfigurera SaaS-projekt

>[!NOTE]
>
>Om du inte ser _[!UICONTROL Commerce Services Connector]_i Commerce-konfigurationen måste du installera Commerce-modulerna för den Commerce Service du vill använda, till exempel [[!DNL Payment Services]](install.md).

Om du vill välja eller skapa ett SaaS-projekt begär du Commerce API-nyckeln från innehavaren av Commerce-licensen för din butik.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Expandera på den vänstra panelen **[!UICONTROL Services]** och välja **[!UICONTROL Commerce Services Connector]**.
1. I _[!UICONTROL API Keys]_kan du klistra in dina nyckelvärden.

   >[!IMPORTANT]
   >
   >Lägg till nyckelvärden för båda **[!UICONTROL sandbox]** och **[!UICONTROL production]** miljöer.

1. Klicka på **[!UICONTROL Save Config]**.

   Om det finns SaaS-projekt associerade med API-nyckeln när du sparar visas dessa projekt i _[!UICONTROL SaaS Project]_i_[!UICONTROL SaaS Identifier]_ -avsnitt.

1. Om det inte finns några SaaS-projekt klickar du på **[!UICONTROL Create Project]**. Ange sedan ett namn för ditt SaaS-projekt i **[!UICONTROL Project Name]** fält.
1. Om du vill använda den aktuella konfigurationen av din Commerce Store väljer du **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>Om du genererar om dina nycklar i API-portalavsnittet för Mitt konto måste du omedelbart uppdatera API-nycklarna i Admin-konfigurationen. Om du genererar nya nycklar och inte uppdaterar dem i Admin, kommer dina SaaS-tillägg inte längre att fungera och du kommer att förlora värdefulla data.

Du kan ändra namnen genom att klicka på **[!UICONTROL Rename this Project]** eller **[!UICONTROL Rename Data Space]** knappar.

## Konfigurera Commerce Services

Det första steget i introduktionen [!DNL Payment Services] konfigurerar dina Commerce Services i Admin.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Klicka på **[!UICONTROL Configure Commerce Services]**.

   Det här alternativet är synligt om du ännu inte har konfigurerat Commerce Services för ditt konto.

   Du dirigeras till konfigurationsområdet i Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, för att konfigurera din Commerce Services Connector.

1. Följ stegen som beskrivs i [Commerce Services](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}.
