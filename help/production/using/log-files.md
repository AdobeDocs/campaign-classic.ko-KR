---
product: campaign
title: 파일 로깅
description: 파일 로깅
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
badge-v7-prem: label="온-프레미스 및 하이브리드" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 4%

---

# 파일 로깅{#log-files}



로그 파일은 다음과 같이 구성됩니다.

![](assets/d_ncs_directory.png)

각 **nlserver** 모듈은 다음 디렉토리에 저장된 로그 파일을 생성합니다. **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

다음 **nlserver syslogd** 모듈이 로그를 디스크에 저장합니다. 이 모듈은 Unix와 유사합니다 **syslog 데몬**&#x200B;는 Unix와 Windows 간의 호환성을 위해 조정되었습니다. 다른 Adobe Campaign 모듈은 로그를 디스크에 저장하지 않고 이 작업을 **syslogd** UDP 패킷을 전송하여 모듈을 만듭니다.

기본적으로 Adobe Campaign 플랫폼에는 **syslogd** 모듈이 설치되었지만 다른 모듈을 사용할 수 있습니다. **syslog 데몬**. 이 모듈은에 로그 파일을 만듭니다. **log** 디렉토리.

다중 인스턴스 모듈의 로그는 다음 디렉토리에 저장됩니다. **`<installation directory>`/var/default/log/**. 모든 인스턴스에서 동일한 로그 파일을 공유합니다(예: **web.log**).

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
>다음 **리디렉터** 디렉터리는 리디렉션 서버에만 있습니다. 다음 **url** 하위 디렉터리에는 리디렉션할 URL과 하위 디렉터리의 일치 항목이 포함되어 있습니다 **log** 에는 추적 로그가 포함되어 있습니다. 추적 로그를 생성하려면 다음을 수행합니다 **trackinglogd** 모듈이 실행 중이어야 합니다.

성능 및 스토리지 최적화를 위해 logins.log 파일은 매일 여러 파일로 분할되며(logins.yy-mm-dd.log) 최대 365개의 파일이 유지됩니다. 일 수는 serverConf.xml의 syslogd(**최대 로그인 수 파일** 선택 사항). 다음에서 설명서를 참조하십시오. [서버 구성 파일](../../installation/using/the-server-configuration-file.md#syslogd).

기본적으로 로그는 모듈 및 인스턴스당 10MB 파일 두 개로 제한됩니다. 두 번째 파일은 다음과 같습니다. **`<modulename>`_2.log**. 따라서 로그 크기는 2로 제한됩니다&#42;모듈 및 인스턴스당 10MB

그러나 더 큰 파일은 유지할 수 있습니다. 이 기능을 사용하려면 의 값을 **maxFileSizeMb=&quot;10&quot;** 에서 설정 **syslogd** 노드의 노드 **conf/serverConf.xml** 파일. 이 값은 로그 파일의 최대 크기(MB)를 나타냅니다.

로그에서 세부 수준을 유지하려면 다음을 사용하여 Adobe Campaign 모듈을 시작할 수 있습니다. **-verbose** 매개 변수:

**nlserver 시작 `<MODULE>`@`<INSTANCE>` -verbose**
