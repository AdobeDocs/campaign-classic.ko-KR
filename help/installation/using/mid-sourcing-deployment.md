---
title: 중간 소싱 배포
seo-title: 중간 소싱 배포
description: 중간 소싱 배포
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# 중간 소싱 배포{#mid-sourcing-deployment}

이 구성은 호스팅된(ASP) 구성과 내부화 간의 최적의 중간 솔루션입니다. 외향적 실행 구성 요소는 Adobe Campaign에서 호스팅되는 &quot;미드소싱&quot; 서버에서 수행됩니다.

>[!NOTE]
>
>이러한 유형의 배포를 설정하려면 적절한 옵션을 확보해야 합니다. 사용권 계약을 확인하십시오.

서버와 프로세스 간의 일반 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_ncs_install_midsourcing.png)

* 인스턴스에서 실행 및 바운스 관리 모듈을 사용할 수 없습니다.
* 응용 프로그램은 SOAP 호출(HTTP 또는 HTTPS를 통해)을 사용하여 실행되는 원격 &quot;mid-sources&quot; 서버에서 메시지 실행을 수행하도록 구성됩니다.

## 기능 {#features}

### 장점 {#advantages}

* 간소화된 서버 구성:고객이 외부 모듈(mta 및 inMail)을 구성할 필요는 없습니다.
* 제한된 대역폭 사용:중간 소싱 서버에서 실행되므로 개인화 데이터를 중간 소싱 서버로 전송하려면 충분한 대역폭만 필요합니다.
* 고가용성은 더 이상 내부 문제가 아닙니다.문제는 중간 소싱 서버(리디렉션, 미러 페이지, 실행 서버 등)로 이동합니다.
* 데이터베이스가 회사를 떠나지 않습니다.메시지를 조합하는 데 필요한 데이터만 중간 소싱 서버로 전송됩니다. 이 경우 HTTPS를 사용할 수 있습니다.
* 이러한 유형의 배포는 상당한 전달 처리량을 갖는 대용량 아키텍처(데이터베이스의 많은 수신자)를 위한 솔루션이 될 수 있습니다.

### 단점 {#disadvantages}

* mid-sourcing 서버에서 정보를 다시 가져오는 데 걸리는 시간 때문에 메시지 실행 정보 보기 및 보고 기능에 대한 약간의 지연.
* 설문 조사 및 웹 양식은 클라이언트 플랫폼에 남아 있습니다.

### 권장 장비 {#recommended-equipment}

* 응용 프로그램 서버:2GHZ 쿼드 코어 CPU, 4GB RAM, 소프트웨어 RAID 1 80GB SATA 하드 드라이브
* 데이터베이스 서버:3GHz bi-쿼드 코어 CPU, 최소 4GB RAM, 하드웨어 RAID 10 15000RPM SAS 하드 드라이브, 데이터베이스의 크기와 예상 성능에 따라 다릅니다.

>[!NOTE]
>
>리디렉션과 미드소싱은 별개의 요소이지만 일반적으로 추적 서버는 mid 소싱 서버와 공유됩니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps-}

### 사전 요구 사항 {#prerequisites}

* 응용 프로그램 서버의 JDK입니다.
* 응용 프로그램 서버에서 데이터베이스 서버에 액세스합니다.
* HTTP(80) 또는 HTTPS(443) 포트를 미드소싱 서버로 열도록 방화벽이 구성되었습니다.

### 설치 및 구성(미드소싱 배포) {#installing-and-configuring--mid-sourcing-deployment-}

mid [소싱 서버를](../../installation/using/mid-sourcing-server.md)참조하십시오.
