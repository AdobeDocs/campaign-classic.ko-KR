---
product: campaign
title: 게재 구성 및 보내기
description: 게재를 구성하고 보내는 방법을 배웁니다
feature: Channel Configuration
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: d59e9f55275bac303a5ed1450bb28ef7fa0f84cd
workflow-type: tm+mt
source-wordcount: '1502'
ht-degree: 4%

---

# 게재 구성 및 보내기 {#configuring-and-sending-the-delivery}

![](../../assets/common.svg)

## 사용 권한{#delivery-permissions}

게재 소유자만 게재를 시작할 수 있습니다. 다른 연산자(또는 연산자 그룹)가 게재를 시작할 수 있도록 에서는 오퍼를 검토자로 추가합니다 **[!UICONTROL Delivery start:]** 필드. [자세히 알아보기](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)

## 게재 추가 매개 변수 {#delivery-additiona-parameters}

게재를 보내기 전에 를 통해 게재 속성에서 전송 매개 변수를 정의할 수 있습니다. **[!UICONTROL Delivery]** 탭.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: 우선순위 수준을 설정하여 게재의 전송 순서를 변경하려면 이 옵션을 사용하십시오. 보통, 높음 또는 낮음.

* **[!UICONTROL Message batch quantity]**: 동일한 XML 배달 패키지 내에 그룹화된 메시지 수를 정의하려면 이 옵션을 사용합니다. 매개 변수를 0으로 설정하면 메시지가 자동으로 그룹화됩니다. 패키지 크기는 계산에 의해 정의됩니다 `<delivery size>/1024`에는 패키지로 최대 256개의 메시지와 최소 8개의 메시지가 있습니다.

   >[!IMPORTANT]
   >
   >기존 매개 변수를 복제하여 게재를 만들면 이 매개 변수는 재설정됩니다.

* **[!UICONTROL Send using multiple waves]**: 이 옵션을 사용하여 메시지를 한 번에 전체 대상자가 아닌 일괄 처리로 보낼 수 있습니다. [자세히 알아보기](#sending-using-multiple-waves)

* **[!UICONTROL Test SMTP delivery]**: SMTP를 통한 전송을 테스트하려면 이 옵션을 사용합니다. 게재는 SMTP 서버에 대한 연결까지 처리되지만 전송되지 않습니다: 게재를 받는 모든 사람에 대해 Campaign은 SMTP 공급자 서버에 연결하고 SMTP RCPT TO 명령을 실행하고 SMTP DATA 명령 전에 연결을 닫습니다.

   >[!NOTE]
   >
   >* 중간 소싱에서 이 옵션을 설정하지 않아야 합니다.
   >
   >* SMTP 서버 구성에 대해 자세히 알아보기, in [이 섹션](../../installation/using/configure-delivery-settings.md).


* **[!UICONTROL Email BCC]**: 메시지 타겟에 숨은 참조 이메일 주소를 추가하면 BCC를 통해 외부 시스템에 이메일을 저장할 수 있습니다. [자세히 알아보기](sending-messages.md#archiving-emails)

## 게재 확인 {#confirming-delivery}

게재를 구성하고 전송할 준비가 되면 게재 분석을 실행합니다.

이렇게 하려면 **[!UICONTROL Send]**&#x200B;를 클릭하고 원하는 작업을 선택한 다음 를 클릭합니다. **[!UICONTROL Analyze]**. [자세히 알아보기](steps-validating-the-delivery.md#analyzing-the-delivery)

![](assets/s_ncs_user_email_del_send.png)

완료되면 을(를) 클릭합니다. **[!UICONTROL Confirm delivery]** 메시지 배달을 시작하려면 다음을 수행하십시오.

그런 다음 게재 마법사를 닫고 에서 게재 실행을 추적할 수 있습니다 **[!UICONTROL Delivery]** 탭으로서, 이 게재의 세부 사항 또는 게재 목록을 통해 액세스할 수 있습니다.

메시지를 보낸 후 게재를 모니터링하고 추적할 수 있습니다. 자세한 정보는 다음 섹션을 참조하십시오.

* [게재 모니터링](about-delivery-monitoring.md)
* [게재 실패 이해](understanding-delivery-failures.md)
* [메시지 추적 정보](about-message-tracking.md)

## 게재 전송 예약 {#scheduling-the-delivery-sending}

게재를 예약하여 메시지 전송을 연기할 수 있습니다.

1. 을(를) 클릭합니다. **[!UICONTROL Send]** 버튼을 클릭하고 **[!UICONTROL Postpone delivery]** 선택 사항입니다.

1. 에서 시작 날짜를 지정합니다. **[!UICONTROL Contact date]** 필드.

![](assets/dlv_email_del_plan.png)

1. 그런 다음 게재 분석을 시작한 다음 게재 전송을 확인할 수 있습니다. 그러나 게재 전송은 에 지정된 날짜까지 시작되지 않습니다 **[!UICONTROL Contact date]** 필드.

>[!IMPORTANT]
>
>분석을 시작하면 정의한 연락 날짜가 수정됩니다. 이 날짜를 수정하는 경우 수정 사항을 고려하도록 분석을 다시 시작해야 합니다.

![](assets/s_ncs_user_email_del_start_delayed.png)

게재 목록에 게재가 다음과 같이 나타납니다 **[!UICONTROL Pending]** 상태.

![](assets/s_ncs_user_email_del_waiting.png)

를 통해 업스트림으로 예약할 수도 있습니다 **[!UICONTROL Scheduling]** 게재의 단추입니다.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

게재를 나중 날짜로 연기하거나 임시 달력에 게재를 저장할 수 있습니다.

* 다음 **[!UICONTROL Schedule delivery (no automatic execution)]** 옵션을 사용하면 게재의 임시 분석을 예약할 수 있습니다.

   이 구성이 저장되면 게재가 **[!UICONTROL Targeting pending]** 상태. 지정된 날짜에 분석이 실행됩니다.

* 다음 **[!UICONTROL Schedule delivery (automatic execution on planned date)]** 옵션을 사용하면 배달 날짜를 지정할 수 있습니다.

   클릭 **[!UICONTROL Send]** 을(를) 선택합니다. **[!UICONTROL Postpone delivery]** 그런 다음 분석을 시작하고 게재를 확인합니다. 분석이 완료되면 게재 대상이 준비되고 지정된 날짜에 메시지가 자동으로 전송됩니다.

날짜와 시간은 현재 연산자의 시간대로 표시됩니다. 다음 **[!UICONTROL Time zone]** 연락 날짜 입력 필드 아래에 있는 드롭다운 목록을 사용하면 입력한 날짜 및 시간을 선택한 시간대로 자동으로 변환할 수 있습니다.

예를 들어, 런던 시간 8시에 게재를 자동으로 실행하도록 예약하는 경우 시간은 자동으로 선택한 시간대로 변환됩니다.

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 여러 웨이브를 사용하여 보내기 {#sending-using-multiple-waves}

로드 균형을 맞추기 위해 게재를 여러 개의 배치로 나눌 수 있습니다. 일괄 처리 수와 전체 게재와 관련된 해당 비율을 구성합니다.

>[!NOTE]
>
>두 연속된 웨이브 사이의 크기와 지연 사이의 크기만 정의할 수 있습니다. 각 파트에 대한 받는 사람 선택 기준을 구성할 수 없습니다.

1. 게재 속성 창을 열고 을(를) 클릭합니다. **[!UICONTROL Delivery]** 탭.
1. 을(를) 선택합니다 **[!UICONTROL Send using multiple waves]** 옵션을 선택하고 **[!UICONTROL Define waves...]** 링크를 클릭합니다.

   ![](assets/s_ncs_user_wizard_waves.png)

1. 웨이브를 구성하려면 다음 중 하나를 수행할 수 있습니다.

   * 각 웨이브의 크기를 정의합니다. 예를 들어, **[!UICONTROL 30%]** 해당 필드에서 각 파도는 메시지의 10%를 나타내는 마지막 파트를 제외하고 게재에 포함된 메시지의 30%를 나타냅니다.

      에서 **[!UICONTROL Period]** 필드, 두 개의 연속된 웨이브의 시작 사이의 지연 시간을 지정합니다. 예를 들어, **[!UICONTROL 2d]** 1차 파장은 즉시 시작되고, 2차 파동은 2일 후 시작되고, 3차 파동은 4일 후에 시작됩니다.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 각 웨이브를 전송할 달력을 정의합니다.

      에서 **[!UICONTROL Start]** 열에서 연속된 두 파도의 시작 사이의 지연 시간을 지정합니다. 에서 **[!UICONTROL Size]** 열에서 고정 번호 또는 백분율을 입력합니다.

      아래 예에서 첫 번째 물결은 게재에 포함된 총 메시지 수의 25%를 나타내며 즉시 시작됩니다. 다음 두 파도는 게재를 완료하고 6시간 간격으로 시작됩니다.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   특정 유형화 규칙, **[!UICONTROL Wave scheduling check]**&#x200B;를 사용하면 게재 유효성 제한 전에 마지막 물결이 계획되어 있는지 확인합니다. 캠페인 유형화 및 규칙이 **[!UICONTROL Typology]** 게재 속성의 탭에는 [유형화를 사용한 유효성 검사 프로세스](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >마지막 웨이브가 **[!UICONTROL Validity]** 탭. 그렇지 않으면 일부 메시지가 전송되지 않을 수 있습니다.
   >
   >마지막 웨이브를 구성할 때 다시 시도할 시간을 충분히 허용해야 합니다. [이 섹션](steps-sending-the-delivery.md#configuring-retries)을 참조하십시오.

1. 전송을 모니터링하려면 게재 로그로 이동합니다. [이 페이지](delivery-dashboard.md#delivery-logs-and-history)를 참조하십시오.

   이미 처리된 웨이브(**[!UICONTROL Sent]** 상태) 및 나머지 웨이브(**[!UICONTROL Pending]** 상태).

아래 두 가지 예는 여러 파도를 사용하는 가장 일반적인 사용 사례입니다.

* **램프 업 프로세스 중**

   새 플랫폼을 사용하여 이메일을 보낼 때 인터넷 서비스 공급자(ISP)는 인식되지 않는 IP 주소를 의심합니다. 대량의 이메일이 갑자기 전송되면 ISP는 종종 이메일을 스팸으로 표시합니다.

   스팸으로 표시되지 않도록 웨이브를 사용하여 보내는 볼륨을 점진적으로 늘릴 수 있습니다. 이렇게 하면 시작 단계의 개발이 원활해야 하며 잘못된 주소의 전체 비율을 줄일 수 있습니다.

   이렇게 하려면 를 사용하십시오 **[!UICONTROL Schedule waves according to a calendar]** 선택 사항입니다. 예를 들어, 첫 번째 물결을 10%로, 두 번째 물결에서 15% 등으로 설정합니다.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **콜 센터를 포함하는 캠페인**

   전화 충성도 캠페인을 관리할 때 조직은 구독자에게 연락할 수 있는 수를 처리할 수 있는 제한된 용량을 갖습니다.

   웨이브를 사용하면 메시지 수를 하루 20개로 제한할 수 있습니다. 이는 콜 센터의 일일 처리 용량입니다.

   이렇게 하려면 **[!UICONTROL Schedule multiple waves of the same size]** 선택 사항입니다. Enter 키 **[!UICONTROL 20]** 파도의 크기와 **[!UICONTROL 1d]** 에서 **[!UICONTROL Period]** 필드.

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 다시 시도 구성 {#configuring-retries}

다음 이유로 인해 일시적으로 게재되지 않은 메시지 **소프트** 또는 **무시됨** 오류가 발생하면 자동 다시 시도를 적용합니다. 게재 실패 유형 및 이유는 다음과 같습니다 [섹션](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우 로 업그레이드한 경우 [향상된 MTA](sending-with-enhanced-mta.md): 게재의 다시 시도 설정은 Campaign에서 더 이상 사용되지 않습니다. 소프트 바운스 다시 시도 및 그 사이의 시간은 메시지의 이메일 도메인에서 돌아오는 바운스 응답의 유형과 심각도를 기반으로 Enhanced MTA에 의해 결정됩니다.

기존 Campaign MTA를 사용하는 온-프레미스 설치 및 호스팅/하이브리드 설치의 경우, **[!UICONTROL Delivery]** 게재 매개 변수의 탭은 게재 다음 날에 수행되어야 하는 다시 시도 횟수와 다시 시도 사이의 최소 지연을 나타냅니다.

![](assets/s_ncs_user_wizard_retry_param.png)

기본적으로 게재 첫 날에 5번의 다시 시도가 예약되며 최소 1시간 간격은 24시간 동안 분산됩니다. 일별 1회 다시 시도는 그 후 및 게재 마감일까지 프로그램되며, 이것은 **[!UICONTROL Validity]** 탭. 자세한 내용은 [유효 기간 정의](#defining-validity-period).

## 유효 기간 정의 {#defining-validity-period}

게재를 시작하면 메시지(및 다시 시도)를 게재 마감일까지 보낼 수 있습니다. 게재 속성에, 을 통해 표시됩니다. **[!UICONTROL Validity]** 탭.

![](assets/s_ncs_user_email_del_valid_period.png)

* 다음 **[!UICONTROL Delivery duration]** 필드를 사용하면 글로벌 게재 다시 시도 제한을 입력할 수 있습니다. 즉, Adobe Campaign은 시작 날짜부터 메시지를 보낸 다음, 오류만 반환하는 메시지의 경우 유효성 제한에 도달할 때까지 정기적으로 구성 가능한 다시 시도가 수행됩니다.

   날짜를 지정하도록 선택할 수도 있습니다. 이렇게 하려면 을(를) 선택합니다. **[!UICONTROL Explicitly set validity dates]**. 이 경우 게재 및 유효성 제한 날짜도 시간을 지정할 수 있도록 해줍니다. 현재 시간은 기본적으로 사용되지만 입력 필드에서 직접 수정할 수 있습니다.

   >[!IMPORTANT]
   >
   >호스팅 또는 하이브리드 설치의 경우 로 업그레이드한 경우 [향상된 MTA](sending-with-enhanced-mta.md), **[!UICONTROL Delivery duration]** campaign 이메일 게재의 설정은 **3.5일 이하**. 3.5일 이상의 값을 정의하면 고려되지 않습니다.

* **리소스의 유효성 제한**: 다음 **[!UICONTROL Validity limit]** 필드는 주로 미러 페이지와 이미지에 대해 업로드된 리소스에 사용됩니다. 이 페이지의 리소스는 제한된 시간 동안 유효합니다(디스크 공간을 절약하기 위함).

   이 필드의 값은 [이 섹션](../../platform/using/adobe-campaign-workspace.md#default-units).
