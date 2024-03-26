---
product: campaign
title: 열거형 관리
description: 열거형 관리
feature: Data Management
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 2ece058d-b493-4fea-b3db-322cf7ea7f4f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 0%

---

# 열거형 관리{#managing-enumerations}



열거형(&#39;itemised list&#39;라고도 함)은 특정 필드를 채우기 위해 시스템에서 제안하는 값 목록입니다. 열거형을 사용하면 이러한 필드의 값을 표준화하고 쿼리 내에서 데이터 입력 또는 사용에 도움을 줄 수 있습니다.

값 목록은 필드에 입력할 값을 선택할 수 있는 드롭다운 목록으로 나타납니다. 드롭다운 목록을 통해 예측 입력도 가능합니다. 여기서 연산자는 처음 몇 글자를 입력하고 애플리케이션은 나머지 글자를 채웁니다.

일부 콘솔 필드가 이 유형의 열거형으로 정의되었습니다. 해당 필드에 직접 입력하여 값을 추가할 수 있는 경우 열거를 &quot;open&quot;이라고 합니다.

## 값에 대한 액세스 {#access-to-values}

이 유형의 필드에 대한 값이 정의되며 이러한 필드의 전체 관리(값 추가/삭제)는 **[!UICONTROL Administration > Platform > Enumerations]** 트리의 노드.

![](assets/s_ncs_user_itemized_list_node.png)

* 상단 섹션은 항목별 목록이 정의된 필드 목록을 제공합니다.
* 아래 섹션에는 제안된 값이 나열됩니다. 이 값은 이 필드를 사용하는 편집기에서 반복됩니다.

  ![](assets/s_ncs_user_itemized_list_values.png)

  새 열거형 값을 만들려면 **[!UICONTROL Add]**.

  ![](assets/s_ncs_user_itemized_list.png)

  다음과 같은 경우 **[!UICONTROL Open]** 옵션을 선택하면 사용자가 해당 필드에 직접 새 항목별 목록 값을 추가할 수 있습니다. 확인 메시지를 통해 이 값을 만들 수 있습니다.

  ![](assets/s_ncs_user_itemized_list_new_value.png)

* 다음과 같은 경우 **[!UICONTROL Closed]** 옵션을 선택하면 사용자가 새 값을 만들 수 없고 사용 가능한 값 중에서 선택할 수만 있습니다.

## 데이터 표준화 {#standardizing-data}

### 앨리어스 정리 정보 {#about-alias-cleansing}

항목별 목록 필드에 열거형 값을 제외한 값을 입력할 수 있습니다. 이러한 지표는 그대로 보관하거나 세척할 수 있습니다.

>[!CAUTION]
>
>데이터 정리는 데이터베이스의 데이터에 영향을 주는 중요한 프로세스입니다. Adobe Campaign은 대량 데이터 업데이트를 수행하여 일부 값이 삭제될 수 있습니다. 따라서 이 작업은 전문가 사용자용으로 예약되어 있습니다.

입력한 값은 다음 중 하나입니다.

* 항목별 목록 값에 추가됨: 이 경우 **[!UICONTROL Open]** 옵션을 선택해야 합니다.
* 또는 해당 별칭으로 자동으로 대체됩니다. 이 경우 **[!UICONTROL Alias]** 항목별 목록의 탭,
* 또는 는 별칭 목록에 저장됩니다. 나중에 별칭을 할당할 수 있습니다.

  >[!NOTE]
  >
  >데이터 정리 기능을 사용해야 하는 경우 **[!UICONTROL Alias cleansing]** 항목이 나열된 상태로 남아 있는 문제를 해결했습니다.

### 별칭 사용 {#using-aliases}

옵션 **[!UICONTROL Alias cleansing]** 선택한 항목별 목록에 별칭을 사용할 수 있습니다. 이 옵션을 선택하면 **[!UICONTROL Alias]** 창 하단에 탭이 표시됩니다.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### 별칭 만들기 {#creating-an-alias}

별칭을 만들려면 **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

변환할 별칭과 적용할 값을 입력하고 **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

이 작업을 확인하기 전에 매개 변수를 확인하십시오.

>[!CAUTION]
>
>이 단계가 확인되면 이전에 입력한 값이 복구되지 않을 수 있습니다. 해당 값은 대체되었습니다.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

따라서 사용자가 값을 입력할 때 **네일센** &quot;회사&quot; 필드(Adobe Campaign 콘솔 또는 양식)에서는 값으로 자동 교체됩니다 **닐슨 주식회사**. 값 교체는 다음을 통해 수행됩니다. **별칭 정리** 워크플로입니다. 을(를) 참조하십시오 [데이터 정리 실행](#running-data-cleansing).

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### 값을 별칭으로 변환 {#converting-values-into-aliases}

열거형 값을 별칭으로 변환하려면 값 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

변환할 값을 선택하고 **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

클릭 **[!UICONTROL Start]** 변환을 실행합니다.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

실행이 완료되면 별칭이 별칭 목록에 추가됩니다.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### 별칭 히트 검색 {#retrieving-alias-hits}

사용자가 입력한 값을 별칭으로 변환할 수 있습니다. 따라서 사용자가 항목별 목록에 포함되지 않은 값을 입력하면 해당 값이 **[!UICONTROL Alias]** 탭.

다음 **별칭 정리** 기술 워크플로우는 매일 밤 이러한 값을 복구하여 항목별 목록을 업데이트합니다. 을(를) 참조하십시오 [데이터 정리 실행](#running-data-cleansing)

필요한 경우 **[!UICONTROL Hits]** 열은 이 값이 입력된 횟수를 표시할 수 있습니다. 이 값을 계산하는 데는 시간과 메모리가 모두 필요할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [시작 발생 횟수 계산](#calculating-entry-occurrences).

### 데이터 정리 실행 {#running-data-cleansing}

데이터 정리는 **[!UICONTROL Alias cleansing]** 기술 워크플로우입니다. 열거형에 대해 정의된 구성은 실행 중에 적용됩니다. 을(를) 참조하십시오 [별칭 정리 워크플로우](#alias-cleansing-workflow).

정리는 다음을 통해 트리거될 수 있습니다. **[!UICONTROL Cleanse values...]** 링크를 클릭합니다.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

다음 **[!UICONTROL Advanced parameters...]** 링크를 사용하면 수집된 값이 고려되는 시작 날짜를 설정할 수 있습니다.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

다음을 클릭합니다. **[!UICONTROL Start]** 데이터 정리를 실행하는 단추입니다.

#### 시작 발생 횟수 계산 {#calculating-entry-occurrences}

다음 **[!UICONTROL Alias]** 항목별 목록의 하위 탭에는 입력된 모든 값 중에서 별칭이 발생한 횟수가 표시됩니다. 이 정보는 예상 값이며 **[!UICONTROL Hits]** 열.

>[!CAUTION]
>
>별칭 항목 발생 횟수를 계산하는 데 시간이 오래 걸릴 수 있습니다. 그렇기 때문에 이 기능을 사용할 때는 주의해야 한다.

다음을 통해 히트 계산을 수동으로 실행할 수 있습니다. **[!UICONTROL Cleanse values...]** 링크를 클릭합니다. 이렇게 하려면 **[!UICONTROL Advanced parameters...]** 링크를 클릭하고 원하는 옵션을 선택합니다.

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: 입력한 날짜에 따라 이미 계산된 히트를 업데이트할 수 있습니다.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: 전체 Adobe Campaign 플랫폼에서 계산을 실행할 수 있습니다.

예를 들어 일주일에 한 번, 주어진 기간 동안 자동으로 계산이 실행되도록 전용 워크플로우를 만들 수도 있습니다.

이렇게 하려면 **[!UICONTROL Alias cleansing]** 워크플로우에서 스케줄러를 변경하고 **[!UICONTROL Enumeration value cleansing]** 활동:

* **-updateHits** 별칭 히트 수를 업데이트하려면
* **-updateHits:full** 모든 별칭 히트를 다시 계산합니다.

#### 별칭 정리 워크플로우 {#alias-cleansing-workflow}

다음 **별칭 정리** 워크플로는 열거형 값 정리를 실행합니다. 기본적으로 매일 실행됩니다.

를 통해 액세스됩니다. **[!UICONTROL Administration > Production > Technical workflows]** 노드.

![](assets/s_ncs_user_itemized_list_alias_wf.png)
