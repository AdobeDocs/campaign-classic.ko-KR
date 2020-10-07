---
title: 보고서에 대한 작업
seo-title: 보고서에 대한 작업
description: 보고서에 대한 작업
seo-description: null
page-status-flag: never-activated
uuid: 7f9d99ab-ce19-46dd-bbf0-79de348d38fb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 3b9c138e-8f7f-4ee1-9baa-328848d01d3a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 2%

---


# 보고서에 대한 작업{#actions-on-reports}

보고서를 볼 때 도구 모음에서 특정 수의 작업을 수행할 수 있습니다. 아래에 자세히 나와 있습니다.

![](assets/s_ncs_advuser_report_wizard_2.png)

도구 모음을 사용하여 보고서를 내보내거나, 인쇄하거나, 보관하거나, 웹 브라우저에 표시할 수 있습니다.

![](assets/s_ncs_advuser_report_wizard_04.png)

## 보고서 내보내기 {#exporting-a-report}

드롭다운 목록에서 보고서를 내보낼 형식을 선택합니다. (.xls, .pdf 또는 .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

보고서에 여러 페이지가 있는 경우 각 페이지에 대해 작업을 반복해야 합니다.

보고서를 PDF, Excel 또는 OpenOffice 형식으로 내보내기하기 전에 보고서를 구성할 수 있습니다. Adobe Campaign 탐색기를 열고 관련 보고서를 선택합니다.

내보내기 옵션은 보고서의 **[!UICONTROL Page]** 활동을 통해 **[!UICONTROL Advanced]** 탭에서 액세스할 수 있습니다.

필요에 따라 **[!UICONTROL Paper]** 및 **[!UICONTROL Margins]** 의 설정을 변경합니다. PDF 형식의 페이지 내보내기만 승인할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** 옵션을 선택 취소합니다.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Microsoft Excel로 내보내기 {#exporting-into-microsoft-excel}

Excel로 내보낼 **[!UICONTROL List with group]** 형식 보고서의 경우 다음과 같은 권장 사항과 제한 사항이 적용됩니다.

* 이러한 보고서에는 빈 줄이 없어야 합니다.

   ![](assets/export_limitations_remove_empty_line.png)

* 목록의 범례가 숨겨져야 합니다.

   ![](assets/export_limitations_hide_label.png)

* 보고서에는 셀 수준에서 정의된 특정 서식을 사용할 필요가 없습니다. 표의 셀 형식 **[!UICONTROL Form rendering]** 을 정의하는 데 사용하는 것이 좋습니다. 를 통해 액세스할 **[!UICONTROL Form rendering]** 수 있습니다 **[!UICONTROL Administration > Configuration > Form rendering]**.
* HTML 컨텐츠를 삽입하는 것은 권장되지 않습니다.
* 보고서에 여러 개의 표, 차트 등이 포함되어 있는 경우 유형 요소, 다른 요소 아래에 내보내집니다.
* 다음과 같은 방법으로 캐리지 리턴을 강제로 셀에 넣을 수 있습니다.이 구성은 Excel에 보관됩니다. 자세한 내용은 셀 형식 [정의를 참조하십시오](../../reporting/using/creating-a-table.md#defining-cell-format).

### 수출 연기 {#postpone-the-export}

예를 들어 비동기 호출을 기다리는 경우 보고서 내보내기를 연기할 수 있습니다. 이렇게 하려면 페이지의 초기화 스크립트에 다음 매개 변수를 입력합니다.

```
document.nl_waitBeforeRender = true;
```

내보내기를 활성화하고 PDF로 변환하려면 매개 변수 없이 **document.nl_renderToPdf()** 함수를 사용합니다.

### 메모리 할당 {#memory-allocation}

특정 큰 보고서를 내보낼 때 메모리 할당 오류가 발생할 수 있습니다.

특정 경우 **serverConf.xml** 구성 파일에 지정된 JavaScript의 기본 값&#x200B;**maxMB** (호스팅된 인스턴스의 **SKMS.** )은64MB로설정됩니다. 보고서를 내보내는 동안 메모리 오류가 발생하는 경우 이 숫자를 512MB로 늘리는 것이 좋습니다.

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

구성에 대한 변경 사항을 적용하려면 **nlserver** 서비스를 다시 시작해야 합니다.

serverConf.xml **파일에 대한 자세한 내용은** 이 섹션을 참조하십시오 [](../../production/using/configuration-principle.md).

서버 서비스에 대한 자세한 **내용은** 이 섹션을 [](../../production/using/administration.md)참조하십시오.

## 보고서 인쇄 {#printing-a-report}

보고서를 인쇄할 수 있습니다.이렇게 하려면 프린터 아이콘을 클릭합니다.그러면 대화 상자가 열립니다.

더 나은 결과를 얻으려면 Internet Explorer 인쇄 옵션을 편집하고 선택합니다 **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## 보고서 보관 파일 만들기 {#creating-report-archives}

보고서 보관을 사용하면 특정 기간에 대한 통계를 표시하는 등 다양한 기간에 보고서 보기를 만들 수 있습니다.

아카이브를 만들려면 관련 보고서를 열고 해당 아이콘을 클릭합니다.

![](assets/s_ncs_advuser_report_wizard_07.png)

기존 아카이브를 표시하거나 숨기려면 표시/숨기기 아이콘을 클릭합니다.

![](assets/s_ncs_advuser_report_history_06.png)

아카이브 날짜는 표시/숨기기 아이콘 아래에 표시됩니다. 아카이브를 클릭하여 봅니다.

![](assets/s_ncs_advuser_report_history_04.png)

보고서 보관 파일을 삭제할 수 있습니다. 이렇게 하려면 보고서가 저장된 Adobe Campaign 노드로 이동합니다. 탭을 **[!UICONTROL Archives]** 클릭하고 삭제할 탭을 선택한 다음 클릭합니다 **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)

