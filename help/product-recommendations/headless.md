---
title: Headless
description: Integrera [!DNL Product Recommendations] i en headless butik.
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Headless

Ni kan integrera [!DNL Product Recommendations] i en headless storefront med antingen [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) eller en anpassad klientteknik, som React eller Vue JS.

[!DNL Product Recommendations] krav [beteendedata och katalogdata](https://devdocs.magento.com/recommendations/product-recs.html#typesofdata) att fungera. Synkroniseringsprocessen för katalogdata förblir oförändrad i en headless-implementering, men ändringar krävs för att samla in beteendedata.

Integrera [!DNL Product Recommendations] i en headless butik måste du:

1. Skicka beteendedata till Adobe Sensei för att analysera och beräkna produktrekommendationsresultat. Du kan också skicka ytterligare data för att aktivera produktrekommendationer [mätrapporter](workspace.md).

1. Hämta produktrekommendationsresultat och återge dessa resultat på sidan.

Du kan utföra båda dessa åtgärder med de tillgängliga SDK:erna enligt följande arbetsflöde.

1. [Installera](install-configure.md) den [!DNL Product Recommendations] -modul.

1. Installera och använda [Storefront Events SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) att avskeda [beteendehändelser](https://devdocs.magento.com/recommendations/events.html).

   Minsta antal händelser som måste returneras [!DNL Product Recommendations] resultat:

   | Händelse | Kategori |
   |--- | ---|
   | `view` | produkt |
   | `add-to-cart` | produkt |
   | `place-order` | utcheckning |

   Aktivera [mätrapporter](workspace.md)krävs följande ytterligare händelser:

   | Händelse | Kategori |
   |--- | ---|
   | `impression-render` | rekommendationsenhet |
   | `view` | rekommendationsenhet |
   | `rec-click` | rekommendationsenhet |
   | `rec-add-to-cart-click` | recommendation-unit (om det finns en tilläggsknapp i kundvagnen i rekommendationsmallen) |

1. När händelserna utlöses använder du [Storefront Events-samlare](https://devdocs.magento.com/shared-services/storefront-event-collector.html) för att hantera händelserna och skicka dem till Adobe Sensei.

1. När beteendedata har samlats in kan du [skapa](create.md) [!DNL Product Recommendations] i Admin.

1. Använd [Recommendations SDK](https://devdocs.magento.com/recommendations/recs-api.html) för att hämta rekommendationsenheterna på butiken. SDK returnerar nödvändiga produktdata för att återge rekommendationsenheter på en sida.
