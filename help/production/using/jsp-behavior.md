---
title: JSP 동작
seo-title: JSP 동작
description: JSP 동작
seo-description: null
page-status-flag: never-activated
uuid: b9e9f348-968c-46e0-8340-df1f1fcaf3a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 5dcc4090-effe-479e-8d5c-67e6a6542fbb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# JSP 동작{#jsp-behavior}

특정 **jsp** 작업이 성공적으로 실행되지 않으면 다시 컴파일해야 합니다.

이 경우 다음 명령을 입력합니다.

```
nlserver stop web
cd nl6/tomcat-7
rm -r work/
nlserver start web
```

다음에 연결할 때 **jsp** 작업이 다시 생성됩니다.
