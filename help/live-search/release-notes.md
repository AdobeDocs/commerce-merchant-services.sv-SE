---
title: '"[!DNL Live Search] Versionsinformation"'
description: '"Den senaste versionsinformationen för [!DNL Live Search] från Adobe Commerce."'
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 097f8af7a1e3e904c69d3a7fe52cb0db5b1b4c23
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# [!DNL Live Search] Versionsinformation

I versionsinformationen beskrivs de senaste versionerna av [!DNL Live Search] och innehåller:

* ![Nytt](../assets/new.svg) - Nya funktioner
* ![Korrigera](../assets/fix.svg) - Korrigeringar och förbättringar
* ![Fel](../assets/bug.svg) - Kända fel

## [!DNL Live Search] 2.0.3

* Kompatibel med Adobe Commerce (EE): 2.4.x
* Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilitet: Stabil

* ![Nytt](../assets/new.svg) - Live Search har nu stöd för B2B-funktioner genom att man hanterar kategoribehörigheter, delade kataloger och kundgruppsspecifika priser.

Handlare måste uppgradera Live Search-tillägget version >= 2.0.3 för att få tillgång till dessa funktioner.

Vi rekommenderar användare att uppgradera och testa innan de går till produktion. Överväg att uppgradera produktionsmiljön under tider med låg belastning efter att ha verifierat testmiljöresultaten.

>[!NOTE]
>
>B2B-stöd kommer att läggas till i faser från och med den 9 augusti för backend-tjänsterna, och en förväntad migrering kommer att vara slutförd i slutet av augusti. Om Live Search-tillägget inte uppgraderas kommer din storefront att fortsätta fungera som vanligt, men utan B2B-funktioner.

### Kända begränsningar/fel:

* ![Fel](../assets/bug.svg) - Förslag kommer från produkter som inte kan visas för kundgruppen.
* ![Fel](../assets/bug.svg) - Produkter visas inte om de inte läggs till i standardkatalogen för delade produkter.
* B2B med Live Search för PWA Studio är inte tillgängligt förrän PWA Studio har stöd för det.
* Åsidosättningar av produkter och produktattribut kan ha synkroniseringsproblem som kräver att administratörer kör `bin/magento indexer:reset` och `bin/magento indexer:reindex` för att synkronisera på nytt.

## [!DNL Live Search] 2.0

* Kompatibel med Adobe Commerce (EE): 2.4.x
* Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilitet: Stabil

Befintlig [!DNL Live Search] installationerna måste uppgraderas till [!DNL Live Search] 2.0.0 för att utnyttja följande nya funktioner, korrigeringar och förbättringar:

* ![Nytt](../assets/new.svg) - [!DNL Live Search] har nu stöd för PHP 8.1 för installationer som kör Adobe Commerce 2.4.4.
* ![Nytt](../assets/new.svg) - `Magento_ElasticsearchCatalogPermissionsGraphQl` läggs till i listan med moduler som är inaktiverade under installationen.
* ![Nytt](../assets/new.svg) - Antalet tillgängliga rader i [[!DNL storefront popover]](quick-tour.md) kan konfigureras från *Administratör*.
* ![Nytt](../assets/new.svg) - Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) kompatibilitet för [!DNL Live Search].
* ![Nytt](../assets/new.svg) - [!DNL Live Search] installationsprocessen uppdateras med avancerade processändringar.
* ![Korrigera](../assets/fix.svg) - [Avancerad sökning](https://docs.magento.com/user-guide/catalog/search-advanced.html) länk borttagen från sidfoten i butiken.
* ![Fel](../assets/bug.svg) - Följande produktattribut stöds inte av [Magento GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql) vid användning i samband med betaversionen av PWA: `description`, `name`, `short_description`
* ![Fel](../assets/bug.svg) - Betaversionen av PWA för [!DNL Live Search] stöder inte [händelsehantering](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1

* Kompatibel med Adobe Commerce (EE): 2.4.x
* Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilitet: Stabil

* ![Korrigera](../assets/fix.svg) - [Anpassat prisattribut](https://docs.magento.com/user-guide/stores/attributes-input-types.html) returnerar inte längre ett fel när det konfigureras som [facet]({% link live-search/facets-add.md %}).
* ![Korrigera](../assets/fix.svg) - Ett problem som orsakade att ett fel uppstod när [valutasymbol](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) är tillgängligt.
* ![Korrigera](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) nu visas [Specialpris](https://docs.magento.com/user-guide/catalog/product-price-special.html) (lägsta slutpris) om tillgängligt.

## [!DNL Live Search] 1.3.0

* Kompatibel med Adobe Commerce (EE): 2.4.x
* Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilitet: Stabil

* ![Nytt](../assets/new.svg) - [Prestanda](performance.md) på kontrollpanelen för rapporter ger insikt i söktermer som kunderna använder.
* ![Nytt](../assets/new.svg) - [!DNL Live Search] [Storefront Events SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) ger tillgång till ett gemensamt datalager med händelsepublicerings- och prenumerationstjänster samt mätvärden.
* ![Korrigera](../assets/fix.svg) - [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) har en ny `active` klassen för `.search-autocomplete` behållare som styr synlighet.
* ![Korrigera](../assets/fix.svg) - I butiken finns [Sökvillkor](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) sidfotslänken tas bort och dess cache inaktiveras för [!DNL Live Search] installationer.
* ![Fel](../assets/bug.svg) - Patch for Search adapter hanterar dubblettprodukter.
* ![Fel](../assets/bug.svg) - [!DNL Live Search] supports [single-source](https://docs.magento.com/user-guide/catalog/inventory-sources.html) (fysisk) lagerplatser med flera (virtuell) [lager](https://docs.magento.com/user-guide/catalog/inventory-stock.html). Flera lagerkällor stöds inte för närvarande.

## [!DNL Live Search] 1.2.0

* Kompatibel med Adobe Commerce (EE): 2.4.x
* Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilitet: Stabil

* ![Nytt](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) visar föreslagna produkter och miniatyrbilder av de bästa sökresultaten när kunderna skriver frågor i sökrutan.
* ![Nytt](../assets/new.svg) - Handel *Administratör* -sessionen förblir öppen under längre perioder av tangentbordsinaktivitet
* ![Nytt](../assets/new.svg) - [!DNL Live Search] aktiveras automatiskt efter introduktionen
* ![Korrigera](../assets/fix.svg) - Inledande indexeringstid är mindre än en timme
* ![Korrigera](../assets/fix.svg) - Stegvisa produktuppdateringar nära realtid (efter installation och installation)
* ![Korrigera](../assets/fix.svg) - Sorterbara kolumner i synonymredigeraren
* ![Korrigera](../assets/fix.svg) - [!DNL Live Search] returnerar inte längre ett fel om sökvillkoren innehåller ett tomt sorteringsordningsvärde
* ![Korrigera](../assets/fix.svg) - Intervallfiltrering avbryts inte längre om attributkoder innehåller strängarna &quot;to&quot; eller &quot;from&quot;

## [!DNL Live Search] 1.1.0

* Kompatibel med Adobe Commerce (EE): 2.4.x
* Kompatibel med Adobe Commerce for Cloud (ECE): 2.4.x
* Stabilitet: Stabil

* ![Fel](../assets/bug.svg) - [!DNL Live Search] tjänsten stöder endast [basvaluta](https://docs.magento.com/user-guide/stores/currency-configuration.html) av Adobe Commerce-installationen.
* ![Fel](../assets/bug.svg) - När du lägger till en fasett uppdateras inte produktattributsmatningen korrekt när den anges till `Update on Save`. För att undvika det här problemet, gå till [Indexhantering](https://docs.magento.com/user-guide/system/index-management.html) och ange produktattribut för feed till `Update by Schedule`.
* ![Fel](../assets/bug.svg) - [!DNL Live Search] synonymer definieras per butiksvy, men lagras för närvarande per webbplats och identifieras med en kombination av `environmentId` + `storeViewCode`. Därför har alla webbplatser och butiksvyer i Adobe Commerce samma uppsättning synonymer. Den senast skapade uppsättningen synonymer för butiksvyn har företräde.
* ![Fel](../assets/bug.svg) - Om en synonymterm innehåller flera ord behandlas varje ord som en separat synonym. Om du till exempel definierar&quot;tidsbit&quot; som en synonym till&quot;watch&quot;, behandlas både&quot;time&quot; och&quot;piece&quot; som synonymer till&quot;watch&quot;.

## Dokumentation

Mer information:

* [Adobe Commerce Developer Documentation](https://devdocs.magento.com/)
* [Adobe Commerce Användarhandbok](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] på Marketplace](https://marketplace.magento.com/magento-live-search.html)
