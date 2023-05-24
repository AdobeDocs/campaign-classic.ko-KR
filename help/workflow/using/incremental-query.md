---
product: campaign
title: 증분 쿼리
description: 증분 쿼리 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# 증분 쿼리{#incremental-query}



증분 쿼리를 사용하면 이 기준에 이미 타겟팅된 사람은 제외하면서 기준에 따라 정기적으로 타겟을 선택할 수 있습니다.

이미 타겟팅된 모집단은 워크플로우 인스턴스 및 활동별로 메모리에 저장됩니다. 즉, 동일한 템플릿에서 시작된 두 개의 워크플로우가 동일한 로그를 공유하지 않습니다. 반면, 동일한 워크플로 인스턴스에 대해 동일한 증분 쿼리를 기반으로 하는 두 개의 작업은 동일한 로그를 사용합니다.

쿼리는 표준 쿼리와 동일한 방식으로 정의되지만 실행이 예약됩니다.

**관련 항목:**

* [사용 사례: 증분 쿼리를 사용한 분기별 목록 업데이트](quarterly-list-update.md)
* [쿼리 만들기](query.md#creating-a-query)

>[!CAUTION]
>
>증분 쿼리의 결과가 다음과 같은 경우 **0** 실행 중 하나에서 쿼리가 다음에 프로그래밍될 때까지 워크플로가 일시 중지됩니다. 따라서 증분 쿼리 다음에 오는 전환 및 활동은 다음 실행 전에 처리되지 않습니다.

방법은 다음과 같습니다.

1. 다음에서 **[!UICONTROL Scheduling & History]** 탭에서 **[!UICONTROL Schedule execution]** 옵션을 선택합니다. 작업은 일단 생성되면 활성 상태로 유지되며, 쿼리 실행 일정에서 지정한 시간에만 트리거됩니다. 그러나 이 옵션이 비활성화되면 쿼리가 즉시 실행됩니다 **한 번에**.
1. **[!UICONTROL Change]** 버튼을 클릭합니다.

   다음에서 **[!UICONTROL Schedule editing wizard]** 창에서 빈도 유형, 이벤트 반복 및 이벤트 유효 기간을 구성할 수 있습니다.

   ![](assets/s_user_segmentation_wizard_11.png)

1. 클릭 **[!UICONTROL Finish]** 일정을 저장합니다.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. 의 하위 섹션 **[!UICONTROL Scheduling & History]** 탭에서는 기록에서 고려할 일 수를 선택할 수 있습니다.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      이미 타겟팅된 수신자는 타겟팅된 날로부터 최대 일 수를 기록할 수 있습니다. 이 값이 0이면 수신자는 로그에서 삭제되지 않습니다.

   * **[!UICONTROL Keep history when starting]**

      이 옵션을 사용하면 활동이 활성화된 경우 로그를 제거할 수 없습니다.

   * **[!UICONTROL SQL table name]**

      이 매개 변수를 사용하면 내역 데이터가 포함된 기본 SQL 테이블을 오버로드할 수 있습니다.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 세트는 쿼리의 타겟팅된 모집단을 식별합니다. **[!UICONTROL tableName]** 는 대상 식별자를 기록하는 테이블의 이름입니다. **[!UICONTROL schema]** 모집단의 스키마(일반적으로 nms:recipient)이며, **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.
