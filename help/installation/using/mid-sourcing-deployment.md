---
product: campaign
title: 중간 소싱 배포
description: 중간 소싱 배포
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 2%

---

# 중간 소싱 배포{#mid-sourcing-deployment}



이 구성은 호스팅(ASP) 구성과 내부 구성 간의 최적 중간 솔루션입니다. 외향 실행 구성 요소는 Adobe Campaign에서 호스팅되는 &quot;중간 소싱&quot; 서버에서 수행됩니다.

>[!NOTE]
>
>이러한 유형의 배포를 설정하려면 적절한 옵션을 가져와야 합니다. 사용권 계약을 확인하십시오.

서버와 프로세스 간의 일반 통신은 다음 스키마에 따라 수행됩니다.

![](assets/s_ncs_install_midsourcing.png)

* 인스턴스에서 실행 및 반송 관리 모듈을 사용할 수 없습니다.
* 이 애플리케이션은 SOAP 호출(HTTP 또는 HTTPS를 통해)을 사용하여 구동되는 원격 &quot;mid 소스&quot; 서버에서 메시지 실행을 수행하도록 구성됩니다.

## 기능 {#features}

### 장점 {#advantages}

* 간소화된 서버 구성: 고객이 외부 환경 모듈(mta 및 inMail)을 구성할 필요는 없습니다.
* 대역폭 사용 제한: 중간 소싱 서버에서 실행되므로 개인화 데이터를 중간 소싱 서버로 전송하는 데 충분한 대역폭만 필요합니다.
* 고가용성은 더 이상 내부 문제가 아닙니다. 중간 소싱 서버(리디렉션, 미러 페이지, 실행 서버 등)로 문제가 이동합니다.
* 데이터베이스가 회사를 벗어나지 않습니다. 메시지를 취합하는 데 필요한 데이터만 중간 소싱 서버로 전송됩니다(이 경우 HTTPS를 사용할 수 있음).
* 이러한 유형의 배포는 대량 아키텍처(데이터베이스의 많은 수신자)를 위한 솔루션이며 상당한 게재 처리량을 제공합니다.

### 단점 {#disadvantages}

* 중간 소싱 서버에서 정보를 다시 가져오는 데 걸리는 시간으로 인해 메시지 실행 정보 보기 및 보고 기능이 약간 지연됩니다.
* 설문 조사 및 웹 양식은 클라이언트 플랫폼에 유지됩니다.

### 추천 장비 {#recommended-equipment}

* 애플리케이션 서버: 2Ghz 쿼드 코어 CPU, 4GB RAM, 소프트웨어 RAID 1 80GB SATA 하드 드라이브
* 데이터베이스 서버: 3GHz bi-quad 코어 CPU, 최소 4GB RAM, 하드웨어 RAID 10 15000RPM SAS 하드 드라이브, 데이터베이스의 크기 및 예상 성능에 따른 숫자

>[!NOTE]
>
>리디렉션 및 중간 소싱은 별도의 요소이지만 일반적으로 추적 서버는 중간 소싱 서버와 공유됩니다.

## 설치 및 구성 단계 {#installation-and-configuration-steps-}

### 전제 조건 {#prerequisites}

* 애플리케이션 서버의 JDK입니다.
* 응용 프로그램 서버의 데이터베이스 서버에 액세스합니다.
* 중간 소싱 서버로 HTTP(80) 또는 HTTPS(443) 포트를 열도록 방화벽이 구성되어 있습니다.

### 설치 및 구성(중간 소싱 배포) {#installing-and-configuring--mid-sourcing-deployment-}

을(를) 참조하십시오. [중간 소싱 서버](../../installation/using/mid-sourcing-server.md).
