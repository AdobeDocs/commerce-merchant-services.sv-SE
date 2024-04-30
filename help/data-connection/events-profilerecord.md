---
title: Profilposter
description: Lär dig vilka data en profilpost hämtar.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: 89607d22ba8e69e0c98fce97e041022e33d01c07
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# [!DNL Data Connection] Profilposter (beta)

Följande beskriver vilka data i profilposten för Commerce som är tillgängliga när du installerar [!DNL Data Connection] tillägg. Data i profilposter skickas till Adobe Experience Platform.

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
| `billingAddress` | Den fakturerande postadressen. |
| `billingAddress.street1` | Primär information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn. |
| `billingAddress.street2` | Ytterligare gatuinformation, andra raden. |
| `billingAddress.city` | Namnet på staden. |
| `billingAddress.state` | Namnet på läget. Det här är ett frihandsfält. |
| `billingAddress.country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `billingAddressPhone` | Telefonnumret som är associerat med faktureringsadressen. |
| `billingAddressPhone.number` | Telefonnumret. Observera att telefonnumret är en sträng och kan innehålla meningsfulla tecken som hakparenteser `()`, bindestreck `-`, eller tecken som anger underuppringningsidentifierare som tillägg `x` till exempel  `1-353(0)18391111` eller `+613 9403600x1234`. |
| `shippingAddress` | Leveransadress. |
| `shippingAddress.street1` | Primär information om gatuminivå, lägenhetsnummer, gatunummer och gatunamn. |
| `shippingAddress.street2` | Ytterligare gatuinformation, andra raden. |
| `shippingAddress.city` | Namnet på staden. |
| `shippingAddress.state` | Namnet på läget. Det här är ett frihandsfält. |
| `shippingAddress.country` | Namnet på det statligt administrerade territoriet. Annan än `xdm:countryCode`är det ett friformsfält som kan ha landsnamnet på vilket språk som helst. |
| `shippingAddressPhone` | Telefonnummer som är associerat med leveransadressen. |
| `shippingAddressPhone.number` | Telefonnumret. Observera att telefonnumret är en sträng och kan innehålla meningsfulla tecken som hakparenteser `()`, bindestreck `-`, eller tecken som anger underuppringningsidentifierare som tillägg `x` till exempel  `1-353(0)18391111` eller `+613 9403600x1234`. |
| `userAccount` | Anger information om lojalitet, inställningar, inloggningsprocesser och andra kontoinställningar. |
| `userAccount.startDate` | Det datum då profilen skapades för första gången. |

>[!NOTE]
>
>Varje profilpost innehåller även [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) som innehåller det systemgenererade kund-ID:t för Commerce som primär identifierare för profilen och ett e-post-ID som används som en sekundär identifierare.

Lär dig hur [skapa ett profilpostspecifikt schema](profile-data.md) som kan importera data från dina profilposter.
