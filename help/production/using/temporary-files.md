---
product: campaign
title: 임시 파일
description: 임시 파일
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# 임시 파일{#temporary-files}



시스템이 프로덕션에 들어갈 때 다음과 같은 오류 메시지가 (특히 게재 로그에) 표시될 수 있습니다.

*&#39;/tmp/tmp0000.tmp&#39; 파일의 이름을 /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml 로 바꿀 수 없습니다.(errno=18, 잘못된 교차 장치 링크) (iRc=-52)*

원인은 다음과 같습니다.

Adobe Campaign은 **/tmp**&#x200B;로 이동한 다음 이름을 로 변경합니다. **/usr/local/neolane/nl6/var**. 이 오류는 두 폴더(**/tmp** 및 **/usr/local/neolane/nl6/var**&#x200B;즉, **/var/nl6**)은 서로 다른 장치에 해당합니다. 다음 **df** 확인에는 명령이 사용됩니다.

이 문제를 해결하려면 임시 파일을 대상과 동일한 장치에서 생성해야 합니다.

예를 들어, 다음을 실행합니다.

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

그런 다음 를 추가합니다.

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
