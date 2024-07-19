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
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 14%

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
