---
solution: Campaign Classic
product: campaign
title: 보고서의 속성
description: 보고서 속성 설정에 대한 자세한 내용
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 1%

---


# 보고서의 속성{#properties-of-the-report}

필요에 맞게 보고서를 완벽하게 개인화하고 구성할 수 있습니다. 이렇게 하려면 해당 속성을 편집합니다. 보고서 속성은 활동 시퀀스 차트 위의 **[!UICONTROL Properties]** 단추를 통해 액세스합니다.

![](assets/s_ncs_advuser_report_properties_01.png)

일반 속성은 아래에 설명되어 있습니다. **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** 및 **[!UICONTROL Scripts]** 탭에 구성된 고급 기능에 대해서는 이 섹션](../../reporting/using/advanced-functionalities.md)에서 [에 대해 설명합니다.

## 일반 속성 {#overall-properties}

보고서 속성의 **[!UICONTROL General]** 탭에서 아래 나열된 설정을 편집할 수 있습니다.

* 보고서의 레이블과 내부 이름입니다. **[!UICONTROL Internal name]**&#x200B;은 보고서 최종 URL에 사용됩니다. 보고서를 만든 후에는 변경할 수 없습니다.

* 보고서 생성 중에 **폴더** 보고서가 선택됩니다. 사용자 지정 보고서의 전용 폴더를 만들어 [내장 보고서](../../reporting/using/about-campaign-built-in-reports.md)와 혼합되지 않도록 하는 것이 좋습니다.

* 보고서를 만들 때 **스토리지**&#x200B;이 선택됩니다. 보고서의 데이터 테이블을 변경하려면 **[!UICONTROL Document type]** 필드 오른쪽에 있는 **[!UICONTROL Select link]** 아이콘을 클릭합니다.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* **Access 컨트롤** 매개 변수. 이러한 설정은 아래에 설명되어 있습니다.

## 보고서 {#report-accessibility} 액세스 제어

보고서는 Adobe Campaign 콘솔 또는 웹 브라우저에서 액세스할 수 있습니다. 이 경우, 아래와 같이 보고서 액세스 제어를 구성해야 할 수 있습니다.

![](assets/s_ncs_advuser_report_properties_02b.png)

가능한 옵션은 다음과 같습니다.

* **[!UICONTROL Anonymous access]**:이 옵션을 사용하면 보고서에 대한 무제한 액세스를 할 수 있습니다. 그러나 조작은 불가능합니다.

   &#39;webapp&#39; 기술 운영자의 권한은 보고서 요소를 표시하는 데 사용됩니다. 이 섹션](../../platform/using/access-management.md#default-operators)에서 [에 대해 자세히 알아보십시오.

* **[!UICONTROL Access control]**:이 옵션을 사용하면 Adobe Campaign 연산자가 로그온한 후에 액세스할 수 있습니다.
* **[!UICONTROL Specific account]**:이 옵션을 사용하면 필드에서 선택된 연산자의 권한으로 보고서를 실행할 수  **[!UICONTROL Operator]** 있습니다.

## 보고서 현지화 관리 {#managing-report-localization}

보고서를 변환할 언어를 구성할 수 있습니다. 이렇게 하려면 **[!UICONTROL Localization]** 탭을 클릭합니다.

![](assets/s_ncs_advuser_report_properties_06.png)

편집 언어는 사용자가 쓰는 언어입니다. 언어를 추가하면 보고서 편집 페이지에 하위 탭이 나타납니다.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>캠페인의 웹 페이지 현지화에 대한 자세한 내용은 [이 섹션](../../web/using/translating-a-web-form.md)을 참조하십시오.

## HTML 렌더링 맞춤화 {#personalizing-html-rendering}

**[!UICONTROL Rendering]** 탭에서 페이지의 데이터 표시 모드를 개인화할 수 있습니다. 다음을 선택할 수 있습니다.

* 차트 렌더링 엔진:Adobe Campaign은 차트 렌더링을 생성하기 위한 서로 다른 두 모드를 제공합니다. 기본적으로 렌더링 엔진은 HTML 5입니다. 필요한 경우 Flash 렌더링을 선택할 수 있습니다.
* 보고서의 탐색 유형:를 클릭하거나 탭합니다.
* 보고서 요소에 대한 레이블의 기본 위치입니다. 이 위치는 각 요소에 대해 오버로드될 수 있습니다.
* 보고서 페이지를 생성하는 데 사용되는 템플릿 또는 테마입니다.

![](assets/s_ncs_advuser_report_properties_08.png)

## 오류 페이지 {#personalizing-the-error-page} 개인 설정

**[!UICONTROL Error page]** 탭에서는 보고서 표시에서 오류가 발생하는 경우에 나타날 메시지를 구성할 수 있습니다.

텍스트를 정의하고 특정 식별자에 연결하여 보고서 현지화를 관리할 수 있습니다. 자세한 내용은 [머리글 및 바닥글 추가](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)를 참조하십시오.

![](assets/s_ncs_advuser_report_properties_11.png)
