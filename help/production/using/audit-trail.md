---
product: campaign
title: 감사 추적
description: Campaign 감사 추적을 통해 인스턴스를 모니터링하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Audit Trail, Monitoring
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 3%

---

# 감사 추적{#audit-trail}



Adobe Campaign에서 **[!UICONTROL Audit trail]** 인스턴스 내에서 수행된 전체 변경 내역에 액세스할 수 있습니다.

**[!UICONTROL Audit trail]** 은(는) Adobe Campaign 인스턴스 내에서 발생하는 작업 및 이벤트의 포괄적인 목록을 실시간으로 캡처합니다. 여기에는 다음과 같은 질문에 답변할 수 있도록 데이터 기록에 액세스하는 셀프서비스 방법이 포함되어 있습니다. 워크플로우가 어떻게 되었고 마지막으로 업데이트한 사람 또는 인스턴스에서 사용자가 수행한 작업이 변경되었습니다.

>[!NOTE]
>
>Adobe Campaign은 사용자 권한, 템플릿, 개인화 또는 캠페인 내에서 수행된 변경 사항을 감사하지 않습니다.\
>감사 추적은 인스턴스의 관리자만 관리할 수 있습니다.

감사 추적은 다음 세 가지 구성 요소로 구성됩니다.

* **스키마 감사 추적**: 활동 및 스키마에 대한 마지막 수정 내용을 확인합니다.

   스키마에 대한 자세한 내용은 다음을 참조하십시오 [페이지](../../configuration/using/data-schemas.md).

* **워크플로우 감사 추적**: 워크플로우에 대한 활동 및 마지막 수정 사항을 확인하고 워크플로우의 상태를 확인합니다.

   * 시작
   * 일시 정지
   * 정지
   * 다시 시작
   * 정리 삭제 내역 작업에 해당하는 항목
   * 시뮬레이션 모드에서 시작 작업에 대한 결과를 시뮬레이션합니다.
   * 작업에 해당하는 절전 모드 해제
   * 무조건 정지

   워크플로우에 대한 자세한 내용은 다음을 참조하십시오 [페이지](../../workflow/using/about-workflows.md).

   워크플로우 모니터링 방법에 대한 자세한 내용은 [전용 섹션](../../workflow/using/monitoring-workflow-execution.md).

* **옵션 감사 추적**: 활동 및 선택 사항에 대한 마지막 수정 사항을 확인합니다.

   옵션에 대한 자세한 내용은 다음을 참조하십시오 [페이지](../../installation/using/configuring-campaign-options.md).

## 감사 추적 액세스 {#accessing-audit-trail}

인스턴스의 **[!UICONTROL Audit trail]** :

1. 액세스 권한 **[!UICONTROL Explorer]** 인스턴스 메뉴입니다.
1. 아래에 **[!UICONTROL Administration]** 메뉴, 선택 **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. 다음 **[!UICONTROL Audit trail]** 엔티티 목록이 있는 창이 열립니다. Adobe Campaign은 워크플로우, 옵션 및 스키마에 대한 만들기, 편집 및 삭제 작업을 감사합니다.

   마지막 수정 사항에 대해 자세히 알아보려면 엔티티 중 하나를 선택합니다.

   ![](assets/audit_trail_2.png)

1. 다음 **[!UICONTROL Audit entity]** 선택한 엔티티에 대한 자세한 정보는 다음과 같습니다.

   * **[!UICONTROL Type]** : 워크플로우, 옵션 또는 스키마.
   * **[!UICONTROL Entity]** : 활동의 내부 이름입니다.
   * **[!UICONTROL Modified by]** : 이 엔터티를 마지막으로 수정한 마지막 사용자의 사용자 이름입니다.
   * **[!UICONTROL Action]** : 이 엔터티에 대해 수행된 마지막 작업(생성됨, 편집됨 또는 삭제됨)입니다.
   * **[!UICONTROL Modification date]** : 이 엔터티에 대해 수행된 마지막 작업의 날짜입니다.

   코드 블록은 엔티티에서 정확히 변경된 내용에 대한 자세한 정보를 제공합니다.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>기본적으로 보존 기간은 180일로 설정됩니다 **[!UICONTROL Audit logs]** . 보존 기간을 변경하는 방법에 대한 자세한 내용은 다음을 참조하십시오 [페이지](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## 감사 추적 활성화/비활성화 {#enable-disable-audit-trail}

예를 들어 데이터베이스의 공간을 절약하려는 경우 특정 활동에 대해 감사 추적을 쉽게 활성화하거나 비활성화할 수 있습니다.

방법은 다음과 같습니다.

1. 액세스 권한 **[!UICONTROL Explorer]** 인스턴스 메뉴입니다.
1. 아래에 **[!UICONTROL Administration]** 메뉴, 선택 **[!UICONTROL Platform]** 그런 다음 **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. 활성화/비활성화할 엔티티에 따라 다음 옵션 중 하나를 선택합니다.

   * 워크플로우의 경우: **[!UICONTROL XtkAudit_Workflows]**
   * 스키마의 경우: **[!UICONTROL XtkAudit_DataSchema]**
   * 옵션: **[!UICONTROL XtkAudit_Option]**
   * 모든 엔티티에 대해: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 변경 **[!UICONTROL Value]** 엔티티를 활성화하려면 1을, 비활성일 경우 0을 선택합니다.

   ![](assets/audit_trail_6.png)

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.
