---
product: campaign
title: 최신 릴리스
description: 최신 Campaign Classic v7 릴리스 정보
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: e4dfdd32c07753ee9e202ab4e4bf815485e47d8b
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 17%

---

# 최신 릴리스{#latest-release}

![](../../assets/v7-only.svg)

이 페이지에는 다음과 같은 새로운 기능, 개선 사항 및 수정 사항이 나와 있습니다 **최신 Campaign Classic v7 릴리스**. 모든 새 빌드는 색상으로 구체화된 상태를 제공합니다. 에서 Campaign Classic v7 빌드 상태에 대해 자세히 알아보십시오 [이 페이지](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) 릴리스 7.2.1 - 빌드 9346 {#release-7-2-1}

_2022년 1월 10일_

**보안 개선**

FDA 계정에 몇 가지 보안 기능이 개선되었습니다.

* 이제 ODBC 드라이버는 Adobe Campaign 타사 과 함께 직접 설치됩니다. 이러한 드라이버를 설치하는 데 더 이상 수동 단계가 필요하지 않습니다.
* 이제 FDA 외부 계정을 구성할 때 향상된 인증 보안을 위해 키 쌍 인증을 사용하여 Snowflake 계정에 로그인할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-snowflake.md)
* 이제 FDA 외부 계정을 구성할 때 시스템에서 할당한 관리 ID를 사용하여 Azure synapse Analytics 계정에 로그인할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-synapse.md#azure-external)


**개선 사항**

* Microsoft Dynamics CRM 365 커넥터

   Microsoft Dynamics Connector 웹 API에 대한 중요 수정 사항이 적용되었습니다.

   * 워크플로우에 의해 트리거된 가져오기 중에 문자열 유형 필드의 null 값이 빈 값 대신 Null로 저장되는 문제가 해결되었습니다.
   * 웹 API 호출을 사용하여 데이터를 가져오거나 내보내는 데 다음 오류가 발생하는 문제를 수정했습니다. &quot;잘못된 URI: URI 체계가 너무 깁니다.&quot;
   * Microsoft Dynamics 365에서 조회 필드가 포함된 데이터를 가져올 때 발생하는 다양한 문제를 해결했습니다.

* Google BigQuery FDA 커넥터

   * 이제 호스팅된 배포에 Google BigQuery FDA Connector를 사용할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-google-big-query.md)
   * Google BigQuery FDA 커넥터용 프록시 서버에 연결할 수 있도록 지원이 추가되었습니다. 필요한 프록시 옵션은 외부 계정 구성의 옵션 필드를 통해 설정할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-google-big-query.md#google-external)

**기타 변경 사항**

* 사용 중단 이후 Microsoft CRM, Salesforce, Oracle CRM On Demand 작업 활동이 인터페이스에서 제거되었습니다. Adobe Campaign과 CRM 시스템 간의 데이터 동기화를 구성하려면 CRM 커넥터 활동을 사용할 수 있습니다. [자세히 표시](../../workflow/using/crm-connector.md)
* 다음 **[!UICONTROL Encrypted identifier]** 필드가 방문자 스키마(nms:visitor)에 추가되었습니다. 이 필드는 계산되며 웹 애플리케이션에 사용할 수 있습니다. 이 기능은 중간 소싱 인스턴스에서 라인 채널이 구성된 경우에 적용됩니다.
* 이제 CRM 데이터 소스를 **데이터 소스 변경** 활동.
* 에 새로운 옵션이 추가되었습니다 **오류 관리** 워크플로우 활동 속성: 다음 **오류 시 중단** 옵션이 자동으로 워크플로우를 중지합니다. 나중에 다시 시작할 수 없습니다(NEO-29661). [자세히 표시](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* 이제 전용 시퀀스를 사용하여 수신자의 통계 그룹을 만드는 데 사용되는 nmsGroup 테이블의 기본 키를 생성합니다. 이전에는 xtknownId 시퀀스가 사용되었습니다. (NEO-30832)
* CRM 커넥터 활동을 사용한 일괄 업데이트 작업에 대한 지원을 추가했습니다.

**패치**

* 게재를 만들 때 Marketing Cloud ID에서 오류가 발생하던 문제를 수정했습니다. **이미지** 의 탭 **추적 및 이미지** 창을 엽니다. 이 문제는 자동 프록시 구성을 사용할 때 발생했습니다. (NEO-33260)
* 동기 모드로 Debian 10 서버(HTTPS)에 파일을 업로드할 수 없는 문제를 해결했습니다.
* 게재 통계 테이블(`nmsDeliveryLogStats`)에서 관련 게재가 삭제된 후 데이터베이스 정리 중에 중간 소싱 인스턴스에서 제거됩니다. (NEO-31034)
* 토큰 기반 인증을 사용하는 동안 iOS에서 모바일 앱 알림을 전송할 수 없는 문제를 해결했습니다(NEO-38640).
* 보고서를 만들고 구성하려고 할 때 스크립트 오류 메시지가 표시되는 문제를 해결했습니다(NEO-38393).
* 동시에 많은 양의 게재 표시기가 업데이트되므로 추적 워크플로우가 Oracle 시 실패하는 문제를 해결했습니다(NEO-39653).
* 제어 유형화를 실행하는 동안 오류가 발생하여 게재를 보낼 수 없는 문제를 해결했습니다(NEO-39833).
* 온라인 설문 조사 응답의 HTML 페이지에 특수 문자가 올바르게 표시되지 않는 랜딩 페이지의 문제를 수정했습니다(NEO-39438).
* 탐색기 탭에서 폴더를 마우스 오른쪽 단추로 클릭하면 Campaign Classic 콘솔이 작동하지 않는 문제가 수정되었습니다(NEO-38884).
* 웹 분석 구성이 누락된 새 게재에서 웹 분석 계정에 연결된 이전에 만든 게재 템플릿을 사용할 때 발생하는 오류를 수정했습니다. (NEO-28666)
* 워크플로우에 첨부된 모바일 게재를 미리 볼 수 없는 문제를 해결했습니다.
* 링크 추적에 대한 URL 서명 메커니즘이 활성화되어 있을 때 개인화된 추적 URL이 리디렉션되지 않는 오류를 수정했습니다.
* 인덱스 관리 문제로 인해 업그레이드 후 오류가 발생할 수 있는 문제를 해결했습니다.
* 의 Microsoft Dynamics CRM에서 조회 필드 데이터 유형을 사용할 때 발생하는 오류를 수정했습니다 **가져오기** 또는 **내보내기** 워크플로우 활동.
* 프록시 구성 문제로 인해 콘솔에 로그인하지 못하는 문제를 해결했습니다. (NEO-38388)
* **폴더 제거** 기능이 제대로 작동하지 못하게 하는 회귀 문제를 해결했습니다. (NEO-37459)
* 참조된 xml에 큰 따옴표가 포함된 경우 Microsoft Dynamics CRM 계정에 xml 데이터 필드를 사용할 때 잘못된 요청 오류가 발생하는 문제를 해결했습니다.
* 네트워크 시간 초과 문제가 네트워크 오류가 아닌 스크립트 중단 문제로 잘못 기록되는 문제를 해결했습니다. 이 문제는 JavaScript 활동에 포함된 HTTP 요청의 경우에 발생했습니다. (NEO-38079)
* Amazon Redshift HoursDiff 및 MinutesDiff 함수를 실행할 때 시간 구성 요소를 추출하려 하는 중 잘못된 결과를 반환하는 문제를 해결했습니다.(NEO-31673)
* Adobe Analytics 도구에서 **핫 클릭** 빌드 9182 이후 게재 로드 보고서. (NEO-28900)
* URL의 및 기호를 문자 엔티티 참조( )로 대체한 오류가 수정되었습니다`&amp;`)를 사용하면 사용자가 QR 코드에 연결된 URL에 액세스할 수 없습니다. (NEO-28621)
* 사용자가 새 캠페인 워크플로우와 웹 분석 계정에 연결된 게재 활동을 만들 때마다 새 외부 계정을 만드는 문제를 수정했습니다. 이 문제는 webAnalyticsAccount 게재 개체에서 ID가 누락되어 발생했습니다. (NEO-39691)
* 목록의 신원이 데이터베이스에서 음수 ID로 지정되어 있는 경우 **목록 읽기** 워크플로우가 작동하지 않는 문제를 해결했습니다. (NEO-39607)
* 이 **중간 소싱(게재 로그)** 워크플로우가 실패합니다. (NEO-39662)
* 워크플로우에 첨부된 이메일 게재를 미리 볼 수 없는 문제를 수정했습니다. (NEO-37840)
* 데이터베이스 정리 워크플로우에서 목록 값이 포함된 유효한 테이블을 삭제할 수 있는 문제를 해결했습니다. (NEO-34911)
* 마케팅 인스턴스에서 과금 워크플로우가 충돌할 수 있는 문제를 해결했습니다.
