---
product: campaign
title: 추적 로그 문제
description: 추적 로그 문제
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 24%

---

# 추적 로그 문제{#tracking-logs-issues}



추적 로그가 전달되지 않는 이유는 여러 가지가 있을 수 있습니다. 다음 정보를 확인하는 것이 좋습니다.

* **&#x200B;**&#x200B;추적&#x200B;**워크플로에 오류가 있습니까?**

[Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=ko){target="_blank"}를 참조하세요.

![](assets/tracking_scheduled_task.png)

* **서버에서** trackinglogd **모듈이 실행되고 있습니까?**

  [로그 파일](../../production/using/log-files.md)을 참조하세요.

* **변경되었습니까?**

  추적 별칭을 사용하여 서버 연결 손실을 트리거할 수 있습니다.
