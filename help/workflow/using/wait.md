---
solution: Campaign Classic
product: campaign
title: 대기
description: 대기 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---


# 대기{#wait}

대기 **** 활동은 몇 초에서 몇 개월 사이의 시간 지연 후에 전환을 활성화합니다. 대기 작업은 다른 작업의 실행을 차단하지 않습니다.워크플로우는 이 작업이 보류 중일 때 동시에 작업을 실행할 수 있습니다.

아래 예와 같이 편집기를 사용하여 레이블을 입력하고 대기 시간을 입력할 수 있습니다.

![](assets/edit_wait.png)

필드에서 값 **[!UICONTROL Duration]** 은 선택 단위로 표시할 수 있습니다.(연산자의 지역 설정에 따라):

* 지역 설정이 지정되지 않은 경우: **s** for seconds, **h** for hours, **** d **days,** y **** for years. 승인 시 값은 자동으로 가장 읽을 수 있는 단위로 변환됩니다.

   기본 단위는 일(**d**)입니다.

* 반면에 예를 들어 지역 설정이 &#39;Français&#39;로 설정되어 있는 경우: **s** for seconds, **h** for **hours,** h **for** hours, **j** j **days, for months,** forfor년. 승인 시, 이 값은 위의 **90년대** 예와 같이 가장 읽기 쉬운 단위로 자동 변환되며 **1mn 30대로**&#x200B;변환되었습니다.

   기본 단위는 일(**d**)입니다.

