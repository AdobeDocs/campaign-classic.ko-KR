---
product: campaign
title: 보고서의 속성
description: 보고서 속성 설정에 대해 자세히 알아보기
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 2%

---

# 보고서의 속성{#properties-of-the-report}



필요에 따라 보고서를 완전히 개인화하고 구성할 수 있습니다. 이렇게 하려면 속성을 편집합니다. 보고서 속성은 활동 시퀀스 차트 위에 있는 **[!UICONTROL Properties]** 단추를 통해 액세스할 수 있습니다.

![](assets/s_ncs_advuser_report_properties_01.png)

일반 속성은 아래에 설명되어 있습니다. **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** 및 **[!UICONTROL Scripts]** 탭에 구성된 고급 기능은 이 섹션[&#128279;](../../reporting/using/advanced-functionalities.md)에서 에 설명되어 있습니다.

## 일반 속성 {#overall-properties}

보고서 속성의 **[!UICONTROL General]** 탭에서 아래 나열된 설정을 편집할 수 있습니다.

* 보고서의 레이블과 내부 이름입니다. **[!UICONTROL Internal name]**&#x200B;은(는) 보고서 최종 URL에 사용됩니다. 보고서 생성 후에는 변경할 수 없습니다.

* 보고서를 만드는 동안 **폴더** 보고서를 선택했습니다. 가장 좋은 방법은 사용자 지정 보고서가 [기본 제공 보고서](../../reporting/using/about-campaign-built-in-reports.md)와 혼합되지 않도록 전용 폴더를 만드는 것입니다.

* 보고서를 만들 때 **저장소**&#x200B;을(를) 선택했습니다. 보고서의 데이터 테이블을 변경하려면 **[!UICONTROL Document type]** 필드 오른쪽에 있는 **[!UICONTROL Select link]** 아이콘을 클릭합니다.

  ![](assets/s_ncs_advuser_report_properties_02.png)

* **액세스 제어** 매개 변수입니다. 이러한 설정은 아래에 설명되어 있습니다.

## 보고서에 대한 액세스 제어 {#report-accessibility}

보고서는 Adobe Campaign 콘솔 또는 웹 브라우저에서 액세스할 수 있습니다. 이 경우 아래와 같이 보고서 액세스 제어를 구성해야 할 수 있습니다.

![](assets/s_ncs_advuser_report_properties_02b.png)

가능한 옵션은 다음과 같습니다.

* **[!UICONTROL Anonymous access]**: 이 옵션을 사용하면 보고서에 무제한 액세스할 수 있습니다. 그러나 조작은 불가능합니다.

  &#39;webapp&#39; 기술 연산자의 권한은 보고서 요소를 표시하는 데 사용됩니다. 자세한 내용은 [이 섹션](../../platform/using/access-management-operators.md)을 참조하세요.

* **[!UICONTROL Access control]**: 이 옵션을 사용하면 Adobe Campaign 운영자가 로그인한 후 액세스할 수 있습니다.
* **[!UICONTROL Specific account]**: 이 옵션을 사용하면 **[!UICONTROL Operator]** 필드에서 선택한 연산자의 권한으로 보고서를 실행할 수 있습니다.

## 보고서 번역 {#report-localization}

보고서를 번역할 언어를 구성할 수 있습니다. 이렇게 하려면 **[!UICONTROL Localization]** 탭을 클릭합니다.

![](assets/s_ncs_advuser_report_properties_06.png)

편집 언어는 사용자가 작성하는 언어입니다. 언어를 추가하면 보고서 편집 페이지에 하위 탭이 나타납니다.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Campaign의 웹 페이지 로컬라이제이션에 대한 자세한 정보는 [이 섹션](../../web/using/translating-a-web-form.md)을 참조하세요.

## HTML 렌더링 개인화 {#personalizing-html-rendering}

**[!UICONTROL Rendering]** 탭에서 페이지에 대한 데이터 표시 모드를 개인화할 수 있습니다. 다음을 선택할 수 있습니다.

* 보고서의 탐색 유형: 버튼 또는 링크를 통해.
* 보고서 요소에 대한 레이블의 기본 위치입니다. 이 위치는 각 요소에 대해 오버로드될 수 있습니다.
* 보고서 페이지 생성에 사용되는 템플릿 또는 테마입니다.

![](assets/s_ncs_advuser_report_properties_08.png)

## 오류 페이지 개인화 {#personalizing-the-error-page}

**[!UICONTROL Error page]** 탭에서는 보고서 표시에 오류가 발생할 경우 표시할 메시지를 구성할 수 있습니다.

텍스트를 정의하고 특정 식별자에 연결하여 보고서 현지화를 관리할 수 있습니다. 자세한 내용은 [머리글 및 바닥글 추가](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)를 참조하세요.

![](assets/s_ncs_advuser_report_properties_11.png)
