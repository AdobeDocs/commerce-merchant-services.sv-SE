---
title: Återbetalningar
description: Skapa återbetalningar för  [!DNL Payment Services] order i Admin som en del av kreditfakturaprocessen.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Återbetalningar

Återbetalningar för [!DNL Payment Services] order skapas i administratören som en del av kreditnotsprocessen. En kreditnota är ett dokument som visar det belopp som ska betalas till kunden, för en fullständig eller partiell återbetalning, som kan tillämpas på ett köp eller återbetalas direkt till kunden. Kreditnotor kan bara utfärdas för order som är [fakturerade](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

Se [Kreditnotor](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} i vår huvudanvändarhandbok för mer information och för att lära dig hur du utfärdar och skriver ut kreditnotor.

För beställningar som behandlas med PayPal eller ett kreditkort kan du:

* Återbetala hela orderbeloppet
* Återbetala en del av en order (eller flera delbelopp)
* Återbetala ett belopp som är mindre än värdet för en viss orderartikel

Mer information finns i [Utfärda kreditnota](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} i vår huvudanvändarhandbok.

>[!NOTE]
>
>Ett fel uppstår för PayPal- eller kreditkortsbeställningar om du försöker att delvis återbetala en order för mer än det återstående orderbeloppet (ursprungligt belopp minus summan av befintliga återbetalningar) eller om du utfärdar en återbetalning för ett belopp som är större än det fullständiga orderbeloppet.

Inställningen [!UICONTROL Payment Action] i din [!UICONTROL Payment Settings]-konfiguration - antingen `Authorize` eller `Authorize and Capture` - avgör det [grundläggande återbetalningsarbetsflödet](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} för order.

Mer information finns i avsnittet [Betalningsåtgärdsinställningar](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} i _Utfärda kreditnota_.
