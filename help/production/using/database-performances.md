---
solution: Campaign Classic
product: campaign
title: 데이터베이스 성능
description: 데이터베이스 성능
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---


# 데이터베이스 성능{#database-performances}

대부분의 성능 문제는 데이터베이스 유지 관리와 관련이 있습니다. 다음은 성능 저하의 원인을 찾는 데 도움이 되는 4가지 주요 리드입니다.

* 구성
* Adobe Campaign 플랫폼 설치 및 구성
* 데이터베이스 유지 관리
* 실시간 진단

## 구성 {#configuration}

초기 Adobe Campaign 플랫폼 구성이 여전히 유효한지 확인하고 필요한 경우 제공 가능 여부 또는 데이터베이스 크기 측면에서 고객의 요구 사항을 재평가하십시오. 또한 전체 하드웨어 검사(CPU, RAM, IO 시스템)를 실행하는 것이 좋습니다.

>[!NOTE]
>
>인사이트를 보려면 [Adobe Campaign 하드웨어 크기 조정 안내서](https://helpx.adobe.com/kr/campaign/kb/hardware-sizing-guide.html)를 참조하십시오.

## 플랫폼 구성 {#platform-configuration}

부적절한 구성은 플랫폼 성능에 영향을 줄 수 있습니다. **serverConf.xml** 파일에서 네트워크 구성, 플랫폼 제공 옵션 및 MTA 구성을 확인하는 것이 좋습니다.

## 데이터베이스 유지 관리 {#database-maintenance}

**데이터베이스 정리 작업**

데이터베이스 정리 작업이 작동하는지 확인하십시오. 이렇게 하려면 로그 파일에 오류가 있는지 확인합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../production/using/database-cleanup-workflow.md)을 참조하십시오.

**유지 관리 계획**

데이터베이스 유지 관리가 올바르게 예약되어 실행되는지 확인하십시오. 이렇게 하려면 데이터베이스 관리자에게 문의하여 다음 사항에 대해 자세히 알아보십시오.

* 유지 관리 일정
* 이전에 실행된 유지 관리 계획
* 스크립트 로그 보기

이 작업에 대한 자세한 정보는 [이 섹션](../../production/using/recommendations.md)을 참조하십시오.

>[!IMPORTANT]
>
>중간 소싱 구성을 사용하는 경우 정기적으로 데이터베이스를 유지 관리하는 것이 중요합니다. 마케팅 플랫폼에서 전달을 분석할 때 마케팅 인스턴스는 mid-sourcing 인스턴스로 정보를 전송합니다. 프로세스가 느려지면 마케팅 인스턴스에 영향을 줍니다.

**작업 테이블 관리**

작업표의 번호와 크기를 확인하십시오. 특정 크기를 초과하면 데이터베이스 성능에 영향을 줍니다. 이러한 테이블은 워크플로우 및 배달로 만들어집니다. 워크플로우와 배달이 활성화된 상태에서 데이터베이스에 남아 있습니다. 작업 테이블 크기를 제한하려면 다음 작업을 수행할 수 있습니다.

* 다음 상태의 납품을 중지하거나 삭제합니다.**[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]** 또는 **[!UICONTROL Paused]**.
* 오류로 인해 일시 중지된 워크플로우를 중지하거나 삭제합니다.
* **[!UICONTROL End]** 활동을 포함하지 않고 그 상태가 **[!UICONTROL Paused]**&#x200B;로 남아 있는 테스트에 사용된 모든 워크플로우를 중지합니다.

>[!IMPORTANT]
>
>작업에 시간이 오래 걸리고 많은 공간을 절약할 경우, 즉 색인 재작성 등 심층적인 유지 관리가 필요합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../production/using/recommendations.md)을 참조하십시오.

**Adobe Campaign 프로세스 모니터링**

Adobe Campaign 설치 설정에 따라 플랫폼 모니터링에 두 가지 도구를 사용할 수 있습니다.

* 인스턴스 프로덕션 페이지입니다. 자세한 내용은 [수동 모니터링](../../production/using/monitoring-processes.md#manual-monitoring)을 참조하십시오.
* *netreport* 스크립트. 자세한 내용은 Adobe Campaign 스크립트](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)를 통한 자동 모니터링을 참조하십시오.[

## 자세한 내용 {#specifics}

문제의 원인을 파악하기 위해 실시간 진단을 실행해야 할 수도 있습니다. 먼저 프로세스 및 플랫폼 로그 파일을 확인한 다음 문제를 다시 만드는 동안 데이터베이스 작업을 모니터링합니다. 다음 사항에 특히 주의하십시오.

* 유지 관리 실행 계획
* 실행 중인 SQL 쿼리
* 외부 프로세스가 동시에 실행되는지 여부(정리, 가져오기, 집계 계산 등)
