---
product: campaign
title: 고급 기능
description: 보고서 작업 시 고급 기능에 대해 자세히 알아보기
feature: Reporting, Monitoring
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 4%

---

# 고급 기능{#advanced-functionalities}



기술 사용자로서 [일반 속성](../../reporting/using/properties-of-the-report.md) 외에도 다음과 같은 고급 기능을 활용하여 보고서를 구성할 수 있습니다.

* **Script** 활동에서 데이터를 처리할 복잡한 쿼리를 만듭니다. [자세히 알아보기](#script-activity)

* 서버측 또는 클라이언트측에서 실행할 외부 스크립트를 추가합니다. [자세히 알아보기](#external-script)

* **Jump** 활동으로 보고서를 호출합니다. [자세히 알아보기](#calling-up-another-report)

* 보고서에 더 쉽게 액세스할 수 있도록 하려면 URL 매개 변수를 추가합니다. [자세히 알아보기](#calling-up-another-report)

* 보고서 컨텍스트에 사용할 변수를 추가합니다. [자세히 알아보기](#adding-variables)

## 스크립트 작업 {#adding-a-script}

### 외부 스크립트 참조 {#external-script}

보고서 페이지가 호출될 때 클라이언트 및/또는 서버측에서 실행될 JavaScript 코드를 참조할 수 있습니다.

방법은 다음과 같습니다.

1. [보고서 속성](../../reporting/using/properties-of-the-report.md)을(를) 편집하고 **[!UICONTROL Scripts]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Add]**&#x200B;을(를) 클릭하고 참조할 스크립트를 선택합니다.
1. 그런 다음 실행 모드를 선택합니다.

   여러 스크립트를 추가하는 경우 도구 모음의 화살표를 사용하여 실행 시퀀스를 정의합니다.

   ![](assets/reporting_custom_js.png)

클라이언트측에서 정상적으로 실행되도록 하려면 참조된 스크립트를 JavaScript에서 작성해야 하며 일반적인 브라우저와 호환되어야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../web/using/web-forms-answers.md)을 참조하십시오.

### 스크립트 활동 추가 {#script-activity}

[보고서를 디자인](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)할 때 **[!UICONTROL Script]** 활동을 사용하여 데이터를 처리하고 SQL 언어를 사용하지 않는 복잡한 쿼리를 쉽게 만들 수 있습니다. 스크립트 창에 쿼리를 직접 입력할 수 있습니다.

**[!UICONTROL Texts]** 탭에서는 텍스트 문자열을 정의할 수 있습니다. 그런 다음 **$(식별자)** 구문과 함께 사용할 수 있습니다. 텍스트 사용에 대한 자세한 내용은 [머리글 및 바닥글 추가](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)를 참조하세요.

>[!CAUTION]
>
>JavaScript 코드를 사용하여 합계를 만들지 않는 것이 좋습니다.

보고서 기록을 만들려면 보관된 데이터를 저장하기 위해 JavaScript 쿼리에 다음 줄을 추가합니다.

```
if( ctx.@_historyId.toString().length == 0 )
```

그렇지 않으면 현재 데이터만 표시됩니다.

## URL 매개 변수 추가 {#defining-additional-settings}

[보고서 속성](../../reporting/using/properties-of-the-report.md)의 **[!UICONTROL Parameters]** 탭에서 보고서에 대한 추가 설정을 정의할 수 있습니다. 이러한 설정은 호출 중에 URL로 전달됩니다.

>[!CAUTION]
>
>보안상의 이유로 이러한 매개 변수는 매우 신중하게 사용해야 합니다.

새 설정을 만들려면 다음 작업을 수행하십시오.

1. **[!UICONTROL Add]** 단추를 클릭하고 설정 이름을 입력합니다.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 필요한 경우 설정이 필수인지 여부를 지정합니다.

1. 만들려는 설정의 형식을 선택하십시오. **[!UICONTROL Filter]** 또는 **[!UICONTROL Variable]**.

   **[!UICONTROL Filter entities]** 옵션을 사용하면 데이터베이스의 필드를 매개 변수로 사용할 수 있습니다.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   데이터는 엔터티 수준 **ctx/recipient/@account**&#x200B;에서 직접 복구됩니다.

   **[!UICONTROL Variable]** 옵션을 사용하면 URL의 매개 변수로 전달되고 필터에서 사용할 수 있는 변수를 만들거나 선택할 수 있습니다.

**[!UICONTROL Response HTTP headers]**&#x200B;을(를) 사용하면 iframe을 사용하여 보고서 페이지를 HTML 페이지에 포함할 때 클릭재킹을 방지할 수 있습니다. 클릭재킹을 방지하려면 **[!UICONTROL X-Frame-options header]** 동작을 선택할 수 있습니다.

* **[!UICONTROL None]**: 보고서에 **[!UICONTROL X-Frame-options header]**&#x200B;이(가) 없습니다.
* **[!UICONTROL Same as origin]**: 새 보고서 및 다시 게시된 보고서에 대해 기본적으로 설정됩니다. 호스트 이름은 보고서의 URL과 동일합니다.
* **[!UICONTROL Deny]**: iframe을 사용하여 HTML 페이지에 보고서를 포함할 수 없습니다.

![](assets/s_ncs_advuser_report_properties_09c.png)

## 변수 추가 {#adding-variables}

**[!UICONTROL Variables]** 탭에는 보고서에 구성된 변수 목록이 포함되어 있습니다. 이러한 변수는 보고서 컨텍스트에 노출되며 계산에 사용할 수 있습니다.

새 변수를 만들려면 **[!UICONTROL Add]** 단추를 클릭하십시오.

변수의 정의를 보려면 변수를 선택하고 **[!UICONTROL Detail...]** 단추를 클릭합니다.

![](assets/s_ncs_advuser_report_properties_10.png)

## 사용 사례: 보고서에 변수 및 매개 변수 사용

아래 비디오 예제에서는 이 속성의 값을 기반으로 다른 보고서 보기를 만들기 위해 &quot;_type&quot; 매개 변수를 추가하는 방법을 배웁니다.

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## 다른 보고서 호출 {#calling-up-another-report}

**Jump** 활동은 화살표가 없는 전환과 같습니다. 한 활동에서 다른 활동으로 이동하거나 다른 보고서에 액세스할 수 있습니다.
