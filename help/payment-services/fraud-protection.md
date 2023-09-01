---
title: Skydd mot signering av bedrägeri
description: Aktivera automatiskt bedrägeriskydd för [!DNL Payment Services] med Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
source-git-commit: 400d1f8a384fceebcd13e9496f8e218e694d2752
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# Skydd mot bedrägeri

Du kan aktivera automatiskt bedrägeriskydd för [!DNL Payment Services] med [Signifierat tillägg](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce har stöd för Signifyd version 5.4.0 och senare. [!DNL Payment Services] har stöd för signeringsflöden före och efter autentisering.

Se [Underteckna dokumentation](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) om du vill veta mer om hur du installerar och konfigurerar tillägget.

## Integreringsbegränsningar

För närvarande gäller följande begränsningar för integreringen mellan Signifyd och [!DNL Payment Services]:

* Signifyd/[!DNL Payment Services] endast stöd för integrering [kortfält](../payment-services/payments-options.md#credit-card-fields) (inte betalningsknappar för PayPal eller Apple Pay). [!DNL Payment Services] skickar beställningsdata som tas emot via betalningsknapparna PayPal och Apple Pay to Signifyd, men integreringen ger bara information om beställningar som görs via kreditkortsfält.
* Signifyd har inte stöd för beställningar som gjorts i administratören av en handlare för en kund.
* Signified stöder inte order som placerats med [bankkreditkort](../payment-services/vaulting.md).

## Onboarding

Du måste kommunicera direkt med Signifyd för att kunna ta med tillägget för användning med [!DNL Payment Services]- det finns inget [!DNL Payment Services] konfiguration krävs. Du kan konfigurera signeringstillägget i Admin när det har installerats. Allt stöd som hör till det här tillägget hanteras av Signifyd.

Vid introduktion med Signifys måste du:

1. Kontakta Signified om du vill konfigurera ett nytt konto.
1. Som standard är Signify [tillåtslista](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) för att säkerställa att Signify inte utlöser för andra betalningsalternativ som för närvarande inte stöds. Om du vill förbjuda en viss betalningsmetod måste du göra ändringar.
1. Bekräfta med Signifyd att PayPal inte kommer att avslå beställningar, via handlarens inställning för bedrägeriskydd i Paypal, som skulle kunna godkännas av Signifyd.
1. Aktivera signeringstillägget så att det är kompatibelt med [!DNL Payment Services]:
   * När du använder [!DNL Payment Services] in _Live_ signeringsläge måste vara i produktionsläge.
   * När du använder [!DNL Payment Services] in _Sandbox_ signeringsläge måste vara i testläge.

## Konfiguration

Eftersom Signified utför en viss åtgärd på dina beställningar är det nödvändigt att konfigurera tillägget så att det beter sig korrekt baserat på den betalningsåtgärd du ställt in för [!DNL Payment Services].

De här konfigurationsalternativen är inte kompatibla med betaltjänster och signeringsintegrering:

* När [!DNL Payment Services] är konfigurerad med `Authorize` betalningsåtgärd _och_ Signifys är i `PostAuth` med _[!UICONTROL Decline Guarantees]_alternativ inställt på&#x200B;**Skapa kreditnota**.

  Orsak: [!DNL Payment Services] skapar en auktoriseringstransaktion som Signify sedan försöker återbetala.


* [!DNL Payment Services] är konfigurerad med `Authorize and Capture` betalningsåtgärd _och_ Signifys är i `PostAuth` med _[!UICONTROL Decline Guarantees]_alternativ inställt på&#x200B;**Avbryt beställning**.

  Orsak: [!DNL Payment Services] skapar en hämtningstransaktion som Signifyd sedan försöker annullera.


Mer information om signering finns i Signera-dokumentationen [konfigurera tillägget](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Se Signera dokumentation för att [läs mer om orderarbetsflödena](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
