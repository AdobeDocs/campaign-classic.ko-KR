---
product: campaign
title: 증분 쿼리
description: 증분 쿼리 워크플로우 활동에 대해 자세히 알아보기
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# 증분 쿼리{#incremental-query}

![](../../assets/v7-only.svg)

증분 쿼리를 사용하면 이 기준에 이미 타깃팅된 사용자를 제외하고 기준에 따라 대상을 주기적으로 선택할 수 있습니다.

이미 타겟팅된 모집단은 워크플로우 인스턴스와 활동별로 메모리에 저장됩니다. 즉, 동일한 템플릿에서 시작된 두 개의 워크플로우는 동일한 로그를 공유하지 않습니다. 반면 동일한 워크플로우 인스턴스에 대해 동일한 증분 쿼리를 기반으로 하는 두 작업은 동일한 로그를 사용합니다.

쿼리는 표준 쿼리와 동일한 방식으로 정의되지만 실행이 예약됩니다.

**관련 항목:**

* [사용 사례: 증분 쿼리를 사용한 분기별 목록 업데이트](quarterly-list-update.md)
* [쿼리 만들기](query.md#creating-a-query)

>[!CAUTION]
>
>증분 쿼리 결과가 다음과 같은 경우 **0** 실행 중 하나에서 워크플로우가 일시 중지되어 쿼리의 다음 프로그램 실행까지 일시 중지됩니다. 따라서 증분 쿼리를 따르는 전환 및 활동은 다음 실행 전에 처리되지 않습니다.

방법은 다음과 같습니다.

1. 에서 **[!UICONTROL Scheduling & History]** 탭에서 을 선택합니다 **[!UICONTROL Schedule execution]** 선택 사항입니다. 작업은 일단 생성되면 활성 상태로 유지되며 쿼리 실행 일정에 의해 지정된 시에만 트리거됩니다. 그러나 이 옵션을 비활성화하면 쿼리가 즉시 실행됩니다 **한 번에**.
1. **[!UICONTROL Change]** 버튼을 클릭합니다.

   에서 **[!UICONTROL Schedule editing wizard]** 창에서 빈도, 이벤트 되풀이 및 이벤트 유효 기간의 유형을 구성할 수 있습니다.

   ![](assets/s_user_segmentation_wizard_11.png)

1. 클릭 **[!UICONTROL Finish]** 일정을 저장합니다.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 의 하위 섹션 **[!UICONTROL Scheduling & History]** 탭에서 내역에서 고려할 일 수를 선택할 수 있습니다.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      이미 타겟팅한 수신자는 타겟팅한 날로부터 최대 일 수를 기록할 수 있습니다. 이 값이 0이면 수신자는 로그에서 제거되지 않습니다.

   * **[!UICONTROL Keep history when starting]**

      이 옵션을 사용하면 활동이 활성화될 때 로그를 삭제할 수 없습니다.

   * **[!UICONTROL SQL table name]**

      이 매개 변수를 사용하면 기록 데이터가 포함된 기본 SQL 테이블을 오버로드할 수 있습니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 쿼리의 타겟팅된 모집단을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름입니다. **[!UICONTROL schema]** 는 모집단의 스키마(일반적으로 nms:recipient)이며 **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.
