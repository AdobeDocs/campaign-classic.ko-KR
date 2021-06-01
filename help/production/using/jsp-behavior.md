---
product: campaign
title: JSP 동작
description: JSP 동작
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP 동작{#jsp-behavior}

특정 **jsp** 작업이 성공적으로 실행되지 않은 경우 강제로 다시 컴파일해야 합니다.

이렇게 하려면 다음 명령을 입력합니다.

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

다음에 연결할 때 **jsp** 작업이 다시 생성됩니다.
