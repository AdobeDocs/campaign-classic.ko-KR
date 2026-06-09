---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
TQID: https://experienceleague.adobe.com/Xq9y8r6xU-hypq1Eeo9ijaiGng7qqkWVqiCXW5fYx2c
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
feature_v2: []
subfeature_v2:
  - id: e5e477db-ebc7-4368-ab0f-4d8fc2aed405
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
source-git-commit: a35dcdddded4483beefc126ee3d603bab36bf9c9
workflow-type: tm+mt
source-wordcount: 415
ht-degree: 93%

---

# 최신 릴리스 {#latest-release}

이 페이지에서는 **최신 Campaign v7 릴리스**&#x200B;의 새로운 기능, 개선 사항 및 버그 해결 사항 목록을 확인할 수 있습니다. 모든 새 빌드는 색상으로 상태가 표시됩니다. [이 페이지](rn-overview.md)에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오.

## 릴리스 7.4.3 {#release-7-4-3}

### 빌드 9396 {#build-9396}

[!BADGE 일반 가용성]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}

_2026년 6월 9일_

이 빌드에는 보안 수정 사항이 포함되어 있습니다. 권장되는 일반 가용성 빌드이며 이전 Campaign Classic v7 빌드를 대체합니다.

### 빌드 9394 {#build-9394}

[!BADGE 사용되지 않음]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="사용되지 않음"}

>[!CAUTION]
>
> 클라이언트 콘솔 업그레이드는 필수입니다.

_2026년 3월 31일_

#### 보안 개선 사항 {#security-7-4-3}

* 최적의 보안, 안정성, 규정 준수를 유지하기 위해 Debian은 버전 13으로, PostgreSQL은 버전 17로 업그레이드되었습니다. [호환성 매트릭스](compatibility-matrix.md)를 참조하십시오.

#### 해결 사항 {#fixes-7-4-3}

>[!NOTE]
>
> 아래 목록의 해결 사항은 연속되는 7.4.3 빌드에서 점진적으로 롤아웃되었습니다. **[!UICONTROL Help > About...]** [메뉴](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)로 이동하여 최신 9394@28aaec9 빌드가 설치되어 있는지 확인하십시오. 자세한 내용은 Adobe 담당자에게 문의하십시오.

* 바코드 구성 요소에서 제한 없는 높이 매개 변수를 허용하여 보안 취약성이 발생할 수 있는 문제를 해결했습니다. (NEO-89984)
* 워크플로를 통해 만든 목록의 열거형 필드에 임시 이름 속성이 누락되어 인터페이스에 잘못되거나 빈 열거형 레이블이 표시되는 문제를 해결했습니다. (NEO-91158)
* 중복 제거 활동이 있는 워크플로에서 targetData 필드를 사용할 때 개인화 오류로 게재 준비가 실패하는 문제를 해결했습니다. (NEO-87693)
* 유형 변환 요구 사항으로 인해 PostgreSQL 15에서 단일 문자 문자열 필드를 다른 문자열과 연결하지 못하는 문제를 해결했습니다. (NEO-88028)
* 상위 및 하위 게재 ID가 일치하지 않아 [분산 마케팅]의 공동 작업 캠페인에 대한 추적 로그가 데이터베이스에 기록되지 않는 문제를 해습니다. (NEO-86836)
* 메시지가 정상적으로 전송되었는데도 게재 로그에는 취소된 것으로 표시되며, 특히 일괄 처리 예약에 영향을 주던 문제를 해결했습니다. (NEO-78933)
* 데이터베이스 정리 워크플로가 성능에 영향을 줄 수 있는 데이터를 효율적으로 삭제하지 못하던 문제를 해결했습니다. (NEO-76439)

<!-- BUILD 7.0.9394.28aaec9 -->

* 일부 게재에 대해 게재 통계가 완전히 다시 계산되지 않고, 특히 성공 지표에 영향을 미치는 문제를 해결했습니다. (NEO-88106) <!-- moved from original 7.4.3 GA Fixes section -->
* 누락된 업스트림 타기팅 스키마를 참조하는 특정 워크플로를 열 때 클라이언트 콘솔이 충돌할 수 있는 문제를 해결했습니다. (NEO-28727)
* 설치 패키지에서 버전 파일이 누락되어 시작이 실패한 후 클라이언트 콘솔 버전을 식별할 수 없는 문제를 해결했습니다. (NEO-94798)

<!--
other fixes - ommitted from release notes

Internal/non-customer-facing:

* Fixed an internal DevOps build race condition when copying the `teradata_timezones.txt` file during build packaging. (NEO-66532) — internal only; the Jira description states "No impact for customers: either it builds (99.9% of the time) or it does not."
* Fixed an internal CI/CD issue where AWS CodeBuild jobs could fail randomly on EC2 Docker containers when copying files during build. (NEO-90823) — internal CI/CD infrastructure only

Customer-specific hotfixes:

* Fixed an issue where coupon assignment could fail during delivery message preparation due to a SQL syntax error when looking up coupon codes. (NEO-92857) — Verizon only
* Fixed an issue where the error count and status in the `nms:address` table were not consistently updated on the marketing server after recurring soft bounces, causing recipients to not be quarantined as expected even though they were correctly flagged on the mid-sourcing server. (NEO-94422) — Walgreens only
-->

