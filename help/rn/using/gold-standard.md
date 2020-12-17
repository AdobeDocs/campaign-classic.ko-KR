---
solution: Campaign Classic
product: campaign
title: Gold Standard 릴리스
description: Campaign Classic Gold Standard 릴리스 정보
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 494be84478f652dd5e1473dd98272056514f31c8
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 90%

---


# Gold Standard 릴리스{#gold-standard}

Gold Standard는 Campaign Classic 장기 지원 릴리스입니다. Gold Standard 사용자는 아무 활동을 하지 않고도 최신 안정된 버전의 Gold Standard 업그레이드를 자동으로 활용할 수 있습니다. 온-프레미스 및 하이브리드 고객은 Gold Standard 릴리스를 활용할 수 있습니다.

이전 빌드에서 마이그레이션하는 경우 먼저 이 버전으로 업그레이드하는 것이 좋습니다.

이 페이지에는 Gold Standard 릴리스가 나열됩니다.

Campaign Gold Standard 프로그램에 대한 자세한 내용은 [이 문서를](https://helpx.adobe.com/kr/campaign/kb/gold-standard.html) 참조하십시오.

## ![](assets/do-not-localize/limited_2.png) Gold Standard 11 릴리스{#gs-11}

_2020년 12월 15일_

>[!CAUTION]
>
>이 릴리스는 새 연결 프로토콜과 함께 제공됩니다.2020년 3월 21일 이후 Campaign 서버 및 클라이언트 콘솔에서 Campaign에 연결할 수 있으려면 업그레이드가 필요합니다.

빌드 9032@2a2a028에는 다음과 같은 개선 사항 및 수정 사항이 포함되어 있습니다.

* 새 IMS 인증 메커니즘을 따르도록 연결 프로토콜이 업데이트되었습니다.

* 기존 oAUTH 인증 설정을 기반으로 파이프라인에 액세스하는 트리거 통합 인증이 변경되었으며 Adobe I/O로 이동되었습니다. [자세히 알아보기](../../integrations/using/configuring-adobe-io.md)

* iOS APNs 레거시 이진 프로토콜에 대한 지원이 종료된 후 업그레이드 후 이 프로토콜을 사용하는 모든 인스턴스가 HTTP/2 프로토콜로 업데이트됩니다.

* SSRF(Server Side Request 위조) 문제에 대한 보호를 강화하려는 보안 문제가 해결되었습니다. (NEO-27777)

## ![](assets/do-not-localize/green_2.png) Gold Standard 10 릴리스{#gs-10}

_2020년 7월 7일_

빌드 9032@efd8a94에는 다음 수정 사항이 포함되어 있습니다.

서명 기능이 비활성화되었을 때 추적을 수행할 수 없는 문제를 해결했습니다. (NEO-26411)

>[!CAUTION]
>
>이 릴리스에서 사용할 수 있는 클라이언트 콘솔을 업그레이드하는 것이 좋습니다. [이 페이지](../../installation/using/installing-the-client-console.md)를 참조하십시오

## ![](assets/do-not-localize/red_2.png) Gold Standard 9 릴리스{#gs-9}

_2020년 6월 22일_

빌드 9032@800be2e에는 다음 수정 사항이 포함되어 있습니다.

* iOS HTTP2 커넥터가 개선되었습니다(타사 업데이트 및 오류 관리). (NEO-25904, NEO-25903, NEO-25799)

다음 수정 사항은 추적 링크 보안 메커니즘과 관련되어 있습니다(자세한 내용은 [보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/kr/campaign/kb/acc-security.html#signature-mechanism)에 있음).

* &quot;알림 클릭&quot; 추적이 작동하지 않는 문제를 해결했습니다(iOS 및 Android 푸시 알림). (NEO-25965)
* 특정 이전 버전의 Outlook을 사용할 때 추적 URL을 열거나 클릭하지 못하는 문제를 해결했습니다.  (NEO-25688)
* 개인화 매개 변수의 조각을 사용하여 URL을 추적할 수 없는 문제(파운드 기호가 있는 앵커 태그)를 해결했습니다. (NEO-25774)
* 피싱 방지 서비스 문제를 해결했습니다. (NEO-25283)
* 특정 사용자 지정 추적 공식을 사용할 때의 추적 문제를 해결했습니다. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard 8 릴리스{#gs-8}

_2020년 4월 29일_

빌드 9032@3a9dc9c에는 다음 수정 사항이 포함되어 있습니다.

* 전자 메일의 링크 추적 보안이 개선되었습니다. 모든 고객에 대해 기본적으로 활성화됩니다. 고객 지원 센터에 연락하여 활성화할 수 있는 향상된 추가 보안 기능을 사용할 수 있습니다. 호스팅되지 않은 고객이 이 기능을 사용하도록 설정하는 기능 및 단계에 대한 자세한 내용은 [보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)에서 확인할 수 있습니다.

>[!CAUTION]
>
>추적 링크를 사용한 푸시 알림 또는 앵커 태그를 사용한 게재 관련 문제가 발생하는 경우 링크 추적을 위해 새 서명 메커니즘을 비활성화하는 것이 좋습니다. 프로시저는 [이 페이지](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)에 자세히 설명되어 있습니다

* 라인 게재에서 이미지가 표시되지 않는 문제를 해결했습니다. (NEO-23207)
* SFTP 키 기반 인증이 Debian 9에서 작동하지 않는 **파일 전송** 활동 문제를 해결했습니다. (NEO-23183)
* 높은 빈도로 전송할 때 푸시 알림에 영향을 줄 수 있는 문제를 해결했습니다. (NEO-20516)
* 웹 서버 충돌을 야기할 수 있는 오퍼 응답 관리 문제를 해결했습니다. (NEO-19482)
* 보고서를 내보낼 수 없는 LibreOffice 관리의 오류를 해결했습니다. (NEO-20982)
* 설문 조사 활동을 사용하여 다양한 워크플로우를 업그레이드할 때 오류가 발생하는 문제를 해결했습니다.
* .odt 파일을 사용하여 전자 메일 미리 보기에 오류가 발생하지 않도록 LibreOffice 관리를 개선했습니다.
* 웹 서비스에서 지연을 방지하기 위해 Apache 연결 관리를 개선했습니다.
* **정보** 메뉴에서 버전 태그(7자리)의 표시를 개선했습니다.
* 오퍼가 게시되지 않도록 하는 목록 관리의 회귀 문제를 해결했습니다.
* 정리 워크플로우가 충돌하는 회귀 문제를 해결했습니다.
* 정리 워크플로우 로그에서 사소한 회귀 문제를 해결했습니다.

## ![](assets/do-not-localize/orange_2.png) Gold Standard 6 릴리스{#gs-6}

_2020년 3월 9일_

빌드 9032@19f73c5에는 다음 수정 사항이 포함되어 있습니다.

* SSL을 통해 FTP를 사용하는 외부 계정 문제를 해결했습니다. (NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 5 릴리스{#gs-5}

_2019년 12월 17일_

빌드 9032@d6b8062에는 다음 수정 사항이 포함되어 있습니다.

* 모바일(SMS, MMS), 푸시(iOS, Android) 및 소셜 네트워크(Facebook, Twitter)와 같은 통신 채널의 추적 문제를 해결했습니다. (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 4 릴리스{#gs-4}

_2019년 12월 11일_

빌드 9032@bc4a935에는 다음 수정 사항이 포함되어 있습니다.

* MSSQL 데이터베이스를 사용하여 메시지를 전송할 때 성능 문제를 해결했습니다. (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 3 릴리스{#gs-3}

_2019년 11월 20일_

빌드 9032@3468c7b에는 다음 수정 사항이 포함되어 있습니다.

* IMS 인증을 통한 로그인 문제를 해결했습니다. (NEO-17312)
* 다중 게재에 대한 누적 보고서를 표시할 때 발생하는 문제를 해결했습니다. (NEO-18165)
* 웹 서버 충돌을 차단하거나 야기할 수 있는 문제를 해결했습니다.

## ![](assets/do-not-localize/red_2.png) Gold Standard 2 릴리스{#gs-2}

_2019년 9월 19일_

빌드 9032@cee805c에는 다음 수정 사항이 포함되어 있습니다.

* Salesforce용 CRM 커넥터를 사용하는 경우 발생하는 문제를 해결했습니다. (NEO-17712)
* 트랜잭션 메시지를 보낼 때 성능 문제가 발생할 수 있는 인덱스 문제를 해결했습니다.

## ![](assets/do-not-localize/red_2.png) 릴리스 19.1.4 - 빌드 9032{#release-19-1-4-build-9032}

_2019년 8월 13일_

초기 19.1.4 빌드에는 다음 수정 사항이 포함되어 있습니다.

* 마법사 구성 중 원치 않는 오류 메시지를 생성하는 스케줄러 활동 문제를 해결했습니다. NEO-11662에서 업데이트를 되돌립니다. (NEO-17097)
* 테스트 활동이 두 번 실행될 때 워크플로우를 중지할 수 있는 NEO-12727에 의해 발생하는 회귀 문제를 해결했습니다. (NEO-16835)
* API 호출에서 유효하지 않거나 만료된 세션 토큰이 사용된 경우 잘못된 HTTP 코드(HTTP 403 대신 HTTP 200 OK)가 반환되는 문제를 해결했습니다. (NEO-16826)
* DKIM 키가 더 이상 전자 메일에 포함되지 않아 게재 문제가 발생하는 문제를 해결했습니다. (NEO-16804)
* 워크플로우 예약과 관련된 다양한 문제를 해결했습니다. 워크플로우는 스케줄러 구성을 고려하지 않고 하루에 한 번 실행되도록 예약되었습니다. (NEO-16619, NEO-16426)
