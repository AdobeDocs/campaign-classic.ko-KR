---
product: campaign
title: 게재 구성 및 보내기
description: 게재를 구성하고 보내는 방법 알아보기
feature: Channel Configuration
role: User
hide: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
TQID: 'https://experienceleague.adobe.com/-Wh-pHFGE1kTId3t6g7wVJFfSvh2W5ERHi2K5-0Ohdw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b4ecd69f-2adf-4219-bc47-c9cd9a53c118
    internal-label: Channel configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 18%
---
# 게재 구성 및 보내기 {#configuring-and-sending-the-delivery}

이 페이지에서는 Campaign Classic v7의 온-프레미스 및 하이브리드 설치와 관련된 게재 전송 설정에 대해 설명합니다.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 게재 전송 설정에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}

## 게재 추가 매개 변수 {#delivery-additiona-parameters}

게재를 보내기 전에 **[!UICONTROL Delivery]** 탭을 통해 게재 속성에서 전송 매개 변수를 정의할 수 있습니다.

* **[!UICONTROL Test SMTP delivery]**: SMTP를 통한 전송을 테스트하려면 이 옵션을 사용하십시오. 게재는 SMTP 서버에 연결될 때까지 처리되지만 전송되지는 않습니다. 게재의 모든 수신자에 대해 Campaign은 SMTP 공급자 서버에 연결하고 SMTP RCPT TO 명령을 실행한 다음 SMTP DATA 명령 전에 연결을 종료합니다.

  >[!NOTE]
  >
  >* 중간 소싱에서는 이 옵션을 설정하지 않아야 합니다.
  >
  >* [이 섹션](../../installation/using/configure-delivery-settings.md)에서 SMTP 서버 구성에 대해 자세히 알아보세요.

## 다시 시도 구성 {#configuring-retries}

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

  >[!IMPORTANT]
  >
  >호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](sending-with-enhanced-mta.md)(으)로 업그레이드한 경우 Campaign 이메일 게재의 **[!UICONTROL Delivery duration]** 설정은 **3.5일 이하**(으)로 설정된 경우에만 사용됩니다. 3.5일 이상의 값을 정의하면 고려되지 않습니다.

* **리소스의 유효성 제한**: **[!UICONTROL Validity limit]** 필드는 주로 미러 페이지와 이미지에 대해 업로드된 리소스에 사용됩니다. 이 페이지의 리소스는 제한된 시간 동안 유효합니다(디스크 공간을 절약하기 위함).

  이 필드의 값은 다음 단위로 표현할 수 있습니다. **s**(초), **m**(분), **h**(시간), **d**(일)(기본값), **y**(년).
