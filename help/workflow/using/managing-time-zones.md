---
solution: Campaign Classic
product: campaign
title: 시간대 관리
description: 시간대 관리
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 3%

---


# 시간대 관리{#managing-time-zones}

Adobe Campaign을 사용하면 동일한 인스턴스에서 관련된 여러 국가 간 시간 지연을 관리할 수 있습니다. 인스턴스 생성 중에 적용된 구성이 구성됩니다.

Adobe Campaign에서 시간대 구성에 대한 자세한 내용은 이 [섹션](../../installation/using/time-zone-management.md)을 참조하십시오.

워크플로우에서는 활동 실행 일정을 조정하고 특정 시간대를 활동 또는 전체 워크플로우에 연결할 수 있습니다. 이 구성은 파일을 가져올 때 또는 배달 예약의 프레임워크 내에서 유용합니다.

## 실행 예약 {#execution-scheduling}

스케줄러를 사용하여 작업 실행을 예약할 수 있습니다([스케줄러](../../workflow/using/scheduler.md) 참조). 이 기능을 제공하는 활동에서 사용할 수 있는 예약 옵션을 사용할 수도 있습니다. 이러한 활동은 **[!UICONTROL Schedule]** 탭을 제공합니다.**[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]** 등

모든 예약된 작업(예약 옵션이 있는 모든 활동)에 대해 적용할 시간대를 선택할 수 있습니다. 시간대는 관련 활동의 **[!UICONTROL Advanced]** 탭을 통해 선택됩니다.

![](assets/wf-timezone-in-a-box.png)

가능한 값은 다음과 같습니다.

* 서버 시간대

   Adobe Campaign 응용 프로그램 서버의 표준 시간대를 사용합니다.

* 사용자 시간대

   워크플로우를 실행하는 Adobe Campaign 연산자의 시간대를 사용합니다.

* 데이터베이스 시간대

   사용된 데이터베이스 서버의 시간대를 사용합니다.

* 특정 시간대

   선택한 시간대를 사용합니다.

**[!UICONTROL By default]** 값을 선택하면 워크플로우의 시간대가 적용되거나, 그렇지 않으면 응용 프로그램 서버의 시간대가 적용됩니다.

## 표준 시간대를 활동 {#linking-a-time-zone-to-an-activity}에 연결

워크플로우 활동의 **[!UICONTROL Advanced]** 탭에서는 시간대를 선택할 수 있습니다. 대부분의 경우 워크플로우의 시간대는 충분하지만, 날짜를 올바른 시간대로 연결하기 위해 데이터 가져오기와 같은 특정 활동에 대해 현재와 다시 과부화해야 할 수 있습니다.
