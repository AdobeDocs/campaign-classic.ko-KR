---
product: campaign
title: 구독 서비스
description: 구독 서비스 워크플로우 활동에 대해 자세히 알아보십시오
feature: Workflows, Targeting Activity, Subscription Services Activity
exl-id: 1b526d1c-4a33-45a1-98f4-dcb803c8d228
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# 구독 서비스{#subscription-services}

![](../../assets/v7-only.svg)

A **구독 서비스**-type 활동을 사용하면 전환에서 지정된 모집단에 대한 정보 서비스 구독을 만들거나 삭제할 수 있습니다.

활동을 구성하려면 활동을 편집하고 해당 레이블을 입력한 다음 다음 다음 예제와 같이 실행할 작업(구독 또는 구독 취소)과 서비스를 선택합니다.

![](assets/edit_service_inscription.png)

1. 활동의 레이블을 입력합니다.
1. 선택 **[!UICONTROL Generate an outbound transition]** 실행 끝에 전환을 만들려면

   일반적으로 정보 서비스에 대한 Target의 구독은 타겟팅 워크플로우의 끝을 표시하며, 이 경우 옵션이 기본적으로 활성화되지 않습니다.

1. 클릭 **[!UICONTROL Subscription]** 또는 **[!UICONTROL Unsubscription]** 지정된 모집단을 선택한 정보 서비스로 구독하거나 구독을 취소하려는 경우
1. 선택 **[!UICONTROL Send a confirmation message]** 을 입력하여 수신자에게 자신이 서비스에 구독 또는 구독 취소되었음을 알립니다.

   이 메시지의 콘텐츠는 정보 서비스와 관련된 게재 템플릿에 지정됩니다. 자세한 정보는 이 [섹션](../../delivery/using/managing-subscriptions.md)을 참조하십시오.

## 예: 뉴스레터에 수신자 목록 가입 {#example--subscribe-a-list-of-recipients-to-a-newsletter}

한 번의 작업으로 다음 워크플로우는 구독자를 모집하기 위해 파리에 거주하는 근로자를 대상으로 뉴스레터에 사용할 수 있는 수신자 목록을 만드는 것을 목표로 합니다.

이렇게 하려면 이미 구독한 수신자도 제외해야 합니다.

>[!CAUTION]
>
>수신자를 서비스에 수동으로 구독하기 전에 이러한 수신자가 사용자의 통신을 수신하도록 허용하는지 확인하십시오.

![](assets/subscription_services_example.png)

1. 다음 세 개의 쿼리를 추가합니다.

   * 한 표적자는 18세에서 60세의 노인입니다.
   * 파리에 거주하는 두 번째 타겟팅 수신자.
   * 현재 뉴스레터를 구독하지 않은 세 번째 타겟팅 수신자입니다.

1. 서로 다른 결과를 상호 참조할 교차 활동을 추가합니다.
1. 원하는 경우 목록 업데이트를 삽입하여 최신 구독자 목록을 최신 상태로 유지합니다.
1. 구독 서비스 활동을 삽입한 다음 이 활동을 두 번 클릭하여 구성합니다.
1. 활동 레이블을 입력하고 을(를) 선택합니다 **[!UICONTROL Subscription]**.

   원하는 경우 을 확인하여 수신자에게 뉴스레터 가입을 알릴 수 있습니다. **[!UICONTROL Send a confirmation message]** 상자.

1. 뉴스레터가 있는 폴더를 선택한 다음 나타나는 목록에서 뉴스레터를 선택합니다.
1. 을(를) 종료하십시오. **[!UICONTROL Generate outbound transition]** 이 활동이 워크플로우의 끝을 표시하도록 선택 취소한 다음 를 클릭합니다 **[!UICONTROL Ok]**.

워크플로우를 실행하는 동안 세 개의 쿼리 모두에 해당하는 수신자가 목록에 추가되고 뉴스레터에 구독됩니다.

로 이동하여 구독이 성공했는지 확인할 수 있습니다. **[!UICONTROL Subscription]** 탭을 클릭합니다.

## 입력 매개 변수 {#input-parameters}

* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.
