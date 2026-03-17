---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: b9a716f327b8fdd68c3bf36dbe864535308def30
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 28%

---

# 최신 릴리스 {#latest-release}

이 페이지에서는 **최신 Campaign v7 릴리스**&#x200B;의 새로운 기능, 개선 사항 및 버그 해결 사항 목록을 확인할 수 있습니다. 모든 새 빌드는 색상으로 상태가 표시됩니다. [이 페이지](rn-overview.md)에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오.

## 릴리스 7.4.3 - 빌드 9394 {#release-7-4-3}

[!BADGE 일반 공급]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="일반 공급"}

_2026년 3월 16일 화요일_

>[!CAUTION]
>
> 클라이언트 콘솔 업그레이드는 필수입니다.

### 보안 개선 사항 {#security-7-4-3}

* 최적의 보안, 안정성 및 규정 준수를 유지하기 위해 Debian은 버전 13으로, PostgreSQL은 버전 17로 업그레이드되었습니다. [호환성 매트릭스](compatibility-matrix.md)를 참조하세요.

### 수정 사항 {#fixes-7-4-3}

* 바코드 구성 요소에서 경계 없는 높이 매개 변수를 허용하여 보안 취약성이 발생할 수 있는 문제를 수정했습니다. (NEO-89984)
* 워크플로우를 통해 만든 목록의 열거형 필드에 임시 이름 속성이 누락되어 인터페이스에 잘못되거나 빈 열거형 레이블이 표시되는 문제를 해결했습니다. (NEO-91158)
* 일부 게재에 대해 게재 통계가 완전히 다시 계산되지 않고, 특히 성공 지표에 영향을 미치는 문제를 해결했습니다. (NEO-88106)
* 중복 제거 활동이 있는 워크플로우에서 targetData 필드를 사용할 때 개인화 오류로 게재를 준비하지 못하던 문제를 수정했습니다. (NEO-87693)
* 유형 캐스팅 요구 사항으로 인해 PostgreSQL 15에서 단일 문자 문자열 필드를 다른 문자열과 연결하지 못하는 문제를 해결했습니다. (NEO-88028)
* 상위 및 하위 게재 ID가 일치하지 않아 분산 마케팅의 공동 작업 캠페인에 대한 추적 로그가 데이터베이스에 기록되지 않는 문제가 해결되었습니다. (NEO-86836)
* 정상적으로 전송되었는데도 게재 로그에 메시지가 취소된 것으로 표시되는 문제가 해결되었습니다. 특히 예약된 일괄 처리에 영향을 주는 문제가 해결되었습니다. (NEO-78933)
* 데이터베이스 정리 워크플로우가 성능에 영향을 줄 수 있는 데이터를 효율적으로 삭제하지 못하던 문제를 해결했습니다. (NEO-76439)

