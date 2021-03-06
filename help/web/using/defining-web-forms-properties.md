---
product: campaign
title: 웹 양식 속성 정의
description: 웹 양식 속성 정의
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 1%

---

# 웹 양식 속성 정의{#defining-web-forms-properties}

![](../../assets/common.svg)

요구 사항을 충족하도록 웹 양식을 완전히 구성하고 개인화할 수 있습니다. 등록 정보 창에 매개변수를 입력해야 합니다.

속성 창은 **[!UICONTROL Properties]** 단추를 클릭합니다. 이 창에서는 웹 양식과 관련된 다양한 설정에 액세스할 수 있습니다. 일부 설정은 템플릿 구성에서 비롯될 수 있습니다.

![](assets/s_ncs_admin_survey_properties_general.png)

## 전체 양식 속성 {#overall-form-properties}

에서 **[!UICONTROL General]** 속성 창의 탭에서 **레이블** 섹션에 있는 마지막 항목이 될 필요가 없습니다. 을 변경하지 않는 것이 좋습니다 **내부 이름**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

양식 서식 파일은 양식을 만드는 동안 선택됩니다. 나중에 변경할 수 없습니다. 양식 템플릿 만들기 및 관리에 대한 자세한 내용은 [웹 양식 템플릿 사용](using-a-web-form-template.md).

## 양식 데이터 저장소 {#form-data-storage}

웹 양식의 필드는 기본적으로 수신자 표에 저장됩니다. 테이블에서 새 테이블을 선택하여 사용하는 테이블을 변경할 수 있습니다 **[!UICONTROL Document type]** 필드. 다음 **[!UICONTROL Zoom]** 아이콘을 사용하면 선택한 테이블의 컨텐트를 볼 수 있습니다.

기본적으로 답변은 **수신자 양식에 응답** 테이블.

## 오류 페이지 설정 {#setting-up-an-error-page}

오류 페이지를 구성할 수 있습니다. 양식 실행 중에 오류가 발생하는 경우 이 페이지가 표시됩니다.

오류 페이지는 양식 속성 창의 해당 탭에 정의됩니다.

기본적으로 다음 정보가 표시됩니다.

![](assets/s_ncs_admin_survey_default_error_page.png)

표시되는 문자열의 컨텐츠는 **[!UICONTROL Error page]** 속성 창의 탭입니다. 다음 **[!UICONTROL HTML]** 탭에는 렌더링 및 **[!UICONTROL Texts]** 탭에서는 텍스트 문자열을 수정하고 필요한 경우 텍스트를 추가할 수 있습니다.

![](assets/s_ncs_admin_survey_error_page.png)

## 양식 로컬라이제이션 {#form-localization}

다음 **[!UICONTROL Localization]** 탭에서는 웹 양식의 디자인 및 표시 언어를 선택할 수 있습니다.

자세한 내용은 [웹 양식 번역](translating-a-web-form.md).

## 양식 탐색 및 렌더링 {#form-browsing-and-rendering}

다음 **[!UICONTROL Rendering]** 탭에서는 웹 양식의 페이지 유형과 사용된 렌더링 템플릿 간의 검색 유형을 정의할 수 있습니다.

링크 또는 단추를 통해 탐색하도록 선택할 수 있습니다.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

버튼은 기본적으로 탐색 요소입니다. 이 구성 요소로 다음 작업을 수행할 수 있습니다.

* 현재 페이지를 승인하고 다음 페이지를 **[!UICONTROL Next]**. 이 단추는 마지막 페이지를 제외한 모든 페이지에 표시됩니다.
* 을 클릭하여 이전 페이지를 표시합니다. **[!UICONTROL Previous]**. 이 단추는 첫 번째 페이지를 제외한 모든 페이지에 표시됩니다.
* 양식 응답을 저장하려면 **[!UICONTROL Approve]** 버튼을 클릭합니다. 이 단추는 마지막 페이지에만 표시됩니다.

이러한 요소는 각 페이지 하단에 표시됩니다. 자세도 바뀔 수 있다. 이를 수행하려면 스타일 시트를 수정해야 합니다.

>[!NOTE]
>
>그리고, **[!UICONTROL Previous]** 일부 페이지의 단추. 이렇게 하려면 관련 페이지로 이동하여 를 확인합니다 **[!UICONTROL Disallow returning to the previous page]** 선택 사항입니다. 이 옵션은 페이지 트리의 루트를 선택한 경우 액세스할 수 있습니다.

다음 **[!UICONTROL Template]** 필드 **[!UICONTROL Rendering]** 탭에서 사용 가능한 테마를 선택할 수 있습니다.

테마는 **[!UICONTROL Administration>Configuration>Form rendering]** 노드 아래에 있어야 합니다. 자세한 내용은 [양식 렌더링 템플릿 선택](form-rendering.md#selecting-the-form-rendering-template)

속성 창의 아래쪽에 샘플 렌더링이 표시됩니다. 다음 **[!UICONTROL Edit link]** 아이콘을 사용하면 선택한 테마의 구성을 볼 수 있습니다.

![](assets/s_ncs_admin_survey_properties_render.png)

## 양식의 텍스트 {#texts-in-the-form}

다음 **[!UICONTROL Page]** 탭에서는 양식 머리글 및 바닥글의 컨텐츠를 정의할 수 있습니다. 자세한 내용은 [머리글 및 바닥글 정의](form-rendering.md#defining-headers-and-footers).

또한 번역을 관리할 수 있습니다. 자세한 내용은 [웹 양식 번역](translating-a-web-form.md).

## 양식의 액세스 가능성 {#accessibility-of-the-form}

웹 양식은 사용자가 액세스할 수 있습니다 **[!UICONTROL Online]** 그리고 현재 날짜가 유효 기간 내에 있는 경우 게시 단계 동안 양식 상태가 수정됩니다(참조 [양식 게시](publishing-a-web-form.md#publishing-a-form)). 상태는 **프로젝트** 섹션 **[!UICONTROL General]** 속성 창의 탭입니다.

유효 기간은 **[!UICONTROL Start]** 날짜 **[!UICONTROL End date]**. 이러한 필드에 날짜가 지정되지 않은 경우 양식은 영구적으로 유효합니다.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>양식이 닫혀 있고, 따라서 유효 기간에 도달하지 않았거나 만료되었거나, Adobe Campaign 연산자가 양식을 닫았다면 사용자가 양식에 액세스하려고 하면 메시지가 표시됩니다. 을(를) 클릭하여 이 메시지를 개인화할 수 있습니다 **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## 양식 액세스 제어 {#form-access-control}

기본적으로 웹 양식에 대한 액세스는 익명 모드에서 수행됩니다. 양식에 액세스하는 모든 운영자에게 WebApp 운영자 권한이 할당됩니다.

사용자를 인증하기 위해 인트라넷 사이트에서 양식을 전달하는 등의 양식 표시에 대한 액세스 제어를 활성화할 수 있습니다. 이렇게 하려면 **[!UICONTROL Properties]** 관련 양식 창에서 **[!UICONTROL Enable access control]** 옵션을 선택합니다.

![](assets/s_ncs_admin_survey_access_ctrl.png)

페이지에 액세스하면 다음 인증 양식이 나타납니다.

![](assets/s_ncs_admin_survey_access_login.png)

로그인 및 암호는 Adobe Campaign 운영자가 사용하는 암호입니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/access-management.md)을 참조하십시오.

다음 **[!UICONTROL Use a specific account]** 옵션을 사용하면 양식에 액세스하는 연산자의 읽기 또는 쓰기 권한을 제한할 수 있습니다. 드롭다운 상자를 사용하여 이러한 권한을 부여할 운영자 또는 운영자 그룹을 선택합니다.

![](assets/s_ncs_admin_survey_access_op_select.png)

## 양식 URL 매개 변수 {#form-url-parameters}

양식의 URL에 매개 변수를 추가하여 콘텐츠를 개인화하고 컨텍스트(언어, 암호화된 수신자 ID, 회사, 변수에 저장된 계산된 수식 등)를 초기화할 수 있습니다. 이렇게 하면 여러 가지 다른 URL을 통해 한 양식에 액세스할 수 있고, URL에 지정된 매개 변수의 값을 기반으로 페이지 컨텐츠를 개인화할 수 있습니다.

기본적으로 Adobe Campaign에서는 양식을 미리 보고 오류를 확인하기 위한 매개 변수를 제공합니다. 양식에 연결된 새 설정을 만들 수 있습니다. 이 설정은 데이터베이스 또는 로컬 변수의 필드 값을 사용할 수 있습니다.

## 표준 매개 변수 {#standard-parameters}

기본적으로 다음 매개 변수를 사용할 수 있습니다.

* **id** 암호화된 식별자를 나타냅니다.
* **lang** 표시 언어를 변경하려면
* **원본** 응답자 출처를 지정합니다.
* **_uuid** 게시 전 및 오류 추적 전에 양식을 볼 수 있도록 합니다. 이 매개 변수는 내부용(만들기 및 디버그): 이 URL을 통해 웹 양식에 액세스하면 생성된 레코드가 추적(보고서)에서 고려되지 않습니다. 원산지는 **[!UICONTROL Adobe Campaign]** 값.

   와 함께 사용됩니다 **_미리 보기** 매개 변수 및/또는 **_debug**:

   **_미리 보기** 마지막으로 저장한 버전을 표시합니다. 이 매개 변수는 테스트 단계에서만 사용해야 합니다.

   **_debug** 를 입력하여 양식의 페이지에서 계산되거나 계산된 데이터 추적을 표시합니다. 양식을 게시한 후 등 오류에 대한 자세한 정보를 제공하는 데 사용됩니다.

   >[!CAUTION]
   >
   >와 함께 URL을 통해 양식이 표시되는 경우 **_uuid** 매개 변수, 값 **[!UICONTROL origin]** 매개 변수는에 강제 적용됩니다. **Adobe Campaign**.

## 매개 변수 추가 {#adding-parameters}

를 통해 매개 변수를 추가할 수 있습니다 **[!UICONTROL Parameters...]** 탭의 값을 설정할 수 있습니다. 다음과 같이 필수로 지정할 수 있습니다.

![](assets/s_ncs_admin_survey_properties_param.png)

매개변수 값을 검색할 저장 위치를 지정해야 합니다. 이렇게 하려면 스토리지 옵션 중 하나를 선택하고 **[!UICONTROL Storage]** 탭하여 관련 필드 또는 변수를 선택합니다. 스토리지 옵션은 [응답 저장소 필드](web-forms-answers.md#response-storage-fields).

그런 다음 양식에 액세스하기 위해 URL에 응답자 상태(0, 1 또는 다른 값)를 추가할 수 있습니다. 이 정보는 양식의 페이지 또는 테스트 상자에서 다시 사용할 수 있습니다. 표시된 페이지는 아래와 같이 컨텍스트의 값을 기준으로 조건을 지정할 수 있습니다.

1. 고객을 위한 홈 페이지(**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 잠재 고객을 위한 홈 페이지(**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 다른 프로필(예: **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

이 양식을 구성하려면 아래 표시된 대로 테스트 상자를 만들어 다이어그램의 시작 위치에 배치합니다.

![](assets/s_ncs_admin_survey_test.png)

테스트 상자를 사용하여 페이지 순서 조건을 구성할 수 있습니다.

![](assets/s_ncs_admin_survey_test_box.png)
