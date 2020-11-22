---
solution: Campaign Classic
product: campaign
title: 보내기 전 확인
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 4%

---


# 보내기 전에 모든 확인 수행 {#perform-all-checks}

메시지가 준비되면, 모든 장치에서 해당 컨텐츠가 올바르게 표시되는지 확인하고, 개인화나 깨진 링크 등의 오류를 포함하지 마십시오.

메시지를 보내기 전에 매개 변수 및 구성이 전달과 일치하는지 확인하십시오.

## 유효성 검사가 중요한 이유 {#validation-is-key}

배달을 보내기 전에 받는 사람이 실제로 보내려는 메시지를 받게 해야 합니다. 이렇게 하려면 메시지 내용 및 배달 매개 변수의 유효성을 확인해야 합니다.

이 단계를 통해 가능한 오류를 감지하여 주 타겟으로 전달하기 전에 수정할 수 있습니다.

배달을 확인하는 단계는 이 섹션 [에 나와 있습니다](../../delivery/using/steps-validating-the-delivery.md).

## 받은 편지함 렌더링 {#inbox-and-email-rendering}

받은 편지함 렌더링을 사용하면 주요 이메일 클라이언트에서 메시지를 미리 보고, 컨텐츠와 명성을 스캔하고, 수신자가 어떻게 메시지를 읽고 있는지 파악할 수 있습니다.

**팁**:

* 수신될 수 있는 다른 컨텍스트에서 보낸 메시지를 볼 수 있습니다.웹메일, 메시지 서비스, 모바일 등

* 받은 편지함 렌더링 기능은 이메일 캠페인이 주요 ISP(Internet Service Providers)와 웹 메일 서비스의 필터를 성공적으로 통과하는지 여부를 식별하기 위해 중요합니다. 이러한 도구는 이메일의 시험판 사본을 테스트 받은 편지함의 네트워크로 전송하므로, 이러한 서비스에서 메시지가 어떻게 표시되거나 렌더링되는지 확인할 수 있습니다. 또한 보고서 및 코드 교정 옵션을 포함하여 빠르게 식별하고 전달을 개선하는 수정 사항을 만들 수 있습니다.

이 섹션 [에서 자세히 알아보십시오](../../delivery/using/inbox-rendering.md).

## 증명 메시지 {#proof-messages}

교정본을 전송하면 옵트아웃 링크, 미러 페이지 및 기타 링크를 확인하고, 메시지를 확인하고, 이미지가 표시되는지 확인하고, 가능한 오류 감지 등을 수행할 수 있습니다. 또한 다양한 디바이스에서 디자인과 렌더링을 확인할 수 있습니다.

이 섹션 [에서 자세히 알아보십시오](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## A/B 테스트 배달 설정 {#a-b-testing-deliveries}

이메일 전달에 필요한 컨텐츠가 여러 개 있는 경우 A/B 테스트를 사용하여 타깃팅된 모집단에게 가장 큰 영향을 미치는 버전을 확인할 수 있습니다.

**팁**:

* 수신자의 일부에게 다른 버전 보내기

* 성공률이 가장 높은 타겟을 선택하고 나머지 타겟으로 보냅니다.

이 섹션 [에서 자세히 알아보십시오](../../workflow/using/a-b-testing.md).

## 메시지가 전달되었는지 확인 {#make-sure-your-message-is-delivered}

마지막 단계로 Adobe Campaign Classic의 역량을 최대한 발휘하여 관련 수신자에게 메시지를 전달할 수 있습니다.

### 유효성 검사 프로세스 진행

Adobe Campaign 연산자 및 그룹이 포함된 전체 유효성 검사 프로세스를 정의하여 대상 및 메시지 컨텐츠의 유효성을 모두 확인할 수 있습니다. 이렇게 하면 캠페인의 다양한 프로세스를 완전히 모니터링하고 제어할 수 있습니다.타깃팅, 컨텐츠, 예산, 추출 및 증명 전송 사용 권한에 따라 사용자에게 알림 메시지를 전송하고 증거 기록을 수신하며 메시지의 유효성을 검사하거나 거부할 수 있습니다. 이 섹션 [에서 자세히 알아보십시오](../../campaign/using/marketing-campaign-approval.md#approval-process).

### 파도 사용

물결을 사용하여 보낸 양을 점진적으로 늘릴 수 있습니다. 이렇게 하면 메시지가 스팸으로 표시되거나 일별 메시지 수를 제한하려는 경우 피됩니다. 파도를 사용하면 대량의 메시지를 동시에 보내지 않고 여러 개의 배치로 배달을 나눌 수 있습니다. 이 섹션 [에서 자세히 알아보십시오](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

### 메시지 우선 순위 지정

우선순위 수준을 표시하여 게재에 대한 전송 주문을 설정할 수 있습니다. 방법은 다음과 같습니다.

1. 배달 속성을 편집하고 **[!UICONTROL Delivery]** 탭을 선택합니다.

1. 배달에 대한 우선 순위 레벨을 척도에서 **[!UICONTROL Very low]** 로 정의합니다 **[!UICONTROL Very high]**.

>[!NOTE]
>
>배달 내에서 메시지를 보내는 순서를 정의할 수 없습니다.

### IP 친화성 설정

아웃바운드 SMTP 트래픽을 더 잘 제어하기 위해 각 관련성에 사용할 수 있는 특정 IP 주소를 정의하여 친화성을 관리할 수 있습니다. 이를 통해 시스템이나 출력 주소로 특정 게재에 대한 이메일 수를 제한할 수 있습니다. 예를 들어 국가 또는 하위 도메인마다 하나의 관련성을 사용할 수 있습니다. 그런 다음 국가별로 하나의 유형을 만들고 각 관련성을 해당 유형에 연결할 수 있습니다.

다음을 수행할 수 있습니다.

* serverConf.xml 구성 파일에서 IP 기능을 정의합니다. [자세히 알아보기](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 각 IPAfferity 요소에 대해 사용할 수 있는 IP 주소를 선언합니다. [자세히 알아보기](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 선택한 [유형](../../campaign/using/about-campaign-typologies.md) 에서 **[!UICONTROL Managing affinities with IP addresses]** 필드를 사용하여 해당 관련성을 관리하는 배달 서버(MTA)에 배달을 연결합니다. [자세히 알아보기](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic)

* 이메일이 전송되면 헤더를 확인하여 배달을 보낸 IP 주소를 확인합니다. 이메일 관리자가 헤더 정보를 가져오는 데 도움이 됩니다.

>[!NOTE]
>
>이러한 대부분의 단계는 전문가 사용자만이 수행할 수 있습니다.

### 유형 지정 사용

유형 규칙을 사용하여 특정 기준에 따라 대상의 일부를 제외할 수 있습니다. 따라서 전송된 메시지는 회사 커뮤니케이션 정책을 준수하면서 고객의 요구 사항과 기대치에 가장 적합한 메시지를 제공합니다. 예를 들어 뉴스레터의 대상에서 미성년자인 수신자를 필터링할 수 있습니다. 이 예제 [에서 자세히 알아보십시오](../../campaign/using/filtering-rules.md).

### 첨부 파일 방지

첨부 파일은 맬웨어의 확산을 위한 가장 일반적인 벡터 중 하나로 남아 있으며, 특히 대량으로 전송될 때 더욱 그렇습니다. 문서를 첨부하지 않고 문서에 대한 보안 링크를 포함합니다. 이로 인해 의도하지 않은 재배포를 방지할 수 있는 추가 보안 레이어가 보장되고 메시지 크기나 보안상의 이유로 인바운드 이메일 게이트웨이에 메시지가 거부될 가능성이 크게 줄어듭니다.
