---
product: campaign
title: Adobe Campaign Classic에서 Enhanced MTA로 보내기
description: Adobe Campaign Enhanced MTA로 이메일 전송 범위 및 특성에 대해 알아봅니다
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 1%

---

# Enhanced MTA로 보내기 {#sending-with-enhanced-mta}

**Adobe Campaign Enhanced MTA**(메일 전송 에이전트)은(는) 개선된 전송 인프라를 제공하여 게재 능력, 신뢰도, 처리량, 보고, 바운스 처리, IP 램프 업 및 연결 설정 관리를 개선합니다.

확장성을 개선하고 게재 처리량을 늘리며 더 많은 이메일을 더 빠르게 전송할 수 있도록 구현됩니다. 이는 인터넷 서비스 공급자의 피드백을 기반으로 이메일 전송 설정을 실시간으로 변경하는 새로운 적응형 전달 기술로 달성할 수 있습니다.

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA는 Campaign Classic 호스팅 또는 하이브리드 고객만 사용할 수 있습니다. 향상된 MTA를 사용하도록 Campaign Classic 온-프레미스 설치를 업그레이드할 수 없습니다.

2018년 9월 이후에 Campaign Classic 인스턴스가 프로비저닝된 경우 Enhanced MTA를 사용하고 있습니다. 다른 모든 Campaign Classic 고객의 경우 아래의 [자주 묻는 질문](#enhanced-mta-faq)을 참조하십시오.

Enhanced MTA 구현이 기존 Campaign 기능 중 일부에 영향을 줄 수 있습니다. 자세한 내용은 [향상된 MTA 특성](#enhanced-mta-impacts)을 참조하세요.

>[!NOTE]
>
>Adobe Campaign의 최종 사용자이고 인스턴스가 Enhanced MTA로 업그레이드되었는지 확인하려면 내부 Campaign 관리자에게 문의하십시오.

## 자주 묻는 질문 {#enhanced-mta-faq}

### 사용 및 이점

**Enhanced MTA란 무엇입니까?**

이제 Adobe Campaign을 업그레이드하여 SparkPost의 상업용 이메일 MTA(**모멘텀**)을 실행하는 새 MTA(메일 전송 에이전트)를 사용할 수 있습니다.

모멘텀은 발송자가 최적의 받은 편지함 게재 비율을 달성하고 유지하는 데 도움이 되는 자동화된 게재 능력 최적화 기능과 더 스마트한 바운스 처리를 포함하는 혁신적인 고성능 MTA 기술을 나타냅니다. <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**어떤 이점이 있습니까?**

* Enhanced MTA를 사용하는 Adobe Campaign 클라이언트의 경우 전체 처리량 속도가 <!--300%-->크게 증가하고 소프트 바운스도 <!--90%+-->크게 감소했습니다.
* Enhanced MTA는 최신 MTA 기술을 사용하여 이메일 게재에 최적의 처리량 속도를 제공합니다.
* 또한 수신되는 피드백에 즉시 자동으로 적용되므로 실시간 게재 데이터를 통해 보다 정확하고 지능적인 이메일 게재를 보장합니다.

**기본 Adobe Campaign MTA와 향상된 MTA를 동시에 사용할 수 있습니까?**

아니요. 인스턴스가 업그레이드된 후 Enhanced MTA만 이메일 게재에 사용할 수 있습니다.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 향상된 MTA로 업그레이드

**Enhanced MTA로 업그레이드하는 데 필요한 사항은 무엇입니까?**

2018년 9월 이후에 Campaign Classic 인스턴스가 프로비저닝된 경우 이미 Enhanced MTA를 사용하고 있으므로 작업이 필요하지 않습니다.

다른 모든 호스팅 또는 부분적으로 호스팅(하이브리드) 고객의 경우 Adobe Campaign 팀은 마이그레이션 날짜를 조정하고 마이그레이션에 필요한 적절한 단계에 대한 세부 정보를 제공합니다.

>[!IMPORTANT]
>
>Enhanced MTA는 온-프레미스 설치에 사용할 수 없습니다.

**인스턴스를 향상된 MTA로 업그레이드하는 프로세스는 무엇입니까?**

호스팅된 인스턴스의 전체 프로세스를 수행하려면 몇 분 정도의 다운타임이 필요합니다. Adobe은 업그레이드 후 최대 24시간 동안 이메일 처리량 및 게재 가능성을 모니터링하여 이메일 게재에 미치는 영향을 평가합니다.

문제가 발견되면 Adobe은 인스턴스를 빠르고 일시적으로 기본 Adobe Campaign MTA로 되돌릴 수 있습니다.

현재 Enhanced MTA는 이메일 채널에만 영향을 줍니다. 푸시 알림 및 SMS 게재는 기본 Campaign MTA를 계속 사용하며 업그레이드에 의해 어떠한 영향도 받지 않습니다.

**Enhanced MTA로 업그레이드한 후 IP warming을 다시 수행해야 합니까?**

아니요. 업그레이드하면 새 IP로 전환할 필요가 없으므로 기존의 따뜻한 이메일 IP를 계속 사용할 수 있습니다.

**Enhanced MTA로 업그레이드하면 현재 진행 중인 캠페인이나 게재에 영향을 줍니까?**

Adobe Campaign 트랜잭션 메시지 기능을 사용하는 고객의 경우, 매우 짧은 업그레이드 다운타임 동안 이메일을 트리거하기 위한 모든 API 호출이 대기열에 추가되며 업그레이드가 완료되면 시도됩니다.

## 향상된 MTA 특성 {#enhanced-mta-impacts}

### 새 MX 규칙

MX 관리 게재 처리량 규칙은 더 이상 사용되지 않습니다. Enhanced MTA에는 자체 MX 규칙이 있어 사용자의 과거 전자 메일 신뢰도와 전자 메일을 보내는 도메인에서 오는 실시간 피드백에 따라 도메인별로 처리량을 사용자 정의할 수 있습니다.

MX 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration)을(를) 참조하십시오.

### 바운스 자격 조건

Campaign **[!UICONTROL Delivery log qualification]** 테이블의 반송 조건은 **동기** 게재 실패 오류 메시지에 더 이상 사용되지 않습니다. Enhanced MTA는 바운스 유형 및 자격을 결정하고 해당 정보를 Campaign에 다시 전송합니다.

>[!NOTE]
>
>Enhanced MTA는 SMTP 바운스를 인증하고 해당 인증을 캠페인 바운스 사유 및 자격에 매핑된 바운스 코드 형태로 Campaign에 다시 전송합니다.

바운스 자격에 대한 자세한 내용은 [이 섹션](understanding-delivery-failures.md#bounce-mail-qualification)을 참조하세요.

### 게재

Campaign에 **[!UICONTROL Stopped]** 상태로 표시되더라도 Enhanced MTA로 전송되면 게재를 중단할 수 없습니다.

### 게재 처리량

Campaign 게재 처리량 그래프는 이메일 수신자에게 더 이상 처리량을 표시하지 않습니다. 이제 이 그래프는 Campaign에서 Enhanced MTA로 메시지를 릴레이하는 처리량 속도를 보여 줍니다.

게재 처리량에 대한 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput)을 참조하세요.

### 재시도

게재의 다시 시도 설정은 Campaign에서 더 이상 사용되지 않습니다. 소프트 바운스 재시도 및 재시도 간 시간은 메시지 이메일 도메인에서 돌아오는 바운스 응답의 유형 및 심각도에 따라 고급 MTA에 의해 결정됩니다.

다시 시도에 대한 자세한 내용은 [이 섹션](steps-sending-the-delivery.md#configuring-retries)을 참조하세요.

### 유효 기간

Campaign 게재의 유효 기간 설정은 **3.5일 이하**(으)로 설정된 경우에만 Enhanced MTA에서 사용됩니다. Campaign에서 3.5일보다 큰 값을 정의하는 경우 값이 고려되지 않습니다.

예를 들어 Campaign에서 유효 기간을 기본값 5일로 설정하면 소프트 바운싱 메시지가 Enhanced MTA로 다시 시도되고 해당 메시지가 Enhanced MTA에 도달한 후 최대 3.5일 동안만 다시 시도됩니다. 이 경우 Campaign에 설정된 값은 사용되지 않습니다.

메시지가 3.5일 동안 Enhanced MTA 큐에 있고 게재에 실패하면 시간이 초과되고 게재 로그에서 **[!UICONTROL Sent]**&#x200B;에서 **[!UICONTROL Failed]**(으)로 상태가 업데이트됩니다.

유효 기간에 대한 자세한 내용은 [이 섹션](steps-sending-the-delivery.md#defining-validity-period)을 참조하세요.

### DKIM 서명

DKIM(DomainKeys Identified Mail) 전자 메일 인증 서명은 Enhanced MTA에서 수행합니다. 기본 Campaign MTA에 의한 DKIM 서명은 Enhanced MTA 업그레이드의 일부로 도메인 관리 테이블 내에서 꺼집니다.
DKIM에 대한 자세한 내용은 [Adobe 게재 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=ko#authentication)를 참조하세요.

### 게재 성공 보고

이메일 게재 [대시보드](delivery-dashboard.md)의 **[!UICONTROL Summary]** 보기에서 **[!UICONTROL Success]** 백분율은 100%에서 시작되며 게재 [유효 기간](steps-sending-the-delivery.md#defining-validity-period) 동안 점진적으로 낮아집니다. 이때 소프트 및 하드 바운스가 Enhanced MTA에서 Campaign으로 다시 보고됩니다.

실제로 모든 메시지는 Campaign에서 Enhanced MTA로 성공적으로 릴레이되는 즉시 [전송 로그](delivery-dashboard.md#delivery-logs-and-history)에 **[!UICONTROL Sent]**(으)로 표시됩니다. 해당 메시지에 대한 [바운스](understanding-delivery-failures.md#delivery-failure-types-and-reasons)가 Enhanced MTA에서 Campaign으로 다시 통신되지 않는 한 또는 통신될 때까지 이 상태는 유지됩니다.

하드 바운스 메시지가 Enhanced MTA에서 다시 보고되면 상태가 **[!UICONTROL Sent]**&#x200B;에서 **[!UICONTROL Failed]**(으)로 변경되고 **[!UICONTROL Success]** 비율이 그에 따라 감소합니다.

소프트 바운싱 메시지가 Enhanced MTA에서 다시 보고되는 경우에도 **[!UICONTROL Sent]**(으)로 표시되고 **[!UICONTROL Success]** 비율이 아직 업데이트되지 않았습니다. 그러면 소프트 바운싱 메시지는 게재 유효 기간 동안 [다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)됩니다.

* 유효 기간이 끝나기 전에 다시 시도하면 메시지 상태는 **[!UICONTROL Sent]**(으)로 유지되며 **[!UICONTROL Success]** 비율은 변경되지 않습니다.

* 그렇지 않으면 상태가 **[!UICONTROL Failed]**(으)로 변경되고 **[!UICONTROL Success]** 비율이 그에 따라 감소합니다.

따라서 최종 **[!UICONTROL Success]** 비율과 실제 **[!UICONTROL Sent]** 및 **[!UICONTROL Failed]** 메시지 수를 보려면 유효 기간이 끝날 때까지 기다려야 합니다.

아래 표에는 해당 KPI 및 전송 로그 상태와 함께 전송 프로세스의 다양한 단계가 나와 있습니다.

| 전송 프로세스의 단계 | KPI 요약 | 전송 로그 상태 |
|--- |--- |--- |
| 메시지가 Campaign에서 Enhanced MTA로 성공적으로 릴레이 | **[!UICONTROL Success]** 백분율이 100%에서 시작 | 전송됨 |
| 하드 바운싱 메시지가 Enhanced MTA에서 다시 보고됨 | **[!UICONTROL Success]** 비율이 이에 따라 감소함 | 실패 |
| 소프트 바운싱 메시지는 Enhanced MTA에서 다시 보고됨 | **[!UICONTROL Success]** 백분율 변경 없음 | 전송됨 |
| 소프트 바운싱 메시지 다시 시도 성공 | **[!UICONTROL Success]** 백분율 변경 없음 | 전송됨 | **[!UICONTROL Success]** 비율이 이에 따라 증가함 | 전송됨 |
| 소프트 바운싱 메시지 다시 시도 실패 | **[!UICONTROL Success]** 비율이 이에 따라 감소함 | 실패 |

