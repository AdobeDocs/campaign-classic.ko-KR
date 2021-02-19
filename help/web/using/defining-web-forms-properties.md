---
solution: Campaign Classic
product: campaign
title: 웹 양식 속성 정의
description: 웹 양식 속성 정의
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 1%

---


# 웹 양식 속성 정의{#defining-web-forms-properties}

웹 양식은 사용자의 요구 사항을 충족하도록 구성 가능하고 개인화할 수 있습니다. 매개 변수는 속성 창에 입력해야 합니다.

속성 창은 웹 양식 도구 모음의 **[!UICONTROL Properties]** 단추를 통해 액세스할 수 있습니다. 이 창을 사용하면 웹 양식에만 적용되는 다양한 설정에 액세스할 수 있습니다. 일부 설정은 템플릿 구성에서 유래할 수 있습니다.

![](assets/s_ncs_admin_survey_properties_general.png)

## 전체 양식 속성 {#overall-form-properties}

속성 창의 **[!UICONTROL General]** 탭에서 양식의 **레이블**&#x200B;을 수정할 수 있습니다. **내부 이름**&#x200B;을 변경하지 않는 것이 좋습니다.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

양식 서식 파일은 양식을 만드는 동안 선택됩니다. 나중에 변경할 수 없습니다. 양식 템플릿 만들기 및 관리에 대한 자세한 내용은 [웹 양식 템플릿 사용](../../web/using/using-a-web-form-template.md)을 참조하십시오.

## 양식 데이터 저장소 {#form-data-storage}

웹 양식의 필드는 기본적으로 수신자 표에 저장됩니다. **[!UICONTROL Document type]** 필드에서 새 테이블을 선택하여 사용하는 테이블을 변경할 수 있습니다. **[!UICONTROL Zoom]** 아이콘을 사용하여 선택한 테이블의 내용을 볼 수 있습니다.

기본적으로 답변은 **수신자 양식** 테이블에 저장됩니다.

## 오류 페이지 {#setting-up-an-error-page} 설정

오류 페이지를 구성할 수 있습니다.이 페이지는 양식 실행 중 오류가 발생한 경우에 표시됩니다.

오류 페이지는 양식 속성 창의 해당 탭에 정의됩니다.

기본적으로 다음 정보가 표시됩니다.

![](assets/s_ncs_admin_survey_default_error_page.png)

표시되는 문자열의 내용은 속성 창의 **[!UICONTROL Error page]** 탭에 정의됩니다. **[!UICONTROL HTML]** 탭에는 렌더링이 표시되고 **[!UICONTROL Texts]** 탭에서는 텍스트 문자열을 수정하고 필요한 경우 텍스트를 추가할 수 있습니다.

![](assets/s_ncs_admin_survey_error_page.png)

## 양식 현지화 {#form-localization}

**[!UICONTROL Localization]** 탭에서는 웹 양식의 디자인 및 표시 언어를 선택할 수 있습니다.

[웹 양식 번역](../../web/using/translating-a-web-form.md)을 참조하십시오.

## 양식 찾기 및 렌더링 {#form-browsing-and-rendering}

**[!UICONTROL Rendering]** 탭에서는 웹 양식의 페이지와 사용된 렌더링 템플릿 간 검색 유형을 정의할 수 있습니다.

링크나 단추를 통해 탐색하도록 선택할 수 있습니다.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

단추는 기본적으로 탐색 요소입니다. 이 구성 요소를 사용하면 다음 작업을 수행할 수 있습니다.

* 현재 페이지를 승인하고 **[!UICONTROL Next]**&#x200B;을 클릭하여 다음 페이지를 표시합니다. 이 단추는 마지막 단추를 제외한 모든 페이지에 표시됩니다.
* **[!UICONTROL Previous]**&#x200B;을 클릭하여 이전 페이지를 표시합니다. 이 단추는 첫 번째 단추를 제외한 모든 페이지에 표시됩니다.
* **[!UICONTROL Approve]** 단추를 클릭하여 양식 응답을 저장합니다. 이 단추는 마지막 페이지에만 표시됩니다.

이러한 요소는 각 페이지 하단에 표시됩니다. 자세도 바뀔 수 있다. 이렇게 하려면 스타일 시트를 수정해야 합니다.

>[!NOTE]
>
>일부 페이지에서 **[!UICONTROL Previous]** 단추를 숨길 수 있습니다. 이렇게 하려면 관련 페이지로 이동하여 **[!UICONTROL Disallow returning to the previous page]** 옵션을 선택합니다. 이 옵션은 페이지 트리의 루트가 선택된 경우 액세스할 수 있습니다.

**[!UICONTROL Rendering]** 탭의 **[!UICONTROL Template]** 필드에서 사용 가능한 테마를 선택할 수 있습니다.

테마는 트리의 **[!UICONTROL Administration>Configuration>Form rendering]** 노드에 저장됩니다. [양식 렌더링 템플릿 선택](../../web/using/form-rendering.md#selecting-the-form-rendering-template)을 참조하십시오.

샘플 렌더링은 속성 창의 아래쪽에 표시됩니다. **[!UICONTROL Edit link]** 아이콘을 사용하여 선택한 테마에 대한 구성을 볼 수 있습니다.

![](assets/s_ncs_admin_survey_properties_render.png)

## {#texts-in-the-form} 형식의 텍스트

**[!UICONTROL Page]** 탭에서는 양식 머리글과 바닥글의 컨텐츠를 정의할 수 있습니다. [머리글 및 바닥글 정의](../../web/using/form-rendering.md#defining-headers-and-footers)를 참조하십시오.

또한 번역을 관리할 수 있습니다. [웹 양식 번역](../../web/using/translating-a-web-form.md)을 참조하십시오.

## 양식 {#accessibility-of-the-form} 액세서빌러티

웹 양식은 **[!UICONTROL Online]**&#x200B;이고 현재 날짜가 유효 기간 이내인 경우 사용자가 액세스할 수 있습니다. 게시 단계 동안 양식 상태가 수정되었습니다([양식 게시](../../web/using/publishing-a-web-form.md#publishing-a-form) 참조). 상태는 속성 창의 **[!UICONTROL General]** 탭의 **프로젝트** 섹션에 표시됩니다.

유효 기간은 **[!UICONTROL Start]** 날짜에서 **[!UICONTROL End date]**&#x200B;로 실행됩니다. 이 필드에 날짜가 지정되지 않은 경우 양식의 유효성은 영구적입니다.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>양식이 닫혀 있고, 따라서 유효 기간에 도달하지 않았거나 만료되었거나, Adobe Campaign 연산자에 의해 닫혀 있는 경우, 사용자가 양식에 액세스하려고 하면 메시지가 표시됩니다. **[!UICONTROL Personalize the message displayed if the form is closed...]**&#x200B;을 클릭하여 이 메시지를 개인화할 수 있습니다.

## 양식 액세스 제어 {#form-access-control}

기본적으로 웹 양식에 대한 액세스는 익명 모드에서 수행됩니다.양식에 액세스하는 모든 연산자에게는 WebApp 연산자 권한이 할당됩니다.

사용자를 인증하기 위해 인트라넷 사이트에서 양식을 제공할 때와 같이 양식 표시에 대한 액세스 제어를 활성화할 수 있습니다. 이렇게 하려면 아래 표시된 대로 해당 양식의 **[!UICONTROL Properties]** 창을 표시하고 **[!UICONTROL Enable access control]** 옵션을 클릭합니다.

![](assets/s_ncs_admin_survey_access_ctrl.png)

페이지에 액세스하면 다음 인증 양식이 나타납니다.

![](assets/s_ncs_admin_survey_access_login.png)

로그인 및 암호는 Adobe Campaign 연산자가 사용하는 암호입니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/access-management.md)을 참조하십시오.

**[!UICONTROL Use a specific account]** 옵션을 사용하면 양식에 액세스하는 연산자의 읽기 또는 쓰기 권한을 제한할 수 있습니다. 드롭다운 상자를 사용하여 이러한 권한을 부여할 연산자 또는 연산자 그룹을 선택합니다.

![](assets/s_ncs_admin_survey_access_op_select.png)

## 양식 URL 매개 변수 {#form-url-parameters}

양식의 URL에 추가 매개 변수를 추가하여 컨텐트를 개인화하고 컨텍스트(언어, 암호화된 수신자 ID, 회사, 변수에 저장된 계산된 공식 등)를 초기화할 수 있습니다. 이렇게 하면 여러 개의 다른 URL을 통해 하나의 양식에 액세스할 수 있고 URL에 지정된 매개 변수의 값을 기반으로 페이지 컨텐츠를 개인화할 수 있습니다.

기본적으로 Adobe Campaign에서는 양식을 미리 보고 오류를 확인하는 매개 변수를 제공합니다. 데이터베이스에 있는 필드 또는 로컬 변수의 값을 사용할 수 있는 양식에 연결된 새 설정을 만들 수 있습니다.

## 표준 매개 변수 {#standard-parameters}

기본적으로 다음 매개 변수를 사용할 수 있습니다.

* **암호화된** 식별자를 나타냅니다.
* **언어** 로 표시 언어를 변경합니다.
* **응답자** 의 원본을 처음 지정합니다.
* **게시 전** 에 양식 보기를 활성화하고 오류 추적을 사용합니다(_uuiddid). 이 매개 변수는 내부용(만들기 및 디버그)입니다.이 URL을 통해 웹 양식에 액세스하면 생성된 레코드가 추적(보고서)에서 고려되지 않습니다. 원점은 **[!UICONTROL Adobe Campaign]** 값으로 강제 지정됩니다.

   이 매개 변수는 **_preview** 매개 변수 및/또는 **_debug**&#x200B;와 함께 사용됩니다.

   **_** previewing을 클릭하여 마지막으로 저장한 버전을 표시합니다. 이 매개 변수는 테스트 단계에서만 사용해야 합니다.

   **_** debuggto display the trace of the data input or calculated in the page of the form 양식을 게시한 후 등 오류에 대한 자세한 정보를 얻는 데 사용됩니다.

   >[!CAUTION]
   >
   >양식이 **_uuid** 매개 변수가 있는 URL을 통해 표시되는 경우 **[!UICONTROL origin]** 매개 변수의 값은 **Adobe Campaign**&#x200B;에 강제 지정됩니다.

## 매개 변수 {#adding-parameters} 추가

양식의 속성 창에서 **[!UICONTROL Parameters...]** 탭을 통해 매개 변수를 추가할 수 있습니다. 아래와 같이 이를 필수 항목으로 지정할 수 있습니다.

![](assets/s_ncs_admin_survey_properties_param.png)

매개 변수의 값을 검색할 저장 위치를 지정해야 합니다. 이렇게 하려면 저장소 옵션 중 하나를 선택한 다음 **[!UICONTROL Storage]** 탭을 클릭하여 해당 필드나 변수를 선택합니다. 저장소 옵션은 [응답 저장소 필드](../../web/using/web-forms-answers.md#response-storage-fields)에 자세히 설명되어 있습니다.

그런 다음 양식에 액세스하기 위해 URL에 응답자 상태(0, 1 또는 기타 값)를 추가할 수 있습니다. 이 정보는 양식의 페이지 또는 테스트 상자에서 다시 사용할 수 있습니다. 표시되는 페이지는 아래와 같이 컨텍스트의 값을 기준으로 수준을 설정할 수 있습니다.

1. 고객용 홈 페이지(**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 잠재 고객을 위한 홈 페이지(**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 다른 프로필의 홈 페이지(예: **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

이 양식을 구성하려면 아래 표시된 대로 테스트 상자를 만들어 다이어그램의 시작 부분에 배치합니다.

![](assets/s_ncs_admin_survey_test.png)

테스트 상자를 사용하여 페이지 순서 조건을 구성할 수 있습니다.

![](assets/s_ncs_admin_survey_test_box.png)

