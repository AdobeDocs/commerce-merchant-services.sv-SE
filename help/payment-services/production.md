---
title: Aktivera [!DNL Payment Services] för produktion
description: Slutför introduktionsprocessen genom att aktivera [!DNL Payment Services] för produktion.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# Aktivera [!DNL Payment Services] för produktion

Du kan sätta igång tjänsten och slutföra [introduktionsprocess](onboard.md), enligt stegen i det här avsnittet, efter att du:

* [Installera](install.md) tillägget Betalningstjänster
* [Konfigurera och ansluta](connect.md) din instans
* [Konfigurera](sandbox.md) och [test](test-validate.md) din sandlåda

## Ange [!DNL Payment Services] som betalningsmetod

Efter [konfigurera dina Commerce Services](connect.md#configure-commerce-services) och aktivera antingen [sandlådetestning](sandbox.md#enable-sandbox-testing) eller [direktbetalningar](#enable-live-payments)måste du ange [!DNL Payment Services] som betalningsmetod.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka **[!UICONTROL Enable Payment Services]**.

   Det här alternativet är synligt om du inte har konfigurerat ännu [!DNL Payment Services] som betalningsmetod för en eller flera av dina webbplatser.

   Du dirigeras till inställningsområdet i hemvyn med relevanta alternativ utökade (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), där du kan aktivera [!DNL Payment Services] som [betalningsmetod](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. I _[!UICONTROL General Configuration]_, ange **[!UICONTROL Enable]**till `Yes`.
1. Ange **[!UICONTROL Payment Action]**, för båda _[!UICONTROL Credit Card Fields]_och_[!UICONTROL PayPal Smart Buttons]_, till något av följande:

   | Inställning | Beskrivning |
   |---|---|
   | `Authorize` | Godkänner köpet och spärrar medlen. Beloppet dras inte tillbaka förrän handlaren&quot;fångar&quot; det. |
   | `Authorize and Capture` | Godkänner köpet och handlaren&quot;fångar&quot; pengarna. |

1. Klicka **[!UICONTROL Save]**.
1. Klicka **[!UICONTROL Go to Payment Services]** för att dirigeras tillbaka till [!DNL Payment Services] Hem.
1. [Rensa cachen](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   Rensning bör göras efter varje konfigurationsändring.

Se [Konfigurera betalningstjänster](settings.md) om du vill ha mer information om hur du konfigurerar kreditkortsfält och smarta PayPal-knappar.

## fullständig registrering av handlare

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka **[!UICONTROL Live onboarding]**.

   Det här alternativet är synligt om du ännu inte har slutfört live-introduktionen för [!DNL Payment Services].

   Du får ett PayPal-fönster.

1. Fortsätt med PayPal-flödet genom att använda dina PayPal-kontouppgifter (inte dina autentiseringsuppgifter för sandlådekonton) eller registrera dig för ett nytt PayPal-konto.
1. Gå till sidlisten Admin **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   The _[!UICONTROL Live onboarding]_knappen inte längre visas och du ser en[!UICONTROL Live payments pending]&quot;.

   I den textrutan kan du också bli ombedd att bekräfta din e-postadress hos PayPal för att slutföra introduktionen.

1. Om du uppmanas att bekräfta din e-postadress kontrollerar du om det finns ett bekräftelsemeddelande från PayPal i din e-postadress och klickar för att bekräfta din e-postadress.
1. Gå till sidlisten Admin **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Uppdatera webbläsarfönstret.

   När din PayPal-handlares introduktion har godkänts bör du se ett meddelande om att ditt betalningssystem är i sandlådeläge och inte hanterar livebetalningar.

   >[!IMPORTANT]
   >
   >Om du återkallar samtycke till [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] för bearbetning av dina betalningar (i dina PayPal-kontoinställningar), kan beställningar i din butik inte bearbetas av [!DNL Payment Services]. På startsidan för betalningstjänsterna visas en varning om det återkallade medgivandet.

## Begär betalningsberättigande från Adobe

Om du vill aktivera direktintroduktion måste du begära betalningstillstånd från Adobe:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka **[!UICONTROL Get Live Payments]** i [!DNL Payment Services] Hem.

   ![Begär berättiganden](assets/request-entitlements.png)

1. Fyll i formuläret.
1. En medlem i säljteamet kommer att kontakta dig.

Du kan också begära stödrättigheter från Adobe på [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Live-introduktion** är inte tillgängligt förrän stödrättigheten har godkänts.

## Konfigurera prisnivå

För att få [!DNL Payment Services] _Affärs-ID_:


1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. I hemvyn klickar du på **[!UICONTROL Settings]**. Se [Startsida](payments-home.md) för mer information.
1. Välj önskat _Affärs-ID_ och skicka in den till din säljare som kommer att konfigurera rätt prisnivå.

## Aktivera direktbetalningar

A _handels-ID för produktion_ genereras automatiskt och fylls i i [konfiguration](configure-admin.md). Ändra eller ändra inte detta ID.

Så här aktiverar du direktbetalningar:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka på **[!UICONTROL Settings]** längst upp till höger på sidan. Se [Startsida](payments-home.md) för mer information.
1. I _[!UICONTROL General Configuration]_avsnittsuppsättning **[!UICONTROL Payment mode]**till `Production`.
1. Klicka **[!UICONTROL Save]**.
1. [Rensa cachen](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >Om du inte rensar ditt cacheminne kan kunderna inte se betalningsalternativ för PayPal under utcheckningen.

Om du går tillbaka till [!DNL Payment Services] Hem visas inte längre meddelandet för sandlådebetalningsläget eftersom du nu bearbetar direktbetalningar.

Se [Konfigurera i administratören](configure-admin.md) för tidigare konfigurationsalternativ.

>[!IMPORTANT]
>
>Om du återkallar samtycke till [!DNL Payment Services] för bearbetning av dina betalningar (i dina PayPal-kontoinställningar), kan beställningar i din butik inte bearbetas av [!DNL Payment Services]. Om du vill återaktivera betalningshanteringen måste du slutföra introduktionen igen. På startsidan för betalningstjänsterna visas en varning om det återkallade medgivandet.

## Test i produktion

Vi rekommenderar att du testar produktionsbetalningar med riktiga kreditkort och banker innan du exponerar denna funktion för kunderna.

Se [Testa och validera](test-validate.md) för mer information.
