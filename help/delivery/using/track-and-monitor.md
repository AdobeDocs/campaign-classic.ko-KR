---
product: campaign
title: 메시지 추적 및 모니터링
description: 메시지 추적 및 모니터링 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Monitoring, Reporting
role: User
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---

# 추적 및 모니터링 {#track-and-monitor}

을(를) 클릭함 **보내기** 단추? 무슨 일이 일어나는지 봅시다. 게재가 전송되면 Adobe Campaign을 통해 전송된 메시지를 추적하고 수신자가 게재에 어떻게 반응하는지 확인할 수 있습니다. 이를 통해 향후 전송을 개선하고 다음 캠페인을 최적화할 수 있습니다.

## 게재 모니터링 {#monitoring-deliveries}

캠페인을 제어하려면 메시지가 실제로 수신자에게 전달되었는지 확인해야 합니다.

Campaign 게재 대시보드에서 처리된 메시지 및 게재 감사 로그를 확인할 수 있습니다.
게재 로그에서 메시지 상태를 제어할 수도 있습니다. [자세히 알아보기](about-delivery-monitoring.md)

게재가 전송되지 않고 상태가 지속되는 경우 어떻게 합니까? **보류 중**?

* 실행 프로세스에서 일부 리소스를 사용할 수 있을 때까지 기다리고 있습니다. MTA가 시작되지 않았을 수 있습니다.
mta@instance 모듈이 MTA 서버에서 시작되었는지 확인하고 필요한 경우 MTA 모듈을 시작합니다. [자세히 알아보기](../../production/using/administration.md)

* 게재는 전송 인스턴스에 구성되지 않은 선호도를 사용하고 있을 수 있습니다.
팁: 트래픽 관리(IP 선호도) 구성을 확인하십시오. 자세한 내용은 발신 SMTP 트래픽 제어 를 참조하십시오.

>[!NOTE]
>
>이러한 단계는 전문가 사용자만 수행할 수 있습니다.

## 동작 추적 {#track-behaviour}

수신자의 동작을 더 잘 알기 위해 수신, 열기, 링크 클릭, 구독 취소 등 수신자가 게재에 어떻게 반응하는지를 추적할 수 있습니다. Campaign Classic에서 이 정보는 게재의 타겟팅한 수신자의 추적 탭과 게재의 추적 탭에 표시됩니다.

**팁**: 메시지 추적은 기본적으로 활성화되어 있습니다. URL을 구성하려면 게재 마법사의 아래 섹션에서 URL 표시 옵션을 선택합니다. 메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택할 수 있습니다.

자세한 내용은 [추적 구성](how-to-configure-tracked-links.md) 섹션 및 [지표 추적](../../reporting/using/delivery-reports.md#tracking-indicators) 설명.

## 게재 성능 {#delivery-performances}

메시지가 전달되는 속도를 측정하기 위해 게재 처리량을 제어할 수 있습니다. 기준은 시간당 전송된 메시지 수와 메시지 크기(초당 비트 수)입니다. 자세한 내용은 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput).

**팁**:

* 임시 테이블을 유지하고 성능에 영향을 주므로 인스턴스에서 게재를 실패 상태로 유지하지 마십시오.

* 더 이상 필요하지 않으며 비활성 수신자가 있는 게재를 데이터베이스에서 제거하여 주소 품질을 유지합니다.

* 큰 게재를 함께 예약하지 마십시오. 시스템에 균일하게 부하를 분산하는 데 5~10분이 소요될 수 있습니다.

## 게재 문제 해결 {#delivery-troubleshooting}

게재와 관련된 문제가 발생할 때 특정 작업을 수행할 수 있습니다.

* [전달성 문제](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [이미지 표시 문제](../../production/using/image-display-issues.md)

* [게재 성능 문제](delivery-performances.md)

* [임시 파일 문제](../../production/using/temporary-files.md) - *온-프레미스 고객만*
