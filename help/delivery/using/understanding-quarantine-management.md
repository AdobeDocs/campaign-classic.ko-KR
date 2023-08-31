---
product: campaign
title: 격리 관리 이해
description: 격리 관리 이해
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '3009'
ht-degree: 12%

---

# 격리 관리 이해{#understanding-quarantine-management}

Adobe Campaign은 격리된 주소 목록을 관리합니다. 주소가 격리된 수신자는 기본적으로 게재 분석 중에 제외되며 타겟팅되지 않습니다. 예를 들어, 사서함이 가득 찼거나 주소가 없는 경우 전자 메일 주소를 격리할 수 있습니다. 어떤 경우든, 격리 절차는 아래에 기술된 특정한 규칙을 준수한다.

>[!NOTE]
>
>이 섹션은 온라인 채널(이메일, SMS, 푸시 알림)에 적용됩니다.

## 격리 관리를 통해 게재 최적화 {#optimizing-your-delivery-through-quarantines}

이메일 주소 또는 전화번호가 격리된 프로필은 메시지를 준비하는 동안 자동으로 제외됩니다(참조) [게재에 대해 격리된 주소 확인](#identifying-quarantined-addresses-for-a-delivery)). 이를 통해 게재 속도를 높일 수 있습니다. 오류율은 게재 속도에 상당한 영향을 미치기 때문입니다.

일부 인터넷 액세스 제공 업체는 잘못된 주소의 비율이 너무 높은 경우 이메일을 자동으로 스팸으로 간주합니다. 따라서 이러한 공급자에 의해 차단 목록에 추가하다에 추가되는 것을 피할 수 있습니다.

또한 격리를 통해 잘못된 전화번호를 게재에서 제외하면 SMS를 보내는 비용을 줄이는 데 도움이 됩니다.

게재 보안 향상 및 최적화 모범 사례를 더 알아보려면 [이 페이지](delivery-best-practices.md)를 참조하십시오.

### 차단 목록에 추가하다 방역 {#quarantine-vs-denylist}

차단 목록에 추가하다와 동일한 객체에는 적용되지 않습니다.

* **격리** 에만 적용됩니다. **주소** (또는 전화 번호 등), 프로필 자체가 아닙니다. 예를 들어 이메일 주소가 격리된 프로필은 프로필을 업데이트하고 새 주소를 입력한 다음 게재 작업으로 다시 타겟팅될 수 있습니다. 마찬가지로, 두 프로필의 전화 번호가 같으면 해당 번호가 격리되면 둘 다 영향을 받습니다.

  격리된 주소 또는 전화번호는 [제외 로그](#identifying-quarantined-addresses-for-a-delivery) (게재용) 또는 [격리 목록](#identifying-quarantined-addresses-for-the-entire-platform) (전체 플랫폼).

* 다음에 있음 **차단 목록**&#x200B;반면 은(는) **프로필** 지정된 채널에 대해 구독 취소(옵트아웃) 후와 같이 더 이상 게재의 타겟이 되지 않습니다. 예를 들어 이메일 채널에 대한 차단 목록에 추가하다의 프로필에 두 개의 이메일 주소가 있는 경우 두 주소 모두 게재에서 제외됩니다.

  프로필이 차단 목록에 추가하다에 있는지 또는 의 하나 이상의 채널에 있는지 확인할 수 있습니다. **[!UICONTROL No longer contact]** 프로필 섹션 **[!UICONTROL General]** 탭. [이 섹션](../../platform/using/editing-a-profile.md#general-tab)을 참조하십시오.

>[!NOTE]
>
>격리 포함 사항 **[!UICONTROL Denylisted]** 상태: 수신자가 메시지를 스팸으로 보고하거나 &quot;STOP&quot;과 같은 키워드를 사용하여 SMS 메시지에 회신할 때 적용됩니다. 이 경우 해당 프로필의 관련 주소나 전화번호는 **[!UICONTROL Denylisted]** 상태. STOP SMS 메시지 관리에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](../../delivery/using/sms-send.md#processing-inbound-messages).

## 격리된 주소 확인 {#identifying-quarantined-addresses}

특정 게재 또는 플랫폼 전체에 대해 격리된 주소를 나열할 수 있습니다.

### 게재에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-a-delivery}

특정 게재에 대해 격리된 주소 목록은 게재 준비 단계 중 게재 대시보드의 게재 로그에 표시됩니다( 참조) [게재 로그 및 내역](delivery-dashboard.md#delivery-logs-and-history)).

### 플랫폼 전체에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-the-entire-platform}

관리자는 의 플랫폼 전체에 대해 격리된 주소 목록을 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 노드.

>[!NOTE]
>
>이 메뉴에는 **이메일**, **SMS** 및 **푸시 알림** 채널에 대해 격리된 요소의 목록이 표시됩니다.

각 주소에 대해 다음 정보를 사용할 수 있습니다.

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>격리 수의 증가는 데이터베이스의 &quot;마모&quot;와 관련된 정상적인 효과입니다. 예를 들어 이메일 주소의 수명을 3년으로 보고 수신자 표가 매년 50%씩 증가하는 경우 다음과 같이 격리 증가를 계산할 수 있습니다.
>
>1년말: (1)&#42;0.33)/(1+0.5)=22%.
>
>2년말: (1.22&#42;0.33)+0.33)/(1.5+0.75)=32.5%.

### 게재 보고서에서 격리된 주소 확인 {#identifying-quarantined-addresses-in-delivery-reports}

다음 보고서는 격리된 주소에 대한 정보를 제공합니다.

* 각 게재의 경우 **[!UICONTROL Delivery summary]** 이 보고서는 게재 대상에 격리된 주소 수를 보여줍니다. 다음과 같이 표시됩니다.

   * 게재 분석 중 격리된 주소 수

   * 게재 작업 후 격리된 주소 수입니다.

* 다음 **[!UICONTROL Non-deliverables and bounces]** 보고서는 격리된 주소, 발생한 오류 유형 등에 대한 정보와 도메인별 오류 분류를 표시합니다.

플랫폼의 모든 게재에 대해 이 정보를 조회할 수 있습니다(**[!UICONTROL Home page > Reports]**) 또는 특정 게재용 사용자 지정된 보고서를 만들고 표시할 정보를 선택할 수도 있습니다.

### 수신자에 대해 격리된 주소 확인 {#identifying-quarantined-addresses-for-a-recipient}

모든 수신자의 이메일 주소 상태를 조회할 수 있습니다. 이렇게 하려면 수신자 프로필을 선택하고 **[!UICONTROL Deliveries]** 탭. 해당 수신자에 대한 모든 게재에 대해 주소가 실패했는지, 분석 중에 격리되었는지 등을 확인할 수 있습니다. 각 폴더에 대해 전자 메일 주소가 격리된 수신자만 표시할 수 있습니다. 이렇게 하려면 **[!UICONTROL Quarantined email address]** 애플리케이션 필터.

![](assets/tech_quarant_recipients_filter.png)


## 주소를 격리하는 조건 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign은 게재 실패 유형 및 오류 메시지 자격 중에 할당된 이유에 따라 격리를 관리합니다( 참조) [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification) 및 [게재 실패 유형 및 이유](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **무시된 오류**: 오류가 무시된 경우 주소가 격리되지 않습니다.
* **하드 오류**: 해당 이메일 주소가 즉시 격리됩니다.
* **소프트 오류**: 소프트 오류의 경우 주소가 즉시 격리되지는 않지만, 오류 카운터가 증가합니다. 자세한 내용은 [소프트 오류 관리](#soft-error-management).

사용자가 이메일을 스팸 처리하려는 경우([되먹임 루프](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)) 메시지는 Adobe에서 관리하는 기술 사서함으로 자동 리디렉션됩니다. 그러면 사용자의 이메일 주소가 자동으로 **[!UICONTROL Denylisted]** 상태로 격리됩니다. 이 상태는 주소만 참조하고, 프로필은 푸시 차단 목록에 있지 않으므로 SMS 메시지와 알림을 계속 수신하게 됩니다.

>[!NOTE]
>
>Adobe Campaign의 격리는 대소문자를 구분합니다. 이메일 주소를 소문자로 가져와야 이후에 다시 타겟팅되지 않습니다.

격리된 주소 목록(참조) [플랫폼 전체에 대해 격리된 주소 확인](#identifying-quarantined-addresses-for-the-entire-platform)), **[!UICONTROL Error reason]** 필드는 선택한 주소가 격리된 이유를 나타냅니다.

![](assets/tech_quarant_error_reasons.png)

### 소프트 오류 관리 {#soft-error-management}

하드 오류와 달리 소프트 오류의 경우 주소가 즉시 격리되지는 않지만, 대신 오류 카운터가 증가합니다.

재시도는 다음 기간 동안 수행됩니다. [게재 기간](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period). 오류 카운터가 제한 임계값에 도달하면 주소가 격리됩니다. 자세한 내용은 다음을 참조하십시오. [일시적 게재 실패 후 다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

10일 이상 전에 마지막으로 중요한 오류가 발생한 경우 오류 카운터가 다시 초기화됩니다. 그러면 주소 상태가 (으)로 변경됩니다. **유효** 그리고 다음에 의해 격리 목록에서 삭제됩니다. [데이터베이스 정리](../../production/using/database-cleanup-workflow.md) 워크플로입니다.


호스팅 또는 하이브리드 설치의 경우 를 로 업그레이드한 경우 [향상된 MTA](sending-with-enhanced-mta.md)를 설정하는 경우 수행할 최대 다시 시도 수 **[!UICONTROL Erroneous]** 상태와 재시도 사이의 최소 지연은 이제 IP가 과거 및 현재 지정된 도메인에서 얼마나 잘 수행하고 있는지에 따라 달라집니다.

기존 Campaign MTA를 사용하는 온-프레미스 설치 및 호스팅/하이브리드 설치의 경우 오류 수와 두 오류 사이의 기간을 수정할 수 있습니다. 이렇게 하려면 [배포 마법사](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) 또는 [게재 수준](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).


## 격리에서 주소 제거 {#removing-a-quarantined-address}

### 자동 업데이트 {#unquarantine-auto}

특정 조건과 일치하는 주소는 다음을 통해 격리 목록에서 자동으로 삭제됩니다. [데이터베이스 정리](../../production/using/database-cleanup-workflow.md) 워크플로입니다.

다음과 같은 경우 주소가 격리 목록에서 자동으로 제거됩니다.

* 의 주소 **[!UICONTROL With errors]** 게재가 성공하면 격리 목록에서 상태가 제거됩니다.
* 의 주소 **[!UICONTROL With errors]** 마지막 소프트 바운스가 10일 이상 전에 발생한 경우 상태가 격리 목록에서 제거됩니다. 소프트 오류 관리에 대한 자세한 내용은 [이 섹션](#soft-error-management).
* 의 주소 **[!UICONTROL With errors]** 와 함께 반송된 상태 **[!UICONTROL Mailbox full]** 30일 후 격리 목록에서 오류가 제거됩니다.

상태가 다음으로 변경됨: **[!UICONTROL Valid]**.

>[!IMPORTANT]
>
>에 주소가 있는 수신자 **[!UICONTROL Quarantine]** 또는 **[!UICONTROL Denylisted]** 이메일을 수신하더라도 상태는 제거되지 않습니다.

### 수동 업데이트 {#unquarantine-manual}

주소를 수동으로 격리 해제할 수도 있습니다. 주소를 격리 목록에서 수동으로 제거하려면 주소를 격리 목록에서 수동으로 주소를 격리 목록에서 격리 목록에서 수동으로 제거 **[!UICONTROL Valid]** 다음에서 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 노드.

![](assets/tech_quarant_error_status.png)

### 벌크 업데이트 {#unquarantine-bulk}

예를 들어 ISP 중단이 있는 경우 격리 목록에서 벌크 업데이트를 수행해야 할 수 있습니다. 이러한 경우 이메일이 수신자에게 성공적으로 전달될 수 없기 때문에 바운스로 잘못 표시됩니다. 격리 목록에서 이러한 주소를 제거해야 합니다.

이 작업을 수행하려면 워크플로우를 만들고 **[!UICONTROL Query]** 격리 테이블에서 활동을 수행하여 영향을 받는 모든 수신자를 필터링합니다. 식별되면 격리 목록에서 제거하고 향후 Campaign 이메일 게재에 포함할 수 있습니다.

다음은 이 쿼리에 대한 권장 지침입니다.

* 에 인바운드 이메일 규칙 정보가 있는 Campaign Classic v7 환경의 경우 **[!UICONTROL Error text]** 격리 목록의 필드:

   * **오류 텍스트(격리 텍스트)** 에는 &quot;Momen_Code10_InvalidRecipient&quot;가 포함되어 있습니다.
   * **이메일 도메인(@domain)** domain1.com과 같음 또는 **이메일 도메인(@domain)** domain2.com과 같음 또는 **이메일 도메인(@domain)** domain3.com과 같음
   * **업데이트 상태(@lastModified)** YYYY/MM/DD HH 또는 이후:MM:오전 SS
   * **업데이트 상태(@lastModified)** YYYY/MM/DD HH 또는 이전:MM:오후

* 에 SMTP 바운스 응답 정보가 있는 Campaign Classic v7 인스턴스 **[!UICONTROL Error text]** 격리 목록의 필드:

   * **오류 텍스트(격리 텍스트)** 은 &quot;550-5.1.1&quot;을 포함하고 **오류 텍스트(격리 텍스트)** &quot;support.ISP.com&quot;을 포함합니다.

  예를 들어 &quot;support.ISP.com&quot;은 &quot;support.apple.com&quot; 또는 &quot;support.google.com&quot;일 수 있습니다.

   * **업데이트 상태(@lastModified)** YYYY/MM/DD HH 또는 이후:MM:오전 SS
   * **업데이트 상태(@lastModified)** YYYY/MM/DD HH 또는 이전:MM:오후

영향을 받는 수신자 목록이 있으면 **[!UICONTROL Update data]** 활동을 통해 이메일 주소 상태를 다음으로 설정 **[!UICONTROL Valid]** 따라서 다음을 통해 격리 목록에서 제거됩니다. **[!UICONTROL Database cleanup]** 워크플로입니다. 격리 테이블에서 삭제할 수도 있습니다.

## 푸시 알림 격리 {#push-notification-quarantines}

푸시 알림의 격리 메커니즘은 전체적으로 일반 프로세스와 동일합니다. 그러나 일부 오류는 푸시 알림에 대해 다르게 관리됩니다. 예를 들어 특정 소프트 오류의 경우 동일한 게재 내에서 재시도가 수행되지 않습니다. 푸시 알림에 대한 특징은 아래에 나와 있습니다. 재시도 메커니즘(재시도 횟수, 빈도)은 이메일과 동일합니다.

격리 중인 항목은 장치 토큰입니다.

### iOS 격리 {#ios-quarantine}

HTTP/V2 프로토콜을 통해 각 푸시 게재에 대한 직접 피드백 및 상태를 사용할 수 있습니다. HTTP/V2 프로토콜 커넥터를 사용하는 경우 피드백 서비스는 더 이상 **[!UICONTROL mobileAppOptOutMgt]** 워크플로입니다. 모바일 애플리케이션을 제거하거나 다시 설치하면 토큰이 등록 취소된 것으로 간주됩니다.

동기적으로 APNs가 메시지에 대해 &quot;등록되지 않음&quot; 상태를 반환하면 대상 토큰이 즉시 격리됩니다.

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
   <td> 대상 장치 전원 켜짐<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 대상 장치의 전원이 꺼짐<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 사용자가 애플리케이션에 대한 알림을 비활성화합니다.<br /> </td> 
   <td> 확인<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 메시지 작성/분석 단계 - 페이로드가 너무 큼<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 페이로드 초과<br /> </td> 
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
   <td> 인증서 문제(암호, 손상 등) 및 APNs 연결 테스트 문제<br /> </td> 
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
   <td> APNs 메시지 거부: 기타 모든 오류<br /> </td> 
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

각 알림에 대해 Adobe Campaign은 FCM 서버로부터 직접 동기 오류를 수신합니다. Adobe 캠페인은 즉시 이를 처리하고 오류 심각도에 따라 하드 또는 소프트 오류를 생성하며 재시도를 수행할 수 있습니다.

* 페이로드 길이 초과, 연결 문제, 서비스 가용성 문제: 재시도 수행, 소프트 오류, 실패 이유: **[!UICONTROL Refused]**.
* 장치 할당량 초과: 재시도 없음, 소프트 오류, 실패 이유: **[!UICONTROL Refused]**.
* 토큰이 잘못되었거나 등록되지 않았습니다. 예기치 않은 오류, 보낸 사람 계정 문제: 재시도 없음, 하드 오류, 실패 이유는 다음과 같습니다. **[!UICONTROL Refused]**.

다음 **[!UICONTROL mobileAppOptOutMgt]** 워크플로우는 6시간마다 실행되어 **AppSubscriptionRcp** 테이블. 등록 취소되었거나 더 이상 유효하지 않다고 선언된 토큰의 경우 필드 **비활성화됨** 이(가) (으)로 설정됨 **True** 및 해당 장치 토큰에 연결된 구독은 향후 게재에서 자동으로 제외됩니다.

게재 분석 중에 대상에서 제외된 모든 장치는 **excludeLogAppSubRcp** 테이블.

>[!NOTE]
>
>Baidu 커넥터를 사용하는 고객의 경우 다음과 같은 다양한 유형의 오류가 있습니다.
>
>* 게재 시작 시 연결 문제: 실패 유형 **[!UICONTROL Undefined]**, 실패 이유 **[!UICONTROL Unreachable]**, 재시도가 수행됩니다.
>* 게재 중 연결 끊김: 소프트 오류, 실패 이유 **[!UICONTROL Refused]**, 재시도가 수행됩니다.
>* 전송 중 Baidu에서 동기 오류 반환: 하드 오류, 실패 이유 **[!UICONTROL Refused]**, 재시도가 수행되지 않습니다.
>
>Adobe Campaign은 10분마다 Baidu 서버에 연결하여 보낸 메시지의 상태를 검색하고 broadlogs를 업데이트합니다. 메시지가 전송됨으로 선언되면 브로드로그의 메시지 상태는 다음과 같이 설정됩니다. **[!UICONTROL Received]**. Baidu에서 오류를 선언하면 상태가 로 설정됩니다. **[!UICONTROL Failed]**.

**Android V2용**

Android V2 격리 메커니즘은 Android V1과 동일한 프로세스를 사용하므로 구독 및 제외 업데이트에도 동일하게 적용됩니다. 자세한 내용은 다음을 참조하십시오. [안드로이드 V1](#android-quarantine) 섹션.

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
   <td> 메시지 작성/분석 단계: 사용자 정의 필드에 잘못된 키워드가 사용됨<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 다음 키워드를 사용할 수 없습니다. {1}<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지 작성/분석 단계: 페이로드가 너무 큼<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 알림이 너무 큽니다. {1}비트이지만 {2}만 인증됩니다.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> 보내는 동안 네트워크 연결이 끊어졌습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> {1} 주소에 대한 Firebase Cloud Messaging 서비스의 응답이 없습니다.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: FCM 서버를 일시적으로 사용할 수 없습니다(예: 시간 초과). <br /> </td> 
   <td> 실패<br /> </td> 
   <td> Firebase Cloud Messaging 서비스를 일시적으로 사용할 수 없습니다<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 보낸 사람 계정을 인증하는 동안 오류 발생<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 개발자 계정을 식별하지 못했습니다. ID와 암호를 확인하십시오.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 장치 할당량 초과<br /> </td> 
   <td> 실패<br /> </td> 
   <td> </td> 
   <td> 소프트<br /> </td> 
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 잘못된 등록/등록되지 않음<br /> </td> 
   <td> 실패<br /> </td> 
   <td> </td> 
   <td> 하드<br /> </td> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM 메시지 거부: 기타 모든 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> Firebase 클라우드 메시징 서버에서 예기치 않은 오류 코드를 반환했습니다. {1} </td> 
   <td> </td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM 메시지 거부: 잘못된 인수<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 잘못된 인수 </td> 
   <td> 무시됨</td> 
   <td> 정의되지 않음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 서드파티 인증 오류<br /> </td> 
   <td> 실패<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 예<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 보낸 사람 ID 불일치<br /> </td> 
   <td> 실패<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 소프트</td>
   <td> 사용자 알 수 없음<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> FCM 메시지 거부: 등록 취소됨<br /> </td> 
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
   <td> 인증: 요청에 승인되지 않은 클라이언트 또는 범위입니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 클라이언트는 이 메서드를 사용하여 액세스 토큰을 검색할 수 있는 권한이 없거나 요청된 범위에 대해 권한이 없는 클라이언트입니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 액세스 거부됨<br /> </td> 
   <td> 실패<br /> </td>
   <td> access_denied</td> 
   <td> 무시됨</td>
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: 잘못된 이메일<br /> </td> 
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
   <td> 인증: 잘못된 OAuth 범위 또는 ID 토큰 대상이 제공되었습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> unauthorized_client</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
    <tr> 
   <td> 인증: OAuth 클라이언트가 비활성화됨<br /> </td> 
   <td> 실패<br /> </td> 
   <td> disabled_client</td> 
   <td> 무시됨</td> 
   <td> 거부됨<br /> </td> 
   <td> 아니요<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS 격리 {#sms-quarantines}

**표준 커넥터의 경우**

SMS 메시지의 격리 메커니즘은 전체적으로 일반 프로세스와 동일합니다. 다음을 참조하십시오 [격리 기본 정보](#about-quarantines). SMS에 대한 특성은 아래에 나와 있습니다.

>[!NOTE]
>
>다음 **[!UICONTROL Delivery log qualification]** 표는 다음에 적용되지 않습니다. **확장된 일반 SMPP** 커넥터.

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
   <td> 전송됨<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 모바일에서 수신됨<br /> </td> 
   <td> 수신됨<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 공급자가 오류를 반환했습니다.<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 데이터(SR 또는 MO) 수신 중 오류 발생<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 MT 승인<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 송신 쿼리에 대한 승인 프레임을 처리하는 동안 오류 '{1}'이(가) 발생했습니다.<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
  </tr> 
  <tr> 
   <td> MT를 전송하는 중 오류 발생<br /> </td> 
   <td> 실패<br /> </td> 
   <td> 메시지를 보내는 중 오류 발생<br /> </td> 
   <td> 소프트<br /> </td> 
   <td> 연결할 수 없음<br /> </td> 
  </tr> 
 </tbody> 
</table>

**확장된 일반 SMPP 커넥터의 경우**

SMPP 프로토콜을 사용하여 SMS 메시지를 전송하는 경우 오류 관리가 다르게 처리됩니다. Extended Generic SMPP 커넥터에 대한 자세한 내용은 [이 페이지](sms-set-up.md#creating-an-smpp-external-account).

SMPP 커넥터는 정규 표현식(정규 표현식)을 사용하여 반환되는 SR(상태 보고서) 메시지에서 데이터를 검색하여 해당 콘텐츠를 필터링합니다. 그런 다음 이 데이터는 **[!UICONTROL Delivery log qualification]** 테이블(다음을 통해 사용 가능) **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** 메뉴)를 참조하십시오.

새로운 유형의 오류가 검증되기 전에 실패 이유는 항상 로 설정됩니다. **거부됨** 기본적으로.

>[!NOTE]
>
>실패 유형 및 실패 이유는 이메일과 동일합니다. 다음을 참조하십시오 [게재 실패 유형 및 이유](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>게재 로그 자격 표에서 적절한 실패 유형 및 실패 이유를 설정하려면 공급자에게 상태 및 오류 코드 목록을 요청하십시오.

생성된 메시지의 예:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 모든 오류 메시지는 다음으로 시작합니다. **SR** sms 오류 코드와 이메일 오류 코드를 구별합니다.
* 두 번째 부분(**일반** 이 예제에서) 오류 메시지는에 정의된 SMSC 구현의 이름을 참조합니다. **[!UICONTROL SMSC implementation name]** SMS 외부 계정 필드. [이 페이지](sms-set-up.md#creating-an-smpp-external-account)를 참조하십시오.

  동일한 오류 코드는 각 공급자에 대해 다른 의미를 가질 수 있으므로 이 필드를 사용하면 오류 코드를 생성한 공급자를 알 수 있습니다. 그런 다음 관련 공급자의 설명서에서 오류를 찾을 수 있습니다.

* 세 번째 부분(**배달 목록** 이 예에서는 ) 오류 메시지의 가 SMS 외부 계정에 정의된 상태 추출 정규 표현식을 사용하여 SR에서 검색한 상태 코드에 해당합니다.

  이 정규 표현식은 **[!UICONTROL SMSC specificities]** 외부 계정의 탭입니다. [이 페이지](sms-set-up.md#creating-an-smpp-external-account)를 참조하십시오.

  ![](assets/tech_quarant_error_regex.png)

  기본적으로 정규 표현식은 **통계:** 로 정의된 필드 **부록 B** 의 섹션 **SMPP 3.4 사양**.

* 네 번째 부분(**000** 이 예에서는) 오류 메시지의 가 SMS 외부 계정에 정의된 오류 코드 추출 정규 표현식을 사용하여 SR에서 추출된 오류 코드에 해당합니다.

  이 정규 표현식은 **[!UICONTROL SMSC specificities]** 외부 계정의 탭입니다. [이 페이지](sms-set-up.md#creating-an-smpp-external-account)를 참조하십시오.

  기본적으로 정규 표현식은 **오류:** 로 정의된 필드 **부록 B** 의 섹션 **SMPP 3.4 사양**.

* 파이프 기호(|) 뒤에 오는 모든 것은 **[!UICONTROL First text]** 열 **[!UICONTROL Delivery log qualification]** 테이블. 이 콘텐츠는 항상 다음으로 대체됩니다. **#MESSAGE#** 메시지가 표준화된 후. 이 프로세스는 유사한 오류에 대해 여러 항목을 포함하지 않으며 이메일과 동일합니다. 자세한 내용은 [반송 메일 조건](understanding-delivery-failures.md#bounce-mail-qualification).

확장된 일반 SMPP 커넥터는 인지 가능한 기본값을 찾는 휴리스틱을 적용합니다. 상태가 다음으로 시작되는 경우 **DELIV**, 공통 상태와 일치하므로 성공으로 간주됩니다 **배달 목록** 또는 **게재됨** 대부분의 공급자가 사용합니다. 그 밖의 어떤 상황도 하드 장애로 이어집니다.
