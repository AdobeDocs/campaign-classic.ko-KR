---
solution: Campaign Classic
product: campaign
title: JSP 동작
description: JSP 동작
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---


# JSP 동작{#jsp-behavior}

특정 **jsp** 작업이 성공적으로 실행되지 않으면 강제로 다시 컴파일해야 합니다.

이 경우 다음 명령을 입력합니다.

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

다음에 연결할 때 **jsp** 작업이 다시 생성됩니다.
