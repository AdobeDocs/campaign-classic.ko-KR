---
product: campaign
title: 보고서의 속성
description: 보고서 속성 설정에 대해 자세히 알아보기
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 7fa8cea04fb4e25187c48ad19330815e9b522b37
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# 보고서의 속성{#properties-of-the-report}

![](../../assets/common.svg)

필요에 따라 보고서를 완벽하게 개인화하고 구성할 수 있습니다. 이렇게 하려면 해당 속성을 편집합니다. 보고서 속성은 **[!UICONTROL Properties]** 활동 시퀀스 차트 위에 있는 단추입니다.

![](assets/s_ncs_advuser_report_properties_01.png)

일반 속성은 아래에 설명되어 있습니다. 에 구성된 고급 기능 **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** 및 **[!UICONTROL Scripts]** 탭에 대해 설명합니다. [이 섹션](../../reporting/using/advanced-functionalities.md).

## 일반 속성 {#overall-properties}

에서 **[!UICONTROL General]** 보고서 속성의 탭에서 아래 나열된 설정을 편집할 수 있습니다.

* 보고서의 레이블과 내부 이름입니다. 다음 **[!UICONTROL Internal name]** 보고서 최종 URL에 사용됩니다. 보고서를 만든 후에는 변경할 수 없습니다.

* 보고서 **폴더** 이 선택되면 보고서가 만들어집니다. 가장 좋은 방법은 사용자 지정 보고서에 대해 혼합되지 않도록 전용 폴더를 만드는 것입니다 [기본 제공 보고서](../../reporting/using/about-campaign-built-in-reports.md).

* 다음 **스토리지** 보고서를 만들 때 선택된 상태로 유지됩니다. 보고서의 데이터 테이블을 변경하려면 **[!UICONTROL Select link]** 아이콘 을 클릭합니다. **[!UICONTROL Document type]** 필드.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* 다음 **액세스 제어** 매개 변수. 이러한 설정은 아래에 설명되어 있습니다.

## 보고서에 대한 액세스 제어 {#report-accessibility}

보고서는 Adobe Campaign 콘솔에서 또는 웹 브라우저로 액세스할 수 있습니다. 이 경우 아래와 같이 보고서 액세스 제어를 구성해야 할 수 있습니다.

![](assets/s_ncs_advuser_report_properties_02b.png)

가능한 옵션은 다음과 같습니다.

* **[!UICONTROL Anonymous access]**: 이 옵션을 사용하면 보고서에 대한 무제한 액세스를 사용할 수 있습니다. 그러나 어떤 조작도 가능하지 않다.

   보고서 요소를 표시하는 데 &#39;webapp&#39; 기술 연산자의 권한이 사용됩니다. 추가 정보 [이 섹션](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**: 이 옵션을 사용하면 Adobe Campaign 운영자가 로그온하면 액세스할 수 있습니다.
* **[!UICONTROL Specific account]**: 이 옵션을 사용하면 다음에서 선택한 연산자의 권한으로 보고서를 실행할 수 있습니다 **[!UICONTROL Operator]** 필드.

## 보고서 현지화 관리 {#managing-report-localization}

보고서를 변환할 언어를 구성할 수 있습니다. 이렇게 하려면 **[!UICONTROL Localization]** 탭.

![](assets/s_ncs_advuser_report_properties_06.png)

편집 언어는 사용자가 쓰는 언어입니다. 언어를 추가하면 하위 탭이 보고서 편집 페이지에 나타납니다.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Campaign의 웹 페이지 현지화에 대한 자세한 내용은 [이 섹션](../../web/using/translating-a-web-form.md).

## HTML 렌더링 개인화 {#personalizing-html-rendering}

에서 **[!UICONTROL Rendering]** 탭에서 페이지에 대한 데이터 표시 모드를 개인화할 수 있습니다. 다음을 선택할 수 있습니다.

* 보고서의 탐색 유형: 버튼 또는 링크를 통해 검색할 수 있습니다.
* 보고서 요소에 대한 레이블의 기본 위치입니다. 이 위치는 각 요소에 대해 오버로드될 수 있습니다.
* 보고서 페이지를 생성하는 데 사용되는 템플릿 또는 테마입니다.

![](assets/s_ncs_advuser_report_properties_08.png)

## 오류 페이지 개인화 {#personalizing-the-error-page}

다음 **[!UICONTROL Error page]** 탭에서는 보고서 표시에 오류가 발생할 경우 나타나는 메시지를 구성할 수 있습니다.

텍스트를 정의하고 특정 식별자에 연결하여 보고서 현지화를 관리할 수 있습니다. 자세한 내용은 [머리글 및 바닥글 추가](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
