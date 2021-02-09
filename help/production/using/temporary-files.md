---
solution: Campaign Classic
product: campaign
title: 임시 파일
description: 임시 파일
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# 임시 파일{#temporary-files}

시스템을 제작할 때 다음과 같은 오류 메시지가(특히 배달 로그에 있음)표시될 수 있습니다.

*파일 &#39;/tmp/tmp0000.tmp&#39;의 이름을 /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, 잘못된 상호 장치 링크)(iRc=-52)로 변경할 수 없습니다.*

원인은 다음과 같습니다.

Adobe Campaign은 **/tmp** 아래에 임시 파일을 생성한 다음 이름을 변경하여 **/usr/local/neolane/nl6/var**&#x200B;로 이동합니다. 이 오류는 두 폴더(**/tmp** 및 **/usr/local/neolane/nl6/var**)가 모두 다른 장치에 해당하는 경우에 발생합니다. 이 두 폴더는 사실상 **/var/nl6**&#x200B;에 대한 심볼 링크입니다. 검증에는 **df** 명령이 사용됩니다.

이 문제를 해결하려면 대상 장치와 동일한 장치에서 임시 파일을 생성해야 합니다.

예를 들어 다음을 실행합니다.

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

그런 다음 다음을 추가합니다.

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
