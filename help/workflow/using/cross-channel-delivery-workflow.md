---
product: campaign
title: 크로스 채널 게재 워크플로우
description: 크로스 채널 게재 워크플로우에 대해 자세히 알아보기
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---

# 크로스 채널 게재 워크플로우{#cross-channel-delivery-workflow}

![](../../assets/common.svg)

이 사용 사례에서는 채널 간 게재 워크플로우와 관련된 예를 제공합니다. 크로스 채널 게재에 대한 일반적인 개념은 다음과 같습니다 [이 섹션](cross-channel-deliveries.md).

목표는 데이터베이스의 수신자로부터 대상자를 다른 그룹으로 세분화하여 그룹에 전자 메일을 보내고 다른 그룹에 SMS 메시지를 보내는 것입니다.

이 사용 사례에 대한 기본 구현 단계는 다음과 같습니다.

1. 만들기 **[!UICONTROL Query]** 활동을 통해 대상을 타깃팅할 수 있습니다.
1. 만들기 **[!UICONTROL Email delivery]** 오퍼에 대한 링크가 포함된 활동.
1. 사용 **[!UICONTROL Split]** 활동 대상:

   * 첫 번째 이메일을 열지 않은 수신자에게 다른 이메일을 보냅니다.
   * 이메일을 열었지만 오퍼에 대한 링크를 클릭하지 않은 수신자에게 SMS를 보냅니다.
   * 이메일을 열고 링크를 클릭한 수신자를 데이터베이스에 추가합니다.

![](assets/wkf_cross-channel_7.png)

## 1단계: 대상자 타겟팅 {#step-1--targeting-the-audience}

대상을 정의하려면 수신자를 식별하는 쿼리를 만듭니다.

1. 캠페인 만들기. 이 작업에 대한 자세한 정보는 [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)을 참조하십시오.
1. 에서 **[!UICONTROL Targeting and workflows]** 캠페인의 탭에서 다음을 추가합니다 **쿼리** 활동을 워크플로우에 추가합니다. 이 활동 사용에 대한 자세한 내용은 [이 섹션](query.md).
1. 게재를 받을 수신자를 정의합니다. 예를 들어 &#39;골드&#39; 멤버를 대상 차원으로 선택합니다.
1. 쿼리에 필터링 조건을 추가합니다. 이 예제에서는 이메일 주소와 모바일 번호가 있는 수신자를 선택합니다.

   ![](assets/wkf_cross-channel_3.png)

1. 변경 내용을 저장합니다.

## 2단계: 오퍼가 포함된 이메일 만들기 {#step-2--creating-an-email-including-an-offer}

1. 만들기 **[!UICONTROL Email delivery]** 활동을 편집하고 워크플로우에서 두 번 클릭합니다. 이메일 만들기에 대한 자세한 내용은 [이 섹션](../../delivery/using/about-email-channel.md).
1. 메시지를 디자인하고 오퍼가 포함된 링크를 컨텐츠에 삽입합니다.

   ![](assets/wkf_cross-channel_1.png)

   메시지 본문에 오퍼를 통합하는 방법에 대한 자세한 내용은 [이 섹션](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. 변경 내용을 저장합니다.
1. 마우스 오른쪽 단추를 클릭합니다. **[!UICONTROL Email delivery]** 활동을 클릭하여 엽니다.
1. 을(를) 선택합니다 **[!UICONTROL Generate an outbound transition]** 모집단 및 추적 로그를 복구하는 옵션입니다.

   ![](assets/wkf_cross-channel_2.png)

   이렇게 하면 첫 번째 이메일을 받을 때 수신자의 행동에 따라 다른 게재를 보내는 데 이 정보를 사용할 수 있습니다.

1. 추가 **[!UICONTROL Wait]** 활동을 통해 수신자가 이메일을 열 수 있도록 며칠 동안 할 수 있습니다.

   ![](assets/wkf_cross-channel_4.png)

## 3단계: 결과 대상 세그먼트화 {#step-3--segmenting-the-resulting-audience}

타겟이 식별되고 첫 번째 게재를 만든 후에는 필터링 조건을 사용하여 대상을 다른 모집단으로 세분해야 합니다.

1. 추가 **분할** 활동을 워크플로우에 추가하고 엽니다. 이 활동 사용에 대한 자세한 내용은 [이 섹션](split.md).
1. 쿼리에서 업스트림 계산된 모집단에서 세 개의 세그먼트를 만듭니다.

   ![](assets/wkf_cross-channel_6.png)

1. 첫 번째 하위 세트에 대해 **[!UICONTROL Add a filtering condition on the inbound population]** 옵션을 선택하고 **[!UICONTROL Edit]**.

   ![](assets/wkf_cross-channel_8.png)

1. 선택 **[!UICONTROL Recipients of a delivery]** 을 제한 필터로 사용하고 을 클릭합니다. **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_9.png)

1. 필터 설정에서 을 선택합니다. **[!UICONTROL Recipients who have not opened or clicked (email)]** 에서 **[!UICONTROL Behavior]** 드롭다운 목록을 클릭한 후 게재 목록에서 전송할 오퍼가 포함된 이메일을 선택합니다. **[!UICONTROL Finish]**&#x200B;를 클릭합니다.

   ![](assets/wkf_cross-channel_10.png)

1. 두 번째 하위 세트에 대해 유사하게 진행하고 을 선택합니다. **[!UICONTROL Recipients who have not clicked (email)]** 에서 **[!UICONTROL Behavior]** 드롭다운 목록.

   ![](assets/wkf_cross-channel_11.png)

1. 세 번째 하위 세트에 대해 **[!UICONTROL Add a filtering condition on the inbound population]** 및 **[!UICONTROL Edit]**&#x200B;에서 을(를) 선택합니다. **[!UICONTROL Use a specific filtering dimension]** 선택 사항입니다.
1. 선택 **[!UICONTROL Recipient tracking log]** 에서 **[!UICONTROL Filtering dimension]** 드롭다운 목록, 강조 표시 **[!UICONTROL Filtering conditions]** 에서 **[!UICONTROL List of restriction filters]** 을(를) 클릭합니다. **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_12.png)

1. 다음과 같이 필터 조건을 선택합니다.

   ![](assets/wkf_cross-channel_13.png)

1. 클릭 **[!UICONTROL Finish]** 변경 사항을 저장하려면 을 클릭합니다.

## 4단계: 워크플로우 완료 {#step-4--finalizing-the-workflow}

1. 워크플로우에 다음 위치에서 생성된 세 개의 하위 집합 뒤에 관련 활동을 추가합니다. **[!UICONTROL Split]** 활동:

   * 추가 **[!UICONTROL Email delivery]** 활동을 사용하여 첫 번째 하위 집합으로 미리 알림 이메일을 보냅니다.
   * 추가 **[!UICONTROL Mobile delivery]** 활동을 통해 두 번째 하위 세트에 SMS 메시지를 보냅니다.
   * 추가 **[!UICONTROL List update]** 활동에 해당 수신자를 데이터베이스에 추가합니다.

1. 워크플로우에서 게재 활동을 두 번 클릭하여 편집합니다. 이메일 및 SMS 만들기에 대한 자세한 내용은 [이메일 채널](../../delivery/using/about-email-channel.md) 및 [SMS 채널](../../delivery/using/sms-channel.md).
1. 를 두 번 클릭합니다. **[!UICONTROL List update]** 활동을 선택하고 을(를) 선택합니다 **[!UICONTROL Generate an outbound transition]** 선택 사항입니다.

   그런 다음 결과 수신자를 Adobe Campaign에서 Adobe Experience Cloud으로 내보낼 수 있습니다. 예를 들어, Adobe Target에서 대상을 **[!UICONTROL Update shared audience]** 활동을 워크플로우에 추가합니다. 자세한 내용은 [대상 내보내기](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. 을(를) 클릭합니다. **시작** 작업 표시줄의 단추를 클릭하여 워크플로우를 실행합니다.

타겟팅된 인구 **쿼리** 활동은 수신자의 행동에 따라 이메일 또는 SMS 게재를 수신하도록 세그먼트화됩니다. 나머지 모집단은 **[!UICONTROL List update]** 활동.
