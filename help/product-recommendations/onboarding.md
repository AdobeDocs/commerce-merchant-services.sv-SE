---
title: Onboarding
description: Läs om kraven och vilka plattformar som stöds i [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '276'
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

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Disposition 2

### Plattformar som stöds

- Adobe Commerce On Premise (EE): 2.4.4+
- Adobe Commerce on Cloud (ECE): 2.4.4+

## Slutpunkt

[!DNL Product Recommendations] kommunicerar via slutpunkten vid `https://catalog-service.adobe.io/graphql`.

### Stöd för Page Builder

[!DNL Product Recommendations] kan läggas till på en sida som en Page Builder-innehållstyp. Information om hur du lägger till stöd för Page Builder i Recommendations finns i [Installera och konfigurera](install-configure.md).

Se [[!DNL Page Builder] Integrering](page-builder.md) för instruktioner om hur du lägger till [!DNL Product Recommendations] till [!DNL Page Builder] innehåll.

### SaaS-prisindexering

Produktrekommendationskunder kan använda [SaaS-prisindexering](../price-index/price-indexing.md), som ger snabbare prisändringar och synkroniseringstid.

### Stöd för B2B {#b2bsupport}

B2B-butiker kräver ofta komplex logik som styr synlighet och pris för varje kund eller kundgrupp. [!DNL Product Recommendations] nu [support](release-notes.md) den här funktionen genom att [kategoribehörigheter](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [delade kataloger](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)och [kundgruppsspecifik prissättning](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Om du t.ex. har dolt vissa kategorier i kundsegmentet för detaljhandeln visas inte rekommendationer för produkter i dessa kategorier för en kund i det segmentet. När du definierar en delad katalog för specifika kundgrupper och företag ser kunderna rekommendationer endast för produkter de har tillgång till. Alla rekommenderade produkter återspeglar korrekt kundgruppsspecifikt pris baserat på varje kunds kundgrupp.

>[!NOTE]
>
>Merchants kan anpassa och utöka widgetar och butikselement med hjälp av [Katalogtjänst](../catalog-service/overview.md) Storefront API, men alla anpassningar är utanför Adobe support-teamets räckvidd.
