---
product: campaign
title: SMS 전송, 모니터링 및 추적
description: Campaign에서 SMS를 보내고, 모니터링하고, 추적하는 방법에 대해 알아보기
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 1%

---

# 추가 구성{#sms-properties}

<!--
## Send SMS messages {#sending-sms-messages}

To approve your message and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validate the delivery](steps-validating-the-delivery.md)
* [Send the delivery](steps-sending-the-delivery.md)
-->

## 고급 매개 변수 {#advanced-parameters}

**[!UICONTROL Properties]** 단추를 사용하면 고급 배달 매개 변수에 액세스할 수 있습니다. SMS 게재와 관련된 매개 변수는 **[!UICONTROL SMS parameters]** 탭의 **[!UICONTROL Delivery]** 섹션에 있습니다.

다음 옵션을 사용할 수 있습니다.

* **보낸 사람 주소**: 11자로 제한된 영숫자 문자열을 사용하여 배달 보낸 사람의 이름을 개인화할 수 있습니다. 그 분야는 오로지 수치로만 구성되어서는 안 된다. 예를 들어 수신자의 지역 코드에 따라 다른 이름을 표시할 조건을 정의할 수 있습니다.

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >보낸 사람 이름 편집에 대해서는 해당 국가의 법을 확인하십시오. 또한 운영자가 이 기능을 제공하는지 여부를 확인해야 합니다.

* **전송 모드**: SMS로 메시지를 전송합니다.
* **우선 순위**: 메시지에 할당된 중요도 수준입니다. 기본적으로 **[!UICONTROL Normal]** 우선 순위가 선택되어 있습니다. 서비스 공급업체에 **[!UICONTROL High]** 우선 순위로 보낸 SMS 비용에 대해 문의하십시오.
* **응용 프로그램 유형**: SMS 게재에 할당할 응용 프로그램을 선택합니다. **[!UICONTROL Direct Marketing]** 옵션은 기본적으로 선택되어 있으며 가장 일반적으로 사용됩니다.

**NetSize 커넥터와 관련된 매개 변수**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **단일 메시지에 여러 SMS 사용**: 여러 SMS 메시지를 통해 160자를 초과하는 메시지를 보낼 수 있습니다.

**SMPP 커넥터와 관련된 매개 변수**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **메시지당 최대 SMS 수**: 이 옵션을 사용하면 메시지를 보내는 데 사용할 SMS 수를 설정할 수 있습니다. 이 수를 0으로 설정하면 SMS를 사용하여 메시지를 전달할 수 있습니다. 예를 들어 SMS 수가 1 또는 2로 설정되어 있고 메시지가 이 임계값을 초과하는 경우 전송되지 않습니다.

<!--
## Monitor and track SMS {#monitoring-and-tracking-sms-deliveries}

After sending messages, you can monitor and track your deliveries. For more on this, refer to these sections:

* [Monitor a delivery](about-delivery-monitoring.md)
* [Understand delivery failures](understanding-delivery-failures.md)
* [About message tracking](about-message-tracking.md)
-->

## 인바운드 메시지 처리 {#processing-inbound-messages}

**nlserver sms** 모듈이 정기적으로 SMS 라우터를 쿼리합니다. 이를 통해 Adobe Campaign은 게재 진행 상황을 추적하고 상태 보고서 및 수신자 구독 취소 요청을 처리할 수 있습니다.

* **상태 보고서**: 게재 로그를 보고 메시지 상태를 확인합니다.

  >[!NOTE]
  >
  >전송된 모든 SMS는 기본 키로 외부 계정에 연결됩니다. 이러한 방식으로:
  >
  > * 삭제된 외부 SMS 계정의 상태 보고서가 올바르게 처리되지 않습니다.
  > * SMS 계정은 상태 보고서가 올바른 계정에 귀속되도록 단일 외부 계정에만 연결할 수 있습니다

* **구독 취소**: SMS 게재 수신을 중지하려는 수신자는 STOP이라는 단어가 포함된 메시지를 반환할 수 있습니다. 공급자가 계약 조건에 따라 허용하는 경우 **인바운드 SMS** 워크플로우 활동을 통해 메시지를 검색한 다음 관련 받는 사람에 대해 **이 받는 사람에게 더 이상 연락하지 않음** 옵션을 사용하도록 설정하는 쿼리를 만들 수 있습니다.

## InSMS 스키마 {#insms-schema}

InSMS 스키마에는 수신 SMS와 관련된 정보가 포함되어 있습니다. 이러한 필드에 대한 설명은 desc 속성을 통해 사용할 수 있습니다.

* **message**: 받은 SMS 콘텐츠.
* **원본**: 메시지 원본의 휴대폰 번호입니다.
* **providerId**: SMSC(메시지 센터)에서 반환된 메시지의 식별자입니다.
* **생성됨**: 날짜 수신 메시지가 Adobe Campaign에 삽입되었습니다.
* **extAccount**: Adobe Campaign 외부 계정입니다.

  >[!IMPORTANT]
  >
  >다음 필드는 NetSize에만 해당됩니다.
  >
  >사용 중인 연산자가 NetSize가 아닌 경우 이러한 필드는 비어 있는 것으로 간주됩니다.

* **별칭**: 받는 메시지의 별칭입니다.
* **구분 기호**: 별칭과 메시지 본문 사이의 구분 기호입니다.
* **messageDate**: 연산자가 제공한 메시지 날짜입니다.
* **receiveDate**: 연산자의 날짜 메시지를 SMSC(메시지 센터)에서 받았습니다.
* **deliveryDate**: SMSC(메시지 센터)에서 보낸 날짜 메시지입니다.
* **largeAccount**: 수신 SMS에 연결된 고객 계정 코드입니다.
* **countryCode**: 연산자 국가 코드입니다.
* **operatorCode**: 연산자 네트워크 코드입니다.
* **linkedSmsId**: 발신 SMS에 연결된 Adobe Campaign 식별자(broadlogId)입니다. 여기서 이 SMS는 응답입니다.

## 자동 회신 관리(미국 규정) {#managing-automatic-replies--american-regulation-}

구독자가 Adobe Campaign을 통해 보낸 SMS 메시지에 회신하고 STOP, HELP 또는 YES와 같은 키워드를 사용하는 경우, 미국 시장에서 자동으로 반환되는 메시지를 구성해야 합니다.

예를 들어 수신자가 STOP 키워드를 전송하는 경우 자동으로 구독을 취소했다는 확인 메시지를 수신합니다.

이 유형의 메시지에 대한 발신자 이름은 보통 게재를 보내는 데 사용되는 짧은 코드입니다.

>[!IMPORTANT]
>
>다음 세부 절차는 확장된 일반 SMPP 커넥터를 제외하고 SMPP 커넥터에만 유효합니다. 자세한 내용은 [SMPP 외부 계정 만들기](sms-set-up.md#creating-an-smpp-external-account) 섹션을 참조하십시오.
>
>미국 내 마케팅 캠페인을 위해 미국 사업자가 수행하는 인증 프로세스의 일부를 구성하고 있다. 키워드가 포함된 구독자 SMS 메시지에 대한 회신은 구독자로부터 메시지를 받은 후 즉시 구독자에게 다시 전송해야 합니다.

1. 다음 유형의 XML 파일 만들기:

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

1. **태그의** name **`<shortcode>`** 특성에 대해 보낸 사람 이름 대신 표시할 짧은 코드를 지정하십시오.

   각 **`<reply>`** 태그에서 키워드가 있는 **keyword** 특성과 이 키워드에 보낼 메시지가 있는 **text** 특성을 입력하십시오.

   >[!NOTE]
   >
   >각 키워드는 대문자로 작성해야 합니다.

   여러 키워드에 대해 동일한 메시지를 보내려면 해당 줄을 복제합니다.

   예제:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 완료되면 이 파일을 **smsAutoReply.xml**(으)로 저장하십시오.

   Linux에서 파일 이름은 대소문자를 구분합니다.

1. 이 파일을 웹 서버와 같은 Adobe Campaign의 **conf** 디렉터리에 복사합니다.

>[!IMPORTANT]
>
>이러한 종류의 자동 메시지는 기록을 보관하지 않습니다. 따라서 게재 대시보드에 표시되지 않습니다. [자세히 알아보기](delivery-dashboard.md)
>
>상업적 압력 규칙에서는 이러한 메시지가 고려되지 않습니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/pressure-rules.html?lang=ko){target="_blank"}를 참조하세요.
