---
solution: Campaign Classic
product: campaign
title: 로그 파일
description: 로그 파일
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# 로그 파일{#log-files}

로그 파일은 다음과 같이 구성됩니다.

![](assets/d_ncs_directory.png)

각 **nlserver** 모듈은 다음 디렉토리에 저장된 로그 파일을 생성합니다.**`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

**nlserver syslogd** 모듈은 로그를 디스크에 저장합니다. 이 모듈은 Unix **syslog 데몬**&#x200B;과 비슷하지만 Unix와 Windows 간의 호환성을 위해 조정되었습니다. 다른 Adobe Campaign 모듈은 디스크에 로그를 저장하지 않습니다.UDP 패킷을 전송하여 이 작업을 **syslogd** 모듈에 위임합니다.

기본적으로 Adobe Campaign 플랫폼에는 **syslogd** 모듈이 설치되어 있지만 다른 **syslog 데몬**&#x200B;을 사용할 수 있습니다. 이 모듈은 **log** 디렉토리에 로그 파일을 만듭니다.

다중 인스턴스 모듈의 로그는 다음 디렉토리에 저장됩니다.**`<installation directory>`/var/default/log/**. 모든 인스턴스(예:**web.log**).

다른 모듈의 로그는 인스턴스 이름을 따서 명명된 하위 폴더에 저장됩니다. 각 인스턴스에는 자체 로그 파일이 있습니다.

다중 인스턴스 로그 파일은 다음 표에 나열되어 있습니다.

| 파일 | 설명 |
|---|---|
| web.log | 웹 모듈 로그(클라이언트 콘솔, 보고서, SOAP API 등) |
| webmdl.log | 리디렉션 모듈에서 로그 |
| watchdog.log | Adobe Campaign 프로세스 모니터링 모듈에서 로그 |
| trackinglogd.log | 추적 로그 |

모노 인스턴스 로그 파일은 다음 표에 나열되어 있습니다.

| 파일 | 설명 |
|---|---|
| mta.log | mta 모듈 로그 |
| mtachild.log | 메시지 배달 처리 로그 |
| wfserver.log | 워크플로 서버 모듈의 로그 |
| runwf.log | 워크플로우 실행 로그 |
| inMail.log | 바운스 메일 모듈 로그 |
| logins.log | Adobe Campaign에 대한 모든 로그인 시도를 기록합니다(성공 여부). |

>[!IMPORTANT]
>
>**리디렉션** 디렉토리는 리디렉션 서버에만 있습니다. **url** 하위 디렉토리에는 리디렉션할 URL의 일치 항목이 포함되어 있고 하위 디렉토리 **log**&#x200B;에는 추적 로그가 포함되어 있습니다. 추적 로그를 생성하려면 **trackinglogd** 모듈이 실행 중이어야 합니다.

성능 및 저장 최적화를 위해 logins.log 파일은 매일 한 번(logins.yy-mm-dd.log) 여러 파일로 분할되며 최대 365개의 파일이 유지됩니다. serverConf.xml에서 sylogin(**maxNumberOfLoginsFiles** 옵션)의 일 수를 변경할 수 있습니다. [서버 구성 파일](../../installation/using/the-server-configuration-file.md#syslogd)에 대한 설명서를 참조하십시오.

기본적으로 로그는 모듈당 및 인스턴스당 10MB 파일 2개로 제한됩니다. 두 번째 파일은 다음과 같습니다.**`<modulename>`_2.log**. 따라서 로그 크기는 모듈당 및 인스턴스당 2*10MB로 제한됩니다.

그러나 더 큰 파일을 유지할 수 있습니다. 이를 활성화하려면 **conf/serverConf.xml** 파일의 **syslogd** 노드에서 **maxFileSizeMb=&quot;10&quot;** 설정 값을 변경하십시오. 이 값은 로그 파일의 최대 크기(MB)를 나타냅니다.

로그에서 세부 정보 수준을 추가로 유지하려면 **-verbose** 매개 변수로 Adobe Campaign 모듈을 시작할 수 있습니다.

**nlserver start  `<MODULE>`@`<INSTANCE>` -verbose**
