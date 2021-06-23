---
product: campaign
title: 메시지 추적 및 모니터링
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 3%

---

# 추적 및 모니터링 {#track-and-monitor}

**보내기** 단추를 클릭했습니까? 어떻게 되는지 봅시다. 게재를 전송하면 Adobe Campaign을 통해 전송된 메시지를 추적하고 수신자가 게재에 어떻게 반응하는지를 알 수 있습니다. 이를 통해 향후 전송을 개선하고 다음 캠페인을 최적화할 수 있습니다.

## 게재 모니터링 {#monitoring-deliveries}

캠페인을 제어하려면 메시지가 수신자에게 실제로 전달되었는지 확인해야 합니다.

Campaign 게재 대시보드에서 처리된 메시지 및 게재 감사 로그를 확인할 수 있습니다.
게재 로그에서 메시지 상태를 제어할 수도 있습니다. [자세히 알아보기](about-delivery-monitoring.md)

게재가 전송되지 않고 상태가 **보류 중**&#x200B;으로 남아 있으면 어떻게 합니까?

* 일부 리소스가 사용 가능한 상태를 기다리는 중입니다. MTA가 시작되지 않았을 수 있습니다.
mta@instance 모듈이 MTA 서버에서 시작되었는지 확인하고 필요한 경우 MTA 모듈을 시작합니다. [자세히 알아보기](../../production/using/administration.md)

* 게재는 전송 인스턴스에서 구성되지 않은 친화성을 사용할 수 있습니다.
팁:트래픽 관리(IP 친화성) 구성을 확인합니다. 자세한 내용은 나가는 SMTP 트래픽 제어를 참조하십시오.

>[!NOTE]
>
>이러한 단계는 전문가 사용자만 수행할 수 있습니다.

## 추적 {#tracking-deliveries}

수신자의 행동을 더 잘 알기 위해 수신자가 게재에 어떻게 반응하는지를 추적할 수 있습니다.수신, 열기, 링크 클릭 수, 구독 취소 등 Campaign Classic에서 이 정보는 게재의 타겟팅된 수신자의 추적 탭 및 게재의 추적 탭에 표시됩니다.

**팁**:메시지 추적은 기본적으로 활성화되어 있습니다. URL을 구성하려면 게재 마법사의 아래 섹션에서 URL 표시 옵션을 선택합니다. 메시지의 각 URL에 대해 추적을 활성화할지 여부를 선택할 수 있습니다.

자세한 내용은 [추적 구성](how-to-configure-tracked-links.md) 섹션과 [추적 표시기](../../reporting/using/delivery-reports.md#tracking-indicators) 설명을 참조하십시오.

## 게재 성능 {#delivery-performances}

메시지가 전달되는 속도를 측정하기 위해 게재 처리량을 제어할 수 있습니다. 기준은 시간당 전송된 메시지 수와 메시지 크기(초당 비트 수)입니다. 자세한 내용은 [게재 처리량](../../reporting/using/global-reports.md#delivery-throughput)을 참조하십시오.

**팁**:

* 임시 테이블을 유지 관리하고 성능에 영향을 주므로 인스턴스에서 게재를 실패 상태로 유지하지 마십시오.

* 주소 품질을 유지하기 위해 더 이상 필요하지 않은 게재 및 비활성 수신자를 데이터베이스에서 제거합니다.

* 대규모 게재를 함께 예약하지 마십시오. 부하를 시스템에 균일하게 분산하는 데 5~10분이 걸릴 수 있습니다.

## 게재 문제 해결 {#delivery-troubleshooting}

게재와 관련된 문제가 발생할 경우 특정 작업을 수행할 수 있습니다.

* [게재 가능성 문제](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [이미지 표시 문제](../../production/using/image-display-issues.md)

* [게재 성능 문제](delivery-performances.md)

* [임시 파일 문제](../../production/using/temporary-files.md)  -  *온-프레미스 고객만*
