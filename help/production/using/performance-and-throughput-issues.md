---
product: campaign
title: 성능 및 처리량 문제
description: 성능 및 처리량 문제
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 5%

---

# 성능 및 처리량 문제{#performance-and-throughput-issues}



먼저 최신 빌드가 설치되어 있는지 확인해야 합니다. 이렇게 하면 최신 기능과 버그 수정 사항이 있습니다.

다음을 참조하십시오. [릴리스 정보](../../rn/using/latest-release.md) 각 릴리스의 콘텐츠에 대한 자세한 내용을 보려면 .

## 하드웨어 및 인프라 {#hardware-and-infrastructure}

온-프레미스 Campaign Classic에 대한 하드웨어 요구 사항에 대한 일반 지침은 이에 대해 자세히 설명합니다 [페이지](https://helpx.adobe.com/kr/campaign/kb/hardware-sizing-guide.html).

컨설팅 팀은 데이터베이스의 다양한 유형의 테이블에서 사용되는 공간의 양과 SFTP 사이트에서 사용되는 공간을 쉽게 볼 수 있는 도구를 호스트된 고객에게 제공할 수 있습니다. 불필요한 데이터를 정리할 수 있는 도구를 추가로 제공합니다. 연락처 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 이 도구를 구현해야 하는 경우 이 도구를 사용하여 확인해야 할 몇 가지 중요한 사항은 다음과 같습니다.

* 인덱스 크기가 테이블 크기보다 큰 경우 진공이 필요합니다.
* 최대 열이 있는 테이블을 확인합니다. 이러한 테이블을 자주 사용하는 경우 진공 청소기로 청소해야 합니다.
* 데이터베이스 차단으로 인해 이메일 전송이 중지될 수 있습니다.

Adobe Campaign은 [도구](../../production/using/monitoring-processes.md#manual-monitoring) cpu 및 RAM 사용량을 확인합니다. 이 도구를 사용하여 다음과 같은 특정 지표를 확인합니다. **메모리**, **메모리 교체**, **디스크**, **활성 프로세스**. 값이 너무 높으면 워크플로우 수를 줄이거나 다른 시간에 시작하도록 워크플로우를 예약할 수 있습니다.

## 데이터베이스 검사 {#database-performances}

대부분의 경우 성능 문제는 데이터베이스 유지 관리와 관련이 있습니다. 확인할 주요 항목은 다음과 같습니다.

* 구성: 초기 Adobe Campaign 플랫폼 구성을 확인하고 전체 하드웨어 검사를 실행하는 것이 좋습니다.
* Adobe Campaign 플랫폼 설치 및 구성: 네트워크 구성 및 플랫폼 전달성 옵션을 확인합니다.
* 데이터베이스 유지 관리: 데이터베이스 정리 작업이 작동 중인지 확인하고 데이터베이스 유지 관리가 올바르게 예약 및 실행되었는지 확인합니다. 작업 테이블의 수와 크기를 확인합니다.
* 실시간 진단: 프로세스 및 플랫폼 로그 파일을 확인한 다음 문제를 다시 만드는 동안 데이터베이스 작업을 모니터링합니다.

>[!NOTE]
>
>자세한 정보는 이 섹션 을 참조하십시오. [데이터베이스 성능](../../production/using/database-performances.md).

## 애플리케이션 구성 {#application-configuration}

다음은 애플리케이션 구성 모범 사례와 관련된 문서 목록입니다.

* MTA 및 MTAChild 프로세스 및 메모리: **mta** 모듈이 메시지를 해당 모듈에 배포함 **일치 항목** 하위 모듈. 각 **일치 항목** 통계 서버에서 인증을 요청하고 전송하기 전에 메시지를 준비합니다. 다음을 참조하십시오. [페이지](../../installation/using/email-deliverability.md) 추가 정보.
* TLS 구성: TLS를 전역적으로 활성화하면 처리량을 줄일 수 있으므로 권장되지 않습니다. 대신 전달성 팀에서 관리하는 도메인별 TLS 설정은 필요에 따라 조정해야 합니다. 다음을 참조하십시오. [페이지](../../installation/using/email-deliverability.md#mx-configuration) 추가 정보.
* DKIM: DKIM의 보안 수준을 보장하기 위해 권장되는 암호화 크기로 1024b를 사용하는 것이 좋습니다. 낮은 DKIM 키는 대부분의 액세스 공급자에서 유효한 것으로 간주되지 않습니다. [이 페이지](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)를 참조하십시오.

## 전달성 문제 {#deliverability-issues}

다음은 전달성과 관련된 모범 사례 및 문서 목록입니다.

* IP 신뢰도: IP 신뢰도가 충분하지 않으면 성능에 영향을 줍니다. 다음 **게재 기능 모니터링** 모듈은 플랫폼의 전달성 성능을 추적하는 다양한 도구를 제공합니다. 다음을 참조하십시오. [페이지](../../delivery/using/monitoring-deliverability.md).
* IP 준비: IP 준비는 게재 가능성 팀이 수행합니다. 여기에는 몇 주 동안 새 IP를 통해 이메일 수가 점차적으로 증가합니다.
* IP 선호도 설정: 잘못된 IP 선호도 설정은 이메일을 모두 중지하거나(구성에서 잘못된 연산자/선호도 이름) 처리량을 줄일 수 있습니다(선호도에 있는 적은 수의 IP). 다음을 참조하십시오. [페이지](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* 이메일 크기: 이메일 크기는 처리량에 중요한 역할을 합니다. 권장되는 최대 이메일 크기는 60KB입니다. 다음을 참조하십시오. [페이지](https://helpx.adobe.com/legal/product-descriptions/campaign.html). 다음에서 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput) 시간별로 전송된 바이트 수를 확인합니다.
* 부적합한 수신자 많음: 부적합한 수신자가 많으면 처리량에 영향을 줄 수 있습니다. MTA가 잘못된 수신자에게 이메일 전송을 계속 재시도합니다. 데이터베이스가 잘 관리되고 있는지 확인하십시오.
* 개인화 양: 게재가 &quot;개인화 진행 중&quot;에 있는 경우 개인화 블록에 사용된 JavaScript를 확인하십시오.

>[!NOTE]
>
>다음 항목도 참조하십시오. [전달성](../../delivery/using/about-deliverability.md) 섹션. 전달성에 대한 자세한 내용은 [Adobe 전달성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=ko).
