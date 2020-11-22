---
solution: Campaign Classic
product: campaign
title: 상호 작용 - 데이터 버퍼
description: 상호 작용 - 데이터 버퍼
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 3%

---


# 상호 작용 - 데이터 버퍼{#interaction-data-buffer}

>[!NOTE]
>
>일부 구성은 Adobe에서 호스팅하는 배포에 대해서만 Adobe에서 수행할 수 있습니다. 예를 들어 서버 및 인스턴스 구성 파일에 액세스하려면 다른 배포에 대한 자세한 내용은 [호스팅 모델](../../installation/using/hosting-models.md) 섹션 또는 [이 페이지를 참조하십시오](../../installation/using/capability-matrix.md).

Adobe Campaign에서 **데이터 버퍼 영역이** 상호 작용 모듈에 도입되었습니다. 따라서 재고 및 오퍼 계산을 **동기화하여 인바운드 상호 작용의 성능을** 높일 수 있습니다.

호출(호출 데이터 포함 또는 없는 호출) 또는 상태 업데이트(updateStatus)에 의해서만 인바운드 상호 작용이 우려됩니다.

수신자와 관련된 제안을 작성할 때 큐를 피하려면 새 w 프로세스가 제안을 비동기식으로 **작성할 수 있는** 데이터 버퍼 영역을 **생성합니다**. 이 데이터 버퍼 영역은 주기적으로 읽고 비웁니다. 기본 기간은 약 1초의 간격입니다. 따라서 제안 쓰기는 그룹화됩니다.

데이터 버퍼 영역 **구성을** 인스턴스의 구성 파일(config-Instance.xml)에서 수행할 수 있습니다.

>[!NOTE]
>
>구성을 변경하려면 웹 서버(Apache:IIS)와 Adobe Campaign 프로세스를 다시 시작해야 합니다.\
>데이터 버퍼 영역을 구성한 후 수정된 하드웨어 구성을 사용할 수 있는지 확인하십시오. (메모리 양).

데이터 버퍼 영역을 구성한 후 수정된 하드웨어 구성을 사용할 수 있는지 확인하십시오. (메모리 양).

쓰기 데몬에 대한 정의(프로세스 이름:상호 작용은 다음과 같습니다.

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

인바운드 상호 작용을 사용하는 경우 Adobe Campaign 서버가 시작될 때 프로세스를 자동으로 시작하려면 @autostart 속성이 &quot;true&quot;여야 합니다.

인수 세부 정보:

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

