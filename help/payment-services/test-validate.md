---
title: Testa och validera
description: Testning och validering säkerställer att [!DNL Payment Services] fungerar som förväntat och erbjuder de bästa betalningsalternativen för dina kunder
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Testa och validera

Innan du visar [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] för era kunder är det en bra idé att testa i sandlådemiljön _och_ i produktion. Testning och validering säkerställer att [!DNL Payment Services] fungerar som väntat och ger de bästa betalningsalternativen för er butik och era kunder.

## Testa i sandlådemiljö

Testning [!DNL Payment Services] i en sandlådemiljö är ett viktigt valideringssteg, även om det är en simulerad miljö som bara är ansluten till PayPal-sandlådan, inte till verkliga banker och handlare.

1. Slutföra en utcheckning från din butik, antingen med [Kreditkortsfält](payments-options.md#credit-card-fields) eller någon av [Betalningsknappar för PayPal](payments-options.md#paypal-smart-buttons). Se [Testa autentiseringsuppgifter](#testing-credentials) om du vill ha mer information om hur du använder falska kreditkort för testning.
1. Fånga (när din betalningsåtgärd är [ange till `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [återbetalning](refunds.md), eller [void](voids.md) den helt färdiga ordern. Du kan också [skapa en faktura](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} för en order, om betalningsåtgärden är inställd på `Authorize` i stället för `Authorize and Capture`.
1. Inom 24-48 timmar kan du se transaktionen och annan information i [Utbetalningsrapport](payouts.md).
1. Se information om beställningen i [Statusrapport för orderbetalning](order-payment-status.md).

### Testa autentiseringsuppgifter

När du testar och validerar din sandlåda måste du använda falska kreditkortsnummer, så att du inte skapar riktiga avgifter för ett befintligt kreditkortskonto.

Använd PayPals kortgenerator för att [generera slumpmässig kreditkortsinformation](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) för testning.

Så här testar du Apple Pay i sandlådeläge:

* Skapa en [Apple sandlådeutvärderingskonto](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), komplett med fejkad kreditkortsinformation och faktureringsinformation.
* [Registrera dina sandlådedomäner](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPals betalningshantering i sandlådan är ibland långsam och tjänsten kan ibland gå ner. Denna situation är inte en indikation på hur snabb och effektiv handläggningen av produktbetalningar är.

## Test i produktion

Vi rekommenderar att du testar [!DNL Payment Services] i produktion, med riktiga kreditkort och banker, innan denna funktionalitet exponeras för kunderna. Även om du testar [!DNL Payment Services] i sandlådan är viktigt är testning i produktionen den mest dummista metoden för att säkerställa [!DNL Payment Services] fungerar som förväntat.

Du kan testa [!DNL Payment Services] i produktion på ett av två sätt:

* Välj en tid då du vet att kunderna inte kommer att beställa.
* Använd en webbutik som tillfälligt inte är tillgänglig för kunderna, men som är tillgänglig för dig för testning.

Slutför produktionstestningen med riktiga kreditkort och PayPal-konton och testa betalningens hela livscykel, inklusive hämtning och återbetalning. Om du slutför hela kassan och betalningsflödet under testningen får du den tydligaste bilden av hur [!DNL Payment Services] funktionaliteten kommer att fungera när de som handlar live använder den.

Du bör också kontrollera att informationen som visas på kontoutdragen för betalningsmetoderna som du använder i produktionstestningen är korrekt och förväntad (inklusive beskrivningen av ditt företag).

Om du vill testa Apple Pay i produktionsläge måste du [registrera dina produktionsdomäner](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
