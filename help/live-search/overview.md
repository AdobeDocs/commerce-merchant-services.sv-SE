---
title: Introduktion till [!DNL Live Search]
description: "[!DNL Live Search] från Adobe Commerce ger en blixtsnabb, superrelevant och intuitiv sökupplevelse."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: c77b2f9cb55d3eb339dcc900ce606b94c592f559
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Introduktion till [!DNL Live Search]

[!DNL Live Search] är en tjänst för Adobe Commerce som ersätter standardsökfunktionerna. The [!DNL Live Search] -modulen installeras med Composer och ansluter [!DNL Commerce] installation i [!DNL Live Search] [service](../landing/saas.md). När det är konfigurerat ersätts standardtextfältet för sökning med [!DNL Live Search] textfält. [!DNL Live Search] Installerar också PLP-widgeten (Product Listing Page) som ger robusta filtreringsfunktioner när du bläddrar bland sökresultaten.

[!DNL Live Search] visas på *Marknadsföring* meny under *SEO &amp; Search* i [!DNL Commerce] *Administratör*.

Adobe Commerce-sidan av arkitekturen innehåller värdtjänster för sökningen *Administratör*, synkroniserar katalogdata och kör frågetjänsten. Efter [!DNL Live Search] installeras och konfigureras, Adobe Commerce börjar dela söknings- och katalogdata med SaaS-tjänster. Nu kan administratörsanvändare konfigurera, anpassa och hantera sökningar [facets](facets.md), [synonymer](synonyms.md)och [försäljningsregler](category-merch.md).

![Arkitektur för Live Search](assets/architecture-diagram.svg)

## Live Search-komponenter

* [!DNL Live Search] [poppor](storefront-popover.md) är den ruta som öppnas under sökfältet som innehåller sökresultaten.
* [Widgeten Produktlistsida](plp-styling.md) innehåller en sökbar produktlistsida med funktioner för ansikten och synonymer.
* AEM CIF: [Widgeten Pekare](https://github.com/adobe/aem-cif-guides-venia/pull/319) och [PLP-widget](https://github.com/adobe/aem-cif-guides-venia/pull/320) tillåta AEM att dra nytta av [!DNL Live Search].
* [[!DNL Live Search] Administratör](workspace.md) är var regler, facets och synonymer konfigureras.
* Sökadaptern är standardimplementeringen av [!DNL Live Search]. Rekommenderas för headlessimplementeringar och anpassade implementeringar.

## [!DNL Live Search] demo

I den här videon får du veta mer om [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

En mer ingående video om hur du använder och konfigurerar Live Search finns i [Fullständig demonstration på [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) ämne.
