---
title: Onboarding
description: Läs om kraven och vilka plattformar som stöds i [!DNL Product Recommendations].
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Onboarding

Startprocessen för [!DNL Product Recommendations] kräver åtkomst till serverns kommandorad och består av följande steg. Om du inte är van vid att arbeta via kommandoraden ber du en utvecklare eller systemintegratör att hjälpa till.

- [Implementeringsarbetsflöde](implementation-workflow.md)
- [Installera och konfigurera](install-configure.md)
- [Inställningar](settings.md)
- [Verifiera](verify.md)
- [Mellanlagringsmiljö](staging-environment.md)

## Krav

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3/7.4
- Disposition

### Plattformar som stöds

- Adobe Commerce on prem (EE): 2.4.x
- Adobe Commerce on Cloud (ECE): 2.4.x

### Stöd för Page Builder

[!DNL Product Recommendations] kan läggas till på en sida som en Page Builder-innehållstyp. Information om hur du lägger till stöd för Page Builder i Recommendations finns i [Installera och konfigurera](install-configure.md).

### Stöd för B2B {#b2bsupport}

B2B-butiker kräver ofta komplex logik som styr synlighet och pris för varje kund eller kundgrupp. [!DNL Product Recommendations] nu [support](release-notes.md) den här funktionaliteten genom att [kategoribehörigheter](https://docs.magento.com/user-guide/catalog/category-permissions.html), [delade kataloger](https://docs.magento.com/user-guide/catalog/catalog-shared.html)och [kundgruppsspecifik prissättning](https://docs.magento.com/user-guide/catalog/pricing-advanced.html). Om du t.ex. har dolt vissa kategorier i kundsegmentet för detaljhandeln visas inte rekommendationer för produkter i dessa kategorier för en kund i det segmentet. När du definierar en delad katalog för specifika kundgrupper och företag ser de kunderna rekommendationer enbart för de produkter de har tillgång till. Alla rekommenderade produkter återspeglar korrekt kundgruppsspecifikt pris baserat på varje kunds kundgrupp.
