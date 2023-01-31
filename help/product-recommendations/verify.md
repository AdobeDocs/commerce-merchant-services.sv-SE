---
title: Verifiera händelsesamling
description: Lär dig hur du kontrollerar att beteendedata skickas till Adobe Commerce.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Verifiera händelsesamling

Efter [installera och konfigurera](install-configure.md) den `magento/product-recommendations` kan du verifiera att beteendedata skickas till Adobe Commerce. Du kan använda utvecklarverktygen i Chrome eller installera tillägget Snöplow Chrome. Om du behöver mer hjälp, se [Felsökning [!DNL Product Recommendations] modul](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) i supportkunskapsbasen.

## Verifiera med utvecklarverktygen i Chrome

Så här ser du till att händelsesamlarens JS-fil läses in på alla webbplatssidor:

1. I Chrome väljer du **Anpassa och styr Google Chrome** välj **Fler verktyg** > **Utvecklarverktyg**.
1. Välj **Nätverk** klickar du på **JS** typ.
1. Filter för `ds.`
1. Läs in sidan igen.
1. Du borde se `ds.js` eller `ds.min.js` i **Namn** kolumn.

![Händelseinsamlings-JS](assets/filter-ds.png)
_Händelseinsamlings-JS_

Så här ser du till att händelser utlöses på sidor på din webbplats (hem, produkt, utcheckning och så vidare):

1. Se till att du inaktiverar alla annonsblockerare i webbläsaren och godkänner cookies på webbplatsen.
1. I Chrome väljer du **Anpassa och styr Google Chrome** (de tre lodräta punkterna i webbläsarens övre högra hörn) och välj sedan **Fler verktyg** > **Utvecklarverktyg**.
1. Välj **Nätverk** tabb och filter för `tp2`.
1. Läs in sidan igen.
1. Du bör se samtal under `tp2` i **Namn** kolumn.

![Starthändelser](assets/filter-tp2.png)
_Verifiera att händelser utlöses_

## Verifiera med Snowplow Chrome-tillägg

Installera [Felsökningstillägg för Snowplow Analytics för Chrome](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Det här tillägget visar de händelser som samlas in och skickas till Adobe Commerce.

1. Se till att du inaktiverar alla annonsblockerare i webbläsaren och godkänner cookies på webbplatsen.

1. I Chrome väljer du **Anpassa och styr Google Chrome** (de tre lodräta punkterna i webbläsarens övre högra hörn) och välj sedan **Fler verktyg** > **Utvecklarverktyg**.

1. Välj **Felsökningsprogram för Snowplow Analytics** -fliken.

1. Under **Händelse** kolumn, markera **Strukturerad händelse**.

1. Bläddra nedåt tills du ser **Kontextdata _n_**. Leta efter storefront-instansen i **Schema**.

1. Verifiera att [SaaS-ID för datautrymme](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) är korrekt inställd.

![filtret Snöpflöde](assets/snowplow-filter.png)
_Snöpfilter_

>[!NOTE]
>
> Värdet för `Data validity : NOT FOUND` i felsökaren anger att det finns ett internt schema. Plugin-programmet Snowplow Chrome kan inte validera händelserna med ett internt schema. Detta påverkar inte den faktiska funktionaliteten.

## Verifiera att händelser utlöses korrekt

Kontrollera att de händelser som används för mätvärden utlöses korrekt genom att leta efter `impression-render`, `view`och `rec-click` händelser i Snowplow Analytics Debugger. Se [fullständig lista över händelser](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> If [Begränsningsläge för cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) är aktiverat samlar Adobe Commerce inte in beteendedata förrän kunden godkänner det. Om läget för cookie-begränsning är inaktiverat samlas beteendedata in som standard.
