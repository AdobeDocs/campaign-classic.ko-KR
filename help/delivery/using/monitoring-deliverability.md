---
title: Adobe Campaign Classic의 전달 모니터링
description: Adobe Campaign Classic의 전달 가능성 모니터링에 대한 도구 및 지침에 대해 알아보십시오.
page-status-flag: never-activated
uuid: 0b5c5dbd-f532-4d8a-a255-9e6d88357d8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 0baef937-f00b-4fc4-8608-a870997be684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 74e1a883088d347cb1aab05d76b630c912411fc4
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---


# 게재 기능 모니터링{#monitoring-deliverability}

아래에서는 Adobe Campaign에서 제공하는 다양한 모니터링 도구에 대한 세부 정보와 배달 기능 모니터링에 대한 일부 추가 지침을 확인할 수 있습니다.

## 모니터링 도구 {#monitoring-tools}

Adobe Campaign에서 제공하는 기능을 사용하여 플랫폼 제공 여부를 모니터링할 수 있습니다.

전달 가능 패키지는 다음과 같은 액세스 권한을 제공합니다.

* 일상적인 전달 성능(기술 모니터링)을 위한 기술 추적 보고서 On-Demand로 제공되는 이 보고서를 사용하면 지정된 주소로 이메일로 일일 보고서를 받을 수 있습니다. 자세한 내용은 Adobe 고객 지원 센터에 문의하십시오.
* 주요 이메일 클라이언트에서 [메시지를 미리 보고 컨텐츠와 명성을 스캔할 수 있는 받은 편지함 렌더링 보고서](../../delivery/using/inbox-rendering.md) .
* 메시지 품질 개요(받은 편지함, 스팸).

다음 도구를 사용할 수도 있습니다.

* 이 **[!UICONTROL Delivery throughput]** 보고서는 지정된 기간 동안 전체 플랫폼의 처리량에 대한 개요를 제공합니다. 자세한 내용은 [이 섹션을 참조하십시오](../../reporting/using/global-reports.md#delivery-throughput).
* 이 **[!UICONTROL Technical deliverability monitoring]** 보고서에는 플랫폼용 전달 품질 지표가 여러 개 포함되어 있습니다. 자세한 내용은 [이 섹션을 참조하십시오](#technical-deliverability-monitoring).
* 각 배달은 서로 다른 인터넷 서비스 공급자(ISP)에 대한 브로드캐스트 통계 보고서를 생성합니다. 다음 숫자를 포함하여 배달능력에 영향을 줄 수 있는 데이터 품질 및 평판 지표를 보여줍니다.
   * **[!UICONTROL Hard bounces]** 데이터 품질을 나타냅니다. 이 숫자는 2% 미만이어야 합니다.
   * **[!UICONTROL Soft bounces]** 평판이 표시됩니다. 해당 ISP의 경우 이 숫자는 10%보다 높지 않아야 합니다.
   자세한 내용은 [배달 통계](../../reporting/using/global-reports.md#delivery-statistics) 섹션을 참조하십시오.
* 일반적으로 [배달 대시보드는](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) 다음과 같은 액세스 권한을 제공합니다.
   * 전송 세부 사항과 성공 시 전송, 처리 및 전송할 메시지 [수](../../delivery/using/monitoring-a-delivery.md#delivery-summary)를 보여주는 배달 요약 [](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent) ;
   * 어느 대상이 제외되었는지와 그 이유를 보여주는 [배달 로그 및 내역](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history);
   * 열기 및 클릭과 같은 추적 정보를 표시하는 [추적 로그](../../delivery/using/monitoring-a-delivery.md#tracking-logs).

## 모니터링 지침 {#monitoring-guidelines}

다음은 제공 능력 모니터링에 대한 몇 가지 추가 지침입니다.

* 전체 플랫폼에 대한 [배달 처리량을](../../reporting/using/global-reports.md#delivery-throughput) 정기적으로 확인하여 원래 설정과 일치하는지 확인합니다.
* 배달 템플릿에서 [재시도](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 횟수가 올바르게 설정되어 있는지(재시도 기간은 30분, 재시도 횟수는 20회 이상) 확인합니다.
* 정기적으로 [바운스](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) 사서함에 액세스할 수 있으며 계정이 만료되지 않도록 확인합니다.
* 각 배달 처리량을 확인하여 배달 컨텐츠의 유효성(예: &#39;flash sales&#39;는 며칠이 아니라 몇 분 만에 배달됩니다.)
* 파도를 사용할 때 [각 파동이 다음 파동이 트리거되기 전에 마무리할 시간이 충분한지 확인합니다](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* 오류 수와 새 [검역소가](../../delivery/using/understanding-quarantine-management.md) 다른 배달물과 일치하는지 확인하십시오.
* 강조 표시된 오류 유형(회색 또는 검정 목록, DNS 문제, 스팸 방지 규칙 등)을 확인하려면 [배달 로그에](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) 자세히 문의하십시오.

## 신호 스팸 {#signal-spam}

Signal Spam은 프랑스 ISP(Orange, SFR)에 대해 익명화된 피드백 루프 보고를 제공하는 프랑스 서비스입니다.

* 이 서비스를 사용하면 프랑스 ISP의 명성을 따르고 고객의 활동 진화를 추적할 수 있습니다.

* Signal Spam은 최종 사용자가 전용 인터페이스를 통해 로그인하는 직접 불만 사항을 제공합니다. 그런 불만은 이메일 주소 데이터베이스로부터 격리된다.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) 는 IP, 도메인 블랙 리스트 및 평판 지표를 제공하는 Adobe 전달 능력 내부 툴에 대한 보완 모니터링 솔루션입니다.

제공된 정보는 실시간으로 제공되므로 적극적인 지원을 받을 수 있습니다.

## 기술 제공 능력 모니터링 보고서 {#technical-deliverability-monitoring}

기술 제공 모니터링 보고서는 매일 업데이트되며 **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** 으로 이동하고 Adobe Campaign **[!UICONTROL Technical monitoring]** 탭에서 **[!UICONTROL Home]** 링크를 클릭하여 사용할 수 있습니다. 플랫폼에 적합한 다양한 전달 품질 지표가 포함되어 있습니다.

이 표시기는 매일 오전 9시에 업데이트됩니다.

>[!NOTE]
>
>또한 지정된 주소로 일일 보고서를 이메일로 받을 수 있습니다. 이메일 또는 Adobe Campaign Extranet을 통해 요청된 이메일 주소를 알려주십시오.

![](assets/s_tn_del_monitoring.png)

다음 지표가 보고서에서 사용됩니다.

* **[!UICONTROL Reverse DNS]** : Adobe Campaign은 IP 주소에 대해 역 DNS가 제공되는지 그리고 이것이 IP를 올바르게 가리키는지 확인합니다.

* **[!UICONTROL SPF]** (보낸 사람 정책 프레임워크): ISP 및 사서함 공급자가 이메일 보낸 사람이 전송 도메인에서 인증되었는지 확인할 수 있는 인증 메커니즘입니다.

* **[!UICONTROL DomainKeys]** : Yahoo가 개발한 서비스로, 이메일 발신자의 신원을 인증합니다.

* **[!UICONTROL IP and RBL domain]** (실시간 블랙홀 목록): 잘못된 전송 평판을 가진 blocklist 조직에 의해 플래그가 지정된 IP 주소 및 도메인 목록. 이러한 목록은 Spamhaus, Spamcop, SURBL/URIBL 등과 같은 전용 조직에서 유지 관리합니다. Adobe Campaign은 현재 전달 가능성에 상당한 영향을 미치는 RBL을 기준으로 검사 과정을 진행하고 있습니다. 이러한 RBL은 전송 명성을 반영하며, 이메일을 받기 위해 수락하기 전에 ISP가 참조할 수 있습니다.

* **[!UICONTROL SNDS]** (스마트 네트워크 데이터 서비스): Windows [Live Hotmail 스팸 방지 서비스](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail은 이러한 유형의 정보를 제공하는 유일한 ISP입니다. 벤치마크 점수는 녹색 필터 결과, 불만 비율이 0.1% 미만이고 스팸 트랩은 0입니다.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
