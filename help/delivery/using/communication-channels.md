---
product: campaign
title: 소통 채널
description: 여러 채널에서 개인화된 메시지를 보낼 수 있는 게재 정보를 만듭니다.
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 20%

---

# 소통 채널{#communication-channels}

![](../../assets/common.svg)

Adobe Campaign을 사용하면 이메일, SMS, LINE 메시지, 푸시 알림 및 DM을 포함한 크로스 채널 캠페인을 전송할 수 있으며, 다양한 전용 캠페인을 사용하여 효과를 측정할 수 있습니다 [보고서](../../reporting/using/delivery-reports.md). 이러한 메시지는 게재를 통해 디자인되고 전송되며 각 수신자에 대해 개인화할 수 있습니다.

핵심 기능에는 타기팅, 정의 및 메시지 개인화, 커뮤니케이션 실행 및 관련 운영 보고서가 포함됩니다. 기본 기능 액세스 포인트는 게재 마법사입니다. 이 액세스 포인트는 Adobe Campaign에서 다루는 다양한 기능으로 이어집니다.

>[!NOTE]
>
>Adobe Campaign은 게재 기능을 모니터링하고 이메일 전송을 최적화하는 도구 세트를 제공합니다. [이 섹션](about-deliverability.md)에서 자세히 알아봅니다.

게재를 준비하거나 워크플로우 프로세스에서 전송하여 게재 전송을 자동화할 수 있습니다. 워크플로우의 게재 유형 활동에 대한 자세한 내용은 [이 섹션](../../workflow/using/about-action-activities.md).

Adobe Campaign에서는 다음 게재 채널을 제공합니다.

1. **이메일 채널**: 이메일 게재를 사용하면 개인화된 이메일을 대상 모집단으로 보낼 수 있습니다. 을(를) 참조하십시오. [이메일 채널 기본 정보](about-email-channel.md).
1. **DM 채널**: DM 게재는 대상 모집단에서 데이터를 포함하는 추출 파일을 생성할 수 있습니다. 을(를) 참조하십시오. [DM 채널 기본 정보](about-direct-mail-channel.md).
1. **모바일 채널**: 모바일 채널의 게재를 사용하면 개인화된 SMS 또는 LINE 메시지를 대상 모집단으로 보낼 수 있습니다. 을(를) 참조하십시오. [SMS 채널](sms-channel.md).
1. **모바일 앱 채널**:모바일 앱 게재를 사용하면 iOS 및 Android 시스템에 알림을 전송할 수 있습니다. 자세한 내용은 [모바일 앱 채널](about-mobile-app-channel.md) 제2장.

   기타 채널은 [이 페이지](steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >사용 가능한 채널 수는 계약에 따라 다릅니다. 사용권 계약을 확인하십시오.

게재를 수행할 수 있습니다 **온라인** (이메일을 통해, 모바일 채널 및 푸시 알림 중 하나) 및 **오프라인** (DM 채널).

채널에 따라 게재 모드는 다음 중 하나일 수 있습니다.

* Adobe Campaign을 통한 직접 대량 게재(이메일 채널의 기본 모드).
* 게재 마법사에서 생성한 출력 파일을 제공하는 전문가 운영자를 통한 외부 게재(DM 채널의 기본 모드).

외부 계정은 **[!UICONTROL Administration > Platform > External accounts]** 노드 아래에 있어야 합니다. 이 구성은 전문가 사용자만 수행해야 합니다.

## 이메일 게재 {#email-deliveries}

다음 [이메일 채널](about-email-channel.md) 은 Adobe Campaign의 핵심 채널 중 하나이며, 특정 타겟에 개인화된 이메일을 예약하고 전송할 수 있습니다.

다음과 같은 유형의 이메일을 보낼 수 있습니다.

* 단일 전송 이메일: 정의된 타겟에게 한 번 보낼 수 있는 이메일. 일반적으로 한 번만 준비하고 전송되는 특정 컨텐츠(뉴스레터, 프로모션 이메일 등)를 홍보하는 데 사용됩니다.
* 반복 이메일: 캠페인에서 동일한 이메일을 정기적으로 보내고 각 전송과 보고서를 정기적으로 집계합니다. 동일한 이메일이 전송되지만 전송 날짜에 적합한 타겟을 기반으로 일반적으로 다른 타겟으로 전송됩니다. 일반적인 예로는 생일 이메일이 있습니다. 자세한 내용은 [반복 게재](../../workflow/using/recurring-delivery.md).
* 트랜잭션 이메일: 고객의 행동을 기반으로 트리거되는 단일 이메일. 을(를) 참조하십시오. [트랜잭션 메시지](../../message-center/using/about-transactional-messaging.md).

게재 사용량 및 권장 사항에 대해 알아보려면 Campaign을 참조하십시오 [게재 모범 사례](delivery-best-practices.md).

게재 유형에 대한 자세한 내용은 [이 섹션](#types-of-deliveries).

## 모바일 게재 {#mobile-deliveries}

Adobe Campaign을 통해 [SMS](sms-channel.md) 및 [라인](line-channel.md) 모바일의 메시지.

SMS 메시지의 경우 텍스트 형식으로만 메시지를 만들고, 수정하고, 개인화할 수 있습니다. SMS 메시지를 보내기 전에 미리 볼 수도 있습니다.

LINE 메시지의 경우 텍스트 또는 이미지 및 링크를 전송할 수 있습니다.

필요한 휴대폰에 SMS 또는 LINE 메시지를 전달하려면 다음을 수행하십시오.

* 에 구성된 외부 계정 **[!UICONTROL Mobile (SMS)]** 채널 또는 **[!UICONTROL LINE]** 채널.
* 이 외부 계정에 올바르게 연결된 SMS 또는 LINE 게재 템플릿입니다.

## 푸시 알림 {#push-notifications}

Adobe Campaign을 통해 개인화 및 세그먼트화된 파일을 보낼 수 있습니다 [푸시 알림](about-mobile-app-channel.md) 전용 앱을 통해 iOS 및 Android 모바일 장치에서 사용할 수 있습니다. 구성 및 통합 단계를 수행하면 iOS 및 Android 게재를 만들고 전송할 수 있습니다. 이미지나 비디오로 풍부한 알림을 디자인할 수도 있습니다.

## DM {#direct-mail}

[DM은 다이렉트 메일 공급자가 요구하는 파일을 개인화하고 생성할 수 있는 오프라인 채널입니다. ](about-direct-mail-channel.md) DM을 통해 고객 여정의 온오프라인 채널을 혼합하여 운영할 수 있습니다.

온라인 채널을 통해 메시지(이메일, SMS, 모바일 앱 게재 등)를 만들고 Adobe Campaign에서 바로 대상자에게 보낼 수 있습니다. 하지만 오프라인 채널에서는 다릅니다. Adobe Campaign은 DM 게재 준비 시 타겟팅 프로필과 선택한 연락처 정보(예를 들면 우편 주소)가 있는 파일을 생성합니다. 그러면 이 파일을 DM 공급자에게 보내어 실제 전송을 처리하도록 할 수 있습니다.

## 기타 채널 {#other-channels}

Adobe Campaign에서는 외부 게재를 만드는 데 사용되는 전화 배달 템플릿을 제공합니다. 이 채널을 사용하면 출력 파일을 처리하는 전용 방법론을 설정할 수 있습니다. 구성 단계는 과 동일합니다 [DM 채널](about-direct-mail-channel.md).

>[!NOTE]
>
>전화 채널은 즉시 사용할 수 없습니다. 구현하려면 Adobe 컨설팅 또는 Adobe 파트너가 참여해야 합니다. 자세한 내용은 Adobe 담당자에게 문의하십시오.

또한 &#39;기타&#39; 유형 게재는 프로세스를 실행하지 않는 특정 기술 템플릿을 사용합니다. 이렇게 하면 Adobe Campaign 플랫폼 외부에서 실행된 마케팅 작업을 관리할 수 있습니다.

이 채널에는 특정 메커니즘이 없습니다. Adobe Campaign에서 사용할 수 있는 다른 통신 채널과 마찬가지로 자체 외부 계정 라우팅 옵션, 게재 템플릿 유형 및 캠페인 워크플로우 활동이 있는 일반 채널입니다.

이 채널은 Adobe Campaign 이외의 도구에서 수행한 캠페인 타겟의 추적을 유지할 게재를 정의하는 등의 수사적 목적으로만 설계되었습니다.

## 게재 유형{#types-of-deliveries}

Campaign에는 다음 세 가지 유형의 게재 개체가 있습니다.

### 단일 게재 {#single-delivery}

A **게재** 는 한 번 실행되는 독립 실행형 게재 개체입니다. 복제되고 다시 준비할 수 있지만 최종 상태(취소, 중지, 완료)에 있는 한 재사용할 수 없습니다.

게재 목록 또는 워크플로우를 통해 게재를 만들 수 있습니다. [배달](../../workflow/using/delivery.md) 활동.

또한 워크플로우는 사용할 채널 유형에 따라 특정 게재 활동을 제공합니다. 이러한 활동에 대한 자세한 내용은 [이 섹션](../../workflow/using/cross-channel-deliveries.md).

### 반복 게재 {#recurring-delivery}

A **반복 게재** 활동을 실행할 때마다 새 게재를 만들 수 있습니다. 따라서 반복되는 작업에 대해 새 게재를 만들 필요가 없습니다.

예를 들어, 한 달에 한 번 이러한 유형의 활동을 실행하면 1년 후 12개의 게재가 제공됩니다.

반복 게재는 을 통해 워크플로우 내에 만들어집니다 [반복 게재 활동](../../workflow/using/recurring-delivery.md). 사용 중인 이 활동의 예는 이 섹션에 나와 있습니다. [타겟팅 워크플로우에서 반복 게재 만들기](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### 지속적인 게재 {#continuous-delivery}

A **연속 게재** 을 사용하면 기존 게재에 새 수신자를 추가할 수 있으므로 수신자가 실행될 때마다 새 게재를 만들 필요가 없습니다.

게재의 정보가 변경되면(콘텐츠, 이름 등) 게재 실행 시 새 게재 개체가 만들어집니다. 변경된 정보가 없으면 동일한 게재 개체를 다시 사용하고 게재 및 추적 로그가 동일한 개체에 추가됩니다.

예를 들어, 한 달에 한 번 이러한 유형의 활동을 실행하면 1년 후 단일 게재로 끝납니다(게재를 변경하지 않은 경우).

연속 게재는 을 통해 워크플로우 내에서 만들어집니다 [연속 게재 활동](../../workflow/using/continuous-delivery.md).
