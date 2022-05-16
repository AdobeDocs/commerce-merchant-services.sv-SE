---
title: '"Tekniska regelanteckningar"'
description: '"Teknisk information om att använda [!DNL Live Search] regler."'
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 0%

---

# Tekniska anteckningar för regel

[!DNL Live Search] regler utlöser åtgärder baserat på ett antal frågevillkor och ger säljarna möjlighet att forma sökupplevelsen för olika scenarier.

Den aktuella versionen av [!DNL Live Search] regler baseras på frågesträngen som anges av användaren, i stället för på uppsättningen returnerade resultat. En frågesträng kan innehålla alfanumeriska tecken och gemener/versaler ignoreras. Precis som för aspekter och synonymer lagras regler i `protobuf dynamo`. Vid frågetiden hämtar söktjänsten regler via `grpc` samtal till `search-admin-service`.
