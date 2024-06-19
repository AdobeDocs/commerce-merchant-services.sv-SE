---
title: Synkronisera data med SaaS-dataexport
description: "Se hur [!DNL SaaS Data Export] Samlar in och synkroniserar data mellan Adobe Commerce-instanser och anslutna SaaS-tjänster."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# Synkronisera data med SaaS-dataexport

När du installerar en Commerce-tjänst som kräver dataexport som Catalog Service, Live Search eller Product Recommendations installeras en samling Saas-moduler för dataexport för att hantera datainsamling och synkroniseringsprocessen. I följande diagram visas dataexportflödet i SaaS.

![Samling och synkronisering av SaaS-data för Adobe Commerce](assets/data-export-flow.png){width="900" zoomable="yes"}

De viktigaste komponenterna i SaaS dataexportflöde är:

- SaaS-moduler för dataexport som samlar in data för flöden från Adobe Commerce, samlar ihop flödesobjekt, lyssnar efter uppdateringar och behåller feedstatus.
- SaaS exporterar moduler som exporterar data, konfigurerar routning och publicerar flöden till anslutna tjänster.
- Adobe Commerce-tjänsten hanterar dataöverföringsprocessen för att validera inkommande flöden och bevarar uppdateringar av anslutna tjänster.

## Synkroniseringslägen

SaaS-dataexport har två lägen för att bearbeta enhetsflöden:

- **Direkt exportläge**- I det här läget samlas data in och skickas omedelbart till Commerce-tjänsten i en enda iteration. Det här läget snabbar upp leveransen av entitetsuppdateringar till Commerce-tjänsten och minskar lagringsstorleken för flödestabellerna.

- **Äldre exportläge**- I det här läget samlas data in i en enda process. Sedan skickar ett cron-jobb insamlade data till de anslutna handelstjänsterna. I loggposter för dataexport etiketteras feeds som använder det äldre läget `(legacy)`.

## Synkroniseringstyper

SaaS-dataexport har stöd för tre synkroniseringstyper: fullständig synkronisering, partiell synkronisering och återförsök med objektsynkronisering.

### Fullständig synkronisering

När du har anslutit en Adobe Commerce-instans till Commerce Service utför du en fullständig synkronisering för att skicka entitetsmatningsdata från Adobe Commerce till den anslutna tjänsten.

>[!NOTE]
>
>Fullständig synkronisering gäller främst för introduktionsfasen. Undvik regelbunden användning för att förhindra databasöverbelastning. Efter den inledande synkroniseringen synkroniseras pågående ändringar automatiskt med partiell synkronisering.

### Delvis synkronisering

Med partiell synkronisering skickar SaaS-dataexport automatiskt uppdateringar från Commerce-programmet, till exempel produktnamnsändringar eller prisuppdateringar, till anslutna handelstjänster.

I dataexportprocessen används följande cron-jobb för att automatisera den partiella synkroniseringsåtgärden.

- &quot;index&quot; cron group-jobb:
   - The `indexer_reindex_all_invalid` alla ogiltiga feeds indexeras om. Det är ett vanligt Adobe Commerce cron-jobb.
   - The `saas_data_exporter` jobb för tidigare exportflöden.
   - The `sales_data_exporter` jobbet är specifikt för exportflödet med försäljningsdata.

Dessa jobb utförs varje minut.

För att partiell synkronisering ska fungera krävs följande konfiguration för Commerce-programmet:

- [Aktivitetsplanering är aktiverad via cron-jobb](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- Alla SaaS-dataexportindexerare har konfigurerats i `Update by Schedule` läge.

  I SaaS dataexportversion 103.1.0 och senare, `Update by Schedule` läge är aktiverat som standard. Du kan verifiera indexkonfigurationen på servern med kommandot Commerce CLI, `bin/magento indexer:show-mode | grep -i feed`

### Försök synkronisera misslyckade objekt igen

Synkroniseringen av objekt som misslyckats med försök använder en separat process för att skicka om objekt som inte kunde synkroniseras på grund av fel under synkroniseringsprocessen, till exempel ett programfel, nätverksavbrott eller ett SaaS-tjänstfel. Implementeringen för den här synkroniseringen baseras också på cron-jobb.

- `resync_failed_feeds_data_exporter` cron group-jobb:
   - The `<feed name>_feed_resend_failed_feeds_items` jobbet skickar om objekt som inte kunde synkroniseras, till exempel `products_feed_resend_failed_items`.

### Visa och hantera synkroniseringsprocessen

De flesta synkroniseringsaktiviteter bearbetas automatiskt baserat på programkonfigurationen. SaaS-dataexport innehåller dock även verktyg för att hantera processen.

- Administratörsanvändare kan visa och spåra synkroniseringsförloppet och få information om data från [Kontrollpanel för datahantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

- Utvecklare, systemintegratörer och administratörer med tillgång till Commerce programserver kan hantera synkroniseringsprocessen och dataflöden med Adobe Commerce kommandoradsverktyg (CLI). Se [Kommandoreferens för dataexport](data-export-cli-commands.md).

### Verifiera Commerce programkonfiguration

Delvis synkronisering och Försök igen misslyckades. Objekten synkroniseras bara om Commerce-instansen har konfigurerats korrekt. Konfigurationen slutförs vanligtvis när du konfigurerar Commerce-tjänsten. Kontrollera följande konfiguration om dataexporten inte fungerar som den ska.

- [Bekräfta att cron-jobb körs](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).

- Verifiera att indexerarna körs från [Administratör](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) eller med kommandot Commerce CLI `bin/magento indexer:info`.

- Verifiera att indexerarna för följande feeds är inställda på `Update by Schedule`: Katalogattribut, produkt, åsidosättning av produkt och produktvariant. Du kan kontrollera indexerarna från [Indexhantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) i Admin eller via CLI (`bin/magento indexer:show-mode | grep -i feed`).
