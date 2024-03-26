---
product: campaign
title: 이미지 누락
description: 이미지 누락
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 11%

---

# 이미지 누락{#images-missing}



17.9 릴리스에서는 여러 파일(특히 아이콘)이 이동되었습니다.

호스팅된 고객의 경우 영향을 주지 않습니다. 온-프레미스 설치의 경우 다음을 읽으십시오.

**Apache 사용자:**

Apache 사용자는 제공된 를 사용하는 경우 영향을 받지 않습니다 **apache_neolane.conf**.

**IIS 사용자:**

IIS 사용자(Windows의 경우)의 경우 빌드 업데이트 후 콘솔에 여러 아이콘이 표시되지 않습니다. 추가 IIS 업데이트 단계가 필요합니다.

1. 빌드 업데이트 후 를 두 번 클릭합니다 **iis_neolane_setup.vbs** Campaign 설치 디렉터리에 있습니다. 기본 경로는 C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf입니다.
1. 이전 단계에서 업데이트한 IIS 사이트를 다시 시작합니다.
