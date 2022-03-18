---
title: '"[!DNL Payment Services] Versionsinformation"'
description: Läs versionsinformationen om du vill ha information om alla [!DNL Payment Services] releaser.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Versionsinformation

I versionsinformationen beskrivs den första versionen av [!DNL Payment Services] och innehåller:

![Nytt](../assets/new.svg) Nya funktioner
![Korrigerat problem](../assets/fix.svg) Korrigeringar och förbättringar
![Känt fel](../assets/bug.svg) Kända fel

## v1.0.0

![Nytt](../assets/new.svg)<!-- Issue PAY-2127 --> Allmän tillgänglighetsrelease. [Betalningstjänster](https://marketplace.magento.com/magento-payment-services.html) är nu kompatibelt med Adobe Commerce och Magento Open Source, version 2.4.0 till 2.4.3-p1.

![Nytt](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] tillägg för Adobe Commerce och Magento Open Source kan installeras för [Adobe Commerce i molninfrastruktur](install.md#magento-commerce-cloud) eller [Lokalt](install.md#on-premises) -instanser. Dessa metoder kräver att ett kommandoradsgränssnitt används.

![Nytt](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] har stöd för [sandlådekonto](onboard.md#enable-sandbox-testing) som gör det möjligt för handlare att bedöma tillägget i testläge.

![Nytt](../assets/new.svg)<!-- Issue PAY-666 --> Handlare kan [konfigurera betaltjänster](configure-admin.md) tillägg med grundläggande betalningsbeteenden (som Auth-capture-kombination och växling mellan sandbox- och produktionsmiljöer).

![Nytt](../assets/new.svg)<!-- Issue PAY-780 --> Köpare kan kolla med [!DNL Payment Services] eller så kan du beställa via telefon och [skapa en hel order](create-order.md) i Admin för dem.

![Nytt](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] erbjuder säljarna omfattande rapportering så att ni får en tydlig bild av era butiksbeställningar och betalningar.

![Nytt](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] stöder differentierade priser (baserat på TPV) som är anpassade till alla handlare.

![Nytt](../assets/new.svg)<!-- Issue PAY-1443 --> Du kan anpassa utseendet på PayPal-knapparna och CC-fälten för [Betalningstjänster](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) tillägg.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2473 --> Använda [felaktiga dispositionsnycklar](https://support.magento.com/hc/en-us/articles/4406603542541) under installationen av tillägget förhindrar användare att [autentisera](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) med rätt `MAGEID`.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [rapporter](https://support.magento.com/hc/en-us/articles/4406114741517) för utbetalnings- och orderbetalningsstatus får inte synkroniseras omedelbart.

![Känt fel](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal-sandlådekonto](https://support.magento.com/hc/en-us/articles/4406954952461) for [!DNL Payment Services] kan inte verifieras.
