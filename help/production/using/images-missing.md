---
title: 이미지 누락
seo-title: 이미지 누락
description: 이미지 누락
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# 이미지 누락{#images-missing}

17.9 릴리스에서는 여러 파일(특히 아이콘)이 이동되었습니다.

호스팅 고객에게는 아무런 영향을 주지 않습니다. 온-프레미스 설치의 경우 다음을 참조하십시오.

**Apache 사용자:**

Apache 사용자가 제공된 **apache_neolane.conf를 사용할 경우 영향을 주지 않습니다.**

**IIS 사용자:**

IIS 사용자(Windows의 경우)의 경우 빌드 업데이트 후 콘솔에 몇 가지 아이콘이 누락된 것으로 나타납니다. 추가 IIS 업데이트 단계는 다음과 같습니다.

1. 빌드 업데이트 후 Campaign 설치 디렉토리에 있는 **iis_neolane_setup.vbs** 를 두 번 클릭합니다. 기본 경로는 C:\Program Files (x86)\Adobe\Adobe Campaign v7\tomcat-7\conf입니다.
1. 이전 단계에서 업데이트된 IIS 사이트를 다시 시작합니다.

