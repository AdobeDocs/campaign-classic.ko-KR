---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic으로 새 플랫폼 시작
description: Adobe Campaign Classic으로 새로운 플랫폼을 시작할 때 제공되는 기능 관리에 대한 자세한 내용을 살펴보십시오.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 1%

---


# 새 플랫폼 시작 {#starting-new-platform}

새 플랫폼을 설정할 때 도메인과 IP 주소 평판 유지 관리가 중요합니다.

* 플랫폼의 사용 내역이 없으므로 이메일 전송을 시작하는 것은 중요한 단계이며 전송 IP가 이러한 목적으로 사용되지 않은 경우, 명성은 없습니다.

* ISP는 이메일을 보내는 데 전혀 사용되지 않은 IP 주소를 의심하기 때문에 갑자기 대량의 이메일 트래픽을 전송하기 시작합니다. 실제로 스팸은 일반적으로 &quot;알 수 없는&quot; IP 주소(에 전혀 차단 목록 없는 주소)를 사용하여 감지하기 전에 가능한 가장 많은 수의 메시지를 전송합니다.

* 제작 단계가 시작될 때 출력 측면에서 운영 속도에 도달하는 것을 기대할 수 없습니다. 또한, ISP가 보내는 주소를 막고 나머지 시작 단계를 심각하게 훼손할 수 있으므로 이 속도로 메시지를 전송하지 않아야 합니다.

다음은 새 플랫폼을 시작할 때 따라야 할 기본 원칙을 설명한 것입니다.

* 이 정보가 있으면 **잘못된 주소를 격리 테이블**로 가져옵니다.
플랫폼을 시작하는 것은 처음 주소 목록을 사용할 때 자주 발생하여 완전히 자격이 없을 수 있습니다. 잘못된 주소 또는 허니포트 주소로 보내는 경우 플랫폼의 명성을 감소시킵니다.

   * 유효하지 않은 주소 목록이 있는 경우 처음 보내기 전에 검역 테이블로 가져오는 것이 좋습니다(**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 메뉴를 통해 사용 가능).
   * 동일한 경우 잘못된 주소를 요청하려는 경우, 플랫폼의 이름이 설정되고 시간이 지남에 따라 잘못된 주소의 사용을 &quot;희석하기&quot;하기 위해 비트별로 비트 전송되면 이 작업을 수행하는 것이 훨씬 좋습니다.

   이것에 대한 자세한 내용은 [검역조사를 통한 배달 최적화](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines)를 참조하십시오.
* **mtachilds 수를** 제한하여 처리량 속도를 제한합니다. 이러한 기술 설정을 조정하는 방법에 대한 자세한 내용은 Adobe Campaign 관리자에게 문의하십시오.
* **스팸으로 표시되지 않도록** 전송된 볼륨을 점진적으로 늘립니다. 처음부터 전체 데이터베이스를 대상으로 하지 않고 전송할 때마다 목록의 일부를 추가로 추가합니다. 따라서 유효하지 않은 주소의 전체 비율을 줄이면서 각 단계에서 볼륨을 증가시킬 수 있습니다. 시작 단계를 매끄럽게 개발하기 위해 물결을 사용할 수 있습니다. 자세한 내용은 [여러 파도를 사용하여 보내기](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)를 참조하십시오.
* **정기적으로** 전송 산발적으로 대형 캠페인보다는 정기적으로 작은 샷을 보내는 것이 더 좋습니다.
* **배달 보고서에 주의를 기울입니다**. 오류 표시기가 높으면 기술 설정이 잘못 구성되었음을 의미합니다. 자세한 내용은 [배달](../../delivery/using/about-delivery-monitoring.md) 모니터링을 참조하십시오.

**관련 항목**:
* [IP 온난화로 이메일 명성 향상](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [스팸 트랩 정보](https://helpx.adobe.com/campaign/kb/spam-traps.html)