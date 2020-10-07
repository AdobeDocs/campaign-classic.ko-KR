---
title: 웹 양식의 정적 요소
seo-title: 웹 양식의 정적 요소
description: 웹 양식의 정적 요소
seo-description: null
page-status-flag: never-activated
uuid: 628e2252-16a2-4c8a-a178-60a9441d3198
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: ca3377c6-a120-4cd0-aaf4-80248f4f5918
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 4%

---


# 웹 양식의 정적 요소{#static-elements-in-a-web-form}

사용자가 양식 페이지에 상호 작용하지 않는 요소를 포함할 수 있습니다.이미지, HTML 컨텐츠, 가로 막대 또는 하이퍼텍스트 링크와 같은 정적 요소입니다. 이러한 요소는 **[!UICONTROL Add static element]** 메뉴를 클릭하여 도구 모음의 첫 번째 단추를 통해 만들어집니다.

![](assets/s_ncs_admin_survey_add_static_element.png)

다음 유형의 필드를 사용할 수 있습니다.

* 이전에 제공된 답변(양식 컨텍스트) 또는 데이터베이스를 기반으로 한 값.
* 하이퍼링크, HTML, 가로 막대 HTML [컨텐츠 삽입을 참조하십시오](#inserting-html-content).
* 리소스 라이브러리 또는 사용자가 액세스할 수 있는 서버에 저장된 이미지입니다. 이미지 [삽입을 참조하십시오](#inserting-images).
* 클라이언트 측 및/또는 서버측에서 실행되는 스크립트 JavaScript로 작성해야 하며 클라이언트 측에서 올바로 실행되도록 대부분의 브라우저와 호환되어야 합니다.

   >[!NOTE]
   >
   >서버측에서 스크립트는 [Campaign JSAPI 설명서에 정의된 함수를 사용할 수 있습니다](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

## HTML 컨텐츠 삽입 {#inserting-html-content}

양식 페이지에 HTML 컨텐츠를 포함할 수 있습니다.하이퍼링크, 이미지, 서식이 지정된 단락, 비디오 또는 Flash 개체 등

HTML 편집기를 사용하면 양식 페이지에 삽입할 컨텐츠를 입력할 수 있습니다. 편집기를 열려면 로 **[!UICONTROL Static elements>HTML]** 이동합니다.

컨텐츠를 직접 입력하고 포맷하거나 소스 코드 창을 표시하여 일부 외부 컨텐츠에 붙여넣을 수 있습니다. &quot;소스 코드&quot; 모드로 전환하려면 도구 모음에서 첫 번째 아이콘을 클릭합니다.

![](assets/s_ncs_admin_survey_html_editor.png)

데이터베이스 필드를 삽입하려면 개인화 단추를 사용합니다.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>HTML 편집기에 입력된 문자열은 하위 탭에서 정의된 경우에만 **[!UICONTROL Texts]** 변환됩니다. 그렇지 않으면 수집되지 않습니다. 자세한 내용은 웹 양식 [변환을 참조하십시오](../../web/using/translating-a-web-form.md).

### Inserting a link {#inserting-a-link}

다음 예와 같이 편집 창의 필드를 채웁니다.

하이퍼텍스트 링크를 추가하려면 로 이동합니다 **[!UICONTROL Static elements>Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* 양식 **[!UICONTROL Label]** 페이지에 표시될 하이퍼텍스트 링크의 컨텐츠입니다.
* 원하는 주소 **[!UICONTROL URL]** (예: [https://www.adobe.com](https://www.adobe.com) for a website, [info@adobe.com](mailto:info@adobe.com) to send a message.
* 이 **[!UICONTROL Window]** 필드를 사용하면 사이트의 경우 링크에 대한 표시 모드를 선택할 수 있습니다. 링크를 새 창, 현재 창 또는 다른 창에서 열 수 있습니다.
* 아래와 같이 도구 설명을 추가할 수 있습니다.

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* 링크를 단추 또는 이미지로 표시하도록 선택할 수 있습니다. 이렇게 하려면 **[!UICONTROL Type]** 필드에서 표시 유형을 선택합니다.

### 링크 유형 {#types-of-links}

기본적으로 링크는 URL 유형 작업과 연관되어 URL 필드에 링크 대상 주소를 입력할 수 있습니다.

![](assets/s_ncs_admin_survey_link_url.png)

사용자가 링크를 클릭하여 다음을 수행할 수 있도록 링크에 대한 다른 작업을 정의할 수 있습니다.

* 페이지 새로 고침

   이렇게 하려면 필드의 드롭다운 상자에서 **[!UICONTROL Refresh page]** 옵션을 **[!UICONTROL Action]** 선택합니다.

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* 다음/이전 페이지 표시

   이렇게 하려면 **[!UICONTROL Next page]** 필드 드롭다운 상자에서 **[!UICONTROL Previous page]** 또는 **[!UICONTROL Action]** 옵션을 선택합니다.

   ![](assets/s_ncs_admin_survey_link_next.png)

   링크로 대체하려면 **[!UICONTROL Next]** 및/또는 **[!UICONTROL Back]** 단추를 숨길 수 있습니다. Refer to this [page](../../web/using/defining-web-forms-page-sequencing.md).

   이 링크는 기본적으로 사용되는 **[!UICONTROL Next]** 단추를 대체합니다.

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* 다른 페이지 표시

   이 **[!UICONTROL Enable a transition]** 옵션을 사용하면 필드에서 선택한 발신 전환과 연관된 특정 페이지를 표시할 수 **[!UICONTROL Transition]** 있습니다.

   ![](assets/s_ncs_admin_survey_link_viral.png)

   기본적으로 한 페이지에는 출력 전환이 하나만 있습니다. 새 전환을 만들려면 페이지를 선택한 다음 아래 표시된 대로 **[!UICONTROL Add]** **[!UICONTROL Output transitions]** 섹션에서 버튼을 클릭합니다.

   ![](assets/s_ncs_admin_survey_add_transition.png)

   다이어그램에서 이 추가는 다음과 같습니다.

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >웹 양식의 페이지 시퀀스에 대한 자세한 내용은 웹 양식 페이지 순서 [정의를 참조하십시오](../../web/using/defining-web-forms-page-sequencing.md).

* Facebook 프로필에서 가져온 데이터로 양식 필드 미리 로드

   >[!CAUTION]
   >
   >이 함수는 응용 프로그램을 설치한 경우에만 사용할 수 **[!UICONTROL Social Marketing]** 있습니다. 이 옵션을 사용하려면 **[!UICONTROL Facebook Connect]** 유형 외부 계정과 함께 Facebook 애플리케이션을 만들어야 합니다. 자세한 정보는 이 [페이지](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)를 참조하십시오.

   이 **[!UICONTROL Preload with Facebook]** 옵션을 사용하면 양식에 단추를 삽입하여 Facebook 프로필 정보를 사용하여 필드를 미리 로드할 수 있습니다.

   ![](assets/web_social_webapp_037.png)

   사용자가 **[!UICONTROL Fill in automatically]** 단추를 클릭하면 Facebook 권한 요청 창이 열립니다.

   ![](assets/web_social_webapp_029.png)

   >[!NOTE]
   >
   >외부 계정을 구성할 때 확장 권한 목록을 변경할 수 있습니다. 확장 권한을 입력하지 않으면 Facebook은 기본적으로 기본 프로필 정보를 전달합니다.\
   >확장 권한 및 해당 구문 목록을 보려면 여기를 클릭하십시오. [https://developers.facebook.com/docs/reference/api/permissions/](https://developers.facebook.com/docs/reference/api/permissions/)

   사용자가 정보를 공유하기로 동의하면 양식 필드가 미리 로드됩니다.

   ![](assets/web_social_webapp_030.png)

이 경우 다음 요소로 구성된 웹 응용 프로그램을 만들었습니다.

* 양식을 포함하는 페이지
* **[!UICONTROL Record]** 활동
* an **[!UICONTROL End]** activity

![](assets/social_webapp_031.png)

미리 로드 단추를 추가하려면 다음 단계를 적용합니다.

1. 양식을 만듭니다.

   ![](assets/social_webapp_032.png)

1. 양식의 필드와 동일한 수준으로 이동한 후 링크를 추가합니다.

   ![](assets/social_webapp_033.png)

1. 레이블을 입력하고 유형을 **[!UICONTROL Button]** 선택합니다.

   ![](assets/social_webapp_034.png)

1. 필드로 이동하여 **[!UICONTROL Action]** 선택합니다 **[!UICONTROL Preload with Facebook]**.

   ![](assets/social_webapp_035.png)

1. 필드로 **[!UICONTROL Application]** 이동하여 이전에 만든 **[!UICONTROL Facebook Connect]** 외부 계정 유형을 선택합니다. 자세한 정보는 이 [페이지](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)를 참조하십시오.

   ![](assets/social_webapp_036.png)

### HTML 컨텐츠 개인화 {#personalizing-html-content}

이전 페이지에 기록된 데이터로 양식 페이지의 HTML 내용을 개인화할 수 있습니다. 예를 들어 자동차 보험 웹 양식을 만들 수 있습니다. 이 웹 양식을 통해 연락처 정보와 자동차 브랜드를 제공할 수 있습니다.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

개인화 필드를 사용하여 사용자 이름과 선택한 브랜드를 다음 페이지에 다시 삽입합니다. 사용할 구문은 정보 저장 모드에 따라 다릅니다. 자세한 내용은 수집된 정보 [사용을 참조하십시오](../../web/using/web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>보안상의 이유로 수식에 입력한 값이 **`<%=`** 이스케이프 문자로 대체됩니다. 이를 방지하려면 필요한 경우에만 다음 구문을 사용하십시오. **`<%=`**.

이 예에서는 받는 사람의 이름과 성이 데이터베이스의 필드에 저장되고 자동차 브랜드가 변수에 저장됩니다. 2페이지에 개인화된 메시지의 구문은 다음과 같습니다.

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

이렇게 하면 다음과 같은 결과가 생성됩니다.

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### 텍스트 변수 사용 {#using-text-variables}

이 **[!UICONTROL Text]** 탭에서는 다음 구문을 사용하여 HTML에서 &lt;%= 및 %> 문자 사이에 사용할 수 있는 변수 필드를 만들 수 있습니다. **$(IDENTIFIER)**.

이 방법을 사용하여 문자열을 쉽게 현지화할 수 있습니다. See [Translating a web form](../../web/using/translating-a-web-form.md)

예를 들어 HTML 컨텐츠에 &quot; **마지막 연락처** 날짜&quot; 문자열을 표시할 수 있는 연락처 필드를 만들 수 있습니다. 이렇게 하려면 아래 단계를 수행합니다:

1. HTML 텍스트 **[!UICONTROL Text]** 탭을 클릭합니다.
1. 아이콘을 **[!UICONTROL Add]** 클릭합니다.
1. 열에 **[!UICONTROL Identifier]** 변수 이름을 입력합니다
1. 열에 **[!UICONTROL Text]** 기본값을 입력합니다.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. HTML 콘텐츠에서 **&lt;%= $(Contact) %>** 구문을 통해 이 텍스트 변수를 삽입합니다.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >HTML 편집기에 이러한 문자를 입력하면 **&lt;** 및 **>** 필드가 이스케이프 문자로대체됩니다. 이 경우 HTML 텍스트 편집기의 **[!UICONTROL Display source code]** 아이콘을 클릭하여 소스 코드를 수정해야 합니다.

1. 양식의 **[!UICONTROL Preview]** 레이블을 열고 HTML에 입력한 값을 봅니다.

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

이 운영 모드를 사용하면 웹 양식의 텍스트를 요인 처리하고 통합 번역 도구를 사용하여 번역을 관리할 수 있습니다. 자세한 내용은 웹 양식 [변환을 참조하십시오](../../web/using/translating-a-web-form.md).

## Inserting images {#inserting-images}

양식에 이미지를 포함하려면 외부에서 액세스할 수 있는 서버에 이미지를 저장해야 합니다.

메뉴를 **[!UICONTROL Static elements>Image]** 선택합니다.

삽입할 이미지의 소스를 선택합니다.공용 리소스 라이브러리에서 가져오거나 외부에서 액세스할 수 있는 외부 서버에 저장할 수 있습니다.

![](assets/s_ncs_admin_survey_add_img.png)

라이브러리의 이미지인 경우 필드의 콤보 상자에서 선택합니다.외부 파일에 있으면 액세스 경로를 입력합니다. 이미지 위에 커서를 가져다 놓거나(HTML의 대체 필드와 일치) 이미지가 표시되지 않으면 레이블이 표시됩니다.

이미지는 편집기의 중앙 섹션에서 볼 수 있습니다.
