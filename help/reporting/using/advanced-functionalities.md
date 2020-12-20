---
solution: Campaign Classic
product: campaign
title: 고급 기능
description: 고급 기능
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 4%

---


# 고급 기능{#advanced-functionalities}

기술 사용자는 [일반 속성](../../reporting/using/properties-of-the-report.md) 외에도 고급 기능을 사용하여 다음과 같은 보고서를 구성할 수 있습니다.

* 복잡한 쿼리를 만들어 **스크립트** 활동의 데이터를 처리합니다. [자세히 알아보기](#script-activity)

* 서버나 클라이언트측에서 실행할 외부 스크립트를 추가합니다. [자세히 알아보기](#external-script)

* **Jump** 활동이 있는 보고서를 호출합니다. [자세히 알아보기](#calling-up-another-report)

* URL 매개 변수를 보고서에 추가하여 보다 쉽게 액세스할 수 있도록 합니다. [자세히 알아보기](#calling-up-another-report)

* 보고서 컨텍스트에서 사용할 변수를 추가합니다. [자세히 알아보기](#adding-variables)

## 스크립트 작업{#adding-a-script}

### 외부 스크립트 참조 {#external-script}

보고서 페이지가 호출될 때 클라이언트 및/또는 서버측에서 실행되는 JavaScript 코드를 참조할 수 있습니다.

방법은 다음과 같습니다.

1. [보고서 속성](../../reporting/using/properties-of-the-report.md)을 편집하고 **[!UICONTROL Scripts]**&#x200B;를 클릭합니다.
1. **[!UICONTROL Add]**&#x200B;을 클릭하고 참조할 스크립트를 선택합니다.
1. 그런 다음 실행 모드를 선택합니다.

   여러 스크립트를 추가하는 경우 도구 모음의 화살표를 사용하여 실행 시퀀스를 정의합니다.

   ![](assets/reporting_custom_js.png)

클라이언트측에서 정상적으로 실행하려면 참조된 스크립트가 JavaScript로 작성되어야 하며 일반적인 브라우저와 호환되어야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../web/using/web-forms-answers.md)을 참조하십시오.

### 스크립트 작업 {#script-activity} 추가

[보고서](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)를 디자인할 때 **[!UICONTROL Script]** 활동을 사용하여 데이터를 처리하고 SQL 언어를 사용하지 않는 복잡한 쿼리를 쉽게 만듭니다. 스크립트 창에 쿼리를 직접 입력할 수 있습니다.

**[!UICONTROL Texts]** 탭에서는 텍스트 문자열을 정의할 수 있습니다. 그런 다음 다음 다음 구문과 함께 사용할 수 있습니다.**$(식별자)**. 텍스트 사용에 대한 자세한 내용은 [머리글 및 바닥글 추가](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)를 참조하십시오.

>[!CAUTION]
>
>JavaScript 코드를 사용하여 집계를 만드는 것은 권장되지 않습니다.

보고서 내역을 만들려면 보관된 데이터를 저장하려면 JavaScript 쿼리에 다음 줄을 추가하십시오.

```
if( ctx.@_historyId.toString().length == 0 )
```

그렇지 않으면 현재 데이터만 표시됩니다.

## URL 매개 변수 {#defining-additional-settings} 추가

[보고서 속성](../../reporting/using/properties-of-the-report.md)의 **[!UICONTROL Parameters]** 탭에서는 보고서에 대한 추가 설정을 정의할 수 있습니다.이러한 설정은 호출 중에 URL로 전달됩니다.

>[!CAUTION]
>
>보안상의 이유로 이러한 매개 변수는 매우 신중하게 사용해야 합니다.

새 설정을 만들려면:

1. **[!UICONTROL Add]** 단추를 클릭하고 설정 이름을 입력합니다.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 필요한 경우 설정이 필수 설정인지 여부를 지정합니다.

1. 만들 설정 유형을 선택합니다.**[!UICONTROL Filter]** 또는 **[!UICONTROL Variable]**.

   **[!UICONTROL Filter entities]** 옵션을 사용하면 데이터베이스의 필드를 매개 변수로 사용할 수 있습니다.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   데이터는 엔티티 수준에서 직접 복구됩니다.**ctx/recipient/@account**.

   **[!UICONTROL Variable]** 옵션을 사용하면 URL의 매개 변수로 전달되고 필터에서 사용할 수 있는 변수를 만들거나 선택할 수 있습니다.

**[!UICONTROL Response HTTP headers]**&#x200B;을 사용하면 iframe을 사용하여 HTML 페이지에 보고서의 페이지를 포함할 때 클릭재킹을 방지할 수 있습니다. 클릭재킹을 방지하려면 **[!UICONTROL X-Frame-options header]** 비헤이비어를 선택할 수 있습니다.

* **[!UICONTROL None]**:그 보고서는 없다 **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**:새 보고서 및 다시 게시된 보고서에 대해 기본적으로 설정됩니다. 호스트 이름은 보고서의 URL과 같습니다.
* **[!UICONTROL Deny]**:iframe을 사용하여 HTML 페이지에 보고서를 포함할 수 없습니다.

![](assets/s_ncs_advuser_report_properties_09c.png)

## 변수 {#adding-variables} 추가

**[!UICONTROL Variables]** 탭에는 보고서에 구성된 변수 목록이 포함되어 있습니다. 이러한 변수는 보고서 컨텍스트에 노출되며 계산에 사용할 수 있습니다.

**[!UICONTROL Add]** 단추를 클릭하여 새 변수를 만듭니다.

변수의 정의를 보려면 해당 변수를 선택하고 **[!UICONTROL Detail...]** 단추를 클릭합니다.

![](assets/s_ncs_advuser_report_properties_10.png)

## 사용 사례:보고서에서 변수 및 매개 변수 사용

아래 비디오 예제에서는 이 속성의 값을 기반으로 &quot;_type&quot; 매개 변수를 추가하여 다른 보고서 보기를 만드는 방법을 알아봅니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## 다른 보고서 {#calling-up-another-report} 호출

**Jump** 활동은 화살표가 없는 전환과 같습니다.이를 통해 한 활동에서 다른 활동으로 이동하거나 다른 보고서에 액세스할 수 있습니다.
