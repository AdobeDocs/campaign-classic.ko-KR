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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 임시 파일{#temporary-files}

시스템이 프로덕션에 들어갈 때 다음과 같은 오류 메시지가 나타나는 경우(특히 배달 로그에 있음):

**파일 &#39;/tmp/tmp0000.tmp&#39;의 이름을 /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link)(iRc=-52)**

원인은 다음과 같습니다.

Adobe Campaign은 **/tmp**&#x200B;아래에 임시 파일을 생성한 다음 이름을 변경하여 **/usr/local/neolane/nl6/var로**&#x200B;이동합니다. 이 오류는 폴더(**/tmp** 및 **/usr/local/neolane/nl6/var**)가 **/var/nl6에**&#x200B;대한 심볼릭 링크)가 모두 다른 장치에 해당되는 경우에 발생합니다. 검증을 위해 **df** 명령을 사용합니다.

이 문제를 해결하려면, 임시 파일을 대상과 동일한 장치에서 생성해야 합니다. 예를 들어 다음을 실행하여

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

다음을 추가한 다음

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

