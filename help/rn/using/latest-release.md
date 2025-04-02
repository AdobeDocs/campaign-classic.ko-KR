---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 86bc3bdfe628cc694e47a4670e99225e05b3df1b
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 100%

---

# 최신 릴리스 {#latest-release}

이 페이지에서는 **최신 Campaign v7 릴리스**&#x200B;의 새로운 기능, 개선 사항 및 버그 해결 사항 목록을 확인할 수 있습니다. 모든 새 빌드는 색상으로 상태가 표시됩니다. [이 페이지](rn-overview.md)에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오.

## 릴리스 7.4.2 - 빌드 9390 {#release-7-4-2}

[!BADGE 일반 공급]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}

_2025년 4월 2일 목요일_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### 보안 개선 사항 {#security-7-4-2}

이 릴리스에서는 여러 보안 문제를 해결합니다.

보안을 강화하기 위해 **[!UICONTROL Adobe Experience Cloud]** 외부 계정을 통한 Adobe 솔루션 및 앱 연결을 업데이트했습니다.

### 해결 사항 {#release-7-4-2-fixes}

이 릴리스에서는 다음과 같은 주요 문제가 해결되었습니다.

* TLS/SMPP 연결 - SMPP 안정성 문제를 해결했습니다.

* Google BigQuery 문제 해결:

   * 부울 데이터 유형에 대한 회귀 문제를 해결했습니다.
   * 프록시 설정 문제를 해결했습니다.
   * DATETIME 데이터 유형에 대한 회귀 문제를 해결했습니다.
   * 대량 로드 안정성 문제를 해결했습니다.
   * ODBC 버전에 대한 내부 테스트를 개선했습니다.
   * 연결 문자열의 특수 문자에 발생하는 문제를 해결했습니다.
   * Google BigQuery 쿼리에서 기본 시간 제한(5분)을 제거했습니다.

* 메일 전송 에이전트(MTA) - 분리된 MTA 하위 요소가 **[!UICONTROL Start pending]** 상태에서 중단되는 문제를 해결했습니다.

이 릴리스에서는 다음 문제도 해결합니다.

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150

