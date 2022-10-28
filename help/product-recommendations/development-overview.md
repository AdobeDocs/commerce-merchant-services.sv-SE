---
title: Utveckling av Recommendations Administrator
description: Översikt över arkitekturen och utvecklingsfunktionerna i Recommendations.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Utveckling av Recommendations Administrator

Produkt-Recommendations är ett kraftfullt marknadsföringsverktyg som ni kan använda för att öka konverteringarna, öka intäkterna och stimulera kundernas engagemang. Produkt-Recommendations finns i butiken i form av enheter som&quot;Kunder som tittade på den här produkten också&quot;,&quot;Kunder som köpte den här produkten också&quot;,&quot;Rekommenderas för dig&quot; och så vidare. Adobe Commerce Product Recommendations drivs av [Adobe Sensei](https://www.adobe.com/sensei.html), som använder artificiell intelligens och maskininlärningsalgoritmer för att utföra en djupgående analys av samlade kunddata. När dessa data kombineras med er Commerce-katalog resulterar de i engagerande, relevanta och personaliserade upplevelser för kunderna.

>[!NOTE]
>
>Om din storefront implementeras med PWA Studio finns mer information i [PWA dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Om du använder en anpassad klientteknik som React eller Vue JS kan du läsa användarhandboken för att lära dig hur du integrerar Product Recommendations i en [headless](headless.md) miljö.

## Arkitektur - översikt

På en hög nivå distribueras Commerce Product Recommendations som SaaS. Handelssidan innehåller storefront, som innehåller händelseinsamlaren och rekommendationslayoutmallen, samt backend-modulen, som innehåller datatjänster, SaaS-exportmodulen och administratörsgränssnittet. Adobe Sensei underrättelsetjänster utnyttjas av SaaS.

![Arkitektur för produktrekommendationer](assets/arch-diag-sensei.svg)

När rekommendationsmodulerna har installerats och konfigurerats börjar butiken samla in beteendedata. Adobe Sensei behandlar dessa beteendedata tillsammans med katalogdata och beräknar produktassociationer som används av rekommendationstjänsten. Nu kan handlaren skapa, hantera och driftsätta produktrekommendationsenheter i butiken direkt från administratörsgränssnittet.

## Typer av data

Produkt-Recommendations kräver följande data:

- **Beteende** - Data från en kunds engagemang på er webbplats, t.ex. produktvisningar, artiklar som lagts till i en kundvagn samt inköp. Handel och Adobe Sensei samlar inte in personligt identifierbar information.

- **Katalog** - Produktmetadata som namn, pris, tillgänglighet och så vidare.

När du installerar `magento/product-recommendations` Adobe Sensei samlar in beteendedata och katalogdata och skapar Product Recommendations för varje rekommendationstyp. Recommendations produkttjänst distribuerar sedan dessa rekommendationer till din butik.

## Nästa steg

Läs följande avsnitt för att komma igång med Product Recommendations:

- [Implementera Recommendations](implementation-workflow.md)

- [Installera och konfigurera Recommendations](install-configure.md)

- [Skapa produkt-Recommendations](create.md)
