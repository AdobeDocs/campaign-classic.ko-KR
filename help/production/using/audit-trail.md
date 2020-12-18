---
solution: Campaign Classic
product: campaign
title: 감사 추적
description: 감사 추적
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---


# 감사 추적{#audit-trail}

Adobe Campaign에서 **[!UICONTROL Audit trail]**&#x200B;을 사용하면 인스턴스 내에서 수행된 변경 사항의 전체 기록에 액세스할 수 있습니다.

**[!UICONTROL Audit trail]** adobe campaign 인스턴스 내에서 발생하는 작업 및 이벤트의 포괄적인 목록을 실시간으로 캡처합니다. 다음과 같은 질문에 대답하는 데 도움이 되는 데이터 기록에 직접 액세스할 수 있는 방법이 포함되어 있습니다.워크플로우가 어떻게 변경되었는지, 마지막으로 업데이트한 사람 또는 사용자가 인스턴스에서 무엇을 했는지 등

>[!NOTE]
>
>Adobe Campaign은 사용자 권한, 템플릿, 개인화 또는 캠페인 내에서 수행된 변경 사항을 감사하지 않습니다.\
>감사 추적은 인스턴스의 관리자만 관리할 수 있습니다.

감사 추적은 다음 3가지 구성 요소로 이루어집니다.

* **스키마 감사 추적**:활동 및 스키마에 대해 마지막으로 수행한 수정 내용을 확인합니다.

   스키마에 대한 자세한 내용은 이 [페이지](../../configuration/using/data-schemas.md)를 참조하십시오.

* **워크플로우 감사 추적**:다음과 같은 워크플로우의 상태를 확인하고 워크플로우에 대해 마지막으로 수정한 내용을 확인합니다.

   * 시작
   * 일시 정지
   * 정지
   * 다시 시작
   * 정리 삭제 내역에 해당하는 작업
   * 시뮬레이션 모드에서 시작 동작과 같은 것을 시뮬레이션합니다.
   * 작업에 해당하는 절전 모드 해제 지금 대기 중인 작업 실행
   * 무조건 정지

   워크플로우에 대한 자세한 내용은 이 [페이지](../../workflow/using/about-workflows.md)를 참조하십시오.

   워크플로우를 모니터링하는 방법에 대한 자세한 내용은 [전용 섹션](../../workflow/using/monitoring-workflow-execution.md)을 참조하십시오.

* **옵션 감사 추적**:활동 및 옵션에 대해 마지막으로 수행한 수정 내용을 확인합니다.

   옵션에 대한 자세한 내용은 이 [페이지](../../installation/using/configuring-campaign-options.md)를 참조하십시오.

## 감사 추적 {#accessing-audit-trail} 액세스

인스턴스의 **[!UICONTROL Audit trail]**&#x200B;에 액세스하려면:

1. 인스턴스의 **[!UICONTROL Explorer]** 메뉴에 액세스합니다.
1. **[!UICONTROL Administration]** 메뉴에서 **[!UICONTROL Audit]** 을 선택합니다.

   ![](assets/audit_trail_1.png)

1. **[!UICONTROL Audit trail]** 창이 개체 목록과 함께 열립니다. Adobe Campaign은 워크플로우, 옵션 및 스키마에 대한 생성, 편집 및 삭제 작업을 감사합니다.

   마지막 수정 사항에 대해 자세히 알아보려면 개체 중 하나를 선택합니다.

   ![](assets/audit_trail_2.png)

1. **[!UICONTROL Audit entity]** 창은 다음과 같은 선택한 엔티티에 대한 자세한 정보를 제공합니다.

   * **[!UICONTROL Type]** :워크플로우, 옵션 또는 스키마.
   * **[!UICONTROL Entity]** :활동의 내부 이름입니다.
   * **[!UICONTROL Modified by]** :이 엔티티를 마지막으로 수정한 최종 사용자의 사용자 이름입니다.
   * **[!UICONTROL Action]** :이 엔티티에 대해 마지막으로 수행한 작업(생성됨, 편집됨 또는 삭제됨)입니다.
   * **[!UICONTROL Modification date]** :이 엔티티에 대해 마지막으로 수행한 작업의 날짜입니다.

   코드 블록은 엔티티에서 정확히 변경된 내용에 대한 자세한 정보를 제공합니다.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>기본적으로 보존 기간은 **[!UICONTROL Audit logs]**&#x200B;에 대해 180일로 설정됩니다. 보존 기간을 변경하는 방법에 대한 자세한 내용은 이 [페이지](../../production/using/database-cleanup-workflow.md#deployment-wizard)를 참조하십시오.

## 감사 추적 {#enable-disable-audit-trail} 활성화/비활성화

예를 들어 데이터베이스의 일부 공간을 절약하려는 경우 특정 활동에 대해 감사 추적을 쉽게 활성화하거나 비활성화할 수 있습니다.

방법은 다음과 같습니다.

1. 인스턴스의 **[!UICONTROL Explorer]** 메뉴에 액세스합니다.
1. **[!UICONTROL Administration]** 메뉴에서 **[!UICONTROL Platform]**, **[!UICONTROL Options]** 순으로 선택합니다.

   ![](assets/audit_trail_4.png)

1. 활성화/비활성화할 엔티티에 따라 다음 옵션 중 하나를 선택합니다.

   * 워크플로우의 경우:**[!UICONTROL XtkAudit_Workflows]**
   * 스키마:**[!UICONTROL XtkAudit_DataSchema]**
   * 옵션:**[!UICONTROL XtkAudit_Option]**
   * 모든 엔티티에 대해:**[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 엔티티를 활성화하려면 **[!UICONTROL Value]**&#x200B;을 1로 변경하고 비활성화하려면 0으로 변경합니다.

   ![](assets/audit_trail_6.png)

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 

