---
product: campaign
title: SMS 전송, 모니터링 및 추적
description: Campaign에서 SMS를 보내고, 모니터링하고, 추적하는 방법에 대해 알아보기
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 3%

---

# SMS 게재 보내기, 모니터링 및 추적{#sms-properties}

## SMS 메시지 보내기 {#sending-sms-messages}

메시지를 승인하고 작성 중인 게재의 수신자에게 보내려면 **[!UICONTROL Send]**.

게재의 유효성을 검사하고 전송할 때 자세한 프로세스는 아래 섹션에 나와 있습니다.

* [게재 유효성 검사](steps-validating-the-delivery.md)
* [게재 보내기](steps-sending-the-delivery.md)

## 고급 매개 변수 {#advanced-parameters}

다음 **[!UICONTROL Properties]** 버튼을 사용하면 고급 게재 매개 변수에 액세스할 수 있습니다. SMS 게재와 관련된 매개 변수는 **[!UICONTROL SMS parameters]** 의 섹션 **[!UICONTROL Delivery]** 탭.

다음 옵션을 사용할 수 있습니다.

* **보낸 사람 주소**: 11자로 제한된 영숫자 문자열을 사용하여 게재 발신자의 이름을 개인화할 수 있습니다. 그 분야는 오로지 수치로만 구성되어서는 안 된다. 예를 들어 수신자의 지역 코드에 따라 다른 이름을 표시할 조건을 정의할 수 있습니다.

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >보낸 사람 이름 편집에 대해서는 해당 국가의 법을 확인하십시오. 또한 운영자가 이 기능을 제공하는지 여부를 확인해야 합니다.

* **전송 모드**: SMS를 통한 메시지 전송.
* **우선 순위**: 메시지에 할당된 중요도 수준입니다. **[!UICONTROL Normal]** 기본적으로 우선 순위가 선택되어 있습니다. 서비스 공급업체에 SMS 전송 비용에 대해 문의 **[!UICONTROL High]** 우선 순위.
* **애플리케이션 유형**: SMS 게재에 할당할 애플리케이션을 선택합니다. 다음 **[!UICONTROL Direct Marketing]** 옵션은 기본적으로 선택되어 있으며 가장 일반적으로 사용됩니다.

**NetSize 커넥터와 관련된 매개 변수**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **단일 메시지에 여러 SMS 사용**: 여러 SMS 메시지를 통해 160자 이상의 메시지를 보낼 수 있습니다.

**SMPP 커넥터와 관련된 매개변수**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **메시지당 최대 SMS 수**: 이 옵션을 사용하면 메시지를 보내는 데 사용할 SMS 수를 설정할 수 있습니다. 이 수를 0으로 설정하면 SMS를 사용하여 메시지를 전달할 수 있습니다. 예를 들어 SMS 수가 1 또는 2로 설정되어 있고 메시지가 이 임계값을 초과하는 경우 전송되지 않습니다.

## SMS 모니터링 및 추적 {#monitoring-and-tracking-sms-deliveries}

메시지를 보낸 후 게재를 모니터링하고 추적할 수 있습니다. 자세한 정보는 다음 섹션을 참조하십시오.

* [게재 모니터링](about-delivery-monitoring.md)
* [게재 실패 이해](understanding-delivery-failures.md)
* [메시지 추적 정보](about-message-tracking.md)

## 인바운드 메시지 처리 {#processing-inbound-messages}

다음 **nlserver sms** 모듈이 정기적으로 SMS 라우터를 쿼리합니다. 이를 통해 Adobe Campaign은 게재 진행 상황을 추적하고 상태 보고서 및 수신자 구독 취소 요청을 처리할 수 있습니다.

* **상태 보고서**: 게재 로그를 보고 메시지 상태를 확인합니다.

  >[!NOTE]
  >
  >전송된 모든 SMS는 기본 키로 외부 계정에 연결됩니다. 이러한 방식으로:
  >
  > * 삭제된 외부 SMS 계정의 상태 보고서가 올바르게 처리되지 않습니다.
  > * SMS 계정은 상태 보고서가 올바른 계정에 귀속되도록 단일 외부 계정에만 연결할 수 있습니다

* **구독 취소**: SMS 게재 수신을 중단하려는 수신자는 STOP이라는 단어가 포함된 메시지를 반환할 수 있습니다. 공급자가 계약 조건에 따라 허용하는 경우 **인바운드 SMS** 워크플로우 활동을 활성화한 다음 쿼리를 만들어 **더 이상 이 수신자에게 연락하지 않음** 관련 수신자에 대한 옵션입니다.

  다음을 참조하십시오. [워크플로](../../workflow/using/architecture.md) 가이드.

## InSMS 스키마 {#insms-schema}

InSMS 스키마에는 수신 SMS와 관련된 정보가 포함되어 있습니다. 이러한 필드에 대한 설명은 desc 속성을 통해 사용할 수 있습니다.

* **메시지**: 받은 SMS의 콘텐츠.
* **원본**: 메시지 출처의 모바일 번호입니다.
* **providerId**: SMSC(메시지 센터)에서 반환된 메시지의 식별자입니다.
* **생성됨**: 날짜 수신 메시지가 Adobe Campaign에 삽입되었습니다.
* **extAccount**: Adobe Campaign 외부 계정입니다.

  >[!IMPORTANT]
  >
  >다음 필드는 NetSize에만 해당됩니다.
  >
  >사용 중인 연산자가 NetSize가 아닌 경우 이러한 필드는 비어 있는 것으로 간주됩니다.

* **별칭**: 수신 메시지의 별칭입니다.
* **분리자**: 별칭과 메시지 본문 사이의 구분 기호입니다.
* **messageDate**: 연산자가 제공한 메시지 날짜입니다.
* **receivalDate**: 연산자의 날짜 메시지를 SMSC(메시지 센터)가 수신했습니다.
* **deliveryDate**: SMSC(메시지 센터)가 보낸 날짜 메시지.
* **큰 계정**: 수신 SMS에 연결된 고객 계정 코드.
* **countryCode**: 연산자 국가 코드.
* **operatorCode**: 운영자 네트워크 코드.
* **linkedSmsId**: 발신 SMS에 연결된 Adobe Campaign 식별자(broadlogId). 여기서 이 SMS는 응답입니다.

## 자동 회신 관리(미국 규정) {#managing-automatic-replies--american-regulation-}

구독자가 Adobe Campaign을 통해 보낸 SMS 메시지에 회신하고 STOP, HELP 또는 YES와 같은 키워드를 사용하는 경우, 미국 시장에서 자동으로 반환되는 메시지를 구성해야 합니다.

예를 들어 수신자가 STOP 키워드를 전송하는 경우 자동으로 구독을 취소했다는 확인 메시지를 수신합니다.

이 유형의 메시지에 대한 발신자 이름은 보통 게재를 보내는 데 사용되는 짧은 코드입니다.

>[!IMPORTANT]
>
>다음 세부 절차는 확장된 일반 SMPP 커넥터를 제외하고 SMPP 커넥터에만 유효합니다. 자세한 내용은 [SMPP 외부 계정 만들기](sms-set-up.md#creating-an-smpp-external-account) 섹션.
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

1. 의 경우 **이름** 속성 **`<shortcode>`** 태그를 지정한 다음 메시지 발신자 이름 위치에 표시할 짧은 코드를 지정합니다.

   각 항목 **`<reply>`** 태그를 입력한 후 **키워드** 키워드 및 이 있는 속성 **텍스트** 이 키워드로 보낼 메시지의 특성입니다.

   >[!NOTE]
   >
   >각 키워드는 대문자로 작성해야 합니다.

   여러 키워드에 대해 동일한 메시지를 보내려면 해당 줄을 복제합니다.

   예제:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 완료되면 이 파일을 이름으로 저장합니다. **smsAutoReply.xml**.

   Linux에서 파일 이름은 대소문자를 구분합니다.

1. 이 파일을 **conf** 웹 서버와 동일한 Adobe Campaign의 디렉터리입니다.

>[!IMPORTANT]
>
>이러한 종류의 자동 메시지는 기록을 보관하지 않습니다. 따라서 게재 대시보드에 표시되지 않습니다. [자세히 알아보기](delivery-dashboard.md)
>
>상업적 압력 규칙에서는 이러한 메시지가 고려되지 않습니다. [자세히 알아보기](../../campaign-opt/using/pressure-rules.md)
