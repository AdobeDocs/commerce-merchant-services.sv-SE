---
title: Anmäl dig till [!DNL Express Checkout] för Adobe Commerce
description: Se hur [!DNL Express Checkout] kan vara till fördel för din Adobe Commerce-instans och för hur du kan ta med och konfigurera tillägget.
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: bd9541c5e4810085ab85206b2ecca21e66800a2f
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# [!DNL Express Checkout] onboarding

>[!IMPORTANT]
>
> Den här funktionen är endast avsedd för användare av tidig Adobe-programvara (EAP) och är ännu inte tillgänglig för alla kunder. För närvarande begränsat till amerikanska kunder. Kontakta Adobe Commerce Support för hjälp och frågor.

Så här kommer du igång med [!DNL Express Checkout] för Adobe Commerce-tillägg måste du slutföra några startsteg för att ansluta instansen med vår utcheckningsfunktion.

1. [Hämta tillägg](#get-extension).
1. [Skapa ett handelskonto för produktion eller sandlåda med [!DNL Bolt]](#create-account-with-bolt). Ange all information som krävs för att verifiera din identitet.
1. [Ange den unika API-nyckeln och den publiceringsbara nyckeln som genereras i [!DNL Bolt]](#obtain-api-credentials).
1. [Konfigurera en betalningsleverantör i [!DNL Bolt] konto](#configure-payment-providers).
1. [Ställ in listrutan Aktivera till Ja](#enable-extension) för att aktivera tillägget.
1. [Definiera dina tjänstinställningar](#complete-admin-configuration) för att konfigurera [!DNL Express Checkout] tillägg.
1. [Klicka på knappen Spara konfiguration](#enable-live-express-checkout) för att aktivera tillägg.

>[!NOTE]
>
> Om du inte konfigurerar [!DNL Bolt] konton (steg 2 ovan) du inte kan konfigurera din sandlåda eller produktionsmiljöer.

## Förutsättningar

För att kunna använda [!DNL Express Checkout]måste du ha följande tillgängliga för [!DNL Bolt]:

- Betalningsleverantörer som stöds
- Marknads- och produktionskonto i [!DNL Bolt]
- API och publiceringsbar nyckel genererad i [!DNL Bolt]

Se [krav](../express-checkout/prerequisites.md) för mer information.

Se [API-autentiseringsuppgifter](#obtain-api-credentials) om du vill lära dig hur du skapar eller kommer åt API-nycklar för din instans.

## Hämta tillägg

Se [installera](../express-checkout/install.md) om du vill ha detaljerad information om hur du skaffar tillägget.

## Skapa konto med bult

Innan du konfigurerar [!DNL Express Checkout] i din Adobe Commerce Admin måste du skapa en [sandlåda](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} och [produktion](https://merchant.bolt.com/register){target=&quot;_blank&quot;} handlarkonto i [!DNL Bolt]. Ange all information som krävs för att skapa ett konto i [!DNL Bolt].

Se [testa och validera](../express-checkout/testing.md) för mer information.

## Hämta API-autentiseringsuppgifter

Så här använder du [!DNL Express Checkout] du behöver [!DNL Bolt] unika nycklar. Hämta följande API-nycklar genom att navigera till **Utvecklare** > **API** > **Tangenter** i **Bolt Merchant Dashboard**.

- API-nyckel: En privat nyckel som används av bakänden för att interagera med [!DNL Bolt] API:er.
- Publiceringsbar nyckel: En tangent som används av den främre änden för att interagera med [!DNL Bolt] API:er.

Se [[!DNL Bolt] miljöinformation](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;} om du vill veta mer om API- och publiceringsnycklar för [!DNL Express Checkout] tillägg.

>[!CAUTION]
>
> Du måste skapa API-nycklar för både sandbox- och produktionsmiljöer.

## Konfigurera betalningsleverantörer

Följ stegen som beskrivs i [processorkonfiguration](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;} utvecklare [!DNL Bolt] sida.

## Aktivera tillägg

1. På _Administratör_ sidlist, navigera till **Lager** > **Konfiguration** > **Utcheckning** för att komma åt konfigurationssidan för administratör för utcheckning.

   ![Express Checkout](assets/admin-view.png)

1. I [!DNL Express Checkout] visa, ange **Aktivera** till `Yes`.
1. Välj metod (Sandbox eller Production) som ska användas.

   - Sandlåda för testning och utveckling
   - Produktion för att bearbeta transaktioner med direktbetalningsprocessor

1. Validera autentiseringsuppgifter efter att du har angett unika API- och publiceringsnycklar.

>[!CAUTION]
>
> Du måste ange unika API- och publiceringsnycklar innan du aktiverar tillägget, annars ser kunderna ett betalningsformulär och kan inte göra en beställning.

## Komplett administratörskonfiguration

1. På _Administratör_ sidlist, navigera till **Lager** > **Konfiguration** > **Utcheckning** för att komma åt den allmänna konfigurationssidan för administratör för utcheckning.
1. I _Tjänstinställningar_ anger du all information som krävs för att aktivera tillägget.
1. Ange _Betalningsåtgärd_ as:

   - Auktorisera: Hämta inte transaktionen automatiskt vid auktorisering.
   - Auktorisera och hämta: Hämta transaktionen automatiskt vid auktorisering.

Mer information om Adobe Commerce standardalternativ för utcheckning finns i [utcheckning](https://docs.magento.com/user-guide/configuration/sales/checkout.html) ämne.

## Aktivera direkt Express-utcheckning

Aktivera [!DNL Express Checkout] för Adobe Commerce-tillägg:

1. Klicka **Spara konfiguration**.
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Cache Management]** och klicka **[!UICONTROL Flush Cache]** om du vill uppdatera alla ogiltiga cacheminnen.

## Få hjälp

Startprocessen är utformad för att vägleda dig genom de steg som krävs för att konfigurera och aktivera [!DNL Express Checkout] funktionalitet. Kontakt [!DNL Adobe Commerce] utvecklingsteam via din tilldelade Slack [Adobe Beta Programchannel](http://adobe-beta-programs.slack.com/) om du behöver hjälp.

Se [testa och validera](../express-checkout/testing.md) för mer information.
