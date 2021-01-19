---
solution: Campaign Classic
product: campaign
title: CRM 커넥터 데이터 동기화
description: Campaign과 CRM 간의 데이터 관리
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 0%

---


# 캠페인과 CRM {#data-synchronization} 간의 데이터 동기화

Adobe Campaign과 CRM 간의 데이터 동기화는 전용 워크플로우 활동을 통해 수행됩니다.[CRM 커넥터](../../workflow/using/crm-connector.md).

예를 들어 Microsoft Dynamics 데이터를 Adobe Campaign으로 가져오려면 다음 유형의 작업 과정을 만드십시오.

![](assets/crm_connectors_msdynamics_07.png)

이 워크플로에서는 Microsoft Dynamics를 통해 연락처를 가져오고, 기존 Adobe Campaign 데이터와 연락처를 동기화하고, 중복된 연락처를 삭제하고, Adobe Campaign 데이터베이스를 업데이트합니다.

데이터를 동기화하려면 **[!UICONTROL CRM Connector]** 활동을 구성해야 합니다.

![](assets/crm_connectors_msdynamics_08.png)

이 활동을 사용하여 다음을 수행할 수 있습니다.

* CRM에서 가져오기 - [자세한 내용](#importing-from-the-crm)
* CRM으로 내보내기 - [자세한 내용](#exporting-to-the-crm)
* CRM에서 삭제된 개체 가져오기 - [자세한 내용](#importing-objects-deleted-in-the-crm)
* CRM에서 개체 삭제 - [자세히 알아보기](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

동기화를 구성할 CRM과 일치하는 외부 계정을 선택한 다음 동기화할 개체를 선택합니다.계정, 기회, 리드, 연락처 등

![](assets/crm_task_select_obj.png)

이 활동의 구성은 수행하는 프로세스에 따라 달라집니다. 다양한 구성이 아래에 자세히 나와 있습니다.

## CRM {#importing-from-the-crm}에서 가져오기

Adobe Campaign의 CRM을 통해 데이터를 가져오려면 다음 유형의 워크플로우를 만들어야 합니다.

![](assets/crm_wf_import.png)

가져오기 작업의 경우 **[!UICONTROL CRM Connector]** 활동 구성 단계는 다음과 같습니다.

1. **[!UICONTROL Import from the CRM]** 작업을 선택합니다.
1. **[!UICONTROL Remote object]** 드롭다운 목록으로 이동하여 해당 프로세스의 개체를 선택합니다. 이 객체는 커넥터 구성 중에 Adobe Campaign에서 만든 테이블 중 하나와 일치합니다.
1. **[!UICONTROL Remote fields]** 섹션으로 이동하여 가져올 필드를 입력합니다.

   필드를 추가하려면 도구 모음에서 **[!UICONTROL Add]** 단추를 클릭한 다음 **[!UICONTROL Edit expression]** 아이콘을 클릭합니다.

   ![](assets/crm_task_import_add_field.png)

   필요한 경우 **[!UICONTROL Conversion]** 열의 드롭다운 목록을 통해 데이터 형식을 변경합니다. 가능한 변환 유형은 [데이터 형식](#data-format)에 자세히 설명되어 있습니다.

   >[!IMPORTANT]
   >
   >CRM과 Adobe Campaign에서 개체를 연결하려면 CRM의 레코드 식별자가 필수적입니다. 상자가 승인되면 자동으로 추가됩니다.
   >
   >CRM 측의 마지막 수정 날짜도 증분 데이터를 가져오는 경우 필수입니다.

1. 필요에 따라 가져올 데이터를 필터링할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Edit the filter...]** 링크를 클릭합니다.

   다음 예에서 Adobe Campaign은 2012년 11월 1일 이후 일부 활동이 기록된 연락처만 가져옵니다.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >데이터 필터링 모드에 연결된 제한 사항은 [데이터 필터링](#filtering-data)에 자세히 설명되어 있습니다.

1. **[!UICONTROL Use automatic index...]** 옵션을 사용하면 날짜 및 마지막 수정 내용에 따라 CRM과 Adobe Campaign 간의 증분 객체 동기화를 자동으로 관리할 수 있습니다.

   자세한 내용은 [변수 관리](#variable-management)를 참조하십시오.

### 변수 관리 {#variable-management}

**[!UICONTROL Automatic index]** 옵션을 활성화하면 마지막 가져오기 이후에 수정된 개체만 수집할 수 있습니다.

![](assets/crm_task_import_option.png)

마지막 동기화 날짜는 기본적으로 구성 창에 지정된 옵션에 저장됩니다.**LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>이 메모는 일반 **[!UICONTROL CRM Connector]** 활동에만 적용됩니다. 다른 CRM 활동의 경우 프로세스가 자동으로 진행됩니다.
>
>이 옵션은 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;에서 수동으로 만들고 채워야 합니다. 텍스트 옵션이어야 하며 값이 다음 형식과 일치해야 합니다.**yyyy/MM/dd hh:mm:ss**.
> 
>추가 가져오기를 위해 이 옵션을 수동으로 업데이트해야 합니다.

최신 변경 사항을 식별하기 위해 고려할 원격 CRM 필드를 지정할 수 있습니다.

기본적으로 다음 필드가 사용됩니다(지정된 순서로).

* Microsoft Dynamics의 경우:**수정**,
* Salesforce.com의 경우:**LastModifiedDate**, **SystemModstamp**.

**[!UICONTROL Automatic index]** 옵션을 활성화하면 **[!UICONTROL JavaScript code]** 유형 활동을 통해 동기화 워크플로에서 사용할 수 있는 3개의 변수가 생성됩니다. 이러한 활동은 다음과 같습니다.

* **vars.crmOptionName**:마지막 가져오기 날짜가 포함된 옵션의 이름을 나타냅니다.
* **vars.crmStartImport**:마지막 데이터 복구의 시작 날짜(포함)를 나타냅니다.
* **vars.crmEndDate**:마지막 데이터 복구의 종료 날짜(제외)를 나타냅니다.

   >[!NOTE]
   >
   >이러한 날짜는 다음 형식으로 표시됩니다.**yyyy/MM/dd hh:mm:ss**.

### 데이터 필터링 {#filtering-data}

다양한 CRM을 사용하여 효율적인 작업을 수행하려면 다음 규칙을 사용하여 필터를 만들어야 합니다.

* 각 필터링 수준은 하나의 연산자 유형만 사용할 수 있습니다.
* AND NOT 연산자는 지원되지 않습니다.
* 비교는 null 값(&#39;is empty&#39;/&#39;is not empty&#39; 유형이 아님) 또는 숫자만 고려해야 할 수 있습니다. 즉, 값(오른쪽 열)을 평가하고 이 평가의 결과가 숫자여야 합니다. 따라서 JOIN 유형 비교는 지원되지 않습니다.
* 오른쪽 열에 포함된 값은 JavaScript로 평가됩니다.
* JOIN 비교는 지원되지 않습니다.
* 왼쪽 열의 표현식은 필드여야 합니다. 여러 표현식, 숫자 등의 조합일 수 없습니다.

예를 들어 OR 연산자는 AND 연산자와 동일한 수준에 배치되므로 다음 필터링 조건은 CRM 가져오기에 유효하지 않습니다.

* OR 연산자는 AND 연산자와 동일한 수준에 배치됩니다
* 텍스트 문자열에서 비교는 수행됩니다

![](assets/crm_import_wrong_filter.png)

### 주문별 {#order-by}

Microsoft Dynamics 및 Salesforce.com에서는 가져올 원격 필드를 오름차순이나 내림차순으로 정렬할 수 있습니다.

이렇게 하려면 **[!UICONTROL Order by]** 링크를 클릭하고 목록에 열을 추가합니다.

목록의 열 순서는 정렬 순입니다.

![](assets/crm_import_order.png)

### ID 기록 {#record-identification}

CRM에 포함(및 필터링될 수 있는) 요소를 가져오는 대신 워크플로우에서 미리 계산된 모집단을 사용할 수 있습니다.

이렇게 하려면 **[!UICONTROL Use the population calculated upstream]** 옵션을 선택하고 원격 식별자가 포함된 필드를 지정합니다.

그런 다음 아래에서 보듯이 가져올 인바운드 인구의 필드를 선택합니다.

![](assets/crm_wf_import_calculated_population.png)

## CRM {#exporting-to-the-crm}으로 내보내기

Adobe Campaign 데이터를 CRM으로 내보내면 전체 내용을 CRM 데이터베이스에 복사할 수 있습니다.

데이터를 CRM으로 내보내려면 다음 유형의 워크플로우를 만들어야 합니다.

![](assets/crm_export_diagram.png)

내보내기의 경우 다음 구성을 **[!UICONTROL CRM Connector]** 활동에 적용합니다.

1. **[!UICONTROL Export to CRM]** 작업을 선택합니다.
1. **[!UICONTROL Remote object]** 드롭다운 목록으로 이동하여 해당 프로세스의 개체를 선택합니다. 이 객체는 커넥터 구성 중에 Adobe Campaign에서 만든 테이블 중 하나와 일치합니다.

   >[!IMPORTANT]
   >
   >**[!UICONTROL CRM Connector]** 활동의 내보내기 함수는 CRM 측에 필드를 삽입하거나 업데이트할 수 있습니다. CRM에서 필드 업데이트를 사용하려면 원격 테이블의 기본 키를 지정해야 합니다. 키가 없는 경우 데이터가 삽입됩니다(업데이트되는 대신).

1. **[!UICONTROL Mapping]** 섹션에서 내보낼 필드와 CRM에서 해당 매핑을 지정합니다.

   ![](assets/crm_export_config.png)

   필드를 추가하려면 도구 모음에서 **[!UICONTROL Add]** 단추를 클릭한 다음 **[!UICONTROL Edit expression]** 아이콘을 클릭합니다.

   >[!NOTE]
   >
   >지정된 필드의 경우 CRM 측에 일치하는 항목이 정의되지 않은 경우 값을 업데이트할 수 없습니다.CRM에 바로 삽입됩니다.

   필요한 경우 **[!UICONTROL Conversion]** 열의 드롭다운 목록을 통해 데이터 형식을 변경합니다. 가능한 변환 유형은 [데이터 형식](#data-format)에 자세히 설명되어 있습니다.

   >[!NOTE]
   >
   >내보낼 레코드 목록과 내보내기 결과는 워크플로우가 완료되거나 다시 시작될 때까지 액세스할 수 있는 임시 파일에 저장됩니다. 이렇게 하면 동일한 레코드를 여러 번 내보내거나 데이터를 잃을 위험을 감수하지 않고 오류가 발생할 경우 프로세스를 다시 시작할 수 있습니다.

## 추가 구성 {#additional-configurations}

### 데이터 형식 {#data-format}

데이터 형식을 CRM으로 가져올 때 즉시 변환할 수 있습니다.

이렇게 하려면 일치하는 열에 적용할 변환을 선택합니다.

![](assets/crm_task_import.png)

**[!UICONTROL Default]** 모드는 자동 데이터 변환을 적용하며, 대부분의 경우 데이터의 복사/붙여넣기와 같습니다. 하지만 표준 시간대 관리가 적용됩니다.

기타 가능한 변환은 다음과 같습니다.

* **[!UICONTROL Date only]**:날짜 + 시간 유형 필드를 삭제합니다.
* **[!UICONTROL Without time offset]**:이 모드는 기본 모드에 적용된 표준 시간대 관리를 취소합니다.
* **[!UICONTROL Copy/Paste]**:이 모드에서는 문자열(전환 없음)과 같은 원시 데이터를 사용합니다.

### {#error-processing} 처리 중 오류 발생

데이터 가져오기 또는 내보내기 프레임워크 내에서 특정 프로세스를 오류와 거부로 적용할 수 있습니다. 이렇게 하려면 **[!UICONTROL Behavior]** 탭에서 **[!UICONTROL Process rejects]** 및 **[!UICONTROL Process errors]** 옵션을 선택합니다.

![](assets/crm_export_options.png)

이러한 옵션은 일치하는 출력 전환을 가져옵니다.

![](assets/crm_export_transitions.png)

적용할 프로세스와 관련된 활동을 배치합니다.

인스턴스에 대한 오류를 처리하려면 대기 상자를 추가하고 다시 시도를 예약할 수 있습니다.

거부는 오류 코드와 관련 메시지로 수집되므로 거부 추적 기능을 설정하여 동기화 프로세스를 최적화할 수 있습니다.

>[!NOTE]
>
>**[!UICONTROL Process rejects]** 옵션이 활성화되지 않은 경우에도 오류 코드와 메시지와 함께 거부된 각 열에 대한 경고가 생성됩니다.

**[!UICONTROL Reject]** 출력 전환을 사용하면 오류 메시지 및 코드와 관련된 특정 열이 포함된 출력 스키마에 액세스할 수 있습니다. Salesforce.com의 경우 이 열은 **errorSymbol**(오류 코드와 다른 오류 기호), **errorMessage**(오류 컨텍스트에 대한 설명)입니다.

## CRM {#importing-objects-deleted-in-the-crm}에서 삭제된 개체 가져오기

광범위한 데이터 동기화 프로세스를 설정하려면 CRM에서 삭제된 개체를 Adobe Campaign으로 가져올 수 있습니다.

이렇게 하려면 다음 단계를 적용합니다.

1. **[!UICONTROL Import objects deleted in the CRM]** 작업을 선택합니다.
1. **[!UICONTROL Remote object]** 드롭다운 목록으로 이동하여 해당 프로세스의 개체를 선택합니다. 이 객체는 커넥터 구성 중에 Adobe Campaign에서 만든 테이블 중 하나와 일치합니다.
1. **[!UICONTROL Start date]** 및 **[!UICONTROL End date]** 필드에서 고려할 삭제 기간을 지정합니다. 이 날짜는 기간에 포함됩니다.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >요소 삭제 기간은 CRM에 대한 제한 사항과 일치해야 합니다. 즉, Salesforce.com의 경우, 예를 들어 30일 전에 삭제된 요소는 복구할 수 없습니다.

## CRM {#deleting-objects-in-the-crm}에서 개체 삭제

CRM 측에서 개체를 삭제하려면 삭제할 원격 요소의 기본 키를 지정해야 합니다.

![](assets/crm_delete_in_crm.png)

**[!UICONTROL Behavior]** 탭에서는 거부 처리를 활성화할 수 있습니다. 이 옵션은 **[!UICONTROL CRM connector]** 활동에 대한 두 번째 출력 전환을 생성합니다. 자세한 내용은 [오류 처리](#error-processing)를 참조하십시오.

>[!NOTE]
>
>**[!UICONTROL Process rejects]** 옵션이 비활성화된 경우에도 거부된 각 열에 대한 경고가 생성됩니다.

