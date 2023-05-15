---
product: campaign
title: 표준 시간대 관리
description: 표준 시간대 관리
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 4%

---

# 시간대 관리{#managing-time-zones}



Adobe Campaign을 사용하면 동일한 인스턴스에 의해 관련된 다양한 국가 간에 시간 지연을 관리할 수 있습니다. 적용된 구성은 인스턴스를 생성하는 동안 구성됩니다.

Adobe Campaign에서 시간대 구성에 대한 자세한 내용은 [Campaign Classic v7 설치 안내서](../../installation/using/time-zone-management.md).

워크플로우에서는 활동 실행 일정을 조정하고 특정 시간대를 활동 또는 전체 워크플로우에 연결할 수 있습니다. 이 구성은 파일을 가져오거나 게재 예약 프레임워크 내에서 사용할 때 유용합니다.

## 실행 예약 {#execution-scheduling}

스케줄러를 사용하여 작업 실행을 예약할 수 있습니다( [스케줄러](scheduler.md)). 이 기능을 제공하는 활동에서 사용할 수 있는 예약 옵션을 사용할 수도 있습니다. 이러한 활동은 다음을 제공합니다 **[!UICONTROL Schedule]** 탭: **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**&#x200B;등

예약된 모든 작업, 즉 예약 옵션이 있는 모든 활동에 대해 적용할 시간대를 선택할 수 있습니다. 시간대는 을 통해 선택됩니다 **[!UICONTROL Advanced]** 관련 활동의 탭:

![](assets/wf-timezone-in-a-box.png)

가능한 값은 다음과 같습니다.

* 서버 시간대

   Adobe Campaign 애플리케이션 서버의 시간대를 사용합니다.

* 사용자 시간대

   워크플로우를 실행하는 Adobe Campaign 연산자의 시간대를 사용합니다.

* 데이터베이스 시간대

   사용된 데이터베이스 서버의 시간대를 사용합니다.

* 특정 시간대

   선택한 시간대를 사용합니다.

만약 **[!UICONTROL By default]** 값이 선택되면 워크플로우의 시간대가 적용되거나, 그렇지 않으면 애플리케이션 서버의 시간대가 적용됩니다.

## 활동에 시간대 연결 {#linking-a-time-zone-to-an-activity}

다음 **[!UICONTROL Advanced]** 워크플로우 활동의 탭에서 표준 시간대를 선택할 수 있습니다. 대부분의 경우 워크플로우의 시간대로도 충분하지만, 날짜를 올바른 시간대로 연결하기 위해 데이터 가져오기와 같은 특정 활동에 대해 현재와 다시 오버로드해야 할 수 있습니다.
