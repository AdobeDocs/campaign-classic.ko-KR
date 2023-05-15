---
product: campaign
title: 파일 로깅
description: 파일 로깅
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# 파일 로깅{#log-files}



로그 파일은 다음과 같이 구성됩니다.

![](assets/d_ncs_directory.png)

각 **nlserver** 모듈은 다음 디렉토리에 저장된 로그 파일을 생성합니다. **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

다음 **nlserver sylogd** 모듈이 로그를 디스크에 저장합니다. 이 모듈은 Unix와 유사합니다 **syslog 데몬**&#x200B;은(는) Unix와 Windows 간에 호환되도록 조정되었습니다. 다른 Adobe Campaign 모듈은 로그를 디스크에 저장하지 않습니다. 이 작업을 **sylogd** 모듈(UDP 패킷 전송)

기본적으로 Adobe Campaign 플랫폼에는 **sylogd** 모듈에 설치되지만 다른 모듈을 사용할 수 있습니다 **syslog 데몬**. 이 모듈은 **로그** 디렉토리.

다중 인스턴스 모듈의 로그는 다음 디렉토리에 저장됩니다. **`<installation directory>`/var/default/log/**. 동일한 로그 파일은 모든 인스턴스(예: **web.log**).

다른 모듈의 로그는 인스턴스의 이름을 따서 명명된 하위 폴더에 저장됩니다. 각 인스턴스에는 자체 로그 파일이 있습니다.

다중 인스턴스 로그 파일은 다음 테이블에 나열됩니다.

| 파일 | 설명 |
|---|---|
| web.log | 웹 모듈 로그(클라이언트 콘솔, 보고서, SOAP API 등) |
| webmdl.log | 리디렉션 모듈에서 로그 |
| watchdog.log | Adobe Campaign 프로세스 모니터링 모듈에서 로그 |
| trackinglogd.log | 추적 로그 |

모노 인스턴스 로그 파일은 다음 테이블에 나열됩니다.

| 파일 | 설명 |
|---|---|
| mta.log | mta 모듈 로그 |
| mtachild.log | 메시지 게재 처리 로그 |
| wfserver.log | 워크플로우 서버 모듈의 로그 |
| runwf.log | 워크플로우 실행 로그 |
| inMail.log | 바운스 메일 모듈 로그 |
| logins.log | Adobe Campaign에 대한 모든 로그인 시도를 기록합니다(성공 또는 아님) |

>[!IMPORTANT]
>
>다음 **리디렉션** 디렉터리는 리디렉션 서버에만 있습니다. 다음 **url** 하위 디렉토리에는 리디렉션할 URL과 하위 디렉토리가 있습니다. **로그** 추적 로그를 포함합니다. 추적 로그를 생성하려면 **trackinglogd** 모듈이 실행 중이어야 합니다.

성능 및 저장 최적화를 위해 logins.log 파일은 매일 1회(logins.yy-mm-dd.log)로 여러 파일로 분할되며 최대 365개의 파일이 유지됩니다. serverConf.xml의 syslogd(**maxNumberOfLoginsFiles** 선택 사항). 다음 항목에 대한 설명서를 참조하십시오. [서버 구성 파일](../../installation/using/the-server-configuration-file.md#syslogd).

기본적으로 로그는 모듈당 2개의 10MB 파일 및 인스턴스당 제한됩니다. 두 번째 파일을 라고 합니다. **`<modulename>`_2.log**. 따라서 로그 크기는 2로 제한됩니다&#42;모듈당 및 인스턴스당 10MB입니다.

그러나 더 큰 파일을 유지할 수 있습니다. 이를 활성화하려면 **maxFileSizeMb=&quot;10&quot;** 설정 **sylogd** 노드 **conf/serverConf.xml** 파일. 이 값은 로그 파일의 최대 크기(MB)를 나타냅니다.

로그에서 세부 사항을 추가로 유지하려면 **-verbose** 매개 변수:

**nlserver 시작 `<MODULE>`@`<INSTANCE>` -verbose**
