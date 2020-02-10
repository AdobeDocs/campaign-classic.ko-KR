---
title: 성능 및 처리량 문제
seo-title: 성능 및 처리량 문제
description: 성능 및 처리량 문제
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 성능 및 처리량 문제{#performance-and-throughput-issues}

>[!NOTE]
>
>먼저 최신 빌드가 설치되어 있는지 확인해야 합니다. 따라서 최신 기능과 버그 수정이 가능합니다. 각 릴리스의 [컨텐츠에](https://docs.campaign.adobe.com/doc/AC/en/RN.html) 대한 자세한 내용은 릴리스 노트를 참조하십시오.

## 하드웨어 및 인프라 {#hardware-and-infrastructure}

온프레미스 Campaign Classic의 하드웨어 요구 사항에 대한 일반 지침은 이 [문서에](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)자세히 설명되어 있습니다.

컨설팅 팀은 호스팅된 고객에게 SFTP 사이트에서 사용되는 공간뿐만 아니라 데이터베이스의 다양한 유형의 테이블에서 사용되는 공간의 크기를 쉽게 볼 수 있는 도구를 제공할 수 있습니다. 또한 불필요한 데이터를 정리할 수 있는 도구를 제공합니다. 이 도구를 구현해야 하는 경우 컨설팅 또는 지원 팀에 문의하십시오. 다음은 이 도구를 사용하여 확인하는 몇 가지 중요한 사항입니다.

* 인덱스 크기가 표 크기보다 큰 경우 진공이 필요합니다.
* 최대값이 있는 표를 확인하십시오. 이 테이블들이 자주 사용된다면 진공청소기로 청소해야 한다.
* 데이터베이스 차단을 통해 이메일이 전송되지 않을 수 있습니다.

또한 Adobe Campaign은 CPU 및 RAM 사용을 확인하는 [도구를](../../production/using/monitoring-processes.md#manual-monitoring) 제공합니다. 이 도구를 사용하여 다음과 같은 특정 지표를 봅니다. **메모리**, **메모리**&#x200B;교체, **디스크**, 활성 **프로세스**&#x200B;중 하나. 값이 너무 높은 경우 워크플로우 수를 줄이거나 워크플로우를 예약하여 다른 시간에 시작할 수 있습니다.

## 데이터베이스 성능 {#database-performances}

대부분의 경우 성능 문제는 데이터베이스 유지 관리와 관련이 있습니다. 다음은 확인할 주요 항목입니다.

* 구성:초기 Adobe Campaign 플랫폼 구성을 확인하고 전체 하드웨어 검사를 실행하는 것이 좋습니다.
* Adobe Campaign 플랫폼의 설치 및 구성:네트워크 구성 및 플랫폼 제공 옵션을 확인하십시오.
* 데이터베이스 유지 관리:데이터베이스 정리 작업이 작동하고 데이터베이스 유지 관리가 올바르게 예약되어 실행되는지 확인하십시오. 작업 표의 수와 크기를 확인합니다.
* 실시간 진단:프로세스 및 플랫폼 로그 파일을 확인한 다음 문제를 다시 만드는 동안 데이터베이스 작업을 모니터링합니다.

>[!NOTE]
>
>자세한 내용은 다음 섹션을 참조하십시오.데이터베이스 [성능](../../production/using/database-performances.md).

## 애플리케이션 구성 {#application-configuration}

다음은 애플리케이션 구성 우수 사례와 관련된 아티클 목록입니다.

* MTA 및 MTAChild 프로세스 및 메모리:mta **모듈은** 해당 하위 모듈에 메시지를 **배포합니다** . 각 **필드는** 통계 서버에서 승인을 요청하고 보내기 전에 메시지를 준비합니다. 자세한 내용은 이 [페이지를](../../installation/using/email-deliverability.md) 참조하십시오.
* TLS 구성:처리량을 줄일 수 있으므로 TLS 전역 활성화는 권장되지 않습니다. 대신 제공 팀이 관리하는 도메인별 TLS 설정은 필요에 따라 조정되어야 합니다. 자세한 내용은 이 [페이지를](../../installation/using/email-deliverability.md#mx-configuration) 참조하십시오.
* DKIM:DKIM의 보안 수준을 보장하기 위해, 1024b는 Best Practices 권장 암호화 크기입니다. DKIM 키가 낮으면 대부분의 액세스 공급자가 유효한 것으로 간주하지 않습니다. 이 [페이지](../../delivery/using/technical-recommendations.md#domainkeys-identified-mail--dkim-) 및 이 [기술 문서를 참조하십시오](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## 전달 가능성 문제 {#deliverability-issues}

다음은 제공 능력과 관련된 모범 사례 및 아티클의 목록입니다.

* IP 인지도:IP 명성에 문제가 있는 경우 성능에 영향을 미칠 수 있습니다. Deliverability **Monitoring** 모듈은 플랫폼의 전달 성능을 추적하는 다양한 툴을 제공합니다. 이 [페이지를](../../delivery/using/technical-monitoring.md)참조하십시오.
* IP 준비:IP 온업은 제공 팀이 수행합니다. 이는 몇 주 동안 새로운 IP를 통해 이메일 수를 점진적으로 증가시키는 것을 포함합니다.
* IP 친화성 설정:잘못된 IP 친화성 설정은 이메일을 완전히 중지하거나(구성에서 잘못된 연산자/친화성 이름) 처리량을 줄일 수 있습니다(친화성의 IP 수가 적음). 이 [페이지를](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)참조하십시오.
* 이메일 크기:이메일 크기는 처리량에서 중요한 역할을 합니다. 권장 최대 이메일 크기는 60KB입니다. 이 [페이지를](https://helpx.adobe.com/legal/product-descriptions/campaign.html)참조하십시오. Delivery [throughput](../../reporting/using/reports-on-deliveries.md#delivery-throughput) 보고서에서 시간별로 전송된 바이트 수를 확인합니다.
* 유효하지 않은 받는 사람 수:잘못된 수신자가 많으면 처리량에 영향을 줄 수 있습니다. MTA가 잘못된 수신자에게 이메일 전송을 계속 시도합니다. 데이터베이스가 제대로 유지되는지 확인하십시오.
* 개인화의 양:배달이 &quot;개인화 진행 중&quot;에 있는 경우 개인화 블록에 사용된 JavaScript를 확인하십시오.

>[!NOTE]
>
>전달 [시작](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 가이드를 참조하십시오.

