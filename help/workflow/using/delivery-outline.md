---
solution: Campaign Classic
product: campaign
title: 게재 개요
description: 배달 개요 워크플로우 활동에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---


# 게재 개요{#delivery-outline}

**배달 개요**&#x200B;를 사용하면 캠페인 워크플로우에서 개요를 사용할 수 있습니다. 미리 캠페인에서 윤곽선을 만들었어야 합니다.

Adobe Campaign의 배달 아웃라인에 대한 자세한 내용은 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)을 참조하십시오.

활동을 구성하려면 계획된 연락처 날짜와 원하는 개요를 선택하기만 하면 됩니다. 유형 또는 분류 규칙을 추가하여 필터링 규칙을 추가할 수 있습니다.

## 예:배달 외곽선 {#example--inserting-an-offer-via-a-delivery-outline}을 통해 오퍼 삽입

캠페인 워크플로우에서 사용할 수 있는 **배달 개요** 활동에서는 진행 중인 현재 캠페인의 배달 개요에서 참조되는 오퍼를 표시할 수 있습니다.

>[!NOTE]
>
>**Interaction** 패키지를 설치해야 합니다.

1. 워크플로우에서 배달 활동을 추가하기 전에 배달 개요 활동을 추가합니다.
1. 배달 개요 활동에서 사용할 개요를 지정합니다.

   배달 외곽선 지정에 대한 자세한 내용은 이 [섹션](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)을 참조하십시오.

1. 게재에 따라 사용 가능한 필드를 완료합니다.
1. 다음과 같은 두 가지 경우가 있습니다.

   * 오퍼 엔진을 호출하려면 **[!UICONTROL Restrict the number of propositions selected]** 상자를 선택합니다. 전달에 제공할 오퍼 공간과 제안 수를 지정합니다.

      오퍼 가중치와 자격 조건 규칙은 오퍼 엔진에서 고려됩니다.

   * 이 상자를 선택하지 않으면 오퍼 엔진을 호출하지 않고 배달 아웃라인의 모든 오퍼가 표시됩니다.

   미리 보기는 배달에 지정된 오퍼 수를 고려합니다. Workflow를 실행할 때 고려되는 배달 아웃라인에 지정된 번호입니다.

   ![](assets/int_compo_offre_wf1.png)

