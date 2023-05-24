---
product: campaign
title: 웹 양식 답변
description: 웹 양식 답변
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Forms
exl-id: 5d48bb27-1884-47f1-acb7-dff5113565bc
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---

# 웹 양식 답변{#web-forms-answers}


## 응답 스토리지 필드 {#response-storage-fields}

양식에 대한 답변은 데이터베이스의 필드 또는 일시적으로 로컬 변수에 저장할 수 있습니다. 답변을 위한 저장 모드는 필드 생성 중에 선택됩니다. 를 통해 편집할 수 있습니다. **[!UICONTROL Edit storage...]** 링크를 클릭합니다.

양식의 각 입력 필드에 대해 다음 저장소 옵션을 사용할 수 있습니다.

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   데이터베이스의 필드를 선택할 수 있습니다. 사용자의 답변은 이 필드에 저장됩니다. 각 사용자에 대해 마지막으로 입력한 값만 저장됩니다. 이 값이 해당 프로필에 추가됩니다. 참조: [데이터베이스에 데이터 저장](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   데이터베이스에 정보를 저장하지 않으려면 변수를 사용할 수 있습니다. 로컬 변수는 업스트림으로 선언할 수 있습니다. 을(를) 참조하십시오 [로컬 변수에 데이터 저장](#storing-data-in-a-local-variable).

### 데이터베이스에 데이터 저장 {#storing-data-in-the-database}

데이터베이스의 기존 필드에 데이터를 저장하려면 **[!UICONTROL Edit expression]** 아이콘을 클릭하고 사용 가능한 필드 목록에서 선택합니다.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>기본 참조 문서는 **nms:recipient** 스키마. 양식을 보거나 새 양식을 선택하려면 목록에서 양식을 선택하고 **[!UICONTROL Properties]** 단추를 클릭합니다.

### 로컬 변수에 데이터 저장 {#storing-data-in-a-local-variable}

로컬 변수를 사용하면 데이터가 데이터베이스에 저장되지 않더라도 페이지나 다른 페이지에서 다시 사용할 수 있습니다. 예를 들어 필드를 표시하거나 메시지를 개인화하는 데 조건을 사용할 수 있습니다.

즉, 저장되지 않은 필드의 값을 사용하여 페이지에 옵션 그룹을 표시하는 권한을 부여할 수 있습니다. 아래 페이지에서 차량 유형은 데이터베이스에 저장되지 않습니다.

![](assets/s_ncs_admin_survey_no_storage_variable.png)

드롭다운 상자를 만들 때 선택해야 하는 변수에 저장되거나 **[!UICONTROL Edit storage...]** 링크를 클릭합니다.

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

를 통해 기존 변수를 표시하고 새 변수를 만들 수 있습니다. **[!UICONTROL Edit variables...]** 링크를 클릭합니다. 다음을 클릭합니다. **[!UICONTROL Add]** 단추를 클릭하여 새 변수를 만듭니다.

![](assets/s_ncs_admin_survey_add_a_variable.png)

추가된 변수는 페이지의 입력 필드가 만들어질 때 로컬 변수 목록에서 사용할 수 있습니다.

>[!NOTE]
>
>각 양식에 대해 변수를 업스트림으로 만들 수 있습니다. 이렇게 하려면 양식을 선택하고 **[!UICONTROL Properties]** 단추를 클릭합니다. 다음 **[!UICONTROL Variables]** 탭에는 양식에 대한 로컬 변수가 포함되어 있습니다.

**컨디셔닝이 포함된 로컬 스토리지의 예**

위의 예에서, 개인 차량에 관한 데이터를 포함하는 컨테이너는 다음 경우에만 표시됩니다. **[!UICONTROL Private]** 가시성 조건에 표시된 대로 드롭다운 목록에서 옵션이 선택됩니다.

![](assets/s_ncs_admin_survey_add_a_condition.png)

사용자가 개인 차량을 선택하면 웹 양식에서 다음 옵션을 제공합니다.

![](assets/s_ncs_admin_survey_no_storage_conda.png)

Professional 옵션을 선택하면 가시성 조건으로 표현된 대로 상용차 관련 데이터를 담는 컨테이너가 표시됩니다.

![](assets/s_ncs_admin_survey_view_a_condition.png)

즉, 사용자가 상용 차량을 선택하면 양식에서 다음 옵션을 제공합니다.

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## 수집된 정보 사용 {#using-collected-information}

각 양식에 대해 제공된 답변을 필드 또는 레이블에서 다시 사용할 수 있습니다. 다음 구문을 사용해야 합니다.

* 데이터베이스의 필드에 저장된 콘텐츠의 경우:

   ```
   <%=ctx.recipient.@field name%
   ```

* 로컬 변수에 저장된 콘텐츠의 경우:

   ```
   <%= ctx.vars.variable name %
   ```

* HTML 텍스트 필드에 저장된 콘텐츠의 경우:

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >에 대한 다른 필드와 달리 `<%=` 문자는 이스케이프 문자로 대체되며 HTML 콘텐츠는 `<%==` 구문.

## 웹 양식 답변 저장 중 {#saving-web-forms-answers}

양식의 페이지에 수집된 정보를 저장하려면 다이어그램에 저장소 상자를 배치해야 합니다.

![](assets/s_ncs_admin_survey_save_box.png)

이 상자를 사용하는 방법에는 두 가지가 있습니다.

* 전자 메일로 보낸 링크를 통해 웹 양식에 액세스하고 응용 프로그램에 액세스하는 사용자가 데이터베이스에 이미 있는 경우 **[!UICONTROL Update the preloaded record]** 옵션을 선택합니다. 자세한 내용은 다음을 참조하십시오. [이메일을 통해 양식 게재](publishing-a-web-form.md#delivering-a-form-via-email).

   이 경우 Adobe Campaign은 사용자 프로필의 암호화된 기본 키, Adobe Campaign에서 각 프로필에 할당한 고유 식별자를 사용합니다. 미리 로드 상자를 통해 미리 로드할 정보를 구성해야 합니다. 자세한 내용은 다음을 참조하십시오. [양식 데이터 미리 로드](publishing-a-web-form.md#pre-loading-the-form-data).

   >[!CAUTION]
   >
   >이 옵션은 입력할 필드가 있는 경우 이메일 주소를 포함하여 사용자 데이터를 무시합니다. 새 프로필을 만드는 데 사용할 수 없으며 양식의 미리 로드 상자를 사용해야 합니다.

* 데이터베이스에서 수신자 데이터를 보강하려면 저장소 상자를 편집하고 조정 키를 선택합니다. 내부 사용(일반적으로 인트라넷 시스템)이나 예를 들어 새 프로필을 만드는 데 사용되는 양식의 경우 조정 필드를 선택할 수 있습니다. 이 상자는 웹 응용 프로그램의 여러 페이지에 사용되는 데이터베이스의 모든 필드를 제공합니다.

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

기본적으로 데이터는 다음을 통해 데이터베이스로 가져옵니다. **[!UICONTROL Update or insertion]** 작업: 데이터베이스에 있으면 요소가 업데이트됩니다(예: 선택한 뉴스레터 또는 입력한 이메일 주소). 존재하지 않는 경우 정보가 추가됩니다.

그러나 이 비헤이비어를 변경할 수 있습니다. 이렇게 하려면 요소의 루트를 선택하고 드롭다운 목록에서 수행할 작업을 선택합니다.

![](assets/s_ncs_admin_survey_save_operation.png)

조정을 위한 검색 폴더와 새 프로파일을 위한 생성 폴더를 선택할 수 있습니다. 이러한 필드가 비어 있으면 프로필이 검색되어 연산자의 기본 폴더에서 생성됩니다.

>[!NOTE]
>
>가능한 작업은 다음과 같습니다. **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>연산자의 기본 폴더는 연산자에 쓰기 권한이 있는 첫 번째 폴더입니다.\
>[이 섹션](../../platform/using/access-management.md)을 참조하십시오.
