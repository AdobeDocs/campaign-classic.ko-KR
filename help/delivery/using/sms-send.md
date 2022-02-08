---
product: campaign
title: SMS 전송, 모니터링 및 추적
description: Campaign에서 SMS를 전송, 모니터링 및 추적하는 방법을 알아봅니다
feature: SMS
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 3%

---

# SMS 게재 전송, 모니터링 및 추적{#sms-properties}

![](../../assets/common.svg)

## SMS 메시지 보내기 {#sending-sms-messages}

메시지를 승인하고 만들 게재 수신자에게 보내려면 **[!UICONTROL Send]**.

게재를 확인하고 전송할 때 세부 프로세스는 아래 섹션에 나와 있습니다.

* [게재 유효성 검사](steps-validating-the-delivery.md)
* [게재 보내기](steps-sending-the-delivery.md)

## 고급 매개 변수 {#advanced-parameters}

다음 **[!UICONTROL Properties]** 버튼을 사용하면 고급 게재 매개 변수에 액세스할 수 있습니다. SMS 게재와 관련된 매개 변수는 **[!UICONTROL SMS parameters]** 섹션 **[!UICONTROL Delivery]** 탭.

다음 옵션을 사용할 수 있습니다.

* **보낸 사람 주소**: 11자로 제한된 영숫자 문자열을 사용하여 게재 발신자의 이름을 개인화할 수 있습니다. 그 필드는 오직 숫자로 구성되어 있지 않아야 한다. 표시할 조건(예: 수신자의 영역 코드에 따라 다른 이름)을 정의할 수 있습니다.

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >발신자 이름 편집에 대한 해당 국가의 법률을 확인하십시오. 연산자가 이 기능을 제공하는지 여부도 확인해야 합니다.

* **전송 모드**: SMS를 통한 메시지 전송
* **우선순위**: 메시지에 할당된 중요도 수준입니다. **[!UICONTROL Normal]** 기본적으로 우선순위가 선택됩니다. 와 함께 보내는 SMS 비용에 대해 서비스 공급업체에 문의하십시오 **[!UICONTROL High]** 우선 순위.
* **애플리케이션 유형**: sms 게재에 할당할 애플리케이션을 선택합니다. 다음 **[!UICONTROL Direct Marketing]** 옵션은 기본적으로 선택되어 있으며 가장 일반적으로 사용되는 옵션입니다.

**NetSize 커넥터에 대한 매개 변수**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **단일 메시지에 여러 SMS 사용**: 따라서 여러 SMS 메시지를 통해 160자 이상의 메시지를 보낼 수 있습니다.

**SMPP 커넥터별 매개 변수**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **메시지당 최대 SMS 수**: 이 옵션을 사용하면 메시지를 보내는 데 사용할 SMS 수를 설정할 수 있습니다. 번호가 0으로 설정된 경우 SMS를 사용하여 메시지를 전달할 수 있습니다. 예를 들어 SMS 수가 1 또는 2로 설정되어 있고 메시지가 이 임계값을 초과하는 경우 전송되지 않습니다.

## SMS 모니터링 및 추적 {#monitoring-and-tracking-sms-deliveries}

메시지를 보낸 후 게재를 모니터링하고 추적할 수 있습니다. 자세한 정보는 다음 섹션을 참조하십시오.

* [게재 모니터링](about-delivery-monitoring.md)
* [게재 실패 이해](understanding-delivery-failures.md)
* [메시지 추적 정보](about-message-tracking.md)

## 인바운드 메시지 처리 {#processing-inbound-messages}

다음 **nlserver sms** 모듈은 정기적으로 SMS 라우터를 쿼리합니다. 이를 통해 Adobe Campaign은 게재 진행 상황을 추적하고 상태 보고서와 수신자 구독 취소 요청을 처리할 수 있습니다.

* **상태 보고서**: 게재 로그를 보고 메시지의 상태를 확인합니다.

   >[!NOTE]
   >
   >전송된 모든 SMS는 기본 키에 외부 계정에 연결됩니다. 이 방법은 다음과 같습니다.
   >
   > * 삭제된 외부 SMS 계정의 상태 보고서가 올바르게 처리되지 않습니다.
   > * SMS 계정은 하나의 외부 계정에만 연결하여 상태 보고서가 올바른 계정에 귀속되도록 할 수 있습니다


* **구독 취소**: SMS 게재 수신을 중지하려는 수신자는 STOP이라는 단어가 포함된 메시지를 반환할 수 있습니다. 공급자가 계약 조건에 따라 이를 허용하는 경우 **인바운드 SMS** 워크플로우 활동 을 만든 다음 쿼리를 만들어 **이 수신자에게 더 이상 연락하지 않음** 관련 수신자에 대한 옵션.

   자세한 내용은 [워크플로우](../../workflow/using/architecture.md) 안내서.

## InSMS 스키마 {#insms-schema}

InSMS 스키마에는 수신 SMS와 관련된 정보가 포함되어 있습니다. 이러한 필드에 대한 설명은 desc 속성을 통해 사용할 수 있습니다.

* **메시지**: 수신한 SMS 컨텐츠
* **원본**: 메시지 출처의 모바일 번호입니다.
* **providerId**: SMSC(메시지 센터)에서 반환한 메시지의 식별자입니다.
* **생성됨**: 받는 날짜 메시지가 Adobe Campaign에 삽입되었습니다.
* **extAccount**: Adobe Campaign 외부 계정.

   >[!IMPORTANT]
   >
   >다음 필드는 NetSize에만 적용됩니다.
   >
   >사용 중인 연산자가 NetSize가 아닌 경우 이러한 필드는 비어 있는 것으로 간주됩니다.

* **별칭**: 수신 메시지의 별칭.
* **구분 기호**: 별칭과 메시지 본문 사이의 구분자입니다.
* **messageDate**: 연산자가 제공한 메시지 날짜입니다.
* **receivvalDate**: SMSC(메시지 센터)에서 연산자로부터 날짜 메시지를 받았습니다.
* **deliveryDate**: SMSC에서 보낸 날짜 메시지(메시지 센터).
* **largeAccount**: 수신 SMS에 연결된 고객 계정 코드
* **countryCode**: 운영자 국가 코드.
* **operatorCode**: 운영자 네트워크 코드.
* **linkedSmsId**: 보내는 SMS에 연결된 Adobe Campaign 식별자(broadlogId)입니다. 여기서 이 SMS가 응답입니다.

## 자동 회신 관리(미국 규정) {#managing-automatic-replies--american-regulation-}

구독자가 Adobe Campaign을 통해 보낸 SMS 메시지에 회신하고 STOP, HELP 또는 YES와 같은 키워드를 사용하는 경우, 미국 시장에서 자동으로 반환되는 메시지를 구성하기 위해 필요합니다.

예를 들어 수신자가 키워드 STOP을 보낼 경우 구독 취소되었음을 나타내는 확인 메시지를 자동으로 수신합니다.

이 유형의 메시지에 대한 발신자 이름은 일반적으로 게재를 보내는 데 사용되는 짧은 코드입니다.

>[!IMPORTANT]
>
>다음 세부 절차는 확장된 일반 SMPP 커넥터를 제외하고 SMPP 커넥터에만 유효합니다. 자세한 내용은 [SMPP 외부 계정 만들기](sms-set-up.md#creating-an-smpp-external-account) 섹션을 참조하십시오.
>
>미국 마케팅 캠페인에서 미국 운영자들이 수행하는 인증 과정의 일부를 구성합니다. 이 키워드가 포함된 가입자 SMS에 대한 이러한 회신은 메시지를 받은 직후 가입자에게 전송해야 한다.

1. 다음 유형의 XML 파일을 만듭니다.

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. 대상 **이름** 의 속성 **`<shortcode>`** 태그에서 메시지를 보낸 사람 이름 앞에 표시할 짧은 코드를 지정합니다.

   각 **`<reply>`** 태그를 지정하고 **키워드** 키워드 및 **텍스트** 이 키워드에 전송할 메시지와 함께 속성을 사용합니다.

   >[!NOTE]
   >
   >각 키워드는 대문자로 써야 한다.

   여러 키워드에 대해 동일한 메시지를 보내려면 해당 줄을 복제합니다.

   예제:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 완료되면 이 파일을 이름으로 저장합니다 **smsAutoReply.xml**.

   파일 이름은 Linux에서 대/소문자를 구분합니다.

1. 이 파일을 **conf** 웹 서버와 동일한 위치에 있는 Adobe Campaign의 디렉토리입니다.

>[!IMPORTANT]
>
>이런 종류의 자동 메시지는 기록되지 않는다. 따라서 게재 대시보드에 표시되지 않습니다. [자세히 알아보기](delivery-dashboard.md)
>
>이 메시지들은 상업적인 압력 규정에서 고려하지 않는다. [자세히 알아보기](../../campaign-opt/using/pressure-rules.md)
