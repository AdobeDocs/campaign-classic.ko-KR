---
product: campaign
title: 필터 만들기
description: 필터 만들기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1963'
ht-degree: 0%

---

# 필터 만들기{#creating-filters}



Adobe Campaign 트리( **[!UICONTROL Explorer]** 홈 페이지의 메뉴)에서 데이터베이스에 포함된 데이터가 목록에 표시됩니다. 연산자에 필요한 데이터만 표시하도록 이러한 목록을 구성할 수 있습니다. 그런 다음 필터링된 데이터에 대해 작업을 시작할 수 있습니다. 필터 구성을 사용하면 목록에서 데이터를 선택할 수 있습니다 **[!UICONTROL dynamically]**. 데이터가 수정되면 필터링된 데이터가 업데이트됩니다.

>[!NOTE]
>
>사용자 인터페이스 구성 설정은 장치 수준에서 로컬로 정의됩니다. 특히 데이터를 새로 고칠 때 문제가 발생하는 경우 이 데이터를 정리할 필요가 있는 경우가 있을 수 있습니다. 이렇게 하려면 **[!UICONTROL File > Clear the local cache]** 메뉴 아래의 제품에서 사용할 수 있습니다.

## 사용 가능한 필터의 유형화 {#typology-of-available-filters}

Adobe Campaign에서 데이터 목록에 필터를 적용할 수 있습니다.

이러한 필터는 한 번 사용하거나 나중에 사용할 수 있도록 저장할 수 있습니다. 여러 필터를 동시에 적용할 수 있습니다.

Adobe Campaign에서는 다음 필터 유형을 사용할 수 있습니다.

* **기본 필터**

   다음 **기본 필터** 는 목록 위에 있는 필드를 통해 액세스할 수 있습니다. 사전 정의된 필드(수신자 프로필의 경우 기본적으로 이름 및 이메일 주소)를 필터링할 수 있습니다. 필드를 사용하여 필터링할 문자를 입력하거나 드롭다운 목록에서 필터 조건을 선택할 수 있습니다.

   ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an email address in the domain "yahoo.com".
-->
목록의 기본 필터를 변경할 수 있습니다. 자세한 내용은 [기본 필터 변경](#altering-the-default-filter).

* **단순 필터**

   **단순 필터** 열에 일회성 필터입니다. 표시된 열에 하나 이상의 간단한 검색 기준으로 정의됩니다.

   동일한 데이터 목록에 여러 개의 단순 필터를 결합하여 검색을 세분화할 수 있습니다. 필터 필드는 다른 필터 아래에 표시됩니다. 서로 독립적으로 삭제할 수 있습니다.

   ![](assets/filters_recipient_simple_filter.png)

   단순 필터는 [단순 필터 만들기](#creating-a-simple-filter).

* **고급 필터**

   **고급 필터** 데이터는 데이터에 대한 쿼리 또는 쿼리 조합을 사용하여 만들어집니다.

   고급 필터 만들기에 대한 자세한 내용은 [고급 필터 만들기](#creating-an-advanced-filter).

   함수를 사용하여 필터의 컨텐츠를 정의할 수 있습니다. 자세한 내용은 [함수를 사용하여 고급 필터 만들기](#creating-an-advanced-filter-with-functions).

   >[!NOTE]
   >
   >Adobe Campaign에서 쿼리 만들기에 대한 자세한 내용은 [이 섹션](../../platform/using/about-queries-in-campaign.md).

* **사용자 필터**

   An **애플리케이션 필터** 는 다른 연산자와 해당 구성을 사용하고 공유할 수 있도록 저장된 고급 필터입니다.

   다음 **[!UICONTROL Filters]** 목록 위에 있는 버튼은 필터링을 세분화하기 위해 결합할 수 있는 애플리케이션 필터 세트를 제공합니다. 이러한 필터를 만드는 방법은 다음과 같습니다. [필터 저장](#saving-a-filter).

## 기본 필터 변경 {#altering-the-default-filter}

수신자 목록에 대한 기본 필터를 변경하려면 **[!UICONTROL Profiles and Targets > Pre-defined filters]** 노드 아래에 있어야 합니다.

다른 모든 유형의 데이터에 대해 **[!UICONTROL Administration > Configuration > Predefined filters]** 노드 아래에 있어야 합니다.

다음 단계를 적용합니다.

1. 기본적으로 사용할 필터를 선택합니다.
1. 을(를) 클릭합니다. **[!UICONTROL Parameters]** 탭을 선택하고 **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >기본 필터가 이미 목록에 적용된 경우, 새 필터를 적용하기 전에 기본 필터를 비활성화해야 합니다. 이렇게 하려면 필터링 필드 오른쪽의 빨간색 십자을 클릭합니다.

1. 클릭 **[!UICONTROL Save]** 필터를 적용하려면

   >[!NOTE]
   >
   >필터 정의 창은 [고급 필터 만들기](#creating-an-advanced-filter) 및 [필터 저장](#saving-a-filter).

## 단순 필터 만들기 {#creating-a-simple-filter}

을(를) 만들려면 **단순 필터**&#x200B;를 채울 때 다음 단계를 적용합니다.

1. 필터링할 필드를 마우스 오른쪽 단추로 클릭하고 을 선택합니다 **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   기본 필터 필드가 목록 위에 표시됩니다.

1. 드롭다운 목록에서 필터 옵션을 선택하거나 적용할 필터 기준을 입력합니다(기준을 선택하거나 입력하는 방법은 필드 유형에 따라 달라집니다.). 텍스트, 열거형 등)

   ![](assets/s_ncs_user_sort_fields.png)

1. 필터를 활성화하려면 키보드에서 Enter 키를 누르거나 필터 필드 오른쪽의 녹색 화살표를 클릭합니다.

데이터를 필터링할 필드가 프로필 형태로 표시되지 않으면 표시된 열에 데이터를 추가한 다음 해당 열을 필터링할 수 있습니다. 삭제 방법,

1. 을(를) 클릭합니다. **[!UICONTROL Configure the list]** 아이콘.

   ![](assets/s_ncs_user_configure_list.png)

1. 표시할 열(예: 수신자의 연령)을 선택합니다.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. 마우스 오른쪽 단추를 클릭합니다. **연령** 받는 사람 목록에서 열을 선택하고 **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   그런 다음 나이 필터링 옵션을 선택할 수 있습니다.

   ![](assets/s_ncs_user_delete_filter.png)

## 고급 필터 만들기 {#creating-an-advanced-filter}

을(를) 만들려면 **고급 필터**&#x200B;를 채울 때 다음 단계를 적용합니다.

1. 을(를) 클릭합니다. **[!UICONTROL Filters]** 단추를 누르고 선택합니다. **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   필터링할 데이터 목록을 마우스 오른쪽 단추로 클릭하고 선택할 수도 있습니다 **[!UICONTROL Advanced filter...]**.

   필터링 조건 정의 창이 표시됩니다.

1. 을(를) 클릭합니다. **[!UICONTROL Expression]** 열을 사용하여 입력 값을 정의합니다.
1. 클릭 **[!UICONTROL Edit expression]** 필터를 적용할 필드를 선택합니다.

   ![](assets/s_user_filter_choose_field.png)

1. 목록에서 데이터를 필터링할 필드를 선택합니다. **[!UICONTROL Finish]**&#x200B;을(를) 클릭하여 확인합니다.
1. 을(를) 클릭합니다. **[!UICONTROL Operator]** 열을 선택하고 드롭다운 목록에서 적용할 연산자를 선택합니다.
1. 에서 예상 값을 선택합니다 **[!UICONTROL Value]** 열. 여러 필터를 결합하여 쿼리를 세분화할 수 있습니다. 필터 조건을 추가하려면 **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. 도구 모음 화살표를 사용하여 표현식에 계층을 할당하거나 쿼리 표현식의 순서를 변경할 수 있습니다.
1. 표현식 간의 기본 연산자는 **및**&#x200B;로 설정되지만 필드를 클릭하여 변경할 수 있습니다. 을(를) 선택할 수 있습니다 **또는** 연산자를 사용할 수 있습니다.

   ![](assets/s_ncs_user_filter_operator.png)

1. 클릭 **[!UICONTROL OK]** 필터 만들기를 확인하고 목록에 적용합니다.

적용된 필터가 목록 위에 표시됩니다.

![](assets/s_ncs_user_filter_adv_edit.png)

이 필터를 편집하거나 수정하려면 해당 레이블을 클릭합니다.

이 필터를 취소하려면 **[!UICONTROL Remove this filter]** 아이콘을 클릭합니다.

![](assets/s_ncs_user_filter_adv_remove.png)

고급 필터를 저장하여 나중에 사용할 수 있도록 유지할 수 있습니다. 이 유형의 필터에 대한 자세한 내용은 [필터 저장](#saving-a-filter).

### 함수를 사용하여 고급 필터 만들기 {#creating-an-advanced-filter-with-functions}

고급 필터는 함수를 사용할 수 있습니다. **함수를 사용하는 필터** 데이터베이스 데이터와 고급 함수를 사용하여 공식을 생성할 수 있는 표현식 편집기를 통해 작성됩니다. 함수를 사용하여 필터를 만들려면 고급 필터 만들기 1단계, 2단계 및 3을 반복한 다음 다음 단계로 진행합니다.

1. 필드 선택 창에서 **[!UICONTROL Advanced selection]**.
1. 사용할 공식 유형을 선택합니다. 집계, 기존 사용자 필터 또는 표현식.

   ![](assets/s_ncs_user_filter_formula_select.png)

   다음 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Field only]** 필드를 선택합니다. 기본 모드입니다.
   * **[!UICONTROL Aggregate]** 사용할 합계 공식(실사, 합계, 평균, 최대값, 최소값)을 선택하려면 다음을 수행합니다.
   * **[!UICONTROL User filter]** 기존 사용자 필터 중 하나를 선택합니다. 사용자 필터는 [필터 저장](#saving-a-filter).
   * **[!UICONTROL Expression]** 표현식 편집기에 액세스합니다.

      표현식 편집기를 사용하면 고급 필터를 정의할 수 있습니다. 다음과 같습니다.

      ![](assets/s_ncs_user_create_exp_exple01.png)

      데이터베이스 테이블에서 필드를 선택하고 고급 함수를 데이터베이스 테이블에 첨부할 수 있습니다. 에서 사용할 함수를 선택합니다 **[!UICONTROL List of functions]**. 사용할 수 있는 함수는 [함수 목록](../../platform/using/defining-filter-conditions.md#list-of-functions). 다음으로, 함수와 관련된 필드 또는 필드를 선택하고 **[!UICONTROL OK]** 표현식을 승인하려면

      >[!NOTE]
      >
      >표현식을 기반으로 하는 필터 만들기의 예는 [이 섹션](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## 필터 저장 {#saving-a-filter}

필터는 각 연산자별로 다르며 연산자가 클라이언트 콘솔의 캐시를 지울 때마다 다시 초기화됩니다.

을(를) 만들 수 있습니다 **애플리케이션 필터** 고급 필터를 저장하여 다음을 수행합니다. 목록을 마우스 오른쪽 단추로 클릭하거나 **[!UICONTROL Filters]** 목록 위에 있는 단추입니다.

게재 마법사의 타겟 선택 단계에서 이러한 필터에 직접 액세스할 수도 있습니다( [이 섹션](../../delivery/using/creating-an-email-delivery.md) 게재 만들기에 대한 자세한 내용). 응용 프로그램 필터를 만들려면 다음을 수행할 수 있습니다.

* 고급 필터를 응용 프로그램 필터로 변환합니다. 이렇게 하려면 **[!UICONTROL Save]** 고급 필터 편집기를 닫기 전에 먼저 추가

   ![](assets/s_ncs_user_filter_save.png)

* 을 통해 이 애플리케이션 필터 만들기 **[!UICONTROL Administration > Configuration > Predefined filters]** 또는 **[!UICONTROL Profiles and targets > Predefined filters]** 받는 사람) 노드 아래에 표시됩니다. 이렇게 하려면 필터 목록을 마우스 오른쪽 단추로 클릭하고 를 선택합니다 **[!UICONTROL New...]**. 절차는 고급 필터를 만드는 것과 동일합니다.

   다음 **[!UICONTROL Label]** 필드를 사용하면 이 필터의 이름을 지정할 수 있습니다. 이 이름은 **[!UICONTROL Filters...]** 버튼을 클릭합니다.

   ![](assets/user_filter_apply.png)

마우스 오른쪽 단추를 클릭하고 을 선택하여 현재 목록의 모든 필터를 삭제할 수 있습니다 **[!UICONTROL No filter]** 또는 **[!UICONTROL Filters]** 목록 위에 있는 아이콘.

을 클릭하여 필터를 결합할 수 있습니다 **[!UICONTROL Filters]** 버튼 및 **[!UICONTROL And...]** 메뉴 아래의 제품에서 사용할 수 있습니다.

![](assets/s_ncs_user_filter_combination.png)

## 수신자 필터링 {#filtering-recipients}

사전 정의된 필터( [필터 저장](#saving-a-filter)) 데이터베이스에 포함된 수신자의 프로필을 필터링할 수 있습니다. 다음에서 필터를 편집할 수 있습니다 **[!UICONTROL Profiles and Targets > Predefined filters]** 노드 아래에 있어야 합니다. 필터는 작업 공간의 위쪽 섹션에 **[!UICONTROL Filters]** 버튼을 클릭합니다.

필터를 선택하여 정의를 표시하고 필터링된 데이터의 미리 보기에 액세스합니다.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>사전 정의된 필터 만들기에 대한 자세한 예는 를 참조하십시오 [사용 사례](../../platform/using/use-case.md).

사전 정의된 필터는 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>쿼리</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 열림<br /> </td> 
   <td> 게재를 연 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 열었지만 클릭하지 않음<br /> </td> 
   <td> 게재를 열었지만 링크를 클릭하지 않은 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 비활성 수신자<br /> </td> 
   <td> X개월 내에 게재를 열지 않은 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 장치 유형별 마지막 활동<br /> </td> 
   <td> 최근 Z일 동안 장치 X를 사용하여 게재를 클릭하거나 연 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 장치 유형별 마지막 활동(추적)<br /> </td> 
   <td> 최근 Z일 동안 장치 X를 사용하여 게재를 클릭하거나 연 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 타겟팅되지 않은 수신자<br /> </td> 
   <td> X개월 동안 채널 Y를 통해 타겟팅되지 않은 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 매우 활성 수신자<br /> </td> 
   <td> 최근 Y개월 동안 게재를 최소 X 번 클릭한 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
 <td> 차단 목록에 추가된 이메일 주소<br /> </td> 
    <td> 전자 메일 주소가에 있는 수신자를 차단 목록 선택합니다.<br/> </td>
  </tr> 
  <tr> 
   <td> 격리된 전자 메일 주소<br /> </td> 
   <td> 전자 메일 주소가 격리된 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 폴더에 중복되는 이메일 주소<br /> </td> 
   <td> 폴더에 이메일 주소가 중복되는 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 열지 또는 클릭하지 않음<br /> </td> 
   <td> 게재를 열지 또는 게재를 클릭하지 않은 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 수신자(일)<br /> </td> 
   <td> 최근 X일 동안 만든 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 수신자(분)<br /> </td> 
   <td> 마지막 X 분 동안 만든 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 수신자(개월)<br /> </td> 
   <td> 최근 X 월에 생성된 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 기준<br /> </td> 
   <td> 구독별로 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 특정 링크를 클릭하여<br /> </td> 
   <td> 게재에서 특정 URL을 클릭한 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 게시 게재 동작별<br /> </td> 
   <td> 게재를 받은 후 자신의 동작에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 생성 날짜별<br /> </td> 
   <td> X개월(현재 날짜에서 n개월을 뺀 숫자)부터 Y개월(현재 날짜에서 n개월을 뺀 숫자)까지의 기간 동안 생성 날짜별로 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 목록별<br /> </td> 
   <td> 목록을 기준으로 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 횟수별<br /> </td> 
   <td> 최근 X 개월 동안 게재를 클릭한 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 메시지 수 기준<br /> </td> 
   <td> 수신한 메시지 수에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기 횟수 기준<br /> </td> 
   <td> Z 시간 동안 X와 Y 게재 간에 연 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 이름 또는 이메일 기준<br /> </td> 
   <td> 이름이나 전자 메일에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 연령 범위별<br /> </td> 
   <td> 나이에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>계산 및 기간에 대한 모든 비교는 광범위한 의미에서 이해할 수 있습니다(쿼리 제한에 해당하는 수신자는 비교에 포함됨).

데이터 계산 방식의 예:

* 30세 미만인 수신자를 선택합니다.

   ![](assets/predefined_filters_01.png)

* 18세 이상인 수신자를 선택합니다.

   ![](assets/predefined_filters_03.png)

* 18세에서 30세 사이의 수신자를 선택합니다.

   ![](assets/predefined_filters_02.png)

## 데이터 필터에 대한 고급 설정 {#advanced-settings-for-data-filters}

을(를) 클릭합니다. **[!UICONTROL Settings]** 탭하여 다음 옵션에 액세스합니다.

* **[!UICONTROL Default filter for the associated document type]**: 이 옵션을 사용하면 기본적으로 정렬 관련 목록 편집기에서 이 필터를 제안할 수 있습니다.

   예: **[!UICONTROL By name or login]** 필터가 연산자에 적용됩니다. 이 옵션이 선택되어 있으므로 모든 연산자 목록에서 항상 필터를 제공합니다.

* **[!UICONTROL Filter shared with other operators]**: 이 옵션을 사용하면 현재 데이터베이스의 다른 모든 연산자가 필터를 사용할 수 있도록 만들 수 있습니다.
* **[!UICONTROL Use parameter entry form]**: 이 옵션을 사용하면 이 필터를 선택하면 목록 위에 표시할 필터 필드를 정의할 수 있습니다. 이러한 필드를 사용하면 필터 설정을 정의할 수 있습니다. 이 양식은 **[!UICONTROL Form]** 버튼을 클릭합니다. 예를 들어 사전 구성된 필터 **[!UICONTROL Recipients who have opened]**&#x200B;수신자 목록에서 사용할 수 있는 에는 필터가 대상으로 하는 게재를 선택할 수 있는 필터 필드가 표시됩니다.

   다음 **[!UICONTROL Preview]** 버튼은 선택한 필터의 결과를 표시합니다.

* 다음 **[!UICONTROL Advanced parameters]** 링크를 통해 추가 설정을 정의할 수 있습니다. 특히 SQL 테이블을 필터와 연결하여 테이블을 공유하는 모든 편집자에게 일반화할 수 있습니다.

   을(를) 선택합니다 **[!UICONTROL Do not restrict the filter]** 옵션을 선택합니다.

   이 옵션은 게재 마법사에서 제공되는 &quot;게재 수신자&quot; 및 &quot;폴더에 속하는 게재 수신자&quot;에 대해 오버로드할 수 없는 필터입니다.

   ![](assets/s_ncs_user_filter_advanced_param.png)
