---
product: campaign
title: 게재 구성 및 보내기
description: 게재를 구성하고 보내는 방법 알아보기
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: 2e3a14c97706a873f0791ef83708d704d2eed6c3
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 11%

---

# 게재 구성 및 보내기 {#configuring-and-sending-the-delivery}

## 권한{#delivery-permissions}

게재 소유자만 게재를 시작할 수 있습니다. 다른 연산자(또는 연산자 그룹)가 게재를 시작하려면 **[!UICONTROL Delivery start:]** 필드에 검토자로 추가하십시오. [자세히 알아보기](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)

## 게재 추가 매개 변수 {#delivery-additiona-parameters}

게재를 보내기 전에 **[!UICONTROL Delivery]** 탭을 통해 게재 속성에서 전송 매개 변수를 정의할 수 있습니다.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: 우선 순위 수준(보통, 높음 또는 낮음)을 설정하여 게재의 전송 순서를 변경하려면 이 옵션을 사용합니다.

* **[!UICONTROL Message batch quantity]**: 이 옵션을 사용하여 동일한 XML 게재 패키지 내에서 그룹화된 메시지 수를 정의합니다. 매개 변수를 0으로 설정하면 메시지가 자동으로 그룹화됩니다. 패키지 크기는 패키지로 최소 8개에서 최대 256개의 메시지로 계산 `<delivery size>/1024`에 의해 정의됩니다.

  >[!IMPORTANT]
  >
  >기존 게재를 복제하여 게재를 만들 때 이 매개 변수는 재설정됩니다.

* **[!UICONTROL Send using multiple waves]**: 이 옵션을 사용하여 한 번에 전체 대상자에게 메시지를 보내는 대신 일괄로 메시지를 보냅니다. [자세히 알아보기](#sending-using-multiple-waves)

* **[!UICONTROL Test SMTP delivery]**: SMTP를 통한 전송을 테스트하려면 이 옵션을 사용하십시오. 게재는 SMTP 서버에 연결될 때까지 처리되지만 전송되지는 않습니다. 게재의 모든 수신자에 대해 Campaign은 SMTP 공급자 서버에 연결하고 SMTP RCPT TO 명령을 실행한 다음 SMTP DATA 명령 전에 연결을 종료합니다.

  >[!NOTE]
  >
  >* 중간 소싱에서는 이 옵션을 설정하지 않아야 합니다.
  >
  >* [이 섹션](../../installation/using/configure-delivery-settings.md)에서 SMTP 서버 구성에 대해 자세히 알아보세요.

* **[!UICONTROL Email BCC]**: 메시지 대상에 BCC 이메일 주소를 추가하여 BCC를 통해 외부 시스템에 이메일을 저장하려면 이 옵션을 사용합니다. [자세히 알아보기](sending-messages.md#archiving-emails)

## 게재 확인 {#confirming-delivery}

게재가 구성되어 전송할 준비가 되면 게재 분석을 실행합니다.

이렇게 하려면 **[!UICONTROL Send]**&#x200B;을(를) 클릭하고 원하는 작업을 선택한 다음 **[!UICONTROL Analyze]**&#x200B;을(를) 클릭합니다. [자세히 알아보기](steps-validating-the-delivery.md#analyzing-the-delivery)

![](assets/s_ncs_user_email_del_send.png)

완료되면 **[!UICONTROL Confirm delivery]**&#x200B;을(를) 클릭하여 메시지 배달을 시작합니다.

그런 다음 게재 도우미를 닫고 이 게재의 세부 정보 또는 게재 목록을 통해 액세스할 수 있는 **[!UICONTROL Delivery]** 탭에서 게재 실행을 추적할 수 있습니다.

메시지를 보낸 후 게재를 모니터링하고 추적할 수 있습니다. 자세한 정보는 다음 섹션을 참조하십시오.

* [게재 모니터링](about-delivery-monitoring.md)
* [게재 실패 이해](delivery-failures-quarantine.md)
* [메시지 추적 정보](about-message-tracking.md)

## 게재 전송 예약 {#scheduling-the-delivery-sending}

게재를 예약하여 메시지 전송을 연기할 수 있습니다.

1. **[!UICONTROL Send]** 단추를 클릭하고 **[!UICONTROL Postpone delivery]** 옵션을 선택합니다.

1. **[!UICONTROL Contact date]** 필드에 시작 날짜를 지정하십시오.

![](assets/dlv_email_del_plan.png)

1. 그런 다음 게재 분석을 시작한 다음 게재 전송을 확인할 수 있습니다. 그러나 게재 전송은 **[!UICONTROL Contact date]** 필드에 지정된 날짜까지 시작되지 않습니다.

>[!IMPORTANT]
>
>분석을 시작하면 정의한 연락 날짜가 수정됩니다. 이 날짜를 수정하는 경우 수정 사항을 고려하도록 분석을 다시 시작해야 합니다.

![](assets/s_ncs_user_email_del_start_delayed.png)

게재 목록에 게재가 **[!UICONTROL Pending]** 상태로 표시됩니다.

![](assets/s_ncs_user_email_del_waiting.png)

게재의 **[!UICONTROL Scheduling]** 단추를 통해 업스트림으로 일정을 구성할 수도 있습니다.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

이 옵션을 사용하면 게재를 나중 날짜로 연기하거나 임시 캘린더에 게재를 저장할 수 있습니다.

* **[!UICONTROL Schedule delivery (no automatic execution)]** 옵션을 사용하면 게재의 임시 분석을 예약할 수 있습니다.

  이 구성을 저장하면 게재 상태가 **[!UICONTROL Targeting pending]**(으)로 변경됩니다. 분석은 지정된 날짜에 시작됩니다.

* **[!UICONTROL Schedule delivery (automatic execution on planned date)]** 옵션을 사용하면 배달 날짜를 지정할 수 있습니다.

  **[!UICONTROL Send]**&#x200B;을(를) 클릭하고 **[!UICONTROL Postpone delivery]**&#x200B;을(를) 선택한 다음 분석을 시작하고 게재를 확인합니다. 분석이 완료되면 게재 대상이 준비되고 지정된 날짜에 메시지가 자동으로 전송됩니다.

날짜 및 시간은 현재 연산자의 시간대로 표시됩니다. 연락 날짜 입력 필드 아래에 있는 **[!UICONTROL Time zone]** 드롭다운 목록을 사용하면 입력한 날짜 및 시간을 선택한 시간대로 자동으로 변환할 수 있습니다.

예를 들어 런던 시간 8시에 자동으로 게재를 실행하도록 예약하는 경우 시간은 선택한 시간대로 자동 변환됩니다.

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 예약된 일괄 처리를 사용해 보내기 {#sending-using-multiple-waves}

로드 밸런싱을 위해 게재를 여러 배치로 나눌 수 있습니다. 전체 게재에 대한 배치 수와 배치 비율을 구성합니다.

>[!NOTE]
>
>크기와 두 연속 예약된 예약된 예약된 일괄 처리 사이의 지연 시간만 정의할 수 있습니다. 각 웨이브에 대한 수신자 선택 기준을 구성할 수 없습니다.

1. 게재 속성 창을 열고 **[!UICONTROL Delivery]** 탭을 클릭합니다.
1. **[!UICONTROL Send using multiple waves]** 옵션을 선택하고 **[!UICONTROL Define waves...]** 링크를 클릭합니다.

   ![](assets/s_ncs_user_wizard_waves.png)

1. 웨이브를 구성하려면 다음 중 하나를 수행할 수 있습니다.

   * 각 웨이브의 크기를 정의합니다. 예를 들어 해당 필드에 **[!UICONTROL 30%]**&#x200B;을(를) 입력하면 각 웨이브는 게재에 포함된 메시지의 30%를 나타냅니다. 단, 마지막 웨이브는 메시지의 10%를 나타냅니다.

     **[!UICONTROL Period]** 필드에서 연속되는 두 예약된 일괄 처리 시작 사이의 지연 시간을 지정합니다. 예를 들어, **[!UICONTROL 2d]**&#x200B;을(를) 입력하면 첫 번째 웨이브가 즉시 시작되고, 두 번째 웨이브가 2일 후에 시작되고, 세 번째 웨이브가 4일 후에 시작됩니다.

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 각 웨이브를 보내는 달력을 정의합니다.

     **[!UICONTROL Start]** 열에서 연속되는 두 예약된 일괄 처리 시작 사이의 지연 시간을 지정합니다. **[!UICONTROL Size]** 열에 고정 숫자 또는 백분율을 입력합니다.

     아래 예에서 첫 번째 웨이브는 게재에 포함된 총 메시지 수의 25%를 나타내며 즉시 시작됩니다. 다음 두 파동은 배달을 완료하고 6시간 간격으로 시작하도록 설정된다.

     ![](assets/s_ncs_user_wizard_waves_create.png)

   특정 유형화 규칙 **[!UICONTROL Wave scheduling check]**&#x200B;은(는) 게재 유효성 검사 제한 전에 마지막 웨이브가 계획되도록 합니다. 게재 속성의 **[!UICONTROL Typology]** 탭에서 구성된 캠페인 유형화 및 해당 규칙은 [유형화를 사용한 유효성 검사 프로세스](steps-validating-the-delivery.md#validation-process-with-typologies)에서 표시됩니다.

   >[!IMPORTANT]
   >
   >마지막 전파가 **[!UICONTROL Validity]** 탭에 정의된 배달 기한을 초과하지 않도록 하십시오. 그렇지 않으면 일부 메시지가 전송되지 않을 수 있습니다.
   >
   >마지막 웨이브를 구성할 때 재시도 시간도 충분히 허용해야 합니다. [이 섹션](steps-sending-the-delivery.md#configuring-retries)을 참조하십시오.

1. 전송을 모니터링하려면 게재 로그로 이동합니다. [이 페이지](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"}를 참조하십시오.

   이미 처리된 웨이브에서 전송된 게재(**[!UICONTROL Sent]** 상태)와 나머지 웨이브에서 전송할 게재(**[!UICONTROL Pending]** 상태)를 볼 수 있습니다.

아래의 두 가지 예는 다중 웨이브를 사용하는 가장 일반적인 사용 사례입니다.

* **램프 업 프로세스 중**

  새로운 플랫폼을 사용해 이메일을 보낼 때 인터넷 서비스 제공자(ISP)는 인지되지 않은 IP 주소를 의심하게 된다. 대량의 이메일이 갑자기 전송되면 ISP는 해당 이메일을 스팸으로 표시하는 경우가 많습니다.

  스팸으로 표시되지 않도록 하기 위해 웨이브를 사용하여 전송된 볼륨을 점진적으로 늘릴 수 있습니다. 이를 통해 시작 단계를 원활하게 발전시키고 잘못된 주소의 전체 비율을 줄일 수 있습니다.

  이렇게 하려면 **[!UICONTROL Schedule waves according to a calendar]** 옵션을 사용합니다. 예를 들어 첫 번째 물결을 10%로 설정하고 두 번째 물결을 15%로 설정하는 식입니다.

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **콜센터 관련 캠페인**

  전화로 충성도 캠페인을 관리할 때 조직에서는 연락하는 구독자에 대한 호출 수를 처리하는 데 제한이 있습니다.

  예를 들어, 콜센터의 일일 처리 용량을 고려하여 웨이브를 사용하여 메시지 수를 하루에 20개로 제한할 수 있습니다.

  이렇게 하려면 **[!UICONTROL Schedule multiple waves of the same size]** 옵션을 선택하십시오. **[!UICONTROL 20]** 필드에 웨이브의 크기로 **[!UICONTROL 1d]**&#x200B;을(를) 입력하고 **[!UICONTROL Period]**&#x200B;을(를) 입력합니다.

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 다시 시도 구성 {#configuring-retries}

**소프트** 또는 **무시됨** 오류로 인해 일시적으로 게재되지 않은 메시지는 자동 다시 시도될 수 있습니다. 게재 실패 유형 및 이유는 이 [섹션](delivery-failures-quarantine.md#delivery-failure-types-and-reasons)에 나와 있습니다.

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](sending-with-enhanced-mta.md)(으)로 업그레이드한 경우 게재의 다시 시도 설정은 Campaign에서 더 이상 사용되지 않습니다. 소프트 바운스 재시도 및 재시도 간 시간은 메시지 이메일 도메인에서 돌아오는 바운스 응답의 유형 및 심각도에 따라 고급 MTA에 의해 결정됩니다.

이전 Campaign MTA를 사용하는 온-프레미스 설치 및 호스팅/하이브리드 설치의 경우 게재 매개 변수에 대한 **[!UICONTROL Delivery]** 탭의 중앙 섹션은 게재 다음 날에 수행해야 하는 다시 시도 횟수와 다시 시도 사이의 최소 지연을 나타냅니다.

![](assets/s_ncs_user_wizard_retry_param.png)

기본적으로 5번의 다시 시도가 배달 첫 날에 예약되며 하루 중 24시간 동안 최소 1시간 간격으로 분산됩니다. **[!UICONTROL Validity]** 탭에 정의된 배달 기한까지 하루에 한 번 다시 시도됩니다. [유효 기간 정의](#defining-validity-period)를 참조하십시오.

## 유효 기간 정의 {#defining-validity-period}

게재가 실행되면 게재 기한까지 메시지(및 다시 시도)를 보낼 수 있습니다. 게재 속성에는 **[!UICONTROL Validity]** 탭을 통해 표시됩니다.

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]** 필드를 사용하면 전역 게재 다시 시도에 대한 제한을 입력할 수 있습니다. 즉, Adobe Campaign은 시작 날짜부터 메시지를 전송하고 나서 메시지가 오류만 반환하는 경우 유효성 검사 제한에 도달할 때까지 구성 가능한 일반 재시도를 수행합니다.

  날짜를 지정할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Explicitly set validity dates]**&#x200B;을(를) 선택합니다. 이 경우 게재 및 유효성 검사 제한 날짜를 통해 시간을 지정할 수도 있습니다. 기본적으로 현재 시간이 사용되지만 입력 필드에서 직접 수정할 수 있습니다.

  >[!IMPORTANT]
  >
  >호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](sending-with-enhanced-mta.md)(으)로 업그레이드한 경우 Campaign 이메일 게재의 **[!UICONTROL Delivery duration]** 설정은 **3.5일 이하**(으)로 설정된 경우에만 사용됩니다. 3.5일 이상의 값을 정의하면 고려되지 않습니다.

* **리소스의 유효성 제한**: **[!UICONTROL Validity limit]** 필드는 주로 미러 페이지와 이미지에 대해 업로드된 리소스에 사용됩니다. 이 페이지의 리소스는 제한된 시간 동안 유효합니다(디스크 공간을 절약하기 위함).

  이 필드의 값은 다음 단위로 표현할 수 있습니다. **s**(초), **m**(분), **h**(시간), **d**(일)(기본값), **y**(년).
