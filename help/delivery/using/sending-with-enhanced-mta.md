---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic에서 향상된 MTA로 보내기
description: Adobe Campaign Enhanced MTA를 통해 이메일을 전송하는 범위와 특정 기능에 대해 알아보십시오.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 07ed17a093cb6fb2d7aae376325a127c61b1dcc2
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 2%

---


# 향상된 MTA {#sending-with-enhanced-mta}로 보내기

**Adobe Campaign Enhanced MTA**(메일 전송 에이전트)는 향상된 전송 인프라를 제공하여 배달, 평판, 처리량, 보고, 바운스 처리, IP 경사 업 및 연결 설정 관리를 개선할 수 있도록 해줍니다.

확장성을 향상시키고 전달 처리량을 높이며 더 많은 이메일을 더 빨리 전송할 수 있도록 구현되었습니다. 이는 인터넷 서비스 공급자의 피드백을 기반으로 이메일 전송 설정을 실시간으로 변경하는 새로운 적응형 전달 기술을 통해 이루어집니다.

>[!IMPORTANT]
>
>Adobe Campaign 향상된 MTA는 Campaign Classic 호스팅 또는 하이브리드 고객에게만 제공됩니다. 향상된 MTA를 사용하도록 Campaign Classic 온-프레미스 설치를 업그레이드할 수 없습니다.

2018년 9월 이후 Campaign Classic 인스턴스를 프로비저닝한 경우 향상된 MTA를 사용합니다. 다른 모든 Campaign Classic 고객의 경우 아래의 [FAQ](#enhanced-mta-faq)를 참조하십시오.

향상된 MTA 구현은 일부 기존 캠페인 기능에 영향을 줄 수 있습니다. 자세한 내용은 [향상된 MTA 사양](#enhanced-mta-impacts)을 참조하십시오.

## 자주 묻는 질문 {#enhanced-mta-faq}

### 사용 및 이점

**향상된 MTA 소개**

이제 Adobe Campaign을 업그레이드하여 SparkPost의 상업용 이메일 MTA인 **Momum**&#x200B;을(를) 실행하는 새로운 MTA(메일 전송 에이전트)를 사용할 수 있습니다.

Momentum은 더욱 스마트해진 바운스 처리 및 전송자가 최적의 받은 편지함 전달 비율을 달성 및 유지 관리할 수 있는 자동화된 전달 방식 최적화 기능이 포함된 혁신적인 고성능 MTA 기술을 제공합니다.<!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**이점은 무엇입니까?**

* 향상된 MTA를 사용하는 Adobe Campaign 클라이언트는 전체 처리량 속도가 <!--300%-->크게 증가하고 소프트 바운스 수가 크게 감소했습니다.<!--90%+-->
* 향상된 MTA는 최신 MTA 기술을 사용하여 이메일 전달을 위한 최적의 처리량 속도를 제공합니다.
* 수신한 피드백을 즉각적이고 자동으로 적용함으로써 실시간 전달 데이터를 통해 보다 정확하고 지능적인 이메일 전달을 보장합니다.

**기본 Adobe Campaign MTA와 향상된 MTA를 동시에 사용할 수 있습니까?**

아니. 인스턴스가 업그레이드된 후에는 향상된 MTA만 이메일 배달에 사용할 수 있습니다.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 향상된 MTA로 업그레이드

**향상된 MTA로 업그레이드하려면 무엇이 필요합니까?**

2018년 9월 이후에 Campaign Classic 인스턴스를 프로비저닝한 경우 이미 향상된 MTA를 사용하고 있으므로 작업이 필요하지 않습니다.

다른 호스팅 또는 부분적으로 호스팅되는(하이브리드) 모든 고객을 위해 Adobe Campaign 팀은 마이그레이션 날짜를 조정하도록 노력하고 마이그레이션에 필요한 해당 단계에 대한 세부 정보를 제공합니다.

>[!IMPORTANT]
>
>향상된 MTA는 온-프레미스 설치에서 사용할 수 없습니다.

**인스턴스를 향상된 MTA로 업그레이드하는 프로세스는 어떻게 됩니까?**

호스팅 인스턴스를 위한 전체 프로세스는 몇 분 동안 다운타임이 필요합니다. Adobe은 이메일 처리량과 수신 능력을 최대 24시간 동안 모니터링하여 이메일 전달에 미치는 영향을 평가합니다.

문제가 발견될 경우 Adobe은 인스턴스를 기본 Adobe Campaign MTA로 신속하고 일시적으로 되돌릴 수 있습니다.

현재 향상된 MTA는 이메일 채널에만 영향을 줍니다. 푸시 알림 및 SMS 배달은 기본 캠페인 MTA를 계속 사용하며 업그레이드해도 어떠한 방식으로든 영향을 받지 않습니다.

**향상된 MTA로 업그레이드한 후 다시 IP 온난화를 수행해야 합니까?**

아니. 업그레이드하더라도 새 IP로 전환할 필요가 없으므로 기존의 따뜻한 이메일 IP를 계속 사용할 수 있습니다.

**향상된 MTA로 업그레이드하면 현재 진행 중인 캠페인 또는 게재에 영향을 미칩니까?**

새 MTA를 제대로 사용하려면 인스턴스가 업그레이드되기 전에 준비된 모든 게재는 다시 준비해야 합니다.

Adobe Campaign 트랜잭션 메시징 기능을 사용하는 고객의 경우 이메일을 트리거하는 모든 API 호출은 매우 짧은 업그레이드 중단 시간 동안 큐에 올라가 있고 업그레이드가 완료되면 시도합니다.

## 향상된 MTA 특성 {#enhanced-mta-impacts}

### 향상된 MTA 헤더

최신 Campaign Classic 인스턴스에는 모든 메시지에 필요한 향상된 MTA 헤더를 추가하는 코드가 포함되어 있습니다. Adobe Campaign 19.1(빌드 9032) 이상을 사용하는 경우 이 경우 &quot;useMomum=true&quot; 매개 변수를 마케팅 인스턴스 구성([serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) 파일)에 추가해야 합니다.

그러나 이 코드를 포함하지 않는 이전 인스턴스를 사용하는 경우, **[!UICONTROL Typology Rule for Enhanced MTAs]**이라는 새 분류 규칙을 캠페인 인스턴스의 모든 기존 유형 분류에 추가해야 합니다.
이 규칙은 향상된 MTA 업그레이드의 일부로 설치된 **[!UICONTROL Typology]** 패키지에 의해 추가됩니다.

>[!IMPORTANT]
>
>유형 분류에서 이 유형 분류 규칙을 볼 경우, 어떤 식으로든 삭제하거나 수정하지 마십시오. 그렇지 않으면 이메일 배달이 부정적인 영향을 받을 수 있습니다.

이 **[!UICONTROL Typology]** 패키지는 Adobe Campaign 마케팅 인스턴스에 설치해야 합니다.

하이브리드 고객인 경우 Adobe Campaign 팀은 향상된 MTA로의 업그레이드의 일부로 마케팅 인스턴스에 **[!UICONTROL Typology]** 패키지를 설치하는 방법에 대한 지침을 제공합니다. 자세한 내용은 계정 담당자에게 문의하십시오.

>[!IMPORTANT]
>
>Adobe Campaign 팀에서 **[!UICONTROL Typology]** 패키지를 설치하는 방법에 대해 제공하는 지침을 신중하게 따라야 합니다. 그렇지 않으면 이메일을 보내는 데 사용된 IP에 문제가 발생할 수 있습니다.

유형 분류에 대한 자세한 내용은 [이 섹션](../../campaign/using/about-campaign-typologies.md)을 참조하십시오.

### 새 MX 규칙

MX 관리 전달 처리량 규칙은 더 이상 사용되지 않습니다. 향상된 MTA에는 MX 규칙이 있어 고유한 내역 이메일 명성을 기반으로 그리고 이메일을 보내는 도메인에서 오는 실시간 피드백에 따라 처리량을 도메인별로 사용자 정의할 수 있습니다.

MX 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration)을 참조하십시오.

### 바운스 자격 조건

캠페인 **[!UICONTROL Delivery log qualification]** 테이블의 바운스 자격 조건은 더 이상 **동기** 배달 실패 오류 메시지에 사용되지 않습니다. 향상된 MTA는 바운스 유형 및 자격을 결정하고 해당 정보를 Campaign에 다시 전송합니다.

>[!NOTE]
>
>향상된 MTA는 SMTP 바운스를 식별하며 해당 자격을 캠페인 바운스 이유 및 자격에 매핑된 바운스 코드 형태로 Campaign에 다시 보냅니다.

바운스 자격에 대한 자세한 내용은 [이 섹션](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)을 참조하십시오.

### 향상된 MTA를 사용하여 보낸 상태

소프트 및 하드 바운스 수가 향상된 MTA에서 캠페인에 다시 보고됨에 따라 이메일 배달 [대시보드](../../delivery/using/delivery-dashboard.md)의 **[!UICONTROL Success]** 보기에서 **[!UICONTROL Summary]** 비율은 100%에서 시작하여 배달 [유효성 기간](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)까지 점진적으로 감소합니다.

실제로 모든 메시지는 Campaign에서 향상된 MTA로 성공적으로 전달되는 즉시 [전송 로그](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)에 **[!UICONTROL Sent]**&#x200B;으로 표시됩니다. 해당 메시지에 대한 [바운스](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)이(가) 향상된 MTA에서 캠페인으로 다시 전달되지 않는 한 해당 상태로 유지됩니다.

하드 바운스 메시지가 향상된 MTA에서 다시 보고되면 해당 상태가 **[!UICONTROL Sent]**&#x200B;에서 **[!UICONTROL Failed]**(으)로 변경되고 그에 따라 **[!UICONTROL Success]** 비율이 감소합니다.

소프트 바운스 메시지가 향상된 MTA에서 다시 보고될 때 여전히 **[!UICONTROL Sent]**&#x200B;으로 표시되고 **[!UICONTROL Success]** 백분율은 아직 업데이트되지 않았습니다. 소프트 바운스 메시지는 배달 유효 기간 동안 [다시 시도됨](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure):

* 유효성 기간이 끝나기 전에 재시도가 성공하면 메시지 상태는 **[!UICONTROL Sent]**&#x200B;으로 유지되며 **[!UICONTROL Success]** 비율은 변경되지 않습니다.

* 그렇지 않으면 상태가 **[!UICONTROL Failed]**&#x200B;으로 변경되고 그에 따라 **[!UICONTROL Success]** 백분율이 감소합니다.

따라서 최종 **[!UICONTROL Success]** 비율과 실제 **[!UICONTROL Sent]** 및 **[!UICONTROL Failed]** 메시지의 최종 수를 보려면 유효 기간이 끝날 때까지 기다려야 합니다.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 게재 처리량

캠페인 배달 처리량 그래프는 더 이상 이메일 수신자에게 처리량을 표시하지 않습니다. 이제 해당 그래프는 향상된 MTA로 Campaign에서 메시지를 릴레이 처리량을 보여줍니다.

배달 처리량에 대한 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.

### 유효 기간

캠페인 배달의 유효성 기간 설정은 **3.5일 이내로**&#x200B;로 설정된 경우에만 향상된 MTA에서 사용됩니다. Campaign에서 3.5일이 넘는 값을 정의하면 이 값을 고려하지 않습니다.

예를 들어 유효성 기간이 Campaign에서 기본값 5일로 설정된 경우 소프트 바운싱 메시지는 향상된 MTA 재시도 큐로 이동하고 해당 메시지가 향상된 MTA에 도달하는 시점부터 최대 3.5일까지 다시 시도됩니다. 이 경우 캠페인에 설정된 값은 사용되지 않습니다.

메시지가 3.5일 동안 Enhanced MTA 큐에 있고 게재에 실패하면 시간이 초과되고 게재 로그에서 해당 상태가 **[!UICONTROL Sent]**&#x200B;에서 **[!UICONTROL Failed]**(으)로 업데이트됩니다.

유효 기간에 대한 자세한 내용은 [이 섹션](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)을 참조하십시오.

### DKIM-signing

DKIM(DomainKeys Identified Mail) 이메일 인증 서명은 향상된 MTA를 통해 수행됩니다. 기본 캠페인 MTA의 DKIM 서명은 향상된 MTA 업그레이드의 일부로 도메인 관리 테이블 내에서 해제됩니다.
DKIM에 대한 자세한 내용은 [이 섹션](../../delivery/using/technical-recommendations.md#dkim)을 참조하십시오.