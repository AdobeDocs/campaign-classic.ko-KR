---
solution: Campaign Classic
product: campaign
title: CRM 커넥터
description: 캠페인에서 CRM 커넥터 시작하기
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 24%

---


# CRM 커넥터{#crm-connectors}

## CRM 커넥터 시작하기 {#about-crm-connectors}

Adobe Campaign은 Adobe Campaign 플랫폼을 타사 시스템에 연결하는 다양한 CRM 커넥터를 제공합니다. 이러한 CRM 커넥터를 사용하면 연락처, 계정, 구매 등을 동기화할 수 있습니다. 또한 다양한 타사 및 비즈니스 애플리케이션과 사용자의 애플리케이션을 손쉽게 통합할 수 있습니다.

이러한 커넥터를 사용하면 빠르고 손쉽게 데이터를 통합할 수 있습니다. Adobe Campaign은 CRM에서 사용할 수 있는 테이블을 수집하고 선택하는 전용 마법사를 제공합니다. 이렇게 하면 시스템 전체에서 항상 데이터가 최신 상태로 유지되도록 양방향 동기화를 보장합니다.

>[!NOTE]
>
>이 기능은 Adobe Campaign에서 **CRM 커넥터** 전용 패키지를 통해 사용할 수 있습니다.


### 호환 시스템 {#compatible-crm-systems-and-limitations}

지원되는 CRM 및 버전은 캠페인 [호환성 매트릭스](../../rn/using/compatibility-matrix.md)에 자세히 설명되어 있습니다.

>[!NOTE]
>
>CRM 커넥터는 보안 URL(https)에서만 작동합니다.

### 구현 단계 {#crm-implementation-steps}

이 섹션](../../platform/using/crm-ms-dynamics.md)에서 Campaign 및 Microsoft Dynamics [을 연결하는 단계별 절차 학습

일반적으로 Adobe Campaign에서 CRM 커넥터를 사용하려면 다음 단계를 따르십시오.

1. Adobe Campaign 트리의 **[!UICONTROL Administration > Platform > External accounts]** 노드를 통해 새 외부 계정을 만듭니다.
1. Campaign을 연결할 CRM 시스템을 선택합니다.
1. 연결을 활성화할 설정을 입력합니다.
1. 구성 마법사를 실행하여 사용 가능한 CRM 테이블을 생성합니다.구성 마법사를 사용하여 테이블을 수집하고 일치하는 스키마를 만들 수 있습니다.

   **Salesforce** 구성 마법사의 예:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >설정을 승인하려면 로그오프했다가 Adobe Campaign 콘솔에 다시 로그온해야 합니다.

1. **[!UICONTROL Administration > Configuration > Data schemas]** 노드의 Adobe Campaign에서 생성된 스키마를 확인합니다.

   **Salesforce** 스키마의 예:

   ![](assets/crm_connectors_sfdc_table.png)

1. 스키마가 생성되면 CRM을 통해 열거형을 Adobe Campaign에 자동으로 동기화할 수 있습니다.

   이렇게 하려면 **[!UICONTROL Synchronizing enumerations...]** 링크를 클릭하고 CRM 열거에 일치하는 Adobe Campaign 열거형을 선택합니다.

   >[!NOTE]
   >
   >Adobe Campaign 열거형의 모든 값을 CRM의 값으로 바꿀 수 있습니다.이렇게 하려면 **[!UICONTROL Replace]** 열에서 **[!UICONTROL Yes]**&#x200B;을 선택합니다.

   **Salesforce** 열거형의 예:

   ![](assets/crm_connectors_sfdc_enum.png)

   **[!UICONTROL Next]**&#x200B;을 클릭한 다음 **[!UICONTROL Start]**&#x200B;을 클릭하여 목록 가져오기를 시작합니다.

1. **[!UICONTROL Administration > Platform > Enumerations]** 메뉴에서 가져온 값을 확인합니다.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Salesforce의 여러 선택 열거형은 지원되지 않습니다.

1. Adobe Campaign 데이터와 CRM 시스템 간의 데이터를 동기화하려면 워크플로우를 만들고 **[!UICONTROL CRM connector]** 활동을 사용해야 합니다.

   ![](assets/crm_connectors_sfdc_wf.png)

   이 페이지](../../platform/using/crm-data-sync.md)에서 데이터 동기화 [에 대해 자세히 알아보십시오.
