---
product: campaign
title: 보안 및 개인 정보 보호에 대해 확인할 사항
description: 보안 및 개인 정보에 대한 확인을 위한 주요 요소에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 6%

---

# 보안 및 개인 정보 보호에 대해 확인할 사항{#get-started-security-privacy}

![](../../assets/v7-only.svg)

이 섹션에서는 보안 및 개인 정보에 대한 확인을 위한 주요 요소를 소개합니다. 일부 구성은 온-프레미스 고객만 수행할 수 있습니다.

## 개인 정보 보호

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

개인 정보 구성 및 경화는 보안 최적화의 주요 요소입니다. 다음은 개인 정보에 대해 따라야 할 몇 가지 모범 사례입니다.

* HTTP 대신 HTTPS를 사용하여 고객 PII를 Protect
* PII 보기 제한을 사용하여 개인 정보를 보호하고 데이터가 오용되지 않도록 합니다.
* 암호화된 암호가 제한되어 있는지 확인하십시오.
* Protect 미러 페이지, 웹 애플리케이션 등의 개인 정보를 포함할 수 있는 페이지를 설정합니다.

[자세히 표시](../../installation/using/privacy.md)

## 액세스 관리

<img src="assets/do-not-localize/icon_access.svg" width="60px">

액세스 관리는 보안 강화의 중요한 부분입니다. 다음은 몇 가지 주요 우수 사례입니다.

* 충분한 보안 그룹 만들기
* 각 연산자에 적절한 액세스 권한이 있는지 확인합니다
* 관리 연산자를 사용하지 않도록 하고, 관리 그룹에 너무 많은 운영자가 없도록 하십시오

[자세히 표시](../../installation/using/access-management.md)

## 스크립팅 및 코딩 지침

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Adobe Campaign(워크플로우, Javascript, JSSP 등)에서 개발할 때에는 항상 다음 지침을 따르십시오.

* **스크립팅**: SQL 문을 사용하지 않도록 설정하고, 문자열 연결 대신 매개 변수화된 함수를 사용하고,에 사용할 SQL 함수를 추가하여 SQL 주입을 허용 목록에 추가하다 방지하십시오.

* **데이터 모델 보안**: 명명된 권한을 사용하여 운영자 작업을 제한하고 시스템 필터 추가(sysFilter)

* **웹 애플리케이션에서 캡션 추가**: 공개 랜딩 페이지 및 구독 페이지에서 captchas를 추가하는 방법을 알아봅니다.

[자세히 표시](../../installation/using/scripting-coding-guidelines.md)

## 네트워크, 데이터베이스 및 SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

온-프레미스 유형의 아키텍처를 배포할 때 확인해야 할 중요한 사항은 네트워킹 구성입니다.

또한 데이터베이스 엔진 보안을 따라야 합니다.

[자세히 표시](../../installation/using/network-database.md)

>[!CAUTION]
>
>2021년 7월 14일부터 TLS 1.2 프로토콜을 지원하지 않는 모든 클라이언트 시스템은 모든 Adobe 제품 및 서비스에 대한 액세스를 잃게 됩니다. 이 날짜 이전에 모든 사용자 및 클라이언트 시스템이 TLS 1.2 호환되는지 확인하십시오. [자세히 알아보기](https://helpx.adobe.com/x-productkb/multi/eol-tls-support.html)

## 서버 구성

<img src="assets/do-not-localize/icon_server.svg" width="60px">

모든 서버에서 구성을 수행해야 합니다. 구성 파일은 형식입니다 **serverConf.xml** 및 **`config-<instance>.xml`**. 다음은 확인해야 하는 주요 요소입니다.

* **보안 영역**: 프록시 클라이언트의 IP 주소를 직접 고려할 수 있도록 보안 영역을 구성합니다.

* **파일 업로드 보호**: 새 uploadAllowList 특성을 사용하여 Adobe Campaign 서버에 업로드할 수 있는 파일 유형을 제한합니다. 서버 구성 파일에서 사용할 수 있습니다.

* **릴레이**: 사용되지 않는 모듈/응용 프로그램에 대한 릴레이 규칙을 비활성화하여 릴레이 구성을 미세 조정합니다.

* **발신 연결 보호** 및 **명령 제한** (서버측)

* 또한 추가 HTTP 헤더를 추가하고, checkIPConsistent, enableTLS, sessionTimeOutSec 등을 활성화할 수 있습니다. 자세한 내용은 [Campaign 서버 구성 설명서](../../installation/using/configuring-campaign-server.md) 그리고 [서버 구성 파일 설명](../../installation/using/the-server-configuration-file.md) 추가 정보.

[자세히 표시](../../installation/using/server-configuration.md)

## 웹 서버 구성

<img src="assets/do-not-localize/icon_web.svg" width="60px">

웹 서버(Apache/IIS)를 구성할 때는 다음과 같은 몇 가지 우수 사례를 따라야 합니다.

* 이전 SSL 버전 및 암호 비활성화
* TRACE 메서드 제거
* 배너 제거
* 중요한 파일이 업로드되지 않도록 쿼리 크기를 제한합니다

[자세히 표시](../../installation/using/web-server-configuration.md)
