---
product: campaign
title: 필터 만들기
description: 필터 만들기
feature: Profiles
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1979'
ht-degree: 0%

---

# 필터 만들기{#creating-filters}



홈 페이지의 **[!UICONTROL Explorer]** 메뉴에서 Adobe Campaign 트리를 탐색하면 데이터베이스에 포함된 데이터가 목록에 표시됩니다. 이러한 목록은 연산자가 필요로 하는 데이터만 표시하도록 구성할 수 있다. 그런 다음 필터링된 데이터에 대해 작업을 실행할 수 있습니다. 필터 구성을 통해 **[!UICONTROL dynamically]** 목록에서 데이터를 선택할 수 있습니다. 데이터가 수정되면 필터링된 데이터가 업데이트됩니다.

>[!NOTE]
>
>사용자 인터페이스 구성 설정은 장치 수준에서 로컬로 정의됩니다. 특히 데이터를 새로 고칠 때 문제가 발생하는 경우 이 데이터를 정리해야 하는 경우가 있습니다. 이렇게 하려면 **[!UICONTROL File > Clear the local cache]** 메뉴를 사용합니다.

## 사용 가능한 필터의 유형화 {#typology-of-available-filters}

Adobe Campaign을 사용하면 데이터 목록에 필터를 적용할 수 있습니다.

이러한 필터는 한 번 사용하거나 나중에 사용할 수 있도록 저장할 수 있습니다. 여러 필터를 동시에 적용할 수 있습니다.

Adobe Campaign에서는 다음 필터 유형을 사용할 수 있습니다.

* **기본 필터**

  **기본 필터**&#x200B;은(는) 목록 위에 있는 필드를 통해 액세스할 수 있습니다. 사전 정의된 필드를 필터링할 수 있습니다(수신자 프로필의 경우 기본적으로 이름과 이메일 주소). 필드를 사용하여 필터링할 문자를 입력하거나 드롭다운 목록에서 필터 조건을 선택할 수 있습니다.

  ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an email address in the domain "yahoo.com".
-->
목록의 기본 필터를 변경할 수 있습니다. 자세한 내용은 [기본 필터 변경](#altering-the-default-filter)을 참조하세요.

* **단순 필터**

  **단순 필터**&#x200B;은(는) 열에서 일회성 필터입니다. 표시된 열에 하나 이상의 단순 검색 기준으로 정의됩니다.

  동일한 데이터 목록에서 여러 개의 간단한 필터를 결합하여 검색을 구체화할 수 있습니다. 필터 필드는 다른 필드 아래에 표시됩니다. 이러한 파일은 서로 독립적으로 삭제할 수 있습니다.

  ![](assets/filters_recipient_simple_filter.png)

  단순 필터는 [단순 필터 만들기](#creating-a-simple-filter)에 자세히 설명되어 있습니다.

* **고급 필터**

  **고급 필터**&#x200B;은(는) 데이터에 대한 쿼리 또는 쿼리 조합을 사용하여 만들어집니다.

  고급 필터를 만드는 방법에 대한 자세한 내용은 [고급 필터 만들기](#creating-an-advanced-filter)를 참조하세요.

  함수를 사용하여 필터의 콘텐츠를 정의할 수 있습니다. 자세한 내용은 [함수를 사용하여 고급 필터 만들기](#creating-an-advanced-filter-with-functions)를 참조하세요.

  >[!NOTE]
  >
  >Adobe Campaign에서 쿼리를 작성하는 방법에 대한 자세한 내용은 [이 섹션](../../platform/using/about-queries-in-campaign.md)을 참조하세요.

* **사용자 필터**

  **응용 프로그램 필터**&#x200B;은(는) 저장된 고급 필터로서, 이 필터를 사용하여 다른 연산자와 구성을 공유할 수 있습니다.

  목록 위에 있는 **[!UICONTROL Filters]** 단추는 필터링을 세분화하기 위해 결합할 수 있는 응용 프로그램 필터 집합을 제공합니다. 이러한 필터를 만드는 방법은 [필터 저장](#saving-a-filter)에 나와 있습니다.

## 기본 필터 변경 {#altering-the-default-filter}

받는 사람 목록의 기본 필터를 변경하려면 트리의 **[!UICONTROL Profiles and Targets > Pre-defined filters]** 노드를 클릭하십시오.

다른 모든 데이터 형식의 경우 **[!UICONTROL Administration > Configuration > Predefined filters]** 노드를 통해 기본 필터를 구성하십시오.

다음 단계를 적용합니다.

1. 기본적으로 사용할 필터를 선택합니다.
1. **[!UICONTROL Parameters]** 탭을 클릭하고 **[!UICONTROL Default filter for the associated document type]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >기본 필터가 이미 목록에 적용된 경우 새 필터를 적용하기 전에 비활성화해야 합니다. 이렇게 하려면 필터링 필드 오른쪽에 있는 빨간색 십자가를 클릭합니다.

1. 필터를 적용하려면 **[!UICONTROL Save]**&#x200B;을(를) 클릭하십시오.

   >[!NOTE]
   >
   >필터 정의 창은 [고급 필터 만들기](#creating-an-advanced-filter) 및 [필터 저장](#saving-a-filter)에 자세히 설명되어 있습니다.

## 간단한 필터 만들기 {#creating-a-simple-filter}

**단순 필터**&#x200B;를 만들려면 다음 단계를 적용하십시오.

1. 필터링할 필드를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Filter on this field]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_sort_this_field.png)

   기본 필터 필드가 목록 위에 표시됩니다.

1. 드롭다운 목록에서 필터 옵션을 선택하거나 적용할 필터 기준을 입력합니다(기준을 선택하거나 입력하는 방법은 필드 유형(텍스트, 열거 등)에 따라 다릅니다).

   ![](assets/s_ncs_user_sort_fields.png)

1. 필터를 활성화하려면 키보드에서 Enter 키를 누르거나 필터 필드의 오른쪽에 있는 녹색 화살표를 클릭합니다.

데이터를 필터링할 필드가 프로필 형태로 표시되지 않으면 표시된 열에 추가한 다음 해당 열을 필터링할 수 있습니다. 이렇게 하려면,

1. **[!UICONTROL Configure the list]** 아이콘을 클릭합니다.

   ![](assets/s_ncs_user_configure_list.png)

1. 표시할 열(예: 수신자 연령)을 선택합니다.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. 받는 사람 목록에서 **나이** 열을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Filter on this column]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_sort_this_column.png)

   그런 다음 연령 필터링 옵션을 선택할 수 있습니다.

   ![](assets/s_ncs_user_delete_filter.png)

## 고급 필터 만들기 {#creating-an-advanced-filter}

**고급 필터**&#x200B;를 만들려면 다음 단계를 적용하십시오.

1. **[!UICONTROL Filters]** 단추를 클릭하고 **[!UICONTROL Advanced filter...]**&#x200B;을(를) 선택합니다.

   ![](assets/filters_recipient_create_adv_filter.png)

   필터링할 데이터 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Advanced filter...]**&#x200B;을(를) 선택할 수도 있습니다.

   필터링 조건 정의 창이 표시됩니다.

1. **[!UICONTROL Expression]** 열을 클릭하여 입력 값을 정의합니다.
1. 필터를 적용할 필드를 선택하려면 **[!UICONTROL Edit expression]**&#x200B;을(를) 클릭하십시오.

   ![](assets/s_user_filter_choose_field.png)

1. 목록에서 데이터를 필터링할 필드를 선택합니다. **[!UICONTROL Finish]**&#x200B;을(를) 클릭하여 확인합니다.
1. **[!UICONTROL Operator]** 열을 클릭하고 드롭다운 목록에서 적용할 연산자를 선택합니다.
1. **[!UICONTROL Value]** 열에서 예상 값을 선택하십시오. 여러 필터를 결합하여 쿼리를 구체화할 수 있습니다. 필터 조건을 추가하려면 **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. 표현식에 계층을 지정하거나 도구 모음 화살표를 사용하여 쿼리 표현식의 순서를 변경할 수 있습니다.
1. 표현식 사이의 기본 연산자는 **And**&#x200B;이지만 필드를 클릭하여 변경할 수 있습니다. **Or** 연산자를 선택할 수 있습니다.

   ![](assets/s_ncs_user_filter_operator.png)

1. **[!UICONTROL OK]**&#x200B;을(를) 클릭하여 필터 만들기를 확인하고 목록에 적용합니다.

적용된 필터가 목록 위에 표시됩니다.

![](assets/s_ncs_user_filter_adv_edit.png)

이 필터를 편집하거나 수정하려면 해당 레이블을 클릭합니다.

이 필터를 취소하려면 필터 오른쪽에 있는 **[!UICONTROL Remove this filter]** 아이콘을 클릭합니다.

![](assets/s_ncs_user_filter_adv_remove.png)

고급 필터를 저장하여 나중에 사용할 수 있도록 유지할 수 있습니다. 이 필터 유형에 대한 자세한 내용은 [필터 저장](#saving-a-filter)을 참조하세요.

### 함수를 사용하여 고급 필터 만들기 {#creating-an-advanced-filter-with-functions}

고급 필터에서는 함수를 사용할 수 있습니다. **함수가 있는 필터**&#x200B;는 데이터베이스 데이터와 고급 함수를 사용하여 수식을 만들 수 있는 식 편집기를 통해 만들어집니다. 함수가 있는 필터를 만들려면 고급 필터 만들기 단계 1, 2 및 3을 반복한 후 다음과 같이 진행합니다.

1. 필드 선택 창에서 **[!UICONTROL Advanced selection]**&#x200B;을(를) 클릭합니다.
1. 사용할 공식 유형(집계, 기존 사용자 필터 또는 표현식)을 선택합니다.

   ![](assets/s_ncs_user_filter_formula_select.png)

   다음 옵션을 사용할 수 있습니다.

   * 필드를 선택하려면 **[!UICONTROL Field only]**&#x200B;하세요. 기본 모드입니다.
   * **[!UICONTROL Aggregate]**&#x200B;을(를) 사용하여 사용할 집계 수식(개수, 합계, 평균, 최대, 최소)을 선택합니다.
   * **[!UICONTROL User filter]**&#x200B;을(를) 클릭하여 기존 사용자 필터 중 하나를 선택합니다. 사용자 필터는 [필터 저장](#saving-a-filter)에 자세히 설명되어 있습니다.
   * **[!UICONTROL Expression]**&#x200B;하여 표현식 편집기에 액세스할 수 있습니다.

     표현식 편집기를 사용하여 고급 필터를 정의할 수 있습니다. 다음과 같습니다.

     ![](assets/s_ncs_user_create_exp_exple01.png)

     데이터베이스 테이블에서 필드를 선택하고 고급 함수를 연결할 수 있습니다. **[!UICONTROL List of functions]**&#x200B;에서 사용할 함수를 선택하십시오. 사용 가능한 함수는 [함수 목록](../../platform/using/defining-filter-conditions.md#list-of-functions)에 자세히 설명되어 있습니다. 그런 다음 함수에 관련된 필드를 선택하고 **[!UICONTROL OK]**&#x200B;을(를) 클릭하여 식을 승인합니다.

     >[!NOTE]
     >
     >식을 기반으로 필터를 만드는 예를 보려면 [이 섹션](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is)을 참조하세요.

## 필터 저장 {#saving-a-filter}

필터는 각 연산자에 따라 다르며 연산자가 클라이언트 콘솔의 캐시를 지울 때마다 다시 초기화됩니다.

고급 필터를 저장하여 **응용 프로그램 필터**&#x200B;을(를) 만들 수 있습니다. 목록을 마우스 오른쪽 단추로 클릭하거나 목록 위에 있는 **[!UICONTROL Filters]** 단추를 통해 다시 사용할 수 있습니다.

이러한 필터는 대상 선택 단계에서 게재 도우미를 통해 직접 액세스할 수도 있습니다(게재 만들기에 대한 자세한 내용은 [이 섹션](../../delivery/using/creating-an-email-delivery.md) 참조). 응용 프로그램 필터를 만들려면 다음 작업을 수행할 수 있습니다.

* 고급 필터를 응용 프로그램 필터로 변환합니다. 이렇게 하려면 고급 필터 편집기를 닫기 전에 **[!UICONTROL Save]**&#x200B;을(를) 클릭하십시오.

  ![](assets/s_ncs_user_filter_save.png)

* 트리의 **[!UICONTROL Administration > Configuration > Predefined filters]**(또는 수신자의 경우 **[!UICONTROL Profiles and targets > Predefined filters]**) 노드를 통해 이 응용 프로그램 필터를 만듭니다. 이렇게 하려면 필터 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL New...]**&#x200B;을(를) 선택합니다. 이 절차는 고급 필터를 만드는 절차와 동일합니다.

  **[!UICONTROL Label]** 필드를 사용하면 이 필터의 이름을 지정할 수 있습니다. 이 이름은 **[!UICONTROL Filters...]** 단추의 콤보 상자에 나타납니다.

  ![](assets/user_filter_apply.png)

마우스 오른쪽 단추를 클릭하고 **[!UICONTROL No filter]**&#x200B;을(를) 선택하거나 목록 위에 있는 **[!UICONTROL Filters]** 아이콘을 통해 현재 목록의 모든 필터를 삭제할 수 있습니다.

**[!UICONTROL Filters]** 단추를 클릭하고 **[!UICONTROL And...]** 메뉴를 사용하여 필터를 결합할 수 있습니다.

![](assets/s_ncs_user_filter_combination.png)

## 수신자 필터링 {#filtering-recipients}

미리 정의된 필터([필터 저장](#saving-a-filter) 참조)를 사용하면 데이터베이스에 포함된 수신자 프로필을 필터링할 수 있습니다. 트리의 **[!UICONTROL Profiles and Targets > Predefined filters]** 노드에서 필터를 편집할 수 있습니다. **[!UICONTROL Filters]** 단추를 통해 작업 영역의 위쪽 섹션에 필터가 나열됩니다.

필터를 선택하여 해당 정의를 표시하고 필터링된 데이터 미리보기에 액세스합니다.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>미리 정의된 필터를 만드는 자세한 예제는 [사용 사례](../../platform/using/use-case.md)를 참조하세요.

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
   <td> 열었지만 클릭하지 않았습니다.<br /> </td> 
   <td> 게재를 열었지만 링크를 클릭하지 않은 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 비활성 수신자<br /> </td> 
   <td> X개월 동안 게재를 열지 않은 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 장치 유형<br />별 마지막 활동 </td> 
   <td> 지난 Z일 동안 장치 X를 사용하여 배달 Y를 클릭하거나 연 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 장치 유형(추적)별 마지막 활동<br /> </td> 
   <td> 지난 Z일 동안 장치 X를 사용하여 배달 Y를 클릭하거나 연 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 타겟팅되지 않은 받는 사람<br /> </td> 
   <td> X개월 동안 채널 Y를 통해 타겟팅한 적이 없는 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 매우 활성 받는 사람<br /> </td> 
   <td> 지난 Y개월 동안 게재를 X번 이상 클릭한 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
 <td> 차단 목록에 추가된 전자 메일 주소<br /> </td> 
    <td> 전자 메일 주소가 차단 목록에 있는 수신자를 선택합니다.<br/> </td>
  </tr> 
  <tr> 
   <td> 격리된 전자 메일 주소<br /> </td> 
   <td> 전자 메일 주소가 격리된 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> 폴더에 중복된 전자 메일 주소 </td> 
   <td> 폴더에 전자 메일 주소가 중복되는 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 열지도 클릭하지도 않음<br /> </td> 
   <td> 게재를 열지 않았거나 게재를 클릭한 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 수신자(일)<br /> </td> 
   <td> 지난 X일 동안 만든 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 수신자(분)<br /> </td> 
   <td> 지난 X분 동안 만든 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 수신자(개월)<br /> </td> 
   <td> 지난 X개월 동안 만든 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독별<br /> </td> 
   <td> 구독별로 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 특정 링크를 클릭하여<br /> </td> 
   <td> 게재에서 특정 URL을 클릭한 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재 후 동작<br /> </td> 
   <td> 게재를 받은 후 해당 동작에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 만든 날짜<br />까지 </td> 
   <td> X개월(현재 날짜에서 n개월을 뺀 숫자)에서 Y개월(현재 날짜에서 n개월을 뺀 숫자) 사이의 기간 동안 생성 날짜별로 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> 목록별 </td> 
   <td> 목록을 기준으로 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> 지난 X개월 동안 게재를 클릭한 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 메시지 수<br />개 </td> 
   <td> 받은 메시지 수에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기 횟수별<br /> </td> 
   <td> Z 시간 동안 X와 Y 게재 사이에 연 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 이름 또는 전자 메일로<br /> </td> 
   <td> 이름 또는 전자 메일에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 연령 범위별<br /> </td> 
   <td> 나이에 따라 수신자를 선택합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>계산 및 기간에 대한 모든 비교는 넓은 의미로 이해해야 합니다(쿼리 제한에 해당하는 수신자는 비교에 포함됨).

데이터 계산 방식의 예:

* 30세 미만의 수신자를 선택합니다.

  ![](assets/predefined_filters_01.png)

* 18세 이상의 수신자를 선택합니다.

  ![](assets/predefined_filters_03.png)

* 18세에서 30세 사이의 수신자를 선택합니다.

  ![](assets/predefined_filters_02.png)

## 데이터 필터에 대한 고급 설정 {#advanced-settings-for-data-filters}

다음 옵션에 액세스하려면 **[!UICONTROL Settings]** 탭을 클릭하십시오.

* **[!UICONTROL Default filter for the associated document type]**: 이 옵션을 사용하면 정렬과 관련된 목록의 편집기에서 기본적으로 이 필터를 제안할 수 있습니다.

  예를 들어 **[!UICONTROL By name or login]** 필터는 연산자에 적용됩니다. 이 옵션이 선택되어 있으므로 필터가 항상 모든 연산자 목록에서 제공됩니다.

* **[!UICONTROL Filter shared with other operators]**: 이 옵션을 사용하면 현재 데이터베이스의 다른 모든 연산자가 필터를 사용할 수 있습니다.
* **[!UICONTROL Use parameter entry form]**: 이 옵션을 사용하면 이 필터를 선택할 때 목록 위에 표시할 필터 필드를 정의할 수 있습니다. 이러한 필드를 사용하면 필터 설정을 정의할 수 있습니다. 이 양식은 **[!UICONTROL Form]** 단추를 통해 XML 형식으로 입력해야 합니다. 예를 들어 수신자 목록에서 사용할 수 있는 사전 구성된 필터 **[!UICONTROL Recipients who have opened]**&#x200B;에는 필터를 적용할 게재를 선택할 수 있는 필터 필드가 표시됩니다.

  **[!UICONTROL Preview]** 단추는 선택한 필터의 결과를 표시합니다.

* **[!UICONTROL Advanced parameters]** 링크를 사용하여 추가 설정을 정의할 수 있습니다. 특히, SQL 테이블을 필터와 연결하여 테이블을 공유하는 모든 편집기에 공통되도록 할 수 있습니다.

  사용자가 이 필터를 재정의하지 못하도록 하려면 **[!UICONTROL Do not restrict the filter]** 옵션을 선택하십시오.

  이 옵션은 오버로드할 수 없는 게재 도우미에서 제공되는 &quot;게재 수신자&quot; 및 &quot;폴더에 속한 게재 수신자&quot; 필터에 대해 활성화됩니다.

  ![](assets/s_ncs_user_filter_advanced_param.png)
