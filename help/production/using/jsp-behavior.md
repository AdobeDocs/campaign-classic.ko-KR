---
product: campaign
title: JSP 동작
description: JSP 동작
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
TQID: https://experienceleague.adobe.com/IQSjBaSbnZcsqs0glv8z1aIwOBbtVO2roeXlJiYgEfo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 66
ht-degree: 36%

---

# JSP 동작{#jsp-behavior}



특정 **jsp** 작업이 성공적으로 실행되지 않은 경우 강제로 다시 컴파일해야 합니다.

이에 대해 다음 명령을 입력합니다.

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

다음에 연결할 때 **jsp** 작업이 다시 생성됩니다.
