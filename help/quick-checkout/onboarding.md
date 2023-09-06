---
title: "Ta med dig [!DNL Quick Checkout] för Adobe Commerce-tillägg"
description: "Se hur [!DNL Quick Checkout] skulle kunna vara till nytta för er Adobe Commerce-instans och för att komma igång med och konfigurera tillägget."
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
feature: Checkout, Services
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---

# [!DNL Quick Checkout] Onboarding

Kom igång med [!DNL Quick Checkout] för Adobe Commerce-tillägg måste du slutföra några startsteg för att ansluta instansen med vår utcheckningsfunktion.

![Snabbutcheckning](assets/overview-admin-panel.png){width="800" zoomable="yes"}

1. [Hämta tillägg](#get-extension).
1. [Skapa ett handelskonto för produktion eller sandlåda med [!DNL Bolt]](#create-account-with-bolt). Ange all information som krävs för att verifiera din identitet.
1. [Ange unika [!DNL API Key] och [!DNL Publishable Key]](#obtain-api-credentials) genereras i [!DNL Bolt].
1. [Konfigurera en betalningsleverantör i [!DNL Bolt] konto](#configure-payment-providers).
1. [Ställ in listrutan Aktivera till Ja](#enable-extension) för att aktivera tillägget.
1. [Definiera dina tjänstinställningar](#complete-admin-configuration) för att konfigurera [!DNL Quick Checkout] tillägg.
1. [Klicka på Spara konfiguration](#enable-live-quick-checkout) för att aktivera tillägg.
1. Växla omfång till **Huvudwebbplats** och [klicka på Konfigurera återanrops-URL](#check-shopper-valid-account) -knappen.

Om Gainsight är aktiverat utlöses **Se vår demo** i [!DNL Quick Checkout] Administratörspanelen om [!DNL Quick Checkout] för Adobe Commerce:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > Avancerat:

   ![Snabbutcheckning](assets/gainsight-admin.png){width="500" zoomable="yes"}

Om Gainsight inte är aktiverat fortsätter du med introduktionsstegen.

Se [[!DNL Quick Checkout] Administratörspanelen](../quick-checkout/admin-panel.md) för mer information.

>[!NOTE]
>
> Om du inte konfigurerar [!DNL Bolt] konton som du inte kan konfigurera sandlådan eller produktionsmiljöer för.

## Förutsättningar

För att kunna använda [!DNL Quick Checkout]måste du ha följande tillgängliga för [!DNL Bolt]:

- Betalningsleverantörer som stöds
- Marknads- och produktionskonto i [!DNL Bolt]
- API och [!DNL Publishable key] genereras i [!DNL Bolt]

Se [krav](../quick-checkout/prerequisites.md) för mer information.

Se [API-referenser](#obtain-api-credentials) om du vill lära dig hur du skapar eller använder [!DNL API keys] till din instans.

## Hämta tillägg

Se [installera](../quick-checkout/install.md) för detaljerad information om hur du får tillägget.

## Skapa konto med [!DNL Bolt]

Innan du konfigurerar [!DNL Quick Checkout] i din Adobe Commerce Admin måste du skapa en [sandlåda](https://merchant-sandbox.bolt.com/register?platform=magento2){target="_blank"} and [production](https://merchant.bolt.com/register?platform=magento2){target="_blank"}  handlarkonton i [!DNL Bolt]. Ange all information som krävs för att skapa ett konto i [!DNL Bolt].

Se [testa och validera](../quick-checkout/testing.md) för mer information.

## Hämta API-autentiseringsuppgifter

Använd [!DNL Quick Checkout] du behöver [!DNL Bolt] unika nycklar och [!DNL signing secret]. Hämta följande [!DNL API keys] genom att navigera till **Utvecklare** > **API** > **Tangenter** i **Bolt Merchant Dashboard**.

- [!DNL API key]: En privat nyckel som används av bakgrunden för interaktion med [!DNL Bolt] API.
- [!DNL Publishable key]: En tangent som används av den främre änden för att interagera med [!DNL Bolt] API.
- [!DNL Signing secret]: Används för signaturverifiering på begäranden som tas emot från [!DNL Bolt].

  ![Snabbutcheckning](assets/account-credentials.png){width="500" zoomable="yes"}

Se [[!DNL Bolt] miljöinformation](https://help.bolt.com/developers/references/environment-details/#about-keys){target="_blank"} sida där du kan lära dig mer om nycklar och signeringshemligheter [!DNL Bolt] för [!DNL Quick Checkout] tillägg.

>[!CAUTION]
>
> Du måste skapa [!DNL API keys] för både sandbox- och produktionsmiljöer.

## Konfigurera betalningsleverantörer

Följ stegen som beskrivs i [processorkonfiguration](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target="_blank"} utvecklare [!DNL Bolt] sida.

## Aktivera tillägg

1. På _Administratör_ sidebar, gå till **Lager** > _Inställningar_ > **Konfiguration**.
1. Expandera på den vänstra panelen **Försäljning** och markera **Utcheckning**.
1. I [!DNL Quick Checkout] visa, ange **Aktivera** till `Yes`.

![Snabbutcheckning](assets/quick-checkout-view-no-enable.png){width="500" zoomable="yes"}

>[!CAUTION]
>
> Snabbutcheckningsfält visas bara när **Aktivera** är inställd på `Yes`.

1. Välj metod (Sandbox eller Production) som ska användas.

   - Sandlåda för testning och utveckling
   - Produktion för att bearbeta transaktioner med direktbetalningsprocessor

1. Validera autentiseringsuppgifter efter att du har angett ditt unika API och [!DNL Publishable keys].

![Snabbutcheckning](assets/quick-checkout-main-view.png){width="500" zoomable="yes"}

Se [Inställningar](../quick-checkout/settings-quick-checkout.md) om du vill ha mer information om konfigurationsalternativen för [!DNL Quick Checkout] för Adobe Commerce.

>[!CAUTION]
>
> Du måste ange ett unikt API och [!DNL Publishable] nycklar innan tillägget aktiveras, annars ser kunderna ett betalningsformulär och kan inte göra en beställning.

## Komplett administratörskonfiguration

1. På _Administratör_ sidlist, navigera till **Lager** > **Konfiguration** > **Utcheckning** för att komma åt den allmänna konfigurationssidan för administratör för utcheckning.
1. I _Tjänstinställningar_ anger du all information som krävs för att aktivera tillägget.
1. Ange _Betalningsåtgärd_ till båda alternativen:

   - `Authorize`: Hämta inte transaktionen automatiskt vid auktorisering.
   - `Authorize and Capture`: Hämta transaktionen automatiskt vid auktorisering.

Mer information om Adobe Commerce standardalternativ för utcheckning finns i [utcheckning](https://docs.magento.com/user-guide/configuration/sales/checkout.html) ämne.

## Aktivera direktutcheckning

Aktivera [!DNL Quick Checkout] för Adobe Commerce-tillägg:

1. Kontrollera att [!UICONTROL Enable] listrutan är inställd på **Ja** för att aktivera tillägget.
1. Klicka **Spara konfiguration**.

## Kontrollera köparens giltiga konto

För att kontrollera om kunden har en [!DNL Bolt] konto:

1. Växla omfånget till **Huvudwebbplats**.
1. Klicka på **Konfigurera återanrops-URL** -knappen. Detta aktiverar [!DNL Bolt] för att avgöra om kunden har ett konto. Om de gör det visas popup-fönstret för engångslösenord.

   >[!CAUTION]
   >
   > Byta omfång till **Huvudwebbplats** ser till att rätt URL anges. Varje webbplats kan ha flera domäner.

Se [Plats, butik och visningsomfång](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings){target="_blank"} om du vill ha mer information om omfattningar i Adobe Commerce.

## Konfigurera tjänstinställningar

![Snabbutcheckning](assets/service-settings.png){width="500" zoomable="yes"}

1. Ange **Aktivera utcheckningsspårning** till `Yes`.

   >[!CAUTION]
   >
   > Om du inaktiverar det här alternativet påverkas rapporteringen eftersom Adobe Commerce inte får dela utcheckningsspårningsinformation med Bolt.

1. Välj **Nästa scen efter inloggning** alternativ för att ändra navigeringsflödet när kunden har loggat in. Som standard är den inställd på **Betalningar** sida.
1. Definiera om [!DNL Quick Checkout] ger **automatisk inloggning** vid utcheckning. Som standard är det aktiverat att automatiskt logga in på [!DNL Bolt] nätverk.

   >[!NOTE]
   >
   > Se [Bults Enable Automatic Login documentation](https://help.bolt.com/products/embedded/direct-api/auto-login/) för mer information.

## Få hjälp

Startprocessen är utformad för att vägleda dig genom de steg som krävs för att konfigurera och aktivera [!DNL Express Checkout] funktionalitet.

Kontakta Adobe Commerce Support via [Adobe Commerce Help Center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) om du behöver hjälp.

Se [testa och validera](../quick-checkout/testing.md) för mer information.
