---
title: Återbetalningar
description: Skapa återbetalningar för [!DNL Payment Services] beställningar hos administratören som en del av kreditnotsprocessen.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Återbetalningar

Återbetalningar för [!DNL Payment Services] beställningar skapas i administratören som en del av kreditnotsprocessen. En kreditnota är ett dokument som visar det belopp som ska betalas till kunden, för en fullständig eller partiell återbetalning, som kan tillämpas på ett köp eller återbetalas direkt till kunden. Kreditnotor kan bara utfärdas för order som [fakturerad](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

Se [Kreditnotor](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} i vår huvudanvändarhandbok för mer information och för att lära dig hur man utfärdar och skriver ut kreditnotor.

För beställningar som behandlas med PayPal eller ett kreditkort kan du:

* Återbetala hela orderbeloppet
* Återbetala en del av en order (eller flera delbelopp)
* Återbetala ett belopp som är mindre än värdet för en viss orderartikel

Se [Utfärda en kreditnota](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} i vår användarhandbok för mer information.

>[!NOTE]
>
>Ett fel uppstår för PayPal- eller kreditkortsbeställningar om du försöker att delvis återbetala en order för mer än det återstående orderbeloppet (ursprungligt belopp minus summan av befintliga återbetalningar) eller om du utfärdar en återbetalning för ett belopp som är större än det fullständiga orderbeloppet.

The [!UICONTROL Payment Action] i [!UICONTROL Payment Settings] configuration—either `Authorize` eller `Authorize and Capture`—bestämmer [grundläggande återbetalningsarbetsflöde](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} för order.

Se [Inställningsavsnitt för betalningsåtgärd](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} av _Utfärda en kreditnota_ för mer information.
