---
title: Anslut lagringslösningen Store Fulfillment
description: Upprätta anslutningarna mellan Adobe Commerce och Store Fulfillment-lösningen genom att skapa och godkänna en Adobe Commerce-integrering och lägga till autentiseringsuppgifterna för Store Fulfillment-kontot i Adobe Commerce tjänstkonfiguration.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Anslut lagringslösningen Store Fulfillment

Upprätta anslutningen mellan Adobe Commerce och Store Fulfillment services genom att konfigurera inloggningsuppgifter och anslutningsdata från administratören.

- **[Konfigurera [!DNL Commerce integration settings]](#create-the-commerce-integration)**-Skapa en Adobe Commerce-integrering för Store Fulfillment services och generera åtkomsttokens för att autentisera inkommande begäranden från Store Fulfillment-servrar.

- **[Konfigurera kontoautentiseringsuppgifter för Store Fulfillation Services](#configure-store-fulfillment-account-credentials)**-Lägg till dina autentiseringsuppgifter för att ansluta Adobe Commerce till ditt Store Fulfillment-konto.

>[!NOTE]
>
>Slutför konfigurationen av anslutningen och validera anslutningen innan du börjar testa.

## Integrera Adobe Commerce

Om du vill integrera Adobe Commerce med Store Fulfillment services skapar du en Commerce-integrering och skapar åtkomsttokens som kan användas för att autentisera begäranden från Store Fulfillment-servrar.

1. I Admin skapar du integreringen för Butiksuppfyllelse.

   - Namnge tillägget
   - Ange din e-postadress
   - Ange ditt lösenord för administratörskontot

1. Konfigurera [!UICONTROL API Resource Access permissions] för integrationen - välj `[!UICONTROL All]`

1. Generera åtkomsttoken för autentisering genom att spara och aktivera integreringen.

1. Kopiera och spara åtkomsttokens på en säker, krypterad plats.

1. Arbeta med din Account Manager för att slutföra konfigurationen på sidan för Store Fulfillment och för att godkänna integreringen.


>[!NOTE]
>
>Detaljerade anvisningar finns i [Integreringar](https://docs.magento.com/user-guide/system/integrations.html) i _Adobe Commerce Användarhandbok_.

## Konfigurera autentiseringsuppgifter för lagringskontot för uppfyllelse

När du fyllt i formuläret skapas ett Walmart Store Fulfillment-konto åt dig. Du får följande autentiseringsuppgifter när de är tillgängliga:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (vanligtvis samma som ovanstående konfiguration)

Dessa autentiseringsuppgifter krävs för att konfigurera och använda Store Fulfillment.

>[!NOTE]
>
>Det kan ta en stund att slutföra processen för att skapa kontot. När du väntar på autentiseringsuppgifter [granska och konfigurera andra inställningar för Store Fulfillment-lösningen](service-config-settings-overview.md).

### Lägg till autentiseringsuppgifter för att ansluta till Store Fulfillment

1. Konfigurera [kontoautentiseringsuppgifter](enable-general.md) för produktions- och sandlådemiljöer.

1. Gå till **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Ange kontoautentiseringsuppgifterna som anges för **[!UICONTROL Production environment]**. Alla fält är obligatoriska.

1. Välj **[!UICONTROL Save Config]**.

1. Testa anslutningen genom att välja **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>Om inloggningsuppgifterna är ogiltiga kontrollerar du att du har angett rätt värden för varje miljö och validerar igen. Kontakta din kontorepresentant om du fortfarande har problem med att ansluta.








