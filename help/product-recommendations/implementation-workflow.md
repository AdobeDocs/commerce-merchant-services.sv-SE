---
title: Implementeringsarbetsflöde
description: Lär dig hur du implementerar [!DNL Product Recommendations] i din butik.
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Implementeringsarbetsflöde

[!DNL Product Recommendations] använder både beteendedata och katalogdata:

- Beteende - Data från en kunds engagemang på er webbplats, till exempel produktvisningar, artiklar som lagts till i en kundvagn och inköp. Adobe Commerce och Adobe Sensei samlar inte in personligt identifierbar information.

- Katalog - Produktmetadata som namn, pris och tillgänglighet.

När du installerar `magento/product-recommendations module`, samlar Adobe Sensei in beteendedata och katalogdata och skapar [!DNL Product Recommendations] för varje rekommendationstyp. The [!DNL Product Recommendations] distribuerar sedan dessa rekommendationer till din butik. Använd följande arbetsflöde för att implementera produktrekommendationer i butiken:

>[!NOTE]
>
> Om din storefront implementeras med PWA Studio finns mer information i [PWA dokumentation](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Om du använder en anpassad klientteknik som React eller Vue JS ska du lära dig hur [integrera](headless.md) [!DNL Product Recommendations] in i ditt headless storefront.

## Arbetsflöde

1. **Distribuera datainsamling till produktion**

   Distribuerar [!DNL Product Recommendations] kräver två huvuden [datakällor](type.md): katalog och beteende. Eftersom produktion är den enda miljön där era kunders handlande fångas in och analyseras är det i ditt bästa intresse att börja samla in data i produktionen så tidigt som möjligt. [Läs](behavioral-data.md) hur Adobe Sensei utbildar maskininlärningsmodeller som leder till rekommendationer av högre kvalitet. Som en ytterligare fördel kan du när du börjar samla in beteendedata i produktionen [hämta rekommendationer](verify.md) baserat på dessa produktionsdata vid verksamhet i icke-produktionsmiljöer. Sedan kan ni testa och experimentera med olika rekommendationer som beräknas utifrån verkliga kunddata som samlats in i produktionen.

   Om du vill distribuera datainsamling till produktionen måste du [installera och konfigurera](install-configure.md) den [!DNL Product Recommendations] genom att tillhandahålla en [API-nyckel](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > Att datainsamlingen distribueras förändrar inte butikens utseende eller kundernas upplevelse. Det är bara när rekommendationsenheter skapas och distribueras som kundupplevelsen i er butik ändras. Testa din icke-produktionsmiljö innan du distribuerar till produktionen. Skapa inte rekommendationsenheter förrän du anpassar mallen. Se nästa steg.

1. **Anpassa mallen så att den matchar din stil**

   Din storefront representerar ditt varumärke, så se till att du ändrar mallen för produktrekommendationer så att den matchar ditt webbplatstema.

   >[!TIP]
   >
   > Genom att anpassa mallen kan du ange din formatmall, skriva över var en rekommendationsenhet visas på en sida och så vidare.

   Se [Anpassa](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) i utvecklardokumentationen för att lära dig hur du slutför det här steget.

1. **Testa rekommendationer i din icke-produktionsmiljö**

   Det är alltid en god praxis att testa ny teknik i icke-produktionsmiljön innan du driftsätter till produktionen. Genom att testa rekommendationer i din icke-produktionsmiljö kan du leka med olika typer av rekommendationsenheter, positionering och sidor. Ni kan dra slutsatser baserade på beteendedata som redan samlats in i produktionen när ni testar i er icke-produktionsmiljö, så att rekommendationsresultaten baseras på de faktiska kundernas shoppingbeteende.

   >[!TIP]
   >
   > Se till att din icke-produktionsmiljökatalog i stort sett är densamma som den du har i produktionen. Genom att använda liknande kataloger ser du till att de produkter som returneras i rekommendationsenheterna liknar produkterna i produktionen.

   Se [Hämta](staging-environment.md) beteendedata från produktionsmiljön för att lära dig hur man slutför det här steget.

1. **Skapa och distribuera rekommendationer i produktionskedjan**

   Nu när du har driftsatt beteendedatainsamlingen i produktion, ändrat produktrekommendationsmallen och testat rekommendationer med hjälp av faktiskt kundbeteende är du redo att marknadsföra all kod till produktion och [skapa](create.md) produktrekommendationer.
