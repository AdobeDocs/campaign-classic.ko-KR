---
product: campaign
title: Adobe Campaign Classic에서 향상된 MTA를 사용한 S
description: Adobe Campaign Enhanced MTA를 사용하여 전자 메일을 보내는 범위와 특성에 대해 알아봅니다
feature: Email
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1946'
ht-degree: 4%

---

# Enhanced MTA로 보내기 {#sending-with-enhanced-mta}

![](../../assets/common.svg)

다음 **Adobe Campaign Enhanced MTA** (Mail Transfer Agent)는 향상된 전송 인프라를 제공하여 게재 능력, 평판, 처리량, 보고, 반송 처리, IP 램프 업 및 연결 설정 관리를 제공합니다.

확장성을 향상시키고 게재 처리량을 늘리고 더 많은 이메일을 더 빨리 보내는 데 도움이 되도록 구현되었습니다. 이는 인터넷 서비스 공급자의 피드백을 기반으로 이메일 전송 설정을 실시간으로 변경하는 새로운 적응형 전달 기술을 통해 달성됩니다.

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA는 호스팅 또는 하이브리드 고객에게만 제공됩니다. 향상된 MTA를 사용하도록 Campaign Classic 온-프레미스 설치를 업그레이드할 수 없습니다.

2018년 9월 이후에 Campaign Classic 인스턴스가 프로비저닝된 경우 향상된 MTA를 사용합니다. 기타 모든 Campaign Classic 고객의 경우 [FAQ](#enhanced-mta-faq) 아래의 제품에서 사용할 수 있습니다.

향상된 MTA 구현은 기존 Campaign 기능 중 일부에 영향을 줄 수 있습니다. 자세한 내용은 [향상된 MTA 특성](#enhanced-mta-impacts).

>[!NOTE]
>
>Adobe Campaign의 최종 사용자로서 인스턴스가 향상된 MTA로 업그레이드되었는지 확인하려면 내부 Campaign 관리자에게 문의하십시오.

## 자주 묻는 질문 {#enhanced-mta-faq}

### 사용 및 이점

**Enhanced MTA란 무엇입니까?**

이제 Adobe Campaign을 업그레이드하여 SparkPost의 상업용 이메일 MTA라는 MTA를 실행하는 새로운 MTA(Mail Transfer Agent)를 사용할 수 있습니다 **모멘텀**.

모멘텀은 보다 스마트한 반송 처리 및 보낸 사람이 최적의 받은 편지함 배달률을 달성하고 유지하는 데 도움이 되는 자동화된 게재 기능 최적화 기능을 포함하는 혁신적이고 고성능 MTA 기술을 나타냅니다. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**어떤 이점이 있습니까?**

* Enhanced MTA를 사용하는 Adobe Campaign 클라이언트가 <!--300%-->전체 처리량 속도 증가 및 <!--90%+-->소프트 바운스의 상당한 감소.
* Enhanced MTA는 최신 MTA 기술을 사용하여 이메일 배달을 위한 최적의 처리량 속도를 제공합니다.
* 수신한 피드백에 즉시 자동으로 적용함으로써 실시간 게재 데이터를 통해 보다 정확하고 지능적인 이메일 전달을 보장합니다.

**네이티브 Adobe Campaign MTA와 Enhanced MTA를 동시에 사용할 수 있습니까?**

아니요. 인스턴스가 업그레이드된 후에는 향상된 MTA만 이메일 게재에 사용할 수 있습니다.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 향상된 MTA로 업그레이드

**Enhanced MTA로 업그레이드하는 데 필요한 것은 무엇입니까?**

2018년 9월 이후에 Campaign Classic 인스턴스가 프로비저닝된 경우, 이미 Enhanced MTA를 사용하고 있으므로 작업이 필요하지 않습니다.

호스팅 또는 부분적으로 호스팅(하이브리드) 중인 다른 모든 고객의 경우 Adobe Campaign 팀이 마이그레이션 날짜를 조정하도록 연락하여 마이그레이션에 필요한 적절한 단계에 대한 세부 정보를 제공합니다.

>[!IMPORTANT]
>
>Enhanced MTA는 온-프레미스 설치에 사용할 수 없습니다.

**인스턴스를 Enhanced MTA로 업그레이드하는 프로세스는 무엇입니까?**

호스팅된 인스턴스에 대한 전체 프로세스는 몇 분의 다운타임이 필요합니다. Adobe은 이메일 처리량과 게재 능력을 최대 24시간 업그레이드 후 모니터링하여 이메일 게재에 미치는 영향을 평가합니다.

문제가 발견된 경우 Adobe은 인스턴스를 일시 중단 없이 기본 Adobe Campaign MTA로 되돌릴 수 있습니다.

현재 향상된 MTA는 이메일 채널에만 영향을 줍니다. 푸시 알림 및 SMS 게재는 기본 Campaign MTA를 계속 사용하며 업그레이드의 영향을 받지 않습니다.

**Enhanced MTA로 업그레이드한 후 IP 온난화를 다시 수행해야 합니까?**

아니요. 업그레이드하지 않아도 새 IP로 전환되므로 기존의 따뜻하게 구성된 이메일 IP를 계속 사용할 수 있습니다.

**Enhanced MTA로 업그레이드하면 현재 진행 중인 캠페인 또는 게재에 영향을 줍니까?**

새 MTA를 제대로 사용하려면 인스턴스가 업그레이드되기 전에 준비된 모든 게재를 다시 준비해야 합니다.

Adobe Campaign 트랜잭션 메시지 기능을 사용하는 고객의 경우 이메일을 트리거하는 모든 API 호출은 매우 짧은 업그레이드 중단 시간 동안 큐에 있다가 업그레이드가 완료되면 시도됩니다.

## 향상된 MTA 특성 {#enhanced-mta-impacts}

### 향상된 MTA 헤더

최신 Campaign Classic 인스턴스에는 모든 메시지에 필요한 향상된 MTA 헤더를 추가하는 코드가 포함되어 있습니다. Adobe Campaign 19.1(빌드 9032) 이상을 사용 중이며 그렇지 않은 경우 요청해야 합니다 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) &quot;useMomentum=true&quot; 매개 변수를 실행 인스턴스 구성에 추가하려면( [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) 파일). [중간 소싱 인스턴스](../../installation/using/mid-sourcing-server.md), 또는 [트랜잭션 메시지 실행 인스턴스](../../message-center/using/configuring-instances.md#execution-instance), 구성에 따라 다릅니다.

그러나 이 코드를 포함하지 않는 이전 인스턴스를 사용하는 경우 라는 새 유형화 규칙을 사용합니다 **[!UICONTROL Typology Rule for Enhanced MTAs]** 는 Campaign 인스턴스의 모든 기존 유형화에 추가해야 합니다.
이 규칙은 **[!UICONTROL Typology]** Enhanced MTA로의 업그레이드의 일부로 설치된 패키지

>[!IMPORTANT]
>
>유형화에서 이 유형화 규칙이 표시되면 어떤 식으로든 삭제하거나 수정하지 마십시오. 그렇지 않으면 이메일 게재에 부정적인 영향을 줄 수 있습니다.

이 **[!UICONTROL Typology]** Adobe Campaign 마케팅 인스턴스에 패키지를 설치해야 합니다.

하이브리드 클라이언트인 경우 Adobe Campaign 팀이 을 설치하는 방법에 대한 지침을 제공합니다 **[!UICONTROL Typology]** enhanced MTA로 업그레이드하는 일부로 마케팅 인스턴스에 패키지를 제공합니다. 자세한 지침은 계정 담당자에게 문의하십시오.

>[!IMPORTANT]
>
>Adobe Campaign 팀이 설치 방법에 대해 제공하는 지침 **[!UICONTROL Typology]** 소포를 주의 깊게 지켜라. 그렇지 않으면 이메일을 전송하는 데 사용되는 IP에 중요한 문제가 발생할 수 있습니다.

유형화에 대한 자세한 내용은 [이 섹션](../../campaign-opt/using/about-campaign-typologies.md).

### 새 MX 규칙

MX 관리 게재 처리량 규칙은 더 이상 사용되지 않습니다. Enhanced MTA에는 자체 MX 규칙을 사용하여 사용자의 과거 전자 메일 신뢰도를 기반으로, 전자 메일을 전송하는 도메인에서 오는 실시간 피드백에 따라 도메인별로 처리량을 사용자 정의할 수 있습니다.

MX 구성에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration).

### 반송 자격

Campaign의 반송 자격 **[!UICONTROL Delivery log qualification]** 표는 더 이상 **동기** 게재 실패 오류 메시지. Enhanced MTA가 반송 유형 및 조건을 결정하고 해당 정보를 Campaign으로 다시 전송합니다.

>[!NOTE]
>
>Enhanced MTA는 SMTP 바운스를 자격을 부여하고 해당 자격을 Campaign 반송 이유 및 자격에 매핑된 반송 코드 형태로 Campaign에 다시 전송합니다.

바운스 자격에 대한 자세한 내용은 [이 섹션](understanding-delivery-failures.md#bounce-mail-qualification).

### 게재 처리량

Campaign 게재 처리량 그래프는 더 이상 이메일 수신자에게 처리량을 표시하지 않습니다. 이제 해당 그래프는 Campaign에서 Enhanced MTA로 메시지 릴레이에 대한 처리량 속도를 보여줍니다.

게재 처리량에 대한 자세한 내용은 [이 섹션](../../reporting/using/global-reports.md#delivery-throughput).

>[!NOTE]
>
>사용 [이메일 피드백 서비스](#email-feedback-service) (EFS) 기능(현재 베타로 사용 가능), Campaign 게재 처리량 그래프는 전자 메일 수신자에 대한 처리량을 계속 표시합니다.

### 유효 기간

Campaign 게재의 유효 기간 설정은 **3.5일 이하**. Campaign에서 3.5일 이상의 값을 정의하면 고려되지 않습니다.

예를 들어 유효 기간이 Campaign에서 기본값 5일로 설정된 경우 소프트 바운스 메시지는 Enhanced MTA 다시 시도 큐로 전환되고 해당 메시지가 Enhanced MTA에 도달한 후 최대 3.5일 동안 다시 시도됩니다. 이 경우 Campaign에 설정된 값은 사용되지 않습니다.

메시지가 3.5일 동안 Enhanced MTA 큐에 있고 게재에 실패하면 시간이 초과되고 게재 로그에서 해당 상태가 **[!UICONTROL Sent]**&#x200B;에서 **[!UICONTROL Failed]**(으)로 업데이트됩니다.

유효 기간에 대한 자세한 내용은 [이 섹션](steps-sending-the-delivery.md#defining-validity-period).

### DKIM 서명

DKIM(DomainKeys Identified Mail) 전자 메일 인증 서명은 Enhanced MTA에서 수행합니다. 기본 Campaign MTA의 DKIM 서명은 Enhanced MTA 업그레이드의 일부로 도메인 관리 테이블 내에서 꺼집니다.
DKIM에 대한 자세한 내용은 [Adobe 게재 가능성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 게재 성공 보고

에서 **[!UICONTROL Summary]** 이메일 게재 보기 [대시보드](delivery-dashboard.md), **[!UICONTROL Success]** 백분율은 100%에서 시작하여 게재 내내 점진적으로 내려갑니다 [유효 기간](steps-sending-the-delivery.md#defining-validity-period)를 반환합니다.

실제로 모든 메시지는 **[!UICONTROL Sent]** 에서 [로그 전송](delivery-dashboard.md#delivery-logs-and-history) campaign에서 Enhanced MTA로 성공적으로 중계되는 즉시 이 경우, 또는 [바운스](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 해당 메시지는 Enhanced MTA에서 Campaign으로 다시 전달됩니다.

하드 바운스 메시지가 향상된 MTA에서 다시 보고되면 상태가 **[!UICONTROL Sent]** to **[!UICONTROL Failed]** 그리고 **[!UICONTROL Success]** 백분율이 그에 따라 감소합니다.

소프트 바운스 메시지가 향상된 MTA에서 다시 보고되면 여전히 으로 표시됩니다 **[!UICONTROL Sent]** 그리고 **[!UICONTROL Success]** 백분율이 아직 업데이트되지 않았습니다. 그러면 소프트 바운스 메시지가 표시됩니다 [다시 시도](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 게재 유효 기간 동안:

* 유효성 기간이 종료되기 전에 다시 시도하면 메시지 상태는 다음과 같이 유지됩니다 **[!UICONTROL Sent]** 그리고 **[!UICONTROL Success]** 백분율은 변경되지 않은 상태로 유지됩니다.

* 그렇지 않으면 상태가 **[!UICONTROL Failed]** 그리고 **[!UICONTROL Success]** 백분율이 그에 따라 감소합니다.

따라서 최종 결과를 보려면 유효 기간이 끝날 때까지 기다려야 합니다 **[!UICONTROL Success]** 백분율과 실제 **[!UICONTROL Sent]** 및 **[!UICONTROL Failed]** 메시지.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 이메일 피드백 서비스(베타) {#email-feedback-service}

피드백을 Enhanced MTA(메시지 전송 에이전트)에서 직접 캡처하므로 EFS(이메일 피드백 서비스) 기능을 사용하면 각 이메일의 상태가 정확하게 보고됩니다.

>[!IMPORTANT]
>
>이메일 피드백 서비스 는 현재 베타 기능으로 사용할 수 있습니다.
>
>이 베타 프로그램에 참여하시려면 다음을 작성해 주십시오 [이 양식](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) 다시 연락드리겠습니다.

게재를 시작하면 에는 변경 사항이 없습니다 **[!UICONTROL Success]** 메시지가 Campaign에서 Enhanced MTA로 성공적으로 중계되는 경우의 백분율입니다.

<!--![](assets/efs-sending.png)-->

게재 로그에는 **[!UICONTROL Taken into account by the service provider]** 타겟팅된 각 주소의 상태입니다.

<!--![](assets/efs-pending.png)-->

메시지가 실제로 타겟팅된 프로필에 전달되고, Enhanced MTA에서 이 정보가 실시간으로 다시 보고되면 게재 로그에는 **[!UICONTROL Sent]** 메시지를 성공적으로 받은 각 주소의 상태입니다. 다음 **[!UICONTROL Success]** 백분율이 게재의 각 성공에따라 증가합니다.

하드 바운스 메시지가 향상된 MTA에서 다시 보고되면 로그 상태가 **[!UICONTROL Taken into account by the service provider]** to **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

소프트 바운스 메시지가 Enhanced MTA에서 다시 보고되면 로그 상태가 변경되지 않은 상태로 유지됩니다(**[!UICONTROL Taken into account by the service provider]**): 유일한 [오류 원인](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 업데이트됨<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. 다음 **[!UICONTROL Success]** 백분율은 변경되지 않은 상태로 유지됩니다. 그런 다음 소프트 바운스 메시지가 게재 동안 다시 시도됩니다 [유효 기간](steps-sending-the-delivery.md#defining-validity-period):

* 유효 기간이 끝나기 전에 재시도가 성공하면 메시지 상태가 **[!UICONTROL Sent]** 그리고 **[!UICONTROL Success]** 백분율이 그에 따라 증가합니다.

* 그렇지 않으면 상태가 **[!UICONTROL Failed]**. 다음 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->백분율은 변경되지 않은 상태로 유지됩니다.

>[!NOTE]
>
>하드 및 소프트 바운스에 대한 자세한 내용은 [이 섹션](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>일시적 게재 실패 후 다시 시도하는 방법에 대한 자세한 내용은 [이 섹션](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


아래 표는 EFS 기능에서 도입된 KPI 및 전송 로그 상태의 변경 사항을 보여줍니다.

**이메일 피드백 서비스 사용**

| 전송 프로세스의 단계 | KPI 요약 | 전송 로그 상태 |
|--- |--- |--- |
| 메시지가 Campaign에서 Enhanced MTA로 성공적으로 전달되었습니다 | **[!UICONTROL Success]** 백분율이 표시되지 않음(0%에서 시작) | 서비스 공급자가 고려함 |
| 하드 바운스 메시지가 향상된 MTA에서 다시 보고됩니다 | 에서 변경 없음 **[!UICONTROL Success]** 백분율 | 실패 |
| 소프트 바운스 메시지는 Enhanced MTA에서 다시 보고됩니다 | 에서 변경 없음 **[!UICONTROL Success]** 백분율 | 서비스 공급자가 고려함 |
| 소프트 바운스 메시지 다시 시도 성공 | **[!UICONTROL Success]** 백분율이 그에 따라 증가함 | 전송됨 |
| 소프트 바운스 메시지 다시 시도 실패 | 에서 변경 없음 **[!UICONTROL Success]** 백분율 | 실패 |

**이메일 피드백 서비스 제외**

| 전송 프로세스의 단계 | KPI 요약 | 전송 로그 상태 |
|--- |--- |--- |
| 메시지가 Campaign에서 Enhanced MTA로 성공적으로 전달되었습니다 | **[!UICONTROL Success]** 백분율이 100%에서 시작됨 | 전송됨 |
| 하드 바운스 메시지가 향상된 MTA에서 다시 보고됩니다 | **[!UICONTROL Success]** 백분율이 그에 따라 감소하다 | 실패 |
| 소프트 바운스 메시지는 Enhanced MTA에서 다시 보고됩니다 | 에서 변경 없음 **[!UICONTROL Success]** 백분율 | 전송됨 |
| 소프트 바운스 메시지 다시 시도 성공 | 에서 변경 없음 **[!UICONTROL Success]** 백분율 | 전송됨 | **[!UICONTROL Success]** 백분율이 그에 따라 증가함 | 전송됨 |
| 소프트 바운스 메시지 다시 시도 실패 | **[!UICONTROL Success]** 백분율이 그에 따라 감소하다 | 실패 |
