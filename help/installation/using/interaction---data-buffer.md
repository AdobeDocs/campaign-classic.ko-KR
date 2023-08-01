---
product: campaign
title: 상호 작용 - 데이터 버퍼
description: 상호 작용 - 데이터 버퍼
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 3%

---

# 상호 작용 - 데이터 버퍼{#interaction-data-buffer}



오퍼 제안 계산의 동기화를 해제하여 인바운드 상호 작용 성능을 높이도록 데이터 버퍼 영역을 구성할 수 있습니다. 이 구성은 인스턴스의 자체 구성 파일(config-Instance.xml)에서 수행됩니다.

Adobe Campaign에서 **데이터 버퍼 영역** 이 상호 작용 모듈에 도입되었습니다. 이렇게 하면 다음 작업을 수행할 수 있습니다. **성능 향상** 재고 및 오퍼 계산 비동기화를 통한 인바운드 상호 작용

호출(호출 데이터 포함/제외) 또는 상태 업데이트(updateStatus)에 의해서만 인바운드 상호 작용이 발생합니다.

수신자와 관련된 제안을 작성할 때 큐를 방지하기 위해 새 w 프로세스는 **데이터 버퍼 영역** 제안 허용 **비동기식으로 작성됨**. 이 데이터 버퍼 영역은 주기적으로 읽고 비웁니다. 기본 기간은 약 1초 정도이며 따라서 제안서 작성은 그룹화됩니다.

>[!NOTE]
>
>분산 아키텍처와 상호 작용을 사용하는 경우 이 매개 변수는 필수입니다.

데이터 버퍼 영역 **구성** 인스턴스의 구성 파일(config-Instance.xml)에서 수행할 수 있습니다.

>[!CAUTION]
>
>일부 구성은 Adobe에서 호스팅하는 배포에 대해 Adobe에 의해서만 수행될 수 있습니다. 예를 들어 서버 및 인스턴스 구성 파일에 액세스합니다. 다양한 배포에 대한 자세한 내용은 [호스팅 모델](../../installation/using/hosting-models.md) 섹션 또는 종료 [이 페이지](../../installation/using/capability-matrix.md).
>
>구성을 변경하려면 웹 서버(Apache:IIS)와 Adobe Campaign 프로세스를 다시 시작해야 합니다.\
>데이터 버퍼 영역을 구성한 후 조정된 하드웨어 구성을 사용할 수 있는지 확인하십시오. (존재하는 메모리 양).


데이터 버퍼 영역을 구성한 후 조정된 하드웨어 구성을 사용할 수 있는지 확인하십시오. (존재하는 메모리 양).

쓰기 데몬(프로세스 이름: interaction)에 대한 정의는 다음과 같습니다.

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

인바운드 상호 작용을 사용하는 경우 @autostart 속성이 &quot;true&quot;여야 Adobe Campaign 서버가 시작될 때 프로세스를 자동으로 실행할 수 있습니다.

인수 세부 사항:

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```
