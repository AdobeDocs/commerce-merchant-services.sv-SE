---
title: Skapa en målgrupp i Real-Time CDP med [!DNL Commerce] händelsedata
description: Lär dig använda [!DNL Commerce] händelsedata för att skapa en publik i Real-Time CDP
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: fc2a7ba6891cf8affdec13b0400d75350284faa2
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Skapa målgrupper i Real-Time CDP med [!DNL Commerce] Händelsedata

Använd händelsedata som hämtats in från [!DNL Commerce] lagra för att skapa målgrupper i Real-Time CDP. De data som samlas in är baserade på webbläsarbeteende, tidigare köp, profilattribut, egenskaper att konvertera eller ändra, lojalitetsstatus, högt och lågt kundvärde och mycket annat.

## Vilka data bör jag överväga att använda?

Skapa målgrupper i Real-Time CDP med data från butiker, back office och profilevent.

| Datatyper | data från Storefront (beteendehändelser) | Back office-data (händelser på serversidan) | Kundprofil och segmentdata |
|---|---|---|---|
| **Definition** | Klicka på eller vidta de åtgärder som kunderna ska vidta på er webbplats. | Information om livscykeln och detaljer för varje order (tidigare och aktuell). | Vilka era kunder är och vilka segment är de kvalificerade för? |
| **Evenemang tagna med Adobe Commerce** | [productPageView](events.md#productpageview)<br>[addToCart](events.md#addtocart) | [placeOrder](events.md#completecheckout)<br>[orderplacerad](events-backoffice.md#orderplaced)<br>[orderLineItemRefunded](events-backoffice.md#orderlineitemrefunded)<br>[beställningen avbröts](events-backoffice.md#ordercancelled)<br>[orderhistorik](connect-data.md#send-historical-order-data) | [createAccount](events.md#createaccount)<br>[editAccount](events.md#editaccount)<br>[Profilpost](events-profilerecord.md) |

## Vad har andra kunder gjort?

Adobe [!DNL Commerce] kunderna har uppnått betydande affärsmässiga effekter genom att aktivera målgrupper som byggts i Real-Time CDP och driftsätta dem för sina [!DNL Commerce] -instans.

En global klädhandlare med flera varumärken har uppnått följande:

- En källa till sanning med 10 miljoner enhetliga kundprofiler
- Skapade över 40 unika målgrupper av&quot;kunder med hög återgivning&quot; för att engagera olika kanaler

Ett globalt dryckesföretag som samlat in

- 98 miljoner kundprofiler från över 100 länder

## Kom så börjar vi

I den här artikeln får du lära dig att:

- Skapa en målgrupp i Real-Time CDP baserat på [!DNL Commerce] uppgifter som evenemangen samlar in
- Aktivera den målgruppen för [!DNL Commerce] store
- Använd målgruppen i [!DNL Commerce] för att informera en kundvagnsprisregel

>[!IMPORTANT]
>
>Slutför uppgifterna som beskrivs i den här artikeln med [!DNL Commerce] sandlådemiljö. Detta garanterar att händelsedata för butiken och back office som du skickar till Experience Platform inte späder ut dina data för produktionshändelser.

### Förutsättningar

Innan du börjar, se till att:

- Du är redo att använda Real-Time CDP. Om du är osäker kan du kontakta systemintegratören eller utvecklingsteamet som hanterar projekt och miljöer.
- Du [installerat](install.md) och [konfigurerad](connect-data.md) den [!DNL Data Connection] tillägg i [!DNL Commerce].
- Du [bekräftad](connect-data.md#confirm-that-event-data-is-collected) som [!DNL Commerce] händelsedata kommer till Experience Platform.

### 1. Skapa en målgrupp

En målgrupp är en uppsättning kunder som har liknande beteenden eller egenskaper. I den här övningen skapar ni en målgrupp som kvalificerar personer som är intresserade av en viss produkt från er butik.

För att förenkla den här övningen använder du händelsedata från [productPageView](events.md#productpageview) -händelse. Den här händelsen innehåller information om produkten som visades, t.ex. produktnamn, SKU, pris och så vidare.

Använd dessa händelsedata för att ange att målgruppen omfattar personer som har minst en&quot;produktvy&quot;-händelse där SKU (produktidentifierare) är lika med en viss produkt på din webbplats och händelsen inträffar under den sista dagen. &#x200B;

1. Öppna Experience Platform och markera **[!UICONTROL Audiences]** från den vänstra navigeringsmenyn.

   ![Audience Dashboard](assets/audience-left-rail.png)

1. Klicka på **[!UICONTROL Create Audience]**.

   ![Skapa publik](assets/browse-create-audience.png)

   The **Segment Builder** visas.

1. I **Segment Builder** arbetsyta väljer du **Byggregel** skapandemetod.

   ![Byggregel](assets/build-rule.png)

   The **Segment Builder** är där du definierar regler och villkor för målgruppen. &#x200B; Dessa regler och villkor baseras på händelse- och profildata från din Commerce Store och definierar de kriterier som avgör om en användare uppfyller kraven för målgruppen. Du kan t.ex. skapa en regel som omfattar användare som har visat en viss produkt eller användare som har gjort ett köp inom en viss tidsram. Läs mer om [Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) samt regler och villkor.

1. Välj [Händelser](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) -fliken.

   ![Fliken Event](assets/audience-events-tab.png)

1. Sök efter händelsetypen&quot;Produktvyer&quot;. Dra och släpp det sedan i **Segment Builder** arbetsyta.

1. Återgå till **Händelser** och söka efter&quot;SKU&quot;, som är ett datafält under `productListItems` fält. Dra och släpp den till **Segment Builder** arbetsytan högst upp i **Produktvy** -händelse.

   The **Händelseregler** visas där du kan ange vilken produkt du vill bygga ut för målgruppen.

   ![Välj SKU](assets/audience-addsku.png)

1. Ställ in tidsintervallet till en dag genom att klicka på **Valfri tid** och markera *I sista* med värdet *1*.

   När du skapar en målgrupp kan du ange ett tidsintervall för att hämta den senaste aktiviteten. Om du anger ett tidsintervall kan du rikta in dig på användare baserat på deras senaste interaktioner eller beteenden inom en viss tidsram.

1. I **Målgruppsegenskaper** till höger om arbetsytan anger du målgruppsegenskaperna genom att ange ett namn, en beskrivning och en utvärderingsmetod för målgruppen.

1. Klicka för att spara **[!UICONTROL Save and Close]**.

   Din målgrupp visas på **Målgrupp** kontrollpanel.

### 2. Aktivera målgruppen för [!DNL Commerce] mål

Gör en målgrupp tillgänglig i [!DNL Commerce] genom att aktivera den för [!DNL Commerce] mål.

>[!IMPORTANT]
>
>Om du inte redan har angett [!DNL Commerce] som ett tillgängligt mål för att ta emot data, se [Adobe [!DNL Commerce] Anslutning](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce) ämne.

1. I **Information** klickar du på **Aktivera till mål**.

1. Välj [!DNL Commerce] mål. Klicka sedan på **Nästa**.

1. Slutför aktiveringsprocessen genom att klicka **[!UICONTROL Finish]**.

## 3. Visa målgruppen på Publikkontrollpanelen

I [!DNL Commerce]kan du visa alla [aktiv](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) målgrupper som kan personaliseras för er [!DNL Commerce] -instans med **Real-Time CDP-målgrupper** kontrollpanel.

Så här öppnar du **Real-Time CDP-målgrupper** kontrollpanelen, gå till _Administratör_ sidebar, sedan går du till **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

På kontrollpanelen letar du efter den målgrupp du har skapat. Observera att det inte används i en kundprisregel eller ett dynamiskt block. I nästa avsnitt länkar du målgruppen till en kundvagnsprisregel.

![Real-Time CDP Auditions Dashboard](assets/real-time-cdp-dashboard.png)

### 4. Skapa en kundprisregel baserad på målgruppen

I det här avsnittet visas hur du skapar en kundprisregel baserat på din nya målgrupp.

1. Bekräfta att din nya målgrupp visas i **Real-Time CDP-målgrupper** kontrollpanel.
1. [Skapa en kundvagnsprisregel](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [Ange villkoret](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) av kundvagnsprisregeln med er nya målgrupp.
1. [Ange åtgärd](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) som du vill ska inträffa när produkten läggs till i kundvagnen.
1. Fortsätt att konfigurera kundvagnsprisregeln.
1. Gå till kundvyn för din sandlådeinstans.
1. Lägg den produkt du baserar målgruppen på i kundvagnen. Observera att kundvagnsprisregeln är aktiverad.

## Radbryt

I den här övningen skapade du en publik i Real-Time CDP och aktiverade den för [!DNL Commerce] mål. Sedan i [!DNL Commerce] admin, du skapade en kundprisregel baserat på den målgruppen och aktiverade regeln i din sandlådemiljö.
