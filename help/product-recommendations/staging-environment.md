---
title: Testa i mellanlagringsmiljön
description: Lär dig använda [!DNL Product Recommendations] från produktionsmiljön i testmiljön.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
feature: Services, Recommendations, Staging
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Testa i mellanlagringsmiljön

Innan du distribuerar rekommendationer till produktionsmiljön bör du testa i en icke-produktionsmiljö för att se till att allt fungerar som det ska.

[!DNL Product Recommendations] returnera produkter baserat på [beteendedata](behavioral-data.md) som samlats in från butiken. I en icke-produktionsmiljö har ni förmodligen inga beteendedata från kunderna. Den enda rekommendationstypen som du kan testa utan beteendedata är `More like this`. Den här rekommendationstypen kräver inga indata eftersom den använder en likhetsmatchning för direkt innehåll.

Följande rekommendationstyper kräver beteendedata:

- Mest visade
- Visade det här, såg du att
- Köpte den här, köpte den där

Hur kan du testa dina rekommendationer i en icke-produktionsmiljö med beteendedata? Det finns ett par alternativ.

## Hämta rekommendationer från produktionsmiljön (rekommenderas)

Med Adobe Commerce kan du hämta rekommendationer från din produktionsmiljö och förhandsgranska dem i din icke-produktionsmiljö av [växling](settings.md) SaaS-datautrymmet.

Om du vill hämta rekommendationer från produktionsmiljön måste du se till att:

- Datainsamlingen i StockFront är [konfigurerad och aktiverad](install-configure.md) i produktionen.
- Din katalog för icke-produktionsmiljö är i stort sett densamma som den du har i produktionen. Genom att använda liknande kataloger ser du till att de produkter som returneras i rekommendationsenheterna liknar de som används i produktionen.

## Generera beteendedata i icke-produktionsmiljö

1. Distribuera `magento/product-recommendations` till en icke-produktionsmiljö där katalogdata liknar din produktionskatalog.

1. Använd ett av de icke-produktionsdatamrådets ID:n för [konfiguration](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) i Admin.

1. Generera data själv genom att klicka runt butiken för att efterlikna de verkliga kundernas beteende (eller skapa ett automatiseringsskript). Genom testningen kan ni generera beteendehändelser i er icke-produktionsmiljö. Dessa händelser används för att skapa de produkttillhörigheter som ger rekommendationer. För testning [!DNL Commerce] föreslår att du interagerar med följande rekommendationstyper:

   - Mest visade - kräver minimala indata. Användarna måste visa produkterna.
   - En titt på det här: Flera användare måste visa flera produkter.
   - Köpta den här produkten - Kräver att flera användare köper flera produkter.

### Caveats

- Beteenings- och katalogdata från SaaS-dataområdet som inte är i produktion identifierar en isolerad miljö där produktrekommendationerna baseras helt på beteendedata som genereras i den associerade butiken.

- Eftersom du inte har stora mängder beteendedata är indata för produktassociationer begränsade. Dessa data skickas dock fortfarande till Sensei för att beräkna maskininlärningsmodellerna och ge rekommendationer baserat på data som du genererat i den här miljön.
