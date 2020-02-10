---
title: 대기
seo-title: 대기
description: 대기
seo-description: null
page-status-flag: never-activated
uuid: 55e4f15d-8d69-45b1-b842-5ccdfdedf550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 41bcfe67-b5d6-4ee6-9f8a-6a7a208e2036
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 대기{#wait}

대기 **활동은** 몇 초에서 몇 달 사이의 시간 지연 후 전환을 활성화합니다. 대기 작업은 다른 작업의 실행을 차단하지 않습니다.워크플로우는 이 작업이 보류 중일 때 동시에 작업을 실행할 수 있습니다.

아래 예와 같이 편집기를 사용하여 레이블과 대기 시간을 입력할 수 있습니다.

![](assets/edit_wait.png)

필드에서 **[!UICONTROL Duration]** 값을 원하는 단위로 표시할 수 있습니다.(연산자의 지역 설정에 따라):

* 지역 설정이 지정되지 않은 경우: **몇 초 동안,** m **for** minutes, **h** for hours, **h****for days,** yfor years, forcontinues. 승인 시 값은 자동으로 가장 읽기 쉬운 단위로 변환됩니다.

   기본 단위는 일(**d**)입니다.

* 예를 들어 지역 설정이 &#39;Français&#39;로 설정되어 있는 경우: **몇 초 동안,** 몇 초 동안 **,** 그 **사람은** 몇 시간 동안, **h** h **j, 낮의 경우,** j는 **몇 달, 남은 시간은** , 평균은 0년간입니다. 승인 시 이 값은 자동으로 가장 읽기 쉬운 단위로 변환됩니다. 위의 예에서 **90년대** 예는 **1mn 30대로**&#x200B;변환되었습니다.

   기본 단위는 일(**d**)입니다.

