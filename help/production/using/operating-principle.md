---
title: 운영 원칙
seo-title: 운영 원칙
description: 운영 원칙
seo-description: null
page-status-flag: never-activated
uuid: a15929ca-5b1f-499a-a883-43fd0a318c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 5e9c17ad-14d2-4173-9fc9-0e48a21426c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 운영 원칙{#operating-principle}

기술적으로 Adobe Campaign 플랫폼은 여러 모듈을 기반으로 합니다.

Adobe Campaign 모듈도 많습니다. 일부는 지속적으로 작동하지만, 일부는 관리 작업(예: 데이터베이스 연결 구성)을 수행하거나 반복 작업(예: 추적 정보 통합)을 실행하기 위해 가끔 시작됩니다.

다음 세 가지 유형의 Adobe Campaign 모듈이 있습니다.

* 다중 인스턴스 모듈:단일 프로세스는 모든 인스턴스에 대해 실행됩니다. 이는 다음 모듈에 적용됩니다. **웹********** , **trackinglogd** 및 **** watchdogActivities (config default.xmlLogging 파일의 활동)
* 모노 인스턴스 모듈:한 프로세스는 인스턴스당 실행됩니다. 이는 다음 모듈에 적용됩니다. **mmmail**, **wfserver**, **inMail**, **sms ta** **** **`<instance>`** , andstatActivities (config-xml 파일의 구성).
* 유틸리티 모듈:이러한 모듈은 가끔 실행(**정리**, **구성**, 추적 로그 다운로드 등)되는 모듈입니다.

모듈 관리는 설치 폴더의 **bin** 디렉터리에 설치된 명령줄 도구 **nlserver** 를 사용하여 수행됩니다.

nlserver 도구의 일반 **구문은** 다음과 같습니다.

**nlserver`<command>``<command arguments>`**

사용 가능한 모듈 목록은 nlserver **명령을** 사용합니다.

사용 가능한 모듈은 다음 표에 자세히 설명되어 있습니다.

| 명령 | 설명 |
|---|---|
| aliasCleaning | 열거형 값 표준화 |
| 과금 | 시스템 활동 보고서를 billing@neolane.net으로 보내기 |
| 정리 | 데이터베이스 정리:데이터베이스에서 오래된 데이터를 삭제하고 데이터베이스 엔진 최적기에 사용되는 통계 업데이트를 실행합니다. |
| config | 서버 구성 수정 |
| 카피베이스 | 데이터베이스 복사본 |
| 내보내기 | 명령줄로 내보내기:adobe Campaign 클라이언트 콘솔에서 만든 내보내기 모델을 명령줄에 보낼 수 있습니다. |
| fileconvert | 세트 크기 파일 변환 |
| 가져오기 | 명령줄에 가져오기:adobe Campaign 클라이언트 콘솔에서 만든 가져오기 모델을 명령줄에 보낼 수 있습니다. |
| inMail | 인바운드 메일 분석기 |
| 설치 프로그램 | 고객 설치 파일의 가용성 |
| javascript | SOAP API에 액세스할 수 있는 JavaScript 스크립트 실행 |
| job | 명령줄 처리 |
| 병합 | 양식 병합 |
| midSourcing | 중간 소싱 모드에서 배달 정보 복구 |
| 모니터 | XML 서버 프로세스 및 예약된 작업의 상태를 인스턴스별로 표시합니다. |
| mta | 주 에이전트 전송 메시지 |
| package | 개체 패키지 파일 가져오기 또는 내보내기 |
| pdump | 서버 프로세스 상태 표시 |
| prefda | 배달 작업 준비 |
| 다시 시작 | 부분 서버 다시 시작 |
| runwf | 워크플로우 인스턴스 실행 |
| 종료 | 전체 시스템 종료 |
| sms | SMS 알림 처리 |
| sql | SQL 스크립트 실행 |
| start | 추가 시작 |
| stat | MTA 연결 통계 유지 |
| stop | 부분 시스템 종료 |
| 제출 | 배달 작업 제출 |
| sylogd | 로그 및 추적 쓰기 서버 |
| 추적 | 추적 로그 통합 및 검색 |
| trackinglogs | 추적 로그 작성 및 제거 서버 |
| 감시 | 시작 및 모니터링 인스턴스 |
| web | 응용 프로그램 서버(HTTP 및 SOAP) |
| wfserver | 워크플로 서버 |

>[!CAUTION]
>
>마지막 모듈은 다음과 같습니다.성능을 위해 기본 메커니즘을 통해 동적 라이브러리를 통해 Apache 또는 IIS 웹 서버에 통합된 추적 및 릴레이 모듈입니다. 이 모듈을 시작하거나 관리할 수 있는 Adobe Campaign 명령이 없습니다. 따라서 웹 서버 자체의 명령을 사용해야 합니다.

모듈 사용 및 해당 매개 변수의 구문은 다음 명령을 사용하여 표시됩니다. **nlserver`[module]`-?**

예:

**nlserver 구성 -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initialises for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```

