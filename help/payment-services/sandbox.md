---
title: Konfigurera testsandlådan
description: Använd ett PayPal-sandlådekonto för att använda [!DNL Payment Services] i testläge.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Konfigurera testsandlådan

Innan du påbörjar introduktionen av sandlådor måste du registrera dig för ett kostnadsfritt PayPal-utvecklarkonto och skapa både handlare (som ska användas för introduktion) och kundkonton (som ska användas för att testa utcheckningen). Du kan skapa flera utvecklarkonton om du vill.

Med ett PayPal-sandlådekonto kan du använda [!DNL Payment Services] i testläge. PayPal kräver att du använder ett PayPal Developer Portal-genererat Business Sandbox-testkonto, e-post och lösenord för sandlådeintroduktion. Skapa inte ett annat konto under sandlådeintroduktionsprocessen.

Om du skapade ett konto under PayPal-introduktionsprocessen i sandlådan måste du återställa din introduktionssandlåda eftersom du inte kan verifiera din e-post.

Så här återställer du sandlådekontot:

1. Klicka på **[!UICONTROL Reset sandbox]**. Se [PayPal skapa ett företagssandlådekonto](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) mer information.
1. Klicka **[!UICONTROL Sandbox onboarding]** och slutföra nästa steg.

Så här slutför du introduktionen av sandlådor:

1. Navigera till [Sidan PayPal Developer Account](https://developer.paypal.com/developer/accounts/).
1. Klicka **[!UICONTROL Log in to Home]** och logga in med dina befintliga uppgifter på PayPal Developers-kontot eller klicka på **Registrera dig** för att skapa ett konto.
1. Skapa ett PayPal-sandlådekonto:
   1. Gå till _[!UICONTROL SANDBOX]_>**[!UICONTROL Accounts]**.
   1. Klicka på **[!UICONTROL Create account]**.
   1. Välj **[!UICONTROL Business]** som kontotyp och klicka på **[!UICONTROL Create]**.
   1. I _[!UICONTROL Sandbox Accounts]_klickar du på de tre punkterna i_[!UICONTROL Manage accounts]_ -kolumn för det sandlådekonto som du har skapat.
   1. Klicka på **[!UICONTROL View/edit account]**.

      ![PayPal - Visa/redigera sandlådekonto](assets/onboarding-viewedit-sandbox.png)

   1. Kopiera och spara e-post-ID och systemgenererat lösenord för framtida bruk.

1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klicka på **[!UICONTROL Sandbox onboarding]**.

   Det här alternativet är synligt om du ännu inte har slutfört sandlådeintroduktion för [!DNL Payment Services].

   Ett handlar-ID för sandlådan genereras automatiskt och fylls i i [inställningar](settings.md). Ändra eller ändra inte detta ID.

   Du får ett PayPal-fönster där du kan ansluta ett PayPal-konto för att börja acceptera betalningar.

1. Ange e-postadressen till ditt företagskonto och ditt land eller din region och klicka på **[!UICONTROL Next]**.

   ![PayPal - Anslut PayPal-konto för betalningar](assets/paypal-connectacct.png)

1. Fortsätt att följa PayPal-flödet med dina tidigare sparade inloggningsuppgifter för sandlådekonton.
1. På _Administratör_ sidebar, gå till **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   The **[!UICONTROL Sandbox onboarding]** knappen visas inte längre och du ser texten &quot;Sandlådebetalningar väntar&quot;.

När din introduktion till PayPal-sandlådan har godkänts bör du se ett meddelande om att ditt betalningssystem för närvarande är i sandlådeläge och inte hanterar livesändningar.

>[!IMPORTANT]
>
>Om du återkallar samtycke till [!DNL Payment Services] for [!DNL Adobe Commerce] och [!DNL Magento Open Source] för bearbetning av dina betalningar (i dina PayPal-kontoinställningar), kan beställningar i din butik inte bearbetas av [!DNL Payment Services].

## Aktivera telefonnummer för kontakt

Med telefonnumret kan du få de telefonnummer som PayPal samlar in från dina kunder. PayPal samlar alltid in kontakttelefonnummer från PayPal-kontoinnehavare för att hjälpa dem att bekräfta sina identiteter och kontakta dem för att lösa problem på sina konton eller för att slutföra sina leveransprocesser. PayPal rekommenderar dock inte att telefonnummer används direkt från handlaren eftersom det kan påverka försäljningen negativt. Se [PayPal hämta telefonnummer till kontaktperson](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) mer information.

Den här funktionen är `off` som standard. När du aktiverar det kan butiksadministratörer se telefonnummer när en kund slutför ett flöde för profilerad utcheckning utanför utcheckningssidan.

>[!IMPORTANT]
>
>Den här inställningen gäller inte andra utcheckningsflöden.

## Testa i sandlådemiljö

Se [Testa och validera](test-validate.md) för mer information.
