---
title: 웹 양식 페이지 순서 정의
seo-title: 웹 양식 페이지 순서 정의
description: 웹 양식 페이지 순서 정의
seo-description: null
page-status-flag: never-activated
uuid: 297fad62-d806-4bd8-9b8c-313c20344ab0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 85bf3244-6896-43e7-96b8-84c45c282fec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 웹 양식 페이지 순서 정의{#defining-web-forms-page-sequencing}

양식은 하나 이상의 페이지를 포함할 수 있습니다. 페이지 및 테스트, 스크립트 실행 및 페이지 점프 기록 단계를 시퀀스 지정할 수 있는 다이어그램을 통해 구축되었습니다. 다이어그램 구성 모드는 워크플로우와 동일합니다.

## 이전 페이지 및 다음 페이지 정보 {#about-previous-page-and-next-page}

각 페이지에 대해 **[!UICONTROL Next]** 또는 **[!UICONTROL Previous]** 단추를 삭제할 수 있습니다. 이렇게 하려면 관련 페이지를 선택하고 옵션 **[!UICONTROL Disable next page]** 또는 을 선택합니다 **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

이러한 단추를 링크로 바꿀 수 있습니다. HTML [컨텐츠](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)삽입을 참조하십시오.

## 점프 삽입 {#inserting-a-jump}

이 **[!UICONTROL Jump]** 개체는 사용자가 클릭할 때 다른 페이지나 다른 양식에 액세스할 수 **[!UICONTROL Next]**&#x200B;있습니다.

대상은 다음과 같습니다.

* 양식의 다른 페이지. 이렇게 하려면, 아래에서 **[!UICONTROL Internal activity]** 선택한 다음 원하는 페이지를 지정합니다.

   ![](assets/s_ncs_admin_jump_param1.png)

* 다른 양식. 이렇게 하려면 **[!UICONTROL Explicit]** 옵션을 선택하고 대상 양식을 지정합니다.

   ![](assets/s_ncs_admin_jump_param2.png)

* 대상은 변수에 저장할 수 있습니다. 이 경우 아래 표시된 대로 드롭다운 목록에서 선택합니다.

   ![](assets/s_ncs_admin_jump_param3.png)

* 이 **[!UICONTROL Comment]** 탭에서는 연산자가 다이어그램에서 개체를 클릭할 때 표시되는 정보를 입력할 수 있습니다.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## 예:url의 매개 변수에 따라 다른 양식에 액세스 {#example--accessing-another-form-according-to-a-parameter-of-the-url}

다음 예에서는 승인 시 URL의 매개 변수로 지정된 다른 양식을 표시하는 웹 양식을 구성하려고 합니다. 이렇게 하려면 다음 단계를 적용합니다.

1. 양식 끝에 이동 삽입:그러면 **[!UICONTROL End]** 상자가 바뀝니다.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 양식 속성에서 로컬 변수(**다음**)에 저장된 매개 변수(**다음**)를 추가합니다. 로컬 변수는 로컬 변수에 [데이터 저장에](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)자세히 설명되어 있습니다.

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 객체를 편집하고 **[!UICONTROL Jump]** 옵션을 선택한 다음 드롭다운 상자에서 **[!UICONTROL Stored in a variable]** 다음 **** 변수를 선택합니다.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 배달 URL에는 대상 양식의 내부 이름이 포함되어야 합니다. 예:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   사용자가 **[!UICONTROL Approve]** 단추를 클릭하면 양식 APP22 **가** 표시됩니다.

## 양식의 다른 페이지에 대한 링크 삽입 {#inserting-a-link-to-another-page-of-the-form}

양식의 다른 페이지에 대한 링크를 삽입할 수 있습니다. 이렇게 하려면 페이지에 **[!UICONTROL Link]** 유형 정적 요소를 추가합니다. 자세한 내용은 링크 [삽입을](../../web/using/static-elements-in-a-web-form.md#inserting-a-link)참조하십시오.

## 조건부 페이지 표시 {#conditional-page-display}

### 응답을 기반으로 표시 {#display-based-on-responses}

이 **[!UICONTROL Test]** 상자를 사용하면 양식의 페이지 순서를 지정할 수 있습니다. 테스트 결과에 따라 다양한 분기 라인을 정의할 수 있습니다. 이렇게 하면 사용자가 제공한 응답에 따라 다른 페이지를 표시할 수 있습니다.

예를 들어 이미 온라인으로 주문한 고객의 경우 다른 페이지를 표시하고 10개 이상의 주문을 제출한 고객의 경우 다른 페이지를 표시할 수 있습니다. 이렇게 하려면 양식의 첫 페이지에 사용자가 주문한 주문 수를 표시할 **[!UICONTROL Number]** 입력 필드를 삽입합니다.

![](assets/s_ncs_admin_survey_test_ex0.png)

이 정보를 데이터베이스의 필드에 저장하거나 로컬 변수를 사용할 수 있습니다.

>[!NOTE]
>
>스토리지 모드는 응답 스토리지 [필드에](../../web/using/web-forms-answers.md#response-storage-fields)자세히 설명되어 있습니다.

이 예에서는 변수를 사용합니다.

![](assets/s_ncs_admin_survey_test_ex1.png)

양식 다이어그램에 조건을 정의하려면 테스트 상자를 삽입합니다. 각 조건에 대해 새 분기가 테스트 상자의 출력에 추가됩니다.

![](assets/s_ncs_admin_survey_test_ex2.png)

조건이 모두 충족되지 않는 경우에 전환을 추가하려면 이 **[!UICONTROL Activate the default branching]** 옵션을 선택합니다. 가능한 모든 대/소문자가 정의된 조건에 따라 적용되는 경우 이 옵션은 불필요합니다.

그런 다음 하나 이상의 조건이 참일 때 페이지 순서를 정의합니다. 예를 들면 다음과 같습니다.

![](assets/s_ncs_admin_survey_test_ex3.png)

### 매개 변수를 기반으로 표시 {#display-based-on-parameters}

웹 양식의 초기화 매개변수 또는 데이터베이스에 저장된 값에 따라 페이지 순서를 개인화할 수도 있습니다. 양식 [URL 매개 변수를](../../web/using/defining-web-forms-properties.md#form-url-parameters)참조하십시오.

## 스크립트 추가 {#adding-scripts}

이 **[!UICONTROL Script]** 개체를 사용하면 필드 값을 수정하거나 데이터베이스에서 데이터를 검색하거나 Adobe Campaign API를 호출하는 등 JavaScript 스크립트를 직접 입력할 수 있습니다.

## 최종 페이지 개인화 {#personalizing-the-end-page}

다이어그램 끝에 끝 페이지를 배치해야 합니다. 사용자가 웹 양식의 **[!UICONTROL Approve]** 단추를 클릭하면 끝 페이지가 표시됩니다.

이 페이지를 개인화하려면, 두 번 **[!UICONTROL End]** 클릭하고 페이지 컨텐츠를 중앙 편집기에 입력합니다.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 기존 HTML 컨텐츠를 복사하여 붙여넣을 수 있습니다. 이렇게 하려면 HTML 코드를 클릭하고 **[!UICONTROL Display source code]** 삽입합니다.
* 외부 URL을 사용할 수 있습니다.이렇게 하려면 해당 옵션을 선택하고 표시할 페이지의 URL을 입력합니다.

