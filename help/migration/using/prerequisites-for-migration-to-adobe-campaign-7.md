---
product: campaign
title: Adobe Campaign 7으로 마이그레이션하기 위한 사전 요구 사항
description: Adobe Campaign 7으로 마이그레이션하기 위한 사전 요구 사항
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# Adobe Campaign 7으로 마이그레이션하기 위한 사전 요구 사항{#prerequisites-for-migration-to-adobe-campaign}

![](../../assets/v7-only.svg)

마이그레이션을 실행하기 전에 다음을 참조하십시오. [마이그레이션을 시작하기 전](../../migration/using/before-starting-migration.md) 및 [플랫폼 구성](../../migration/using/configuring-your-platform.md) 섹션에 자세히 설명되어 있습니다.

v6.02에서 Adobe Campaign v7로 마이그레이션할 때 미리 배달된 일부 파일이 배달되지 않습니다.

클라이언트 오류가 표시되면 대시보드를 새 Adobe Campaign v7 코드로 업데이트하거나 v6.02 인스턴스에서 v7 인스턴스로 다음 파일을 수동으로 복사해야 합니다.

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
