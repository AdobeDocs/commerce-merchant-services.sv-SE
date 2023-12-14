---
title: Introduktion till [!DNL Live Search]
description: "[!DNL Live Search] från Adobe Commerce ger en snabb, relevant och intuitiv sökupplevelse."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 12c9fa011662e2e9fd7bb088db97359dcde87915
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Introduktion till [!DNL Live Search]

[!DNL Live Search] är en tjänst för Adobe Commerce som ersätter standardsökfunktionerna. The [!DNL Live Search] -modulen installeras med Composer och ansluter [!DNL Commerce] installation i [!DNL Live Search] [service](../landing/saas.md). När det är konfigurerat ersätts standardtextfältet för sökning med [!DNL Live Search] textfält. [!DNL Live Search] Installerar också PLP-widgeten (Product Listing Page) som ger robusta filtreringsfunktioner när du bläddrar bland sökresultaten.

[!DNL Live Search] visas på *Marknadsföring* meny under *SEO &amp; Search* i [!DNL Commerce] *Administratör*.

Adobe Commerce-sidan av arkitekturen innehåller värdtjänster för sökningen *Administratör*, synkroniserar katalogdata och kör frågetjänsten. Efter [!DNL Live Search] installeras och konfigureras, Adobe Commerce börjar dela söknings- och katalogdata med SaaS-tjänster. Nu kan administratörsanvändare konfigurera, anpassa och hantera sökningar [facets](facets.md), [synonymer](synonyms.md)och [försäljningsregler](category-merch.md).

## Live Search-komponenter

* [!DNL Live Search] [poppwidget](storefront-popover.md) är den ruta som öppnas under sökfältet som innehåller sökresultaten.
* [Widgeten Produktlistsida](plp-styling.md) innehåller en sökbar produktlistsida med funktioner för ansikten och synonymer.
* AEM CIF: [Widgeten Pekare](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) och [PLP-widget](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) tillåta AEM att dra nytta av [!DNL Live Search].
* [[!DNL Live Search] Administratör](workspace.md) är var regler, facets och synonymer konfigureras.

## Översikt över arbetsflödet

[!DNL Live Search] arbetar genom att flytta katalogdata till Adobe Commerce SaaS-infrastrukturen och bygga index som används för att snabbt leverera sökresultat när användare skriver.

### 1. Installation

[!DNL Live Search] är [installerat](install.md) till Adobe Commerce via [Disposition](https://getcomposer.org/). Detta installerar de moduler som krävs för att ansluta till tjänsten och konfigurerar Commerce-instansen att åsidosätta standardsökfältet. Det installerar även alternativ för Commerce Admin för att konfigurera tjänsten.

### 2. Synkronisera data

[!DNL Live Search] flyttar katalogdata till infrastrukturen i Adobe SaaS. Data indexeras och sökresultat levereras från detta index direkt till butiken. Beroende på storlek och komplexitet kan indexeringen ta mellan 30 minuter och några timmar.

### 3. Konfigurera data

Om du konfigurerar dina produktdata på rätt sätt får du bra sökresultat för dina kunder. Det finns några konfigurationssteg som krävs: tilldela kategorier och konfigurera attribut.

#### Tilldela kategorier

Produkten returnerades i [!DNL Live Search] måste tilldelas en [kategori](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). I Luma kan till exempel produkter delas in i kategorier som &quot;Män&quot;, &quot;Kvinnor&quot; och &quot;Kugghjul&quot;. Underkategorierna är också inställda för &quot;Tops&quot;, &quot;Bottom&quot; och &quot;Watches&quot;. Detta ger bättre granularitet vid filtrering.

#### Sökbara och filterbara fält

Produkter tilldelas [attributes](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) som kan användas för sökning och filtrering. Attribut är t.ex. &quot;Color&quot;, &quot;Size&quot; och &quot;Material Type&quot;. Med de här attributen kan användarna leta efter&quot;gröna toppar&quot;. Varje produkt kan ha många attribut definierade i Commerce Admin.

Var och en av dessa attribut kan definieras som [&quot;sökbar&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) i administratören. Om attributen anges som &quot;sökbara&quot; är de tillgängliga för sökning av [!DNL Live Search].

[Fasetter](facets.md) är produktattribut som definieras i [!DNL Live Search] som ska kunna filtreras. Alla filterbara attribut kan anges som en faktor i [!DNL Live Search] men det finns gränser för hur många aspekter som kan sökas igenom samtidigt.

[Synonymer](synonyms.md) är termer som du kan definiera för att hjälpa användarna att hitta rätt produkt. Användare som söker efter byxor kan skriva in &quot;byxor&quot; eller &quot;slacks&quot;. Du kan ställa in synonymer så att de här söktermerna får användarna att se resultatet.

## [!DNL Live Search] arbetsyta

The [!DNL Live Search] [arbetsyta](workspace.md) är området i administratören där du konfigurerar [!DNL Live Search] funktioner som synonymer, facets och Category Merchandising.

## Händelser

[!DNL Live Search] använder [händelser](events.md) att beräkna [Intelligent marknadsföring](category-merch.md) och [prestanda](performance.md) instrumentpaneler. Händelser tillhandahålls med standardimplementeringar. Händelser för headless-butiker ska aktiveras manuellt.

## Anpassa widgetar

De flesta butiksägarna vill se till att [!DNL Live Search] widgetar anpassar sig efter butikens utseende och känsla.

Widgetarna pover och PLP kan formateras genom att definiera anpassade CSS-regler efter behov. Se [Formatera popoposerelement](storefront-popover-styling.md) och [Sidwidget för produktlista](plp-styling.md).

Om du vill utöka widgetarnas funktioner är källkoden för varje tillgängligt i en offentlig rapport.
I det här scenariot kan du anpassa JavaScript efter dina egna behov och sedan lägga din egen kod på ditt CDN. Det här anpassade skriptet kommunicerar med [!DNL Live Search] och returnerar resultatet som vanligt, så att du kan styra widgetens funktioner.

* [PLP-widget - repo](https://github.com/adobe/storefront-product-listing-page)
* [Repo av sökfältet](https://github.com/adobe/storefront-search-as-you-type)

Läs mer om [!DNL Live Search] i [Teknisk översikt](technical-overview.md).

## [!DNL Live Search] demo

I den här videon får du veta mer om [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

En mer ingående video om hur du använder och konfigurerar Live Search finns i [Fullständig demonstration på [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) ämne.
