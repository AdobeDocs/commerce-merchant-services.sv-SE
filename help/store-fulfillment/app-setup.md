---
title: Appinställningar
description: Konfigurera [!DNL Store Assist] app för att hantera kompletta arbetsflöden och processer för att köpa online, och hämta in butiksbeställningar.
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Appinställningar

Store Assist är en faaS-plattformsapp (fulfillment-as-a-service) som drivs av Walmart Commerce Technologies. Appen har funktioner för att hantera leveranser i butiken [!DNL buy online, pick up in store] (BOPIS) order. Med hjälp av Store Assist kan butikspersonalen se vilka artiklar kunderna beställt, hämta rätt artiklar snabbare och lägga upp färdiga order för kundmottagning i butik eller i butik.

Store Assist-appen får all beställnings- och kundinformation - från beställningsinformation till hämtningstider - och gör data tillgängliga för att lagra partners online, via mobila enheter. Appen innehåller [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]och [!UICONTROL Orders] moduler som hjälper Store Associates att utföra följande aktiviteter:

- Tilldela leveransdatum och leveranstid för order.
- Få meddelanden från kunderna när de kommer för orderhämtning.
- Scenbeställningar för kundleverans.
- Spåra orderstatus för alla order på deras tilldelade butiksplatser.

>[!NOTE]
>
>Läs mer om appen Store Assist genom att läsa [Arbetsflöden för utförande av butiksassistenten](store-assist-modules.md) ämne.

## Konfigurera Store Assist-appen

Store Assist-appen kräver två typer av konfigurationer:

- Systeminställningar för Adobe Commerce Admin till [hantera användarkonton, användarroller, resursbehörigheter](user-setup.md)och [göra bilfabrikat och modellval tillgängliga för kunderna under incheckningsprocessen](check-in-experience-setup.md).

- Anpassa Store Assist-appgränssnittet och andra inställningar:

   - **Varumärk appen Store Assist**- Anpassa appens användargränssnitt med företagets logotyp och färger.

   - **Uppdatera standardinstruktionerna**- Anpassa instruktionerna i arkivassistentmodulerna Pick, Stage, Handoff och Order för att vägleda Store Associates genom varje steg i arbetsflödet.

   - **Lokalisering**—Välj tillgängligt språk för programmet. Välj datum- och tidsformat och välj standardmåttenheter och standardvaluta.

   - **Inaktivitetstid**—Ange hur lång tid programmet måste vara inaktivt innan det loggas ut.

   - **Annullering från butiken**—Ange om beställningar kan avbrytas från butiken och vilka roller som har annulleringsbehörigheter

   - **Orderrensningsfönster**—Ange hur långt efter [Beräknad plockningstid för lead](enable-general.md#delivery-method-title-configuration) att en plockad beställning finns kvar i mellanlagringsutrymmet innan den återställs, till exempel tre dagar. Standardvärdet är sju dagar. Om den här konfigurationen är aktiverad avbryts ordern automatiskt när den här tiden går ut. Objekten återställs och handlaren får ett e-postmeddelande.

   - Anpassa allt i appinstruktioner (plockning, mellanlagring, utleverans).

   - **Plockmeddelanden**- Ange om ett push-meddelande ska skickas för att starta plockningsprocessen efter att en kund har gjort en beställning.

   - **Checka in meddelanden**- Ange om ett push-meddelande ska skickas under incheckningsprocessen för orderplockningar efter incheckning, när kundväntetiden överskrider en angiven tidsperiod. Eller inaktivera meddelanden.

   - **Lämna processen**—Möjliggör valfria processer när Store Associate levererar order till kunden, t.ex. kräver en kundsignatur eller uppmanar denne att kontrollera kund-ID.

   - **Aktivera avvisning av objekt vid överlämning**- Ge kunderna möjlighet att returnera eller annullera orderartiklar under orderleveransen.

  Samarbeta med Walmart Commerce Technologies Client Services-teamet för att slutföra konfigurationen av frontend för Store Assist App.

## Hämta och installera appar

När Store Assist-appen har konfigurerats och konfigurerats kan Store Associates hämta, installera och logga in på Store Assist-appen från sina mobila enheter.

- Verifiera att den mobila enheten uppfyller [maskinvaru- och programvarukrav](solution-requirements.md#store-assist-app-requirements) för lösningen Store Fulfillment.

- Hämta Store Assist-appen från [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- Store Associates kräver följande information för att kunna logga in:

   - **[!UICONTROL Company name]** associerat med Store Assist-kontot

   - **Autentiseringsuppgifter för Store Assist-konto**—användarnamn och lösenord för deras konto.

  En Adobe Commerce-administratör kan skapa och hantera [!DNL Store Assist app] användarkonton för alla butiksplatser som har [Plocka in i butik](merchant-store-configuration.md#pickup-location-configuration) aktiveras i inställningarna för Admin Stores.
