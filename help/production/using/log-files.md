---
title: 로그 파일
seo-title: 로그 파일
description: 로그 파일
seo-description: null
page-status-flag: never-activated
uuid: 266bc067-0218-4b3e-941c-dc5cd0b6a10d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: fac3e3ec-82a7-4087-ba88-2b28b0f69d1c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 2%

---


# 로그 파일{#log-files}

로그 파일은 다음과 같이 구성됩니다.

![](assets/d_ncs_directory.png)

각 **nlserver** 모듈은 다음 디렉토리에 저장된 로그 파일을 생성합니다. **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

nlserver **syslogd** 모듈은 로그를 디스크에 저장합니다. 이 모듈은 Unix **syslog 데몬과**&#x200B;비슷하지만 Unix와 Windows 간의 호환성을 위해 조정되었습니다. 다른 Adobe Campaign 모듈은 로그를 디스크에 저장하지 않습니다.UDP 패킷을 보내 이 **작업을** syslogd 모듈로 위임합니다.

기본적으로 Adobe Campaign 플랫폼에 **syslogd** 모듈이 설치되어 있지만 다른 **syslog 데몬을 사용할 수 있습니다**. 이 모듈은 **로그** 디렉토리에 로그 파일을 생성합니다.

다중 인스턴스 모듈의 로그는 다음 디렉토리에 저장됩니다. **`<installation directory>`/var/default/log/**. 동일한 로그 파일은 모든 인스턴스(예: **web.log**)에서 공유합니다.

다른 모듈의 로그는 인스턴스 이름을 따서 명명된 하위 폴더에 저장됩니다. 각 인스턴스에는 자체 로그 파일이 있습니다.

다중 인스턴스 로그 파일은 다음 표에 나열되어 있습니다.

| 파일 | 설명 |
|---|---|
| web.log | 웹 모듈 로그(클라이언트 콘솔, 보고서, SOAP API 등) |
| webmdl.log | 리디렉션 모듈에서 로그 |
| watchdog.log | Adobe Campaign 프로세스 모니터링 모듈의 로그 |
| trackinglogd.log | 추적 로그 |

모노 인스턴스 로그 파일은 다음 표에 나열되어 있습니다.

| 파일 | 설명 |
|---|---|
| mta.log | mta 모듈 로그 |
| mtachild.log | 메시지 배달 처리 로그 |
| wfserver.log | 워크플로 서버 모듈의 로그 |
| runwf.log | 워크플로우 실행 로그 |
| inMail.log | 바운스 메일 모듈 로그 |
| logins.log | 모든 로그인 시도를 Adobe Campaign에 기록합니다(성공 여부). |

>[!CAUTION]
>
>리디렉션 서버에만 **리디렉션** 디렉터리가 있습니다. url **하위 디렉토리에는 리디렉션할 URL의 일치 항목이** 포함되어 있으며 하위 디렉토리 **로그에는 추적 로그가** 포함되어 있습니다. 추적 로그를 생성하려면 **trackinglogd** 모듈이 실행되고 있어야 합니다.

성능 및 저장 최적화를 위해 logins.log 파일은 하루 1회(logins.yy-mm-dd.log)에 최대 365개의 파일이 보존됩니다. serverConf.xml에서 sylogid(**maxNumberOfLoginsFiles 옵션)의 일 수를 변경할 수** 있습니다. 자세한 내용은 [서버 구성 파일의 설명서를 참조하십시오](../../installation/using/the-server-configuration-file.md#syslogd).

기본적으로 로그는 모듈당 및 인스턴스당 두 개의 10MB 파일로 제한됩니다. 두 번째 파일은 다음과 같습니다. **`<modulename>`_2.log**. 따라서 로그 크기는 모듈당 및 인스턴스당 2*10MB로 제한됩니다.

그러나 더 큰 파일을 유지할 수 있습니다. 이를 활성화하려면 conf/serverConf.xml 파일의 **syslogd** 노드에서 **maxFileSizeMb=&quot;10&quot;** 설정 값을 **** 변경하십시오. 이 값은 로그 파일의 최대 크기(MB)를 나타냅니다.

로그에서 세부 수준을 더 유지하려면 세부 정보 **** 매개 변수를 사용하여 Adobe Campaign 모듈을 시작할 수 있습니다.

**nlserver start`<MODULE>`@`<INSTANCE>`-verbose**
