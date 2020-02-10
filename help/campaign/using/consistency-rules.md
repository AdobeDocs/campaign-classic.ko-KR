---
title: 일관성 규칙
seo-title: 일관성 규칙
description: 일관성 규칙
seo-description: null
page-status-flag: never-activated
uuid: 9b497460-ba42-4bc7-98e0-55c1b4be5e44
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 9bcb5dc1-8cb4-4781-a8cd-8d072ff28b1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 일관성 규칙{#consistency-rules}

## 일관성 규칙 정보 {#about-consistency-rules}

Adobe Campaign은 캠페인 유형 분석에 포함된 규칙 세트를 사용하여 일관된 커뮤니케이션을 보장합니다. 이러한 고객의 목표는 볼륨, 자연, 연관성 등과 같이 수신자에게 전송되는 배송 정보를 관리하는 것입니다.

**예를 들어 용량** 규칙은 메시지 배달로 인해 관련 플랫폼을 오버로드할 수 없도록 합니다. 예를 들어 다운로드 링크가 포함된 특별 오퍼는 서버 채도를 방지하기 위해 한 번에 너무 많은 사람에게 전송해서는 안 됩니다.전화 캠페인은 콜 센터 등의 처리 능력을 초과해서는 안 됩니다. 자세한 내용은 용량 [제어를 참조하십시오](#controlling-capacity).

## 용량 제어 {#controlling-capacity}

메시지를 전달하기 전에 조직에 배달(물리적 인프라), 배달이 생성할 수 있는 응답(인바운드 메시지), 가입자에게 문의할 전화 수(콜 센터 처리 용량) 등이 있는지 확인해야 합니다.

이렇게 하려면 유형 **[!UICONTROL Capacity]** 규칙을 만들어야 합니다.

다음 예에서는 전화 충성도 캠페인에 대한 유형 규칙을 만듭니다. Adobe는 메시지 수를 하루 20개(예: 콜센터의 일일 처리 용량)로 제한합니다. 규칙이 두 개의 게재에 적용되면 로그를 통해 소비를 모니터링할 수 있습니다.

새 용량 규칙을 디자인하려면 아래 절차를 따르십시오.

1. 노드에서 을 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 클릭합니다 **[!UICONTROL New]**.
1. 규칙 유형을 **[!UICONTROL Capacity]** 선택합니다.

   ![](assets/campaign_opt_create_capacity_01.png)

1. 탭에서 가용성 라인을 **[!UICONTROL Capacity]** 생성합니다.이 예에서는 통화가 가능한 기간입니다. 24시간 기간을 선택하고 초기 수량으로 150을 입력합니다. 즉, 콜센터는 하루에 150개의 호출을 처리할 수 있습니다.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >가용성 라인은 정보 용도로만 사용할 수 있습니다. 용량 제한에 도달했을 때 메시지를 제외해야 하는 경우 [이 섹션을](#exclude-messages-when-capacity-limit-reached)참조하십시오.

1. 이 규칙을 유형 분석에 연결한 다음 유형 분석을 전달에 참조하여 이 용량 규칙을 적용합니다. For more on this, refer to [this section](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. 규칙 **[!UICONTROL Consumptions]** 및 **[!UICONTROL Capacity]** 탭에서 소비를 모니터링할 수 있습니다.

   전달에 규칙이 사용될 때 **[!UICONTROL Consumed]** 및 **[!UICONTROL Remaining]** 열은 아래와 같이 로드 정보를 제공합니다.

   ![](assets/campaign_opt_create_capacity_03.png)

   For more on this, refer to [this section](#monitoring-consumption).

## 최대 로드 정의 {#defining-the-maximum-load}

최대 로드를 정의하려면 가용 라인을 정의해야 합니다. 이렇게 하려면 다음 두 가지 옵션을 사용할 수 있습니다.하나 이상의 가용성 라인을 수동으로 생성하거나(가용성 라인 하나씩 [추가 참조](#adding-availability-lines-one-by-one)) 가용성 범위를 생성할 수 있습니다. 이러한 기간의 빈도는 자동화할 수 있습니다(가용성 라인 [세트](#add-a-set-of-availability-lines)추가 참조).

### 가용성 라인 하나씩 추가 {#adding-availability-lines-one-by-one}

가용 라인을 생성하려면 **[!UICONTROL Add]** 버튼을 클릭하고 **[!UICONTROL Add an availability line]**&#x200B;선택합니다. 가용 기간과 사용 가능한 로드를 입력합니다.

![](assets/campaign_opt_create_capacity_02.png)

처리 능력에 맞게 필요한 만큼 라인을 추가합니다.

### 가용성 라인 세트 추가 {#add-a-set-of-availability-lines}

주어진 시간에 대한 가용성 기간을 정의하려면 **[!UICONTROL Add]** 단추를 클릭하고 **[!UICONTROL Add a set of availability lines]** 옵션을 선택합니다. 각 기간의 지속 시간과 만들 기간 수를 나타냅니다.

페이지 작성 빈도를 자동화하려면 **[!UICONTROL Change]** 단추를 클릭하고 기간 예약을 정의합니다.

![](assets/campaign_opt_create_capacity_07.png)

예를 들어 모든 근무일에 대해 9AM에서 5PM 사이의 시간당 10회 호출 비율로 가용 기간을 생성하는 일정을 정의하겠습니다. 이렇게 하려면 다음 단계를 적용합니다.

1. 주기성 유형과 유효 기간 및 시간을 선택합니다.

   ![](assets/campaign_opt_create_capacity_08.png)

1. 유효 일자를 지정합니다.

   ![](assets/campaign_opt_create_capacity_09.png)

1. 승인하기 전에 일정을 확인합니다.

   ![](assets/campaign_opt_create_capacity_10.png)

워크플로우는 일치하는 모든 라인을 자동으로 생성합니다. **[!UICONTROL Forecasting]**

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>파일 가져오기를 통해 가용성 라인을 만드는 것이 좋습니다. 이 탭에서는 소비 라인을 보고 확인할 수 있습니다.

## 용량 제한에 도달하면 메시지 제외 {#exclude-messages-when-capacity-limit-reached}

가용성 라인은 정보 용도로만 제공됩니다. 초과 메시지를 제외하려면 **[!UICONTROL Exclude from the target messages in excess of capacity]** 옵션을 선택합니다. 따라서 용량이 초과되지 않습니다. 이전 예와 동일한 모집단에서 소비와 남은 용량은 초기 수량을 초과할 수 없습니다.

![](assets/campaign_opt_create_capacity_04.png)

처리할 메시지 수는 정의된 가용성 범위 이상으로 균등하게 분류됩니다. 이는 일 단위의 최대 통화 수가 제한되어 있으므로 콜 센터에 특히 유용합니다. 이메일 배달의 경우 이 가용성 범위를 무시하고 동시에 이메일을 보낼 수 **[!UICONTROL Do not limit instantaneous delivery capacity]** 있습니다.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>오버로드의 경우, 저장된 메시지는 배달 속성에 정의된 공식에 따라 선택됩니다.

![](assets/campaign_opt_create_capacity_06.png)

## 모니터링 사용 {#monitoring-consumption}

기본적으로 용량 규칙은 표시 용도로만 사용됩니다. 정의된 로드가 초과되지 않도록 하려면 **[!UICONTROL Exclude messages in excess of capacity from the target]** 옵션을 선택합니다. 이 경우, 초과된 메시지는 이 유형 규칙을 사용하여 게재에서 자동으로 제외됩니다.

소비를 모니터링하려면 Typical 규칙의 탭 **[!UICONTROL Consumed]** 열에 표시된 값을 **[!UICONTROL Capacity]** 봅니다.

![](assets/campaign_opt_create_capacity_04.png)

소비 라인을 보려면 규칙에서 **[!UICONTROL Consumptions]** 탭을 클릭합니다.
