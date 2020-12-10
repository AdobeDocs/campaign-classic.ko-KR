---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic에서 새로운 플랫폼 시작
description: Adobe Campaign Classic에서 새로운 플랫폼을 시작할 때 전달 능력 관리에 대한 자세한 내용을 살펴보십시오.
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

새 플랫폼을 설정할 때는 도메인 및 IP 주소 명성을 유지해야 합니다.

* 플랫폼의 사용 내역이 없으므로 이메일 전송을 시작하는 것은 중요한 단계이며 전송 IP가 이러한 목적으로 사용되지 않은 경우, 명성도 없습니다.

* ISP는 원래 이메일을 보내는 데 전혀 사용되지 않은 IP 주소를 의심하기 때문에 갑자기 많은 양의 이메일 트래픽이 전송되기 시작합니다. 실제로 스팸은 일반적으로 &quot;알 수 없는&quot; IP 주소(에 있었던 적이 없는 주소)를 사용하여 감지하기 전에 가장 많은 메시지 수를 전송합니다차단 목록.

* 제작 단계에서 출력 측면에서 운영 속도에 도달하는 것은 기대할 수 없습니다. 또한, ISP가 전송 주소를 막고 나머지 시작 단계를 심각하게 훼손할 수 있으므로 이러한 속도로 메시지를 전송하지 마십시오.

다음은 새 플랫폼을 시작할 때 따라야 할 주요 원칙입니다.

* 이 정보가 있는 경우 **잘못된 주소를 격리 테이블**로 가져옵니다.
플랫폼 시작은 처음 주소 목록을 사용할 때 일어나며, 이것은 완전히 검증되지 않을 수 있습니다. 잘못된 주소나 허니포트 주소로 보내면 플랫폼의 이름이 낮아지는 데 도움이 됩니다.

   * 잘못된 주소 목록이 있는 경우 처음 보내기 전에 검역 테이블로 가져오는 것이 좋습니다(**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 메뉴를 통해 사용 가능).
   * 동일한 경우 잘못된 주소를 요청하려는 경우, 플랫폼의 이름이 설정되고 시간이 지남에 따라 잘못된 주소의 사용을 &quot;희석시키기&quot;위해 비트별로 비트 단위로 설정되면 이 방법을 사용하는 것이 더 좋습니다.

   이에 대한 자세한 내용은 [검역물을 통해 배달 최적화](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines)를 참조하십시오.
* **Limit the throughput** rateby limited the number of matchilds. 이러한 기술 설정을 조정하는 방법에 대한 자세한 내용은 Adobe Campaign 관리자에게 문의하십시오.
* **스팸으로 표시되지 않도록 전송된 볼륨** 을 점진적으로 늘립니다. 처음부터 전체 데이터베이스를 대상으로 하지 않고 전송할 때마다 목록의 일부분을 추가합니다. 따라서 각 단계에서 볼륨을 증가시키고 잘못된 주소의 전체 속도를 줄일 수 있습니다. 시작 단계의 원활한 개발을 위해 파도를 사용할 수 있습니다. 이에 대한 자세한 내용은 [여러 파동을 사용하여 보내기](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)를 참조하십시오.
* **정기적으로** 전송 산발적으로 대형 캠페인보다는 작은 샷을 정기적으로 보내는 것이 좋다.
* **배달 보고서에 주의를 기울입니다**. 오류 표시기가 높으면 기술 설정이 잘못 구성되었을 수 있습니다. 자세한 내용은 [배달 모니터링](../../delivery/using/about-delivery-monitoring.md)을 참조하십시오.

**관련 항목**:
* [IP로 이메일 인지도 향상](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [스팸 트랩에 대한 모든 정보](https://helpx.adobe.com/campaign/kb/spam-traps.html)