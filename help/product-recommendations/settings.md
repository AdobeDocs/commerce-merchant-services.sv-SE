---
title: Inställningar
description: Lär dig hur du ändrar källan för dina [!DNL Product Recommendations] data och hur du aktiverar visuella rekommendationer.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Inställningar

När du [konfigurera ett SaaS-dataområde](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) för Recommendations samlar SaaS-datautrymmet in katalogdata och butiksbeteendedata. [Adobe Sensei](https://www.adobe.com/sensei.html) analyserar data och beräknar produktassociationer som används för att betjäna Product Recommendations.

Icke-produktionsmiljöer för testning eller testning har vanligtvis inte den kvantitet eller kvalitet av butiksbeteendedata som behövs för att ta fram realistiska produktrekommendationer. Faktiskt shoppingbeteende i stor skala kan endast fångas i en produktionsmiljö. För att lösa detta problem kan du med Adobe Commerce använda produktrekommendationer från din produktionsmiljö tillsammans med andra SaaS-datamallar som inte är i produktion. Om du använder faktiska butiksdata i en icke-produktionsmiljö kan du förhandsgranska de rekommendationer kunderna ser och experimentera med olika rekommendationstyper och placeringsplatser. Recommendations från en annan SaaS-datautrymm kan förhandsgranskas av kunderna, men inte klickas.

## Välj rekommendationskälla

Om du vill ändra källan till dina produktrekommendationer väljer du SaaS-dataområdet med de beteendedata som du vill använda. Innan du börjar bör du kontrollera att:

- Datainsamling för Storefront måste [konfigurerad och aktiverad](install-configure.md) för produktionsmiljön och [verifierad](verify.md) att beteendedata skickas till Adobe Commerce.
- Katalogen för icke-produktionsmiljö bör i princip vara densamma som din produktionskatalog. Genom att använda liknande kataloger ser du till att produktrekommendationsenheterna returnerar mycket liknande produktrekommendationsenheter.

1. Logga in på Admin i din icke-produktionsmiljö i Adobe Commerce.

1. På _Administratör_ sidebar, gå till **Marknadsföring** > _Erbjudanden_ > **Recommendations**.

1. Klicka **Inställningar**.

   ![produktrekommendationsinställningar](assets/settings.png)
   _Inställningar_

1. I _Recommendations-källa_ -sektion, aktivera **Hämta rekommendationer från en annan SaaS-datamängd** alternativ. The _Recommendations-källa_ -avsnittet visas bara i en icke-produktionsmiljö.

   En lista med _Tillgängliga SaaS-datautrymmen_ visas.

   ![produktrekommendationsinställningar](assets/settings-select-saas.png)
   _Inställningar_

1. Välj den SaaS-dataminne som innehåller kunddata som du vill använda.

1. Klicka **Spara ändringar**.

   Adobe Commerce hämtar nu rekommendationer från den valda datamängden.

   >[!NOTE]
   >
   > Du kan visa rekommendationer som hämtats från ett annat SaaS-datautrymme i butiken som inte är i produktion, men du kan inte klicka på rekommendationerna.

### Konfigurera ett nytt SaaS-datautrymme

1. I källavsnittet för Recommendations klickar du på **Redigera konfiguration**.

1. Följ instruktionerna för att konfigurera en ny [[!DNL Commerce] service](/help/landing/saas.md).

## Aktivera visuella rekommendationer

Om [Visual Product Recommendations](install-configure.md) är installerat måste du aktivera Visual Recommendations för att kunna använda [Visuell likhet](type.md#visualsim) rekommendationstyp.

I _Visual Recommendations_ avsnitt, ange **Aktivera Visual Recommendations** till den aktiva positionen.
