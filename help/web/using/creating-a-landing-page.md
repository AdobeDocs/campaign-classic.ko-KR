---
title: 랜딩 페이지 만들기
seo-title: 랜딩 페이지 만들기
description: 랜딩 페이지 만들기
seo-description: null
page-status-flag: never-activated
uuid: fc0e9749-f44e-4aa0-bdfa-6f44ba570bea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 5f1e5886-628f-4c9e-80c1-d82feec23e8c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 랜딩 페이지 만들기{#creating-a-landing-page}

## 랜딩 페이지 생성 정보 {#about-landing-pages-creation}

이 사용 사례는 디지털 편집기를 사용하여 Adobe Campaign 콘솔에서 랜딩 페이지를 만드는 방법을 보여줍니다.

Adobe Campaign에서 랜딩 페이지 구성을 시작하기 전에 HTML 페이지를 나타내는 템플릿이 **하나 이상** 있어야 합니다.

이 사용 사례의 주요 목표는 랜딩 페이지 양식 필드가 DCE의 함수를 사용하여 Adobe Campaign의 내부 필드와 일치하도록 하는 것입니다.

## 랜딩 페이지 만들기 {#creating-the-landing-page}

새 랜딩 페이지 유형 웹 응용 프로그램을 만들려면 다음 단계를 따르십시오.

1. 탭으로 **[!UICONTROL Campaigns]** 이동하고 **[!UICONTROL Web application]** 링크를 클릭한 다음 **[!UICONTROL Create]** 단추를 클릭합니다.
1. 템플릿을 **[!UICONTROL New landing page]** 선택하고 레이블을 입력한 다음 을 클릭합니다 **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. 탭을 **[!UICONTROL Edit]** 클릭합니다.
1. 종료 **활동을** 삭제합니다.
1. 활동 후에 **[!UICONTROL Page]** 활동을 **[!UICONTROL Storage]** 추가합니다.
1. 페이지 **2** 활동을 편집한 다음 **[!UICONTROL Activate outbound transitions]** 탭에서 **[!UICONTROL Properties]** 옵션의 선택을 취소합니다.

   ![](assets/dce_uc1_transition.png)

1. 변경 내용을 저장합니다.

그런 다음 다음 순서를 가져옵니다.

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>웹 응용 프로그램 만들기에 대한 자세한 내용은 [이 섹션을](../../web/using/creating-a-new-web-application.md)참조하십시오.

## 1단계 - 템플릿 선택 및 로드 {#step-1---selecting-and-loading-templates}

이 섹션에서는 웹 애플리케이션의 각 페이지에 대한 HTML 컨텐츠를 **** 가져오는 방법을 살펴봅니다.

템플릿에는 다음이 포함되어야 합니다.

* HTML **파일** (필수)
* 하나 이상의 **CSS** 파일(선택 사항)
* 하나 이상의 **이미지** (선택 사항)

첫 번째 페이지에서 템플릿을 로드하려면 다음 단계를 적용합니다.

1. 웹 애플리케이션의 첫 번째 **[!UICONTROL Page]** 활동을 엽니다.
1. 컨텐츠 템플릿을 **[!UICONTROL From a file]** 페치하려면 선택합니다.

   ![](assets/dce_uc1_selectmodel.png)

1. 사용할 HTML 파일을 선택합니다.
1. 열기를 **클릭하여** 가져오기를 시작합니다.

   로드하는 동안 공유 파일 목록이 표시됩니다. 가져오기 시스템에서는 선택한 HTML에 연결된 모든 파일(CSS, 이미지 등)이 있는지 확인합니다.

   가져오기가 완료되면 **[!UICONTROL Close]** 단추를 클릭합니다.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >닫기 전에 다음 메시지가 표시될 때까지 기다려야 합니다. **[!UICONTROL The external resources have been successfully published]** 을 클릭합니다.

1. 탭을 **[!UICONTROL Properties]** 클릭합니다.
1. 각 페이지에 대한 **레이블을** 입력합니다(예:페이지 1= 수집, 페이지 2=감사).

   ![](assets/dce_uc1_pagelabel.png)

웹 애플리케이션에 삽입된 각 페이지에 대해 다음 단계를 적용합니다.

>[!CAUTION]
>
>**DCE는 로드된 HTML 페이지에 대한 JavaScript 코드를 실행합니다.** Adobe Campaign 인터페이스에 표시될 수 있는 HTML 템플릿의 JavaScript 오류입니다. 이러한 오류는 편집기와 관련이 없습니다. 가져온 파일에 오류가 없는지 확인하려면 파일을 DCE로 가져오기 전에 브라우저(Internet Explorer / Firefox / Chrome)에서 테스트하는 것이 좋습니다.

## 2단계 - 컨텐츠 구성 {#step-2---configuring-the-content}

이 섹션에서는 가져온 컨텐츠를 조정하고 데이터베이스의 필드를 웹 페이지의 양식에 연결합니다. 이전에 만든 웹 응용 프로그램은 다음과 같습니다.

![](assets/dce_uc1_lp_enchainement.png)

### 컨텐츠 수정 {#modifying-content}

먼저 페이지의 색상을 변경해 보겠습니다. 이렇게 하려면:

1. 페이지를 **[!UICONTROL Collection]** 엽니다.
1. 배경을 클릭합니다.
1. 오른쪽에 **있는 배경색을** 클릭합니다.
1. 새 배경색을 선택합니다.
1. 확인을 **클릭하여** 변경을 확인합니다.

   ![](assets/dce_uc1_changecolor.png)

1. 동일한 프로세스를 적용하여 단추 색상 변경

   ![](assets/dce_uc1_finalcolor.png)

### 양식 필드 연결 {#linking-form-fields}

제공된 정보를 저장하기 위해 페이지의 필드를 데이터베이스의 필드에 연결합니다.

1. 양식 필드를 선택합니다.
1. 편집기의 오른쪽에 있는 **[!UICONTROL Field]** 섹션을 편집합니다.
1. 선택한 필드에 연결할 데이터베이스 필드를 선택합니다.

   ![](assets/dce_uc1_mapping.png)

1. 페이지의 각 필드에 대해 이 프로세스를 반복합니다.

필드를 필수 필드로 만들 수 있습니다.예를 들어, **[!UICONTROL Email]** 필드를 클릭한 다음 필수 **옵션을 활성화합니다** .

![](assets/dce_uc1_fieldmandatory.png)

### 다음 페이지에 대한 링크 만들기 {#creating-a-link-to-the-next-page}

이 단계는 웹 응용 프로그램이 다음 단계의 순서를 결정할 수 있도록 허용하므로 필수입니다.수집된 데이터를 데이터베이스에 저장한 다음 다음 페이지를 표시합니다(**감사** 페이지).

1. 페이지의 **[!UICONTROL Send it!]** 단추를 선택합니다 **[!UICONTROL Collection]** .
1. 드롭다운 **[!UICONTROL Action]** 메뉴를 클릭합니다.
1. 작업을 **[!UICONTROL Next page]** 선택합니다.

   ![](assets/dce_uc1_actionbouton.png)

### 개인화 필드 삽입 {#inserting-a-personalization-field}

이 단계에서는 감사 페이지를 개인화할 수 있습니다. 이렇게 하려면:

1. 페이지를 **[!UICONTROL Thank you]** 엽니다.
1. 수신자의 이름을 삽입할 텍스트 영역에 커서를 놓습니다.
1. 도구 **[!UICONTROL Personalization field]** 모음의 **[!UICONTROL Insert]** 메뉴에서 을 선택합니다.
1. 이름을 선택합니다.

   ![](assets/dce_uc1_persochamp.png)

개인화 필드에 편집기의 노란색 배경이 있습니다.

![](assets/dce_uc1_edit_champperso.png)

## 3단계 - 컨텐츠 게시 {#step-3---publishing-content}

컨텐츠는 웹 애플리케이션 대시보드에서 게시됩니다. 단추를 클릭하여 **[!UICONTROL Publish]** 실행합니다.

![](assets/dce_uc1_pub_dashboard.png)

게시 중에 로그가 표시됩니다. 게시 시스템은 웹 응용 프로그램에 있는 모든 컨텐츠를 분석합니다.

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>게시 로그에서 경고 및 오류는 활동별로 정렬됩니다.

이제 양식을 사용할 수 있습니다.애플리케이션 대시보드에서 해당 URL에 액세스할 수 있으며 수신자에게 전송할 수 있습니다.
