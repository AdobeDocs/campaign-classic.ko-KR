---
title: 소통 채널
seo-title: 소통 채널
description: 소통 채널
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b14f5ecd2b06ed9f4cb49d8779b9f94ea4bcdddc
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 11%

---


# 소통 채널{#communication-channels}

Adobe Campaign을 사용하면 이메일, SMS, LINE 메시지, 푸시 알림 및 다이렉트 메일을 비롯한 크로스 채널 캠페인을 전송할 수 있으며 다양한 전용 [보고서를 사용하여 캠페인 효과를 측정할 수 있습니다](../../reporting/using/delivery-reports.md). 이러한 메시지는 배달할 때 디자인되고 전송되며 각 수신자에 대해 개인화할 수 있습니다.

핵심 기능에는 타깃팅, 정의 및 메시지 개인화, 커뮤니케이션 실행 및 관련 운영 보고서가 포함됩니다. 기본 기능 액세스 포인트는 배달 마법사로, 이 액세스 포인트는 Adobe Campaign의 다양한 기능으로 이어집니다.

>[!NOTE]
>
>Adobe Campaign은 전달 능력을 모니터링하고 이메일 전송을 최적화할 수 있는 다양한 툴을 제공합니다. 자세한 내용은 전달 [능력 시작](../../delivery/using/deliverability-key-points.md) 및 [전달 능력 관리를](../../delivery/using/about-deliverability.md)참조하십시오.

배달 전송을 준비하고 워크플로우 과정에서 전송하여 배달 전송을 자동화할 수 있습니다. 워크플로우의 배달 유형 활동에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../workflow/using/about-action-activities.md).

Adobe Campaign은 다음과 같은 배달 채널을 제공합니다.

1. **이메일 채널**:이메일 전달을 사용하면 개인화된 이메일을 타겟 모집단으로 보낼 수 있습니다. 이메일 채널 [정보를 참조하십시오](../../delivery/using/about-email-channel.md).
1. **DM 채널**:직접 메일 배달에서는 대상 모집단에서 데이터가 포함된 추출 파일을 생성할 수 있습니다. DM 채널 [정보를 참조하십시오](../../delivery/using/about-direct-mail-channel.md).
1. **모바일 채널**:모바일 채널을 통해 전달하면 개인화된 SMS 또는 LINE 메시지를 타겟 모집단으로 보낼 수 있습니다. SMS [채널을 참조하십시오](../../delivery/using/sms-channel.md).
1. **모바일 애플리케이션 채널**:모바일 앱 게재를 사용하면 iOS 및 Android 시스템에 알림을 전송할 수 있습니다. 모바일 앱 [채널](../../delivery/using/about-mobile-app-channel.md) 장을 참조하십시오.

   다른 채널은 [이 페이지에 설명되어 있습니다](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >여러 채널을 사용하는 것은 패키지에 따라 다릅니다. 사용권 계약을 확인하십시오.

게재는 **온라인** (이메일, 모바일 채널 및 푸시 알림 중 하나)과 **오프라인** (DM 채널)으로 수행할 수 있습니다.

채널에 따라 전달 모드는 다음과 같습니다.

* Adobe Campaign을 통한 직접 대량 배달(이메일 채널의 기본 모드)
* 배달 마법사로 생성된 출력 파일(DM 채널의 기본 모드)을 제공하는 전문가 연산자를 통해 외부 배달입니다.

외부 계정은 노드를 통해 **[!UICONTROL Administration > Platform > External accounts]** 구성됩니다. 이 구성은 전문가 사용자만 수행해야 합니다.

## 이메일 게재 {#email-deliveries}

이메일 [채널은](../../delivery/using/about-email-channel.md) Adobe Campaign의 핵심 채널 중 하나로, 개인화된 이메일을 특정 타겟으로 예약 및 전송할 수 있습니다.

다음과 같은 다양한 유형의 이메일을 보낼 수 있습니다.

* 단일 전송 이메일:정의된 타겟으로 한 번 보낼 수 있는 이메일 일반적으로 특정 컨텐츠를 홍보하는 데 사용됩니다. 이 컨텐츠는 한 번만 준비되고 발송됩니다(뉴스레터, 홍보 이메일 등).
* 반복 이메일:캠페인에서 동일한 이메일을 정기적으로 보내고 각 전송과 보고서를 정기적으로 집계합니다. 동일한 이메일이 전송되지만, 일반적으로 전송 날짜에 적합한 타겟을 기준으로 다른 타겟으로 전송됩니다. 일반적인 예는 생일 이메일입니다. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* 트랜잭션 이메일:고객의 행동에 따라 트리거되는 이메일 트랜잭션 메시지 [를 참조하십시오](../../message-center/using/about-transactional-messaging.md).

배달 사용 및 권장 사항에 대해 알아보려면 캠페인 [배달 우수 사례를 참조하십시오](../../delivery/using/delivery-best-practices.md).

다른 유형의 게재에 대한 자세한 내용은 [이 섹션을 참조하십시오](#types-of-deliveries).

## 모바일 전달 {#mobile-deliveries}

Adobe Campaign을 사용하면 모바일에 [SMS](../../delivery/using/sms-channel.md) 와 [LINE](../../delivery/using/line-channel.md) 메시지를 전달할 수 있습니다.

SMS 메시지의 경우 텍스트 형식으로만 메시지를 만들고 수정하고 개인화할 수 있습니다. SMS 메시지를 보내기 전에 미리 볼 수도 있습니다.

LINE 메시지의 경우 텍스트 또는 이미지와 링크를 보낼 수 있습니다.

필요한 휴대폰에 SMS 또는 LINE 메시지를 전달하려면

* 채널 또는 채널에 구성된 **[!UICONTROL Mobile (SMS)]** 외부 **[!UICONTROL LINE]** 계정
* 이 외부 계정에 올바르게 연결된 SMS 또는 LINE 배달 템플릿입니다.

## 푸시 알림 {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](../../delivery/using/about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. 구성 및 통합 단계가 수행되면 iOS 및 Android 배달을 만들고 전송할 수 있습니다. 이미지나 비디오가 포함된 풍부한 알림을 디자인할 수도 있습니다.

## DM {#direct-mail}

[DM은 다이렉트 메일 공급자가 요구하는 파일을 개인화하고 생성할 수 있는 오프라인 채널입니다. ](../../delivery/using/about-direct-mail-channel.md) DM을 통해 고객 여정의 온오프라인 채널을 혼합하여 운영할 수 있습니다.

온라인 채널을 통해 메시지(이메일, SMS, 모바일 앱 게재 등)를 만들고 Adobe Campaign에서 바로 대상자에게 보낼 수 있습니다. 하지만 오프라인 채널에서는 다릅니다. Adobe Campaign은 DM 게재 준비 시 타겟팅 프로필과 선택한 연락처 정보(예를 들면 우편 주소)가 있는 파일을 생성합니다. 그러면 이 파일을 DM 공급자에게 보내어 실제 전송을 처리하도록 할 수 있습니다.

## 기타 채널 {#other-channels}

Adobe Campaign은 외부 배달을 만드는 데 사용되는 에이전시 또는 전화 배달 템플릿을 제공합니다. 이러한 채널을 사용하면 출력 파일을 처리할 전용 방법을 설정할 수 있습니다. 구성 단계는 [DM 채널과 동일합니다](../../delivery/using/about-direct-mail-channel.md).

또한 &#39;기타&#39; 유형 배달은 프로세스를 실행하지 않는 특정 기술 템플릿을 사용합니다.이를 통해 Adobe Campaign 플랫폼 외부에서 실행되는 마케팅 작업을 관리할 수 있습니다.

이 채널에는 특정 메커니즘이 없습니다. 고유한 외부 계정 라우팅 옵션, 배달 템플릿 유형 및 캠페인 워크플로우 활동이 있는 일반 채널이며 Adobe Campaign에서 제공되는 기타 커뮤니케이션 채널과 같습니다.

이 채널은 설명 목적으로만 설계되었습니다. 예를 들어 Adobe Campaign 이외의 도구에서 수행한 캠페인 대상의 추적을 유지하려는 게재를 정의합니다.

## 배달 유형{#types-of-deliveries}

Campaign에는 세 가지 유형의 배달 개체가 있습니다.

### 단일 전달 {#single-delivery}

배달 **은** 한 번 실행되는 독립 실행형 배달 개체입니다. 복제하거나 다시 준비할 수 있지만 최종 상태(취소, 중단, 완료)인 경우 재사용할 수 없습니다.

게재는 배달 목록 또는 배달 활동을 통해 워크플로우 내에서 만들 수 [있습니다](../../workflow/using/delivery.md) .

또한 워크플로우는 사용할 채널 유형에 따라 특정 배달 활동을 제공합니다. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### 반복 전달 {#recurring-delivery}

반복 **배달을 사용하면** 활동이 실행될 때마다 새 배달을 만들 수 있습니다. 따라서 반복되는 작업에 대해 새 배달을 만들지 않아도 됩니다.

예를 들어, 이 유형의 활동을 한 달에 한 번 실행하면 1년 후에 12개의 배달로 끝납니다.

반복 배달은 반복 배달 활동을 통해 워크플로우 내에서 [생성됩니다](../../workflow/using/recurring-delivery.md). 사용 중인 이 활동의 예는 다음 섹션에 나와 있습니다. [타깃팅 워크플로우에서 반복적인 배달 만들기](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### 지속적인 전달 {#continuous-delivery}

연속 배달 **** 기능을 사용하면 기존 전달에 새 받는 사람을 추가할 수 있으므로 매번 새 배달을 만들지 않아도 됩니다.

배달 내의 정보가 변경되면(컨텐츠, 이름 등) 배달 실행 시 새 배달 개체가 만들어집니다. 정보를 변경하지 않은 경우 동일한 배달 개체를 다시 사용하고 동일한 개체에 전달 및 추적 로그가 추가됩니다.

예를 들어, 한 달에 한 번 이 유형의 활동을 실행하면 1년 후 단일 배달로 끝납니다(전달을 변경하지 않은 경우).

연속 배달은 [연속 배달 활동을 통해 워크플로우 내에서 만들어집니다](../../workflow/using/continuous-delivery.md).
