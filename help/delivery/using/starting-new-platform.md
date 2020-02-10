---
title: Adobe Campaign Classic을 사용하여 새 플랫폼 시작
description: Adobe Campaign Classic을 사용하여 새 플랫폼을 시작할 때 전달 가능성 관리에 대한 자세한 내용을 살펴보십시오.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# 새 플랫폼 시작 {#starting-new-platform}

도메인과 IP 주소 평판 유지 관리가 중요합니다. 새 플랫폼 설정에 대한 몇 가지 조언이 아래에 나와 있습니다.

새 플랫폼에서 이메일을 보내는 것은 플랫폼이 사용 내역이 없고 명성도 없기 때문에(전송 IP가 이 용도로 사용되지 않은 경우) 민감한 단계입니다. ISP는 일반적으로 이메일을 보내는 데 전혀 사용되지 않은 IP 주소를 의심하며 갑자기 대량의 이메일 트래픽을 전송합니다. 실제로 스팸은 검색하기 전에 가장 많은 수의 메시지를 보내기 위해 일반적으로 &quot;알 수 없는&quot; IP 주소(블랙리스트에 오르지 않은 주소라고 함)를 사용합니다.

제작 단계에서 출력 측면에서 운영 속도를 기대할 수 없습니다. 또한 ISP가 전송 주소를 차단하고 나머지 시작 단계를 심각하게 훼손할 수 있으므로 이 속도로 메시지를 전송하지 마십시오.

플랫폼 시작은 처음 주소 목록을 사용할 때 종종 발생하며, 이것은 완전히 검증되지 않을 수 있습니다. 잘못된 주소 또는 허니포트 주소로 전송하는 경우 플랫폼의 명성을 감소시킵니다. 잘못된 주소 목록이 있는 경우 처음으로 보내기 전에 격리 테이블(**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**)로 가져오는 것이 좋습니다. 동일한 경우 잘못된 주소를 요청하려는 경우, 플랫폼의 이름이 설정되고 시간이 지남에 따라 잘못된 주소의 사용을 &quot;희석시키기&quot;위해 비트별로 설정되면 이 작업을 수행하는 것이 훨씬 좋습니다.

시작할 때 따라야 할 원칙을 요약하려면

* 잘못된 주소를 격리 테이블로 가져오기(이 정보가 있는 경우)
* 처리량 속도 제한(기술 설정:일치 수 제한)
* 전송된 볼륨을 점진적으로 증가시킵니다.처음부터 전체 데이터베이스를 타깃팅하지 말고 전송할 때마다 목록의 일부를 추가합니다.따라서 각 단계에서 볼륨을 늘리고 잘못된 주소의 전체 속도를 줄일 수 있습니다
* 정기적으로 전송:산발적으로 대규모 캠페인보다 작은 샷을 정기적으로 보내는 것이 좋습니다
* 배달 보고서에 대한 주의 사항:오류 표시기가 높으면 기술 설정이 잘못 구성되었을 수 있습니다.