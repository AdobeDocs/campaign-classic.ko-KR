---
solution: Campaign Classic
product: campaign
title: SMS 커넥터 프로토콜 및 설정
description: SMS 커넥터와 구성 방법에 대해 자세히 알아보십시오.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '2751'
ht-degree: 0%

---


# SMS 문제 해결 {#troubleshooting-sms}

## 다른 외부 계정 {#external-account-conflict} 간 충돌

인스턴스에 여러 개의 SMS 외부 계정이 있는 경우 외부 계정 간의 충돌로 인해 문제가 발생하지 않는지 확인해야 합니다.

Adobe Campaign은 외부 계정을 관련 없는 엔티티로 취급합니다.

여러 계정이 있는 경우 다음 절차에 따라 문제를 일으키는 외부 계정을 분리합니다.

1. 모든 외부 계정을 비활성화합니다.
1. 하나의 외부 계정을 활성화합니다.
1. 문제를 재현해 보세요.
1. 초기 문제가 항상 나타나지 않는 경우, 결론에 도달하기 전에 적절한 양의 시도를 해야 합니다.
1. 해당 단일 계정에 문제가 나타나지 않으면 계정을 비활성화하고 다음 계정의 2단계로 다시 시작합니다.

모든 계정을 개별적으로 확인하면 다음과 같은 2가지 가능한 시나리오가 있습니다.

* **문제가 하나 또는 여러 개의 계정에 나타났다**

   이 경우 각 계정에 대해 다른 문제 해결 절차를 개별적으로 적용할 수 있습니다. 네트워크 트래픽과 로그 수를 줄이기 위해 계정을 진단하면서 다른 계정을 비활성화하는 것이 가장 좋습니다.

* **한 개의 계정만 활성 상태일 때 문제가 나타나지 않았습니다.**

   계정 간에 충돌이 있습니다. 앞에서 언급했듯이 Adobe Campaign은 계정을 개별적으로 처리하지만 제공자는 계정을 단일 계정으로 처리할 수 있습니다.

   * 모든 계정 간에 다른 로그인/암호 조합을 사용하고 있습니다.
해당 측면에서 잠재적인 충돌을 진단하려면 해당 공급업체에 문의하십시오.

   * 일부 외부 계정은 동일한 로그인/암호 조합을 공유합니다.
공급자는 `BIND PDU`이(가) 어느 외부 계정에서 왔는지를 알 수 없으므로 여러 계정의 모든 연결을 하나의 계정으로 처리합니다. 그들은 두 계정에 대해 MO와 SR을 무작위로 라우팅하여 문제를 일으켰을 수 있습니다.
공급자가 동일한 로그인/암호 조합에 대해 여러 개의 짧은 코드를 지원하는 경우 해당 짧은 코드를 `BIND PDU`에 배치할 위치를 지정해야 합니다. `BIND PDU`은(는) MO를 올바로 라우트할 수 있는 유일한 장소이기 때문에 이 정보는 `BIND PDU` 내에 넣어야 하며 `SUBMIT_SM`에는 삽입하지 않아야 합니다.
`BIND PDU`에서 사용할 수 있는 필드를 알아보려면 위의 각 유형의 PDU](../../delivery/using/sms-protocol.md#information-pdu) 섹션의 [정보를 참조하십시오. 일반적으로 `address_range`에서 짧은 코드를 추가하지만 공급자의 특별한 지원이 필요합니다. 여러 개의 짧은 코드를 독립적으로 라우팅할 수 있는 방법을 알려면 해당 고객에게 문의하십시오.
Adobe Campaign은 동일한 외부 계정에서 여러 개의 짧은 코드 처리를 지원합니다.

## 일반 {#external-account-issues}의 외부 계정 문제

* 커넥터가 최근에 변경되었는지 및 누가 변경되었는지 확인합니다(외부 계정을 그룹으로 확인).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* 시스템이 업그레이드되었는지 여부와 시기를 조사합니다(/postupgrade 디렉토리).
* SMS에 영향을 주는 모든 패키지가 최근에 업그레이드되었는지 확인합니다(/var/log/dpkg.log).

## 중간 소싱(호스트){#issue-mid-sourcing} 문제

* 중간 소싱 환경에서 문제가 발생하는 경우 중간 소싱 서버에서 배달 및 확장 로그가 올바르게 만들어지고 업데이트되는지 확인하십시오. 그렇지 않은 경우 SMS 문제가 아닙니다.

* mid 서버에서 모든 작업이 작동하고 SMS가 올바르게 전송되지만 마케팅 인스턴스가 제대로 업데이트되지 않으면 중간 동기화 문제가 있을 수 있습니다.

## {#issue-provider} 공급자에 연결할 때 발생하는 문제

* `BIND PDU`이 0이 아닌 `command_status` 코드를 반환하는 경우 자세한 내용을 공급자에게 요청하십시오.

* TCP 연결이 공급자에 연결되도록 네트워크가 올바르게 구성되었는지 확인합니다.

* 공급자가 Adobe Campaign 인스턴스의에 IP를 제대로 허용 목록에 추가하다 추가했는지 확인하십시오.

* **외부 계정** 설정을 선택합니다. 공급자에게 필드의 값을 요청합니다.

* 연결이 성공했지만 불안정하면 [연결이 불안정하면 ](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) 섹션을 확인하십시오.

* 연결 문제를 진단하기 어려운 경우 네트워크 캡처는 정보를 제공할 수 있습니다. 문제가 표시되는 동안 네트워크 캡처가 동시에 실행되므로 효율적으로 분석할 수 있습니다. 또한 문제가 나타나는 정확한 시간을 주목해야 합니다.

## 불안정한 연결 {#issues-unstable-connection} 문제

다음 중 하나가 발생하면 연결이 불안정하다고 간주됩니다.

* 연결 기간은 1시간 미만입니다. Adobe Campaign Classic 송신기 연결은 Adobe Campaign Classic MTA의 작동 방식 때문에 예외입니다.

* 공급자가 `UNBIND PDU`s를 보냅니다.

* `enquire_link` adobe campaign 쪽이나 공급자 측에서 시간이 초과됩니다. 이 경우 0이 아닌 오류 코드와 함께 `ENQUIRE_LINK_RESP`이 표시될 수 있습니다.

* `BIND PDU`s가 많습니다.연결 수에 따라 하루에 몇 개 이상 있을 수 없습니다. BIND PDU를 1시간 이상 경고해야 합니다.

연결 안정성 문제를 수정하는 방법:

* 불안정한 연결은 근본 원인은 아니지만 연결을 차단하는 다른 문제가 발생하는 경우가 많습니다. 근본 원인을 찾는 것이 우선 순위이다.

* 자세한 SMPP 추적을 활성화합니다. 연결이 다시 시작될 때 어떤 일이 발생하는지 확인할 수 있어야 합니다.

* 공급자가 `BIND PDU`s를 전송하는 경우 잘못된 것일 수 있습니다. `UNBING`이(가) 왜 전송되었는지 공급자에게 물어보십시오.

* 네트워크 캡처를 취하는 것이 연결이 닫힌 방식을 확인하는 유일한 방법일 수 있습니다.

* 공급자가 `TCP FIN` 또는 `TCP RST packet`을(를) 전송하여 연결을 종료하는 경우 자세한 내용을 공급자에게 문의하십시오.

* 공급자가 오류 코드와 함께 `DELIVER_SM_RESP` 같은 클린 오류를 보낸 후 연결을 종료하는 경우 다른 유형의 메시지가 전송되지 않도록 하는 커넥터를 별도로 수정하고 MTA 조절을 트리거해야 합니다. 연결을 닫으면 MT 및 SR 모두에 영향을 주는 트랜시버 모드에서 특히 중요합니다.

## MT(최종 사용자에게 전송되는 일반 SMS){#issue-MT} 전송 시 발생하는 문제

* 연결이 안정적인지 확인하십시오. SMPP 연결은 Adobe Campaign Classic의 발신자를 제외하고 최소 1시간 동안 계속 유지되어야 합니다. [불안정한 연결 문제](../../delivery/using/sms-protocol.md#issues-unstable-connection) 섹션을 참조하십시오.

* MTA를 다시 시작하면 일정 시간 동안 MT를 다시 보낼 수 있으므로 연결이 불안정하기 때문에 조절이 있을 수 있습니다. [불안정한 연결 문제](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) 섹션을 참조하십시오.

* 확장 로그가 있으며 올바른 날짜와 함께 올바른 상태를 확인하십시오. 그렇지 않은 경우 배송 또는 배달 준비 문제가 될 수 있습니다.

* MTA가 메시지를 실제로 처리하는지 확인합니다. 그렇지 않은 경우 SMS 문제가 아닐 수 있습니다.

* SMS 커넥터가 실제로 제공업체의 장비에 연결되어 있는지 확인합니다. 모든 시스템이 제대로 통신하는지 확인하려면 공급업체에 의견을 문의하십시오. 바인딩 프로세스에 대한 자세한 내용은 `BIND_TRANSMITTER` 및 `BIND_TRANSCEIVER PDU`s를 참조하십시오. 적절한 문제 해결을 위해 SMPP 추적을 활성화해야 할 수 있습니다.

* SMPP 추적이 활성화된 상태에서 `SUBMIT_SM PDU`에 올바른 정보가 포함되어 있는지 확인하십시오.

* 공급자가 &quot;OK&quot; 값(코드 0)과 함께 `SUBMIT_SM_RESP PDU`에 응답하는지 확인합니다. PDU가 적절한 지연과 함께 도착하는지 확인하십시오.1초 이상은 제공자와 논의해야 하며, 대개 100ms 이내에 도착합니다.

* 이러한 모든 단계가 제대로 작동하면 공급자 측에 문제가 있음을 확신할 수 있습니다. 그들은 자신의 플랫폼에서 문제 해결을 해야 할 것이다.

* 그래도 처리량이 일관되지 않으면 전송 창을 조정하고 MT 처리량을 낮춰 보십시오. 제공업체와 협력하여 조정해야 합니다. Adobe Campaign은 메시지를 매우 신속하게 보낼 수 있으므로 공급자의 장비에 성능 문제가 발생할 수 있습니다.

## MT가 중복됩니다(동일한 SMS가 한 행에 여러 번 전송됨){#duplicated-MT}

재시도에서 중복되는 경우가 많습니다. 메시지를 다시 시도할 때 중복이 있는 것은 정상이며, 다시 시도할 때 근본 원인을 제거하도록 시도해야 합니다.

* 정확히 60초 간격으로 전송된 중복 항목이 보이면 제공업체에서는 문제가 있을 수 있으며, 충분히 빠르게 `SUBMIT_SM_RESP`을(를) 보내지 않습니다.

* `BIND/UNBIND`이 많이 표시되면 연결이 불안정한 것입니다. 중복 메시지 문제를 해결하기 전에 솔루션에 대해 [불안정한 연결 문제](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) 섹션을 참조하십시오.

재시도가 있을 때 중복 항목 양 줄이기:

* 전송 창을 낮춥니다. 전송 창은 `SUBMIT_SM_RESP` 지연을 덮을 수 있을 만큼 커야 합니다. 이 값은 창이 가득 찬 동안 오류가 발생하는 경우 복제할 수 있는 최대 메시지 수를 나타냅니다.

## SR(배달 영수증) {#issue-process-SR} 처리 시 발생하는 문제

* 모든 유형의 SR 문제 해결을 수행하려면 SMPP 추적을 활성화해야 합니다.

* `DELIVER_SM PDU`이(가) 공급자로부터 오고 있으며 형식이 올바른지 확인하십시오.

* Adobe Campaign이 `DELIVER_SM_RESP PDU`에 성공하여 답글을 달았는지 확인합니다. Adobe Campaign Classic에서는 SMS 프로세스에서 지연된 처리를 위해 SR이 `providerMsgId` 테이블에 삽입되었음을 보장합니다.

`DELIVER_SM PDU`이(가) 성공적으로 확인되지 않으면 다음을 확인해야 합니다.

* **외부 계정**&#x200B;의 ID 추출 및 오류 처리와 관련하여 regex를 확인합니다. `DELIVER_SM PDU`의 컨텐츠에 대해 유효성을 검사해야 할 수 있습니다.

* `broadLogMsg` 테이블에서 오류가 올바르게 제공되었는지 확인합니다.

Adobe Campaign Classic 확장 SMPP 커넥터에서 `DELIVER_SM PDU`을(를) 확인했지만 broadLog가 제대로 업데이트되지 않은 경우 [일치하는 MT, SR 및 broadlog 항목](../../delivery/using/sms-protocol.md#matching-mt) 섹션에 설명된 ID 조정 프로세스를 확인하십시오.

유효하지 않은 SR이 제공자의 버퍼에 있지만 모든 문제를 해결했다면 &quot;잘못된 ID 확인 수&quot; 옵션을 사용하여 이러한 SR을 건너뛸 수 있습니다. 버퍼가 정리된 후 이를 주의해서 사용하고 가능한 한 빨리 0으로 재설정해야 합니다.

## MO(및 블랙 목록/자동 응답){#issue-process-MO} 처리 시 발생하는 문제

* 테스트 중에 SMPP 추적을 활성화합니다. TLS를 활성화하지 않는 경우 MO를 문제 해결할 때 네트워크 캡처를 수행하여 PDU에 올바른 정보가 포함되어 있고 올바른 형식이 지정되었는지 확인해야 합니다.

* 네트워크 트래픽을 캡처하거나 SMPP 추적을 분석할 때는 응답이 구성된 경우 MO 및 해당 응답 MT와의 전체 대화를 캡처해야 합니다.

* MO(`DELIVER_SM PDU`)가 추적에 나타나지 않으면 공급자 측에 문제가 있습니다. 그들은 자신의 플랫폼에서 문제 해결을 해야 할 것이다.

* `DELIVER_SM PDU`이(가) 나타나면 성공한 `DELIVER_SM_RESP PDU`(코드 0)과 함께 Adobe Campaign이 이 값을 알고 있는지 확인합니다. 이 RESP는 모든 처리 로직이 Adobe Campaign에 의해 적용되었음을 보장합니다(자동 응답 및 허용/차단 목록). 그렇지 않은 경우 SMS 프로세스 로그에서 오류 메시지를 검색합니다.

* 자동 응답이 활성화된 경우 `SUBMIT_SM`이(가) 공급자에게 전송되었는지 확인합니다. 그렇지 않은 경우 SMS 프로세스 로그에서 오류 메시지를 찾을 수 있습니다.

* 회신이 포함된 `SUBMIT_SM MT PDU`이(가) 추적에서 발견되었지만 SMS가 휴대폰에 도달하지 않은 경우 문제 해결에 대한 지원을 위해 공급자에게 문의해야 합니다.

## 배달 준비 중 격리된 받는 사람을 제외하지 않는 문제(자동 응답 기능으로 격리됨) {#issue-delivery-preparation}

* 전화 번호 형식이 격리 테이블과 배달 로그에서 정확히 동일한지 확인합니다. 그렇지 않은 경우 국제 전화 번호 형식의 더하기 접두어에 문제가 있는 경우 이 [섹션](../../delivery/using/sms-protocol.md#automatic-reply)을 참조하십시오.

* 짧은 코드를 확인합니다. 받는 사람의 짧은 코드가 외부 계정에 정의된 것과 동일하거나 비어 있는 경우(비어 있는 경우 = 임의의 단축 코드) 제외가 발생할 수 있습니다. 전체 Adobe Campaign 인스턴스에 짧은 코드가 하나만 사용되는 경우 모든 **짧은 코드** 필드를 비워 두는 것이 더 쉽습니다.

## 인코딩 문제 {#encoding-issues}

**1단계:공급자에게 문의**

그들에게 연락해서 그들에게 무슨 문제가 있는지 보세요. 고객이 문제가 자신의 편인지 또는 Adobe Campaign 쪽인지 파악할 수 있어야 합니다. Adobe Campaign에서 문제가 발생하면 어떤 필드가 잘못되었는지 정확하게 파악할 수 있어야 합니다.

**2단계:메시지에 포함된 내용 확인**

유니코드는 유사 문자에 대해 많은 변형을 허용하며 Adobe Campaign은 모든 문자를 처리할 수 없습니다.

가장 일반적인 문제 원인은 워드 프로세서에서 복사하여 붙여넣는 것으로, 일반적인 문자를 타이포그래피가 올바른 버전으로 바꿉니다.공백이 줄바꿈되지 않는 공백으로 변경되거나, 큰따옴표가 열기 및 닫기 따옴표로 변경되고, 빼기 기호는 다양한 종류의 하이픈 등으로 변경되었습니다.

테스트할 때 메시지를 복사하여 붙여넣지 말고 인터페이스에 항상 직접 메시지를 입력합니다.

16진수를 사용하여 유사한 문자 간의 차이를 구별할 수 있습니다. 소문자 L, 대문자 I, O, 0, 모든 서로 다른 유형의 인용 부호, 라틴어가 아닌 인코딩 또는 서로 다른 유형의 공백도 모두 동일하게 보이거나 전혀 표시되지 않을 수 있습니다.

유니코드를 16진수로 변환하려면 [유니코드 코드 변환기](https://r12a.github.io/app-conversion/) 웹 사이트와 같은 온라인 도구를 사용할 수 있습니다. 텍스트를 입력하고 전화 번호와 같은 PII가 없는지 확인하고 **변환**&#x200B;을 클릭합니다. 아래쪽의 16진수 값(UTF-32 영역)이 표시됩니다.

공급자 또는 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에서 인코딩 문제에 대한 티켓을 열 때는 항상 입력한 내용과 표시되는 내용에 대한 16진수 버전을 포함합니다.

**3단계:전송해야 하는 사항 파악**

사용할 인코딩을 결정하고 문자 표를 온라인으로 검색합니다. 전송하려는 문자를 대상 코드 페이지에서 실제로 사용할 수 있는지 확인합니다. `data_coding` 필드가 올바르고 사용자와 공급자가 예상하는 것과 일치하는지 확인합니다.

**4단계:실제로 전송한 내용 파악**

공급자에게 보내는 바이트를 정확하게 보려면 커넥터의 디버그 출력이 필요합니다. 인코딩 문제는 `SUBMIT_SM PDU`s에 표시되므로 캡처하십시오. 로그에서 찾을 수 있는 매우 뚜렷한 메시지를 보낼 수 있습니다.

테스트할 때 다양한 유형의 특수 문자를 보낼 수 있습니다. 예를 들어 GSM7 인코딩은 16진수 형식의 서로 매우 다른 확장 문자를 포함하므로 다른 인코딩에는 표시되지 않으므로 쉽게 찾을 수 있습니다.

## SMS 문제 {#element-include}에 대해 통신할 때 포함할 요소

SMS 문제, Adobe Campaign에 대한 지원 티켓 열기, SMS 제공업체 또는 이 문제에 대한 모든 종류의 통신 등 SMS 문제에 대한 지원을 요청할 때마다 적절한 자격을 갖추려면 다음 정보를 포함해야 합니다. 문제를 신속하게 해결하는 데 필요한 자격 조건을 갖춘 문제가 있습니다.

* **문제가 나타나면 자세한** SMPP 메시지를 활성화합니다. 대부분의 SMS 문제는 이것 없이는 해결할 수 없다.

* 문제가 SMS 트래픽과 관련된 경우 공급자에게 먼저 문의하십시오. 이러한 플랫폼은 실시간으로 SMS 트래픽 문제를 효율적으로 진단하는 데 가장 적합합니다.

* 그 문제에 대해 간단히 사실적인 설명을 포함하라.

* 예상 결과에 대한 설명을 포함합니다.

* 공급자의 피드백을 포함합니다.

* 관련 로그 및/또는 네트워크 캡처를 포함합니다. 캡처를 할 때는 캡처 중에 문제를 재현해야 합니다.

* 로그, 추적 또는 캡처를 포함하는 경우 문제가 나타날 때 파일의 정확한 위치를 정확히 찾아냅니다.

* 메시지, PDU 또는 로그를 참조하면 해당 타임스탬프를 명확하게 표시하여 찾기 쉬워집니다.

* 테스트 환경에서 문제를 재현해 보세요. 설정에 대해 잘 모르는 경우 테스트 환경에서 테스트해 보고 SMPP 추적을 통해 결과를 확인합니다. 일반적으로 프로덕션 환경에서 문제를 직접 보고하는 것보다 테스트 환경에서 복제된 문제를 보고하는 것이 좋습니다.

* 플랫폼에서 변경한 내용 또는 변경된 내용을 포함할 수 있습니다. 또한 공급자가 자체적으로 수행한 변경 사항을 포함합니다.

### 네트워크 캡처 {#network-capture}

네트워크 캡처가 반드시 필요한 것은 아닙니다. 일반적으로 자세한 SMPP 메시지는 충분합니다. 다음은 네트워크 캡처가 필요한지 확인하는 데 도움이 되는 몇 가지 지침입니다.

* 연결 문제가 발생했지만 자세한 내용은 `BIND_RESP PDU`을(를) 표시하지 않습니다.

* 오류 메시지가 없는 연결 해제, 낮은 수준 프로토콜 오류가 감지되면 커넥터의 일반적인 동작입니다.

* 공급자가 연결 해제/연결 해제 프로세스에 대해 불평합니다.

* 선택적 TLV 필드의 인코딩 문제.

* 서로 다른 연결 간에 트래픽이 섞여 있는 것으로 간주됩니다.

다른 모든 상황에서는 먼저 자세한 SMPP 메시지를 분석하고 자세한 정보 로그에 정보가 없는 경우에만 네트워크 캡처를 요청합니다.

경우에 따라 네트워크 트래픽을 캡처할 필요가 없습니다. 다음은 가장 일반적인 경우입니다.

* TLS 사용:TLS 트래픽은 암호화되므로 캡처할 수 없습니다.

* 성능 문제:로그에는 성능 문제를 추적하는 데 필요한 모든 정보가 포함되어 있습니다.

* 시간 설정 문제(`retry timing`, `enquire_link` 기간, 처리량 매핑 등)

* SR 구문 분석 및 처리:자세한 내용은 더 많은 컨텍스트를 제공하고 더 나은 프레젠테이션을 제공합니다.

* MO 처리(자동 회신, 격리).

* 실제 SMPP 트래픽이 포함되지 않는 오류:배달 준비, 메시지 센터 API 문제, 워크플로우 문제 등

## SMPP 추적을 사용하도록 설정하면 {#enabling-smpp-traces}

새로운 커넥터는 추적을 통한 확장 로깅을 지원합니다.SMPP. 추적은 표준 출력이 아니라 MTA 로그에 출력됩니다.

**외부 계정당 활성화(기본 설정 방법)**

1. **외부 계정**&#x200B;에서 로그 파일&#x200B;**에 있는 자세한 SMPP 추적 활성화를 선택합니다.**
1. 서버가 외부 계정을 다시 로드할 수 있도록 하려면 10분을 기다립니다.

지금 활성화되어야 합니다.

**구성에서 활성화**

`config-instance.xml` 파일에서 다음 매개 변수를 설정합니다.

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## 컨테이너 {#open-connections}에 대한 열린 연결 수 확인

컨테이너에서 열린 연결 수를 확인하려면 다음 명령을 사용할 수 있습니다.

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

지정된 포트에 대해 열린 연결 수가 나열됩니다. 여기 3600번 포트를 사용하고 있습니다

결과는 다음과 같습니다.

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

sms 프로세스에 대한 4개의 연결이 열렸으며 5명의 하위 페이지가 있는 mta당 2개의 연결이 열립니다.
