---
product: campaign
title: Campaign Classic 2022 릴리스
description: Campaign Classic 2022 릴리스에 대해 자세히 알아보기
feature: Release Notes
role: User
level: Beginner
exl-id: 28490323-41d0-4d61-b309-6892fb826d21
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '2100'
ht-degree: 100%

---

# 2022년 릴리스{#release-2022}

## 릴리스 7.3.1 - 빌드 9352 {#release-7-3-1}

[!BADGE 사용되지 않음]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="사용되지 않음"}

_2022년 7월 1일_

**새로운 기능**

<table> 
<thead>
<tr> 
<th> <strong>시간 구분 알림</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>iOS 15에서 Apple은 알림이 긴급하다고 간주되어 사용자에게 실시간으로 연락해야 할 때 앱 개발자에게 포커스 모드를 무시하도록 제어하는 긴급한 알림 개념을 추가했습니다.</p>
<p>긴급한 알림을 만드는 방법은 <a href="../../delivery/using/create-notifications-ios.md">세부 설명서</a>에서 확인하세요.</p>
</td> 
</tr> 
</tbody> 
</table>

**호환성 업데이트**

* 이제 Adobe Campaign SDK가 Android 12 및 iOS 15에서 푸시 알림을 지원합니다.
* Adobe Campaign이 이제 MySQL 8과 호환됩니다.
* Adobe Campaign은 이제 Windows 11과 호환됩니다.
* Adobe Campaign이 이제 Debian 11과 호환됩니다. 자세한 정보는 이 [기술 노트](../../technotes/using/tech-stack-upgrade.md)를 참조하세요.

[캠페인 호환성 매트릭스](../../rn/using/compatibility-matrix.md#OperatingSystems)를 참조하십시오.

**개선 사항**

* Microsoft Internet Explorer 11의 수명 종료에 따라 클라이언트 콘솔 환경에서 Adobe 서비스(로그인 페이지)용 HTML 렌더링 엔진이 이제 Edge Chromium을 사용합니다. Microsoft Internet Explorer 11은 여전히 클라이언트 콘솔의 대시보드용 HTML 렌더링 엔진입니다.  또한 이제 모든 클라이언트 콘솔 설치(Campaign Classic 7.3 빌드 버전)에 Microsoft Edge Webview 2 런타임을 설치해야 합니다. [자세히 보기](../../installation/using/installing-the-client-console.md)
* 안정성을 최적화하기 위해 Adobe Campaign의 데이터베이스 연결 관리를 개선했습니다.
* 이제 Campaign에서 POP3용 Microsoft Exchange Online OAuth 2.0 인증이 지원됩니다. [자세히 보기](../../installation/using/external-accounts.md#bounce-mails-external-account)
* 외부 데이터에 대해 데이터 보강 워크플로 활동을 사용할 때 발생하는 다양한 문제를 해결했습니다. (NEO-38069)
* SAP Hana FDA 커넥터를 SAP Hana 데이터베이스 최신 버전(2.x)에 사용할 수 있도록 업데이트했습니다.
* Teradata FDA 커넥터를 Teradata 최신 버전(17)에 사용할 수 있도록 업데이트했습니다.
* 20.2에서는 iOS 게재 시 새 게재 및 게재 템플릿에 대한 토큰 기반 인증 지원을 도입했습니다. 7.2에서는 이전에 만든 게재 및 게재 템플릿 최대 10,000개에 토큰 기반 인증 지원을 적용할 수 있도록 업그레이드 후 버전에 패치를 추가했습니다. 7.3에서 해당 패치를 개선하여 지원 적용 수 제한을 없앴습니다.

**패치**

* 이전 빌드에서 사용자가 IMS 로그인 페이지의 크기를 조정할 수 없는 오류를 해결했습니다. (NEO-30085)
* 기존 인스턴스에 콘텐츠 관리자 패키지를 설치할 때 발생하는 오류를 해결했습니다. (NEO-32349)
* **캠페인** 메뉴에 &quot;작업 진행 중&quot; 메시지가 계속 표시되는 문제를 해결했습니다. (NEO-44904)
* Adobe Analytics 사용 시 게재를 저장하지 않고 URL로 이메일을 보내면 URL의 BID(Broadlog ID) 및 CID(캠페인 ID)가 없어지는 문제를 해결했습니다. (NEO-38678)
* 메시지 센터 전용 구성이 있는 인스턴스에서 공개 리소스 폴더에 있는 이미지를 업로드할 때 발생하는 문제를 해결했습니다. 문제 해결 전에는 이 경우 &quot;추적 서버에 이미지를 업로드할 수 없음&quot;이라는 오류 메시지를 표시했습니다. (NEO-38546, NEO-45572)
* 구성 파일이 잘못된 경우 구성을 다시 생성할 때 시스템이 충돌하는 문제를 해결했습니다. (NEO-38752)
* 게재 지표를 올바르게 업데이트하지 못하는 문제를 해결했습니다. (NEO-44827)
* 복잡한 쿼리를 사용할 때 업그레이드 후 오류가 발생하는 문제를 해결했습니다. (NEO-43648)
* webApps 미리 보기가 되지 않는 문제를 해결했습니다. (NEO-43242)
* 데이터 로드(파일) 활동이 있는 워크플로에서 외부 대상 매핑 파일을 사용할 때 게재 준비가 실패하는 문제를 해결했습니다. (NEO-43691)
* 충돌의 원인이 되며 인스턴스를 완전히 다시 시작해야 하는 문제를 해결했습니다. (NEO-44645)
* 워크플로 히트맵에서 결과를 로드할 수 없는 문제를 해결했습니다. (NEO-43360)
* FDA 외부 커넥터를 사용할 때 연결 문제로 이어질 수 있는 문제를 해결했습니다. (NEO-42722)
* 주소 대체 및 컨트롤 그룹 제외를 사용할 때 발생하는 증명 문제를 해결했습니다. (NEO-39695)
* Snowflake 커넥터 문제로 인해 워크플로 오류가 발생하는 문제를 해결했습니다. (NEO-46299)
* 개인화 블록에 잘못된 문자가 있을 때 클라이언트 콘솔이 멈추는 문제를 해결했습니다. (NEO-45761)
* Snowflake를 외부 데이터베이스로 사용하기 위해 외부 계정을 만들 때 발생할 수 있는 연결 문제를 해결했습니다. (NEO-45744)
* visibleIf 속성으로 보호되는 테이블의 정보를 표시하는 문제를 해결했습니다. (NEO-37865)
* 게재 분석 단계에서 &quot;$이(가) 정의되지 않음&quot; 오류 메시지를 표시하는 문제를 해결했습니다. (NEO-32940)
* 게재를 잘못된 eventType과 연결하는 문제를 해결했습니다. (NEO-45743)
* 간헐적인 코어 덤프로 인해 충돌이 발생하는 문제를 해결했습니다(NEO-30549).
* 게재에서 잘못된 HTML 코드를 사용할 때 충돌이 발생하는 문제를 해결했습니다. (NEO-40385)
* 관리자가 아닌 사용자가 게재 속성의 **분석** 탭에 액세스할 수 없는 문제를 해결했습니다. (NEO-34025)
* 메시지를 준비하는 동안 외부 서버에서 청크 모드로 이미지가 업로드되지 않는 문제를 수정했습니다. (NEO-40307)
* 원하는 수신자보다 많은 사람에게 게재가 보내질 수 있는 문제를 해결했습니다. (NEO-45108)

## 릴리스 7.2.2 - 빌드 9349 {#release-7-2-2}

[!BADGE 사용되지 않음]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="사용되지 않음"}

_2022년 3월 1일_

>[!NOTE]
>
> 이 빌드는 v7.2.1 Client Console과 호환됩니다.

**패치**

* **웹 분석** 외부 계정을 구성할 때 오류가 발생한 경우에도 통합 상태가 항상 [통합 성공]으로 표시되는 문제를 해결했습니다. (NEO-36672)
* 업그레이드 후 음수 ID가 있는 경우 시퀀스 ID 메커니즘과 관련된 몇 가지 오류를 해결했습니다. (NEO-43205, NEO-42846, NEO-42845)
* **웹 분석** 외부 계정에 반복 및 연속 게재를 사용할 때 해당 외부 계정의 데이터 일부가 유실되는 문제를 해결했습니다. (NEO-38548)
* 업그레이드 후 NmsActiveContact 테이블을 업데이트할 때 속도가 느려지는 문제를 해결했습니다. (NEO-43206)
* 업그레이드 후 **관리** 노드에 있던 기본 제공 폴더를 다른 위치로 옮긴 경우 발생하던 작업 실패 문제를 해결했습니다. (NEO-42875)
* **데이터 업데이트** 워크플로 활동을 사용할 때 수신자 스키마를 Google Cloud 외부 데이터베이스의 수신자 데이터로 업데이트하지 못하는 문제를 해결했습니다. (NEO-42343)
* 업그레이드 후 Adobe Analytics 커넥터 관련 문제를 해결했습니다. (NEO-43318, NEO-38136)
* 업그레이드 후 CUID를 &#39;VALUE_TO_CHANGE&#39;로 덮어쓰는 문제를 해결했습니다. (NEO-43267)
* 중간 소싱이 여러 개인 구성에서 중간 소싱 인스턴스와 마케팅 인스턴스를 동기화할 때 오류가 발생하는 문제를 해결했습니다. (NEO-10432)
* 브로드로그가 동시에 1,000개 이상 있는 경우 게재 가능성 워크플로를 새로 고칠 때 오류가 발생하는 문제를 해결했습니다. (NEO-40276)
* 오픈율 및 클릭률 게재 지표가 자동으로 업데이트되지 않는 문제를 해결했습니다. (NEO-43253)

## 릴리스 7.2.1 - 빌드 9346 {#release-7-2-1}

[!BADGE 사용되지 않음]{type=negative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=ko#rn-statuses" tooltip="사용되지 않음"}

_2022년 1월 10일_

**보안 개선**

FDA 계정의 보안 기능을 몇 가지 면에서 개선했습니다.

* 이제 FDA 외부 계정을 구성할 때 보다 안전한 인증을 위해 [키 쌍] 인증을 사용하여 Snowflake 계정에 로그인할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-snowflake.md)
* 이제 FDA 외부 계정을 구성할 때 시스템에서 할당한 관리 ID를 사용하여 Azure Synapse Analytics 계정에 로그인할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-synapse.md#azure-external)
* 최적의 보안을 위해 Campaign에서 log4j 라이브러리에 대한 참조를 모두 제거했습니다.

**호환성 업데이트**

Adobe Campaign은 이제 Windows Server 2019와 호환됩니다. [캠페인 호환성 매트릭스](../../rn/using/compatibility-matrix.md#OperatingSystems)를 참조하십시오.

**개선 사항**

* Microsoft Dynamics CRM 365 Connector

  Microsoft Dynamics Connector 웹 API에 대해 중요한 문제를 해결했습니다.

   * 워크플로에 의해 트리거된 가져오기 중에 문자열 유형 필드의 null 값이 빈 값 대신 Null로 저장되는 문제가 해결되었습니다.
   * 웹 API 호출을 사용하여 데이터를 가져오거나 내보내는 데 다음 오류가 발생하는 문제를 수정했습니다. &quot;잘못된 URI: URI 체계가 너무 깁니다.&quot;
   * Microsoft Dynamics 365에서 조회 필드가 포함된 데이터를 가져올 때 발생하는 다양한 문제를 해결했습니다.

* Google BigQuery FDA Connector

   * 이제 [호스팅 배포]에 Google BigQuery FDA Connector를 사용할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-google-big-query.md)
   * Google BigQuery FDA 커넥터용 프록시 서버에 연결할 수 있도록 지원을 추가했습니다. 필요한 프록시 옵션은 외부 계정 구성의 [옵션] 필드를 통해 설정할 수 있습니다. [자세히 표시](../../installation/using/configure-fda-google-big-query.md#google-external)

**기타 변경 사항**

* Microsoft CRM, Salesforce, Oracle CRM On Demand 작업 활동의 사용이 중단됨에 따라 인터페이스에서 제거했습니다. CRM 커넥터 활동을 사용하여 Adobe Campaign과 CRM 시스템 간의 데이터 동기화를 구성할 수 있습니다. [자세히 표시](../../workflow/using/crm-connector.md)
* 방문자 스키마(nms:visitor)에 **[!UICONTROL Encrypted identifier]** 필드를 추가했습니다. 이 필드는 계산되며 웹 애플리케이션에 사용할 수 있습니다. 중간 소싱 인스턴스에 Line 채널을 구성한 경우에 적용됩니다.
* 이제 CRM 데이터 소스를 **데이터 소스 변경** 활동으로 사용할 수 있습니다.
* 워크플로 활동의 **오류 관리** 속성에 새로운 옵션을 추가했습니다. **오류 시 중단** 옵션을 사용하면 자동으로 워크플로를 중지합니다. 중지한 워크플로우는 나중에 다시 시작할 수 없습니다(NEO-29661). [자세히 표시](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* 이제 수신자의 통계 그룹을 만드는 데 사용되는 nmsGroup 테이블의 기본 키를 생성할 때 전용 시퀀스를 사용합니다. 이전에는 xtknewId 시퀀스를 사용했습니다. (NEO-30832)
* CRM 커넥터 활동을 사용한 일괄 업데이트 작업에 대한 지원을 추가했습니다.
* 트랜잭션 메시지 처리 시간 관련 성능을 개선했습니다. (NEO-40370)

**패치**

* 게재를 만들 때 **추적 및 이미지** 창의 **이미지** 탭에 오류가 발생하는 문제를 해결했습니다. 이 문제는 자동 프록시 구성을 사용할 때 발생했습니다. (NEO-33260)
* 동기화 모드로 Debian 10 서버(HTTPS)에 파일을 업로드할 수 없는 문제를 해결했습니다.
* 게재 통계 테이블(`nmsDeliveryLogStats`)의 기록이 관련 게재 삭제 후에도 데이터베이스 정리 시 중간 소싱 인스턴스에서 제거되지 않는 문제를 해결했습니다. (NEO-31034)
* 토큰 기반 인증을 사용할 때 iOS에서 모바일 앱 알림을 보낼 수 없는 문제를 해결했습니다(NEO-38640).
* 보고서를 만들고 구성하려고 할 때 스크립트 오류 메시지가 표시되는 문제를 해결했습니다(NEO-38393).
* 대량의 게재 지표가 동시에 업데이트되면서 Oracle에서 추적 워크플로가 실패하는 문제를 해결했습니다(NEO-39653).
* 제어 유형화 실행 중 오류가 발생하여 게재를 보낼 수 없는 문제를 해결했습니다(NEO-39833).
* 온라인 설문 조사 응답의 HTML 페이지에 특수 문자가 올바르게 표시되지 않는 랜딩 페이지 관련 문제를 해결했습니다(NEO-39438).
* [탐색기] 탭에서 폴더를 마우스 오른쪽 버튼으로 클릭하면 Campaign Classic 콘솔이 작동하지 않는 문제를 해결했습니다(NEO-38884).
* [웹 분석] 구성이 누락된 새 게재에서 이전에 만들었으며 [웹 분석] 계정에 연결되어 있는 게재 템플릿을 사용할 때 발생하는 오류를 해결했습니다. (NEO-28666)
* 워크플로에 첨부된 모바일 게재를 미리 볼 수 없는 문제를 해결했습니다.
* 링크 추적용 URL 서명 메커니즘이 활성화되어 있을 때 개인화된 추적 URL이 리디렉션되지 않는 오류를 해결했습니다.
* 인덱스 관리 문제로 인해 업그레이드 후 오류가 발생할 수 있는 문제를 해결했습니다.
* **가져오기** 또는 **내보내기** 워크플로 활동에서 Microsoft Dynamics CRM에 룩업 필드 데이터 유형을 사용할 때 발생하는 오류를 해결했습니다.
* 프록시 구성 문제로 인해 콘솔에 로그인하지 못하는 문제를 해결했습니다. (NEO-38388)
* **폴더 제거** 기능이 제대로 작동하지 못하게 하는 회귀 문제를 해결했습니다. (NEO-37459)
* Microsoft Dynamics CRM 계정에 xml 데이터 필드를 사용할 때 참조된 xml에 큰따옴표가 포함된 경우 잘못된 요청 오류가 발생하는 문제를 해결했습니다.
* 네트워크 시간 초과 문제가 네트워크 오류가 아닌 스크립트 중단 문제로 잘못 기록되는 문제를 해결했습니다. 이 문제는 JavaScript 활동에 포함된 HTTP 요청의 경우에 발생했습니다. (NEO-38079)
* Amazon Redshift HoursDiff 및 MinutesDiff 함수를 실행할 때 시간 구성 요소를 추출하려 하는 중 잘못된 결과를 반환하는 문제를 해결했습니다.(NEO-31673)
* 빌드 9182 이후 게재에 대해 **핫 클릭** 보고서를 로드할 수 없는 문제를 해결했습니다. (NEO-28900)
* URL의 &amp; 기호를 문자 엔티티 참조(`&amp;`)로 바꾸어 사용자가 QR 코드에 연결된 URL에 액세스할 수 없는 문제를 해결했습니다. (NEO-28621)
* 사용자가 [웹 분석] 계정에 연결된 새 캠페인 워크플로와 게재 활동을 만들 때마다 새 외부 계정이 생기는 문제를 해결했습니다. 이 문제는 webAnalyticsAccount 게재 개체에서 ID가 누락되어 발생했습니다. (NEO-39691)
* 목록의 신원이 데이터베이스에서 음수 ID로 지정되어 있는 경우 **목록 읽기** 워크플로가 작동하지 않는 문제를 해결했습니다. (NEO-39607)
* **중간 소싱(게재 로그)** 워크플로가 실패하는 문제를 해결했습니다. (NEO-39662)
* 워크플로에 첨부된 이메일 게재를 미리 볼 수 없는 문제를 해결했습니다. (NEO-37840)
* 데이터베이스 정리 워크플로에서 목록 값이 포함된 유효한 테이블을 삭제할 수 있는 문제를 해결했습니다. (NEO-34911)
* 마케팅 인스턴스에서 과금 워크플로가 충돌할 수 있는 문제를 해결했습니다.
