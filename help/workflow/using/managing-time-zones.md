---
title: 시간대 관리
seo-title: 시간대 관리
description: 시간대 관리
seo-description: null
page-status-flag: never-activated
uuid: a253861a-fc15-406d-969d-33cfb4169839
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 8bcbcd23-9251-412a-ae72-11f15db74112
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 시간대 관리{#managing-time-zones}

Adobe Campaign을 사용하면 동일한 인스턴스에서 관련된 여러 국가 간 시간 지연을 관리할 수 있습니다. 적용된 구성은 인스턴스 생성 중에 구성됩니다.

Adobe Campaign에서 시간대 구성에 대한 자세한 내용은 이 [섹션을](../../installation/using/time-zone-management.md)참조하십시오.

워크플로우에서는 활동 실행 일정을 조정하고 특정 시간대를 활동 또는 전체 워크플로우에 연결할 수 있습니다. 이 구성은 파일을 가져올 때 또는 배달 예약의 프레임워크 내에서 유용할 수 있습니다.

## 실행 예약 {#execution-scheduling}

스케줄러를 사용하여 작업 실행을 예약할 수 [있습니다](../../workflow/using/scheduler.md). 이 기능을 제공하는 활동에서 사용할 수 있는 예약 옵션을 사용할 수도 있습니다. 이러한 활동은 **[!UICONTROL Schedule]** 탭을 제공합니다. **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]****[!UICONTROL Email reception]** 및 **[!UICONTROL SMS]**&#x200B;등

모든 예약 작업, 즉 예약 옵션이 있는 모든 활동에 대해 적용할 시간대를 선택할 수 있습니다. 시간대는 관련 활동의 **[!UICONTROL Advanced]** 탭을 통해 선택됩니다.

![](assets/wf-timezone-in-a-box.png)

가능한 값은 다음과 같습니다.

* 서버 표준 시간대

   Adobe Campaign 애플리케이션 서버의 시간대를 사용합니다.

* 사용자 표준 시간대

   워크플로우를 실행하는 Adobe Campaign 연산자의 시간대를 사용합니다.

* 데이터베이스 시간대

   사용된 데이터베이스 서버의 시간대를 사용합니다.

* 특정 시간대

   선택한 시간대를 사용합니다.

이 **[!UICONTROL By default]** 값을 선택하면 워크플로우의 시간대가 적용되거나 애플리케이션 서버의 시간대가 적용됩니다.

## 활동에 표준 시간대 연결 {#linking-a-time-zone-to-an-activity}

워크플로우 활동의 **[!UICONTROL Advanced]** 탭을 사용하여 시간대를 선택할 수 있습니다. 대부분의 경우 워크플로우의 표준 시간대가 충분하지만 날짜를 올바른 표준 시간대로 연결하기 위해 데이터 가져오기와 같은 특정 활동에 대해 현재 및 다시 오버로드해야 합니다.
