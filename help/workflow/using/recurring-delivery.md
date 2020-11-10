---
title: 반복 게재
description: 반복 배달 워크플로우 활동에 대한 자세한 내용
page-status-flag: never-activated
uuid: 715855df-fe29-46e8-a7ab-d534f010a26e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 185d3256-a21e-47d7-bee7-7b91762ca1e2
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 7%

---


# 반복 게재{#recurring-delivery}

활동을 **[!UICONTROL Recurring delivery]** 사용하면 캠페인과 관련된 게재 템플릿 발생을 구성할 수 있습니다.

이 활동은 캠페인에 있는 **[!UICONTROL Targeting and workflows]** 탭에서만 사용할 수 있습니다.

방법은 다음과 같습니다.

1. 활동이 기반으로 할 배달 템플릿을 선택합니다.

   ![](assets/recurring_delivery_001.png)

1. 배달 템플릿을 구성합니다.

이 활동에 대한 구성 프로세스는 사용 가능한 옵션 측면에서 배달 템플릿을 만드는 프로세스와 비슷합니다. 자세한 정보는 이 [섹션](../../delivery/using/about-templates.md)을 참조하십시오.

사용 중인 활동의 예를 보려면 이 [섹션을 참조하십시오](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## 반복 배달을 설정하는 방법

반복 **배달은** 실행될 때마다 새 배달 인스턴스를 만듭니다. 예를 들어, 워크플로우가 일주일에 한 번 실행되도록 예약된 경우 1년 후에 52회의 배달이 됩니다. 또한 광범위한 로그 및 추적 로그가 각 배달 인스턴스로 구분됩니다.

![반복 배달](assets/delivery_recurring.jpg)

이 비디오에서는 반복 게재 및 스케줄러 활동을 구성하는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>유형 활동에서 증거를 보낼 수 **[!UICONTROL Recurring delivery]** 없습니다.\
>캠페인 워크플로우를 통해 배달을 직접 만들려면 미리 구성된 채널별 활동(예: **[!UICONTROL Email delivery]**).
