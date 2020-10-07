---
title: Adobe Campaign 7으로 마이그레이션하기 위한 사전 요구 사항
seo-title: Adobe Campaign 7으로 마이그레이션하기 위한 사전 요구 사항
description: Adobe Campaign 7으로 마이그레이션하기 위한 사전 요구 사항
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 27%

---


# Adobe Campaign 7으로 마이그레이션하기 위한 사전 요구 사항{#prerequisites-for-migration-to-adobe-campaign}

마이그레이션을 실행하기 전에 마이그레이션을 시작하기 [전](../../migration/using/before-starting-migration.md) 및 플랫폼 [구성 섹션을](../../migration/using/configuring-your-platform.md) 참조하십시오.

v6.02에서 Adobe Campaign v7으로 마이그레이션할 때 미리 제공된 일부 파일이 배달되지 않습니다.

클라이언트 오류가 나타나면 새 Adobe Campaign v7 코드로 대시보드를 업데이트하거나 v6.02 인스턴스의 v7 인스턴스로 다음 파일을 수동으로 복사해야 합니다.

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
