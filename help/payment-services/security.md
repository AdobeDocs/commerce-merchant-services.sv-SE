---
title: Säkerhet och efterlevnad
description: Granska säkerhets- och efterlevnadskrav för er webbplats.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Säkerhet och efterlevnad

Säkerheten är mycket viktig när det gäller [!DNL Payment Services] och ingen information som regleras av privat system eller betalkortsföretag (PCI) skickas över din [!DNL Payment Services].

## Handelssäkerhet

[!DNL Adobe Commerce] och [!DNL Magento Open Source] har stöd för flera säkerhetsfunktioner.

Se [Säkerhet](https://docs.magento.com/user-guide/stores/security.html){target=&quot;_blank&quot;} i huvudanvändarhandboken för att läsa om bästa säkerhetspraxis och lära dig hur du hanterar administratörssessioner och autentiseringsuppgifter, implementerar CAPTCHA och hanterar webbplatsbegränsningar.

## PCI-kompatibilitet

Betalkortsbranschen (PCI) har fastställt en uppsättning krav för företag som tar emot betalningar via kreditkort via Internet. Förutom att upprätthålla en säker miljö är handlare som hanterar kundens kreditkortsinformation ansvariga för att följa vissa standardriktlinjer.

Se [Riktlinjer för efterlevnad av PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;} om du vill ha mer information.

Handlare kan fylla i en [självbedömningsfrågeformulär](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}, som är ett självvalideringsverktyg för att utvärdera säkerheten för kortinnehavardata.

### Kreditkortsfält

Med kreditkortsfält skickas inga PCI-reglerade data via dina tjänster. Du behöver inte lagra eller underhålla dessa data, vilket avsevärt minskar problemen med PCI-kompatibilitet.

### Smarta knappar för PayPal

Med smarta PayPal-knappar skickas inga PCI-reglerade data över era tjänster. Du behöver inte lagra eller underhålla dessa data, vilket avsevärt minskar problemen med PCI-kompatibilitet.

Av säkerhetsskäl skickar PayPal inte faktureringsadressen under utcheckningen - land, e-post och namn är den enda faktureringsinformationen som används. Du kan också aktivera utcheckningen av din webbplats för PayPal för att returnera hela faktureringsadressen genom att kontakta PayPal och slutföra en kontrollprocess.

PayPal har också ett integrerat bedrägeriskydd som använder maskininlärning för att hjälpa dig att bekämpa bedrägerier. Se PayPals [Dokumentation om säljskydd](https://www.paypal.com/us/webapps/mpp/security/seller-protection) för mer information.
