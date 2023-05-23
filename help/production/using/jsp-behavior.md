---
product: campaign
title: JSP 동작
description: JSP 동작
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP 동작{#jsp-behavior}



확실한 경우 **jsp** 작업이 성공적으로 실행되지 않았습니다. 다시 컴파일해야 합니다.

이에 대해 다음 명령을 입력합니다.

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

다음 **jsp** 다음에 연결하면 작업이 다시 생성됩니다.
