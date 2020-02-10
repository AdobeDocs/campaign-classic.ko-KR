---
title: 배달 구성 및 보내기
seo-title: 배달 구성 및 보내기
description: 배달 구성 및 보내기
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# 배달 구성 및 보내기 {#configuring-and-sending-the-delivery}

>[!NOTE]
>
>배달 소유자만 배달을 시작할 수 있습니다. 다른 연산자(또는 연산자 그룹)가 배달을 시작할 수 있으려면 **[!UICONTROL Delivery start:]** 필드에 검토자로 추가해야 합니다.
>
>자세한 내용은 [이 섹션을](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers) 참조하십시오.

## 추가 매개 변수 전달 {#delivery-additiona-parameters}

배달을 보내기 전에 **[!UICONTROL Delivery]** 탭을 통해 전달 속성에서 전송 매개 변수를 정의할 수 있습니다.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**:이 옵션을 사용하면 우선순위 수준(일반, 높음 또는 낮음)을 지정하여 게재의 전송 주문에 영향을 줄 수 있습니다. 이렇게 하면 특정 긴급 배달의 우선 순위를 다른 배달보다 더 정할 수 있습니다.

* **[!UICONTROL Message batch quantity]**:이 옵션을 사용하면 동일한 XML 배달 패키지 내에서 그룹화된 메시지 수를 정의할 수 있습니다. 이 매개 변수를 0으로 설정하면 메시지가 자동으로 그룹화됩니다. 패키지 크기는 최소 8개 `<delivery size>/1024`및 최대 256개 메시지와 함께 계산에서 정의됩니다.

   >[!CAUTION]
   >
   >배달이 중복되면 매개 변수가 재설정됩니다.

* **[!UICONTROL Send using multiple waves]**:자세한 내용은 [여러 파도를](#sending-using-multiple-waves)사용하여 보내기를 참조하십시오.

* **[!UICONTROL Test SMTP delivery]**:이 옵션을 사용하면 SMTP를 통해 배달 전송을 테스트할 수 있습니다. 배달은 SMTP 서버에 대한 연결까지 처리되지만 전송되지 않습니다.

   >[!NOTE]
   >
   >mta를 호출하지 않도록 mid-sourcing을 사용하여 설치하는 경우에는 이 옵션을 사용하는 것이 좋습니다.
   >
   >SMTP 서버 구성에 대한 자세한 내용은 [이 섹션을](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)참조하십시오.

* **[!UICONTROL Archive emails]**:이 옵션을 사용하면 BCC를 통해 외부 시스템에 메시지를 저장할 수 있습니다. 자세한 내용은 이메일 보관을 [참조하십시오](../../delivery/using/sending-messages.md#archiving-emails).

배달이 구성되고 전송될 준비가 되면 배달 분석을 [실행했는지 확인합니다](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery). 완료되면 을 클릭하여 메시지 배달을 **[!UICONTROL Confirm delivery]** 시작합니다.

![](assets/s_ncs_user_email_del_send.png)

그런 다음 배달 마법사를 닫고 이 배달의 세부 사항이나 배달 목록을 통해 액세스할 수 있는 **[!UICONTROL Delivery]** 탭에서 배달 실행을 추적할 수 있습니다.

메시지를 보낸 후 배달을 모니터링하고 추적할 수 있습니다. 자세한 내용은 다음 섹션을 참조하십시오.

* [게재 모니터링](../../delivery/using/monitoring-a-delivery.md)
* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)
* [메시지 추적 정보](../../delivery/using/about-message-tracking.md)

## 배달 전송 예약 {#scheduling-the-delivery-sending}

메시지 전달을 연기하여 배달 일정을 잡거나 판매 압력을 관리하며 모집단을 과도한 모집하지 않을 수 있습니다.

1. 단추를 클릭하고 **[!UICONTROL Send]** **[!UICONTROL Postpone delivery]** 옵션을 선택합니다.

1. 시작 날짜를 **[!UICONTROL Contact date]** 필드에 지정합니다.

![](assets/dlv_email_del_plan.png)

1. 그런 다음 배달 분석을 시작한 다음 배달 전송을 확인할 수 있습니다. 그러나 배달 보내기는 **[!UICONTROL Contact date]** 필드에 지정된 날짜까지 시작되지 않습니다.

>[!CAUTION]
>
>분석을 시작하면 정의한 연락처 날짜가 수정됩니다. 이 날짜를 수정하는 경우 수정을 고려하도록 분석을 다시 시작해야 합니다.

![](assets/s_ncs_user_email_del_start_delayed.png)

배달 목록에 배달이 **[!UICONTROL Pending]** 상태와 함께 표시됩니다.

![](assets/s_ncs_user_email_del_waiting.png)

배달 **[!UICONTROL Scheduling]** 단추를 통해 업스트림 예약을 구성할 수도 있습니다.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

배달을 나중 날짜로 연기하거나 임시 달력에 배달을 저장할 수 있습니다.

* 이 **[!UICONTROL Schedule delivery (no automatic execution)]** 옵션을 사용하면 게재의 잠정적인 분석을 예약할 수 있습니다.

   이 구성이 저장되면 배달이 **[!UICONTROL Targeting pending]** 상태로 변경됩니다. 분석은 지정된 날짜에 실행됩니다.

* 이 **[!UICONTROL Schedule delivery (automatic execution on planned date)]** 옵션을 사용하면 배달 날짜를 지정할 수 있습니다.

   을 클릭하고 **[!UICONTROL Send]** 선택한 **[!UICONTROL Postpone delivery]** 다음 분석을 실행하고 전달을 확인합니다. 분석이 완료되면 전달 대상이 준비되고 지정된 날짜에 메시지가 자동으로 전송됩니다.

날짜와 시간은 현재 연산자의 시간대로 표시됩니다. 연락처 날짜 입력 필드 아래에 있는 **[!UICONTROL Time zone]** 드롭다운 목록을 사용하면 입력한 날짜와 시간을 선택한 시간대로 자동으로 변환할 수 있습니다.

예를 들어, 배달이 런던 시간으로 8시에 자동으로 실행되도록 예약하는 경우 시간은 선택한 시간대로 자동 변환됩니다.

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 여러 파도를 사용하여 보내기 {#sending-using-multiple-waves}

로드 밸런싱을 위해 여러 개의 배치로 납품을 나눌 수 있습니다. 전체 게재와 관련하여 배치의 수와 비율을 구성합니다.

>[!NOTE]
>
>두 개의 연속된 파도 사이의 크기와 지연만 정의할 수 있습니다. 각 웨이브에 대한 수신자 선택 기준을 구성할 수 없습니다.

1. 배달 속성 창을 열고 **[!UICONTROL Delivery]** 탭을 클릭합니다.
1. 옵션을 **[!UICONTROL Send using multiple waves]** 선택하고 **[!UICONTROL Define waves...]** 링크를 클릭합니다.

   ![](assets/s_ncs_user_wizard_waves.png)

1. 파도를 구성하려면 다음 중 하나를 수행합니다.

   * 각 웨이브의 크기를 정의합니다. 예를 들어, 해당 **[!UICONTROL 30%]** 필드에 입력할 경우, 마지막 메시지를 제외하고, 전달에 포함된 메시지의 30%가 해당 메시지의 10%를 나타냅니다.

      필드에서 **[!UICONTROL Period]** 연속된 두 파도의 시작 사이의 지연을 지정합니다. 예를 들어, 첫 번째 **[!UICONTROL 2d]**&#x200B;파도가 즉시 시작되고, 두 번째 파도는 이틀 후 시작되고, 세 번째 파동은 4일 후에 시작됩니다.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 각 웨이브를 보낼 달력을 정의합니다.

      열에서 연속된 두 개의 파도 사이의 지연을 **[!UICONTROL Start]** 지정합니다. 열에 고정 숫자 또는 백분율을 **[!UICONTROL Size]** 입력합니다.

      아래 예에서 첫 번째 물결은 전달에 포함된 총 메시지 수의 25%를 나타내며 즉시 시작됩니다. 다음 두 번의 물결이 배달을 완료하고 6시간 간격으로 시작하도록 설정되어 있습니다.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   특정 유형 규칙, **[!UICONTROL Wave scheduling check]**&#x200B;마지막 물결이 배달 유효성 제한 전에 계획되도록 합니다. 배달 속성의 **[!UICONTROL Typology]** 탭에 구성된 캠페인 유형 및 해당 규칙은 유형 분류를 [포함하는 유효성 검사 프로세스에 표시됩니다](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!CAUTION]
   >
   >마지막 물결이 **[!UICONTROL Validity]** 탭에 정의된 배달 마감일을 초과하지 않도록 하십시오. 그렇지 않으면 일부 메시지가 전송되지 않을 수 있습니다.
   >
   >마지막 파도를 구성할 때 다시 시도할 시간도 충분해야 합니다. 이 [섹션을](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)참조하십시오.

1. 전송을 모니터링하려면 배달 로그로 이동합니다. 이 [페이지를](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)참조하십시오.

   이미 처리된 파도(**[!UICONTROL Sent]** 상태)에서 전송된 게재와 나머지 파도(**[!UICONTROL Pending]** 상태)에서 발송될 납품을 볼 수 있습니다.

아래 두 가지 예는 여러 파동을 사용하는 데 가장 일반적인 사용 사례입니다.

* **경사 과정 중**

   새 플랫폼을 사용하여 이메일을 전송하는 경우, 인터넷 서비스 제공업체(ISP)는 인식할 수 없는 IP 주소를 의심하고 있습니다. 대량의 이메일이 갑자기 전송되면 ISP는 종종 이메일을 스팸으로 표시합니다.

   스팸으로 표시되지 않도록 물결을 사용하여 전송된 양을 점진적으로 늘릴 수 있습니다. 이렇게 하면 시작 단계를 원활하게 개발하고 잘못된 주소의 전체 비율을 줄일 수 있습니다.

   이렇게 하려면 **[!UICONTROL Schedule waves according to a calendar]** 옵션을 사용합니다. 예를 들어 첫 번째 물결을 10%, 두 번째 물결을 15%로 설정하는 등의 작업을 수행합니다.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **콜 센터 관련 캠페인**

   전화 충성도 캠페인을 관리할 때 조직은 가입자에 대한 통화 수를 처리할 수 있는 제한된 용량을 갖습니다.

   웨이브를 사용하면 메시지 수를 하루 20개(콜 센터의 일일 처리 용량)로 제한할 수 있습니다.

   이렇게 하려면 **[!UICONTROL Schedule multiple waves of the same size]** 옵션을 선택합니다. 파도의 **[!UICONTROL 20]** 크기와 **[!UICONTROL 1d]** 필드에 입력합니다 **[!UICONTROL Period]** .

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 재시도 구성 {#configuring-retries}

소프트 또는 무시됨 **오류로 인해** 일시적으로 배달되지 않은 **메시지는** 자동 재시도가 적용됩니다. 배달 실패 유형 및 원인은 이 [섹션에](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)설명되어 있습니다.

배달 매개 변수에 대한 **[!UICONTROL Delivery]** 탭의 중앙 섹션은 배달 후 하루 동안 시도할 재시도 횟수와 재시도 사이의 최소 지연을 나타냅니다.

![](assets/s_ncs_user_wizard_retry_param.png)

기본적으로 5회 재시도 횟수는 배달 첫 날에 예약되며 최소 1시간 간격은 하루 24시간 동안 분산됩니다. 일별 1회 재시도는 그 후 **[!UICONTROL Validity]** 탭에 정의된 배달 마감일까지 프로그래밍됩니다(유효성 기간 [정의 참조](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)).

>[!NOTE]
>
>호스팅 또는 하이브리드 설치의 경우 향상된 MTA로 업그레이드한 경우, 게재의 재시도 설정은 더 이상 Campaign에서 사용되지 않습니다. 소프트 바운스 재시도와 그 사이의 시간은 메시지의 이메일 도메인에서 돌아오는 바운스 응답 유형 및 심각도에 따라 향상된 MTA에 의해 결정됩니다.
>
>모든 영향은 Adobe Campaign 향상된 [MTA 문서에 자세히](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) 설명되어 있습니다.


## 유효 기간 정의 {#defining-validity-period}

배달이 실행되면 메시지(및 재시도)는 배달 마감 시간까지 보낼 수 있습니다. 이것은 **[!UICONTROL Validity]** 탭을 통해 배달 속성에 표시됩니다.

![](assets/s_ncs_user_email_del_valid_period.png)

* 이 **[!UICONTROL Delivery duration]** 필드를 사용하면 글로벌 배달 재시도에 대한 제한을 입력할 수 있습니다. 즉, Adobe Campaign이 시작 날짜에 시작된 메시지를 보낸 다음, 오류를 반환하는 메시지의 경우 유효성 제한에 도달할 때까지 정기적으로 구성 가능한 재시도가 수행됩니다.

   날짜를 지정할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Explicitly set validity dates]**&#x200B;선택합니다. 이 경우 배달 및 유효성 제한 날짜도 시간을 지정할 수 있습니다. 현재 시간은 기본적으로 사용되지만 입력 필드에서 직접 수정할 수 있습니다.

* **리소스의**&#x200B;유효성 제한:이 **[!UICONTROL Validity limit]** 필드는 업로드된 리소스에 대해 주로 미러 페이지 및 이미지에 사용됩니다. 이 페이지의 리소스는 제한된 시간 동안 유효합니다(디스크 공간을 절약하려면).

   이 필드의 값은 [이 섹션에](../../platform/using/adobe-campaign-workspace.md#default-units)나열된 단위로 표시할 수 있습니다.

>[!NOTE]
>
>호스팅 또는 하이브리드 설치의 경우 향상된 MTA로 업그레이드한 경우 캠페인 전달의 **[!UICONTROL Delivery duration]** 설정은 **3.5** 일 이내로 설정된 경우에만 사용됩니다. 3.5일 이상의 값을 정의하면 고려되지 않습니다.
>
>모든 영향은 Adobe Campaign 향상된 [MTA 문서에 자세히](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) 설명되어 있습니다.
