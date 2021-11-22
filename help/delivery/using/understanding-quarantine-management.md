---
product: campaign
title: 격리 관리 이해
description: 격리 관리 이해
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '2614'
ht-degree: 14%

---

# 격리 관리 이해{#understanding-quarantine-management}

![](../../assets/common.svg)

## 격리 기본 정보 {#about-quarantines}

Adobe Campaign은 격리된 주소 목록을 관리합니다. 주소가 격리된 수신자는 기본적으로 게재 분석 중에 제외되며 타겟팅되지 않습니다. 예를 들어, 사서함이 가득 찼거나 주소가 없는 경우 전자 메일 주소를 격리할 수 있습니다. 어떤 경우든, 격리 절차는 아래에서 설명하는 특정한 규칙을 준수합니다.

>[!NOTE]
>
>이 섹션은 온라인 채널에 적용됩니다. 이메일, SMS, 푸시 알림

### 격리를 통한 게재 최적화 {#optimizing-your-delivery-through-quarantines}

이메일 주소나 전화번호가 격리된 프로필은 메시지를 준비하는 동안 자동으로 제외됩니다([게재에 대해 격리된 주소 확인](#identifying-quarantined-addresses-for-a-delivery) 참조). 이를 통해 게재 속도를 높일 수 있습니다. 오류율은 게재 속도에 상당한 영향을 미치기 때문입니다.

일부 인터넷 액세스 제공 업체는 잘못된 주소의 비율이 너무 높은 경우 이메일을 자동으로 스팸으로 간주합니다. 따라서 격리 를 사용하면 이러한 제공 업체에 의해 차단 목록에 추가되지 않습니다.

또한 격리를 통해 잘못된 전화번호를 게재에서 제외하면 SMS를 보내는 비용을 줄이는 데 도움이 됩니다. 게재 보안 향상 및 최적화 모범 사례를 더 알아보려면 [이 페이지](delivery-best-practices.md)를 참조하십시오 .

### 격리와 차단 목록 {#quarantine-vs-denylist}

**격리**&#x200B;는 프로필 자체가 아니라 주소에만 적용됩니다. 즉, 두 프로필에 동일한 이메일 주소가 있는 경우 해당 주소가 격리되면 두 프로필 모두에 영향을 줍니다.

마찬가지로, 프로필의 이메일 주소가 격리 상태이더라도 프로필을 업데이트하여 새 주소를 입력하면 게재 작업 시 다시 타겟팅될 수 있습니다.

설정 **차단 목록**&#x200B;반면 은(는) 더 이상 프로필이 더 이상 게재의 타겟이 되지 않습니다. 예를 들어 구독 취소(옵트아웃) 이후와 같은 경우가 있습니다.

>[!NOTE]
>
>사용자가 SMS 게재에서 옵트아웃하기 위해 SMS 메시지에 &quot;STOP&quot; 등의 키워드로 답장하는 경우, 이메일 옵트아웃 프로세스에서처럼 차단 목록 프로필에 추가되지 않습니다. 프로필의 전화번호는 격리에 전송되므로 사용자는 계속해서 이메일 메시지를 수신하게 됩니다.

## 격리된 주소 확인 {#identifying-quarantined-addresses}

특정 게재 또는 플랫폼 전체에 대해 격리된 주소를 나열할 수 있습니다.

### 게재에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-a-delivery}

특정 게재에 대해 격리된 주소 목록은 게재 준비 단계 중 게재 대시보드의 게재 로그에서 확인할 수 있습니다(참조) [게재 로그 및 내역](delivery-dashboard.md#delivery-logs-and-history)).

### 플랫폼 전체에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-the-entire-platform}

관리자는 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 노드 아래에 있어야 합니다.

>[!NOTE]
>
>이 메뉴에는 **이메일**, **SMS** 및 **푸시 알림** 채널에 대해 격리된 요소의 목록이 표시됩니다.

각 주소에 대해 다음 정보를 사용할 수 있습니다.

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>격리 수의 증가는 데이터베이스의 &quot;마모&quot;와 관련된 정상적인 현상입니다. 예를 들어 이메일 주소의 수명을 3년으로 보고 수신자 표가 매년 50%씩 증가할 경우, 격리 증가는 다음과 같이 계산할 수 있습니다.
>
>1년말: (1*0.33)/(1+0.5)=22%.
두 번째 해가 끝나는 시점: ((1.22*0.33)+0.33)/(1.5+0.75)=32.5% 

### 게재 보고서에서 격리된 주소 확인 {#identifying-quarantined-addresses-in-delivery-reports}

다음 보고서는 격리 주소에 대한 정보를 제공합니다.

* 각 게재에 대해 **[!UICONTROL Delivery summary]** 보고서는 게재 대상의 격리된 주소 수를 보여줍니다. 다음과 같이 표시됩니다.

   * 게재 분석 중 격리된 주소 수,

   * 게재 작업 후 격리된 주소 수입니다.

* 다음 **[!UICONTROL Non-deliverables and bounces]** 보고서에는 격리된 주소, 발생한 오류 유형 등 및 도메인별 오류 분류에 대한 정보가 표시됩니다.

플랫폼의 모든 게재에 대해 이 정보를 조회할 수 있습니다(**[!UICONTROL Home page > Reports]**) 또는 특정 전달에 사용할 수 있습니다. 사용자 지정 보고서를 만들고 표시할 정보를 선택할 수도 있습니다.

### 수신자에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-a-recipient}

수신자의 이메일 주소 상태를 조회할 수 있습니다. 이렇게 하려면 수신자 프로필을 선택하고 **[!UICONTROL Deliveries]** 탭. 해당 수신자에 대한 모든 게재의 경우, 주소가 실패했는지, 분석 중 격리되었는지 등을 확인할 수 있습니다. 각 폴더에 대해 이메일 주소가 격리된 수신자만 표시할 수 있습니다. 이렇게 하려면 **[!UICONTROL Quarantined email address]** 애플리케이션 필터.

![](assets/tech_quarant_recipients_filter.png)

### 격리된 주소 제거 {#removing-a-quarantined-address}

필요한 경우 격리 목록에서 주소를 수동으로 제거할 수 있습니다. 또한 특정 조건과 일치하는 주소는 격리 목록에서 **[!UICONTROL Database cleanup]** 워크플로우.

격리 목록에서 주소를 수동으로 제거하려면

* 상태를 **[!UICONTROL Valid]** 에서 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 노드 아래에 있어야 합니다.

   ![](assets/tech_quarant_error_status.png)

* 상태를 **[!UICONTROL Allowlisted]**. 이 경우 주소는 격리 목록에 남아 있지만 오류가 발생하는 경우에도 체계적으로 타겟팅됩니다.

다음과 같은 경우 주소가 격리 목록에서 자동으로 제거됩니다.

* 의 주소 **[!UICONTROL With errors]** 게재가 성공하면 상태가 격리 목록에서 제거됩니다.
* 의 주소 **[!UICONTROL With errors]** 10일 이상 전에 마지막 소프트 바운스가 발생한 경우 상태가 격리 목록에서 제거됩니다. 소프트 오류 관리에 대한 자세한 내용은 [이 섹션](#soft-error-management).
* 의 주소 **[!UICONTROL With errors]** 다음으로 바운스된 상태 **[!UICONTROL Mailbox full]** 30일 후 격리 목록에서 오류가 제거됩니다.

그러면 상태가 **[!UICONTROL Valid]**.

>[!IMPORTANT]
주소가 있는 수신자 **[!UICONTROL Quarantine]** 또는 **[!UICONTROL On denylist]** 이메일이 수신되더라도 상태는 제거되지 않습니다.

오류 수와 두 오류 사이의 기간을 수정할 수 있습니다. 이렇게 하려면 배포 마법사(**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**). 배포 마법사에 대한 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md).

## 주소를 격리하는 조건 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign은 게재 실패 유형 및 오류 메시지 자격 중에 할당된 이유에 따라 격리를 관리합니다( 참조) [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification)) 및 [게재 실패 유형 및 이유](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

* **무시된 오류**: 오류가 무시된 경우 주소가 격리되지 않습니다.
* **하드 오류**: 해당 이메일 주소가 즉시 격리됩니다.
* **소프트 오류**: 소프트 오류의 경우 주소가 즉시 격리되지는 않지만, 오류 카운터가 증가합니다. 자세한 내용은 [소프트 오류 관리](#soft-error-management).

사용자가 이메일을 스팸 처리하면([피드백 루프](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)). 메시지는 Adobe에서 관리하는 기술 사서함으로 자동 리디렉션됩니다. 그러면 사용자의 이메일 주소가 자동으로 격리됩니다.

격리된 주소 목록에서 **[!UICONTROL Error reason]** 필드는 선택한 주소가 격리된 이유를 나타냅니다. Adobe Campaign의 격리는 대소문자를 구분합니다. 이메일 주소를 소문자로 가져와야 이후에 다시 타겟팅되지 않습니다.

![](assets/tech_quarant_error_reasons.png)

### 소프트 오류 관리 {#soft-error-management}

하드 오류와 달리 소프트 오류의 경우 주소가 즉시 격리되지는 않지만, 오류 카운터가 증가합니다.

* 오류 카운터가 제한 임계값에 도달하면 주소가 격리됩니다.
* 기본 구성에서 오류 임계값은 5로 설정되며, 두 오류가 최소 24시간 간격으로 발생하면 유효한 오류 두 개로 취급됩니다. 다섯 번째 오류 발생 시 주소가 격리됩니다.
* 오류 카운터 임계값은 수정할 수 있습니다. 자세한 내용은 [일시적 게재 실패 후 다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

10일 이전에 마지막으로 중요한 오류가 발생한 경우 오류 카운터는 다시 초기화됩니다. 그러면 주소 상태가 **유효한** 그리고 격리 목록에서 **데이터베이스 정리** 워크플로우.

## 푸시 알림 격리 {#push-notification-quarantines}

푸시 알림에 대한 격리 메커니즘은 전반적인 프로세스와 동일합니다. 자세한 내용은 [격리 기본 정보](#about-quarantines). 그러나 특정 오류는 푸시 알림에 대해 다르게 관리됩니다. 예를 들어 특정 소프트 오류의 경우 동일한 배달 내에서 다시 시도가 수행되지 않습니다. 푸시 알림의 특성은 아래에 나와 있습니다. 다시 시도 메커니즘(다시 시도 횟수, 빈도)은 이메일과 동일합니다.

격리된 항목은 장치 토큰입니다.

### iOS 격리 {#ios-quarantine}

HTTP/V2 프로토콜을 사용하면 각 푸시 게재에 대한 직접 피드백 및 상태를 사용할 수 있습니다. HTTP/V2 프로토콜 커넥터를 사용하는 경우 피드백 서비스는 더 이상 **[!UICONTROL mobileAppOptOutMgt]** 워크플로우. 모바일 애플리케이션을 제거하거나 다시 설치하면 토큰이 등록되지 않은 것으로 간주됩니다.

동기적으로 APNs가 메시지에 대해 &quot;등록되지 않음&quot; 상태를 반환하는 경우 대상 토큰이 즉시 격리됩니다.

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
   <td> 대상 장치 전원이 켜진 장치<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 대상 장치 전원이 꺼짐<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 사용자가 응용 프로그램에 대한 알림을 비활성화합니다<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 메시지 만들기/분석 단계 - 페이로드가 너무 큽니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 페이로드가 너무 깁니다.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지 작성/분석 단계 - 예기치 않은 콘텐츠 형식 문제<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 오류에 따른 다양한 오류 메시지<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 정의되지 않음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 인증서 문제(암호, 손상 등) APNs 문제에 대한 연결 테스트<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 오류에 따른 다양한 오류 메시지<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 보내는 동안 네트워크 연결이 끊어졌습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 연결 오류<br /> </td> 
   <td> 정의되지 않음<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs 메시지 거부: 등록 취소<br /> 사용자가 애플리케이션을 제거했거나 토큰이 만료되었습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 등록되지 않음<br /> </td> 
   <td> 하드<br /> </td> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs 메시지 거부: 기타 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 오류 거부 원인이 오류 메시지에 표시됩니다<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android 격리 {#android-quarantine}

**Android용 V1**

각 알림에 대해 Adobe Campaign은 FCM 서버로부터 직접 동기 오류를 수신합니다. Adobe 캠페인에서 이러한 이벤트를 즉시 처리하고 오류 심각도에 따라 하드 또는 소프트 오류를 생성하고 다시 시도할 수 있습니다.

* 페이로드 길이를 초과했습니다. 연결 문제, 서비스 가용성 문제: 다시 시도 수행, 소프트 오류, 실패 이유 **[!UICONTROL Refused]**.
* 장치 할당량을 초과했습니다. 다시 시도 없음, 소프트 오류, 실패 이유 **[!UICONTROL Refused]**.
* 잘못되었거나 등록되지 않은 토큰, 예기치 않은 오류, 보낸 사람 계정 문제: 다시 시도 없음, 하드 오류, 실패 이유 **[!UICONTROL Refused]**.

다음 **[!UICONTROL mobileAppOptOutMgt]** 워크플로우는 6시간마다 실행되어 업데이트됩니다 **AppSubscriptionRcp** 테이블. 등록되지 않았거나 더 이상 유효하지 않은 것으로 선언된 토큰의 경우 필드가 **비활성화됨** 가 로 설정되어 있습니다. **True** 해당 장치 토큰에 연결된 구독은 향후 게재에서 자동으로 제외됩니다.

게재 분석 중에 대상에서 제외된 모든 장치가 자동으로 **excludeLogAppSubRcp** 테이블.

>[!NOTE]
Baidu 커넥터를 사용하는 고객의 경우 다음과 같은 다양한 오류 유형이 있습니다.
* 게재 시작 시 연결 문제: 실패 유형 **[!UICONTROL Undefined]**, 실패 이유 **[!UICONTROL Unreachable]**, 다시 시도됩니다.
* 게재 중 연결이 끊어졌습니다. 소프트 오류, 실패 이유 **[!UICONTROL Refused]**, 다시 시도됩니다.
* 전송 중에 Baidu에서 동기 오류가 반환되었습니다. 하드 오류, 실패 이유 **[!UICONTROL Refused]**&#x200B;를 재시도하지 않습니다.
Adobe Campaign은 Baidu 서버에 10분마다 연락하여 보낸 메시지의 상태를 검색하고 브로드로그를 업데이트합니다. 메시지가 전송됨으로 선언되면 브로드로그에 있는 메시지의 상태가 **[!UICONTROL Received]**. Baidu가 오류를 선언하면 상태는 로 설정됩니다. **[!UICONTROL Failed]**.

**Android V2용**

Android V2 격리 메커니즘은 Android V1과 동일한 프로세스를 사용하며, 구독 및 제외 업데이트에도 적용됩니다. 자세한 내용은 [Android V1](#android-quarantine) 섹션을 참조하십시오.

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
   <td> 메시지 작성/분석 단계: 사용자 지정 필드에 사용된 잘못된 키워드입니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 다음 키워드를 사용할 수 없습니다. {1}<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지 작성/분석 단계: 페이로드가 너무 큽니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 알림이 너무 큽니다. {1}비트({2}만 인증됨)<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 보내는 동안 네트워크 연결이 끊어졌습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 다음 주소에서 Firebase Cloud Messaging 서비스의 응답이 없습니다. {1}<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: FCM 서버를 일시적으로 사용할 수 없습니다(예: 시간 초과 포함). <br /> </td> 
   <td> 실패<br /> </td> 
   <td> Firebase 클라우드 메시징 서비스를 일시적으로 사용할 수 없습니다<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 보낸 사람 계정을 인증하는 동안 오류가 발생했습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 개발자 계정을 식별하지 못했습니다. ID와 암호를 확인하십시오<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 장치 할당량을 초과했습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 잘못된 등록/등록되지 않았습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> </td> 
   <td> 하드<br /> </td> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 다른 모든 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> Firebase Cloud 메시징 서버에서 예기치 않은 오류 코드를 반환했습니다. {1} </td> 
   <td> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM 메시지 거부: 잘못된 인수<br /> </td> 
   <td> 실패<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> 무시됨</td> 
   <td> 정의되지 않음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 타사 인증 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 보낸 사람 ID가 일치하지 않습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 소프트</td>
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 등록되지 않음<br /> </td> 
   <td> 실패<br /> </td>
   <td> 등록되지 않음 </td> 
   <td> 하드</td> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 내부<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 내부 </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 사용할 수 없음<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 사용할 수 없음</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 예기치 않은 오류 코드<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 예기치 않은 오류 코드</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
  <tr> 
   <td> 인증: 연결 문제<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 인증 서버에 연결할 수 없음 </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 요청에 있는 권한이 없는 클라이언트 또는 범위입니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 클라이언트가 이 방법을 사용하여 액세스 토큰을 검색할 권한이 없거나 클라이언트가 요청한 범위에 대해 권한이 없습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 액세스가 거부되었습니다.<br /> </td> 
   <td> 실패<br /> </td>
   <td> access_denied</td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 잘못된 전자 메일<br /> </td> 
   <td> 실패<br /> </td> 
   <td> invalid_grant </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 잘못된 JWT<br /> </td> 
   <td> 실패<br /> </td> 
   <td> invalid_grant </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 잘못된 JWT 서명<br /> </td> 
   <td> 실패<br /> </td> 
   <td> invalid_grant </td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 잘못된 OAuth 범위 또는 ID 토큰 대상이 제공되었습니다<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: OAuth 클라이언트가 비활성화되었습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> disabled_client</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS 격리 {#sms-quarantines}

**표준 커넥터용**

SMS 메시지의 격리 메커니즘은 전반적인 프로세스와 전체적으로 동일합니다. 자세한 내용은 [격리 기본 정보](#about-quarantines). SMS에 대한 세부 사항은 아래에 나와 있습니다.

>[!NOTE]
다음 **[!UICONTROL Delivery log qualification]** 테이블은 **확장된 일반 SMPP** 커넥터.

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
   <td> 공급자에게 전송됨<br /> </td> 
   <td> 전송<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 모바일에서 수신<br /> </td> 
   <td> 수신<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 공급자가 반환한 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 데이터를 받는 동안 오류(SR 또는 MO)<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 MT 승인<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 전송 쿼리에 대한 승인 프레임을 처리하는 동안 '{1}' 오류가 발생했습니다.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
  </tr> 
  <tr> 
   <td> MT를 보내는 동안 오류가 발생했습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 메시지를 보내는 동안 오류가 발생했습니다.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
  </tr> 
 </tbody> 
</table>

**확장된 일반 SMPP 커넥터의 경우**

SMPP 프로토콜을 사용하여 SMS 메시지를 보낼 때 오류 관리는 다르게 처리됩니다. 확장 일반 SMPP 커넥터에 대한 자세한 내용은 [이 페이지](sms-set-up.md#creating-an-smpp-external-account).

SMPP 커넥터는 정규 표현식(regexes)을 사용하여 반환되는 SR(상태 보고서) 메시지에서 데이터를 검색하여 컨텐츠를 필터링합니다. 그러면 이 데이터가 **[!UICONTROL Delivery log qualification]** 표(를 통해 사용 가능 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** 메뉴 아래의 제품에서 사용할 수 있습니다.

새 유형의 오류가 검증되기 전에 실패 이유가 항상 **거부됨** 기본적으로 제공됩니다.

>[!NOTE]
실패 유형 및 실패 이유는 이메일과 동일합니다. 자세한 내용은 [게재 실패 유형 및 이유](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
게재 로그 자격 테이블에서 적절한 실패 유형 및 실패 이유를 설정하려면 상태 및 오류 코드 목록을 공급자에게 문의하십시오.

생성된 메시지의 예:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 모든 오류 메시지는 **SR** sms 오류 코드와 이메일 오류 코드를 구분하기 위한 것입니다.
* 두 번째 부품(**일반** 이 예에서) 오류 메시지의 는 **[!UICONTROL SMSC implementation name]** SMS 외부 계정의 필드입니다. [이 페이지](sms-set-up.md#creating-an-smpp-external-account)를 참조하십시오.

   동일한 오류 코드에는 각 공급자에 대해 다른 의미가 있을 수 있으므로 이 필드에서 오류 코드를 생성한 공급자를 파악할 수 있습니다. 그런 다음 관련 공급자 설명서에서 오류를 찾을 수 있습니다.

* 세 번째 부분(**DELIVRD** 다음 예에서 ) 오류 메시지의 경우 SMS 외부 계정에 정의된 상태 추출 regex를 사용하여 SR에서 검색한 상태 코드에 해당합니다.

   이 정규식은 **[!UICONTROL SMSC specificities]** 외부 계정의 탭. [이 페이지](sms-set-up.md#creating-an-smpp-external-account)를 참조하십시오.

   ![](assets/tech_quarant_error_regex.png)

   기본적으로 regex는 **stat:** 에 의해 정의된 필드 **부록 B** 섹션 **SMPP 3.4 사양**.

* 네 번째 부분(**000** 다음 예에서 ) 오류 메시지의 오류 코드는 SMS 외부 계정에 정의된 오류 코드 추출 regex를 사용하여 SR에서 추출된 오류 코드에 해당합니다.

   이 정규식은 **[!UICONTROL SMSC specificities]** 외부 계정의 탭. [이 페이지](sms-set-up.md#creating-an-smpp-external-account)를 참조하십시오.

   기본적으로 regex는 **오류:** 에 의해 정의된 필드 **부록 B** 섹션 **SMPP 3.4 사양**.

* 파이프 기호(|) 다음에 오는 모든 것은 **[!UICONTROL First text]** 열 **[!UICONTROL Delivery log qualification]** 테이블. 이 콘텐츠는 항상 **#MESSAGE#** 메시지가 표준화된 후. 이 프로세스는 유사한 오류에 대한 여러 항목을 사용하지 않으며 이메일과 동일합니다. 자세한 내용은 [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification).

확장 일반 SMPP 커넥터는 현별 기본값을 찾기 위해 휴리스틱을 적용합니다. 상태가 **DELIVV**&#x200B;를 입력하면 공통 상태와 일치하므로 성공으로 간주됩니다 **DELIVRD** 또는 **배달됨** 대부분의 공급자가 사용합니다. 다른 모든 상태는 하드 실패로 이어집니다.
