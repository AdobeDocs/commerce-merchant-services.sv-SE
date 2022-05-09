---
title: Betalningsalternativ
description: Ange betalningsalternativen för att anpassa de metoder som är tillgängliga för dina butikskunder.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Betalningsalternativ

Med [!DNL Adobe Commerce] och [!DNL Magento Open Source] [!DNL Payment Services]har du flera betalningsalternativ. Du kan konfigurera dessa betalningsalternativ genom att:

* [Startsida](payments-home.md)
* [Butikskonfiguration](configure-admin.md) (rekommenderas för äldre betalningsalternativ eller en inställning för flera butiker)

Det finns olika beteenden för varje betalningsmetod beroende på var du befinner dig i utcheckningsprocessen:

* Produktsida - produktsidan för en artikel
* Mini-cart - Tillgängligt när du klickar på kundvagnen när en produkt har lagts till i varukorgen
* Kundvagn - Tillgänglig när du klickar på _Visa och redigera kundvagn_ från minivagnen
* Utcheckningsvy - tillgänglig när du klickar på _Gå till kassan_ från minivagn eller kundvagn

>[!IMPORTANT]
>
>Inloggningen av betaltjänster måste slutföras innan betalningar kan behandlas.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] tillhandahålla en enkel och säker utcheckning av betalningsmetoder för kreditkort eller betalkort. När en kund checkar ut med kreditkortsfält anger han/hon sitt namn, sin faktureringsadress och kreditkortsinformation för att göra sin beställning. Deras kundinformation används på ett säkert sätt under köpsessionen för att smidigt vägleda dem genom utcheckningsflödet.

Du kan konfigurera [!UICONTROL Credit Card Fields] i butikskonfigurationen eller startsidan för Betalningstjänster. Se [Konfigurerar [!DNL Payment Services]](settings.md#configure-credit-card-fields) för mer information.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], som använder PayPal för att slutföra ett köp, lagrar kundens leveransadress, faktureringsadress och betalningsinformation för senare bruk. Köpare kan använda vilken betalningsmetod som helst som tidigare lagrats eller erbjuds av PayPal.

Du kan konfigurera [!DNL PayPal Smart Buttons] i butikskonfigurationen eller startsidan för Betalningstjänster.  Se [Konfigurerar [!DNL Payment Services]](settings.md#configure-paypal-smart-buttons) för mer information.

### PayPal-knapp

Med PayPal-knappen kan kunderna enkelt och säkert kolla in resultatet.

Knappen PayPal visas på produktsidan, i minikundvagnen, i kundvagnen och i kassan.

### Venmo, knapp

Kunder kan checka ut med [Venmo](https://venmo.com/) -knappen.

Knappen Venmo visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

### [!DNL Pay Later] knapp

Erbjud era kunder kortfristiga räntefria betalningar och andra finansieringsalternativ så att de kan köpa nu och betala senare med [!DNL Pay Later] -knappen.

The [!DNL Pay Later] visas på produktsidan, i varukorgen, i kundvagnen och i kassan.

Det finns två betalningsalternativ med [!DNL Pay Later] knapp:

* **Betala 4**—Kunderna kan betala sitt ordersaldo i fyra räntefria betalningar (varannan vecka) efter en första nedladdningsbetalning. Se [Betala i 4-dokumentation](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) för mer information.
* **PayPal-kredit**—Kunderna kan betala hela ordersaldot under sex månader utan ränta. Se [PayPal-kreditdokumentation](https://www.paypal.com/us/webapps/mpp/paypal-credit) för mer information.

### [!DNL Pay Now] knapp

The [!DNL Pay Now] knappen visas i popup-fönstret PayPal när en kund klickar på en betalningsknapp på betalningsskärmen.

Om det slutgiltiga orderbeloppet ännu inte är känt (t.ex. om du inte har någon leveransadress) och kunden håller på att checka ut från produktsidan, minivagnen eller kundvagnen, är _Fortsätt_ finns i stället. När en kund klickar _Fortsätt_ när de har bekräftat sin betalningsmetod dirigeras de till en ordergranskningssida där de samlar in nödvändiga uppgifter innan de slutför utcheckningen.

## [!DNL Pay Later] meddelanden

För att hjälpa kunden att identifiera dessa som möjliga betalningsalternativ [!DNL Pay Later] meddelanden visas på produktsidan, i minikorgen och i kundvagnen samt under utcheckningen.

* **När en kund väljer en produkt mellan 30 och 600 dollar**, meddelanden under PayPal och [!DNL Pay Later] ger kunden mer information om betalningsalternativet Betala med 4. Kunderna kan klicka **Läs mer** om du vill veta mer om alternativet Betala i 4 _eller_ klicka på texten&quot;Eller se 6 månaders särskild finansiering&quot; i popup-fönstret för att lära dig mer om och ansöka om PayPal-kreditalternativet.
* **När en kund väljer en produkt eller produkter som överstiger 98,99 USD**, meddelanden under PayPal och [!DNL Pay Later] ger kunderna mer information om betalningsalternativet PayPal Credit. Kunderna kan klicka **Läs mer** om du vill veta mer om och ansöka om PayPal-kreditalternativet _eller_ Klicka på texten &quot;Eller se Betala i 4&quot; i popup-fönstret för att lära dig mer om alternativet Betala i 4.

   >[!NOTE]
   >
   >Beloppen ovan kan komma att ändras.

Se [Konfigurera [!DNL Payment Services]](configure-admin.md#configure-paypal-smart-buttons) för att lära dig hur du inaktiverar eller aktiverar [!DNL Pay Later] meddelanden.

## Orderomberäkning

När en kund går in i kassan från minikorgen, kundvagnen eller produktsidan dirigeras de till en ordergranskningssida där de kan se den valda leveransadressen i ett popup-fönster i PayPal. När kunden har valt leveranssätt beräknas orderbeloppet om på lämpligt sätt och kunden kan se fraktkostnader och skatter.

När en kund går in i utcheckningsflödet från utcheckningssidan är systemet redan medvetet om leveransadressen och det slutliga beräknade beloppet, och summorna representeras korrekt.

Skattehelgdagar, fraktkostnader och moms kan variera mycket mellan olika platser. Efter [!DNL Payment Services] tar emot leveransadressen och fraktkostnaden, beräknar snabbt om alla tillämpliga kostnader och visar dem korrekt under de sista stegen i utcheckningen.

## Utcheckning från produktsida

När en kund checkar ut direkt från produktsidan använder du PayPal eller [!DNL Pay Later] är det bara den artikel som finns på den aktuella produktsidan som köpts. Artiklar som redan finns i kundens kundvagn läggs inte till i utcheckningsflödet och köps inte.

Om kunden annullerar beställningen läggs artikeln på den aktuella produktsidan till i kundvagnen och alla andra artiklar i vagnen kopplas. Med den här funktionen kan kunden snabbt köpa det objekt de för närvarande visar, samtidigt som andra artiklar de lagt i kundvagnen tidigare behålls när de bläddrar bland produkterna.

När en kund går in i utcheckningsflödet från produktsidan förenklas utcheckningssidan - vyn visar endast orderrelaterade data och alternativ.

## Säkerhet

Se [PCI-kompatibilitet](security.md#pci-compliance) för mer information.
