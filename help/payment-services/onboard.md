---
title: Inbyggt [!DNL Payment Services]
description: Koppla instansen till [!DNL Payment Services] genom att slutföra några steg i introduktionen.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Inbyggt [!DNL Payment Services]

Kom igång med att använda [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source]måste du slutföra några startsteg för att ansluta instansen med betalningsfunktionen.

## Startflöde

![Startflöde](assets/onboarding-diagram.svg){width="600" zoomable="yes"}

Det här introduktionsflödesdiagrammet visar den allmänna processen för introduktion [!DNL Payment Services].

När du är klar med introduktionen av sandlådor eller livebetalningar är ekonomisk rapportering tillgänglig från [!DNL Payment Services] i Admin.

Om både sandlåda och live-betalningar är aktiverade kan du enkelt växla mellan dessa lägen från [!DNL Payment Services] Hem.

## Förutsättningar

För att kunna använda [!DNL Payment Services]måste du ha följande tillgängliga för din instans:

* Modulen Services Connector
* Tjänster-ID-modul
* API-nycklar

Services Connector- och Services ID-modulerna installeras automatiskt under [installation av [!DNL Payment Services]](install.md). När installationen är klar visas ett nytt avsnitt i konfigurationsinställningarna (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) när du expanderar **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Om du vill veta mer om hur du skapar eller får åtkomst till dina API-nycklar kan du läsa [API-referenser](#obtain-api-credentials).

## Onboarding-steg

1. [Installera [!DNL Payment Services] extension](install.md#get-payment-services).
1. [Hämta API-autentiseringsuppgifter](connect.md#obtain-api-credentials).
1. [Anslut instansen](connect.md#configure-commerce-services) till Commerce Services. Den här anslutningen får bara slutföras en gång per Commerce-instans.
1. [Konfigurera sandlådetjänsten](sandbox.md#enable-sandbox-testing) (eller, alternativt, fortsätta till [aktivera direktbetalningar](sandbox.md#enable-live-payments) om du har testat funktionaliteten i en annan miljö) med ett PayPal-betalningshanteringskonto.
1. [Ange [!DNL Payment Services] som betalningsmetod](production.md#set-payment-services-as-payment-method), i sandlådeläge, för att börja bearbeta testbetalningar.
1. [Begär berättiganden för betalningar](production.md#request-payments-entitlement-from-adobe) för att möjliggöra live onboarding.
1. [fullständig registrering av handlare](production.md#complete-merchant-onboarding) för att aktivera direktbetalningar för era Commerce-webbplatser.
1. [Skaffa [!DNL Payment Services] Affärs-ID](production.md#configure-pricing-tier) och skicka det till säljarna för att konfigurera rätt prisnivå.
1. [Aktivera [!DNL Payment Services] i direktläge](production.md#enable-live-payments) för att börja behandla direktbetalningar.
1. Testa betalningar, i båda [sandlåda](sandbox.md#test-in-sandbox-environment) och [produktion](production.md#test-in-production) miljöer.

>[!NOTE]
>
>Om du inte konfigurerar dina Commerce Services i Admin (steg 3) kan du inte konfigurera sandlådor eller livesändningar.

## Felsökning

* [Felsökning [!DNL Payment Services] installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [PayPal-sandlådekontot har inte verifierats](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [Fördröjd [!DNL Payment Services] rapportdata](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [Testa kreditkortet fungerar inte med PayPal när betalningar bearbetas i en sandlådemiljö](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
