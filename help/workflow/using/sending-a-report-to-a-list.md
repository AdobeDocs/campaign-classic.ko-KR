---
product: campaign
title: 목록으로 보고서 보내기
description: 워크플로우를 사용하여 목록으로 보고서를 보내는 방법 알아보기
feature: Workflows
exl-id: cb24aea5-f3c7-4b17-8899-1792ea18c235
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---

# 목록으로 보고서 보내기{#sending-a-report-to-a-list}

![](../../assets/common.svg)

이 사용 사례에서는 월별 기본 제공 세트를 생성하는 방법을 자세히 설명합니다 **[!UICONTROL Tracking indicators]** 수신자 목록으로 보내는 방법 및 PDF 형식으로 보고서를 보냅니다.

![](assets/use_case_report_intro.png)

이 사용 사례에 대한 기본 구현 단계는 다음과 같습니다.

* 게재를 받을 수신자 목록 만들기(참조: [1단계: 수신자 목록 만들기](#step-1--creating-the-recipient-list)).
* 워크플로우를 실행할 때마다 새 게재를 생성할 수 있는 게재 템플릿 만들기(참조: [2단계: 게재 템플릿 만들기](#step-2--creating-the-delivery-template)).
* 보고서를 PDF 형식으로 생성하여 수신자 목록으로 보낼 수 있는 워크플로우를 만듭니다(참조: [3단계: 워크플로우 만들기](#step-3--creating-the-workflow)).

## 1단계: 수신자 목록 만들기 {#step-1--creating-the-recipient-list}

로 이동합니다. **[!UICONTROL Profiles and targets]** 탭에서 **[!UICONTROL Lists]** 링크를 클릭한 다음 **[!UICONTROL Create]** 버튼을 클릭합니다. 선택 **[!UICONTROL New list]** 로 전송할 보고서에 대한 새 수신자 목록을 만듭니다.

![](assets/use_case_report_1.png)

목록 만들기에 대한 자세한 내용은 다음을 참조하십시오 [섹션](../../platform/using/creating-and-managing-lists.md).

## 2단계: 게재 템플릿 만들기 {#step-2--creating-the-delivery-template}

1. 로 이동합니다. **[!UICONTROL Resources > Templates > Delivery templates]** Adobe Campaign 탐색기의 노드 및 **[!UICONTROL Email delivery]** 기본 제공 템플릿.

   ![](assets/use_case_report_2.png)

   게재 템플릿 만들기에 대한 자세한 내용은 다음을 참조하십시오 [섹션](../../delivery/using/about-templates.md).

1. 다양한 템플릿 매개 변수를 입력합니다. 레이블, target(이전에 만든 수신자 목록), 제목 및 콘텐츠

   ![](assets/use_case_report_3.png)

1. 워크플로우를 실행할 때마다 **[!UICONTROL Tracking indicators]** 보고서가 업데이트됨(참조) [3단계: 워크플로우 만들기](#step-3--creating-the-workflow)). 게재에 최신 버전의 보고서를 포함하려면 **[!UICONTROL Calculated attachment]**:

   계산된 첨부 파일 만들기에 대한 자세한 내용은 다음을 참조하십시오 [섹션](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * 을(를) 클릭합니다. **[!UICONTROL Attachments]** 링크를 클릭하고 를 클릭합니다. **[!UICONTROL Add]**&#x200B;를 선택하고 을 선택합니다. **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * 로 이동합니다. **[!UICONTROL Type]** 필드를 선택하고 네 번째 옵션을 선택합니다. **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      에 입력한 값 **[!UICONTROL Label]** 최종 게재에는 필드가 표시되지 않습니다.

   * 편집 영역으로 이동하여 액세스 경로 및 파일 이름을 입력합니다.

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >파일이 서버에 있어야 합니다. 경로 및 이름은 **[!UICONTROL JavaScript code]** 워크플로우의 유형 활동(참조: [3단계: 워크플로우 만들기](#step-3--creating-the-workflow)).

   * 을(를) 선택합니다 **[!UICONTROL Advanced]** 탭 및 확인 **[!UICONTROL Script the name of the file name displayed in the mails sent]**. 편집 영역으로 이동하여 최종 게재에 첨부 파일을 제공할 이름을 입력합니다.

      ![](assets/use_case_report_6bis.png)

## 3단계: 워크플로우 만들기 {#step-3--creating-the-workflow}

이 사용 사례에 대해 다음 워크플로우가 만들어졌습니다. 여기에는 세 가지 활동이 있습니다.

* 1개 **[!UICONTROL Scheduler]** 한 달에 한 번 워크플로우를 실행할 수 있는 활동 입력
* 1개 **[!UICONTROL JavaScript code]** 보고서를 PDF 형식으로 생성할 수 있는 활동 유형
* 하나 **[!UICONTROL Delivery]** 이전에 만든 게재 템플릿을 사용하는 활동 유형.

![](assets/use_case_report_8.png)

1. 이제 로 이동합니다. **[!UICONTROL Administration > Production > Technical workflows]** 노드 및 새 워크플로우를 만듭니다.

   ![](assets/use_case_report_7.png)

1. 다음을 추가하여 시작합니다 **[!UICONTROL Scheduler]** 활동을 입력하고 워크플로우가 해당 월의 첫 번째 월요일에 실행되도록 구성합니다.

   ![](assets/use_case_report_9.png)

   스케줄러 구성에 대한 자세한 내용은 [스케줄러](scheduler.md).

1. 그런 다음 **[!UICONTROL JavaScript code]** 유형 활동.

   ![](assets/use_case_report_10.png)

   편집 영역에 다음 코드를 입력합니다.

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   다음 변수가 사용됩니다.

   * **var reportName**: 보고서의 내부 이름을 큰따옴표로 입력합니다. 이 경우 의 내부 이름입니다 **추적 표시기** 보고서가 &quot;deliveryFeedback&quot;입니다.
   * **var 경로**: 파일(&quot;tmp/files/&quot;), 파일(&quot;deliveryFeedback&quot;) 및 파일 확장명(&quot;.pdf&quot;)의 저장 경로를 입력합니다. 이 경우 내부 이름을 파일 이름으로 사용했습니다. 값은 큰따옴표 사이에 있어야 하고 &quot;+&quot; 문자로 구분해야 합니다.

      >[!CAUTION]
      >
      >파일을 서버에 저장해야 합니다. 같은 경로와 같은 이름을 **[!UICONTROL General]** 계산된 첨부 파일의 편집 창 탭(참조: [2단계: 게재 템플릿 만들기](#step-2--creating-the-delivery-template)).

   * **var exportFormat**: 파일(&quot;PDF&quot;)의 내보내기 형식을 입력합니다.
   * **var_ctx** (컨텍스트): 이 경우에는 **[!UICONTROL Tracking indicators]** 글로벌 컨텍스트에서 보고합니다.

1. 을(를) 추가하여 마칩니다. **[!UICONTROL Delivery]** 다음 옵션을 사용하여 활동을 입력합니다.

   * **[!UICONTROL Delivery]**: 선택 **[!UICONTROL New, created from a template]**&#x200B;을 누르고 이전에 만든 게재 템플릿을 선택합니다.
   * 대상 **[!UICONTROL Recipients]** 및 **[!UICONTROL Content]** 필드, 선택 **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**: 선택 **[!UICONTROL Prepare and start]**.
   * 확인 취소 **[!UICONTROL Generate an outbound transition]** 및 **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)
