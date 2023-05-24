---
product: campaign
title: 일반 아키텍처
description: 일반 아키텍처
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---

# 일반 아키텍처{#general-architecture}



## 최소 아키텍처 {#minimum-architecture}

최소 구성에서 Adobe Campaign은 다음과 같이 작동합니다.

* Adobe Campaign 애플리케이션 서버,
* 데이터베이스.

   ![](assets/formation_exploitation.png)

이 다이어그램은 최소 아키텍처의 컨텍스트와 관련된 유일한 트래픽은

1. 인터넷을 통한 Adobe Campaign 서버로의 HTTP 프로토콜 트래픽,
1. 인터넷을 통해 Adobe Campaign 서버와 주고받는 SMTP 프로토콜 트래픽.

## 분산 아키텍처 {#distributed-architecture}

Adobe Campaign은 여러 시스템에 걸쳐 분류할 수 있는 여러 모듈로 구성됩니다. 이 운영 모드에는 다음과 같은 몇 가지 이점이 있습니다.

* 로드 밸런싱,
* 모듈 이중화 설정,
* 여러 서비스 제공업체(제공된 서비스의 세분화)에 대해 분류된 아키텍처 구축.

![](assets/architecturerepartie.png)

여러 시스템에 걸쳐 모듈을 배포하면 사용 유연성이 뛰어나고 적응성이 향상됩니다.

>[!NOTE]
>
>다양한 아키텍처에 대한 자세한 내용은 [이 섹션](../../installation/using/general-architecture.md).

## 열린 포트 목록 {#list-of-open-ports}

| 포트 번호 | 관련 Adobe Campaign 모듈 또는 애플리케이션 | 구성 가능 |
|---|---|---|
| 443/tcp 또는 80/tcp | 웹 서버(Apache/IIS) | 예 |
| 6666/udp(로컬) | Adobe Campaign: Syslogd | 예 |
| 8005/tcp(로컬) | Adobe Campaign: 웹 모듈 | 예 |
| 8080/tcp | Adobe Campaign: 웹 모듈(tomcat) | 예 |
| 7777 | 통계 서버(통계 서버) | 예 |
