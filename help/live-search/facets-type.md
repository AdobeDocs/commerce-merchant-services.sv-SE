---
title: "Typer av ansikten"
description: "[!DNL Live Search] är dynamiska och visas i filterlistan när det är relevant."
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: f96f94a16e1926b7dd2f1ee94f124ac0c823a9e0
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Typer av ansikten

[!DNL Live Search] använder en mängd olika ansiktstyper och de visas i *Filter* endast i tillämpliga fall. Listan över tillgängliga facets ändras beroende på vilka produkter som returneras. Följande egenskaper påverkar deras presentation och beteende:

* Fastnålade ansikten - De vanligaste ansiktena kan fästas överst i listan. De återstående faktorerna listas i *Sorteringstyp* beställa efter de fästa ansiktena.
* Dynamiska aspekter - produktattribut som [Adobe Sensei](https://www.adobe.com/sensei.html) hittar mest relevanta för en produktuppsättning och fråga. Beräkningen tar hänsyn till attributmetadata för hela katalogen och fastställer vid frågans tidpunkt de mest relevanta aspekterna.
* Populära aspekter - Produktattribut som oftast förekommer i sökresultat.
* Prisfaktorer - Returprodukter efter prisintervall. Du kan ange antalet val och prisintervallet på [*Inställningar*](settings.md) arbetsyta.

Vid frågetiden, [!DNL Live Search] genererar sökresultaten i grupper med dynamiska och populära aspekter.

![Fasetter - pris](assets/storefront-search-results-run-price.png)

## Alternativ för Stock-front och headless

Ansikten som återges för [!DNL Commerce] storefront bearbetas av sökadaptern, som dirigerar begäranden och återger resultaten i butiken. Alla [!DNL Commerce] storefront-ansikten sorteras i bokstavsordning med alternativ för en enstaka markering, oavsett vilken indatatyp som tilldelas till motsvarande attribut. Ansikten som är tillgängliga i butiken återges enligt det aktuella temat och återspeglar eventuella anpassningar av presentationen av lagerstyrd navigering.

I motsats till [headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) implementeringar behandlas av API:t och har stöd för ytterligare alternativ. Headless-aspekter kan sorteras alfabetiskt eller efter antal och kan ha antingen en- eller flervalsalternativ.

### Fasettetiketter

För [!DNL Commerce] storefronts, ansiktsetiketten bestäms av [*Attributegenskaper*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). För butiker med flera vyer kan ytterligare etiketter definieras under *Hantera etiketter*. För headless-implementeringar redigeras etiketter från [arbetsyta för ansikten](faceting-workspace.md).

### Sorteringstyp

Alla ansikten som återges för butiken sorteras i alfabetisk ordning. För headless-implementationer kan ansiktena sorteras i bokstavsordning eller efter antal.

| Sorteringstyp | Beskrivning |
|--- |--- |
| Alfabetiskt | I butiken *Filter* -lista sorteras fasetterna i alfabetisk ordning. |
| Antal | (Endast Headless) För headless-implementationer kan facets också sorteras efter antalet värden som finns per facet i den aktuella uppsättningen returnerade produkter. |
