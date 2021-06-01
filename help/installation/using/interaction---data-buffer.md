---
product: campaign
title: 상호 작용 - 데이터 버퍼
description: 상호 작용 - 데이터 버퍼
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# 상호 작용 - 데이터 버퍼{#interaction-data-buffer}

오퍼 제안 계산을 동기화하여 인바운드 상호 작용 성능을 증가하도록 데이터 버퍼 영역을 구성할 수 있습니다. 이 구성은 인스턴스의 고유한 구성 파일(config-Instance.xml)에서 수행됩니다.

Adobe Campaign에서 **데이터 버퍼 영역**&#x200B;이(가) 상호 작용 모듈에 도입되었습니다. 이렇게 하면 스톡 및 오퍼 계산을 동기화하여 인바운드 상호 작용의 **성능**&#x200B;을 늘릴 수 있습니다.

이것은 호출(호출 데이터 포함 또는 호출 데이터 없음) 또는 상태 업데이트(updateStatus)에 의해서만 인바운드 상호 작용에 관한 것입니다.

수신자와 관련된 제안을 작성할 때 큐를 피하려면 새 W 프로세스가 제안서를 비동기식으로 **쓸 수 있는**&#x200B;데이터 버퍼 영역&#x200B;**을 생성합니다.** 이 데이터 버퍼 영역은 주기적으로 읽고 비웁니다. 기본 기간은 약 1초 간격입니다. 따라서 제안 쓰기는 그룹화됩니다.

>[!NOTE]
>
>이 매개 변수는 분산 아키텍처와 상호 작용을 사용하는 경우 필수입니다.

데이터 버퍼 영역 **구성**&#x200B;은 인스턴스의 구성 파일(config-Instance.xml)에서 수행할 수 있습니다.

>[!CAUTION]
>
>일부 구성은 Adobe이 호스팅하는 배포에 대해서만 Adobe에서 수행할 수 있습니다. 예를 들어, 서버 및 인스턴스 구성 파일에 액세스할 수 있습니다. 서로 다른 배포에 대한 자세한 내용은 [호스팅 모델](../../installation/using/hosting-models.md) 섹션 또는 [이 페이지](../../installation/using/capability-matrix.md)를 참조하십시오.
>
>구성을 변경하려면 웹 서버(Apache:IIS)와 Adobe Campaign 프로세스를 다시 시작해야 합니다.\
>데이터 버퍼 영역을 구성한 후 수정된 하드웨어 구성을 사용할 수 있는지 확인하십시오. (메모리 양).


데이터 버퍼 영역을 구성한 후 수정된 하드웨어 구성을 사용할 수 있는지 확인하십시오. (메모리 양).

쓰기 데몬에 대한 정의(이름이 지정된 프로세스:상호 작용)은 다음과 같습니다.

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
