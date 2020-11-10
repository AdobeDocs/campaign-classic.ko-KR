---
title: 게재 개요
description: 배달 개요 워크플로우 활동에 대한 자세한 내용
page-status-flag: never-activated
uuid: 2b924cc6-6b71-481e-acab-2d035bbc2852
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: a2a65f97-425b-44b2-8cf4-beea850423bc
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---


# 게재 개요{#delivery-outline}

전달 **개요를** 사용하면 캠페인 워크플로우에서 개요를 사용할 수 있습니다. 캠페인에서 미리 윤곽선을 만들었어야 합니다.

Adobe Campaign의 배송 개요에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

활동을 구성하려면 계획된 연락처 날짜 및 원하는 개요를 선택하기만 하면 됩니다. 분류 또는 분류 규칙을 추가하여 필터링 규칙을 추가할 수 있습니다.

## 예:배달 개요를 통해 오퍼 삽입 {#example--inserting-an-offer-via-a-delivery-outline}

캠페인 워크플로우에서 사용할 수 있는 **배달 개요** 활동을 사용하면 진행 중인 현재 캠페인의 배달 개요에서 참조되는 오퍼를 표시할 수 있습니다.

>[!NOTE]
>
>상호 **작용** 패키지가 설치되어 있어야 합니다.

1. 워크플로우에서 배달 활동을 추가하기 전에 배달 개요 활동을 추가합니다.
1. 배달 개요 활동에서 사용할 개요를 지정합니다.

   배달 외곽선 지정에 대한 자세한 내용은 이 [섹션을 참조하십시오](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. 게재에 따라 사용 가능한 필드를 완료합니다.
1. 두 가지 가능한 경우가 있습니다.

   * 오퍼 엔진에 전화를 걸려면 **[!UICONTROL Restrict the number of propositions selected]** 상자를 선택하십시오. 전달에 제공할 오퍼 공간과 제안 수를 지정합니다.

      오퍼 가중치와 자격 조건 규칙은 오퍼 엔진에서 고려됩니다.

   * 이 상자를 선택하지 않으면 배달 아웃라인에 있는 모든 오퍼가 오퍼 엔진으로 호출하지 않고 표시됩니다.

   미리 보기는 배달에 지정된 오퍼 수를 고려합니다. 워크플로우를 실행할 때 고려되는 배달 아웃라인에 지정된 번호입니다.

   ![](assets/int_compo_offre_wf1.png)

