---
product: campaign
title: 모든 방문 수집
description: 모든 방문 수집
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: cc554d0d-bbab-4f72-b870-5fef5a2fda9d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 3%

---

# 모든 방문 수집{#collecting-all-visits}

![](../../assets/v7-only.svg)

Adobe Campaign에서 제공하는 웹 추적 모듈을 사용하면 메시지의 클릭 후 사이트 추적 컨텍스트에서 수신자가 수행한 사이트의 특정 페이지에 대한 방문을 수집할 수 있습니다.

그러나 플랫폼에 알려진 사용자에 의해 웹 추적 태그가 있는 페이지에 대한 모든 방문을 수집하도록 플랫폼을 구성할 수 있습니다.

플랫폼에 알려진 사용자는 이미 게재의 타겟팅되고 수신한 메시지를 최소 한 번 클릭한 수신자입니다. 영구 쿠키는 이 수신자를 식별하는 데 사용됩니다.

>[!IMPORTANT]
>
>Adobe Campaign 플랫폼은 메시지의 클릭에 따라 사이트를 방문하는 컨텍스트 외에 웹 사이트 추적 도구로 사용되지 않습니다. 이 옵션을 사용하면 서버를 호스팅하는 시스템에서 리소스를 매우 많이 사용할 수 있습니다(리디렉션, 응용 프로그램 및 데이터베이스). 하드웨어 아키텍처가 이 로드를 지원할 수 있는지 확인하고, 홈 페이지와 같이 가장 자주 방문하는 페이지에 웹 추적 태그를 삽입하지 않도록 하는 것이 좋습니다.

## 서버 구성 {#server-configuration}

서버는 **serverConf.xml** 파일의 특정 요소를 오버로드하여 구성됩니다. 이러한 파일은 Adobe Campaign 설치 디렉토리의 **conf** 하위 디렉토리에 저장됩니다.

### 리디렉션 서버 {#redirection-server}

리디렉션 서버의 경우 **redirection** 요소의 **trackWebVisitors** 속성을 **true**&#x200B;로 설정합니다.

```
<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="true"
trackingPassword=""
```

## 기본 일치 캠페인 구성 {#configuring-a-default-matching-campaign}

클라이언트 콘솔을 통해 추적 정보를 보려면 다음을 수행해야 합니다.

* **더미 배달**&#x200B;을(를) 만듭니다(게재 매핑은 대상 스키마의 매핑과 동일해야 함).
* **NmsTracking_WebTrackingDelivery** 옵션에 이 게재의 **내부 이름**&#x200B;을 입력합니다.

이메일에서 클릭이 직접 이어지지 않은 모든 사이트 추적 정보는 생성된 더미 게재에서 볼 수 있습니다.
