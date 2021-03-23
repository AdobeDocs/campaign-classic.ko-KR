---
solution: Campaign Classic
product: campaign
title: 게재 성능 모범 사례
description: 전달 성능 및 모범 사례에 대한 자세한 내용을 살펴보십시오.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 5%

---


# 게재 성능 모범 사례 {#delivery-performances}

배달이 제대로 수행되도록 하려면 아래 지침을 따를 것을 권장합니다. 또한 납품 문제가 발생하면 확인 작업을 수행하는 것이 좋습니다.

**관련 항목:**

* [게재 대시보드](../../delivery/using/delivery-dashboard.md)
* [게재 문제 해결](../../delivery/using/delivery-troubleshooting.md)
* [게재 기능 기본 정보](../../delivery/using/about-deliverability.md)

## 성능 모범 사례 {#best-practices-performance}

* 임시 테이블을 유지 관리하고 성능에 영향을 주므로 인스턴스에 대해 배달이 실패한 상태로 유지되지 마십시오.

* 더 이상 필요하지 않은 제공을 제거합니다.

* 주소 품질을 유지하기 위해 데이터베이스에서 제거할 최근 12개월 동안 비활성 받는 사람.

* 큰 배달은 함께 예약하지 마십시오. 이 부하를 시스템에 균일하게 분산시키는 데 5-10분의 차이가 있다. 최상의 성능을 보장하도록 팀의 다른 구성원과 배달 예약을 조정합니다. 마케팅 서버가 동시에 여러 가지 작업을 처리할 때 성능이 저하될 수 있습니다.

* 이메일 크기를 최대한 낮게 유지하십시오. 권장되는 최대 이메일 크기는 약 35KB입니다. 이메일 배달의 크기는 전송 서버에서 특정 양의 볼륨을 생성합니다.

* 100만 명 이상의 수신자에게 배달과 같은 큰 배달은 전송 대기열에 공간이 필요합니다. 이러한 문제는 서버 자체만으로는 문제가 되지 않지만, 수십 개의 다른 큰 배달과 함께 동시에 모든 것이 전달될 때 전송 지연을 유발할 수 있습니다.

* 이메일의 개인화는 각 수신자에 대한 데이터를 데이터베이스에서 가져옵니다. 개인화 요소가 많이 있는 경우 전달을 준비하는 데 필요한 데이터의 양이 증가합니다.

* 색인 주소. 응용 프로그램에 사용된 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 기본 요소에서 인덱스를 선언할 수 있습니다.

>[!NOTE]
>
>ISP는 비활성 기간 후 주소를 비활성화합니다. 바운스된 메시지는 이 새로운 상태에 대해 알려 주기 위해 전송자에게 전송됩니다.

## 성능 문제 검사 목록 {#performance-issues}

배달 실적이 나쁜 경우 다음을 확인할 수 있습니다.

* **배달의 크기**:큰 배달은 완료하는 데 시간이 오래 걸릴 수 있습니다. MTA 하위는 대부분의 인스턴스에서 작동하는 기본 배치 크기를 처리하도록 구성되지만 배달이 지속적으로 느려질 때 확인해야 합니다.
* **배달** 대상:배달 성능 제한은 다시 시도 구성에 따라 처리되는 소프트 바운스 오류에 영향을 받습니다. 오류 수가 많을수록 더 많은 재시도가 필요합니다.
* **전체 플랫폼 로드**:여러 개의 큰 배달이 전송되면 전체 플랫폼에 영향을 줄 수 있습니다. 또한 IP 명성과 전달 가능성 문제를 확인할 수 있습니다. 자세한 내용은 [이 섹션](../../delivery/using/about-deliverability.md)과 [Adobe 제공 우수 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)를 참조하십시오.

플랫폼 및 데이터베이스 유지 관리도 전달 전송 성능에 영향을 줄 수 있습니다. 자세한 정보는 이 [페이지](../../production/using/database-performances.md)를 참조하십시오.
