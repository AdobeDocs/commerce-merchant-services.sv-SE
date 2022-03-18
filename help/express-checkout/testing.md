---
title: Testa [!DNL Express Checkout] för Adobe Commerce
description: Testning och validering säkerställer att [!DNL Express Checkout] tillägg fungerar som förväntat.
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Testa [!DNL Express Checkout] för Adobe Commerce

>[!IMPORTANT]
>
> Den här funktionen är endast avsedd för användare av tidig Adobe-programvara (EAP) och är ännu inte tillgänglig för alla kunder. För närvarande begränsat till amerikanska kunder. Kontakta Adobe Commerce Support för hjälp och frågor.

Innan du visar [!DNL Express Checkout] för Adobe Commerce-tillägg till era kunder rekommenderar vi att du testar i sandlådemiljö och i produktionsmiljön. Testning och validering säkerställer att [!DNL Express Checkout] fungerar som väntat och ger en smidig utcheckningsupplevelse för både er butik och era kunder.

Innan du konfigurerar [!DNL Express Checkout] i din Adobe Commerce Admin måste du skapa en [produktion](https://merchant.bolt.com/register){target=&quot;_blank&quot;} och [sandlåda](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} handlarkonto i Bolt.

## Testa i sandlåda

Testa [!DNL Express Checkout] i en sandlådemiljö är ett mycket viktigt valideringssteg, även om det är en simulerad miljö som bara är kopplad till Bult-sandlådekontot, inte till verkliga banker eller handlare.

### Använda sandlådekonto

När du testar och validerar din sandlåda måste du använda ett falskt kreditkortsnummer och ett [sandlåda](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} handlarkonto i Bolt, så att du inte skapar riktiga avgifter för ett befintligt kreditkortskonto.

## Testning i produktion

>[!NOTE]
>
> Vi rekommenderar att du testar [!DNL Express Checkout] i en produktionsmiljö, med riktiga kreditkort och banker, innan utökningen görs för kunderna. Även om det är viktigt att testa i sandlådan är testning i produktionen den mest dummista metoden för att säkerställa att den fungerar som förväntat.

Rekommenderas att testa i produktionen på ett av två sätt:

- Välj en tid då du vet att kunderna inte kommer att göra några beställningar.
- Använd en webbutik som tillfälligt inte är tillgänglig för kunderna, men som är tillgänglig för dig för testning.

Komplettera produktionstestningen med riktiga kreditkort och Bolt-produktionskonton och testa hela livscykeln för en utcheckning. När du är klar med hela utcheckningsflödet under testningen får du en tydlig bild av hur din funktionalitet fungerar när direktkunder använder den.

Du bör också kontrollera att informationen som visas på kontoutdragen för betalningsmetoderna som du använder i produktionstestningen är korrekt och förväntad (inklusive beskrivningen av ditt företag).

## Så här testar du [!DNL Express Checkout] extension

Utför en utcheckning från din butik enligt följande:

1. Gå till butiken och placera önskade artiklar i kundvagnen.
1. Gå till kassan.
1. Ange en e-postadress som är kopplad till ett bolt-konto när du uppmanas till det.
1. Ange engångslösenordet som skickas till kontots e-postadress.
1. Välj miljökontrollpanelen:

   - Sandbox
   - Produktion

1. Beställ.

När en beställning har lagts kan du se information om dina beställningar i _Ordningsrutnät_ vy:

1. Navigera till _Försäljning_ > _Beställningar_.
1. Se lista över alla placerade order.

Se [order](https://docs.magento.com/user-guide/sales/orders.html) om du vill ha mer information om _Ordningsrutnät_ vy.
