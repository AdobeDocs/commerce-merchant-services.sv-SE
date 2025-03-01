---
title: Utveckling av Recommendations Administrator
description: Översikt över arkitekturen och utvecklingsfunktionerna i Recommendations.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: 4a5c3550b03651279c24de6b6361ffa6dc28776e
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Utveckling av Recommendations Administrator

Produkt-Recommendations är ett kraftfullt marknadsföringsverktyg som ni kan använda för att öka konverteringarna, öka intäkterna och stimulera kundernas engagemang. Produkt-Recommendations finns i butiken i form av enheter som&quot;Kunder som tittade på den här produkten också&quot;,&quot;Kunder som köpte den här produkten också&quot;,&quot;Rekommenderas för dig&quot; och så vidare. Adobe Commerce Product Recommendations drivs av [Adobe Sensei](https://www.adobe.com/sensei.html) som använder artificiell intelligens och algoritmer för maskininlärning för att göra en djupgående analys av samlade kunddata. Dessa data kombineras med er Commerce-katalog och ger en engagerande, relevant och personaliserad upplevelse för kunderna.

>[!NOTE]
>
>Om din storefront implementeras med PWA Studio finns mer information i [dokumentationen för PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Om du använder en anpassad klientteknik som React eller Vue JS kan du läsa användarhandboken för att lära dig hur du integrerar Product Recommendations i en [headless](headless.md) -miljö. Headless-instanser måste implementera händelser för att fungera bättre i produktrekommendationsarbetsytan.

## Arkitektur - översikt

På en hög nivå driftsätts Commerce Product Recommendations som SaaS. På Commerce-sidan finns storefront, som innehåller händelseinsamlaren och rekommendationslayoutmallen, samt serverdelen, som innehåller datatjänster, SaaS-exportmodulen och administratörsgränssnittet. Adobe Sensei underrättelsetjänster utnyttjas av SaaS.

![Arkitektur för produktrekommendationer](assets/arch-diag-sensei.svg)

När rekommendationsmodulerna har installerats och konfigurerats börjar butiken samla in beteendedata. Adobe Sensei behandlar dessa beteendedata tillsammans med katalogdata och beräknar produktassociationer som används av rekommendationstjänsten. Nu kan handlaren skapa, hantera och driftsätta produktrekommendationsenheter i butiken direkt från administratörsgränssnittet.

## Nästa steg

Läs följande avsnitt för att komma igång med Product Recommendations:

- [Så här implementerar du Recommendations](implementation-workflow.md)

- [Installera och konfigurera Recommendations](install-configure.md)

- [Skapa Recommendations](create.md)
