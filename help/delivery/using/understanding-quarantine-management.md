---
solution: Campaign Classic
product: campaign
title: 격리 관리 이해
description: 격리 관리 이해
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2799'
ht-degree: 14%

---


# 격리 관리 이해{#understanding-quarantine-management}

## 격리 기본 정보 {#about-quarantines}

Adobe Campaign은 격리된 주소 목록을 관리합니다. 주소가 격리된 수신자는 기본적으로 게재 분석 중에 제외되며 타겟팅되지 않습니다. 예를 들어, 사서함이 가득 찼거나 주소가 없는 경우 전자 메일 주소를 격리할 수 있습니다. 어떠한 경우에도 격리 절차는 아래에 설명된 특정 규칙을 준수합니다.

>[!NOTE]
>
>이 섹션은 온라인 채널에 적용됩니다.이메일, SMS, 푸시 알림

### 격리를 통한 게재 최적화 {#optimizing-your-delivery-through-quarantines}

이메일 주소나 전화번호가 격리된 프로필은 메시지를 준비하는 동안 자동으로 제외됩니다([게재에 대해 격리된 주소 확인](#identifying-quarantined-addresses-for-a-delivery) 참조). 이를 통해 게재 속도를 높일 수 있습니다. 오류율은 게재 속도에 상당한 영향을 미치기 때문입니다.

일부 인터넷 액세스 제공 업체는 잘못된 주소의 비율이 너무 높은 경우 이메일을 자동으로 스팸으로 간주합니다. 따라서 격리 기능을 사용하면 이러한 제공자가에 추가하는 것을 차단 목록 방지할 수 있습니다.

또한 격리를 통해 잘못된 전화번호를 게재에서 제외하면 SMS를 보내는 비용을 줄이는 데 도움이 됩니다. 게재 보안 향상 및 최적화 모범 사례를 더 알아보려면 [이 페이지](../../delivery/using/delivery-best-practices.md)를 참조하십시오 .

### 격리 대 차단 목록 {#quarantine-vs-denylist}

**격리**&#x200B;는 프로필 자체가 아니라 주소에만 적용됩니다. 즉, 두 프로필에 동일한 이메일 주소가 있는 경우 해당 주소가 격리되면 두 프로필 모두에 영향을 줍니다.

마찬가지로, 프로필의 이메일 주소가 격리 상태이더라도 프로필을 업데이트하여 새 주소를 입력하면 게재 작업 시 다시 타겟팅될 수 있습니다.

반면에 **차단 목록**&#x200B;에 있는 경우, 더 이상 프로필이 전달의 대상이 되지 않습니다(예: 구독 취소).

>[!NOTE]
>
>사용자가 SMS 전달에서 옵트아웃하기 위해 &quot;STOP&quot;과 같은 키워드를 사용하여 SMS 메시지에 댓글을 달면 이메일 옵트아웃 프로세스차단 목록과 같이 자신의 프로필이에 추가되지 않습니다. 프로파일 전화 번호는 격리되도록 보내져 사용자가 이메일 메시지를 계속 수신하게 됩니다.

## 격리된 주소 확인 {#identifying-quarantined-addresses}

특정 게재 또는 플랫폼 전체에 대해 격리된 주소를 나열할 수 있습니다.

### 게재에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-a-delivery}

배달 준비 단계 동안 격리된 주소가 배달 대시보드의 배달 로그에 나열됩니다([배달 로그 및 내역](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) 참조).

### 플랫폼 전체에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-the-entire-platform}

관리자는 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 노드의 전체 플랫폼에 대해 격리 시 주소를 나열할 수 있습니다.

>[!NOTE]
>
>이 메뉴에는 **이메일**, **SMS** 및 **푸시 알림** 채널에 대해 격리된 요소의 목록이 표시됩니다.

각 주소에 대해 다음 정보를 사용할 수 있습니다.

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>검역소의 수가 증가한 것은 데이터베이스의 &quot;마모&quot;와 관련된 정상적인 효과이다. 예를 들어 이메일 주소의 수명을 3년으로 간주하여 수신자의 테이블이 매년 50% 증가하면 격리의 증가는 다음과 같이 계산될 수 있습니다.
>
>1년말:(1*0.33)/(1+0.5)=22%.
두 번째 해가 끝나는 시점: ((1.22*0.33)+0.33)/(1.5+0.75)=32.5% 

### 배달 보고서에서 격리된 주소 식별 {#identifying-quarantined-addresses-in-delivery-reports}

다음 보고서에서는 격리 주소에 대한 정보를 제공합니다.

* 배달할 때마다 **[!UICONTROL Delivery summary]** 보고서에는 배달 대상의 격리 주소 수가 표시됩니다. 다음과 같이 표시됩니다.

   * 배달 분석 중에 격리된 주소 수,

   * 배달 작업 후 격리된 주소 수입니다.

* **[!UICONTROL Non-deliverables and bounces]** 보고서에는 격리 주소, 발생한 오류 유형 등에 대한 정보와 도메인별 실패 분류가 표시됩니다.

플랫폼(**[!UICONTROL Home page > Reports]**)의 모든 게재나 특정 게재에 대해 이 정보를 조회할 수 있습니다. 사용자 지정된 보고서를 만들고 표시할 정보를 선택할 수도 있습니다.

### 받는 사람 {#identifying-quarantined-addresses-for-a-recipient}에 대해 격리된 주소 식별

수신자의 이메일 주소 상태를 조회할 수 있습니다. 이렇게 하려면 수신자 프로필을 선택하고 **[!UICONTROL Deliveries]** 탭을 클릭합니다. 해당 수신자에 대한 모든 배달의 경우, 해당 주소가 실패했는지, 분석 중에 격리되었는지 등을 확인할 수 있습니다. 각 폴더에 대해 이메일 주소가 격리 상태인 수신자만 표시할 수 있습니다. 이렇게 하려면 **[!UICONTROL Quarantined email address]** 응용 프로그램 필터를 사용하십시오.

![](assets/tech_quarant_recipients_filter.png)

### 격리된 주소 {#removing-a-quarantined-address} 제거

필요한 경우 격리 목록에서 주소를 수동으로 제거할 수 있습니다. 이 외에, 특정 조건과 일치하는 주소는 **[!UICONTROL Database cleanup]** 워크플로우에 의해 격리 목록에서 자동으로 삭제됩니다.

격리 목록에서 주소를 수동으로 제거하려면 다음을 수행하십시오.

* **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 노드에서 상태를 **[!UICONTROL Valid]**&#x200B;으로 변경할 수 있습니다.

   ![](assets/tech_quarant_error_status.png)

* 상태를 **[!UICONTROL Allowlisted]**&#x200B;으로 변경할 수도 있습니다. 이 경우 주소는 격리 목록에 남아 있지만 오류가 발생하더라도 체계적으로 타깃팅됩니다.

다음 경우 주소가 격리 목록에서 자동으로 제거됩니다.

* **[!UICONTROL With errors]** 상태의 주소는 배달 성공 후 격리 목록에서 제거됩니다.
* 마지막 소프트 바운스가 10일 이전에 발생한 경우 **[!UICONTROL With errors]** 상태의 주소가 격리 목록에서 제거됩니다. 소프트 오류 관리에 대한 자세한 내용은 [이 섹션](#soft-error-management)을 참조하십시오.
* **[!UICONTROL Mailbox full]** 오류로 인한 **[!UICONTROL With errors]** 상태의 주소는 30일 후에 격리 목록에서 제거됩니다.

그러면 상태는 **[!UICONTROL Valid]**&#x200B;으로 변경됩니다.

>[!IMPORTANT]
**[!UICONTROL Quarantine]** 또는 **[!UICONTROL On denylist]** 상태의 주소가 있는 수신자는 이메일을 수신하더라도 제거되지 않습니다.

오류 수와 두 오류 사이의 기간을 수정할 수 있습니다. 이렇게 하려면 배포 마법사(**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)에서 해당 설정을 변경합니다. 배포 마법사에 대한 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md)을 참조하십시오.

## 주소를 격리하는 조건 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign은 배달 실패 유형 및 오류 메시지 자격 조건([바운스 메일 자격 조건](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) 참조) 및 [배달 실패 유형 및 이유](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)를 참조하십시오.

* **무시된 오류**: 오류가 무시된 경우 주소가 격리되지 않습니다.
* **하드 오류**: 해당 이메일 주소가 즉시 격리됩니다.
* **소프트 오류**: 소프트 오류의 경우 주소가 즉시 격리되지는 않지만, 오류 카운터가 증가합니다. 자세한 내용은 [소프트 오류 관리](#soft-error-management)를 참조하십시오.

사용자가 이메일을 스팸([피드백 루프](../../delivery/using/technical-recommendations.md#feedback-loop))으로 자격이 되는 경우, 메시지는 Adobe에서 관리하는 기술 사서함으로 자동 리디렉션됩니다. 그러면 사용자의 이메일 주소가 자동으로 격리되도록 전송됩니다.

격리된 주소 목록에서 **[!UICONTROL Error reason]** 필드는 선택한 주소를 격리된 이유를 나타냅니다. Adobe Campaign의 격리는 대소문자를 구분합니다. 이메일 주소를 소문자로 가져와야 이후에 다시 타겟팅되지 않습니다.

![](assets/tech_quarant_error_reasons.png)

### 소프트 오류 관리 {#soft-error-management}

하드 오류와 대조적으로, 소프트 오류는 즉시 격리된 주소를 전송하지 않고 오류 카운터를 증가시킵니다.

* 오류 카운터가 한도 임계값에 도달하면 주소가 격리됩니다.
* 기본 구성에서 오류 임계값은 5로 설정되며, 두 오류가 최소 24시간 간격으로 발생하면 유효한 오류 두 개로 취급됩니다. 다섯 번째 오류 발생 시 주소가 격리됩니다.
* 오류 카운터 임계값은 수정할 수 있습니다. 이에 대한 자세한 내용은 배달 임시 실패 후 [재시도](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)를 참조하십시오.

마지막 중요한 오류가 10일 이전에 발생한 경우 오류 카운터가 다시 초기화됩니다. 그런 다음 주소 상태가 **유효한**&#x200B;로 변경되고 **데이터베이스 정리** 작업 과정에 의해 격리 목록에서 삭제됩니다.

## 푸시 알림 검역서 {#push-notification-quarantines}

푸시 알림에 대한 격리 메커니즘은 전체적으로 일반 프로세스와 동일합니다. [검역정보](#about-quarantines)를 참조하십시오. 하지만 특정 오류는 푸시 알림에 대해 다르게 관리됩니다. 예를 들어 특정 소프트 오류의 경우 동일한 전달 내에서 재시도를 수행하지 않습니다. 푸시 알림에 대한 설명은 아래에 나와 있습니다. 재시도 메커니즘(재시도 횟수, 빈도)은 이메일과 같습니다.

격리된 항목은 장치 토큰입니다.

### iOS 격리 {#ios-quarantine}

**iOS용 - 이진 커넥터**

>[!NOTE]
Campaign 20.3 릴리스부터 iOS 레거시 바이너리 커넥터는 사용되지 않습니다. 이 커넥터를 사용하는 경우 그에 따라 구현을 조정해야 합니다. [자세히 알아보기](https://helpx.adobe.com/kr/campaign/kb/migrate-to-apns-http2.html)

각 알림에 대해 Adobe Campaign은 APNs 서버로부터 동기 및 비동기 오류를 수신합니다. 다음 동기 오류에 대해 Adobe Campaign은 소프트 오류를 생성합니다.

* 페이로드 길이 문제:재시도가 없습니다. 실패 이유는 **[!UICONTROL Unreachable]**&#x200B;입니다.
* 인증서 만료 문제:재시도가 없습니다. 실패 이유는 **[!UICONTROL Unreachable]**&#x200B;입니다.
* 배달 중 연결이 끊겼습니다.다시 시도했지만 실패 이유는 **[!UICONTROL Unreachable]**&#x200B;입니다.
* 서비스 구성 문제(잘못된 인증서, 잘못된 인증서 암호, 인증서 없음):재시도가 없습니다. 실패 이유는 **[!UICONTROL Unreachable]**&#x200B;입니다.

APNs 서버는 장치 토큰이 등록되지 않았음을 Adobe Campaign에 비동기적으로 알립니다(사용자가 모바일 응용 프로그램을 제거했을 때). **[!UICONTROL mobileAppOptOutMgt]** 작업 과정은 6시간마다 실행되어 APNs 피드백 서비스에 문의하여 **AppSubscriptionRcp** 표를 업데이트합니다. 비활성화된 모든 토큰의 경우 **비활성화됨** 필드가 **True**&#x200B;로 설정되고 해당 장치 토큰에 연결된 구독이 자동으로 향후 배달에서 제외됩니다.

**iOS용 - HTTP/V2 커넥터**

HTTP/V2 프로토콜을 사용하면 각 푸시 전달에 대한 직접적인 피드백과 상태를 확인할 수 있습니다. HTTP/V2 프로토콜 커넥터를 사용하는 경우, 피드백 서비스는 더 이상 **[!UICONTROL mobileAppOptOutMgt]** 워크플로우에서 호출되지 않습니다. 등록되지 않은 토큰은 iOS 이진 커넥터와 iOS HTTP/V2 커넥터 간에 다르게 처리됩니다. 모바일 응용 프로그램을 제거하거나 다시 설치한 경우 토큰은 등록되지 않은 것으로 간주됩니다.

동기적으로 APNs가 메시지에 대해 &quot;등록되지 않은&quot; 상태를 반환하면 대상 토큰은 즉시 격리됩니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>시나리오</strong><br /> </td> 
   <td> <strong>상태</strong><br /> </td> 
   <td> <strong>오류 메시지</strong><br /> </td> 
   <td> <strong>실패 유형</strong><br /> </td> 
   <td> <strong>실패 이유</strong><br /> </td> 
   <td> <strong>다시 시도</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 대상 장치가 켜짐<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 대상 장치가 꺼져 있음<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 사용자가 응용 프로그램<br /> 알림을 비활성화합니다. </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 메시지 생성/분석 단계 - 페이로드가 너무 큽니다<br />. </td> 
   <td> 실패<br /> </td> 
   <td> 페이로드가 너무 깁니다<br />. </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지 생성/분석 단계 - 예기치 않은 콘텐츠 형식 문제<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 오류<br />에 따른 다양한 오류 메시지 </td> 
   <td> 소프트<br /> </td> 
   <td> 정의되지 않음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 인증서 문제(암호, 손상 등) 및 APNs 문제에 대한 연결 테스트<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 오류<br />에 따른 다양한 오류 메시지 </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 전송 중 네트워크 연결이 끊김<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 연결 오류<br /> </td> 
   <td> 정의되지 않음<br /> </td> 
   <td> 연결할 수 없습니다.<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs 메시지 거부:등록 취소<br /> 사용자가 애플리케이션을 제거했거나 토큰이 만료되었습니다<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 등록되지 않은 <br /> </td> 
   <td> 하드<br /> </td> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs 메시지 거부:기타 모든 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 오류 메시지<br />에 오류 거부 원인이 표시됩니다. </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android 격리 {#android-quarantine}

**Android V1용**

각 알림에 대해 Adobe Campaign은 FCM 서버에서 바로 동기 오류를 수신합니다. Adobe 캠페인은 오류를 신속하게 처리하고 오류 심각도에 따라 하드 또는 소프트 오류를 생성하고 재시도를 수행할 수 있습니다.

* 페이로드 길이 초과, 연결 문제, 서비스 가용성 문제:재시도 수행, 소프트 오류, 실패 이유는 **[!UICONTROL Refused]**&#x200B;입니다.
* 장치 할당량 초과:재시도 없음, 소프트 오류, 실패 이유는 **[!UICONTROL Refused]**&#x200B;입니다.
* 유효하지 않거나 등록되지 않은 토큰, 예기치 않은 오류, 보낸 사람 계정 문제:재시도 없음, 하드 오류, 실패 이유는 **[!UICONTROL Refused]**&#x200B;입니다.

**[!UICONTROL mobileAppOptOutMgt]** 작업 과정은 6시간마다 실행되어 **AppSubscriptionRcp** 테이블을 업데이트합니다. 등록되지 않았거나 더 이상 유효하지 않다고 선언된 토큰의 경우 **Disabled** 필드가 **True**&#x200B;로 설정되고 해당 장치 토큰에 연결된 구독이 자동으로 이후 배달에서 제외됩니다.

배달 분석 중에 대상에서 제외된 모든 장치가 자동으로 **excludeLogAppSubRcp** 테이블에 추가됩니다.

>[!NOTE]
Baidu 커넥터를 사용하는 고객의 경우 다음과 같은 다양한 오류 유형이 있습니다.
* 배달 시작 시 연결 문제:실패 유형 **[!UICONTROL Undefined]**, 실패 이유 **[!UICONTROL Unreachable]**, 재시도가 수행됩니다.
* 배달 중 연결 손실:소프트 오류, 실패 이유 **[!UICONTROL Refused]**, 재시도가 수행됩니다.
* 전송 중 Baidu가 반환하는 동기 오류:하드 오류, 실패 이유 **[!UICONTROL Refused]**&#x200B;입니다. 다시 시도하지 않습니다.

Adobe Campaign은 10분마다 Baidu 서버에 연결하여 보낸 메시지의 상태를 검색하고 브로드로그를 업데이트합니다. 메시지가 전송됨으로 선언되면 브로드로그에 있는 메시지 상태가 **[!UICONTROL Received]**&#x200B;으로 설정됩니다. Baidu가 오류를 선언하면 상태는 **[!UICONTROL Failed]**&#x200B;으로 설정됩니다.

**Android V2용**

Android V2 격리 메커니즘은 Android V1과 동일한 프로세스를 사용합니다. 구독 및 제외 업데이트에 대해서도 마찬가지입니다. 이에 대한 자세한 내용은 [Android V1](#android-quarantine) 섹션을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>시나리오</strong><br /> </td> 
   <td> <strong>상태</strong><br /> </td> 
   <td> <strong>오류 메시지</strong><br /> </td> 
   <td> <strong>실패 유형</strong><br /> </td> 
   <td> <strong>실패 이유</strong><br /> </td> 
   <td> <strong>다시 시도</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지 생성/분석 단계:사용자 지정 필드<br />에 사용된 키워드가 잘못되었습니다. </td> 
   <td> 실패<br /> </td> 
   <td> 다음 키워드를 사용할 수 없습니다.{1}<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지 생성/분석 단계:페이로드가 너무 큼<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 알림은 너무 무겁습니다.{1}비트(단, {2}만 인증됨<br />) </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 전송 중 네트워크 연결이 끊김<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 다음 주소에 대한 Firebase Cloud Messaging 서비스에서 응답이 없습니다.{1}<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없습니다.<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부:FCM 서버를 일시적으로 사용할 수 없습니다(예: 시간 초과).<br /> </td> 
   <td> 실패<br /> </td> 
   <td> Firebase 클라우드 메시지 서비스를 일시적으로 사용할 수 없습니다.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없습니다.<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부:보낸 사람 계정<br /> 인증 오류 </td> 
   <td> 실패<br /> </td> 
   <td> 개발자 계정을 식별하지 못했습니다. ID 및 암호<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부:장치 할당량이<br />을(를) 초과했습니다. </td> 
   <td> 실패<br /> </td> 
   <td> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부:잘못된 등록 /<br /> 등록되지 않음 </td> 
   <td> 실패<br /> </td> 
   <td> </td> 
   <td> 하드<br /> </td> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부:다른 모든 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> Firebase Cloud Messaging 서버에서 예기치 않은 오류 코드를 반환했습니다.{1} </td> 
   <td> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM 메시지 거부:잘못된 인수<br /> </td> 
   <td> 실패<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> 무시됨</td> 
   <td> 정의되지 않음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부:타사 인증 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부:보낸 사람 ID가 일치하지 않음<br /> </td> 
   <td> 실패<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 소프트</td>
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부:등록되지 않은 <br /> </td> 
   <td> 실패<br /> </td>
   <td> 미등록 </td> 
   <td> 하드</td> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부:내부<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 내부 </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부:사용할 수 없음<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 사용할 수 없음</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부:예기치 않은 오류 코드<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 예기치 않은 오류 코드</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
  <tr> 
   <td> 인증:연결 문제<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 인증 서버에 연결할 수 없습니다. </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:요청에 권한이 없는 클라이언트 또는 범위입니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:클라이언트가 이 방법을 사용하여 액세스 토큰을 검색할 권한이 없거나 클라이언트가 요청한 범위에 대해 인증되지 않았습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:액세스 거부됨<br /> </td> 
   <td> 실패<br /> </td>
   <td> access_denied</td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:유효하지 않은 이메일<br /> </td> 
   <td> 실패<br /> </td> 
   <td> invalid_grant </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:잘못된 JWT<br /> </td> 
   <td> 실패<br /> </td> 
   <td> invalid_grant </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:잘못된 JWT 서명<br /> </td> 
   <td> 실패<br /> </td> 
   <td> invalid_grant </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:잘못된 OAuth 범위 또는 ID 토큰 대상이 제공됨<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증:OAuth 클라이언트가 비활성화됨<br /> </td> 
   <td> 실패<br /> </td> 
   <td> disabled_client</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS 검역소 {#sms-quarantines}

**표준 커넥터의 경우**

SMS 메시지의 격리 메커니즘은 전 세계적으로 일반 프로세스와 동일합니다. [검역정보](#about-quarantines)를 참조하십시오. SMS에 대한 설명은 아래에 나와 있습니다.

>[!NOTE]
**[!UICONTROL Delivery log qualification]** 테이블은 **확장 일반 SMPP** 커넥터에 적용되지 않습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>시나리오</strong><br /> </td> 
   <td> <strong>상태</strong><br /> </td> 
   <td> <strong>오류 메시지</strong><br /> </td> 
   <td> <strong>실패 유형</strong><br /> </td> 
   <td> <strong>실패 이유</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 공급자로 전송됨<br /> </td> 
   <td> 보낸 날짜<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 모바일<br />에서 수신됨 </td> 
   <td> 수신됨<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 공급자<br />에서 반환된 오류 </td> 
   <td> 실패<br /> </td> 
   <td> 데이터를 받는 동안 오류 발생(SR 또는 MO)<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 MT 인식<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 송신 쿼리<br />에 대한 승인 프레임을 처리하는 동안 '{1}' 오류가 발생했습니다. </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> MT<br />을(를) 보내는 동안 오류가 발생했습니다. </td> 
   <td> 실패<br /> </td> 
   <td> 메시지 전송 중 오류 발생<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**확장 범용 SMPP 커넥터의 경우**

SMPP 프로토콜을 사용하여 SMS 메시지를 보낼 때 오류 관리는 다르게 처리됩니다. 확장 범용 SMPP 커넥터에 대한 자세한 내용은 [이 페이지](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)를 참조하십시오.

SMPP 커넥터는 정규 표현식(등록)을 사용하여 반환되는 SR(상태 보고서) 메시지의 데이터를 검색하여 내용을 필터링합니다. 그러면 이 데이터가 **[!UICONTROL Delivery log qualification]** 테이블에 있는 정보와 일치합니다(**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** 메뉴를 통해 제공).

새로운 유형의 오류가 검증되기 전에 실패 이유는 항상 기본적으로 **Redensed**&#x200B;로 설정됩니다.

>[!NOTE]
실패 유형 및 실패 원인은 이메일과 동일합니다. [배달 실패 유형 및 이유](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)를 참조하십시오.
배달 로그 자격 조건 표에서 적절한 오류 유형과 실패 이유를 설정하려면 공급자에게 상태 및 오류 코드 목록을 요청합니다.

생성된 메시지의 예:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 모든 오류 메시지는 **SR**&#x200B;으로 시작하여 SMS 오류 코드와 이메일 오류 코드를 구별합니다.
* 오류 메시지의 두 번째 부분(**일반**)은 SMS 외부 계정의 **[!UICONTROL SMSC implementation name]** 필드에 정의된 것과 같은 SMSC 구현의 이름을 나타냅니다. [이 페이지](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)를 참조하십시오.

   동일한 오류 코드는 각 공급자에 대해 다른 의미를 가질 수 있으므로 이 필드에서 오류 코드를 생성한 공급자를 알 수 있습니다. 그런 다음 관련 공급자의 설명서에서 오류를 찾을 수 있습니다.

* 오류 메시지의 세 번째 부분(**DELIVRD**)은 SMS 외부 계정에 정의된 상태 추출 규칙을 사용하여 SR에서 검색한 상태 코드에 해당합니다.

   이 정규식은 외부 계정의 **[!UICONTROL SMSC specificities]** 탭에 지정됩니다. [이 페이지](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)를 참조하십시오.

   ![](assets/tech_quarant_error_regex.png)

   기본적으로 regex는 **SMPP 3.4 사양**&#x200B;의 **부록 B** 섹션에 정의된 대로 **stat:** 필드를 추출합니다.

* 오류 메시지의 네 번째 부분(**000** 이 예제의 경우)은 SMS 외부 계정에 정의된 오류 코드 추출 규칙을 사용하여 SR에서 추출되는 오류 코드에 해당합니다.

   이 정규식은 외부 계정의 **[!UICONTROL SMSC specificities]** 탭에 지정됩니다. [이 페이지](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)를 참조하십시오.

   기본적으로 regex는 **SMPP 3.4 사양**&#x200B;의 **부록 B** 섹션에 정의된 대로 **err:** 필드를 추출합니다.

* 파이프 기호(|) 다음에 오는 모든 내용은 **[!UICONTROL Delivery log qualification]** 테이블의 **[!UICONTROL First text]** 열에만 표시됩니다. 메시지가 표준화된 후 이 컨텐츠는 항상 **#MESSAGE#**&#x200B;로 대체됩니다. 이 프로세스는 유사한 오류에 대해 여러 항목을 포함하지 않으며 이메일과 동일합니다. 자세한 내용은 [바운스 메일 자격 조건](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)을 참조하십시오.

확장 범용 SMPP 커넥터는 적절한 기본값을 찾기 위해 휴리스틱을 적용합니다.상태가 **DELIV**&#x200B;로 시작하는 경우 대부분의 공급자가 사용하는 일반적인 상태 **DELIVRD** 또는 **DELIVERED**&#x200B;과(와) 일치하기 때문에 성공한 것으로 간주됩니다. 다른 모든 상태는 심각한 실패로 이어진다.
