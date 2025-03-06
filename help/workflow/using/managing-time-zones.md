---
product: campaign
title: 표준 시간대 관리
description: 표준 시간대 관리
feature: Workflows
hide: true
hidefromtoc: true
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 3%

---

# 표준 시간대 관리{#managing-time-zones}



Adobe Campaign을 사용하면 동일한 인스턴스로 관련된 다양한 국가 간의 시간 차이를 관리할 수 있습니다. 적용된 구성은 인스턴스 생성 중 구성됩니다.

Adobe Campaign에서 시간대를 구성하는 방법에 대한 자세한 내용은 [Campaign Classic v7 설치 안내서](../../installation/using/time-zone-management.md)를 참조하십시오.

워크플로우에서 활동 실행 일정을 조정하고 특정 시간대를 활동 또는 전체 워크플로우에 연결할 수 있습니다. 이 구성은 파일을 가져올 때 또는 배달 예약의 프레임워크 내에서 유용할 수 있습니다.

## 실행 예약 {#execution-scheduling}

스케줄러를 사용하여 작업 실행을 예약할 수 있습니다([스케줄러](scheduler.md) 참조). 이 기능을 제공하는 활동에서 사용할 수 있는 예약 옵션을 사용할 수도 있습니다. 이러한 활동은 **[!UICONTROL Schedule]** 탭을 제공합니다. **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** 및 **[!UICONTROL SMS]** 등

모든 예약된 작업, 즉 예약 옵션이 있는 모든 활동에 대해 적용할 시간대를 선택할 수 있습니다. 관련 활동의 **[!UICONTROL Advanced]** 탭을 통해 시간대를 선택합니다.

![](assets/wf-timezone-in-a-box.png)

가능한 값:

* 서버 시간대

  Adobe Campaign 애플리케이션 서버의 시간대를 사용합니다.

* 사용자 시간대

  워크플로우를 실행하는 Adobe Campaign 연산자의 시간대를 사용합니다.

* 데이터베이스 시간대

  사용된 데이터베이스 서버의 시간대를 사용합니다.

* 특정 시간대

  선택한 시간대를 사용합니다.

**[!UICONTROL By default]** 값을 선택하면 워크플로의 시간대가 적용되거나, 그렇지 않으면 응용 프로그램 서버의 시간대가 적용됩니다.

## 활동에 시간대 연결 {#linking-a-time-zone-to-an-activity}

워크플로우 활동의 **[!UICONTROL Advanced]** 탭에서 시간대를 선택할 수 있습니다. 대부분의 시간대에서는 워크플로우의 시간대로 충분하지만, 날짜를 올바른 시간대로 연결하기 위해 데이터 가져오기와 같은 특정 활동에 대해 워크플로우를 지금부터 다시 오버로드해야 할 수 있습니다.
