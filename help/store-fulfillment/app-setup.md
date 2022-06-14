---
title: Appinställningar
description: '"Konfigurera [!DNL Store Assist] app för att hantera kompletta arbetsflöden och processer för att köpa online, och hämta in butiksbeställningar." '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Appinställningar

Store Assist är en faaS-plattformsapp (fulfillment-as-a-service) som drivs av Walmart Commerce Technologies. Appen har funktioner för att hantera leveranser i butiken [!DNL buy online], [!DNL pick up in store] (BOPIS) order.

Appen får all beställnings- och kundinformation - från beställningsinformation till hämtningstider - och gör informationen tillgänglig för att lagra partners online, via mobila enheter. Med hjälp av Store Assist kan butikspersonalen se vilka artiklar kunderna beställt, hämta rätt artiklar snabbare och lägga upp färdiga order för kundmottagning i butik eller i butik.

Store Associates använder Store Assist [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]och [!UICONTROL Orders] för att hantera leverans och leverans:

- Tilldela leveransdatum och leveranstid för order
- Få meddelanden från kunderna när de kommer till butiken för orderhämtning
- Scenorder som skickas till kunder
- Spåra orderstatus för alla order på deras tilldelade butiksplatser

Se [Arbetsflöden för utförande av butiksassistenten](store-assist-modules.md) om du vill veta mer om Store Assist-appen.


## Konfigurera Store Assist-appen

Store Assist-appen kräver två typer av konfigurationer:

- Konfigurationsinställningar för Adobe Commerce Admin till [Hantera användarkonton, användarroller och resursbehörigheter från systeminställningarna för Adobe Commerce Admin](user-setup.md).

- Anpassa Store Assist-appgränssnittet och andra inställningar:

   - **Varumärk appen Store Assist**- Anpassa appens användargränssnitt med företagets logotyp och färger

   - **Uppdatera standardinstruktionerna**- Anpassa de instruktioner som visas i Store Assist-gränssnitten för modulerna Pick, Stage, Handoff och Order så att dina kollegor vet exakt vad de ska göra under varje steg i processen.

   - **Lokalisering**—Välj tillgängligt språk för appen, välj datum- och tidsformat, välj standardmåttenheter och välj standardvaluta

   - **Inaktivitetstid**—Ange hur länge appen måste vara inaktiv innan den loggar ut

   - **Annullering från butiken**—Ange om beställningar kan avbrytas från butiken och vilka roller som har annulleringsbehörigheter

   - **Orderrensningsfönster**—Ange hur långt efter den schemalagda upphämtningstiden som en plockad order stannar i mellanlagringen innan den återställs, till exempel tre dagar.

   - Anpassa allt i appinstruktioner (plockning, mellanlagring, utleverans)

   - **Plockmeddelanden**-Konfigurera om du vill att push-meddelanden ska starta plockningen när en order har lagts

   - **Checka in meddelanden**-Konfigurera om du vill ha push-meddelanden när en kund har checkat in/väntar på X min/eller inga meddelanden alls

   - **Lämna processen**—Aktivera kundens underskrift, aktivera en uppmaning om att kontrollera kund-ID innan ordern skickas

   - **Aktivera avvisning av objekt vid överlämning**

   Arbeta med Walmart Commerce Technologies Client Services-teamet för att slutföra konfigurationen av klientservern för Store Assist App.

## Hämta och installera appar

När konfigurationen av Store Assist-appen har slutförts kan Store Associates hämta och installera Store Assist-appen på sina mobila enheter och logga in.

- Hämta Store Assist-appen från [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) eller Google Play Store.

- Store Associates kräver följande information för att kunna logga in:

   - Det företagsnamn som är associerat med ditt Store Assist-konto

   - Butiksassistentkontots autentiseringsuppgifter - användarnamn och lösenord för deras konto.
   En Adobe Commerce-administratör kan skapa Store Assist-appanvändarkonton för butiksplatser som har [Plocka in i butik](merchant-store-configuration.md#pickup-location-configuration) aktiveras i inställningarna för Admin Stores.

