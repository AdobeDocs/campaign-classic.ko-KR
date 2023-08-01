---
product: campaign
title: 보고서에 대한 작업
description: 보고서에 대한 작업
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
exl-id: b30cdeaf-4ad6-473d-bdbc-91984755b609
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 3%

---

# 보고서에 대한 작업{#actions-on-reports}



보고서를 볼 때 도구 모음을 사용하여 특정 수의 작업을 수행할 수 있습니다. 이러한 내용은 아래에 자세히 설명되어 있습니다.

![](assets/s_ncs_advuser_report_wizard_2.png)

도구 모음을 사용하면 웹 브라우저에서 보고서를 내보내기, 인쇄, 보관 또는 표시할 수 있습니다.

![](assets/s_ncs_advuser_report_wizard_04.png)

## 보고서 내보내기 {#exporting-a-report}

드롭다운 목록에서 보고서를 로 내보낼 형식을 선택합니다. (.xls, .pdf 또는 .ods).

![](assets/s_ncs_advuser_report_wizard_06.png)

보고서에 페이지가 여러 개 있는 경우 각 페이지에 대해 작업을 반복해야 합니다.

보고서를 PDF, Excel 또는 OpenOffice 형식으로 내보내는 관점에서 보고서를 구성할 수 있습니다. Adobe Campaign 탐색기를 열고 관련 보고서를 선택합니다.

내보내기 옵션은 **[!UICONTROL Page]** 보고서의 활동( **[!UICONTROL Advanced]** 탭.

의 설정 변경 **[!UICONTROL Paper]** 및 **[!UICONTROL Margins]** 필요에 따라. PDF 형식으로만 페이지 내보내기를 승인할 수도 있습니다. 이렇게 하려면 선택을 취소합니다. **[!UICONTROL Activate OpenOffice/Microsoft Excel export]** 옵션을 선택합니다.

![](assets/s_ncs_advuser_report_wizard_021.png)

### Microsoft Excel로 내보내기 {#exporting-into-microsoft-excel}

대상 **[!UICONTROL List with group]** excel로 내보내도록 지정된 유형 보고서에는 다음과 같은 권장 사항과 제한 사항이 적용됩니다.

* 이러한 보고서에는 빈 줄이 없어야 합니다.

  ![](assets/export_limitations_remove_empty_line.png)

* 목록의 범례는 숨겨야 합니다.

  ![](assets/export_limitations_hide_label.png)

* 보고서는 셀 수준에서 정의된 특정 서식을 사용할 필요가 없습니다. 사용하는 것이 바람직하다 **[!UICONTROL Form rendering]** 를 클릭하여 표에 있는 셀의 형식을 정의합니다. 다음 **[!UICONTROL Form rendering]** 을 통해 액세스할 수 있음 **[!UICONTROL Administration > Configuration > Form rendering]**.
* HTML 콘텐츠는 삽입하지 않는 것이 좋습니다.
* 보고서에 테이블, 차트 등이 여러 개 포함된 경우 요소를 입력하면 다른 요소 아래로 내보내집니다.
* 셀에서 캐리지가 강제로 반환될 수 있습니다. 이 구성은 Excel에 유지됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/creating-a-table.md#defining-cell-format)을 참조하십시오.

### 내보내기 연기 {#postpone-the-export}

비동기 호출을 기다리기 위해 보고서 내보내기를 연기할 수 있습니다. 이렇게 하려면 페이지의 초기화 스크립트에 다음 매개 변수를 입력합니다.

```
document.nl_waitBeforeRender = true;
```

내보내기를 활성화하고 PDF으로 변환을 시작하려면 **document.nl_renderToPdf()** 매개 변수가 없는 함수입니다.

### 메모리 할당 {#memory-allocation}

특정 대용량 보고서를 내보낼 때 메모리 할당 오류가 발생할 수 있습니다.

특정 경우 기본값 **최대 MB** (**SKMS** 호스팅된 인스턴스의 경우)에 표시된 JavaScript의 **serverConf.xml** 구성 파일은 64MB로 설정됩니다. 보고서를 내보내는 동안 메모리 부족 오류가 발생하면 이 수치를 512MB로 늘리는 것이 좋습니다.

```
<javaScript maxMB="512" stackSizeKB="8"/>
```

구성에 대한 변경 사항을 적용하려면 **nlserver** 서비스를 다시 시작해야 합니다.

에 대해 자세히 알아보려면 **serverConf.xml** 파일, 참조 [이 섹션](../../production/using/configuration-principle.md).

에 대해 자세히 알아보려면 **nlserver** 서비스, 참조 [이 섹션](../../production/using/administration.md).

## 보고서 인쇄 {#printing-a-report}

보고서를 인쇄하려면 프린터 아이콘을 클릭합니다. 그러면 대화 상자가 열립니다.

더 나은 결과를 위해 Explorer 인쇄 옵션을 편집하고 를 선택합니다. **[!UICONTROL Print background colors and images]**.

![](assets/s_ncs_advuser_report_print_options.png)

## 보고서 아카이브 만들기 {#creating-report-archives}

보고서를 보관하면 다양한 기간에 보고서 보기를 만들 수 있습니다. 예를 들어 주어진 기간에 대한 통계를 표시할 수 있습니다.

아카이브를 만들려면 관련 보고서를 열고 해당 아이콘을 클릭합니다.

![](assets/s_ncs_advuser_report_wizard_07.png)

기존 아카이브를 표시하거나 숨기려면 표시/숨기기 아이콘을 클릭합니다.

![](assets/s_ncs_advuser_report_history_06.png)

보관 날짜는 표시/숨기기 아이콘 아래에 표시됩니다. 아카이브를 클릭하여 확인합니다.

![](assets/s_ncs_advuser_report_history_04.png)

보고서 아카이브를 삭제할 수 있습니다. 이렇게 하려면 보고서가 저장된 Adobe Campaign 노드로 이동합니다. 다음을 클릭합니다. **[!UICONTROL Archives]** 탭을 클릭하고 삭제할 항목을 선택한 다음 를 클릭합니다 **[!UICONTROL Delete]**.

![](assets/s_ncs_advuser_report_history_01.png)
