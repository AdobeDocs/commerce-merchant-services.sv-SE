---
title: Användarinställningar
description: 'Konfigurera förbättrade Inventory management-källor som butiker. '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Användarinställningar

Store Assist-appanvändare hanteras i Adobe Commerce. Dessa användare interagerar dock inte direkt med Adobe Commerce. Användarhanteringen är konfigurerad i Adobe Commerce för att möjliggöra säkra anslutningar mellan Adobe Commerce och appen.

Store Fulfillment App User model är skild från andra Adobe Commerce-användarmodeller. Appen behåller sin egen behörighetsmodell via användarroller och användare som kan tilldelas till alla eller specifika platser. Följande behörigheter stöds: Plockningsordning, Dispensationsordning och Minskning av artikelkvantitet (och annullering).

>[!TIP]
>
>För bästa resultat [konfigurera anslutningen](connect-set-up-service.md) innan du lägger till användare och behörigheter för Store Associates som använder Store Assist-appen.

## Store Assist App - Användarroller

Under den första användarkonfigurationen för Store Assist-appen skapar du användarroller för att anpassa användarbehörigheter till Store Assist-appen. Du kan t.ex. skapa olika roller för butikshanterare och butikskolledare och tilldela olika rollresurser för att hantera behörigheter för varje typ av användare.

Konfigurera användarroller från **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Rollinformation

| **Fält** | **Beskrivning** | **Omfång** | **Obligatoriskt** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Aktivera eller inaktivera användare. | Global | Ja |

### Rollresurser

| **Fält** | **Beskrivning** | **Omfång** | **Obligatoriskt** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Visa en lista över tillgängliga behörighetsgrupper som kan tilldelas till en användarroll. För närvarande har inte lagringslösningen för arkivering olika behörighetsnivåer definierade för resursroller. Alla användarroller har samma resursåtkomst. | Global | Ja |

## Store Assist - användarinformation

Hantera användarprofiler för Store Assist-appen från inställningarna för Admin System:  **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.


| **Fält** | **Beskrivning** | **Omfång** | **Obligatoriskt** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Aktivera eller inaktivera användare. | Global | Ja |
| **[!UICONTROL User Name]** | Användarnamn associerat med användare | Global | Ja |
| **[!UICONTROL First Name]** | Förnamn associerat med användare | Global | Nej |
| **[!UICONTROL Last Name]** | Efternamn associerat med användare | Global | Nej |
| **[!UICONTROL Role]** | Roll som är associerad med användaren | Global | Nej |
| **[!UICONTROL Access to all locations]** | Tilldela användare åtkomst till alla butiker, eller välj butiker individuellt. | Global | Nej |
| **Språk för gränssnitt** | Om din butik har flera språk anger du Språk för Gränssnitt till det språk som ska användas för Admin-gränssnittet. | Global | Nej |
| **Aktiv från** | Om du vill ange ett startdatum väljer du kalenderikonen. | Global | Nej |
| **Aktiv till** | Ange förfallodatum genom att markera kalenderikonen. Det är praktiskt att ange ett förfallodatum när du vill ställa in tillfälliga användar- eller rolltilldelningar. Efter förfallodatumet ändras användarkontots status till `Inactive`men kontot kan fortfarande uppdateras om det behövs. | Global | Nej |





