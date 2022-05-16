---
title: '"Typer av ansikten"'
description: '"[!DNL Live Search] är dynamiska och visas i filterlistan när det är relevant."'
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# Typer av ansikten

Alla [!DNL Live Search] är dynamiska och visas i *Filter* endast i tillämpliga fall. Listan över tillgängliga facets ändras beroende på vilka produkter som returneras. Följande egenskaper påverkar deras presentation och beteende:

* Fastnålade ansikten - De vanligaste ansiktena kan fästas överst i listan. De återstående faktorerna listas i *Sorteringstyp* beställa efter de fästa ansiktena.
* Intelligenta aspekter - produktattribut som [Adobe Sensei](https://www.adobe.com/sensei.html) hittar mest relevanta för en produktuppsättning och fråga. Beräkningen tar hänsyn till attributmetadata för hela katalogen och fastställer vid frågans tidpunkt de mest relevanta aspekterna.
* Populära aspekter - Produktattribut som oftast förekommer i sökresultat.
* Prisfaktorer - Returprodukter efter prisintervall. Du kan ange antalet val och prisintervallet på [*Inställningar*](settings.md) -fliken.

Vid frågetiden, [!DNL Live Search] genererar sökresultaten i grupper med intelligenta och populära aspekter.

![Fasetter - pris](assets/storefront-search-results-run-price.png)

## Alternativ för Stock-front och headless

Ansikten som återges för [!DNL Commerce] storefront bearbetas av sökadaptern, som dirigerar begäranden och återger resultaten i butiken. Alla [!DNL Commerce] storefront-ansikten sorteras i bokstavsordning med alternativ för en enstaka markering, oavsett vilken indatatyp som tilldelats motsvarande attribut. Ansikten som är tillgängliga i butiken återges enligt det aktuella temat och återspeglar eventuella anpassningar av presentationen av lagerstyrd navigering.

I motsats till [headless](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/webapi-vision.html) implementeringar behandlas av API:t och har stöd för ytterligare alternativ. Headless-aspekter kan sorteras alfabetiskt eller efter antal och kan ha antingen en- eller flervalsalternativ.

### Välj typ

För headless-implementeringar kan facets definieras som `single select` eller `multi-select` med logiska operatorer som bestämmer den returnerade produktuppsättningen. Till exempel: `green AND blue` eller `green OR blue`.

![Ansikten - Välj typ](assets/facets-select-type.png)

| Välj typ | Beskrivning |
|--- |--- |
| Enkelt val | Ett enskilt val ger flera alternativ, men låter kunden välja endast ett värde. |
| Flera val (eller) | (Endast Headless) Shoppare kan välja mer än ett alternativ och returnerade produkter kan matcha vilket värde som helst. Exempel: `green OR blue` |
| Flera val (och) | (Endast Headless) Shoppare kan välja mer än ett alternativ, och returnerade produkter måste matcha alla valda värden. Exempel: `green AND blue` |

### Fasettetiketter

För [!DNL Commerce] storefronts, ansiktsetiketten bestäms av [*Attributegenskaper*](https://docs.magento.com/user-guide/stores/attribute-product-create.html). För butiker med flera vyer kan ytterligare etiketter definieras under *Hantera etiketter*. För headless-implementeringar redigeras etiketter från [arbetsyta för ansikten](faceting-workspace.md).

### Sorteringstyp

Alla ansikten som återges för butiken sorteras i alfabetisk ordning. För headless-implementationer kan ansiktena sorteras i bokstavsordning eller efter antal.

| Sorteringstyp | Beskrivning |
|--- |--- |
| Alfabetiskt | I butiken *Filter* -lista sorteras fasetterna i alfabetisk ordning. |
| Antal | (Endast Headless) För headless-implementationer kan facets också sorteras efter antalet värden som finns per facet i den aktuella uppsättningen returnerade produkter. |
