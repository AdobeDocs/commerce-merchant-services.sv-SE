---
title: Betalningsalternativ
description: Ange betalningsalternativen för att anpassa de metoder som är tillgängliga för dina butikskunder.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 36dd961d06f279143e90f3a1f5a6114db14e8c1b
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---

# Betalningsalternativ

Med [!DNL Adobe Commerce] och [!DNL Magento Open Source] [!DNL Payment Services]har du flera betalningsalternativ. Du kan konfigurera dessa betalningsalternativ genom att:

* [Heminställningar](payments-home.md)
* [Butikskonfiguration](configure-admin.md) (rekommenderas för äldre betalningsalternativ eller en inställning för flera butiker)

Det finns olika beteenden för varje betalningsmetod beroende på var du befinner dig i utcheckningsprocessen:

* Produktsida - produktsidan för en artikel
* Mini cart - Tillgängligt när du klickar på varukorgen när en produkt har lagts till i varukorgen
* Kundvagn - Tillgänglig när du klickar på _Visa och redigera kundvagn_ från minivagnen
* Utcheckningsvy - tillgänglig när du klickar på _Gå till kassan_ från minivagn eller kundvagn

>[!IMPORTANT]
>
>Inloggningen av betaltjänster måste slutföras innan betalningar kan behandlas.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] tillhandahålla en enkel och säker utcheckning av betalningsmetoder för kreditkort eller betalkort. När en kund checkar ut med kreditkortsfält anger han/hon sitt namn, sin faktureringsadress och kreditkortsinformation för att göra sin beställning. Deras kundinformation används på ett säkert sätt under köpsessionen för att smidigt vägleda dem genom utcheckningsflödet.

Aktivera [kreditkortsvalv](#vaulting) för butikerna så att kunderna kan vault (save) sina kreditkortsuppgifter för en snabb utcheckning senare.

Du kan konfigurera [!UICONTROL Credit Card Fields] i butikskonfigurationen eller startsidan för Betalningstjänster. Se [Inställningar](settings.md#credit-card-fields) för mer information.

Du kan också ändra layout, bredd, höjd och yttre format för kreditkortsfälten. Se [PayPal-dokumentation](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) för mer information.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], som använder PayPal för att slutföra ett köp, lagrar kundens leveransadress, faktureringsadress och betalningsinformation för senare bruk. Köpare kan använda vilken betalningsmetod som helst som tidigare lagrats eller erbjuds av PayPal.

![[!DNL PayPal Smart Buttons] alternativ](assets/payment-buttons.png){width="500"}

Du kan konfigurera [!UICONTROL PayPal Smart Buttons] i butikskonfigurationen eller startsidan för Betalningstjänster.  Se [Inställningar](settings.md#payment-buttons) för mer information.

### [!DNL PayPal] knapp

Med PayPal-knappen kan kunderna enkelt och säkert kolla in resultatet.

The [!DNL PayPal] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

### [!DNL Venmo] knapp

Kunder kan checka ut med [Venmo](https://venmo.com/) -knappen.

The [!DNL Venmo] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

### [!DNL Apple Pay] knapp

Kunder kan använda Touch ID på sina enheter för att använda [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), som använder kreditkortets och betalkortets autentiseringsuppgifter som lagras på en iOS- eller macOS-enhet.

The [!DNL Apple Pay] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

>[!NOTE]
>
> Används [!DNL Apple Pay] för butikerna, fullständigt [självregistrering med [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Registrera din aktiva domän_ endast ) och [konfigurera den för dina butiker i [!DNL Payment Services]](settings.md#payment-buttons).

### PayPal Debit eller kreditkortsknapp

Kunder kan checka ut med PayPal Debit- eller kreditkortsknappen.

Knappen PayPal Debit eller Kreditkort visas på utcheckningssidan.

Det här alternativet kan användas för att presentera ett betalningsalternativ för PayPal Debit eller kreditkort för dina kunder när du inte har någon alternativ kreditkortsleverantör.

### [!DNL Pay Later] knapp

Erbjud era kunder kortfristiga räntefria betalningar och andra finansieringsalternativ så att de kan köpa nu och betala senare med [!DNL Pay Later] -knappen.

The [!DNL Pay Later] visas på produktsidan, i varukorgen, i kundvagnen och i kassan:

* **När en kund väljer en produkt mellan 30 och 600 dollar**, meddelanden under PayPal och [!DNL Pay Later] ger kunden mer information om [!DNL Pay in 4] betalningsalternativ. Kunderna kan klicka **Läs mer** om du vill veta mer om[!DNL Pay in 4]&quot;, alternativ _eller_ klicka på texten&quot;Eller se 6 månaders särskild finansiering&quot; i popup-fönstret för att lära dig mer om och ansöka om PayPal-kreditalternativet.
* **När en kund väljer en produkt eller produkter som överstiger 98,99 USD**, meddelanden under PayPal och [!DNL Pay Later] ger kunderna mer information om betalningsalternativet PayPal Credit. Kunderna kan klicka **Läs mer** om du vill veta mer om och ansöka om PayPal-kreditalternativet, _eller_ klicka på texten &quot;eller se Betala i 4&quot; i popup-fönstret för att lära dig mer om [!DNL Pay in 4] alternativ.

  >[!NOTE]
  >
  >Beloppen ovan kan komma att ändras.

Se [Inställningar](settings.md#payment-buttons) för att lära dig hur du inaktiverar/aktiverar [!DNL Pay Later] meddelanden.

Det finns två betalningsalternativ med [!DNL Pay Later] knapp:

* **Betala 4**—Kunderna kan betala sitt ordersaldo i fyra räntefria betalningar (varannan vecka) efter en första nedladdningsbetalning. Se [Betala i 4-dokumentation](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) för mer information.
* **PayPal-kredit**—Kunderna kan betala hela ordersaldot under sex månader utan ränta. Se [PayPal-kreditdokumentation](https://www.paypal.com/us/webapps/mpp/paypal-credit) för mer information.

### [!DNL Pay Now] knapp

The [!DNL Pay Now] knappen visas i popup-fönstret PayPal när en kund klickar på en betalningsknapp på betalningsskärmen.

Om det slutgiltiga orderbeloppet ännu inte är känt (t.ex. om du inte har någon leveransadress) och kunden håller på att checka ut från produktsidan, minivagnen eller kundvagnen, är _Fortsätt_ finns i stället. När en kund klickar _Fortsätt_ när de har bekräftat sin betalningsmetod dirigeras de till en ordergranskningssida där de samlar in nödvändiga uppgifter innan de slutför utcheckningen.

## Använd endast PayPal-betalningsknappar

För att snabbt få butiken i produktionsläge kan du konfigurera _endast_ Betalningsknappar för PayPal (Venmo, PayPal osv.)- i stället för att också använda betalningsalternativet PayPal-kreditkort.

På så sätt kan du:

* Ge kunderna olika betalningsalternativ, inklusive betalningsknapparna Venmo och PayPal, med möjlighet att stänga av värdkortsfält för PayPal och använda en befintlig kreditkortsleverantör.
* Använd din befintliga kreditkortsleverantör för kreditkortsbetalningar, samtidigt som du använder PayPals andra betalningsalternativ.
* Använd PayPals betalningsknappar i en region där PayPal inte stöder kreditkort som betalningsalternativ.

Till **betalning med _endast_ Betalningsknappar för PayPal (_not_ kreditkortsbetalningsalternativet PayPal)**:

1. Se till att din butik [i produktionsläge](settings.md#enable-payment-services).
1. [Konfigurera önskade PayPal-betalningsknappar](settings.md#payment-buttons) i Inställningar.
1. Sväng _Av_ den **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** i _[!UICONTROL Payment buttons]_-avsnitt.

Till **betala med hjälp av din befintliga kreditkortsleverantör _och_ Betalningsknappar för PayPal**:

1. Se till att din butik [i produktionsläge](settings.md#enable-payment-services).
1. [Konfigurera önskade PayPal-betalningsknappar](settings.md#payment-buttons).
1. Sväng _Av_ den **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** i _[!UICONTROL Payment buttons]_-avsnitt.
1. Sväng _Av_ den **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** i _[!UICONTROL Credit card fields]_och använda [befintligt kreditkortsleverantörskonto](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Orderomberäkning

När en kund går in i kassan från minikorgen, kundvagnen eller produktsidan dirigeras de till en ordergranskningssida där de kan se den valda leveransadressen i ett popup-fönster i PayPal. När kunden har valt leveranssätt beräknas orderbeloppet om på lämpligt sätt och kunden kan se fraktkostnader och skatter.

När en kund går in i utcheckningsflödet från utcheckningssidan är systemet redan medvetet om leveransadressen och det slutliga beräknade beloppet, och summorna representeras korrekt.

Skattehelgdagar, fraktkostnader och moms kan variera mycket mellan olika platser. Efter [!DNL Payment Services] tar emot leveransadressen och fraktkostnaden, beräknar snabbt om alla tillämpliga kostnader och visar dem korrekt under de sista stegen i utcheckningen.

## Kreditkortssäkringar

Köpare kan vault - eller&quot;save&quot; - deras kreditkortsinformation för framtida inköp på webbplatsnivå (vilken butik som helst på samma handlares konto).

Se [Kreditkortssäkringar](vaulting.md) för mer information.

## Säkerhet

Se [PCI-kompatibilitet](security.md#pci-compliance) för mer information.
