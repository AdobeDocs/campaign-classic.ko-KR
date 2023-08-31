---
product: campaign
title: 게재 성능 모범 사례
description: 게재 성능 및 모범 사례에 대해 자세히 알아보기
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Deliverability
role: User, Data Engineer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 6%

---

# 게재 성능 모범 사례 {#delivery-performances}

게재 문제가 발생할 경우 게재가 제대로 수행되고 수행되는지 확인하려면 아래 지침을 따르는 것이 좋습니다.

**관련 항목:**

* [게재 대시보드](delivery-dashboard.md)
* [게재 문제 해결](delivery-troubleshooting.md)
* [게재 기능 기본 정보](about-deliverability.md)

## 성능 모범 사례 {#best-practices-performance}

* 임시 테이블을 유지하고 성능에 영향을 주므로 인스턴스에서 게재를 실패 상태로 유지하지 마십시오.

* 더 이상 필요하지 않은 게재를 제거합니다.

* 지난 12개월 동안 주소 품질을 유지하기 위해 데이터베이스에서 제거할 비활성 수신자입니다.

* 큰 게재를 함께 예약하지 마십시오. 시스템 전체에 균등하게 부하를 분산시키기 위해서는 5-10분의 간격이 있다. 최상의 성능을 보장하려면 팀의 다른 멤버와 게재 일정을 조정하십시오. 마케팅 서버가 동시에 많은 다른 작업을 처리할 때 성능이 저하될 수 있습니다.

* 이메일 크기를 최대한 작게 유지하십시오. 이메일의 권장 최대 크기는 약 35KB입니다. 이메일 게재 크기는 전송 서버에서 특정 양의 볼륨을 생성합니다.

* 백만 명이 넘는 수신자에게 게재하는 것과 같은 대용량 게재는 전송 큐에 공간이 필요합니다. 이 방법만으로 서버에 문제가 되지는 않지만 수십 개의 다른 대형 게재가 동시에 나가는 경우 전송 지연이 발생할 수 있습니다.

* 이메일의 개인화는 각 수신자에 대해 데이터베이스에서 데이터를 가져옵니다. 개인화 요소가 많으면 게재를 준비하는 데 필요한 데이터의 양이 증가합니다.

* 색인 주소. 응용 프로그램에서 사용되는 SQL 쿼리의 성능을 최적화하기 위해 데이터 스키마의 주 요소에서 인덱스를 선언할 수 있습니다.

>[!NOTE]
>
>ISP는 일정 기간 동안 활동이 없으면 주소를 비활성화합니다. 반송된 메시지는 보낸 사람에게 이 새로운 상태에 대해 알리기 위해 전송됩니다.

## 성능 문제 검사 목록 {#performance-issues}

게재 성능이 나쁜 경우 다음을 확인할 수 있습니다.

* **게재 크기**: 큰 게재를 완료하는 데 시간이 더 걸릴 수 있습니다. MTA 하위 항목은 대부분의 인스턴스에 작동하는 기본 배치 크기를 처리하도록 구성되지만 게재가 지속적으로 느려질 때 확인해야 합니다.
* **게재 대상**: 게재 성능은 소프트 바운스 오류의 영향을 받지 않으며, 이는 다시 시도 구성에 따라 처리됩니다. 오류 수가 많을수록 더 많은 재시도가 필요합니다.
* **전체 플랫폼 로드**: 여러 개의 큰 게재가 전송되는 경우 전체 플랫폼이 영향을 받을 수 있습니다. IP 신뢰도 및 전달성 문제도 확인할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [이 섹션](about-deliverability.md) 및 대상 [Adobe 전달성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=ko).

플랫폼 및 데이터베이스 유지 관리는 게재 전송 성능에도 영향을 줄 수 있습니다. 자세한 정보는 이 [페이지](../../production/using/database-performances.md)를 참조하십시오.
