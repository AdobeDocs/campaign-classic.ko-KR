---
solution: Campaign Classic
product: campaign
title: 모든 방문 수집
description: 모든 방문 수집
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---


# 모든 방문 수집{#collecting-all-visits}

Adobe Campaign에서 제공하는 웹 추적 모듈을 사용하면 메시지 클릭 후 사이트 추적 컨텍스트에서 수신자가 수행한 사이트의 특정 페이지에 대한 방문을 수집할 수 있습니다.

하지만 플랫폼을 구성하면 플랫폼에 알려진 사용자에 의해 웹 추적 태그가 있는 페이지의 모든 방문을 수집할 수 있습니다.

플랫폼에 알려진 사용자는 이미 전달의 대상이 되어 있고 받은 메시지를 최소한 한 번 클릭한 수신자입니다. 이 수신자를 식별하는 데 영구 쿠키가 사용됩니다.

>[!IMPORTANT]
>
>Adobe Campaign 플랫폼은 메시지 클릭 후 사이트를 방문하는 컨텍스트를 넘어 웹 사이트 추적 도구로 사용되도록 되어 있지 않습니다. 이 옵션을 활성화하면 서버를 호스팅하는 시스템에서 리소스를 매우 많이 사용할 수 있습니다(리디렉션, 응용 프로그램 및 데이터베이스). 하드웨어 아키텍처가 이 로드를 지원할 수 있도록 하고 홈 페이지와 같이 가장 자주 방문하는 페이지에 웹 추적 태그를 삽입하지 않도록 하는 것이 좋습니다.

## 서버 구성 {#server-configuration}

서버는 **serverConf.xml** 파일의 특정 요소를 오버로드하여 구성됩니다. 이러한 파일은 Adobe Campaign 설치 디렉토리의 **conf** 하위 디렉토리에 저장됩니다.

### 리디렉션 서버 {#redirection-server}

리디렉션 서버의 경우 **리디렉션** 요소의 trackWebVisitors **특성을** true로 **설정합니다**.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 기본 일치 캠페인 구성 {#configuring-a-default-matching-campaign}

클라이언트 콘솔을 통해 추적 정보를 보려면 다음을 수행해야 합니다.

* 더미 **배달** 만들기(배달 매핑이 대상 스키마의 매핑과 동일해야 함),
* NmsTracking_WebTrackingDelivery **옵션에서 이 게재의** 내부 이름을 **** 입력합니다.

이메일의 클릭 바로 다음에 오지 않는 모든 사이트 추적 정보는 생성된 더미 배달에서 볼 수 있습니다.
