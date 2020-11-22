---
solution: Campaign Classic
product: campaign
title: 웹 양식 페이지 순서 정의
description: 웹 양식 페이지 순서 정의
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 2%

---


# 웹 양식 페이지 순서 정의{#defining-web-forms-page-sequencing}

양식에 하나 이상의 페이지가 포함될 수 있습니다. 페이지 시퀀스 및 테스트, 스크립트 실행 및 페이지 점프 기록 단계를 위한 다이어그램을 통해 구축됩니다. 다이어그램 구성 모드는 워크플로우와 동일합니다.

## 이전 페이지 및 다음 페이지 정보 {#about-previous-page-and-next-page}

각 페이지에 대해 **[!UICONTROL Next]** 또는 **[!UICONTROL Previous]** 단추를 삭제할 수 있습니다. 이렇게 하려면 관련 페이지를 선택하고 옵션 **[!UICONTROL Disable next page]** 또는 을 선택합니다 **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

이 단추를 링크로 바꿀 수 있습니다. HTML [컨텐츠 삽입을 참조하십시오](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

## 점프 삽입 {#inserting-a-jump}

이 **[!UICONTROL Jump]** 개체는 사용자가 클릭할 때 다른 페이지나 다른 양식에 액세스할 수 있게 합니다 **[!UICONTROL Next]**.

대상은 다음과 같습니다.

* 양식의 다른 페이지입니다. 이렇게 하려면 아래 **[!UICONTROL Internal activity]** 와 같이 원하는 페이지를 선택하고 지정합니다.

   ![](assets/s_ncs_admin_jump_param1.png)

* 다른 양식. 이렇게 하려면 옵션을 선택하고 **[!UICONTROL Explicit]** 대상 양식을 지정합니다.

   ![](assets/s_ncs_admin_jump_param2.png)

* 대상은 변수에 저장할 수 있습니다. 이 경우 아래 표시된 대로 드롭다운 목록에서 선택합니다.

   ![](assets/s_ncs_admin_jump_param3.png)

* 이 **[!UICONTROL Comment]** 탭에서는 연산자가 다이어그램에서 개체를 클릭할 때 표시되는 정보를 입력할 수 있습니다.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## 예:URL의 매개 변수에 따라 다른 양식에 액세스 {#example--accessing-another-form-according-to-a-parameter-of-the-url}

다음 예에서는, 승인 시 URL의 매개 변수로 지정된 다른 양식을 표시하는 웹 양식을 구성하려고 합니다. 이렇게 하려면 다음 단계를 적용합니다.

1. 양식 끝에 이동 삽입:이 필드는 **[!UICONTROL End]** 상자를 대체합니다.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 양식 속성에서 로컬 변수에 저장된 매개 변수(**다음**)를&#x200B;**추가합니다**. 로컬 변수는 로컬 변수에 [데이터 저장에 자세히 설명되어 있습니다](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable).

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 개체를 **[!UICONTROL Jump]** 편집하고 **[!UICONTROL Stored in a variable]** 옵션을 선택한 다음 드롭다운 상자에서 **다음** 변수를 선택합니다.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 배달 URL에는 대상 양식의 내부 이름이 포함되어야 합니다. 예:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   사용자가 **[!UICONTROL Approve]** 단추를 클릭하면 양식 **APP22가** 표시됩니다.

## 양식의 다른 페이지에 링크 삽입 {#inserting-a-link-to-another-page-of-the-form}

양식의 다른 페이지에 대한 링크를 삽입할 수 있습니다. 이렇게 하려면 페이지에 **[!UICONTROL Link]** 유형 정적 요소를 추가합니다. 자세한 내용은 링크 [삽입을 참조하십시오](../../web/using/static-elements-in-a-web-form.md#inserting-a-link).

## 조건부 페이지 표시 {#conditional-page-display}

### 응답을 기반으로 표시 {#display-based-on-responses}

이 **[!UICONTROL Test]** 상자를 사용하면 양식에서 페이지의 순서를 지정할 수 있습니다. 테스트 결과에 따라 다양한 분기 라인을 정의할 수 있습니다. 사용자가 제공한 응답에 따라 다른 페이지를 표시할 수 있습니다.

예를 들어, 이미 온라인으로 주문한 고객의 경우, 10개 이상의 주문을 제출한 고객의 경우 다른 페이지를 표시할 수 있습니다. 이렇게 하려면 양식의 첫 페이지에 사용자가 주문한 항목 수를 표시할 **[!UICONTROL Number]** 입력 필드를 삽입합니다.

![](assets/s_ncs_admin_survey_test_ex0.png)

이 정보를 데이터베이스 필드에 저장하거나 로컬 변수를 사용할 수 있습니다.

>[!NOTE]
>
>스토리지 모드는 응답 저장소 필드에 [자세히 나와 있습니다](../../web/using/web-forms-answers.md#response-storage-fields).

이 예에서는 변수를 사용하려고 합니다.

![](assets/s_ncs_admin_survey_test_ex1.png)

양식 다이어그램에 조건을 정의하려면 테스트 상자를 삽입합니다. 각 조건에 대해 새 분기가 테스트 상자의 출력에 추가됩니다.

![](assets/s_ncs_admin_survey_test_ex2.png)

조건이 true가 아닌 경우 전환을 추가하려면 옵션을 **[!UICONTROL Activate the default branching]** 선택합니다. 가능한 모든 대/소문자를 정의된 조건으로 덮는 경우 이 옵션은 불필요합니다.

다음, 하나 또는 다른 조건이 참이면 페이지 순서를 정의합니다. 예를 들면 다음과 같습니다.

![](assets/s_ncs_admin_survey_test_ex3.png)

### 매개 변수를 기반으로 표시 {#display-based-on-parameters}

웹 양식의 초기화 매개 변수 또는 데이터베이스에 저장된 값에 따라 페이지 순서를 개인화할 수도 있습니다. 양식 [URL 매개 변수를 참조하십시오](../../web/using/defining-web-forms-properties.md#form-url-parameters).

## 스크립트 추가 {#adding-scripts}

이 **[!UICONTROL Script]** 객체를 사용하면 필드 값을 수정하거나 데이터베이스에서 데이터를 검색하거나 Adobe Campaign API를 호출하는 등 JavaScript 스크립트를 직접 입력할 수 있습니다.

## 최종 페이지 개인화 {#personalizing-the-end-page}

다이어그램 끝에 종료 페이지를 배치해야 합니다. 사용자가 웹 양식의 **[!UICONTROL Approve]** 단추를 클릭하면 종료 페이지가 표시됩니다.

이 페이지를 개인화하려면 두 번 **[!UICONTROL End]** 을 클릭하고 페이지 컨텐츠를 중앙 편집기에 입력합니다.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 기존 HTML 컨텐츠를 복사하고 붙여넣을 수 있습니다. 이렇게 하려면 을 클릭하고 HTML 코드 **[!UICONTROL Display source code]** 를 삽입합니다.
* 외부 URL을 사용할 수 있습니다.이렇게 하려면 해당 옵션을 선택하고 표시할 페이지의 URL을 입력합니다.

