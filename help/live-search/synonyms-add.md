---
title: "Lägg till synonymer"
description: "Lägg till [!DNL Live Search] synonymer för att förbättra svar på sökförfrågningar."
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: 63318e2eb75bc5fb0a243b6430751b076e541b72
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Lägg till synonymer

Öka kundengagemanget genom att lägga till en egen förvaltad lista med [!DNL Live Search] synonymer. [!DNL Live Search] kan hantera upp till 200 synonymer per `Data Space ID`.

![[!DNL Live Search] synonymer](assets/synonym-workspace.png)

## Steg 1: Lägg till en synonym

1. Gå till Admin **Marknadsföring** > SEO &amp; Search > **[!DNL Live Search]**.
1. För flera butiker: **Omfång** till [butiksvy](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) där synonyminställningarna gäller.
1. Klicka på **Synonymer** -fliken.
1. Klicka på **Lägg till synonymer** -knappen.

## Steg 2: Definiera synonymen efter typ

Följ instruktionerna för [typ av synonym](synonyms-type.md) som du vill skapa.

### Tvåvägssynonym

1. Acceptera standardinställningen **Tvåvägs** alternativ.

   ![Lägg till tvåvägssynonym](assets/synonym-add-two-way.png)


1. Ange **Nyckelord** term eller fras som ska matchas.
1. Ange **Utbyggnad** termer som du vill lägga till som synonymer för nyckelordet. Avgränsa flera termer med komma.
I det här exemplet är nyckelordet som ska matchas&quot;byxor&quot; och uppsättningen expansionstermer är&quot;byxor, slackar&quot;.

   ![Exempel på dubbelriktad synonym](assets/synonym-add-two-way-example.png)

1. När du är klar klickar du på **Spara**.
Synonymuppsättningen visas i listan med en dubbelriktad pil mellan varje term, vilket betyder att termerna är utbytbara.

   ![Tvåvägssynonym](assets/synonym-two-way.png)

### Envägssynonym

1. Klicka på **Envägs** synonymtyp.

   ![Lägg till envägssynonym](assets/synonym-add-one-way.png)

1. Ange **Nyckelord** och **Utbyggnad** villkor. Avgränsa flera termer med komma.

   ![Exempel på enkelriktad synonym](assets/synonym-add-one-way-example.png)

   I det här exemplet är nyckelordet &quot;byxor&quot; och de ensidiga expansionstermerna &quot;capris, peddle-pushers&quot; är en delmängd av &quot;byxor&quot;, men med en specifik betydelse.

1. När du är klar klickar du på **Spara**.
Synonymuppsättningen visas i listan med en enkelriktad pil som pekar från expanderingsvillkoren till nyckelordet för att ange att termerna är deluppsättningar av nyckelordet. Ett plustecken avgränsar varje expansionsterm.

   ![Envägssynonym](assets/synonym-one-way.png)

## Steg 3: Publicera ändringar

1. När dina synonymer är klara klickar du på **Publicera ändringar**.
1. Vänta i upp till två timmar tills dina uppdateringar är tillgängliga i butiken.

## Fältbeskrivningar

| Fält | Beskrivning |
|--- |--- |
| [Typ](synonyms.md) | Avgör om synonymer har samma betydelse som nyckelordet eller är en delmängd av nyckelordet. Alternativ:<br />Tvåvägs (standard) - Termer som har samma betydelse som nyckelordet och returnerar samma sökresultat<br />Enkelriktad - Termer som är en delmängd av nyckelordet. Envägssynonymer returnerar en mer smal lista över specifika produkter. |
| Nyckelord | Ett ord som vanligtvis associeras med ett urval produkter i din katalog. |
| Utbyggnad | Ytterligare termer som har samma eller liknande betydelse som nyckelordet. |
