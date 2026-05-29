---
product: campaign
title: 이미지 누락
description: 이미지 누락
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c
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
source-wordcount: 111
ht-degree: 5%

---

# 이미지 누락{#images-missing}



17.9 릴리스에서는 여러 파일(특히 아이콘)이 이동되었습니다.

호스팅된 고객의 경우 영향을 주지 않습니다. 온-프레미스 설치의 경우 다음을 읽으십시오.

**Apache 사용자:**

Apache 사용자가 제공된 **apache_neolane.conf**&#x200B;을(를) 사용하는 경우 Apache 사용자에게 영향을 주지 않습니다.

**IIS 사용자:**

IIS 사용자(Windows의 경우)의 경우 빌드 업데이트 후 콘솔에 여러 아이콘이 표시되지 않습니다. 추가 IIS 업데이트 단계가 필요합니다.

1. 빌드를 업데이트한 후 Campaign 설치 디렉터리에 있는 **iis_neolane_setup.vbs**&#x200B;을(를) 두 번 클릭합니다. 기본 경로는 C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf입니다.
1. 이전 단계에서 업데이트한 IIS 사이트를 다시 시작합니다.
