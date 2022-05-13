---
title: Typer av synonymer
description: Enkel- och tvåvägssynonymer för Live Search utökar definitionen av nyckelord.
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: 7c3b7ff9e892521108dfec3f308db795e3ab42f9
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Typer av synonymer

Envägs- och tvåvägssynonymer utökar definitionen av nyckelord. Vissa är utbytbara med nyckelordet, medan andra representerar en delmängd av nyckelordet.

## Tvåvägs

Tvåvägssynonymer har samma betydelse och returnerar samma sökresultat. I följande exempel är det första ordet som visas i fet stil det nyckelord som används i katalogen, följt av ord som har samma betydelse som det ursprungliga nyckelordet. Du kan skapa ett enkelt par tvåvägssynonymer, eller en kedja av flera tvåvägssynonymer för samma nyckelord.

**jacka** ![Tvåvägsväljare](assets/btn-two-way.png) rock
**byxor** ![Tvåvägsväljare](assets/btn-two-way.png) slack ![Tvåvägsväljare](assets/btn-two-way.png) trousers

## Envägs

En envägssynonym är en delmängd av ett nyckelord, men med en mer specifik betydelse. Till exempel är kapris och shorts byxor, men inte alla byxor är kapris eller shorts. En sökning efter byxor innefattar kapris och shorts. Men om du söker efter kortkommandon returneras inte kapris.

**tröja** ![Envägsväljare](assets/btn-one-way.png) hoodie
**byxor** ![Envägsväljare](assets/btn-one-way.png) kapris ![Flervägsväljare](assets/btn-multiple-one-way.png) kalvlångbyxor ![Flervägsväljare](assets/btn-multiple-one-way.png) pedagoger

## God praxis

Kom ihåg följande metodtips för att få ut det mesta av Live Search-synonymer.

### Nyckelordsmappning

Den här tekniken använder sökbara produktattribut, i stället för synonymer, för att skapa nyckelordsbaserade associationer mellan produkter. Därför kan en mappad produkt visas i sökresultatet för en annan produkt. Mer information finns på [Sökresultat](https://docs.magento.com/user-guide/catalog/search-results.html).

### Använd enstaka ord

Om en synonymterm innehåller flera ord behandlas de som separata synonymer om de är tomma mellan orden. Om du till exempel definierar&quot;tidsbit&quot; som en synonym för&quot;watch&quot; behandlas orden&quot;time&quot; och&quot;piece&quot; som separata synonymer.

### Användning av singular och plural

Det är inte nödvändigt att definiera både singular- och plural-former för ett ord som synonym. Om du har en blandning av enstaka och plurala termer i din katalog hittar du rätt uppsättning med produkter i Sök. Om du till exempel använder ordet &quot;pant&quot; i produktnamnet och en kund söker efter &quot;byxor&quot;, returneras rätt uppsättning produkter och det enstaka ordet &quot;pant&quot; erbjuds som förslag. Det enstaka ordet&quot;pant&quot; används ofta i modebranschen och ibland i detaljhandeln, även om pluralformen&quot;byxor&quot; används oftare i vissa områden. (Ordet&quot;gnagare&quot; avser tekniskt sett den del av ett plagg som täcker ett ben, vilket är orsaken till att du behöver ett &quot;byxpar&quot; för att täcka båda benen.)

### Konsekvens

Se till att terminologin används på samma sätt i katalogen. Tänk på att det kan finnas regionala skillnader i användning och ibland skillnader inom en bransch.
