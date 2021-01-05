---
solution: Campaign Classic
product: campaign
title: 이미지 누락
description: 이미지 누락
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---


# 이미지 누락{#images-missing}

17.9 릴리스에서는 여러 파일(특히 아이콘)이 이동되었습니다.

호스팅 고객에게는 아무런 영향을 주지 않습니다. 온-프레미스 설치의 경우 다음을 참조하십시오.

**Apache 사용자:**

Apache 사용자가 제공된 **apache_neolane.conf**&#x200B;을(를) 사용하는 경우에는 영향을 주지 않습니다.

**IIS 사용자:**

IIS 사용자(Windows의 경우)의 경우 빌드 업데이트 후 콘솔에 여러 개의 아이콘이 없는 것으로 나타납니다. 추가 IIS 업데이트 단계는 다음과 같습니다.

1. 빌드 업데이트 후 캠페인 설치 디렉토리에 있는 **iis_neolane_setup.vbs**&#x200B;를 두 번 클릭합니다. 기본 경로는 C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf입니다.
1. 이전 단계로 업데이트된 IIS 사이트를 다시 시작합니다.
