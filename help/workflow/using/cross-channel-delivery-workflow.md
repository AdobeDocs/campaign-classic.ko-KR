---
product: campaign
title: 크로스 채널 게재 워크플로우
description: 크로스 채널 게재 워크플로우에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---

# 크로스 채널 게재 워크플로우{#cross-channel-delivery-workflow}



이 사용 사례에서는 채널 간 게재 워크플로우와 관련된 예제를 제공합니다. 크로스채널 게재의 일반적인 개념은에 나와 있습니다. [이 섹션](cross-channel-deliveries.md).

목표는 데이터베이스 수신자의 대상자를 다른 그룹으로 세분화하여 이메일을 그룹에 보내고 SMS 메시지를 다른 그룹에 보내는 것입니다.

이 사용 사례의 주요 구현 단계는 다음과 같습니다.

1. 만들기 **[!UICONTROL Query]** 활동을 통해 대상자를 타겟팅합니다.
1. 만들기 **[!UICONTROL Email delivery]** 오퍼에 대한 링크가 포함된 활동.
1. 사용 **[!UICONTROL Split]** 활동 대상:

   * 첫 번째 이메일을 열지 않은 수신자에게 다른 이메일을 보냅니다.
   * 이메일을 열었지만 오퍼에 대한 링크를 클릭하지 않은 수신자에게 SMS를 보냅니다.
   * 이메일을 열고 링크를 클릭한 수신자를 데이터베이스에 추가합니다.

![](assets/wkf_cross-channel_7.png)

## 1단계: 대상자 타겟팅 {#step-1--targeting-the-audience}

대상을 정의하려면 수신자를 식별하는 쿼리를 만듭니다.

1. 캠페인 만들기. 이 작업에 대한 자세한 정보는 [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)을 참조하십시오.
1. 다음에서 **[!UICONTROL Targeting and workflows]** 캠페인의 탭에서 **쿼리** 활동을 워크플로우에 추가합니다. 이 활동 사용에 대한 자세한 내용은 을 참조하십시오. [이 섹션](query.md).
1. 게재를 받을 수신자를 정의합니다. 예를 들어 &#39;골드&#39; 멤버를 대상 차원으로 선택합니다.
1. 쿼리에 필터링 조건을 추가합니다. 이 예에서는 전자 메일 주소와 휴대폰 번호가 있는 수신자를 선택합니다.

   ![](assets/wkf_cross-channel_3.png)

1. 변경 내용을 저장합니다.

## 2단계: 오퍼를 포함하는 이메일 만들기 {#step-2--creating-an-email-including-an-offer}

1. 만들기 **[!UICONTROL Email delivery]** 활동을 만든 후 워크플로우에서 두 번 클릭하여 편집합니다. 전자 메일 만들기에 대한 자세한 내용은 [이 섹션](../../delivery/using/about-email-channel.md).
1. 메시지를 디자인하고 오퍼를 포함하는 링크를 콘텐츠에 삽입합니다.

   ![](assets/wkf_cross-channel_1.png)

   오퍼를 메시지 본문에 통합하는 방법에 대한 자세한 내용은 을 참조하십시오. [이 섹션](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. 변경 내용을 저장합니다.
1. 마우스 오른쪽 단추 클릭 **[!UICONTROL Email delivery]** 활동을 통해 엽니다.
1. 다음 항목 선택 **[!UICONTROL Generate an outbound transition]** 모집단과 추적 로그를 복구하는 옵션입니다.

   ![](assets/wkf_cross-channel_2.png)

   이렇게 하면 첫 번째 이메일을 받을 때 이 정보를 사용하여 수신자의 행동에 따라 다른 게재를 보낼 수 있습니다.

1. 추가 **[!UICONTROL Wait]** 활동은 수신자가 며칠 동안 이메일을 열 수 있도록 해 줍니다.

   ![](assets/wkf_cross-channel_4.png)

## 3단계: 결과 대상자 세그먼트화 {#step-3--segmenting-the-resulting-audience}

타겟이 식별되고 첫 번째 게재가 생성되면 필터링 조건을 사용하여 타겟을 다양한 모집단으로 세분화해야 합니다.

1. 추가 **분할** 활동을 워크플로우에 추가하고 엽니다. 이 활동 사용에 대한 자세한 내용은 을 참조하십시오. [이 섹션](split.md).
1. 쿼리에서 업스트림으로 계산한 모집단에서 3개의 세그먼트를 만듭니다.

   ![](assets/wkf_cross-channel_6.png)

1. 첫 번째 하위 집합의 경우 **[!UICONTROL Add a filtering condition on the inbound population]** 옵션 및 클릭 **[!UICONTROL Edit]**.

   ![](assets/wkf_cross-channel_8.png)

1. 선택 **[!UICONTROL Recipients of a delivery]** 를 제한 필터로 사용하고 **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_9.png)

1. 필터 설정에서 을 선택합니다. **[!UICONTROL Recipients who have not opened or clicked (email)]** 다음에서 **[!UICONTROL Behavior]** 드롭다운 목록에서 게재 목록에서 보낼 오퍼가 포함된 이메일을 선택합니다. **[!UICONTROL Finish]**&#x200B;를 클릭합니다.

   ![](assets/wkf_cross-channel_10.png)

1. 두 번째 하위 집합에 대해서도 유사하게 진행하고 을 선택합니다. **[!UICONTROL Recipients who have not clicked (email)]** 다음에서 **[!UICONTROL Behavior]** 드롭다운 목록입니다.

   ![](assets/wkf_cross-channel_11.png)

1. 세 번째 하위 집합의 경우 **[!UICONTROL Add a filtering condition on the inbound population]** 및 클릭 **[!UICONTROL Edit]**&#x200B;를 선택하고 **[!UICONTROL Use a specific filtering dimension]** 옵션을 선택합니다.
1. 선택 **[!UICONTROL Recipient tracking log]** 다음에서 **[!UICONTROL Filtering dimension]** 드롭다운 목록, 강조 표시 **[!UICONTROL Filtering conditions]** 다음에서 **[!UICONTROL List of restriction filters]** 및 클릭 **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_12.png)

1. 다음과 같이 필터 조건을 선택합니다.

   ![](assets/wkf_cross-channel_13.png)

1. 클릭 **[!UICONTROL Finish]** 변경 사항을 저장합니다.

## 4단계: 워크플로우 완료 {#step-4--finalizing-the-workflow}

1. 의 하위 집합 세 개 뒤에 관련 활동을 워크플로우에 추가합니다. **[!UICONTROL Split]** 활동:

   * 추가 **[!UICONTROL Email delivery]** 활동은 첫 번째 하위 집합으로 미리 알림 이메일을 보냅니다.
   * 추가 **[!UICONTROL Mobile delivery]** 두 번째 하위 집합으로 SMS 메시지를 보내는 활동.
   * 추가 **[!UICONTROL List update]** 활동을 사용하여 해당 수신자를 데이터베이스에 추가합니다.

1. 워크플로우에서 게재 활동을 두 번 클릭하여 편집합니다. 이메일 및 SMS 만들기에 대한 자세한 내용은 다음을 참조하십시오. [이메일 채널](../../delivery/using/about-email-channel.md) 및 [SMS 채널](../../delivery/using/sms-channel.md).
1. 를 두 번 클릭합니다. **[!UICONTROL List update]** 활동 및 선택 **[!UICONTROL Generate an outbound transition]** 옵션을 선택합니다.

   그런 다음 결과 수신자를 Adobe Campaign에서 Adobe Experience Cloud으로 내보낼 수 있습니다. 예를 들어, 다음을 추가하여 Adobe Target에서 대상을 사용할 수 있습니다. **[!UICONTROL Update shared audience]** 활동을 워크플로우에 추가합니다. 자세한 내용은 다음을 참조하십시오. [대상자 내보내기](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. 다음을 클릭합니다. **시작** 단추를 클릭하여 워크플로우를 실행합니다.

다음에 의해 타겟팅된 모집단 **쿼리** 활동은 수신자의 행동에 따라 이메일 또는 SMS 게재를 받도록 세그먼트화됩니다. 나머지 모집단은 다음을 사용하여 데이터베이스에 추가됩니다 **[!UICONTROL List update]** 활동.
