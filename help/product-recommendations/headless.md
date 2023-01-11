---
title: Headless
description: Integrera [!DNL Product Recommendations] i en headless butik.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Headless

Ni kan integrera [!DNL Product Recommendations] i en headless storefront med antingen [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) eller en anpassad klientteknik, som React eller Vue JS.

[!DNL Product Recommendations] krav [beteendedata och katalogdata](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) att fungera. Synkroniseringsprocessen för katalogdata förblir oförändrad i en headless-implementering, men ändringar krävs för att samla in beteendedata.

Integrera [!DNL Product Recommendations] i en headless butik måste du:

1. Skicka beteendedata till Adobe Sensei för att analysera och beräkna produktrekommendationsresultat. Du kan också skicka ytterligare data för att aktivera produktrekommendationer [mätrapporter](workspace.md).

1. Hämta produktrekommendationsresultat och återge dessa resultat på sidan.

Du kan utföra båda dessa åtgärder med de tillgängliga SDK:erna enligt följande arbetsflöde.

1. [Installera](install-configure.md) den [!DNL Product Recommendations] -modul.

1. Installera och använda [Adobe Commerce Storefront Event SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) att avskeda [beteendehändelser](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

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

1. När händelserna utlöses använder du [Adobe Commerce Storefront Event Collector](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) för att hantera händelserna och skicka dem till Adobe Sensei.

1. När beteendedata har samlats in kan du [skapa](create.md) [!DNL Product Recommendations] i Admin.

1. Använd [Recommendations SDK](https://developer.adobe.com/commerce/services/product-recommendations/) för att hämta rekommendationsenheterna på butiken. SDK returnerar nödvändiga produktdata för att återge rekommendationsenheter på en sida.
