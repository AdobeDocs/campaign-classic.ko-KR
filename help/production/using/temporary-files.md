---
title: 임시 파일
seo-title: 임시 파일
description: 임시 파일
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 6%

---


# 임시 파일{#temporary-files}

시스템이 프로덕션에 들어갈 때 다음과 같은 오류 메시지가 나타나는 경우(특히 배달 로그에 있음):

**파일 &#39;/tmp/tmp0000.tmp&#39;의 이름을 /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, 잘못된 상호 장치 링크)(iRc=-52)로 변경할 수 없습니다.**

원인은 다음과 같습니다.

Adobe Campaign은 **/tmp**&#x200B;아래에 임시 파일을 생성한 다음 이름을 변경하여 **/usr/local/neolane/nl6/var로 이동시킵니다**. 이 오류는 폴더(**/tmp** 및 **/usr/local/neolane/nl6/var**)가 모두 **/var/nl6**&#x200B;에 대한 상징적 링크인 경우발생합니다. 확인을 위해 **df** 명령을 사용합니다.

이 문제를 해결하려면, 임시 파일은 대상과 동일한 장치에서 생성되어야 합니다. 예를 들어 다음을 실행하여

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

다음을 추가하여

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

