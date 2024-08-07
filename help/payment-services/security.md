---
title: Säkerhet och efterlevnad
description: Granska säkerhets- och efterlevnadskrav för er webbplats.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Säkerhet och efterlevnad

Säkerhet är mycket viktigt i [!DNL Payment Services] och ingen privat eller PCI-reglerad information skickas över din [!DNL Payment Services].

## Commerce säkerhet

[!DNL Adobe Commerce] och [!DNL Magento Open Source] innehåller stöd för flera säkerhetsfunktioner.

Se [Säkerhet](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} i användarhandboken för att läsa om bästa säkerhetspraxis och lära dig hur du hanterar administratörssessioner och autentiseringsuppgifter, implementerar CAPTCHA och hanterar webbplatsbegränsningar.

## PCI-kompatibilitet

Betalkortsbranschen (PCI) har fastställt en uppsättning krav för företag som tar emot betalningar via kreditkort via Internet. Förutom att upprätthålla en säker miljö är handlare som hanterar kundens kreditkortsinformation ansvariga för att följa vissa standardriktlinjer.

Mer information finns i [Riktlinjer för efterlevnad av PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"}.

Handlare kan fylla i ett [självutvärderingsfrågeformulär (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, som är ett självvalideringsverktyg för att utvärdera säkerheten för kortinnehavardata.

### Kreditkortsfält

Med kreditkortsfält skickas inga PCI-reglerade data via dina tjänster. Du behöver inte lagra eller underhålla dessa data, vilket avsevärt minskar problemen med PCI-kompatibilitet.

### 3DS

PCI 3-D Secure (3DS) möjliggör autentisering av köpare med kreditkortsutfärdaren vid köp av kreditkort online. Detta extra säkerhetsskikt bidrar till att förhindra onlinebedrägerier och krävs som en del av EU:s förordningar om regelefterlevnad.

[!UICONTROL Payment Services] tillhandahåller 3DS-funktioner som gör det möjligt för handlare att följa EU-regler och skydda kunder och handlare från bedräglig aktivitet i sina butiker.

Om du är handlare inom EU eller Storbritannien där 3DS-kompatibilitet krävs, måste du manuellt aktivera 3DS (det är `Off` som standard) i [Inställningar](settings.md#credit-card-fields).

>[!NOTE]
>
>3DS-kravet gäller transaktioner där affärsverksamheten och kortinnehavarens bank är belägna i [Europeiska ekonomiska samarbetsområdet](https://www.efta.int/eea) (EES) och Storbritannien. Handlare i USA behöver inte 3DS, men kan aktivera det för sina transaktioner om så önskas.

Order som handlaren/butikspersonalen lägger åt köparen är inte konfigurerade med 3DS-efterlevnadsåtgärder.

Mer information finns i [3DS i Inställningar](settings.md#3ds).

### Kortsäkring

När en kund [ valverar, eller sparar, sin kreditkortsinformation](vaulting.md) för framtida inköp i dina butiker, delas minimal kreditkortsinformation med kunden (de fyra sista siffrorna, kortets utgångsdatum och kortets varumärke). Kreditkortsinformation lagras hos betalningsförmedlaren. När ett kort upphör att gälla eller de inte längre behöver informationen sparad, kan de ta bort denna token så att informationen inte längre lagras av betalningsleverantören.

Mer information finns i [Kreditkortssäkringar](vaulting.md).

### Betalningsknappar för PayPal

Med betalningsknapparna PayPal skickas inga PCI-reglerade data över era tjänster. Du behöver inte lagra eller underhålla dessa data, vilket avsevärt minskar problemen med PCI-kompatibilitet.

Av säkerhetsskäl skickar PayPal inte faktureringsadressen under utcheckningen - land, e-post och namn är den enda faktureringsinformationen som används. Du kan också aktivera utcheckningen av din webbplats för PayPal för att returnera hela faktureringsadressen genom att kontakta PayPal och slutföra en kontrollprocess.

PayPal har också ett integrerat bedrägeriskydd som använder maskininlärning för att hjälpa dig att bekämpa bedrägerier. Mer information finns i PayPals [dokumentation om säljskydd](https://www.paypal.com/us/webapps/mpp/security/seller-protection).

## Bedrägeriskydd

Du kan aktivera automatiskt bedrägeriskydd för betaltjänster med tillägget [Signera](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Mer information finns i [Skydd mot bedrägeri](fraud-protection.md).

