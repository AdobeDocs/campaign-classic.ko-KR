---
product: campaign
title: 이미지 누락
description: 이미지 누락
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# 이미지 누락{#images-missing}

![](../../assets/v7-only.svg)

17.9 릴리스에서는 여러 파일(특히 아이콘)이 이동되었습니다.

호스팅된 고객의 경우 영향을 주지 않습니다. 온-프레미스 설치의 경우 다음을 참조하십시오.

**Apache 사용자:**

제공된 를 사용하는 Apache 사용자는 영향을 받지 않습니다 **apache_neolane.conf**.

**IIS 사용자:**

IIS 사용자(Windows의 경우)의 경우 빌드 업데이트 후 콘솔에 여러 아이콘이 누락됩니다. 추가 IIS 업데이트 단계가 필요합니다.

1. 빌드 업데이트 후 두 번 클릭합니다 **iis_neolane_setup.vbs** ( Campaign 설치 디렉토리)에 있습니다. 기본 경로는 C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf입니다.
1. 이전 단계에서 업데이트된 IIS 사이트를 다시 시작합니다.
