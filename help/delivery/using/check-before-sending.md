---
product: campaign
title: 보내기 전 확인
description: 메시지가 준비되면 보내기 전에 모든 검사를 수행하십시오
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Deliverability
role: User
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 4%

---

# 보내기 전에 모든 확인 수행 {#perform-all-checks}

메시지가 준비되면 모든 디바이스에서 해당 콘텐츠가 올바르게 표시되고 잘못된 개인화 또는 링크가 끊어지는 등의 오류가 없는지 확인합니다.

메시지를 보내기 전에 매개 변수 및 구성이 게재와 일치하는지 확인하십시오.

## 유효성 검사가 중요한 이유 {#validation-is-key}

게재를 보내기 전에 받는 사람이 실제로 보낼 메시지를 받게 해야 합니다. 이렇게 하려면 메시지 콘텐츠 및 게재 매개 변수의 유효성을 검사해야 합니다.

이 단계를 통해 가능한 오류를 감지하고 수정한 후 주 타겟에 전달할 수 있습니다.

게재 유효성 검사 단계가 표시됩니다 [이 섹션에서](steps-validating-the-delivery.md).

## 받은 편지함 렌더링 {#inbox-and-email-rendering}

받은 편지함 렌더링을 사용하면 주요 이메일 클라이언트에서 메시지를 미리 보고, 콘텐츠 및 평판을 검사하고, 수신자가 메시지를 읽는 방식을 발견할 수 있습니다.

**팁**:

* 웹 메일, 메시지 서비스, 모바일 등 수신 가능한 다양한 컨텍스트에서 전송된 메시지를 볼 수 있습니다.

* 받은 편지함 렌더링 기능은 이메일 캠페인이 주요 ISP(인터넷 서비스 공급자) 및 웹 메일 서비스의 필터를 성공적으로 통과했는지 여부를 식별하는 데 중요합니다. 이러한 도구는 테스트 받은 편지함 네트워크로 전자 메일의 사전 사본을 보내므로 이러한 서비스에서 메시지가 표시되거나 렌더링되는 방법을 알 수 있습니다. 또한 게재 능력을 향상시키는 것을 신속하게 식별하고 수정하는 데 도움이 되는 보고서 및 코드 수정 옵션이 포함될 수 있습니다.

자세히 알아보기 [이 섹션에서](inbox-rendering.md).

## 증명 메시지 {#proof-messages}

증명을 보내면 옵트아웃 링크, 미러 페이지 및 기타 링크를 확인하고, 메시지의 유효성을 검사하고, 이미지가 표시되는지 확인하고, 가능한 오류를 감지하는 등의 작업을 수행할 수 있습니다. 다른 장치에서 디자인과 렌더링을 확인할 수도 있습니다.

자세히 알아보기 [이 섹션에서](steps-validating-the-delivery.md#sending-a-proof).

## A/B 테스트 게재 설정 {#a-b-testing-deliveries}

이메일 게재에 대한 콘텐츠가 여러 개 있는 경우 A/B 테스트를 사용하여 타겟팅된 모집단에 가장 큰 영향을 주는 버전을 확인할 수 있습니다.

**팁**:

* 일부 수신자에게 다른 버전 보내기

* 성공률이 가장 높은 프로그램을 선택하여 나머지 타겟으로 보냅니다.

자세히 알아보기 [이 섹션에서](get-started-a-b-testing.md).

## 메시지가 전달되었는지 확인합니다. {#make-sure-your-message-is-delivered}

마지막 단계로, 기회를 극대화하고 Adobe Campaign Classic의 기능을 활용하여 메시지가 관련 수신자에게 실제로 전달되도록 하십시오.

### 유효성 검사 프로세스 진행

Adobe Campaign 연산자 및 그룹을 포함하는 전체 유효성 검사 프로세스를 정의하여 대상과 메시지 콘텐츠의 유효성을 모두 검사할 수 있습니다. 이를 통해 타겟팅, 콘텐츠, 예산, 추출 및 증명 전송과 같은 캠페인의 다양한 프로세스를 완벽하게 모니터링하고 제어할 수 있습니다. 사용자는 권한에 따라 알림을 받고 증명을 받으며 메시지를 확인 또는 거부할 수 있습니다. 자세히 알아보기 [이 섹션에서](../../campaign/using/marketing-campaign-approval.md).

### 예약된 일괄 처리 사용

웨이브를 사용하여 전송되는 볼륨을 점진적으로 늘릴 수 있습니다. 이렇게 하면 메시지가 스팸으로 표시되거나 하루에 메시지 수를 제한하려는 경우를 방지할 수 있습니다. 웨이브를 사용하여 동시에 대량의 메시지를 전송하는 대신 게재를 여러 배치로 나눌 수 있습니다. 자세히 알아보기 [이 섹션에서](steps-sending-the-delivery.md#sending-using-multiple-waves).

### 메시지 우선 순위 지정

우선 순위 수준을 입력하여 게재의 전송 순서를 설정할 수 있습니다. 방법은 다음과 같습니다.

1. 게재 속성을 편집하고 **[!UICONTROL Delivery]** 탭.

1. 다음에서 배율로 게재의 우선 순위 수준을 정의합니다. **[!UICONTROL Very low]** 끝 **[!UICONTROL Very high]**.

>[!NOTE]
>
>게재 내에서 메시지를 보내는 순서를 정의할 수 없습니다.

### IP 선호도 설정

아웃바운드 SMTP 트래픽을 더 잘 제어하기 위해 각 선호도에 사용할 수 있는 특정 IP 주소를 정의하여 선호도를 관리할 수 있습니다. 이를 통해 시스템 또는 출력 주소에 대한 특정 게재에 대한 이메일 수를 제한할 수 있습니다. 예를 들어 국가 또는 하위 도메인당 하나의 관심도를 사용할 수 있습니다. 그런 다음 국가당 하나의 유형화를 만들고 각 친화성을 해당 유형화에 연결할 수 있습니다.

다음을 수행할 수 있습니다.

* serverConf.xml 구성 파일에서 IP 관심도를 정의합니다. [자세히 알아보기](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 각 IPAffinity 요소에 대해 사용할 수 있는 IP 주소를 선언합니다. [자세히 알아보기](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 다음에서 [유형화](../../campaign-opt/using/about-campaign-typologies.md) 원하는 경우 다음을 사용하십시오. **[!UICONTROL Managing affinities with IP addresses]** 해당 선호도를 관리하는 게재 서버(MTA)에 게재를 연결하는 필드입니다. [자세히 알아보기](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic)

* 이메일이 전송되면 헤더를 확인하여 게재가 전송된 IP 주소를 확인하십시오. 이메일 관리자가 헤더 정보를 얻는 데 도움을 줄 수 있습니다.

* SMS 게재의 경우 SMS 채널에 다음으로 제한된 전용 관심도가 있는지 확인하십시오. **1** 애플리케이션 서버 컨테이너입니다. [자세히 알아보기](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

>[!NOTE]
>
>이러한 단계의 대부분은 전문가 사용자만이 수행할 수 있습니다.

### 유형화 사용

유형화 규칙을 사용하여 특정 기준에 따라 대상의 일부를 제외할 수 있습니다. 따라서 전송된 메시지는 회사 커뮤니케이션 정책을 준수하면서 고객의 요구 사항과 기대치에 가장 적합한 메시지를 제공합니다. 예를 들어 뉴스레터의 대상에서 미성년인 수신자를 필터링할 수 있습니다. 자세히 알아보기 [이 예에서](../../campaign-opt/using/filtering-rules.md).

### 첨부 파일 방지

첨부 파일은 특히 대량으로 전송되는 경우 맬웨어의 확산에 가장 일반적인 벡터 중 하나로 유지됩니다. 문서에 첨부하는 대신 보안 링크를 포함하십시오. 이렇게 하면 의도하지 않은 재배포를 방지하기 위해 추가 보안 계층을 보장하고 메시지 크기 또는 보안상의 이유로 인바운드 이메일 게이트웨이에서 메시지가 거부되는 가능성을 크게 줄일 수 있습니다.
