---
title: Inställningar
description: Lär dig hur du ändrar källan för dina [!DNL Product Recommendations] -data och hur du aktiverar visuella rekommendationer.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 3a5dec9422aa34eeb204b9fe6f089551e4038f1c
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Inställningar

När du [konfigurerar ett SaaS-datautrymme](../landing/saas.md#saas-configuration) för Recommendations, samlar SaaS-datautrymmet in katalogdata och butiksbeteendedata. [Adobe Sensei](https://www.adobe.com/sensei.html) analyserar data och beräknar produktassociationer som används för att betjäna Recommendations.

Icke-produktionsmiljöer för testning eller testning har vanligtvis inte den kvantitet eller kvalitet av butiksbeteendedata som behövs för realistiska produktrekommendationer. Faktiskt shoppingbeteende i stor skala kan endast fångas i en produktionsmiljö. För att lösa detta problem kan du med Adobe Commerce använda produktrekommendationer från din produktionsmiljö tillsammans med andra SaaS-datamallar som inte är i produktion. Om du använder faktiska butiksdata i en icke-produktionsmiljö kan du förhandsgranska de rekommendationer kunderna ser och experimentera med olika rekommendationstyper och placeringsplatser. Recommendations från en annan SaaS-datautrymm kan förhandsgranskas av kunderna, men inte klickas.

Mellanlagringsorder spelas in med mellanlagring `environmentId`. Det påverkar inte produktionsdata. Produktionsdata hämtas med `alternateEnvironmentId`.

>[!NOTE]
>
>När du använder Product Recommendations via REST kan parametern `alternateEnvironmentId` användas för att ange andra dataspaces. När du använder Product Recommendations via GraphQL är den här parametern inte tillgänglig.

## Välj rekommendationskälla

Om du vill ändra källan till dina produktrekommendationer väljer du SaaS-dataområdet med de beteendedata som du vill använda. Innan du börjar bör du kontrollera att:

- Datainsamlingen i Storefront måste vara [konfigurerad och aktiverad](install-configure.md) för din produktionsmiljö och [verifierad](verify.md) att beteendedata skickas till Adobe Commerce.
- Katalogen för icke-produktionsmiljö bör i princip vara densamma som din produktionskatalog. Genom att använda liknande kataloger ser du till att produktrekommendationsenheterna returnerar mycket liknande produktrekommendationsenheter.

1. Logga in på Admin i din icke-produktionsmiljö i Adobe Commerce.

1. Gå till **Marknadsföring** > _Kampanjer_ > **Produkt-Recommendations** på sidofältet _Admin_.

1. Klicka på **Inställningar**.

   ![inställningar för produktrekommendation](assets/settings.png)
   _Inställningar_

1. Aktivera alternativet **Hämta rekommendationer från ett annat SaaS-datautrymme** i avsnittet _Recommendations-källa_. Avsnittet _Recommendations-källa_ visas bara i en icke-produktionsmiljö.

   En lista över _tillgängliga SaaS-datautrymmen_ visas.

   ![inställningar för produktrekommendation](assets/settings-select-saas.png)
   _Inställningar_

1. Välj den SaaS-dataminne som innehåller kunddata som du vill använda.

1. Klicka på **Spara ändringar**.

   Adobe Commerce hämtar nu rekommendationer från den valda datamängden.

   >[!NOTE]
   >
   > Du kan visa rekommendationer som hämtats från ett annat SaaS-datautrymme i butiken som inte är i produktion, men du kan inte klicka på rekommendationerna.

### Konfigurera ett nytt SaaS-datautrymme

1. Klicka på **Redigera konfiguration** i källavsnittet för Recommendations.

1. Följ instruktionerna för att konfigurera en ny [[!DNL Commerce] tjänst](/help/landing/saas.md).

## Aktivera visuella rekommendationer

Om modulen [Visual Product Recommendations](install-configure.md) är installerad måste du aktivera Visual Recommendations för att kunna använda rekommendationstypen [Visual Likity](type.md#visualsim) .

I avsnittet _Visual Recommendations_ anger du **Aktivera Visual Recommendations** till den aktiva positionen.
