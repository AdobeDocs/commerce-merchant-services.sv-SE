---
title: Samla in data
description: Läs om hur händelser samlar in data för produktrekommendationer.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 7ed9321a2f4e58a7476aa91e74611fe896e1a7b1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Samla in data

När du installerar och konfigurerar SaaS-baserade Adobe Commerce-funktioner som [Recommendations](install-configure.md) eller [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)distribuerar modulerna beteendedatainsamling till butiken. Den här mekanismen samlar in anonyma beteendedata från era kunder och ligger till grund för produktrekommendationer. Till exempel `view` -händelsen används för att beräkna `Viewed this, viewed that` rekommendationstyp och `place-order` -händelsen används för att beräkna `Bought this, bought that` rekommendationstyp.

>[!NOTE]
>
>Datainsamling för produktrekommendationer omfattar inte personligt identifierbar information. Alla användaridentifierare, som cookie-ID:n och IP-adresser, är strikt anonymiserade. Läs [mer](https://www.adobe.com/privacy/experience-cloud.html).

Följande händelser är inte specifika för Product Recommendations, men krävs för att returnera resultaten:

- `view`
- `add-to-cart`
- `place-order`

The [Adobe Commerce Store Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) visar alla händelser som distribuerats till din butik. I den listan finns det dock en delmängd av händelser som är specifika för Product Recommendations. Dessa händelser samlar in data när kunderna interagerar med rekommendationsenheter i butiken och styr mätvärdena som används för att analysera hur bra era rekommendationer fungerar.

| Händelse | Beskrivning | Används för mätvärden? |
| --- | --- | --- |
| `impression-render` | Rekommendationsenheten återges på sidan. | Ja |
| `rec-add-to-cart-click` | Kunden klickar på **Lägg i kundvagnen** för ett objekt i rekommendationsenheten. | Ja, när en **Lägg i kundvagnen** finns i rekommendationsmallen. |
| `rec-click` | Kunden klickar på en produkt i rekommendationsenheten. | Ja |
| `view` | Rekommendationsenheten kan visas på sidan, t.ex. genom att bläddra i vyn. | Ja |

Följande händelser krävs för att instrumentpanelen ska kunna fyllas i korrekt.
| Kontrollpanelskolumn | Händelser | Kopplingsfält | | — | — | — | | Impressions |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId | | Vyer |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId | | Klickningar |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`    | unitId | | Intäkter |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku | | LT intäkt |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku | | CTR |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click`  | unitId, sku | | vCTR |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |

Om din storefront implementeras med PWA Studio finns mer information i [PWA dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Om du använder en anpassad klientteknik som React eller Vue JS läser du i användarhandboken för att lära dig hur du integrerar [Produkt-Recommendations i ett headless](headless.md) miljö.

## Caveats

Annonsblockerare och sekretessinställningar kan förhindra `magento/product-recommendations` från att samla in händelser och kan skapa engagemang och intäkter [mått](workspace.md) att underrapporteras.

Händelser fångar inte upp alla transaktioner som sker på handlarens webbplats. Händelser är avsedda att ge handlaren en allmän uppfattning om händelser som inträffar på webbplatsen.

Headless-implementationer måste implementera händelser för att göra Product Recommendations Dashboard mer kraftfullt.

>[!NOTE]
>
>If [Begränsningsläge för cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) är aktiverat samlar Adobe Commerce inte in beteendedata förrän kunden samtycker till att använda cookies. Om läget för cookie-begränsning är inaktiverat samlar Adobe Commerce in beteendedata som standard.
