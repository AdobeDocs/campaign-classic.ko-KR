---
product: campaign
title: 추적 로그 문제
description: 추적 로그 문제
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 13%

---

# 추적 로그 문제{#tracking-logs-issues}



추적 로그가 전달되지 않는 이유는 여러 가지가 있을 수 있습니다. 다음 정보를 확인하는 것이 좋습니다.

* **다음을 수행합니다.**&#x200B;추적&#x200B;**워크플로우에 오류가 있습니까?**

  을(를) 참조하십시오 [기술 워크플로우 모니터링](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **모듈임** trackinglogd **서버에서 실행 중입니까?**

  을(를) 참조하십시오 [로그 파일](../../production/using/log-files.md).

* **변경 사항이 적용되었습니까?**

  추적 별칭을 사용하여 서버 연결 손실을 트리거할 수 있습니다.
