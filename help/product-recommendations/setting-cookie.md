---
title: Hantera cookie-begränsningar
description: Läs om hur produktrekommendationer hanterar begränsningar av cookies.
exl-id: 2f48c47c-569b-455c-a589-8f99b7b74064
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Hantera cookie-begränsningar

Både Adobe Commerce och Magento Open Source begär samtycke innan data lagras i webbläsarcookies. Mer information finns i [Begränsningsläge för cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

När du distribuerar `magento/product-recommendations` från en modul till en produktion börjar det samla in interaktionshändelser för kunderna i din butik. Eftersom data för de här händelserna kan lagras i webbläsarcookies eller lokal lagring stöder funktionen läget för begränsning av cookies genom att inte samla in händelser förrän kunden har gett sitt samtycke till cookies.

Detta kanske inte fungerar med cookie-lösningar från tredje part. Det är varje handlares ansvar att se till att datainsamlingen inte sker innan cookie-samtycke har lämnats, vilket ofta krävs enligt lag. Om du hanterar cookie-samtycke med anpassad kod kan du använda en cookie som kallas för att inte spåra `mg_dnt` för att begränsa datainsamling.

- Namn på cookie:

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- Ställ in Do-not-track-cookie för att inaktivera datainsamling:

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- Så här rensar du cookien när användaren har accepterat cookies:

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
