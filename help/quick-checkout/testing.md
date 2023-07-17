---
title: "Testar [!DNL Quick Checkout] för Adobe Commerce-tillägg"
description: "Testning och validering säkerställer att [!DNL Quick Checkout] tillägg fungerar som förväntat."
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Testa [!DNL Quick Checkout] extension

Innan du visar [!DNL Quick Checkout] för Adobe Commerce-tillägg till era kunder rekommenderar vi att du testar i sandlådemiljö och i produktionsmiljön. Testning och validering säkerställer att [!DNL Quick Checkout] fungerar som väntat och ger en smidig utcheckningsupplevelse för både er butik och era kunder.

Innan du konfigurerar [!DNL Quick Checkout] i din Adobe Commerce Admin måste du skapa  [produktion](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} handlarkonton i [!DNL Bolt].

## Testa i sandlåda

Testa [!DNL Quick Checkout] i en sandlådemiljö är ett mycket viktigt valideringssteg, även om det är en simulerad miljö som bara är ansluten till [!DNL Bolt] sandlådekonto, inte till riktiga banker eller handlare.

### Använda sandlådekonto

När du testar och validerar din sandlåda måste du använda ett falskt kreditkortsnummer och ett [sandlåda](https://merchant-sandbox.bolt.com/register){target="_blank"} handelskonto i [!DNL Bolt]så att du inte skapar reella avgifter för ett befintligt kreditkortskonto.

## Testning i produktion

>[!NOTE]
>
> Vi rekommenderar att du testar [!DNL Quick Checkout] i en produktionsmiljö, med riktiga kreditkort och banker, innan utökningen görs för kunderna. Även om det är viktigt att testa i sandlådan är testning i produktionen den mest dummista metoden för att säkerställa att den fungerar som förväntat.

Testa produktionsmiljön på något av följande två sätt:

- Välj en tid då du vet att kunderna inte kommer att göra några beställningar.
- Använd en webbutik som tillfälligt inte är tillgänglig för kunderna, men som är tillgänglig för dig för testning.

Komplettera produktionstestningen med riktiga kreditkort och [!DNL Bolt] produktionskonton, testa hela livscykeln för en utcheckning. När du är klar med hela utcheckningsflödet under testningen får du en tydlig bild av hur funktionen fungerar när kunderna använder den.

Du bör också kontrollera att informationen som visas på kontoutdragen för betalningsmetoderna som du använder i produktionstestningen är korrekt och förväntad (inklusive beskrivningen av ditt företag).

## Så här testar du [!DNL Quick Checkout] extension

Slutför en utcheckning från din butik:

1. Gå till butiken och placera önskade artiklar i kundvagnen.
1. Gå till kassan.
1. Ange en e-postadress som är associerad med en [!DNL Bolt] när du uppmanas att göra det.
1. Ange engångslösenordet som skickas till kontots e-postadress.
1. Välj miljökontrollpanelen:

   - Sandbox
   - Produktion

1. Beställ.

När en beställning har lagts kan du se information om dina beställningar i _Ordningsrutnät_ vy:

1. Navigera till _Försäljning_ > _Beställningar_.
1. Se lista över alla placerade order.

Se [Beställningar](https://docs.magento.com/user-guide/sales/orders.html) om du vill ha mer information om _Ordningsrutnät_ vy.
