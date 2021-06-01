---
product: campaign
title: 성능 및 처리량 문제
description: 성능 및 처리량 문제
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 4%

---

# 성능 및 처리량 문제{#performance-and-throughput-issues}

먼저 최신 빌드가 설치되어 있는지 확인해야 합니다. 이렇게 하면 최신 기능과 버그 수정 사항이 제공됩니다.

각 릴리스의 콘텐츠에 대한 자세한 내용은 [릴리스 노트](../../rn/using/latest-release.md)를 참조하십시오.

## 하드웨어 및 인프라 {#hardware-and-infrastructure}

온-프레미스 Campaign Classic에 대한 하드웨어 요구 사항에 대한 일반 지침은 이 [페이지](https://helpx.adobe.com/kr/campaign/kb/hardware-sizing-guide.html)에 자세히 설명되어 있습니다.

컨설팅 팀은 호스팅된 고객에게 데이터베이스의 다양한 유형의 테이블에서 사용되는 공간 및 SFTP 사이트에서 사용되는 공간을 쉽게 볼 수 있는 도구를 제공할 수 있습니다. 또한 불필요한 데이터를 정리할 수 있는 도구를 제공합니다. 이 도구를 구현해야 하는 경우 [고객 지원 센터 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오. 다음은 이 도구를 사용하여 확인할 몇 가지 중요한 작업입니다.

* 인덱스 크기가 표 크기보다 큰 경우 진공이 필요합니다.
* 최대 볼트가 있는 테이블을 확인합니다. 이런 테이블들을 자주 사용한다면 진공을 해야 한다.
* 데이터베이스 차단으로 인해 전자 메일이 전송되지 않을 수 있습니다.

Adobe Campaign은 CPU 및 RAM 사용을 확인하는 [도구](../../production/using/monitoring-processes.md#manual-monitoring)도 제공합니다. 이 도구를 사용하여 다음과 같은 특정 지표를 확인합니다.**메모리**, **메모리 교체**, **디스크**, **활성 프로세스**. 값이 너무 높으면 워크플로우 수를 줄이거나 워크플로우를 다른 시간에 시작하도록 예약할 수 있습니다.

## 데이터베이스 확인 {#database-performances}

대부분의 경우 성능 문제는 데이터베이스 유지 관리와 관련되어 있습니다. 확인할 주요 항목은 다음과 같습니다.

* 구성:초기 Adobe Campaign 플랫폼 구성을 확인하고 전체 하드웨어 검사를 실행하는 것이 좋습니다.
* Adobe Campaign 플랫폼의 설치 및 구성:네트워크 구성 및 플랫폼 게재 기능 옵션을 확인합니다.
* 데이터베이스 유지 관리:데이터베이스 정리 작업이 작동 중이고 데이터베이스 유지 관리가 올바르게 예약되어 실행되었는지 확인합니다. 작업 테이블의 수와 크기를 확인합니다.
* 실시간 진단:프로세스 및 플랫폼 로그 파일을 확인한 다음 문제를 다시 만드는 동안 데이터베이스 활동을 모니터링합니다.

>[!NOTE]
>
>자세한 정보는 다음 섹션을 참조하십시오.[데이터베이스 성능](../../production/using/database-performances.md)

## 응용 프로그램 구성 {#application-configuration}

다음은 애플리케이션 구성 모범 사례와 관련된 문서 목록입니다.

* MTA 및 MTAChild 프로세스 및 메모리:**mta** 모듈은 **mtachild** 하위 모듈에 메시지를 배포합니다. 각 **mtachild**&#x200B;은(는) 통계 서버에서 인증을 요청하여 보내기 전에 메시지를 준비합니다. 자세한 내용은 이 [page](../../installation/using/email-deliverability.md)을 참조하십시오.
* TLS 구성:tls를 전역적으로 활성화하는 것은 처리량을 줄일 수 있으므로 권장되지 않습니다. 대신, 게재 가능성 팀에서 관리하는 도메인별 TLS 설정은 필요에 따라 조정되어야 합니다. 자세한 내용은 이 [page](../../installation/using/email-deliverability.md#mx-configuration)을 참조하십시오.
* DKIM:DKIM의 보안 수준을 보장하기 위해 1024b가 권장되는 암호화 크기입니다. 낮은 DKIM 키는 대부분의 액세스 공급자가 유효하다고 간주하지 않습니다. [이 페이지](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)를 참조하십시오.

## 게재 가능성 문제 {#deliverability-issues}

다음은 게재 능력과 관련된 우수 사례 및 문서 목록입니다.

* IP 평판:IP 평판이 좋지 않으면 성능에 영향을 줄 것입니다. **게재 기능 모니터링** 모듈은 플랫폼의 게재 기능 성능을 추적하는 다양한 도구를 제공합니다. 이 [page](../../delivery/using/monitoring-deliverability.md)을 참조하십시오.
* IP 준비:ip 준비 작업은 게재 가능성 팀이 수행합니다. 이에 따라 몇 주 동안 새로운 IP를 통해 이메일 수를 점진적으로 늘리는 작업이 포함됩니다.
* IP 선호도 설정:잘못된 IP 선호도 설정으로 인해 이메일이 완전히 중지되거나(구성의 잘못된 연산자/선호도 이름) 처리량을 줄일 수 있습니다(친화성에 있는 IP 수가 적음). 이 [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)을 참조하십시오.
* 전자 메일 크기:이메일 크기는 처리량에서 중요한 역할을 합니다. 권장되는 최대 이메일 크기는 60KB입니다. 이 [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html)을 참조하십시오. [배달 처리량](../../reporting/using/global-reports.md#delivery-throughput) 보고서에서 시간별로 전송된 바이트 수를 확인합니다.
* 잘못된 받는 사람 수:잘못된 수신자가 많으면 처리량에 영향을 줄 수 있습니다. MTA는 잘못된 수신자에게 전자 메일 전송을 계속 재시도합니다. 데이터베이스가 잘 유지되는지 확인하십시오.
* 개인화 양:게재가 &quot;개인화 진행 중&quot;에 있는 경우 개인화 블록에 사용된 JavaScript를 확인하십시오.

>[!NOTE]
>
>[게재 가능성](../../delivery/using/about-deliverability.md) 섹션도 참조하십시오. 게재 능력에 대한 자세한 내용은 [Adobe 게재 가능성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=ko)를 참조하십시오.
