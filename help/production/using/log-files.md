---
product: campaign
title: 파일 로깅
description: 파일 로깅
feature: Monitoring
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 2%

---

# 파일 로깅{#log-files}



로그 파일은 다음과 같이 구성됩니다.

![](assets/d_ncs_directory.png)

각 **nlserver** 모듈은 **`<installation directory>`/var/`<instance>`/log/`<module>`.log** 디렉터리에 저장된 로그 파일을 생성합니다.

**nlserver syslogd** 모듈이 로그를 디스크에 저장합니다. 이 모듈은 Unix **syslog 데몬**&#x200B;과 비슷하지만 Unix와 Windows 간의 호환성을 위해 조정되었습니다. 다른 Adobe Campaign 모듈은 해당 로그를 디스크에 저장하지 않습니다. UDP 패킷을 전송하여 **syslogd** 모듈에 이 작업을 위임합니다.

기본적으로 Adobe Campaign 플랫폼에는 **syslogd** 모듈이 설치되어 있지만 다른 **syslog 데몬**&#x200B;을 사용할 수도 있습니다. 이 모듈은 **log** 디렉터리에 로그 파일을 만듭니다.

다중 인스턴스 모듈의 로그가 **`<installation directory>`/var/default/log/** 디렉터리에 저장됩니다. 모든 인스턴스(예: **web.log**)에서 동일한 로그 파일을 공유합니다.

다른 모듈의 로그는 인스턴스의 이름을 딴 하위 폴더에 저장됩니다. 각 인스턴스에는 자체 로그 파일이 있습니다.

다중 인스턴스 로그 파일은 다음 표에 나와 있습니다.

| 파일 | 설명 |
|---|---|
| web.log | 웹 모듈 로그(클라이언트 콘솔, 보고서, SOAP API 등) |
| webmdl.log | 리디렉션 모듈의 로그 |
| watchdog.log | Adobe Campaign 프로세스 모니터링 모듈의 로그 |
| trackinglogd.log | 추적 로그 |

다음 표에는 모노 인스턴스 로그 파일이 나열되어 있습니다.

| 파일 | 설명 |
|---|---|
| mta.log | mta 모듈 로그 |
| mtachild.log | 메시지 게재 처리 로그 |
| wfserver.log | 워크플로우 서버 모듈의 로그 |
| runwf.log | 워크플로우 실행 로그 |
| inMail.log | 바운스 메일 모듈 로그 |
| logins.log | Adobe Campaign에 대한 모든 로그인 시도를 기록합니다(성공 여부). |

>[!IMPORTANT]
>
>**redir** 디렉터리는 리디렉션 서버에만 있습니다. **url** 하위 디렉터리에는 리디렉션할 URL의 일치 항목이 포함되어 있고 하위 디렉터리 **log**&#x200B;에는 추적 로그가 포함되어 있습니다. 추적 로그를 생성하려면 **trackinglogd** 모듈이 실행되고 있어야 합니다.

성능 및 스토리지 최적화를 위해 logins.log 파일은 매일 여러 파일로 분할되며(logins.yy-mm-dd.log) 최대 365개의 파일이 유지됩니다. 서버Conf.xml의 syslogd(**maxNumberOfLoginsFiles** 옵션) 아래에 있는 일 수를 변경할 수 있습니다. [서버 구성 파일](../../installation/using/the-server-configuration-file.md#syslogd)에 대한 설명서를 참조하세요.

기본적으로 로그는 모듈 및 인스턴스당 10MB 파일 두 개로 제한됩니다. 두 번째 파일은 **`<modulename>`_2.log**&#x200B;입니다. 따라서 로그 크기는 모듈 및 인스턴스당 2&#42;10MB로 제한됩니다.

그러나 더 큰 파일은 유지할 수 있습니다. 이 기능을 사용하려면 **conf/serverConf.xml** 파일의 **syslogd** 노드에서 **maxFileSizeMb=&quot;10&quot;** 설정 값을 변경하십시오. 이 값은 로그 파일의 최대 크기(MB)를 나타냅니다.

로그에서 세부 수준을 유지하려면 **-verbose** 매개 변수로 Adobe Campaign 모듈을 시작할 수 있습니다.

**nlserver 시작 `<MODULE>`@`<INSTANCE>` -verbose**
