---
solution: Campaign Classic
product: campaign
title: SMS 전송, 모니터링 및 추적
description: Campaign에서 SMS를 전송, 모니터링 및 추적하는 방법을 알아봅니다.
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 1%

---


# SMS 배달 전송, 모니터링 및 추적{#sms-properties}

## SMS 메시지 전송 {#sending-sms-messages}

메시지를 승인하고 만드는 배달의 받는 사람에게 메시지를 보내려면 **[!UICONTROL Send]**&#x200B;을 클릭합니다.

게재의 유효성을 확인하고 전송할 때의 자세한 프로세스는 아래 섹션에 있습니다.

* [배달 유효성 확인](../../delivery/using/steps-validating-the-delivery.md)
* [배달 보내기](../../delivery/using/steps-sending-the-delivery.md)

## 고급 매개 변수 {#advanced-parameters}

**[!UICONTROL Properties]** 단추를 사용하면 고급 배달 매개 변수에 액세스할 수 있습니다. SMS 게재와 관련된 매개 변수는 **[!UICONTROL Delivery]** 탭의 **[!UICONTROL SMS parameters]** 섹션에 있습니다.

다음 옵션을 사용할 수 있습니다.

* **보낸 사람 주소**:11자로 제한된 영숫자 문자열을 사용하여 배달 보낸 사람의 이름을 개인화할 수 있습니다. 그 분야는 숫자만 가지고 있지 않아야 한다. 표시할 조건(예: 수신자의 영역 코드에 따라 다른 이름)을 정의할 수 있습니다.

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >발신자 이름 편집과 관련하여 해당 국가의 법률을 확인하십시오. 이 기능을 제공하는지 여부를 운영자도 확인해야 합니다.

* **전송 모드**:SMS로 메시지 전송
* **우선 순위**:메시지에 할당된 중요도 수준입니다. **[!UICONTROL Normal]** 우선 순위는 기본적으로 선택됩니다. 서비스 공급업체에 **[!UICONTROL High]** 우선 순위와 함께 보낸 SMS 비용을 문의하십시오.
* **응용 프로그램** 유형:SMS 전달에 할당할 애플리케이션을 선택합니다. **[!UICONTROL Direct Marketing]** 옵션은 기본적으로 선택되어 있으며 가장 일반적으로 사용되는 옵션입니다.

**NetSize 커넥터에 대한 매개 변수**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **단일 메시지에 여러 SMS를 사용합니다**.여러 SMS 메시지를 통해 160자 이상의 메시지를 보낼 수 있습니다.

**SMPP 커넥터에 대한 매개 변수**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **메시지당 최대 SMS 수**:이 옵션을 사용하면 메시지를 보내는 데 사용할 SMS 수를 설정할 수 있습니다. 번호가 0으로 설정된 경우 SMS를 사용하여 메시지를 전달할 수 있습니다. 예를 들어 SMS 수가 1이나 2로 설정되어 있고 메시지가 이 임계값을 초과하는 경우 전송되지 않습니다.

## SMS {#monitoring-and-tracking-sms-deliveries} 모니터링 및 추적

메시지를 보낸 후 배달을 모니터링하고 추적할 수 있습니다. 자세한 정보는 다음 섹션을 참조하십시오.

* [배달 모니터링](../../delivery/using/about-delivery-monitoring.md)
* [배달 오류 이해](../../delivery/using/understanding-delivery-failures.md)
* [메시지 추적 기본 정보](../../delivery/using/about-message-tracking.md)

## 인바운드 메시지 처리 {#processing-inbound-messages}

**nlserver sms** 모듈은 정기적으로 SMS 라우터를 쿼리합니다. 이를 통해 Adobe Campaign은 게재 진행 상황을 추적하고 상태 보고서와 수신자 구독 취소 요청을 처리할 수 있습니다.

* **상태 보고서**:배달 로그를 확인하여 메시지 상태를 확인합니다.

   >[!NOTE]
   >
   >전송된 모든 SMS는 기본 키로 외부 계정에 연결됩니다. 이 방법으로 다음을 수행합니다.
   >
   > * 삭제된 외부 SMS 계정의 상태 보고서가 올바르게 처리되지 않습니다.
   > * SMS 계정은 상태 보고서가 올바른 계정에 속하도록 단일 외부 계정에만 연결할 수 있습니다


* **구독 취소**:SMS 배달 알림을 받지 않으려면 STOP이라는 단어가 포함된 메시지를 반환할 수 있습니다. 공급자가 계약 조항에 따라 메시지를 허용하는 경우 **인바운드 SMS** 워크플로 활동을 통해 메시지를 검색한 다음 쿼리를 작성하여 해당 수신자에게 **더 이상 연락하지 않음** 옵션을 사용하도록 할 수 있습니다.

   [워크플로](../../workflow/using/architecture.md) 안내서를 참조하십시오.

## InSMS 스키마 {#insms-schema}

InSMS 스키마는 들어오는 SMS와 관련된 정보를 포함합니다. 이러한 필드에 대한 설명은 desc 속성을 통해 사용할 수 있습니다.

* **메시지**:수신한 SMS 컨텐츠
* **원본**:메시지의 원본에서 모바일 번호입니다.
* **providerId**:SMSC(메시지 센터)가 반환하는 메시지의 식별자입니다.
* **만든 날짜**:수신 메시지 날짜가 Adobe Campaign에 삽입되었습니다.
* **extAccount**:Adobe Campaign 외부 계정.

   >[!IMPORTANT]
   >
   >다음 필드는 NetSize에만 적용됩니다.
   >
   >사용 중인 연산자가 NetSize가 아닌 경우 이러한 필드는 비어 있는 것으로 간주됩니다.

* **별칭**:수신 메시지의 별칭입니다.
* **구분 기호**:메시지의 별칭과 본문 사이의 구분 기호.
* **messageDate**:연산자가 제공한 메시지 날짜입니다.
* **receivvalDate**:SMSC(메시지 센터)에서 연산자의 날짜 메시지를 받았습니다.
* **deliveryDate**:SMSC가 보낸 날짜 메시지(메시지 센터).
* **largeAccount**:수신 SMS에 연결된 고객 계정 코드
* **countryCode**:연산자 국가 코드.
* **operatorCode**:연산자 네트워크 코드.
* **linkedSmsId**:이 SMS가 응답인 나가는 SMS에 연결된 Adobe Campaign 식별자(broadlogId)입니다.

## 자동 답글 관리(미국 규정) {#managing-automatic-replies--american-regulation-}

Adobe Campaign을 통해 전송한 SMS 메시지에 댓글을 단 구독자가 STOP, HELP 또는 YES 등의 키워드를 사용하는 경우 미국 시장에서 자동으로 반환되는 메시지를 구성해야 합니다.

예를 들어 수신자가 키워드 STOP을 보내면 구독 취소되었음을 알리는 확인 메시지가 자동으로 수신됩니다.

이 유형의 메시지에 대한 보낸 사람 이름은 일반적으로 배달을 보내는 데 사용되는 짧은 코드입니다.

>[!IMPORTANT]
>
>다음 세부 절차는 확장된 범용 SMPP 커넥터를 제외한 SMPP 커넥터에만 유효합니다. 자세한 내용은 [SMPP 외부 계정 만들기](sms-set-up.md#creating-an-smpp-external-account) 섹션을 참조하십시오.
>
>이것은 미국 마케팅 캠페인에 대해 미국 운영자들이 수행하는 인증 과정의 일부를 차지한다. 이 키워드가 포함된 가입자 SMS 메시지에 대한 이러한 응답은 수신자가 메시지를 받은 즉시 가입자에게 전송해야 합니다.

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

1. **`<shortcode>`** 태그의 **name** 특성에 대해 메시지 보낸 사람 이름 대신 표시할 짧은 코드를 지정합니다.

   각 **`<reply>`** 태그에 **키워드** 속성과 **text** 속성을 이 키워드에 대해 보낼 메시지와 함께 입력합니다.

   >[!NOTE]
   >
   >각 키워드는 대문자로 작성해야 합니다.

   여러 키워드에 대해 동일한 메시지를 보내려면 해당 줄을 복제합니다.

   예제:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 완료되면 **smsAutoReply.xml** 이름으로 이 파일을 저장합니다.

   파일 이름은 Linux에서 대/소문자를 구분합니다.

1. 이 파일을 웹 서버와 동일한 위치에 있는 Adobe Campaign의 **conf** 디렉토리로 복사합니다.

>[!IMPORTANT]
>
>이런 자동 메시지는 역사를 보존하지 않는다. 따라서 배달 대시보드에 나타나지 않습니다. [자세히 알아보기](../../delivery/using/delivery-dashboard.md)
>
>이러한 메시지는 상업적인 압력 규정에 고려되지 않습니다. [자세히 알아보기](../../campaign/using/pressure-rules.md)
