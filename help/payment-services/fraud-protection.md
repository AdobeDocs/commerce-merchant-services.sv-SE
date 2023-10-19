---
title: Skydd mot signering av bedrägeri
description: Aktivera automatiskt bedrägeriskydd för [!DNL Payment Services] med Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 480b35fbc57b8528dbc305aa7db52483ba49d98c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Skydd mot bedrägeri

Du kan aktivera automatiskt bedrägeriskydd för [!DNL Payment Services] med [Signifierat tillägg](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce har stöd för Signifyd version 5.4.0 och senare. [!DNL Payment Services] har stöd för signeringsflöden före och efter autentisering.

Signifyd/[!DNL Payment Services] integrering ger täckning för kreditkort, betalkort, vaultkort, utcheckning via Admin samt betalningsmetoder för PayPal och Apple Pay. Vissa detaljer om transaktionerna delas inte mellan Betalningstjänster och Signifyd, men Signifyd erbjuder en omfattande risktäckning för alla betalningsmetoder och garanterar ett så gott skydd som möjligt.

Se [Underteckna dokumentation](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) om du vill veta mer om hur du installerar och konfigurerar tillägget.

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
