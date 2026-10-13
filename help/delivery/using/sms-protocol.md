---
product: campaign
title: SMS 커넥터 프로토콜 및 설정
description: SMS 커넥터에 대한 자세한 내용 및 구성 방법 알아보기
feature: SMS
role: Developer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
TQID: 'https://experienceleague.adobe.com/-e39I2kK3veYtZTufN0ZZrnZPAAco47dU8HFlCtlIxY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
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
  - id: b1bd1421-1927-4c59-9bc6-ce292360e43b
    internal-label: SMS Messaging
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '4785'
ht-degree: 1%
---
# SMS 커넥터 프로토콜 및 설정 {#sms-connector-protocol}

>[!NOTE]
>
>이 문서를 통해 프로토콜, 필드 이름 및 값에 대한 세부 정보에 대한 모든 참조는 [SMPP 3.4 사양](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)을 참조합니다.
>

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. SMS 커넥터 설정에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}

## 개요 {#overview}

SMS는 형식이 지정되지 않은 짧은 텍스트 메시지로 제한적일 수 있지만 SMS의 간소화는 귀중한 통신 채널로 사용됩니다.

SMS를 보내는 주요 방법에는 두 가지가 있습니다.

* 사람들 간에 직접 통신하는 일반적인 방법인 휴대폰에서 수동으로 보냅니다.
* Adobe Campaign에서 메시지를 보내는 방식인 인터넷에서 보냅니다. 이를 위해서는 인터넷을 모바일 네트워크에 연결하는 SMS 서비스 공급자가 필요합니다.
Adobe Campaign은 SMPP 프로토콜을 사용하여 서비스 공급자에게 SMS를 전송합니다.

이 문서는 Adobe Campaign과 SMPP 공급자 간에 설정된 연결을 설명합니다.

SMPP 공급자는 때때로 공식 사양을 벗어날 수 있지만 Adobe Campaign의 SMS 커넥터는 대부분의 공급자와 호환되도록 동작을 조정하는 다양한 옵션을 제공합니다.

>[!IMPORTANT]
>
>새 공급자에 대한 연결을 설정하려면 TCP, 이진, 16진수 표현 및 텍스트 인코딩에 대한 기술 지식 및 몇 가지 기술이 필요할 수 있습니다. 또한 제공자와의 적극적인 협력이 필요할 것이다.

## SMPP 프로토콜 {#smpp-protocol}

Adobe Campaign Classic은 SMPP 프로토콜 버전 3.4를 지원합니다. SMS를 공급자(SMSC)에게 전송하고 SMS와 영수증을 받을 수 있는 광범위한 프로토콜입니다. 자세한 내용은 [SMPP 설명서](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)를 참조하세요.

SMS 서비스 공급자 측의 네트워크 장비는 종종 SMSC라고 합니다.

### SMPP 연결 {#smpp-connections}

Adobe Campaign은 TCP를 통해 SMS 서비스 공급자의 네트워크 장비에 연결합니다. SMPP 프로토콜은 Adobe Campaign에서 공급자로의 영구 TCP 연결을 설정합니다. TCP 연결은 메시지를 받을 때에도 항상 Adobe Campaign에 의해 시작됩니다.
SMPP는 모드에 따라 1개 또는 2개의 TCP 연결을 엽니다. 모든 연결은 항상 Adobe Campaign에 의해 시작됩니다.

SMPP 프로토콜은 다음 두 가지 모드에서 작동할 수 있습니다.

* **송신기+수신기(또는 TX+RX)**: 두 개의 별도 TCP 연결이 메시지 송수신에 사용됩니다.
* **송수신기(또는 TRX)**: 단일 TCP 연결이 메시지 송수신에 사용됩니다.

>[!NOTE]
>
> Adobe Campaign Classic은 TX+RX 모드만 지원합니다. 이 제한은 기술 아키텍처에 의한 것입니다.

### SMPP PDU {#smpp-pdu}

SMPP 전송 단위(&quot;패킷&quot;)를 PDU라고 합니다. **PDU**&#x200B;에는 명령, 상태, 시퀀스 번호 및 데이터가 포함되어 있습니다.

각 PDU는 `SMPP RESP PDU`(동기 응답)에 의해 확인되어야 합니다. 요청이 파이프라인될 수 있음: 보낸 사람이 `RESP`을(를) 기다리지 않고 많은 명령을 보낼 수 있으며 언제든지 파이프라인될 수 있는 요청 수를 창이라고 합니다. `RESP PDU`은(는) 해당 이니시에이터 PDU의 순서와 관련이 없는 순서로 도착할 수 있습니다.

분리된 **송신기+수신기** 모드에서 사용되는 연결은 전송된 메시지의 종류에 따라 다릅니다. 송신기 연결은 MT에, 수신기 연결은 MO와 SR에 사용됩니다. 각 유형의 메시지에 대한 요청과 응답은 동일한 TCP 연결을 통해 전송됩니다.

예를 들어 MT를 전송할 때 송신기 연결이 사용되며 MT를 확인하는 `RESP`도 송신기 채널을 통해 전송됩니다. MO(또는 SR)를 받으면 수신기 연결을 사용하여 MO를 수신하고 MO를 승인하는 `RESP`을(를) 보냅니다.

![](assets/do-not-localize/sms_protocol_1.png)

Adobe Campaign Classic에서 SR을 해당 MT와 연결하기 위해 SMSC에서 `SUBMIT_SM_RESP` 및 `DELIVER_SM` 단계를 통해 ID가 반환됩니다. 식별자가 `nms::providerMsgId` 테이블의 `providerId` 필드에 저장되고 `broadLogId` 및 `deliveryId`에 연결됩니다. 이 일치 작업은 데이터베이스에 쓸 때 SMS 프로세스에 의해 수행됩니다.

성공한 `SUBMIT_SM_RESP PDU`은(는) 전송 로그에서 &quot;보낸&quot; 메시지 상태를 트리거하고 성공한 `DELIVER_SM (SR) PDU`은(는) &quot;받은&quot; 메시지 상태를 트리거합니다.

### 보안 측면 {#security-aspects}

프로토콜 자체는 암호화되지 않습니다. 대부분의 공급자는 변형 IP를 허용 목록에 추가하다에서 구현하므로 Adobe Campaign 서버 IP 주소를 공급자에게 선언해야 합니다.

Adobe Campaign은 바인드 단계 동안 로그인 및 암호 전달을 지원합니다. 또한 TLS보다 SMPP를 지원합니다. 적절한 보안을 위해 인증서가 필요하다는 점을 유의해야 합니다. SMPP 커넥터는 인증서 검사를 우회할 수 있지만 인증서가 없는 TLS는 훨씬 낮은 수준의 보안을 제공하므로 테스트용으로만 사용해야 합니다.

커넥터가 시스템 `openssl` 라이브러리에서 제공하는 기본 인증서를 사용합니다. 일반적으로 Debian의 `/etc/ssl/certs` 디렉터리에서 제공합니다. 이 디렉터리는 기본적으로 &quot;ca-certificates&quot; 패키지에서 제공되지만 사용자 지정할 수 있습니다.

### 각 유형의 PDU에 있는 정보 {#information-pdu}

각 유형의 PDU에는 서로 다른 정보를 전달하는 개별 필드가 있습니다. 이러한 PDU는 [SMPP 3.4 사양](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)에 자세히 설명되어 있습니다.

아래 각 섹션에서는 PDU와 동기 응답(`*_RESP PDU`)에 대해 설명합니다. 모든 PDU는 해당 `RESP`에서 확인해야 합니다. 이는 사양의 필수 부분입니다.

PDU에는 선택적 필드가 있을 수 있습니다. 가장 일반적인 필드만 여기에 설명되어 있습니다. 자세한 내용은 [SMPP 3.4 사양](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)을 참조하세요.

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

이 PDU는 SMSC에 대한 연결을 시작하는 데 사용됩니다. **송신기**, **수신기** 및 **송수신기** 모드는 이 연결을 통해 전송할 수 있는 SMS의 종류만 변경합니다. 구체적으로 다음과 같습니다.

| 모드 | 허용되는 SMS 종류 |
|:-:|:-:|
| 송신기 | MT |
| 수신자 | MO + SR |
| 송수신기 | MT + MO + SR |

`BIND_* PDU`의 주목할 만한 필드:

* **system_id**: 인증에 사용되는 로그인입니다. 외부 계정에서 설정합니다.

* **암호**: 인증에 사용되는 암호입니다. 외부 계정에서 설정합니다.

* **system_type**: 일부 공급자에 대해 특정 값으로 설정해야 합니다. 모든 버전에서 사용할 수 있는 외부 계정에서 설정합니다. 종종 계약, 채널, 국가 등이 서로 다른 유형을 구분합니다.

* **addr_ton** 및 **addr_npi**: 일부 공급자에 필요합니다. 외부 계정의 `Bind TON` 및 `Bind NPI` 설정에 의해 설정됩니다.

* **address_range**: 일부 공급자에 필요합니다. 대부분의 경우 이 연결에 허용된 바로 가기 코드 목록입니다. 외부 계정에서 설정합니다.

`BIND_*_RESP`에 특정 필드가 없으므로 연결이 성공했는지 여부를 확인합니다.

#### 바인딩 해제 {#unbind}

연결을 끊기 전에 시스템에서 이 PDU를 보내야 합니다. 연결을 닫기 전에 일치하는 `UNBIND_RESP` PDU를 기다려야 합니다.

SMSC를 준수하는 경우 연결을 닫으면 안 됩니다. TCP 연결은 Adobe Campaign 커넥터에 의해 제어됩니다.

#### SUBMIT_SM {#submit-sm}

이 PDU는 MT를 SMSC로 전송합니다. 응답 PDU는 MT의 ID를 제공합니다.

`SUBMIT_SM` PDU의 주요 필드:

* **service_type**: 일부 공급자에 필요합니다. 게재 속성에서 을 설정합니다.

* **source_addr_ton** 및 **source_addr_npi**: 전송되는 소스 주소의 종류를 나타냅니다. 이러한 필드의 의미는 표준화되어 있지만 일부 공급자가 필드를 다르게 사용하므로 공급자에게 정확한 값을 요청해야 합니다. 외부 계정에서 설정합니다.

* **source_addr**: MT의 원본 주소/oADC 휴대폰에 표시됩니다. 외부 계정 및 게재에서 설정하면 게재 값이 외부 계정 값보다 우선합니다.

* **dest_addr_ton** 및 **dest_addr_npi**: 전송되는 대상 주소의 종류(예: 로컬 또는 국제 형식)를 나타냅니다. 이러한 필드의 의미는 표준화되어 있지만 일부 공급자가 필드를 다르게 사용하므로 공급자에게 정확한 값을 요청해야 합니다. 외부 계정에서 설정합니다.

* **destination_addr**: 받는 사람 주소, 전화 번호 또는 MSISDN입니다.

* **esm_class**: 텍스트 필드에 UDH가 사용되는지 여부를 확인하는 데 사용됩니다. `message_payload` 모드가 사용되지 않는 경우 커넥터가 분할 SMS에 대해 자동으로 사용하도록 설정합니다.

* **priority_flag**: 이 메시지의 우선 순위를 다른 메시지보다 우선합니다. 이는 게재 자체의 우선 순위와 연관되어 있습니다.

* **validity_period**: 그 이후에는 다시 시도하지 않아야 하는 타임스탬프입니다. 게재 자체를 설정합니다.

* **registered_delivery**: SR이 요청되었는지 여부를 알려줍니다. Adobe Campaign은 자동 회신을 제외하고 항상 이 플래그를 설정합니다. 다중 파트 메시지의 경우 플래그는 첫 번째 파트에만 설정됩니다. 모든 버전의 비헤이비어가 동일합니다.

* **data_coding**: 텍스트 필드에 사용된 인코딩을 나타냅니다. 자세한 내용은 [SMS 텍스트 인코딩](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/sms/sms-channel#sms-text-encoding){target="_blank"}(Campaign v8 설명서) 섹션을 참조하십시오.

* **짧은 메시지**: 메시지 텍스트입니다. UDH를 사용하는 경우 여기에 UHD 헤더도 포함됩니다.

Adobe Campaign은 다음과 같은 옵션 필드를 지원합니다.

* **dest_addr_subunit**: SMS 대상(플래시, 모바일 또는 SIM 카드)을 지정하는 데 사용됩니다. 게재 속성에서 을 설정합니다.

* **message_payload**: 외부 계정에서 활성화하면 긴 메시지가 단일 PDU에서 전송되고 `short_message` 필드 대신 이 필드에서 텍스트가 전송됩니다.

#### SUBMIT_SM_RESP {#submit-sm-resp}

이 PDU에는 MT의 ID가 포함됩니다. 이는 수신 SR과 연결하는 데 유용합니다.

>[!IMPORTANT]
>
>많은 공급자가 MT ID를 16진수로 전송합니다. 외부 계정에서 MT 승인&#x200B;**설정의** ID 형식을 올바르게 설정했는지 확인하십시오.

일부 공급자는 SR을 보낸 후 `SUBMIT_SM_RESP`을(를) 보냅니다. 이 동작을 설명하기 위해 Adobe Campaign은 알 수 없는 ID가 있는 SR에 **잘못된 메시지 ID**&#x200B;을(를) 응답하기 전에 30초를 기다립니다.

#### DELIVER_SM {#delivery-sm}

이 PDU는 SMSC에서 Adobe Campaign으로 전송됩니다. 여기에는 MO 또는 SR이 포함되어 있습니다.

대부분의 필드는 해당 `SUBMIT_SM` 필드와 같은 의미를 갖습니다. 다음은 유용한 필드 목록입니다.

* **source_addr**: MO/SR의 원본 주소입니다. 보통 이것은 전화번호입니다.

* **destination_addr**: MO 또는 SR을 받은 짧은 코드.

* **esm_class**: PDU가 MO인지 SR인지 확인하는 데 사용됩니다.

* **짧은 메시지**: 메시지 텍스트입니다. SR의 경우 SMPP 프로토콜 사양의 부록 B에 설명된 데이터가 포함됩니다. 자세한 내용은 [SR 오류 관리](sms-protocol.md#sr-error-management)를 참조하십시오.

Adobe Campaign에서 일부 구성을 사용하여 선택적 필드 `receipted_message_id`의 메시지 ID를 읽을 수 있습니다.

#### DELIVER_SM_RESP {#deliver-sm-resp}

이 PDU는 Adobe Campaign에서 SR 및 MO를 승인하도록 전송됩니다.

Adobe Campaign Classic은 SR 및 MO가 데이터베이스에 삽입되면 이를 확인합니다. 성공적인 `DELIVER_SM_RESP` PDU가 전송된 경우에도 일부 처리 오류가 발생할 수 있습니다. 이 제한은 Adobe Campaign Classic의 소프트웨어 아키텍처로 인해 발생합니다.

#### ENQUIRE_LINK {#enquire-links}

이 PDU는 연결이 활성 상태인지 확인하는 데만 사용됩니다. 그 빈도는 제공자의 필요에 따라 설정되어야 한다.

기본 60초는 외부 계정에 설정된 대부분의 구성과 일치해야 합니다.

#### ENQUIRE_LINK_RESP {#enquire-links-resp}

이 PDU는 연결이 활성 상태임을 확인합니다.

### 다중 파트 SMS(긴 SMS) {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign은 전송에 대해 다중 부분 SMS 또는 긴 SMS만 지원합니다. UDH 및 `message_payload`은(는) 수신 SMS(MO)에 지원되지 않습니다. 즉, MO는 160자로 제한됩니다.

### 처리량 제한 및 창 {#throughput-capping}

대부분의 공급업체는 각 SMPP 연결에 대해 처리량 제한을 필요로 합니다. 이 작업은 외부 계정에서 SMS 수를 설정하여 수행할 수 있습니다. 처리량 제한은 접속당 발생하며, 총 유효 처리량은 접속당 한도에 총 접속 수를 곱한 값입니다. 자세한 내용은 [동시 연결](sms-protocol.md#connection-settings) 섹션을 참조하십시오.

가능한 최대 처리량에 도달하려면 최대 전송 창을 미세 조정해야 합니다. 전송 기간은 `SUBMIT_SM_RESP`을(를) 기다리지 않고 보낼 수 있는 `SUBMIT_SM PDU`의 수입니다. 자세한 내용은 [전송 창 설정](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account#smpp-delays){target="_blank"}(Campaign v8 설명서) 섹션을 참조하십시오.

### SR 및 오류 관리 (&quot;부록 B&quot;) {#sr-error-management}

SMPP 프로토콜은 `RESP PDU`의 표준 동기 오류를 정의하지만 SR에 대한 오류 코드를 정의하지 않습니다. 각 공급자는 자신의 의미를 갖는 자체 오류 코드를 사용합니다.

[SMPP 프로토콜 사양](https://smpp.org/SMPP_v3_4_Issue1_2.pdf)의 부록 B 섹션(167페이지)에 권장 사항이 있지만 실제 오류 코드와 그 의미가 나열되지 않습니다.

오류 관리에 적응하기 위해 Adobe Campaign의 Broadlog 메시지 시스템을 활용하여 오류와 심각도(하드, 소프트 등)를 적절하게 프로비저닝합니다.

위에서 언급했듯이 두 가지 유형의 오류가 있습니다.

* `SUBMIT_SM_RESP`에서 메시지가 SMSC로 전송된 직후 발생하는 동기 답글
* 확인 메일은 모바일이 메시지를 수신했을 때 또는 메시지가 시간 초과되었을 때 훨씬 나중에 올 수 있습니다. 이 경우 SR에서 오류가 발견되었습니다.

SR을 받으면 `short_message` 필드에서 상태 및 오류를 찾을 수 있습니다(예: 부록 B 준수 구현). PDU의 `short_message` 필드는 MT의 텍스트를 포함하므로 종종 **텍스트 필드**&#x200B;라고 합니다. SR의 경우 기술 정보와 **Text**&#x200B;이라는 하위 필드가 포함되어 있습니다. 이 두 필드는 서로 다르며 `short_message`에는 실제로 **텍스트** 필드 및 기타 정보가 포함되어 있습니다.

Adobe Campaign Classic 커넥터(확장 SMPP 제외)는 선택한 공급자에 따라 달라지는 하드코딩된 동작을 사용합니다. 일반 SMPP는 세부 정보 없이 성공과 오류만 구별합니다. 게재 로그에는 보장되지 않는 일부 정보가 포함될 수 있습니다.

#### SR 텍스트 필드 형식 {#sr-text-field-format}

사양은 SR 텍스트 필드에 이 형식을 사용하는 것을 권장합니다. 이 목록은 필드 이름과 값을 구분하기 위해 콜론으로 공백으로 구분된 하위 필드 목록입니다. 필드 이름은 대소문자를 구분하지 않습니다.

부록 B 권장 사항과 일치하는 SR 텍스트 필드의 예:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

ID 필드는 `SUBMIT_SM_RESP PDU`에서 받은 ID, MT의 승인입니다.

`sub` 및 `dlvrd`은(는) 배달된 부분 및 배달된 메시지의 양을 계산해야 하지만 broadlog 시스템이 더 나은 통합 정보를 제공하므로 Adobe Campaign에서는 이 정보를 사용하지 않습니다.

`submit date` 및 `done date` 필드는 MT를 보낸 시기와 모바일에서 SR를 보낸 시기를 나타내는 타임스탬프입니다. 시간대와 관련된 일부 문제 또는 잘못된 날짜가 설정된 모바일이 제공한 잘못된 타임스탬프를 예상하십시오.

통계 필드는 메시지 상태를 알려주기 때문에 중요합니다. 중요한 상태는 `DELIVRD`, `UNDELIV` 및 `REJECTD`뿐입니다. `DELIVRD` 상태는 성공을 나타내고 나머지 두 상태는 오류를 나타냅니다. 다른 값도 가능하지만 일반적으로 중간 알림입니다(예: MT가 이동통신사에 도달했지만 휴대폰은 아님). Adobe Campaign에서는 이러한 중간 알림을 무시합니다.

err 필드에는 공급자별 오류 코드가 포함됩니다. 공급자는 이 값을 해석할 수 있도록 가능한 오류 코드 표를 의미와 함께 제공해야 합니다.

마지막으로 텍스트 필드에는 일반적으로 MT 텍스트의 시작이 포함됩니다. Adobe Campaign에서는 이를 무시하며 일부 공급업체는 PII 누출 및 네트워크 대역폭 소비를 방지하기 위해 전송하지 않습니다. 이 필드를 읽으면 문제 해결 중에 테스트 MT와 일치하는 SR을 더 쉽게 찾을 수 있습니다.

### Adobe Campaign Classic Extended Generic SMPP의 SR 처리 예 {#sr-processing}

이 예는 부록 B 권장 사항, 외부 계정의 기본값 및 성공적인 SMS MT에 따른 구현 사례를 표시합니다.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

먼저 `id extraction` 정규식을 적용하여 ID를 추출하고 해당 MT와 조정합니다.

그런 다음 `status extraction` 정규 표현식 및 `error code extraction` 정규 표현식이 적용되어 이러한 필드를 추출하고 문자열에 추가됩니다.

broadlog 메시지는 이 정보로 구성되며, 참조용으로 변경되지 않은 원래 문자열이 추가됩니다.

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

그런 다음 메시지가 표준화되어 MESSAGE 부분이 제거되어 동일한 통계 및 오류 코드로 여러 메시지를 일치시킬 수 있습니다.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

메시지가 broadlog 메시지 테이블에 아직 프로비저닝되지 않은 경우 전체 메시지를 **firstText**(으)로 사용하고 정규화된 메시지를 사용하여 새 항목이 만들어집니다. 그런 다음 커넥터는 성공 및 `error` 정규식을 사용하여 성공 또는 실패인지를 확인합니다.

* `success` 정규식과 일치하면 성공한 것으로 간주됩니다.

* `error` 정규식과 일치하면 메시지가 오류로 처리됩니다.

* 이 두 정규 표현식 중 어느 하나도 일치하지 않으면 SR이 무시됩니다. Adobe Campaign에서 처리하지 않는 중간 알림일 수 있습니다.

기본적으로 모든 오류는 소프트 오류로 프로비저닝됩니다. 즉, 하드 오류를 직접 프로비저닝해야 합니다.

## SMPP 외부 계정 매개 변수 {#SMPP-parameters-external}

SMPP 프로토콜의 각 구현에는 많은 변형이 있습니다. 호환성과 적응성을 향상시키기 위해 SMPP 커넥터의 동작을 변경하는 데 사용할 수 있는 다양한 설정을 제공합니다. 이 섹션에서는 모든 매개 변수와 커넥터에 미치는 영향을 설명합니다.

### 일반 매개 변수 및 라우팅 {#general-parameters-routing}

**이 계정의 MTA 인스턴스 제한**

SMPP 공급자에 연결할 수 있는 MTA 인스턴스 수로 제한을 설정할 수 있습니다. 선택할 경우 최대 사용할 수 있는 MTA 수를 지정할 수 있습니다.

이 옵션을 사용하면 연결 수를 보다 세밀하게 제어할 수 있습니다. [동시 연결](sms-protocol.md#connection-settings)을 참조하세요.

실행 중인 MTA 수보다 큰 값을 설정하면 모든 MTA가 정상적으로 실행됩니다. 이 옵션은 제한일 뿐이며 추가 MTA를 생성할 수 없습니다.

공급자 요구 사항과 같은 연결 수를 정확하게 제어해야 하는 경우, 현재 배포에 실행 중인 MTA의 수가 적절하더라도 항상 이 옵션을 설정하는 것이 좋습니다. 이후에 추가 MTA가 추가되더라도 연결 제한은 계속 유지됩니다.

### 연결 설정 {#connection-settings}

#### SMSC 구현 이름 {#smsc-implementation-name}

SMSC 구현의 이름을 설정합니다. 공급자 이름으로 설정해야 합니다. 이 필드에 추가할 내용을 알아보려면 관리자 또는 게재 팀에 문의하십시오. 이 필드의 역할은 [SR 오류 관리](sms-protocol.md#sr-error-management) 섹션에 설명되어 있습니다.

>[!NOTE]
>
>전달성 팀의 참여는 계약을 기반으로 하며, 고객은 전달성 참여와 관련된 정보를 얻으려면 Adobe 담당자에게 문의해야 합니다.

#### MTA 하위 연결 수 {#number-mta-child}

Adobe Campaign Classic에서 MTA 하위 항목당 연결 수를 정의합니다.

Adobe Campaign Classic Extended SMPP 커넥터는 MTA 하위 항목당 연결 수를 제어할 수 있습니다. 연결의 전역 제한을 제어하려면 MTA 하위 프로세스 수를 제한해야 합니다. 이는 종종 SMS에 대한 전용 중간 소싱 플랫폼을 보유하는 것을 의미합니다.

Adobe Campaign Classic의 경우 서로 다른 수의 수신기 및 송신기 연결이 있을 수 있습니다.

* **송신기 연결 = MTA 하위 연결 수 * MTA 하위 프로세스 수 * MTA 수(자동 회신이 설정된 경우) * MTA 하위 연결 수**

위에서 제안한 대로 자동 회신이 활성화된 경우 Adobe Campaign Classic SMS 프로세스에서 더 많은 송신기 연결을 엽니다. 이러한 추가 연결은 자동 답장을 보내는 데 사용됩니다.

* **받는 사람 연결 = MTA 자식 연결 수**

자동 회신을 설정하면 SMS 프로세스에서 송신기/수신기 쌍을 열어 송신기 연결 수를 늘립니다. 자동 회신을 설정하지 않은 경우 수신자 연결만 열립니다.

#### SMPP에 대해 TLS 활성화 {#enable-TLS}

TLS를 사용하여 공급자에 연결합니다. 연결이 암호화됩니다. OpenSSL 라이브러리에서 TLS 연결을 관리합니다. OpenSSL에 적용되는 모든 항목은 이 연결에 대해 적용됩니다.

#### 로그 파일의 자세한 SMPP 추적 활성화 {#enable-verbose-log-file}

이 설정은 모든 SMPP 트래픽을 로그 파일로 덤프합니다. 초기 설정 중에 매개 변수를 조정해야 하는 경우가 많습니다. 커넥터의 문제를 해결할 때 공급자가 보는 트래픽과 비교하여 이 기능을 활성화해야 합니다.

Adobe Campaign Classic에서 로그 출력은 MT 관련 트래픽의 MTA 로그와 MO 및 SR 관련 트래픽의 SMS 로그에 있습니다.

### 수신자 연결 설정 {#receiver-connection}

이 섹션은 분리된 **송신기+수신기** 모드에서만 볼 수 있습니다.

#### 수신자에 대해 다른 매개 변수 사용 {#receiver-parameters}

확인란을 선택 취소하면 송신기와 수신기에 동일한 설정이 사용됩니다.

확인란을 선택하면 **연결 설정** 섹션의 설정이 전송기에 적용되고 **수신기 연결** 설정의 설정이 수신기에 적용됩니다.

**받는 사람 서버, 포트, 계정, 암호, 시스템 유형**

이러한 설정은 송신기+수신기 모드에 있을 때 수신기에 적용됩니다. 송신기 부품처럼 작동합니다. 자세한 내용은 위 를 참조하십시오.

### SMPP 채널 설정 {#smpp-channel-settings}

#### 데이터베이스에 수신 MO 저장 {#incoming-mo-storing}

활성화되면 들어오는 MO가 데이터베이스의 inSMS 테이블에 저장됩니다. 이 테이블은 모든 워크플로우의 쿼리 활동을 사용하여 쿼리할 수 있습니다.

Adobe Campaign Classic은 항상 모든 MO를 inSMS 데이터베이스에 저장하므로 이 옵션을 사용할 수 없습니다.

#### SR 처리 중 실시간 KPI 업데이트 활성화 {#real-time-kpi}

활성화되면 오류 SR이 수신될 때 기본 게재 페이지에서 KPI가 실시간으로 업데이트됩니다.

이 경우 데이터베이스 경합 때문에 성능이 저하될 수 있습니다. 사용하지 않도록 설정하면 20분마다 실행되는 **syncfromexec** 워크플로우로 통계가 업데이트됩니다.

Adobe Campaign Classic에는 KPI에 대해 완전히 다른 메커니즘이 있으므로 이 옵션을 사용할 수 없습니다.

#### 짧은 코드 {#short-code}

계정의 기본 짧은 코드를 나타냅니다. 이 계정에 여러 짧은 코드가 사용되거나 짧은 코드를 알 수 없는 경우 이 필드를 비워 둡니다.

짧은 코드를 지정하면 두 가지 기능에 유용합니다.

* 소스 번호가 제공되지 않으면 미리보기에 짧은 코드가 표시됩니다. 그것은 휴대폰의 실제 행동을 반영할 것입니다.

* 자동 회신 기능의 설정에 대한 차단 목록에 추가하다는 특정 짧은 코드만 사용자에게 보냅니다.

### SMSC 세부 사항 {#SMSC-specifics}

이러한 설정은 Adobe Campaign 커넥터를 대부분의 SMPP 구현 특성에 적용하는 고급 설정입니다.

#### TLS 인증서 검사 건너뛰기 {#skip-tls}

TLS가 활성화되면 모든 인증서 검사를 건너뜁니다.

선택하면 연결이 더 이상 안전하지 않습니다. 프로덕션에서 활성화해서는 안 됩니다.

이 메서드는 디버깅 또는 테스트 목적으로 유용합니다.

인증서 유효성 검사에 대해 세 가지 다른 값 중에서 선택할 수 있습니다.

* 전체 인증 확인(호스트 이름 포함), 기본값
* 호스트 이름 확인을 건너뜁니다.
* 인증서 확인을 건너뜁니다.

#### 성공/오류 상태를 결정하기 위해 적용된 정규 표현식 {#regex-applied}

알 수 없는 stat/err 필드 조합이 있는 메시지가 발생하면 이 정규 표현식이 stat 필드에 적용되어 SR이 성공인지 아니면 오류인지 파악합니다. 이 정규 표현식과 일치하지 않는 통계 값이 있는 SR은 무시됩니다.

기본적으로 [부록 B](sms-protocol.md#sr-error-management)에서 `DELIV`(예: `DELIVRD`)으로 시작하는 통계 값은 성공적으로 전달된 것으로 간주되며 `REJECTED`, `UNDELIV` 같은 오류와 일치하는 모든 통계 값은 오류로 간주됩니다.

#### MT 승인의 ID 형식 {#id-format-mt}

`SUBMIT_SM_RESP PDU`의 `message_id` 필드에서 반환된 ID의 형식을 나타냅니다.

* **수정하지 않음**: ID가 데이터베이스에 있는 그대로 ASCII로 인코딩된 텍스트로 저장됩니다. 사전 처리나 필터링이 발생하지 않습니다.

* **10진수**: ID는 ASCII 형식의 10진수입니다. 이 설정을 사용하면 선행 및 후행 공백과 선행 0이 제거됩니다.

* **16진수**: ID는 ASCII 형식의 16진수여야 하며 앞에 0x가 없고 뒤에 h가 없습니다. 그런 다음 ID가 데이터베이스에 저장되기 전에 10진수로 변환됩니다.

* **16진수 문자열**: ID는 16진수로 인코딩된 바이트 문자열인 ASCII 인코딩된 텍스트여야 합니다. 예를 들어 PDU에서 ASCII &quot;414243&quot;으로 변환되는 `0x34 0x31 0x34 0x32 0x34 0x33`을(를) 찾을 수 있습니다. 그런 다음 이 문자열은 16진수 바이트 문자열로 디코딩되며 그 결과 &quot;ABC&quot;를 얻습니다. ID &quot;ABC&quot;를 데이터베이스에 저장합니다.

#### SR의 ID 포맷 {#id-format-sr}

SR에서 ID의 `Extraction` 정규식에 의해 캡처된 ID의 형식을 나타냅니다. 값은 위의 MT에서 포맷과 동일한 의미 및 동일한 동작을 갖습니다.

선택적 필드에 **SR ID 또는 오류 코드**

>[!NOTE]
>
>Adobe Campaign Classic Extended SMPP 커넥터에서만 사용할 수 있습니다.

선택하면 선택적 필드의 내용이 위의 정규 표현식에서 처리한 텍스트에 추가됩니다. 텍스트에는 `0xTAG:VALUE`, `0xTAG` 형식의 태그가 있으며, 이 값은 대소문자가 `0x002E`인 4자리 16진수 값입니다.

예를 들어 `receipted_message_id` 필드에서 ID를 캡처할 수 있습니다. 이를 위해 이 확인란을 활성화하면 다음 텍스트가 상태에 추가됩니다.

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

이 예에서 0x001E는 선택적 필드의 태그이고 UUID는 필드의 값입니다.

이제 이 값을 캡처하기 위해 SR 필드의 ID 추출 정규 표현식에서 다음 정규 표현식을 설정할 수 있습니다.

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>텍스트(ASCII/UTF-8) 값이 있는 선택적 필드만 캡처할 수 있습니다. 특히, 이진 필드는 현재의 정규 표현식 시스템으로는 안정적으로 캡처될 수 없다.

**서비스 ID 태그**

사용자 지정 TLV를 추가할 수 있습니다. 이 필드는 태그 부분을 설정합니다. 게재의 고급 매개 변수에서 **서비스 또는 프로그램 ID** 값의 게재별로 값을 사용자 지정할 수 있습니다.

이 설정은 메시지당 하나의 TLV 옵션만 추가할 수 있습니다.

### MO로 자동 회신 전송됨 {#automatic-reply}

>[!IMPORTANT]
>
>Adobe Campaign Classic 및 하이브리드 아키텍처에서 확장된 SMPP 커넥터에 대해 자동 회신을 적용하려면 **외부 계정** 폴더에 있는 mid 연산자에 대한 쓰기 액세스 권한을 추가해야 합니다.

이 기능을 사용하면 MO에 빠르게 텍스트를 응답하고 짧은 코드별로 차단 목록에 추가하다에 보내는 것을 처리할 수 있습니다.

**키워드** 및 **짧은 코드** 열은 자동 응답을 트리거하는 조건을 정의합니다. 두 필드가 일치하면 MO가 전송되고 추가 작업이 트리거됩니다. 와일드카드를 지정하려면 필드를 비워 두어야 합니다. 키워드는 문장 부호 및 선행 공백을 무시하고 MO 텍스트의 첫 번째 영숫자 단어와 일치합니다. 즉, **키워드** 필드는 공백을 포함할 수 없으며 단일 단어여야 합니다.

**키워드** 설정은 접두사입니다. 예를 들어 &quot;AD&quot;를 지정하는 경우 &quot;AD&quot;, &quot;ADAPT&quot; 및 &quot;ADOBE&quot;와 일치합니다. 공통 접두사가 있는 키워드가 여러 개 있는 경우 키워드가 위에서 아래로 처리되므로 순서에 주의해야 합니다.

**회신** 열은 회신할 텍스트입니다. 이 필드에는 사용할 수 있는 개인화가 없습니다. 이 필드를 비워 두면 메시지가 회신되지 않지만 추가 작업이 트리거됩니다.

**추가 작업** 열은 **키워드**&#x200B;와 **짧은 코드**&#x200B;가 모두 일치하고 빈 짧은 코드가 모든 짧은 코드와 일치하는 경우 추가 작업을 제공합니다. 격리로 보내거나 격리에서 제거할 수 있습니다. value none은 텍스트에 답글을 달지 않습니다. **추가 작업**&#x200B;을 지정했지만 **회신** 필드를 비워 두면 작업이 실행되지만 회신이 전송되지 않습니다. 격리는 지정된 짧은 코드에만 적용되거나 필드가 비어 있는 경우 모든 짧은 코드에 적용됩니다.

>[!IMPORTANT]
>
>전체 전화 번호 보내기 설정은 자동 회신 격리 메커니즘의 동작에 영향을 줍니다. 전체 전화 번호 보내기를 선택하지 않으면 격리된 전화 번호에 국제 전화 번호 형식과 호환되도록 더하기 기호(&quot;+&quot;)가 붙습니다.

테이블의 모든 항목은 하나의 규칙이 일치할 때까지 지정된 순서로 처리됩니다. 여러 규칙이 MO와 일치하는 경우 최상위 규칙만 적용됩니다.

## SMS 게재 템플릿 매개 변수 {#sms-delivery-template-parameters}

일부 매개 변수는 게재 템플릿별로 설정할 수 있습니다.

### 게재 매개 변수 {#delivery-parameters}

#### 변속 모드 {#transmission-mode}

이 필드는 전송할 SMS 종류를 나타냅니다(모바일 또는 SIM 카드에 저장된 일반 또는 플래시 메시지).

이 설정은 `SUBMIT_SM PDU`의 `dest_addr_subunit` 선택적 필드에서 전송됩니다.

* **지정되지 않음**&#x200B;에서 PDU에 선택적 필드를 보내지 않습니다.

* **Flash**&#x200B;이(가) 값을 1로 설정합니다. 이 메시지는 모바일에 표시되며 메모리에 저장되지 않는 플래시 메시지를 보냅니다.

* **보통**&#x200B;은 값을 0으로 설정합니다. 정상적인 메시지를 보냅니다.

* **모바일에 저장**&#x200B;에서 값을 2로 설정합니다. SMS를 내부 메모리에 저장하도록 전화기에 알립니다.

* **터미널에 저장**&#x200B;에서 값을 3으로 설정합니다. SMS를 SIM 카드에 저장하도록 전화기에 알려줍니다.

#### 유효 기간 {#validity-period}

유효 기간이 `SUBMIT_SM PDU`의 `validity_period` 필드에서 전송됩니다. 날짜는 항상 절대 UTC 시간 형식으로 지정되며 날짜 필드는 &quot;00+&quot;로 끝납니다.

## 확장된 일반 SMPP 커넥터 {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

화살표는 데이터 흐름을 나타냅니다.

게재 부분을 보낼 때 MTA에서 MTA 하위 항목을 생성합니다. MTA 하위 프로세스 수는 동적이며 serverConf.xml의 구성에 따라 다릅니다. 각 MTA 자식은 SMPP 공급자에 연결하는 커넥터 `CSmppConnectorWorker`을(를) 인스턴스화합니다. MTA 하위 항목이 활성 상태를 유지하는 한 연결은 활성 상태로 유지되며 serverConf.xml에서도 구성할 수 있습니다.

SMS 프로세스는 SR만 처리하고, 공급자에 연결하고, 연결을 열어 둡니다. 프로세스는 새 설정을 다시 로드하기 위해 10분마다 다시 연결합니다. 이는 정상적인 작업입니다.

### 일치하는 MT, SR 및 broadlog 항목 {#matching-mt}

중간 테이블 `nmsProviderMsgId`은(는) Broadlog에 비동기적으로 커밋되기 전에 MT 및 SR 데이터를 임시로 저장하는 데 사용됩니다.

`nmsProviderMsgId` 테이블에 3개의 열 그룹이 있습니다.

* MT가 전송되고 승인되면 열이 업데이트됨: `iBroadLogId`, `iDeliveryId`

* SR을 받을 때 업데이트된 열: `iMsgId`, `iStatus`

* 항상 업데이트되는 열: `tsCreated`, `sProviderId`

MT와 SR이 모두 처리를 완료하면 브로드로그 정보와 상태 정보가 모두 포함된 전체 줄이 있어야 합니다.

`iMsgId`이(가) `nmsBroadLogMsg` 테이블에 연결되어 전체 상태/오류 메시지를 나타냅니다.

SMS 프로세스는 매분마다 전체 줄을 확인한 다음 비동기적으로 처리합니다.

* 전체 줄을 읽습니다.
* SMS 프로세스는 게재 매핑을 기반으로 브로드로그 테이블의 이름을 계산합니다.
* SMS 프로세스는 메시지 ID 및 상태로 브로드로그 테이블을 업데이트합니다.

**처리량 및 병렬 연결**

각 MTA 하위 항목은 구성 가능한 연결 양을 만들므로 MTA 하위 항목의 수를 제한하면 연결 수가 제한됩니다. MTA 하위 프로세스와 트래픽 간의 상관 관계는 상관 관계가 있으므로 어느 정도 제어할 수 있지만 여전히 예측할 수 없습니다.
