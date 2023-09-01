---
title: Säkerhet och efterlevnad
description: Granska säkerhets- och efterlevnadskrav för er webbplats.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: fef972355565472f0d0851a2e3cace692fb2db67
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Säkerhet och efterlevnad

Säkerheten är mycket viktig inom [!DNL Payment Services] och ingen information som regleras av privat system eller betalkortsföretag (PCI) skickas över din [!DNL Payment Services].

## Handelssäkerhet

[!DNL Adobe Commerce] och [!DNL Magento Open Source] har stöd för flera säkerhetsfunktioner.

Se [Säkerhet](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} i huvudanvändarhandboken för att granska de bästa säkerhetsrutinerna och lära dig hur du hanterar administratörssessioner och autentiseringsuppgifter, implementerar CAPTCHA och hanterar begränsningar för webbplatser.

## PCI-kompatibilitet

Betalkortsbranschen (PCI) har fastställt en uppsättning krav för företag som tar emot betalningar via kreditkort via Internet. Förutom att upprätthålla en säker miljö är handlare som hanterar kundens kreditkortsinformation ansvariga för att följa vissa standardriktlinjer.

Se [Riktlinjer för efterlevnad av PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} för mer information.

Handlare kan fylla i en [självbedömningsfrågeformulär](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, som är ett självvalideringsverktyg för att bedöma säkerheten för kortinnehavardata.

### Kreditkortsfält

Med kreditkortsfält skickas inga PCI-reglerade data via dina tjänster. Du behöver inte lagra eller underhålla dessa data, vilket avsevärt minskar problemen med PCI-kompatibilitet.

### 3DS

PCI 3-D Secure (3DS) möjliggör autentisering av köpare med kreditkortsutfärdaren vid köp av kreditkort online. Detta extra säkerhetsskikt bidrar till att förhindra onlinebedrägerier och krävs som en del av EU:s förordningar om regelefterlevnad.

[!UICONTROL Payment Services] tillhandahåller 3DS-funktionalitet som gör det möjligt för handlare att följa EU:s regler och skydda kunder och handlare från bedräglig verksamhet i sina butiker.

Om du handlar inom EU eller Storbritannien där 3DS-överensstämmelse krävs måste du manuellt aktivera 3DS (det är `Off` som standard) in [Inställningar](settings.md#credit-card-fields).

>[!NOTE]
>
>3DS-kravet gäller transaktioner där affärsverksamheten och kortinnehavarens bank är belägna i [Europeiska ekonomiska samarbetsområdet](https://www.efta.int/eea) (EES) och Storbritannien. Handlare i USA behöver inte 3DS, men kan aktivera det för sina transaktioner om så önskas.

Order som handlaren/butikspersonalen lägger åt köparen är inte konfigurerade med 3DS-efterlevnadsåtgärder.

Se [3DS i Inställningar](settings.md#3ds) för mer information.

### Kortsäkring

När en kund [vaults - eller&quot;save&quot; - deras kreditkortsinformation](vaulting.md) för framtida inköp i butikerna delas minimal kreditkortsinformation med kunden (de fyra sista siffrorna, kortets utgångsdatum och kortets varumärke). Kreditkortsinformation lagras hos betalningsförmedlaren. När ett kort upphör att gälla eller de inte längre behöver informationen sparad, kan de ta bort denna token så att informationen inte längre lagras av betalningsleverantören.

Se [Kreditkortssäkringar](vaulting.md) för mer information.

### Smarta knappar för PayPal

Med smarta PayPal-knappar skickas inga PCI-reglerade data över era tjänster. Du behöver inte lagra eller underhålla dessa data, vilket avsevärt minskar problemen med PCI-kompatibilitet.

Av säkerhetsskäl skickar PayPal inte faktureringsadressen under utcheckningen - land, e-post och namn är den enda faktureringsinformationen som används. Du kan också aktivera utcheckningen av din webbplats för PayPal för att returnera hela faktureringsadressen genom att kontakta PayPal och slutföra en kontrollprocess.

PayPal har också ett integrerat bedrägeriskydd som använder maskininlärning för att hjälpa dig att bekämpa bedrägerier. Se PayPals [Dokumentation om säljskydd](https://www.paypal.com/us/webapps/mpp/security/seller-protection) för mer information.

## Bedrägeriskydd

Du kan aktivera automatiskt bedrägeriskydd för betaltjänster med [Signifierat tillägg](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Se [Skydd mot bedrägeri](fraud-protection.md) för mer information.

