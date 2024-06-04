---
title: Aktivera [!DNL Payment Services] för produktion
description: Slutför introduktionsprocessen genom att aktivera [!DNL Payment Services] för produktion.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Aktivera [!DNL Payment Services] för produktion

Du kan sätta igång tjänsten och slutföra [introduktionsprocess](onboard.md), enligt stegen i det här avsnittet, efter att du:

* [Installera](install.md) tillägget Betalningstjänster
* [Konfigurera och ansluta](connect.md) din instans
* [Konfigurera](sandbox.md) och [test](test-validate.md) din sandlåda

## Ange [!DNL Payment Services] som betalningsmetod

Efter dig [konfigurera dina Commerce-tjänster](connect.md#configure-commerce-services) och aktivera antingen [sandlådetestning](sandbox.md#enable-sandbox-testing) eller [direktbetalningar](#enable-live-payments)måste du ange [!DNL Payment Services] som betalningsmetod.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka på **[!UICONTROL Enable Payment Services]**.

   Det här alternativet är synligt om du inte har konfigurerat ännu [!DNL Payment Services] som betalningsmetod för en eller flera av dina webbplatser.

   Du dirigeras till inställningsområdet i hemvyn med relevanta alternativ utökade (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), där du kan aktivera [!DNL Payment Services] alternativ som [betalningsmetod](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. I _[!UICONTROL General Configuration]_, ange **[!UICONTROL Enable]**till `Yes`.
1. Ange **[!UICONTROL Payment Action]**, för båda _[!UICONTROL Credit Card Fields]_och_[!UICONTROL PayPal payment buttons]_, till något av följande:

   | Inställning | Beskrivning |
   |---|---|
   | `Authorize` | Godkänner köpet och spärrar medlen. Beloppet dras inte tillbaka förrän handlaren&quot;fångar&quot; det. |
   | `Authorize and Capture` | Godkänner köpet och handlaren&quot;fångar&quot; pengarna. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] har stöd för partiella klipp. En handlare kan delvis hämta (fakturera) delar av en order. Du kan till exempel hämta varje objekt individuellt, eller ett objekt nu och resten senare.

1. Klicka på **[!UICONTROL Save]**.
1. Klicka **[!UICONTROL Go to Payment Services]** för att dirigeras tillbaka till [!DNL Payment Services] Hem.
1. [Rensa cachen](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   Rensning bör göras efter varje konfigurationsändring.

Se [Konfigurera betalningstjänster](settings.md) om du vill ha mer information om hur du konfigurerar kreditkortsfält och PayPal-betalningsknappar.

## fullständig registrering av handlare

Nästa steg på vägen mot att göra era butiker tillgängliga med betaltjänster är att slutföra direktintroduktionen.

Betalningstjänster [**Avancerat** (stöds fullt ut) och **Standard** Betalningsalternativ (Express Checkout)](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) och introduktionsflöden, beroende på vilket land du är verksam i och vilken betalningsupplevelse du föredrar.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka på **[!UICONTROL Live onboarding]**.

   Det här alternativet är synligt om du ännu inte har slutfört live-introduktionen för [!DNL Payment Services].

1. I _Välj land_ modal, välj det land som du arbetar från.

   Betalningstjänster ger fullständigt stöd för alla betalningsalternativ i [fem länder](../payment-services/overview.md#availability) för närvarande. Betalningstjänster erbjuder funktioner för Express Checkout (en deluppsättning av betalningsalternativ) för alla andra länder som finns representerade i landslistan.

   Det land du väljer i listan avgör betalningsalternativen och introduktionsflödet -[Avancerat](#advanced-onboarding) (stöds fullt ut) eller [Standard](#standard-onboarding) (Express Checkout) - tillgänglig för dig.

>[!TIP]
>
> När du valt och fortsätter med ett introduktionsalternativ - Standard eller Avancerat - måste du slutföra introduktionen på nytt för att antingen uppgradera eller nedgradera från det ursprungliga valet.

### Avancerad introduktion

Detta introduktionsflöde är tillgängligt för handlare i [länder med fullt stöd](../payment-services/overview.md#availability).

När landet har valts:

1. I den modal som visas väljer du **Avancerat**.

   För **Standard** går du vidare till [Standardstartflöde](#standard-onboarding).

1. Klicka **Fortsätt**.
1. Fortsätt med PayPal-flödet för avancerad introduktion som stöds till fullo med hjälp av dina PayPal-kontoinloggningsuppgifter (inte dina autentiseringsuppgifter för sandlådekonton) _eller_ registrera ett nytt PayPal-konto.

>[!IMPORTANT]
>
>**Avancerad introduktion** kräver att handlare [stödrättighet](#request-payments-entitlement-from-adobe) för att möjliggöra live onboarding.

### Standard onboarding

Detta standardintroduktionsflöde är tillgängligt för handlare i tillgängliga länder för vilka [endast stöd för Express Checkout](../payment-services/overview.md#availability) anges.

När landet har valts:

1. I _Betalningstjänster, avtal_ modal som visas klickar du på **Betalningstjänster, avtal** om du vill visa Adobe Commerce Payment Services Agreement.
1. I _Betalningstjänster, avtal_ modal, klicka **Jag accepterar**.
1. Fortsätt med PayPal-flödet för Express Checkout-introduktion, med dina PayPal-kontoinloggningsuppgifter (inte dina autentiseringsuppgifter för sandlådekonton) eller registrera dig för ett nytt PayPal-konto.

>[!IMPORTANT]
>
>[Apple Betala- och kreditkortsfält](../payment-services/payments-options.md) är inte tillgängliga för **Standard onboarding**.

## Bekräfta e-postadress

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

## Begär berättigande för betalningar från Adobe

För att göra dina butiker levande, begär du betalningstillstånd från Adobe (för [Endast avancerad introduktion](#advanced-onboarding)):

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka **[!UICONTROL Get Live Payments]** i [!DNL Payment Services] Hem.

   ![Begär berättiganden](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Fyll i formuläret.
1. En medlem i säljteamet kommer att kontakta dig.

Du kan också begära stödrättigheter från Adobe på [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Live-introduktion** är inte tillgängligt förrän stödrättigheten har godkänts.

## Konfigurera prisnivå

Skaffa [!DNL Payment Services] _Affärs-ID_:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. I hemvyn klickar du på **[!UICONTROL Settings]**. Se [Startsida](payments-home.md) för mer information.
1. Välj önskat _Affärs-ID_ och skicka in den till din säljare som kommer att konfigurera rätt prisnivå.

Se [Bearbetning på nivå 2 och nivå 3](levels-card-payment-transactions.md) för mer information om betalningstransaktioner.

## Aktivera direktbetalningar

A _handels-ID för produktion_ genereras automatiskt och fylls i i [konfiguration](configure-admin.md). Ändra eller ändra inte detta ID.

Aktivera direktbetalningar:

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka på **[!UICONTROL Settings]** längst upp till höger på sidan. Se [Startsida](payments-home.md) för mer information.
1. I _[!UICONTROL General Configuration]_avsnittsuppsättning **[!UICONTROL Payment mode]**till `Production`.
1. Klicka på **[!UICONTROL Save]**.
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
