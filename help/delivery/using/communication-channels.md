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
source-git-commit: c1f7ff6a281c2830ac23ad995b750dc09ade5e92
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 1%

---


# 소통 채널{#communication-channels}

Adobe Campaign을 통해 이메일, SMS, LINE 메시지, 푸시 알림 및 다이렉트 메일을 비롯한 크로스 채널 캠페인을 전송할 수 있으며 다양한 전용 [보고서를 사용하여 캠페인 효과를 측정할 수 있습니다](../../reporting/using/delivery-reports.md). 이러한 메시지는 배달할 때 디자인되고 전송되며 각 수신자에 대해 개인화할 수 있습니다.

핵심 기능에는 타깃팅, 정의 및 메시지 개인화, 커뮤니케이션 실행 및 관련 운영 보고서가 포함됩니다. 기본 기능 액세스 포인트는 배달 마법사로, 이 액세스 포인트는 Adobe Campaign에서 다루는 여러 기능으로 이어집니다.

>[!NOTE]
>
>Adobe Campaign은 전달 능력을 모니터링하고 이메일 전송을 최적화하는 일련의 툴을 제공합니다. 자세한 내용은 전달 [능력 시작](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 및 [전달 능력 관리를](../../delivery/using/about-deliverability.md)참조하십시오.

배달 전송을 준비하고 워크플로우 과정에서 전송하여 배달 전송을 자동화할 수 있습니다. 워크플로우의 배달 유형 활동에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../workflow/using/about-action-activities.md).

Adobe Campaign은 다음 배달 채널을 제공합니다.

1. **이메일 채널**: 이메일 전달을 사용하면 개인화된 이메일을 타겟 모집단으로 보낼 수 있습니다. 이메일 채널 [정보를 참조하십시오](../../delivery/using/about-email-channel.md).
1. **DM 채널**: 직접 메일 배달에서는 대상 모집단에서 데이터가 포함된 추출 파일을 생성할 수 있습니다. DM 채널 [정보를 참조하십시오](../../delivery/using/about-direct-mail-channel.md).
1. **모바일 채널**: 모바일 채널을 통해 전달하면 개인화된 SMS 또는 LINE 메시지를 타겟 모집단으로 보낼 수 있습니다. SMS [채널을 참조하십시오](../../delivery/using/sms-channel.md).
1. **모바일 애플리케이션 채널**: 모바일 앱 게재를 사용하면 iOS 및 Android 시스템에 알림을 전송할 수 있습니다. 모바일 앱 [채널](../../delivery/using/about-mobile-app-channel.md) 장을 참조하십시오.

   다른 채널은 [이 페이지에 설명되어 있습니다](../../delivery/using/communication-channels.md#other-channels).

   >[!NOTE]
   >
   >여러 채널을 사용하는 것은 패키지에 따라 다릅니다. 사용권 계약을 확인하십시오.

게재는 **온라인** (이메일, 모바일 채널 및 푸시 알림 중 하나)과 **오프라인** (DM 채널)으로 수행할 수 있습니다.

채널에 따라 전달 모드는 다음과 같습니다.

* Adobe Campaign을 통한 직접 대량 배달(이메일 채널의 기본 모드)
* 배달 마법사로 생성된 출력 파일(DM 채널의 기본 모드)을 제공하는 전문가 연산자를 통해 외부 배달입니다.

외부 계정은 노드를 통해 **[!UICONTROL Administration > Platform > External accounts]** 구성됩니다. 이 구성은 전문가 사용자만 수행해야 합니다.

## 이메일 배달 {#email-deliveries}

이메일 [채널은](../../delivery/using/about-email-channel.md) Adobe Campaign의 핵심 채널 중 하나로, 개인화된 이메일을 예약하고 특정 타겟으로 보낼 수 있습니다.

다음과 같은 다양한 유형의 이메일을 보낼 수 있습니다.

* 단일 전송 이메일: 정의된 타겟으로 한 번 보낼 수 있는 이메일 일반적으로 특정 컨텐츠를 홍보하는 데 사용됩니다. 이 컨텐츠는 한 번만 준비되고 발송됩니다(뉴스레터, 홍보 이메일 등).
* 반복 이메일: 캠페인에서 동일한 이메일을 정기적으로 보내고 각 전송과 보고서를 정기적으로 집계합니다. 동일한 이메일이 전송되지만, 일반적으로 전송 날짜에 적합한 타겟을 기준으로 다른 타겟으로 전송됩니다. 일반적인 예는 생일 이메일입니다. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* 트랜잭션 이메일: 고객의 행동에 따라 트리거되는 이메일 트랜잭션 메시지 [를 참조하십시오](../../message-center/using/about-transactional-messaging.md).

배달 사용 및 권장 사항에 대해 알아보려면 캠페인 [배달 우수 사례를 참조하십시오](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html).

다른 유형의 게재에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../delivery/using/types-of-deliveries.md).

## 모바일 전달 {#mobile-deliveries}

Adobe Campaign을 사용하면 모바일에 [SMS](../../delivery/using/sms-channel.md) 와 [LINE](../../delivery/using/line-channel.md) 메시지를 전달할 수 있습니다.

SMS 메시지의 경우 텍스트 형식으로만 메시지를 만들고 수정하고 개인화할 수 있습니다. SMS 메시지를 보내기 전에 미리 볼 수도 있습니다.

LINE 메시지의 경우 텍스트 또는 이미지와 링크를 보낼 수 있습니다.

필요한 휴대폰에 SMS 또는 LINE 메시지를 전달하려면

* 채널 또는 채널에 구성된 **[!UICONTROL Mobile (SMS)]** 외부 **[!UICONTROL LINE]** 계정
* 이 외부 계정에 올바르게 연결된 SMS 또는 LINE 배달 템플릿입니다.

## 푸시 알림 {#push-notifications}

Adobe Campaign을 사용하면 전용 앱을 통해 iOS 및 Android 모바일 디바이스에서 개인화된 [푸시 알림을](../../delivery/using/about-mobile-app-channel.md) 전송할 수 있습니다. 구성 및 통합 단계가 수행되면 iOS 및 Android 배달을 만들고 전송할 수 있습니다. 이미지나 비디오가 포함된 풍부한 알림을 디자인할 수도 있습니다.

## DM {#direct-mail}

[DM(Direct Mail](../../delivery/using/about-direct-mail-channel.md) )은 DM 제공업체가 요구하는 파일을 개인화하고 생성할 수 있는 오프라인 채널입니다. 또한 고객 여정의 온라인 및 오프라인 채널을 혼합하여 운영할 수 있습니다.

온라인 채널을 통해 메시지(이메일, SMS, 모바일 앱 전달 등)를 만들 수 있습니다 또한 Adobe Campaign에서 바로 고객에게 전달할 수 있습니다. 오프라인 채널에서는 다릅니다. 직접 메일 배달을 준비할 때 Adobe Campaign은 모든 대상 프로필 및 선택한 연락처 정보(예: 우편 주소)를 포함하는 파일을 생성합니다. 그러면 이 파일을 다이렉트 메일 제공업체에 보낼 수 있으며 이 제공업체는 실제 전송을 처리합니다.

## 기타 채널 {#other-channels}

Adobe Campaign은 외부 전달을 만드는 데 사용되는 에이전시 또는 전화 배달 템플릿을 제공합니다. 이러한 채널을 사용하면 출력 파일을 처리할 전용 방법을 설정할 수 있습니다. 구성 단계는 [DM 채널과 동일합니다](../../delivery/using/about-direct-mail-channel.md).

또한 &#39;기타&#39; 유형 배달은 프로세스를 실행하지 않는 특정 기술 템플릿을 사용합니다. 따라서 Adobe Campaign 플랫폼 외부에서 실행되는 마케팅 작업을 관리할 수 있습니다.

이 채널에는 특정 메커니즘이 없습니다. Adobe Campaign에서 사용할 수 있는 다른 통신 채널과 마찬가지로 자체 외부 계정 라우팅 옵션, 배달 템플릿 유형 및 캠페인 워크플로우 활동이 있는 일반 채널입니다.

이 채널은 Adobe Campaign 이외의 도구에서 수행한 캠페인 타겟의 추적을 유지하려는 전달을 정의하는 등의 수사적 목적으로만 설계되었습니다.
