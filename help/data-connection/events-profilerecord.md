---
title: Profilposter
description: Lär dig vilka data en profilpost hämtar.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# [!DNL Data Connection] Profilposter

Nedan beskrivs de registerdata för Commerce-profiler som är tillgängliga när du installerar [!DNL Data Connection] tillägg. Data i profilposter skickas till Adobe Experience Platform.

## Profilpost

Profilpostuppdateringar är tillgängliga i Experience Platform när en ny profil skapas, uppdateras eller tas bort.

### Data som samlats in från profilpost

Nedan beskrivs de data som hämtas för en profilpost.

| Fält | Beskrivning |
|---|---|
| `channel` | Innehåller information om datakällan för data. Båda `_id` och `_type` innehåller [namnutrymmesvärden](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | Kanalens unika identifierare, till exempel `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifierar kanaldatakällan, till exempel `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Innehåller information om kunden. |
| `person.name` | Innehåller information om kundens namn. |
| `person.name.firstName` | Innehåller kundens förnamn. |
| `person.name.lastName` | Innehåller kundens efternamn. |
| `person.birthDate` | Köparens födelsedatum. |
| `personalEmail` | En personlig e-postadress. |
| `personalEmail.address` | Den tekniska adressen, till exempel `name@domain.com` som det definieras vanligen i RFC2822 och senare standarder. |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar. |
| `userAccount.startDate` | Det datum då profilen skapades för första gången. |

>[!NOTE]
>
>Varje profilpost innehåller även [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) -fält, som innehåller kundens e-postadress, när den är tillgänglig, och ECID.

Lär dig hur [skapa ett profilpostspecifikt schema](profile-data.md) som kan importera data från dina profilposter.
