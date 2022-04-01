---
title: Lägg till synonymer
description: Lägg till Live Search-synonymer för att förbättra svar på sökningar.
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Lägg till synonymer

Lägg till en egen kuraterad lista med [!DNL Live Search] synonymer för att förbättra svar på sökförfrågningar och hålla kunderna engagerade.

![[!DNL Live Search] synonymer](assets/synonym-workspace.png)

## Steg 1: Lägg till en synonym

1. Gå till Admin **Marknadsföring** > SEO &amp; Search > **[!DNL Live Search]**.
1. För flera butiker: ange **Omfång** till [butiksvy](https://docs.magento.com/user-guide/configuration/scope.html) där synonyminställningarna gäller.
1. Klicka på **Synonymer** -fliken.
1. Klicka på **Lägg till synonymer** -knappen.

## Steg 2: Definiera synonymen efter typ

Följ instruktionerna för [typ av synonym](synonyms-type.md) som du vill skapa.

### Tvåvägssynonym

1. Acceptera standardinställningen **Tvåvägs** alternativ.

   ![Lägg till tvåvägssynonym](assets/synonym-add-two-way.png)


1. Ange **Nyckelord** term eller fras som ska matchas.
1. Ange **Utbyggnad** termer som du vill lägga till som synonymer för nyckelordet. Avgränsa flera termer med kommatecken.
I det här exemplet är nyckelordet som ska matchas&quot;byxor&quot; och uppsättningen expansionstermer är&quot;långbyxor, byxor, slackar&quot;.

   ![Exempel på dubbelriktad synonym](assets/synonym-add-two-way-example.png)

1. När du är klar klickar du på **Spara**.
Synonymuppsättningen visas i listan med en dubbelriktad pil mellan varje term, vilket betyder att termerna är utbytbara.

   ![Tvåvägssynonym](assets/synonym-two-way.png)

### Envägssynonym

1. Klicka på **Envägs** synonymtyp.

   ![Lägg till envägssynonym](assets/synonym-add-one-way.png)

1. Ange **Nyckelord** och **Utbyggnad** term(er). Avgränsa flera termer med kommatecken.

   ![Exempel på enkelriktad synonym](assets/synonym-add-one-way-example.png)

   I det här exemplet är nyckelordet &quot;byxor&quot; och de ensidiga expansionstermerna &quot;capris, kalvbyxor, pedagogisk tändare&quot; är var och en en delmängd av &quot;byxor&quot;, men med en specifik betydelse.

1. När du är klar klickar du på **Spara**.
Synonymuppsättningen visas i listan med en enkelriktad pil som pekar från expanderingsvillkoren till nyckelordet för att ange att termerna är deluppsättningar av nyckelordet. Ett plustecken avgränsar varje expansionsterm.

   ![Envägssynonym](assets/synonym-one-way.png)

## Steg 3: Publicera ändringar

1. När dina synonymer är klara klickar du på **Publicera ändringar**.
1. Vänta i upp till två timmar tills dina uppdateringar är tillgängliga i butiken.

![Publicera ändringar](assets/synonym-publish.png)

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| [Typ](synonyms.md) | Avgör om synonymer har samma betydelse som nyckelordet eller är en delmängd av nyckelordet. Alternativ:<br />Tvåvägs (standard) - Termer som har samma betydelse som nyckelordet och returnerar samma sökresultat<br />Enkelriktad - Termer som är en delmängd av nyckelordet. Envägssynonymer returnerar en mer smal lista över specifika produkter. |
| Nyckelord | Ett ord som vanligtvis associeras med ett urval produkter i din katalog. |
| Utbyggnad | Ytterligare termer som har samma eller liknande betydelse som nyckelordet. |
