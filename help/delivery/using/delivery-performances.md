---
solution: Campaign Classic
product: campaign
title: 전달 성능 우수 사례
description: 전달 성능 및 모범 사례에 대한 자세한 내용을 살펴보십시오.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 5b43412286762977c416665d296908a9bfc9b20a
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 2%

---


# 배달 성능 우수 사례 {#delivery-performances}

아래 지침에 따라 배송이 제대로 수행되도록 하고 배달 문제가 발생하면 수행 여부를 확인하는 것이 좋습니다.

**관련 항목:**

* [배달 대시보드](../../delivery/using/delivery-dashboard.md)
* [배달 문제 해결](../../delivery/using/delivery-troubleshooting.md)
* [게재 기능 기본 정보](../../delivery/using/about-deliverability.md)

## 성능 모범 사례 {#best-practices-performance}

* 임시 테이블을 유지하고 성능에 영향을 주므로 인스턴스에 배달을 실패한 상태로 유지하지 마십시오.

* 더 이상 필요하지 않은 배달을 제거합니다.

* 주소 품질을 유지하기 위해 최근 12개월 동안 비활성 수신자를 데이터베이스에서 제거해야 합니다.

* 큰 배달은 함께 예약하지 마십시오. 이 부하를 시스템에 균일하게 분산시키는 데에는 5-10분의 차이가 있다. 우수 성과를 확보하기 위해 팀의 다른 구성원과 배달 예약을 조정합니다. 마케팅 서버가 동시에 여러 가지 작업을 처리할 때 성능이 저하될 수 있습니다.

* 이메일 크기를 최대한 낮게 유지하십시오. 권장되는 최대 이메일 크기는 약 35KB입니다. 이메일 배달의 크기는 전송 서버에서 특정 양을 생성합니다.

* 100만 명 이상의 수신자에게 배달하는 것과 같은 큰 배달은 전송 대기열에 공간이 필요합니다. 이 자체만으로는 서버에 문제가 되지 않지만 수십 개의 다른 큰 배달과 함께 동시에 발송되는 경우 전송 지연을 유발할 수 있습니다.

* 이메일의 개인화는 각 수신자에 대한 데이터를 데이터베이스에서 가져옵니다. 개인화 요소가 많은 경우 전달을 준비하는 데 필요한 데이터의 양이 증가합니다.

* 색인 주소. 응용 프로그램에 사용되는 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 기본 요소에서 인덱스를 선언할 수 있습니다.

>[!NOTE]
>
>ISP는 비활성 기간 후 주소를 비활성화합니다. 바운스된 메시지는 이 새로운 상태에 대해 알려주기 위해 발신자에게 전송됩니다.

## 성능 문제 검사 목록 {#performance-issues}

배달 실적이 나쁜 경우 다음을 확인할 수 있습니다.

* **배달** 크기:큰 배달은 완료하는 데 더 오래 걸릴 수 있습니다. MTA 하위는 대부분의 인스턴스에서 작동하는 기본 배치 크기를 처리하도록 구성되지만 배달이 지속적으로 느려질 때 확인해야 합니다.
* **배달** 대상:배달 성능 제한은 다시 시도 구성에 따라 처리되는 소프트 바운스 오류로 인해 영향을 받습니다. 오류 수가 많을수록 더 많은 재시도가 필요합니다.
* **전체 플랫폼 로드**:여러 개의 큰 배달이 전송되면 전체 플랫폼에 영향을 줄 수 있습니다. 또한 IP 명성과 전달 가능성 문제를 확인할 수 있습니다. 자세한 내용은 Adobe Campaign [배달 가능성 모범 사례 가이드](../../delivery/using/deliverability-key-points.md)와 [이 페이지](../../delivery/using/about-deliverability.md)를 참조하십시오.

플랫폼 및 데이터베이스 유지 관리도 배달 전송 성능에 영향을 줄 수 있습니다. 자세한 정보는 이 [페이지](../../production/using/database-performances.md)를 참조하십시오.
