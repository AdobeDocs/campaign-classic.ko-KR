---
product: campaign
title: 보고서에 대한 작업
description: 보고서에 대한 작업
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# 보고서에 대한 작업{#actions-on-reports}

![](../../assets/common.svg)

보고서를 볼 때 도구 모음에서 특정 수의 작업을 수행할 수 있습니다. 다음은 아래에 자세히 설명되어 있습니다.

![](assets/s_ncs_advuser_report_wizard_2.png)

도구 모음을 사용하여 보고서를 내보내기, 인쇄, 보관 또는 웹 브라우저에 표시할 수 있습니다.

![](assets/s_ncs_advuser_report_wizard_04.png)

## 보고서 내보내기 {#exporting-a-report}

드롭다운 목록에서 로 보고서를 내보낼 형식을 선택합니다. (.xls, .pdf 또는 .ods)

![](assets/s_ncs_advuser_report_wizard_06.png)

보고서에 여러 페이지가 포함되어 있으면 각 페이지에 대해 작업을 반복해야 합니다.

보고서를 PDF, Excel 또는 OpenOffice 형식으로 내보낼 때 보고서를 구성할 수 있습니다. Adobe Campaign 탐색기를 열고 관련 보고서를 선택합니다.

내보내기 옵션은 **[!UICONTROL Page]** 보고서의 활동, 즉 **[!UICONTROL Advanced]** 탭.

설정 변경 **[!UICONTROL Paper]** 및 **[!UICONTROL Margins]** 당신의 요구에 맞게 페이지 내보내기를 PDF 형식으로만 승인할 수도 있습니다. 이렇게 하려면 의 선택을 취소합니다. **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** 선택 사항입니다.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Microsoft Excel로 내보내기 {#exporting-into-microsoft-excel}

대상 **[!UICONTROL List with group]** Excel로 내보내도록 지정된 유형 보고서에는 다음 권장 사항과 제한 사항이 적용됩니다.

* 이러한 보고서에는 빈 줄이 없어야 합니다.

   ![](assets/export_limitations_remove_empty_line.png)

* 목록의 범례는 숨겨야 합니다.

   ![](assets/export_limitations_hide_label.png)

* 보고서는 셀 수준에서 정의된 특정 서식을 사용할 필요가 없습니다. 사용하는 것이 좋습니다 **[!UICONTROL Form rendering]** 를 클릭하여 테이블에서 셀의 형식을 정의합니다. 다음 **[!UICONTROL Form rendering]** 를 통해 액세스할 수 있습니다. **[!UICONTROL Administration > Configuration > Form rendering]**.
* HTML 컨텐츠를 삽입하지 않는 것이 좋습니다.
* 보고서에 여러 개의 테이블, 차트 등이 포함되어 있는 경우 유형 요소가 다른 요소 아래에 내보내집니다.
* 셀에서 캐리지 리턴을 강제 적용할 수 있습니다. 이 구성은 Excel에 유지됩니다. 자세한 내용은 다음을 참조하십시오 [셀 형식 정의](../../reporting/using/creating-a-table.md#defining-cell-format).

### 내보내기 연기 {#postpone-the-export}

예를 들어 비동기 호출이 발생할 때까지 보고서 내보내기를 연기할 수 있습니다. 이렇게 하려면 페이지의 초기화 스크립트에 다음 매개 변수를 입력합니다.

```
document.nl_waitBeforeRender = true;
```

내보내기를 활성화하고 PDF으로 변환하려면 **document.nl_renderToPdf()** 매개 변수 없이 함수를 사용합니다.

### 메모리 할당 {#memory-allocation}

특정 큰 보고서를 내보낼 때 메모리 할당 오류가 발생할 수 있습니다.

특정 경우 기본값은 **maxMB** (**SKMS** 에 지정된 JavaScript의 경우) **serverConf.xml** 구성 파일이 64MB로 설정되어 있습니다. 보고서를 내보내는 동안 메모리 오류가 발생하면 이 그림을 512MB로 늘리는 것이 좋습니다.

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

구성에 대한 변경 사항을 적용하려면 **nlserver** 서비스를 다시 시작해야 합니다.

자세한 내용은 **serverConf.xml** 파일, [이 섹션](../../production/using/configuration-principle.md).

자세한 내용은 **nlserver** 서비스, [이 섹션](../../production/using/administration.md).

## 보고서 인쇄 {#printing-a-report}

보고서를 인쇄할 수 있습니다. 이렇게 하려면 프린터 아이콘을 클릭합니다. 그러면 대화 상자가 열립니다.

더 좋은 결과를 얻으려면 Internet Explorer 인쇄 옵션을 편집하고 **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## 보고서 아카이브 만들기 {#creating-report-archives}

보고서 보관 기능을 사용하면 지정된 기간 동안의 통계를 보여주는 등 다양한 기간에 보고서 보기를 만들 수 있습니다.

아카이브를 만들려면 관련 보고서를 열고 해당 아이콘을 클릭합니다.

![](assets/s_ncs_advuser_report_wizard_07.png)

기존 아카이브를 표시하거나 숨기려면 표시/숨기기 아이콘을 클릭합니다.

![](assets/s_ncs_advuser_report_history_06.png)

아카이브 날짜는 표시/숨기기 아이콘 아래에 표시됩니다. 아카이브를 클릭하여 봅니다.

![](assets/s_ncs_advuser_report_history_04.png)

보고서 보관 파일을 삭제할 수 있습니다. 이렇게 하려면 보고서가 저장된 Adobe Campaign 노드로 이동합니다. 을(를) 클릭합니다. **[!UICONTROL Archives]** 탭에서 삭제할 항목을 선택하고 **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
