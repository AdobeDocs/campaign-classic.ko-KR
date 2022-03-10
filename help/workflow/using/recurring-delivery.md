---
product: campaign
title: 반복 게재
description: 반복 게재 워크플로우 활동에 대해 자세히 알아보십시오
feature: Workflows
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 6f0479cfe6c6801eb44fcc7a35bdac1241ec3be6
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 17%

---

# 반복 게재{#recurring-delivery}

![](../../assets/common.svg)

A **[!UICONTROL Recurring delivery]** 활동을 사용하면 캠페인에만 해당하는 게재 템플릿 발생을 구성할 수 있습니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#recurring-delivery-video)

이 활동은 **[!UICONTROL Targeting and workflows]** 탭에서 찾을 수 있습니다.

방법은 다음과 같습니다.

1. 활동이 기반으로 할 게재 템플릿을 선택합니다.

   ![](assets/recurring_delivery_001.png)

1. 게재 템플릿을 구성합니다.

이 활동에 대한 구성 프로세스는 사용 가능한 옵션 측면에서 게재 템플릿을 만드는 프로세스와 유사합니다. 자세한 정보는 이 [섹션](../../delivery/using/about-templates.md)을 참조하십시오.

사용 중인 이 활동의 예는 다음 항목을 참조하십시오 [섹션](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## 반복 게재를 설정하는 방법

A **반복 게재** 가 실행될 때마다 새 게재 인스턴스를 만듭니다. 예를 들어 워크플로우를 일주일에 한 번 실행하도록 예약하면 1년 후 52회 게재가 됩니다. 즉, 광범위한 로그 및 추적 로그는 각 게재 인스턴스로 구분됩니다.

![반복 게재](assets/delivery_recurring.jpg)

반복 게재 실행을 중지하려면 캠페인을 완전히 취소하거나 캠페인 실행 워크플로우를 중지해야 합니다. Campaign 대시보드에서 게재를 중지하면 게재 발생만 중지됩니다. 각 워크플로우 실행 시 되풀이되는 게재의 다음 인스턴스는 계속 생성됩니다.

>[!NOTE]
>
>에서 증명을 보낼 수 없습니다. **[!UICONTROL Recurring delivery]** 유형 활동.
> 
>캠페인 워크플로우를 통해 직접 게재를 만들려면 미리 구성된 채널별 활동(예: **[!UICONTROL Email delivery]**).

## 튜토리얼 비디오 (#recurring-delivery-video)

이 비디오에서는 반복 게재 및 스케줄러 활동을 구성하는 방법을 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
