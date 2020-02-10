---
title: 로그 정확도
seo-title: 로그 정확도
description: 로그 정확도
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# 로그 정확도{#log-precision}

이 프로세스를 모든 Adobe Campaign 모듈에 적용하여 로그 정확도를 높일 수 있습니다.

더 높은 수준의 로그를 사용하여 프로세스를 다시 시작하는 작업이 수반됩니다.

>[!CAUTION]
>
>이 절차는 이 모듈에서 진행 중인 서비스를 취소합니다.

Adobe Campaign은 다음 두 가지 수준의 로그로 작동할 수 있습니다.

1. 세부 정보 **표시** 모드는 표준 수준 이후의 첫 번째 수준입니다. 다음 명령을 사용하여 활성화합니다.

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   오류가 실제로 발생했는지 확인한 다음 일반적인 방법으로 프로세스를 다시 시작합니다.

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. TraceFilter **모드를** 사용하여 최대 로그 수를 저장할 수 있습니다. 다음 명령으로 활성화됩니다.

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >tracefilter:* **를 사용하는**&#x200B;경우 모든 로그 유형이 활성화됩니다.ncm, rdr, nms, jst, 타이밍, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   가장 유용한 로그 유형은 다음과 같습니다. **wdbc** (모든 SQL 호출 표시), **soap** (모든 SOAP 호출 표시), **ldap** (인증 후 모든 LDAP 쿼리 표시) **, xtkquery** 에는 모든 querydef 목록이 표시됩니다.\
   개별적으로 사용할 수 있습니다(**예: tracefilter:soap, wdbc** ). 모두 활성화하고 특정 타인을 제외하도록 선택할 수도 있습니다.추적 **필터:*,!soap**

   오류가 실제로 발생했는지 확인한 다음 일반적인 방법으로 프로세스를 다시 시작합니다.

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!CAUTION]
이러한 명령의 로그는 모듈의 로그 파일에 저장됩니다.

다음은 웹 모듈과 관련된 예입니다. 다른 모듈은 위에 표시된 대로 작동합니다.

이 명령을 보내기 전에 진행 중인 작업이 영향을 받지 않는지 확인하십시오.

```
nlserver pdump -who
```

그런 다음 TraceFilter 모드에서 모듈을 종료한 후 다시 **시작합니다** .

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

다른 예:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
추적 **파일** 모드를 사용하면 로그를 저장할 수 있습니다. 위의 예에서 로그는 **var//mta_debug.log`<instance-name>`및 var/default/web_debug.log** 파일에 **저장됩니다** .

>[!CAUTION]
Windows에서는 LD_PRELOAD 옵션을 추가하지 마십시오. 다음 명령이 필요합니다.\
nlserver web -tomcat -verbose -tracefilter:*

문제가 다시 발생하는지 확인한 다음 모듈을 다시 시작합니다.

```
nlserver restart web -tomcat -noconsole
```

모든 정보는 /usr/local/neolane/nl6/var/default/log/web.log 파일에서 확인할 수 **있습니다**.
