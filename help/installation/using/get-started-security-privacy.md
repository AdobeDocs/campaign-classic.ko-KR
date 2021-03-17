---
solution: Campaign Classic
product: campaign
title: 보안 및 개인 정보 시작하기
description: 보안 및 개인 정보를 확인할 수 있는 주요 요소에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 922603492d2c98d751683d3aa481e9ab19bca70c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---


# 보안 및 개인 정보 보호 시작하기 {#get-started-security-privacy}

이 섹션에서는 보안 및 개인 정보를 확인할 수 있는 주요 요소를 소개합니다. 일부 구성은 온-프레미스 고객만 수행할 수 있습니다.

## 개인 정보

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

개인 정보 구성 및 강화는 보안 최적화의 핵심 요소입니다. 다음은 개인 정보에 대한 몇 가지 우수 사례입니다.

* Protect HTTP 대신 HTTPS를 사용하여 고객 PII 사용
* PII 보기 제한을 사용하여 개인 정보를 보호하고 데이터가 오용되지 않도록 합니다.
* 암호화된 암호가 제한되어 있는지 확인합니다.
* Protect은 미러 페이지, 웹 애플리케이션 등과 같은 개인 정보를 포함할 수 있는 페이지를 말합니다.

[자세한 내용](../../installation/using/privacy.md)

## 액세스 관리

<img src="assets/do-not-localize/icon_access.svg" width="60px">

액세스 관리는 보안 강화를 위한 중요한 요소입니다. 다음은 몇 가지 주요 우수 사례입니다.

* 충분한 보안 그룹 만들기
* 각 연산자에 적절한 액세스 권한이 있는지 확인합니다.
* 관리 연산자 사용을 피하고 관리 그룹에 너무 많은 연산자가 없도록 하십시오.

[자세한 내용](../../installation/using/access-management.md)

## 스크립팅 및 코딩 지침

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Adobe Campaign(워크플로우, Javascript, JSSP 등)에서 개발하는 경우 항상 다음 지침을 따르십시오.

* **스크립팅**:SQL 문을 사용하지 말고 문자열 연결 대신 매개 변수가 있는 함수를 사용하십시오. 허용 목록에 사용할 SQL 함수를 추가하면 SQL 주입을 방지할 수 있습니다.

* **데이터 모델의 보안**:명명된 권한을 사용하여 연산자 작업을 제한하고 시스템 필터를 추가합니다(sysFilter).

* **웹 애플리케이션에 캡처를 추가합니다**.공개 랜딩 페이지 및 구독 페이지에서 캡처를 추가하는 방법을 알아봅니다.

[자세한 내용](../../installation/using/scripting-coding-guidelines.md)

## 네트워크, 데이터베이스 및 SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

온-프레미스 유형의 아키텍처를 배포할 때 확인해야 할 중요한 것은 네트워킹 구성입니다.

또한 데이터베이스 엔진 보안을 따라야 합니다.

[자세한 내용](../../installation/using/network-database.md)

## 서버 구성

<img src="assets/do-not-localize/icon_server.svg" width="60px">

모든 서버에서 구성을 수행해야 합니다. 구성 파일은 **serverConf.xml** 및 **`config-<instance>.xml`** 유형의 파일입니다. 다음은 확인해야 할 주요 요소입니다.

* **보안 영역**:프록시 클라이언트의 IP 주소를 직접 고려할 수 있도록 보안 영역을 구성합니다.

* **파일 업로드 보호**:새 uploadAllowList 특성을 사용하여 Adobe Campaign 서버에 업로드할 수 있는 파일 유형을 제한합니다. 서버 구성 파일에서 사용할 수 있습니다.

* **릴레이**:사용하지 않은 모듈/응용 프로그램에 대한 릴레이 규칙을 비활성화하여 릴레이 구성을 세밀하게 조정합니다.

* **나가는 연결** 보호 및  **명령 제한** (서버측)

* 추가 HTTP 헤더를 추가하고 checkIPConsistent, enableTLS, sessionTimeOutSec 등을 활성화할 수도 있습니다. 자세한 내용은 [캠페인 서버 구성 설명서](../../installation/using/configuring-campaign-server.md) 및 [서버 구성 파일 설명](../../installation/using/the-server-configuration-file.md)을 참조하십시오.

[자세한 내용](../../installation/using/server-configuration.md)

## 웹 서버 구성

<img src="assets/do-not-localize/icon_web.svg" width="60px">

웹 서버(Apache/IIS)를 구성할 때는 몇 가지 우수 사례를 수행해야 합니다.

* 이전 SSL 버전 및 암호 비활성화
* TRACE 메서드 제거
* 배너 제거
* 쿼리 크기를 제한하여 중요한 파일이 업로드되지 않도록 합니다.

[자세한 내용](../../installation/using/web-server-configuration.md)
