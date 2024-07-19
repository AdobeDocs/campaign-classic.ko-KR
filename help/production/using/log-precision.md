---
product: campaign
title: 로그 정밀도
description: 로그 정밀도
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 2%

---

# 로그 정밀도{#log-precision}



이 프로세스를 모든 Adobe Campaign 모듈에 적용하여 로그 정밀도를 높일 수 있습니다.

이 작업에는 더 높은 수준의 로그를 사용하여 프로세스를 다시 실행하는 작업이 포함됩니다.

>[!IMPORTANT]
>
>이 절차에서는 이 모듈에서 진행 중인 서비스를 취소합니다.

Adobe Campaign은 다음 두 가지 수준의 로그로 작동할 수 있습니다.

1. **Verbose** 모드는 표준 수준 이후의 첫 번째 수준입니다. 다음 명령을 사용하여 활성화합니다.

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   오류가 실제로 발생했는지 확인한 후 프로세스를 정상적으로 다시 시작합니다.

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. 최대 로그 수를 저장할 수 있는 **TraceFilter** 모드 다음 명령에 의해 활성화됩니다.

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >**tracefilter:&#42;**&#x200B;을(를) 사용하는 경우 모든 로그 유형이 활성화됩니다. ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   가장 유용한 로그 유형은 **wdbc**(모든 SQL 쿼리 표시), **soap**(모든 SOAP 호출 표시), **ldap**(인증 후 모든 LDAP 쿼리 표시), **xtkquery**(모든 querydef 목록 표시)입니다.\
   개별적으로 사용할 수 있습니다(예: **tracefilter:soap,wdbc**). 모든 기능을 활성화하고 특정 다른 기능을 제외하도록 선택할 수도 있습니다. **-tracefilter:&#42;,!soap**

   오류가 실제로 발생했는지 확인한 후 프로세스를 정상적으로 다시 시작합니다.

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
이러한 명령의 로그는 모듈의 로그 파일에 저장됩니다.

다음은 웹 모듈과 관련된 예입니다. 다른 모듈은 위에 표시된 대로 작동합니다.

이 명령을 보내기 전에 진행 중인 작업이 영향을 받지 않는지 확인하십시오.

```
nlserver pdump -who
```

그런 다음 **TraceFilter** 모드에서 모듈을 종료했다가 다시 시작하십시오.

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

또 다른 예:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
**Tracefile** 모드를 사용하면 로그를 저장할 수 있습니다. 위의 예에서 로그는 **var/`<instance-name>`/mta_debug.log** 및 **var/default/web_debug.log** 파일에 저장됩니다.

>[!IMPORTANT]
>
Windows에서는 LD_PRELOAD 옵션을 추가하지 마십시오. 다음 명령으로 충분합니다.\
nlserver web -tomcat -verbose -tracefilter:&#42;

문제가 다시 발생하는지 확인한 후 모듈을 다시 시작합니다.

```
nlserver restart web -tomcat -noconsole
```

모든 정보는 **/usr/local/neolane/nl6/var/default/log/web.log** 파일에서 사용할 수 있습니다.
