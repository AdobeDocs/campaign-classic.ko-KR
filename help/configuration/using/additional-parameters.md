---
product: campaign
title: 추가 웹 추적 매개 변수
description: 웹 추적에 대한 매개 변수에 대해 자세히 알아보십시오
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---

# 추가 매개 변수{#additional-parameters}

![](../../assets/v7-only.svg)

## 매개 변수 정의 {#definition-of-parameters}

Adobe Campaign 플랫폼에서는 표준으로 두 개의 TRANSACTION-type 웹 추적 매개 변수를 제공합니다.

* **금액**: 거래 금액을 나타냅니다.
* **문서**: 거래의 항목 수를 나타냅니다.

이러한 매개 변수는 **nms:webTrackingLog** 스키마이며, 보고에 표시되는 지표 중 일부입니다.

추가 매개 변수를 정의하려면 이 스키마를 확장해야 합니다.

**예제**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

추적 로그 목록(게재 또는 수신자)을 구성하여 이러한 매개 변수의 값을 표시할 수 있습니다.

## 리디렉션 서버 구성 {#redirection-server-configuration}

서버 구성에서 웹 추적 매개 변수에 고려할 최대 문자 수를 정의할 수 있습니다.

>[!IMPORTANT]
>
>고려할 최대 문자 수를 늘리면 플랫폼의 웹 추적 성능에 영향을 줄 수 있습니다.

이렇게 하려면 을(를) 수정합니다 **webTrackingParamSize** 의 속성 **`<trackinglogd>`** 요소의 요소 **serverConf.xml** 파일. 이 파일은 **conf** Adobe Campaign 설치 디렉토리의 하위 디렉토리입니다.

**예제**:

기본값은 64자입니다. 이 값을 통해 **금액** 및 **문서** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;) 표준 매개 변수입니다.

위의 확장 스키마 예에서 표시된 매개 변수(이름 + 값 크기)를 모두 고려하여 구성을 수정하여 100자를 고려하여 (&quot;amount=xxxxxxxxxx&amp;article=xxxxxxxxxxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxxxxxx&quot;)할 수 있습니다.

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

구성을 수정한 경우 다음을 수행해야 합니다.

* 리디렉션 모듈(Apache, IIS 등)을 호스팅하는 웹 서버를 중지합니다.
* Adobe Campaign 서버를 중지합니다. **net stop nlserver6** Windows에서는 **/etc/init.d/nlserver6 중지** Linux에서

   >[!NOTE]
   >
   >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systectl stop nlserver**

* Linux에서 공유 메모리 세그먼트를 **ipcrm** command,
* Adobe Campaign 서버를 다시 시작합니다. **net start nlserver6** Windows에서는 **/etc/init.d/nlserver6 시작** Linux에서

   >[!NOTE]
   >
   >20.1부터 다음 명령을 대신 사용하는 것이 좋습니다(Linux의 경우). **systectl start nlserver**

* 웹 서버를 다시 시작합니다.

**예**: Linux에서 구성을 고려합니다.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>Linux의 경우 **webTrackingParamSize** 또는 **maxSharedLogs** 매개 변수를 사용하면 공유 메모리(SHM)의 크기를 늘려야 할 수도 있습니다.
