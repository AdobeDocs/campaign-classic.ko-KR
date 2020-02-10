---
title: 추가 매개 변수
seo-title: 추가 매개 변수
description: 추가 매개 변수
seo-description: null
page-status-flag: never-activated
uuid: c223c84a-f8fd-43d3-9deb-b1c19d442c65
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 1b2ae224-8406-4506-b589-6e5f6631e87f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 추가 매개 변수{#additional-parameters}

## 매개 변수 정의 {#definition-of-parameters}

Adobe Campaign 플랫폼은 표준으로 두 개의 TRANSACTION 유형 웹 추적 매개 변수를 제공합니다.

* **금액**:거래 금액을 나타냅니다.
* **아티클**:는 트랜잭션의 항목 수를 나타냅니다.

이러한 매개 변수는 **nms:webTrackingLog** 스키마에서 정의되며 보고에 표시되는 표시기 중 일부입니다.

추가 매개 변수를 정의하려면 이 스키마를 확장해야 합니다.

**예**:

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

배달 또는 수신자의 추적 로그 목록을 구성하여 이러한 매개 변수의 값을 표시할 수 있습니다.

## 리디렉션 서버 구성 {#redirection-server-configuration}

서버 구성에서 웹 추적 매개 변수에 사용할 최대 문자 수를 정의할 수 있습니다.

>[!CAUTION]
>
>고려해야 할 최대 문자 수를 늘리면 플랫폼의 웹 추적 성능에 영향을 줄 수 있습니다.

이렇게 하려면 serverConf. **xml** 파일에서 **`<trackinglogd>`** 요소의 webTrackingParamSize **속성을** 수정합니다. 이 파일은 Adobe Campaign 설치 디렉토리의 **conf** 하위 디렉토리에 저장됩니다.

**예**:

기본값은 64자입니다. 이 값을 사용하면 **금액** 및 **아티클** (&quot;amount=xxxxxxxx&amp;article=xxxxxxxx&quot;) 표준 매개 변수를 고려할 수 있습니다.

위의 확장 스키마 예제에 표시된 매개 변수(이름 + 값 크기)를 모두 고려하여 구성을 수정하여 100자를 고려합니다(&quot;amount=xxxxxxxx&amp;article=xxxxxxxxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

구성이 수정되면 다음을 수행해야 합니다.

* 리디렉션 모듈(Apache, IIS 등)을 호스팅하는 웹 서버를 중지합니다.
* Adobe Campaign 서버를 중지합니다.Windows의 **net stop nlserver6** , **/etc/init.d/nlserver6 stop** in Linux,
* Linux에서 ipcrm **명령을 사용하여 공유 메모리** 세그먼트를 삭제합니다.
* Adobe Campaign 서버를 다시 시작합니다.Windows의 **net start nlserver6** , **/etc/init.d/nlserver6** , Linux에서 시작
* 웹 서버를 다시 시작합니다.

**예**:Linux에서 구성을 고려합니다.

```
adobe@selma:~$ /etc/init.d/nlserver6 stop
adobe@selma:~$ /etc/init.d/apache stop
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
adobe@selma:~$ /etc/init.d/nlserver6 start
adobe@selma:~$ /etc/init.d/apache start
```

>[!NOTE]
>
>Linux의 경우 webTrackingParamSize **또는** maxSharedLogs **매개 변수의 크기를** 늘리려면 공유 메모리(SHM)의 크기를 늘려야 할 수 있습니다.

