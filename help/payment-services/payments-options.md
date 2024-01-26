---
title: Betalningsalternativ
description: Ange betalningsalternativen för att anpassa de metoder som är tillgängliga för dina butikskunder.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 7ea19e5c47142e31995c570c5e1efb50850d99b2
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 0%

---

# Betalningsalternativ

Med [!DNL Adobe Commerce] och [!DNL Magento Open Source] [!DNL Payment Services]har du flera betalningsalternativ.

Du kan konfigurera betalningsalternativen i [Heminställningar](payments-home.md) eller [Butikskonfiguration](configure-admin.md) (rekommenderas för äldre betalningsalternativ eller en konfiguration för flera butiker).

Det finns olika beteenden för varje betalningsmetod beroende på var du befinner dig i utcheckningsprocessen:

* Produktsida - produktsidan för en artikel
* Mini cart - Tillgängligt när du klickar på varukorgen när en produkt har lagts till i varukorgen
* Kundvagn - Tillgänglig när du klickar på _Visa och redigera kundvagn_ från minivagnen
* Utcheckningsvy - tillgänglig när du klickar på _Gå till kassan_ från minivagn eller kundvagn

>[!IMPORTANT]
>
>[!DNL Payment Services] Införandet måste vara slutfört innan betalningarna kan behandlas.

## Standard vs. Advanced Payments Experience

[!DNL Payment Services] innehåller **Avancerat** (stöds fullt ut) och **Standard** (Express Checkout) Betalningsalternativ och introduktionsflöden, beroende på vilket land du arbetar i.

* **Avancerat** - Alla tillgängliga [betalningsalternativ](../payment-services/payments-options.md) är tillgängliga för aktuell [länder med fullt stöd](../payment-services/overview.md#availability). Vid introduktionen för att aktivera livebetalningar väljer du [Avancerat alternativ för onboarding](../payment-services/production.md#advanced-onboarding).
* **Standard** - En delmängd av betalningsalternativen (Express Checkout) - PayPal-kort för kredit- och debetkort - finns för andra tillgängliga länder som stöds. [Kreditkortsfält](#credit-card-fields) och [Apple Pay](#apple-pay-button) är inte tillgängliga för det här introduktionsalternativet. Vid introduktionen för att aktivera livebetalningar väljer du [Standardalternativ för onboarding](../payment-services/production.md#standard-onboarding).

Se [Aktivera [!DNL Payment Services] för produktion](../payment-services/production.md#complete-merchant-onboarding) för information om avancerad och standardintroduktion.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] tillhandahålla en enkel och säker utcheckning av betalningsmetoder för kreditkort eller betalkort. När en kund checkar ut med kreditkortsfält anger han/hon sitt namn, sin faktureringsadress och kreditkortsinformation för att göra sin beställning. Deras kundinformation används säkert under köpsessionen för att smidigt vägleda dem genom utcheckningsflödet.

![Kreditkortsfält i kassan](assets/credit-card-fields.png){width="500" zoomable="yes"}

Aktivera [kreditkortsvalv](#vaulting) för butikerna så att kunderna kan vault (save) sina kreditkortsuppgifter för en snabb utcheckning senare.

Du kan konfigurera [!UICONTROL Credit Card Fields] i butikskonfigurationen eller [!DNL Payment Services] Hem. Se [Inställningar](settings.md#credit-card-fields) för mer information.

Du kan också ändra layout, bredd, höjd och yttre format för kreditkortsfälten. Se [PayPal-dokumentation](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) för mer information.

## [!DNL Apple Pay] knapp

Kunder kan använda [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), som använder betalnings- och betalkortsuppgifter som lagras på en iOS- eller macOS-enhet för att göra inköp.

[!DNL Apple Pay] är bara tillgängligt i webbläsaren Safari.

![Apple Pay button in the minicart](assets/apple-pay-button.png){width="500" zoomable="yes"}

The [!DNL Apple Pay] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

>[!NOTE]
>
> Används [!DNL Apple Pay] för butikerna, fullständigt [självregistrering med [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Registrera din livedomän_ endast ) och [konfigurera den för dina butiker i [!DNL Payment Services]](settings.md#payment-buttons).

Du kan konfigurera [!UICONTROL Apple Pay] i butikskonfigurationen eller startsidan för Betalningstjänster. Se [Inställningar](settings.md#apple-pay) för mer information.

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons], som använder PayPal för att slutföra ett köp, lagrar kundens leveransadress, faktureringsadress och betalningsinformation för senare bruk. Köpare kan använda vilken betalningsmetod som helst som tidigare lagrats eller erbjuds av PayPal.

![PayPal-knapp](assets/paypal-button.png){width="350" zoomable="yes"}

Du kan konfigurera [!UICONTROL PayPal payment buttons] i butikskonfigurationen eller [!DNL Payment Services] Hem.  Se [Inställningar](settings.md#payment-buttons) för mer information.

Se PayPals [Dokumentation om betalningsmetoder](https://developer.paypal.com/docs/checkout/payment-methods/) för att lära sig i vilka länder varje betalningsmetod finns tillgänglig för närvarande.

### [!DNL PayPal] knapp

Med PayPal-knappen kan kunderna enkelt och säkert kolla in resultatet.

The [!DNL PayPal] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

### [!DNL Venmo] knapp

Kunder kan checka ut med [Venmo](https://venmo.com/) -knappen.

The [!DNL Venmo] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

### PayPal Debit eller kreditkortsknapp

Kunder kan checka ut med PayPal Debit- eller kreditkortsknappen.

Knappen PayPal Debit eller Kreditkort visas på utcheckningssidan.

Det här alternativet kan användas för att visa kunderna ett betalnings- eller kreditkortsalternativ med en PayPal-värdbaserad knapp som ett alternativ till en kreditkortsintegrering.

### [!DNL Pay Later] knapp

Erbjud era kunder kortfristiga räntefria betalningar och andra finansieringsalternativ så att de kan köpa nu och betala senare med [!DNL Pay Later] -knappen.

The [!DNL Pay Later] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

Se information om Betala senare erbjudanden i [PayPal&#39;s Pay Later erbjuder dokumentation](https://developer.paypal.com/docs/checkout/pay-later/us/). Använd **Land/region** för att välja ett intresseområde.

Se [Inställningar](settings.md#payment-buttons) för att lära dig hur du inaktiverar/aktiverar [!DNL Pay Later] meddelanden.

## Använd endast PayPal-betalningsknappar

För att snabbt få butiken i produktionsläge kan du konfigurera _endast_ Betalningsknappar för PayPal (Venmo, PayPal osv.)- i stället för att också använda betalningsalternativet PayPal-kreditkort.

På så sätt kan du:

* Ge kunderna olika betalningsalternativ, inklusive betalningsknapparna Venmo och PayPal, med möjlighet att stänga av värdkortsfält för PayPal och använda en befintlig kreditkortsleverantör.
* Använd din befintliga kreditkortsleverantör för kreditkortsbetalningar, samtidigt som du använder PayPals andra betalningsalternativ.
* Använd PayPals betalningsknappar i en region där PayPal inte stöder kreditkort som betalningsalternativ.

Till **betalning med _endast_ Betalningsknappar för PayPal (_not_ betalningsalternativet PayPal)**:

1. Se till att din butik [i produktionsläge](settings.md#enable-payment-services).
1. [Konfigurera önskade PayPal-betalningsknappar](settings.md#payment-buttons) i Inställningar.
1. Sväng _Av_ den **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** i _[!UICONTROL Payment buttons]_-avsnitt.

Till **betala med hjälp av din befintliga kreditkortsleverantör _och_ Betalningsknappar för PayPal**:

1. Se till att din butik [i produktionsläge](settings.md#enable-payment-services).
1. [Konfigurera önskade PayPal-betalningsknappar](settings.md#payment-buttons).
1. Sväng _Av_ den **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** i _[!UICONTROL Payment buttons]_-avsnitt.
1. Sväng _Av_ den **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** i _[!UICONTROL Credit card fields]_och använda [befintligt kreditkortskonto](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Orderomberäkning

När en kund går in i kassan från minikorgen, kundvagnen eller produktsidan dirigeras de till en ordergranskningssida där de kan se den valda leveransadressen i ett popup-fönster i PayPal. När kunden har valt leveranssätt beräknas orderbeloppet om på lämpligt sätt och kunden kan se fraktkostnader och skatter.

När en kund går in i utcheckningsflödet från utcheckningssidan är systemet redan medvetet om leveransadressen och det slutliga beräknade beloppet, och summorna representeras korrekt.

Skattehelgdagar, fraktkostnader och moms kan variera mycket mellan olika platser. Efter [!DNL Payment Services] tar emot leveransadressen och fraktkostnaden, beräknar snabbt om alla tillämpliga kostnader och visar dem korrekt under de sista stegen i utcheckningen.

## Kreditkortssäkringar

Köpare kan vault - eller&quot;save&quot; - deras kreditkortsinformation för framtida inköp på webbplatsnivå (vilken butik som helst på samma handlares konto).

Se [Kreditkortssäkringar](vaulting.md) för mer information.

## Säkerhet

Se [PCI-kompatibilitet](security.md#pci-compliance) för mer information.
