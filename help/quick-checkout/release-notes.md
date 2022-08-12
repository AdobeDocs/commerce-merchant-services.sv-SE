---
title: '''[!DNL Quick Checkout] Versionsinformation'
description: Läs versionsinformationen om du vill ha information om alla [!DNL Quick Checkout] releaser.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 27e91a640999cf83a0f0d6701e616f7ceecde12d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Versionsinformation

I versionsinformationen beskrivs den första versionen av [!DNL Quick Checkout] och innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigerat problem](../assets/fix.svg) Korrigeringar och förbättringar
![Känt fel](../assets/bug.svg) Kända fel

Se [Kommande versioner](https://devdocs.magento.com/release/) om du vill veta mer om releasescheman och support.

Se [Tillgänglighet](https://devdocs.magento.com/release/availability.html) i utvecklardokumentationen om du vill veta mer om produktkompatibilitet.

## v1.1.0

_12 augusti 2022_

![Korrigerat problem](../assets/fix.svg)<!-- Issue BOLT-375 --> Förbättringar av användarupplevelsen i [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) inkluderar nu bara de parametrar som är synliga och validerade när tillägget är aktiverat.

![Korrigerat problem](../assets/fix.svg)<!-- Issue BOLT-349 --> Kompatibilitetsförbättringar för befintliga leveransadresser med lastpallen.

## v1.0.0

_9 augusti 2022_

![Nytt](../assets/new.svg)<!-- Issue BOLT-341 --> Allmän tillgänglighetsrelease—[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) är nu kompatibelt med Adobe Commerce version 2.4.1 till 2.4.4.

![Nytt](../assets/new.svg)<!-- Issue BOLT-340 --> The [!DNL Quick Checkout] för Adobe Commerce kan installeras antingen för Adobe Commerce [om molninfrastruktur](install.md#adobe-commerce-on-cloud-infrastructure) eller [lokal](install.md#on-premises) -instanser. Dessa metoder kräver att ett kommandoradsgränssnitt används.

![Nytt](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] för Adobe Commerce har en optimerad butik med [enklicksfunktion](overview.md) utan att konsumenterna behöver fylla i något.

![Nytt](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] för Adobe Commerce känner automatiskt igen varje kund i sitt nätverk för [köp med ett klick](checkout-flow.md) direkt på er webbplats.

![Nytt](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] för Adobe Commerce tillåter en kund att vara samtidigt [inloggad i både Adobe Commerce- och Bolt-nätverk](checkout-flow.md/#quick-checkout-use-cases) för att ge bättre `one-click checkout` upplevelse.

![Nytt](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] för Adobe Commerce [sandlådekonto](testing.md#testing-in-sandbox) som gör det möjligt för handlare att bedöma tillägget i testläge.

![Nytt](../assets/new.svg)<!-- Issue BOLT-780 --> Dina kunder kan kolla in via [[!DNL Quick Checkout]](checkout-page.md) eller via [manuell orderhantering](create-order-admin.md).

![Nytt](../assets/new.svg)<!-- Issue BOLT-666 --> Handlare kan konfigurera [!DNL Quick Checkout] med grundläggande betalningsåtgärder, som [`Authorize and Capture` eller `Authorize` ](onboarding.md#complete-admin-configuration)eller växla mellan sandlådor och produktionsmiljöer.

![Nytt](../assets/new.svg)<!-- Issue BOLT-288 --> Egen [användarsessionens livstid](user-session-lifetime.md) for [!DNL Quick Checkout] för Adobe Commerce.

![Korrigerat problem](../assets/fix.svg)<!-- Issue BOLT-375 --> Förbättringar av användarupplevelsen i [[!DNL Quick Checkout] Admin Panel](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) gör att du kan spara konfigurationen när alla obligatoriska parametrar anges.

![Känt fel](../assets/bug.svg)<!-- Issue BOLT-342 --> Vanliga [felsökning](https://support.magento.com/hc/en-us/articles/6909450342541) vid installation av [!DNL Quick Checkout].
