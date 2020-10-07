---
title: 일반 아키텍처
seo-title: 일반 아키텍처
description: 일반 아키텍처
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 4%

---


# 일반 아키텍처{#general-architecture}

## 최소 아키텍처 {#minimum-architecture}

Adobe Campaign은 최소 구성으로 다음을 수행합니다.

* adobe campaign 애플리케이션 서버,
* 데이터베이스를 참조하십시오.

   ![](assets/formation_exploitation.png)

이 다이어그램은 최소 아키텍처 컨텍스트와 관련된 유일한 트래픽이

1. 인터넷을 통해 Adobe Campaign 서버에 대한 HTTP 프로토콜 트래픽
1. 인터넷을 통해 Adobe Campaign 서버로부터의 SMTP 프로토콜 트래픽

## 분산 아키텍처 {#distributed-architecture}

Adobe Campaign은 여러 대의 기계로 분해할 수 있는 여러 모듈로 구성되어 있다. 이 운영 모드는 다음과 같은 여러 이점을 제공합니다.

* 부하 균형 조정,
* 모듈 이중화 설정,
* 여러 서비스 제공업체를 통해 세분화된 아키텍처 구축(제공된 서비스의 세분화)

![](assets/architecturerepartie.png)

여러 시스템에 모듈을 배포하면 뛰어난 유연성과 향상된 적응성을 제공합니다.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## 열려 있는 포트 목록 {#list-of-open-ports}

| 포트 번호 | 관련 Adobe Campaign 모듈 또는 애플리케이션 | 구성 가능 |
|---|---|---|
| 443/tcp 또는 80/tcp | 웹 서버(Apache/IIS) | 예 |
| 6666/udp(로컬) | Adobe Campaign:Syslogd | 예 |
| 8005/tcp(로컬) | Adobe Campaign:웹 모듈 | 예 |
| 8080/tcp | Adobe Campaign:웹 모듈(tomcat) | 예 |
| 7777 | 통계 서버(통계 서버) | 예 |

