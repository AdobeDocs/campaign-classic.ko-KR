---
product: campaign
title: 운영 원칙
description: 운영 원칙
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 30f2451849dec0f640915e81c36d0a9c5f466d6c
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 1%

---

# 운영 원칙{#operating-principle}

![](../../assets/v7-only.svg)

기술적으로 Adobe Campaign 플랫폼은 여러 모듈을 기반으로 합니다.

많은 Adobe Campaign 모듈이 있습니다. 일부는 지속적으로 작동하지만 일부는 관리 작업(예: 데이터베이스 연결 구성)을 수행하거나 반복 작업(예: 추적 정보 통합)을 실행하기 위해 가끔 시작됩니다.

다음과 같은 세 가지 유형의 Adobe Campaign 모듈이 있습니다.

* 다중 인스턴스 모듈: 모든 인스턴스에 대해 단일 프로세스가 실행됩니다. 이는 다음 모듈에 적용됩니다. **웹**, **sylogd**, **trackinglogd** 및 **감시** (활동: **config-default.xml** 파일)에 액세스할 수 없습니다.
* 모노 인스턴스 모듈: 하나의 프로세스는 인스턴스당 실행됩니다. 이는 다음 모듈에 적용됩니다. **mta**, **wfserver**, **inMail**, **sms** 및 **stat** (활동: **config-`<instance>`.xml** 파일)에 액세스할 수 없습니다.
* 유틸리티 모듈: 이러한 모듈은 가끔 실행되어 가끔 또는 반복적인 작업을 수행하는 모듈입니다.**cleanup**, **config**, 추적 로그 다운로드 등).

모듈 관리는 명령줄 도구를 사용하여 수행합니다 **nlserver** 에 설치 **bin** 설치 폴더의 디렉토리입니다.

의 일반 구문 **nlserver** 도구는 다음과 같습니다.

**nlserver `<command>``<command arguments>`**

사용 가능한 모듈 목록에 대해서는 **nlserver** 명령.

사용 가능한 모듈은 다음 표에 자세히 설명되어 있습니다.

| 명령 | 설명 |
|---|---|
| aliasCleaning | 열거형 값 표준화 |
| 과금 | 시스템 활동 보고서를 billing@neolane.net에 보내는 중 |
| cleanup | 데이터베이스 정리: 데이터베이스에서 오래된 데이터를 삭제하고 데이터베이스 엔진 최적기에서 사용하는 통계 업데이트를 실행합니다. |
| config | 서버 구성 수정 |
| 내보내기 | 명령줄에서 내보내기: 명령줄에서 Adobe Campaign 클라이언트 콘솔에서 만든 내보내기 모델을 보낼 수 있습니다. |
| fileconvert | 설정된 크기 파일 변환 |
| 가져오기 | 명령줄에서 가져오기: Adobe Campaign 클라이언트 콘솔에서 만든 가져오기 모델을 명령줄에서 보낼 수 있습니다. |
| inMail | 인바운드 메일 분석기 |
| 설치 프로그램 | 고객 설치 파일의 가용성 |
| javascript | SOAP API에 대한 액세스를 사용하여 JavaScript 스크립트 실행. |
| 작업 | 명령줄 처리 |
| 병합 | 양식 병합 |
| midSourcing | 중간 소싱 모드에서 게재 정보 복구 |
| 모니터 | XML 서버 프로세스 및 예약된 작업의 상태를 인스턴스별로 표시합니다. |
| mta | 주 에이전트 전송 메시지 |
| 패키지 | 엔티티 패키지 파일 가져오기 또는 내보내기 |
| pdump | 서버 프로세스 상태 표시 |
| 준비 | 게재 작업 준비 |
| 다시 시작 | 부분 서버 다시 시작 |
| runwf | 워크플로우 인스턴스 실행 |
| 종료 | 전체 시스템 종료 |
| sms | SMS 알림 처리 |
| sql | SQL 스크립트 실행 |
| start | 추가 시작 |
| stat | MTA 연결 통계 유지 |
| stop | 부분 시스템 종료 |
| submitda | 게재 작업 제출 |
| sylogd | 로그 및 추적 쓰기 서버 |
| 추적 | 추적 로그 통합 및 검색 |
| trackinglogd | 추적 로그 쓰기 및 제거 서버 |
| 감시 | 시작 및 모니터링 인스턴스 |
| 웹 | 애플리케이션 서버(HTTP 및 SOAP) |
| wfserver | 워크플로우 서버 |

>[!IMPORTANT]
>
>마지막 모듈이 하나 있습니다. 애플리케이션 서버에 연결된 추적 및 릴레이 모듈은 성능을 위해 기본 메커니즘을 통해 동적 라이브러리를 통해 Apache 또는 IIS 웹 서버로 통합됩니다. 이 모듈을 시작하거나 관리할 수 있는 Adobe Campaign 명령이 없습니다. 따라서 웹 서버 자체의 명령을 사용해야 합니다.

모듈 사용 및 해당 매개 변수의 구문은 다음 명령을 사용하여 표시됩니다. **nlserver `[module]` -?**

예제:

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
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
