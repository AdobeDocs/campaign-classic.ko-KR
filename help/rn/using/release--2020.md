---
product: campaign
title: 2020년 릴리스
description: Campaign Classic 2020 릴리스에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
hidefromtoc: true
hide: true
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: 378ac691c15f8200f8a14d573d4b15521f6cb531
workflow-type: tm+mt
source-wordcount: '6601'
ht-degree: 73%

---

# 2020년 릴리스{#release-2020}




## 릴리스 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) 릴리스 20.3.3 - 빌드 9234 {#release-20-3-3-build-9234}

_2021년 1월 11일_

* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)
* MTA 프로세스가 충돌할 수 있는 브로드로그 생성 프로세스와 관련된 회귀 문제를 해결했습니다.

### ![](assets/do-not-localize/red_2.png) 릴리스 20.3.1 - 빌드 9228 {#release-20-3-1-build-9228}

_2020년 10월 27일_

>[!CAUTION]
>
> * 이 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Adobe IMS(ID 관리 서비스)를 통해 Campaign에 연결할 경우, **2021년 6월 30일** 이후부터 Campaign 서버 및 클라이언트 콘솔은 Campaign에 연결할 수 있도록 업그레이드를 해야 합니다. [자세히 알아보기](../../technotes/using/ims-updates.md)
> * 이 릴리스는 [보안 픽스](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.
> * oAuth 인증을 통해 Experience Cloud 트리거 통합을 사용할 경우 [이 페이지에서](../../integrations/using/configuring-adobe-io.md) 설명한 대로 Adobe I/O로 이동해야 합니다. Campaign의 [레거시 oAuth 인증 모드는](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=ko) **2021년 9월**&#x200B;부로 사용이 중단되었습니다. 호스팅 환경의 경우 **2022년 2월 23일**&#x200B;까지 연장 사용할 수 있습니다. 온-프레미스 또는 하이브리드 고객은 Adobe 고객 지원 센터에 문의하면 2022년 2월까지 지원을 연장할 수 있습니다. Adobe에 [OAuth 애플리케이션의 AppID](../../integrations/using/configuring-pipeline.md#step-optional)를 제공해야 합니다.

**새로운 기능**

<table> 
<thead>
<tr> 
<th> <strong>iOS 푸시 알림 개선</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>모바일 앱을 Campaign과 통합할 때 APNs(Apple 푸시 알림 서비스)와의 통신 보안을 유지해야 합니다. 인증서 기반 인증 또는 토큰 기반 인증을 사용할 수 있습니다.
</p>
<p>이제 Campaign Classic의 iOS 모바일 앱에서 다음 두 가지 인증 모드를 사용할 수 있습니다.
</p>
<ul> 
<li><p>토큰 기반 인증(권장): 이 인증 모드는 .p8 파일을 기반으로 합니다. APNs에 대한 각 요청에 토큰이 포함되어 있으므로 이 인증 모드가 더 빠릅니다. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">자세히 알아보기</a></p></li>
<li><p>인증서 기반 인증:이 인증 모드는 .p12 파일을 기반으로 합니다. 모든 앱에 대해 별도의 인증서가 필요합니다. 이 인증서는 개발자 계정을 통해 Apple에서 제공합니다. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">자세히 알아보기</a></p></li> 
</ul>
<p><a href="../../delivery/using/configuring-the-mobile-application.md">자세한 설명서</a>에서 Campaign에서 인증 모드를 선택하는 방법을 알아봅니다.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Android 푸시 알림 개선</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Android 푸시 채널 인증용 FCM HTTP v1 API를 지원하도록 <a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Android 푸시 알림</a>이 개선되었습니다. </p>
<p>새롭게 지원되는 API 버전을 사용하면 향상된 풍부한 푸시 메시지 기능을 제공하는 FCM 알림 메시지를 전송할 수 있습니다. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">자세히 알아보기</a></p> 
<p>Adobe Campaign에서 Android용 FCM HTTP v1 API를 구성하는 방법을 <a href="../../delivery/using/configuring-the-mobile-application-android.md">이 섹션</a>에서 살펴보십시오.</p>
</td> 
</tr> 
</tbody> 
</table>

**향상된 보안 기능**

* 라이브러리의 안전한 로드:이제 DLL 사전 로드 공격으로부터 보호하기 위해 Campaign 클라이언트(nlclient)를 로드하는 동안 Windows 기본 시스템 DLL 경로에서만 Windows DLL이 로드됩니다. [자세한 내용](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks)(NEO-24147)
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하려는 보안 문제를 해결했습니다. (NEO-25661)
* 수신자 테이블과 두 번째 수준 관계가 있는 사용자 지정 테이블에서 레코드가 삭제되지 않는 GDPR 개인 정보 요청을 처리하는 동안 발생하는 문제를 해결했습니다. (NEO-25967)
* Adobe Experience Manager 템플릿을 동기화하려고 할 때 관리자가 아닌 사용자가 API 호출을 사용하는 보안 문제를 해결했습니다. (NEO-23487)

**호환성 업데이트**

이제 다음 시스템이 Campaign에서 지원됩니다.
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

자세한 내용은 [Campaign 호환성 매트릭스](../../rn/using/compatibility-matrix.md)를 참조하십시오.

**사용되지 않는 기능**

다음 기능은 20.3에서 사용되지 않습니다.

* 대상을 Adobe Experience Cloud으로 가져오고 내보내는 데 사용되는 demdex 도메인은 사용되지 않습니다. 외부 계정 가져오기/내보내기에 demdex 도메인을 사용하는 경우 그에 따라 구현을 조정해야 합니다. [자세히 알아보기](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* 기존 oAUTH 인증 설정을 기반으로 파이프라인에 액세스하는 트리거 통합 인증이 변경되었으며 Adobe I/O로 이동되었습니다. [자세히 알아보기](../../integrations/using/configuring-adobe-io.md)

더 자세한 내용은 [사용되지 않거나 제거된 기능 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

**개선 사항**

* **클라이언트 콘솔**&#x200B;에 몇 가지 기능이 개선되었습니다.
   * 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다. 서버 및 클라이언트 콘솔 업그레이드는 2021년 6월 30일 이후에 연결할 수 있어야 합니다.
   * 일부 인터넷 보안 GPO 규칙 제한 사항과 비호환이 되지 않도록 하기 위해 Campaign 클라이언트 콘솔 로그온 화면이 기본 제공 표준 Windows 양식으로 대체되었습니다.
   * 워크플로우에서 64비트 클라이언트 콘솔을 사용하여 활동을 복사/붙여넣을 때 발생하는 문제를 해결했습니다. (NEO-27635)
   * **정보** 메뉴에서 64비트 및 32비트 콘솔을 구분하는 정보가 추가되었습니다.
* 이제 워크플로우를 다시 시작할 때 워크플로우 식별자가 로그에 표시되므로 다시 시작된 워크플로우를 보다 잘 식별할 수 있습니다.
* Nllastdelid라는 새로운 영구 쿠키가 도입되었습니다. 이 쿠키(UUID230 제외)는 deliveryId를 저장합니다. 세션 쿠키가 없으면 이 쿠키에 있는 deliveryId에서 브로드로그 정보를 가져옵니다.
이 변경 사항은 브라우저 세션이 종료될 때 발생하는 다음의 문제를 해결합니다. deliveryId 및 broadlogId가 포함된 세션 쿠키가 삭제됨. deliveryId가 없으면 브로드로그 정보를 찾을 수 없으며 영구 추적(최신 게재)의 경우 추적 테이블 정보가 누락됩니다.
쿠키에 대한 자세한 내용은 [이 섹션](../../platform/using/privacy-and-recommendations.md#cookies)을 참조하십시오.
* 게재 전송 전에 MTA 프로세스를 다시 시작하여 게재 가능한 서버를 통해 대량 게재 처리량 성능을 개선했습니다.

**기타 변경 사항**

* SFTP에 상대 경로를 사용할 때 `~/` 문자가 더 이상 자동으로 추가되지 않습니다. 필요한 경우 경로에 `~/` 문자를 수동으로 추가할 수 있지만 **절대 경로**&#x200B;를 사용하는 것이 좋습니다.
* Microsoft SQL Server로 새 데이터베이스를 구성할 때 사용 가능한 인증 방법에서 Windows NT 인증이 제거되었습니다. [자세한 내용](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* 데이터베이스 정리 워크플로우는 성능을 개선하기 위해 Teradata에 맞게 최적화되었습니다. (NEO-19959)
* Adobe Target에서 이미지를 삽입할 때 표시되는 오류 메시지가 개선되었으며 테넌트 이름이 외부 계정에서 비어 있었습니다.
* 게재 속성에서 **[!UICONTROL Archive emails]** 옵션 이름이 변경되었습니다 **[!UICONTROL Email BCC]**.
* 견고성 향상을 위해 노드가 잘못된 모든 쿼리가 거부됩니다. 검사를 비활성화하고 이전 동작으로 돌아가야 하는 경우 XtkSecurity_Disable_QueryCheck를 0으로 설정할 수 있습니다.
* nmsBroadlogId 시퀀스에 대한 음수 ID 범위 지원이 추가되었습니다. 이 빌드는 음수 범위를 포함하도록 nmsBroadlogId 시퀀스의 min_value를 조정합니다. 음의 ID를 허용하지 않는 엄격한 사용 사례가 있는 경우 시퀀스의 min_value를 1로 되돌립니다.

**기술 진화**

Tomcat이 버전 7(7.0.103)에서 버전 8(8.5.57)로 업데이트되었습니다.

`tomcat-7` 디렉터리가 `tomcat-8` 디렉터리로 대체됩니다.

Windows의 경우 _iis_neolane_setup.vbs_ 및 _apache_neolane.conf_&#x200B;가 `conf` 디렉터리(기존 `tomcat-7/conf` 디렉터리 대신)에 설치됩니다.

linux의 경우 _apache_neolane.conf_&#x200B;가 이제 `conf` 디렉터리에 설치됩니다.

**패치**

* 게재 통계가 다시 계산되지 않도록 하는 문제를 해결했습니다.
* 이전 빌드를 사용하여 서버에 연결된 Campaign Classic 9080 빌드를 사용하는 경우 CSV 파일을 업로드할 때 오류 메시지가 표시되는 문제를 해결했습니다. (NEO-23218)
* 외부 계정에 대한 Microsoft Dynamics CRM 마법사를 구성할 때 오류 메시지를 표시하는 문제를 해결했습니다. 이는 최신 MS Dynamics CRM API 버전과의 호환성 문제 때문입니다. (NEO-24528)
* CRM 커넥터를 사용하여 Campaign Classic에서 Microsoft Dynamics로 검색 형식 레코드(다른 테이블과 연결된 외부 키 레코드로 구성된 데이터를 의미)를 내보낼 수 없는 문제를 해결했습니다. (NEO-23864)
* CRM 커넥터에서 **자동 인덱스** 옵션을 활성화한 경우 Microsoft Dynamics 데이터를 가져올 수 없는 문제를 해결했습니다. (NEO-25981)
* 연결이 종료된 경우에도 열려 있을 수 있었던 IMS 인증 문제가 해결되었습니다. 연결이 누적되고 시스템 리소스가 소모되는 것을 방지하기 위해 이제 연결이 종료되는 즉시 자동으로 닫힙니다. (NEO-25996)
* 외부 계정의 잘못된 구성(잘못된 계정 또는 암호)으로 인해 게재에 대한 Adobe Experience Manager 콘텐츠 동기화가 실패할 때 오류 메시지가 표시되지 않는 문제를 해결했습니다. 이제 실패 시 메시지가 표시되므로 문제를 보다 쉽게 식별할 수 있습니다. (NEO-25586)
* **데이터 업데이트** 활동에서 **업데이트** 작업 유형을 선택할 때 발생하는 문제를 수정했습니다. 업데이트할 데이터가 올바르지 않으면 워크플로우는 오류가 발생하여 실패합니다. 데이터가 잘못된 경우 워크플로우는 실패하지 않으며 레코드는 **거부** 아웃바운드 전환에 저장됩니다. (NEO-23794)
* 하위 워크플로우가 포함된 워크플로우가 작동하지 않는 문제를 해결했습니다. (NEO-24036)
* 캠페인 템플릿 설명을 편집 시 기호(예: 일본어 문자)를 복사 및 붙여넣을 때 **저장** 단추가 표시되지 않는 문제를 해결했습니다. (NEO-27071)
* 인스턴스 구성 마법사에서 추적 서버를 변경할 수 없는 문제를 해결했습니다.
* **저장** 단추를 클릭하기 전에 창 외부를 클릭할 때 캠페인 또는 캠페인 템플릿의 설명이 저장되지 않는 문제를 해결했습니다. (NEO-27449)
* **활성 청구 프로필 수**(billingActiveContactCount) 기술 워크플로우가 작동하지 않는 문제를 해결했습니다. 스키마 확장의 계산된 필드에서 링크가 수행된 경우 이 문제가 발생할 수 있습니다. 많은 양의 데이터가 만들어져서 이로 인해 데이터베이스가 임시 공간이 부족해질 수 있습니다. (NEO-24062)
* 일본어 문자를 텍스트 및 csv 파일의 파일 끝에 배치하면 가져올 수 없는 **데이터 로드(파일)** 작업 문제를 해결했습니다. (NEO-24957)
* **분석 시작** 및 **분석 완료** 필드가 올바르게 채워지지 않도록 하는 연속 게재 문제를 수정했습니다. (NEO-20755)
* **수신자**(nms:recipient)가 아닌 다른 스키마에서 쿼리 후에 SMS 메시지를 미리 볼 때 오류 메시지를 표시하는 문제를 해결했습니다. (NEO-27517)
* Snowflake FDA 커넥터를 사용할 때 발생하는 문제를 해결했습니다. Snowflake FDA 액세스 이름 권한이 있는 사용자가 Snowflake 스키마에 대한 쿼리를 실행할 수 없습니다. 로그에 &quot;암호를 찾을 수 없음&quot; 유형의 오류가 표시되었습니다. (NEO-23851)
* FDA 커넥터를 사용하는 경우 연결된 FDA 스키마 이름이 현재 스키마의 요소 이름의 하위 문자열에서 발생하던 문제를 해결했습니다. 예를 들어 FDA 스키마가 &quot;cust&quot;이고 수신자 스키마 내의 요소 중 하나가 &quot;고객&quot;인 경우 이러한 문제가 발생했습니다. &quot;customer&quot; 요소 내에서 열을 가져오고 &quot;cust&quot; FDA 스키마에서 열을 추가할 때 로컬 열에 대한 값이 누락되었습니다. (NEO-20193)
* 외부 데이터베이스에서 레코드를 가져와 캠페인 데이터베이스에 삽입할 때의 워크플로우 문제를 해결했습니다. (NEO-26359)
* 다음과 같은 **업데이트 이벤트 상태** 기술 워크플로우의 문제를 수정했습니다. **게재 통계** 활동에서 들어오는 해당 필드의 크기 조정을 일치시키기 위해 **업데이트 게재 통계** 활동에서 3개의 대상 필드 크기가 32비트에서 64비트로 변경되었습니다. (NEO-11557) **업데이트 이벤트 상태** 워크플로우에 대한 자세한 내용은 [이 섹션](../../workflow/using/about-technical-workflows.md)에서 알아봅니다.
* 필터를 적용하려고 할 때 스크립트 오류가 발생하고 날짜 범위별로 필터를 사용할 수 없게 하는 **메시지 센터 이벤트 내역** 보고서의 문제를 해결했습니다. (NEO-23365)
* **Campaign 작업** (operationMgt) 및 **미리 보기** (예측) 기술 워크플로우 간의 간섭 문제를 해결했습니다. 이 문제는 예약된 게재가 &quot;Target 준비&quot; 또는 &quot;게재할 준비가 됨&quot; 상태에 있을 때 발생했습니다. (NEO-20819)
* xtkOperator의 mdata 필드에 XML 식별자가 없을 때 XML 구문 분석 문제를 해결했습니다. 업그레이드 후 오류가 발생했습니다. (NEO-26113)
* SSL에서 암호화된 Azure 외부 계정에 연결된 **파일 전송** 활동을 사용할 때 HTTPS 대신 HTTP로 연결이 되는 문제를 해결했습니다. (NEO-26720)
* 정리 워크플로 중 up_updates 프로시저에서 오류가 발생할 수 있는 MSSQL 데이터베이스에 대한 문제를 해결했습니다.
* 상호 작용 요청이 계속 처리되는 경우 웹 프로세스 종료 중에 발생하는 충돌을 해결했습니다. (NEO-26447)
* Oracle DB의 **NoNull** 함수가 업그레이드 후 더 이상 작동하지 않던 문제를 해결했습니다. (NEO-26488)
* LINEV2 패키지가 메시지 센터 패키지 없이 설치된 경우 9171 업그레이드 후 추적 워크플로우가 실패하는 문제를 해결했습니다.
* &#39;APP&#39; 특성에 대한 데이터베이스 연결 문자열이 잘못된 값을 얻음으로써 연결 풀이 원하는 연결 수로 증가하지 못하는 확장성 문제를 해결했습니다. (NEO-25105)
* 최신 Windows 10 업데이트 후 Adobe Campaign에 로그인할 수 없는 프록시 구성 수준의 문제를 해결했습니다. (NEO-27813)
* 추적 링크가 포함된 HTML 템플릿을 가져온 후 게재된 이메일에 원하지 않는 URL이 표시되는 문제를 해결했습니다. (NEO-25909)
* 워크플로우에서 **분할** 작업 중 나머지 부분의 타겟 데이터를 표시할 때 서버가 충돌하는 문제를 해결했습니다.
* 식 구문 분석기를 지울 때 메모리 손상을 방지하여 서버 충돌 문제를 해결했습니다. (NEO-26856)
* 관리자가 아닌 사용자가 인스턴스 변수를 정의했던 데이터 연계 강화 작업의 문제를 해결했습니다. (NEO-25653)
* FDA 데이터베이스(Teradata, Snowflake)로 워크플로우 데이터 내보내기를 차단할 수 있는 회귀 문제를 해결했습니다.

## 릴리스 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) 릴리스 20.2.5 - 빌드 9188 {#release-20-2-5-build-9188}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2021년 3월 31일_

**개선 사항**

* 잘못된 Soap 호출에서 충돌이 발생하지 않도록 개선되었습니다. 이렇게 하면 복잡한 특정 쿼리를 실행하려고 할 때 인스턴스 작동이 중지될 수 있습니다. (NEO-28796, NEO-30553)
* 호스트 이름 확인으로 인해 TLS를 사용하는 SMS 게재가 전송되지 않는 회귀 문제를 해결했습니다. (NEO-29581)
* 일부 이메일 클라이언트에서 서명된 추적 링크가 작동하지 않는 문제를 해결했습니다. (NEO-28414, NEO-29615)
* WebApp 추적 태그를 사용할 때 중복 ID와 충돌할 수 있는 추적 ID 시퀀스를 수정했습니다. (NEO-27931)
* 실행 중인 워크플로우가 일별 wfserver 다시 시작에 의해 중지되는 문제를 해결했습니다. (NEO-30047)
* Adobe Experience Manager 템플릿을 동기화하려고 할 때 관리자가 아닌 사용자가 API 호출을 사용하는 보안 문제를 해결했습니다. (NEO-32389, NEO-23487)
* 템플릿으로 만든 게재에서 게재 대화 상자를 닫을 때 콘솔이 충돌하는 문제를 해결했습니다. (NEO-31547)
* 내에서 게재를 만들고 저장할 때 발생하는 문제를 해결했습니다. **타깃팅 및 워크플로** 캠페인의 탭: 다음 오류로 미리 보기가 실패합니다. (NEO-29440)
* Tomcat 8.5에서 잘못된 응답을 전송하여 트랜잭션 메시지 로그에 오류가 발생하는 문제를 해결했습니다. (NEO-30858)
* 외부 스레드 관리에서 메모리 손상을 일으키고 성능에 영향을 주는 회귀 문제를 해결했습니다.
* 사용자 지정 대상 매핑을 사용할 때 청구 워크플로우가 실패하는 문제를 해결했습니다. 사용자 지정 스키마의 기본 키는 정수 값만 허용하는 &#39;sourceId&#39; 열에 저장됩니다. 이제 정수 및 문자열 값을 허용합니다. (NEO-25914, NEO-28146)
* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) 릴리스 20.2.4 - 빌드 9187 {#release-20-2-4-build-9187}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)
* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453, NEO-31454)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2020년 12월 22일_

>[!CAUTION]
>
> * 이 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Adobe IMS(ID 관리 서비스)를 통해 Campaign에 연결할 경우, **2021년 6월 30일** 이후부터 Campaign 서버 및 클라이언트 콘솔은 Campaign에 연결할 수 있도록 업그레이드를 해야 합니다.  [자세히 알아보기](../../technotes/using/ims-updates.md)
> * 이 릴리스는 [보안 픽스](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.
> * oAuth 인증을 통해 Experience Cloud 트리거 통합을 사용할 경우 [이 페이지에서](../../integrations/using/configuring-adobe-io.md) 설명한 대로 Adobe I/O로 이동해야 합니다. Campaign의 [레거시 oAuth 인증 모드는](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=ko) **2021년 9월**&#x200B;부로 사용이 중단되었습니다. 호스팅 환경의 경우 **2022년 2월 23일**&#x200B;까지 연장 사용할 수 있습니다. 온-프레미스 또는 하이브리드 고객은 Adobe 고객 지원 센터에 문의하면 2022년 2월까지 지원을 연장할 수 있습니다. Adobe에 [OAuth 애플리케이션의 AppID](../../integrations/using/configuring-pipeline.md#step-optional)를 제공해야 합니다.

**개선 사항**

* 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다.
* 기존 oAUTH 인증 설정을 기반으로 파이프라인에 액세스하는 트리거 통합 인증이 변경되었으며 Adobe I/O으로 이동되었습니다. [자세히 알아보기](../../integrations/using/configuring-adobe-io.md)
* [iOS APNs 레거시 이진 프로토콜에 대한 지원 종료](https://developer.apple.com/kr/news/?id=c88acm2b)에 따라 업그레이드 이후 이 프로토콜을 사용하는 모든 인스턴스는 HTTP/2 프로토콜로 업데이트됩니다.
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)
* 연결 오류 후 SMPP 커넥터가 비활성화되고 다른 SMS 게재가 전송되지 않아 성능 문제가 발생하는 문제를 해결했습니다. (NEO-28609)
* 식 구문 분석기를 지울 때 메모리 손상을 방지하여 서버 충돌 문제를 해결했습니다. (NEO-26856)
* 워크플로우에서 **분할** 작업 중 나머지 부분의 타겟 데이터를 표시할 때 서버가 충돌하는 문제를 해결했습니다.
* **수신자**(nms:recipient)가 아닌 다른 스키마에서 쿼리 후에 SMS 메시지를 미리 볼 때 오류 메시지를 표시하는 문제를 해결했습니다. (NEO-27517)
* 호스트 이름에 명시적으로 정의된 포트 번호로 HTTPS 연결 요청을 할 때 인증서 오류로 인해 호출이 실패하는 문제를 해결했습니다. (NEO-29146)
* 마케팅 인스턴스에서 큰 코어 덤프 파일을 생성하는 POSIX 스레드 관리 문제를 해결했습니다. (NEO-28117, NEO-29281)
* 게재를 준비하거나 되풀이하는 게재 미리 보기를 사용할 때 웹 프로세스가 충돌할 수 있는 문제를 해결했습니다. (NEO-27790, NEO-27517)
* 관리자가 아닌 연산자에 의해 트리거될 때 게재 또는 증명 전송이 실패하는 문제를 해결했습니다. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) CNAME과 새로운 데이터베이스 모니터링 기능을 사용하는 도메인 구성이 포함된 **새로운 10월 컨트롤 패널 릴리스**. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=ko)

### ![](assets/do-not-localize/red_2.png) 릴리스 20.2.3 - 빌드 9182 {#release-20-2-3-build-9182}

_2020년 9월 11일_

* 게재 부분의 잘못된 기능 하나 때문에 메모리 과부하가 발생하여 게재 준비의 차단을 야기하는 회귀 문제를 해결했습니다. (NEO-27346)
* 웹 애플리케이션을 다시 게시하기 전에 Apache와 웹 서버가 꺼지는 업그레이드 후 문제를 해결했습니다. (NEO-27155)
* 탭의 잘못된 해석으로 인해 추적 URL이 표시되는 HTML 템플릿 관리의 회귀 문제를 해결했습니다. (NEO-25909)
* 관리되지 않는 데이터 소스로 인해 실패할 수 있는 데이터베이스 정리 워크플로우 문제를 해결했습니다. (NEO-23160, NEO-23364)
* 이제 정리 워크플로우는 만료된 목록을 하나씩 제거하는 대신 100개씩 일괄처리합니다.
* 외부 계정의 내부 이름을 수정할 수 없는 회귀 문제를 해결했습니다. (NEO-27323)
* nlserver(오류 로그)의 잘못된 시작을 야기하는 업그레이드 후 회기를 해결합니다.
* 공유 메모리에 대한 업데이트 관리가 개선되었습니다. 20.2에서 필요한 추가 단계는 더 이상 필요하지 않습니다.

### ![](assets/do-not-localize/red_2.png) 릴리스 20.2.2 - 빌드 9180 {#release-20-2-2-build-9180}

_2020년 7월 22일_

* 서명 기능이 비활성화되었을 때 추적을 수행할 수 없는 문제를 해결했습니다. (NEO-26411)
* 개인화된 도메인에서 서명되지 않은 링크가 허용되어야 할 때 차단되는 문제를 해결했습니다. (NEO-25210)
* 특정 이전 버전의 Outlook을 사용할 때 추적 URL을 열거나 클릭하지 못하는 문제를 해결했습니다. (NEO-25688)
* 부적절한 ASCII 문자 제어로 인해 이메일 게재에서 미러 페이지 URL이 잘못 정의되는 문제를 해결했습니다. (NEO-26084)
* 피싱 방지 서비스에서 인코딩 URL 관리 문제를 해결했습니다. (NEO-25283)
* 개인화 매개 변수의 조각을 사용하여 URL을 추적할 수 없는 문제(파운드 기호가 있는 앵커 태그)를 해결했습니다. (NEO-25774)
* 특정 사용자 지정 추적 공식을 사용할 때의 추적 문제를 해결했습니다. (NEO-25277)
* &quot;알림 클릭&quot; 추적이 작동하지 않는 문제를 해결했습니다(iOS 및 Android 푸시 알림). (NEO-25965)
* 워크플로우의 실패를 야기하는 워크플로우 내 계산된 필드에 영향을 주는 회귀 문제를 해결했습니다. (NEO-25194)
* 웹 추적 URL 즉시 만들기가 작동하지 못하게 하는 회귀 문제를 해결했습니다. (NEO-20999)
* PDF로 내보낼 때 잘림으로 표시되는 기본 제공 게재 보고서의 회귀 문제를 해결했습니다. (NEO-25757)
* 배포 마법사의 충돌 문제를 해결했습니다.
* 업그레이드 후 오퍼 알림 워크플로우가 제대로 작동하지 않는 문제를 해결했습니다.
* iOS HTTP2 커넥터가 개선되었습니다(타사 업데이트 및 오류 관리). (NEO-25904, NEO-25903)
* 더 이상 사용되지 않은 jar 파일에 대한 참조(iOS 알림)를 제거하도록 catalina.properties의 jarToSkip 목록이 업데이트되었습니다.
* 업그레이드 후 게재 준비를 차단하는 문제를 해결했습니다.
* 새 시퀀스 ID 메커니즘으로 전환에 따라서 수신자 테이블을 업데이트하는 모든 웹 애플리케이션은 업그레이드 후 다시 게시됩니다.
* 게재 콘텐츠의 잠재적 XSS 취약성 문제를 해결했습니다. (NEO-17987, NEO-26073)

![](assets/do-not-localize/cp-icon.png) 활성 프로필 모니터링, 하위 도메인 게재 기능 감사 및 GPG 키 관리가 포함된 **새로운 제어판 6월 릴리스** . [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=ko)

### ![](assets/do-not-localize/red_2.png) 릴리스 20.2.1 - 빌드 9178 {#release-20-2-1-build-9178}

_2020년 6월 8일_

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> <strong>이모티콘 지원</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Campaign에서 메시지를 디자인할 때 이제 전용 단추를 사용하여 메시지 본문에 이모티콘을 쉽게 삽입할 수 있습니다. 전자 메일 제목 줄에도 추가할 수 있습니다. 인터페이스에서 사용 가능한 이모티콘 목록을 사용자 지정할 수 있습니다.</p>
    <p>이모티콘 추가에 대한 자세한 내용은 <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">세부 설명서</a>를 참조하십시오. <a href="../../delivery/using/customizing-emoticon-list.md">이 섹션</a>에서 이모티콘 목록 을 사용자 지정하는 방법을 배웁니다.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA 커넥터</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>이제 캠페인 인스턴스를 Azure Synapse 외부 데이터베이스에 연결할 수 있습니다. 이 연결은 새 외부 계정을 통해 관리됩니다.</p>
    <p>Azure Synapse는 하이브리드 및 온-프레미스 환경에서만 사용할 수 있습니다. 자세한 내용은 <a href="../../installation/using/configure-fda-synapse.md">세부 설명서</a>를 참조하십시오.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>태국 및 브라질 개인 정보 보호 법</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>태국 개인 정보 보호법(PDPA)은 태국에 대한 데이터 보호 요구 사항을 통합하고 현대화한 새로운 개인 정보 보호법입니다. </p>
   <p>브라질의 Lei Geral de Proteção de Dados(LGPD)는 2021년 초부터 브라질에서 개인 데이터를 수집하거나 처리하는 모든 회사에 효력을 발휘합니다.</p>
   <p>이러한 규정은 해당 국가에 있는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다. Adobe는 Adobe Campaign에서는 이미 사용 가능한 개인 정보 보호 기능(동의 관리, 데이터 보존 설정 및 사용자 역할 포함) 이외에도 다음과 같은 추가 기능을 추가하여 PDPA 및 LGPD에 대한 준비를 도울 수 있습니다.</p>
   <ul> 
     <li><p>액세스 권한 및 삭제 권한: GDPR 및 CCPA에 추가된 기능을 활용하고 있습니다. <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html">자세한 내용</a></p></li> 
     <li> <p>이제 Campaign 인터페이스 또는 API를 사용하여 개인 정보 요청을 만들 때 PDPA, LGPD, GDPR, CCPA와 같은 <strong>규정</strong> 유형을 선택합니다. <a href="https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">자세한 내용</a></p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 전자 메일 링크 추적에 대한 개선된 보안 기능이 모든 고객에 대해 기본적으로 활성화되어 있습니다. 고객 지원 센터에 연락하여 활성화할 수 있는 향상된 추가 보안 기능을 사용할 수 있습니다. 호스팅되지 않은 고객이 이 기능을 사용하도록 설정하는 기능 및 단계에 대한 자세한 내용은 [보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/kr/campaign/kb/acc-security.html)에서 확인할 수 있습니다. (NEO-24232)

* 보안을 최적화하기 위해 파일 이름을 생성하는 데 사용되는 MD5 해싱 알고리즘이 공개 파일 업로드를 위해 sha256으로 보강되었습니다. (NEO-17044)

* XSS 공격에 대한 보안을 강화하기 위해 미러 페이지를 실행할 때 클라이언트측 스크립트가 비활성화됩니다. (NEO-17987)

* **개인 정보 보호 요청 파일 정리** 기술 워크플로우가 조정 데이터를 삭제하지 못하는 문제를 해결했습니다. (NEO-25168, NEO-21004)

* SFTP 키 기반 인증이 Debian 9에서 작동하지 않는 **파일 전송** 활동 문제를 해결했습니다. (NEO-23183)

**향상된 호환성**

이제 다음 시스템이 Campaign에서 지원됩니다.
* 운영 체제: Debian 10
* RDBMS: Oracle 18c 및 Oracle 19c
* FDA: Azure Synapse Analytics

자세한 내용은 [Campaign 호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.

**개선 사항**

* 트랜잭션 메시지 기능이 개선되어 사용자 경험이 향상되었습니다. 이제 실행 인스턴스에서 삭제되는 트랜잭션 메시지 템플릿을 게시 취소할 수 있습니다. [자세히 알아보기](../../message-center/using/publishing-message-templates.md#template-unpublication)

* 이미지나 첨부 파일이 포함된 전자 메일을 보낼 때 제한을 설정하는 새로운 옵션을 사용할 수 있습니다. 이러한 경고는 성능 문제를 방지할 수 있으며 이는 트랜잭션 메시징에서 특히 유용합니다. [자세한 내용](../../installation/using/configuring-campaign-options.md#delivery)

* 새로운 **데이터베이스 게재 부분 준비** 옵션을 사용하면 데이터베이스 내에서 직접 게재 준비를 수행할 수 있으므로 분석 시간을 크게 단축할 수 있습니다. 이 옵션은 특정 구성에만 사용할 수 있습니다. [자세히 알아보기](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis) (NEO-23886)

* Microsoft Dynamics용 [CRM 커넥터 작업](../../workflow/using/crm-connector.md) 성능이 개선되었습니다. (NEO-13303, NEO-12710)

* 공유 메모리 버전이 증가했습니다.

  >[!WARNING]
  >
  >이 개선 사항은 업그레이드를 수행한 후 추가 단계가 필요합니다. 아래의 **기술 진화** 섹션을 참조하십시오.

* 정리 워크플로우가 향상되었습니다. 이제 삭제된 모든 워크플로우의 분리된 작업 테이블도 정리 워크플로우에 의해 자동으로 삭제됩니다. [자세히 알아보기](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances)

* 이제 푸시 알림을 전송하기 전에 iOS HTTP2 커넥터를 사용하는 iOS 모바일 애플리케이션에 대한 인증서의 유효성을 검사하여 인증서 만료로 인해 게재의 실패를 방지합니다.

* HTTP 프록시 연결 관리가 개선되었습니다. [자세히 알아보기](../../installation/using/file-res-management.md)

* 제한 후 실행을 중지하는 **[!UICONTROL Javascript Code]** 및 **[!UICONTROL Advanced Javascript Code]** 워크플로우 활동의 새 옵션입니다. 기본값은 1시간입니다. [자세히 알아보기](../../workflow/using/sql-code-and-javascript-code.md#javascript-code)

**기타 변경 사항**

* 레거시 SMS 커넥터는 이제 사용되지 않습니다. [사용되지 않는 기능 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

* 더 이상 자체 리트머스 계정을 사용하여 Adobe Campaign에서 받은 편지함 렌더링을 프로비저닝하고 사용할 수 없습니다. [자세히 알아보기](../../delivery/using/inbox-rendering.md)

* 뷰를 폴더와 구분하기 위해 뷰 이름의 색상이 짙은 파란색에서 어두운 녹청색으로 변경되었습니다. [자세한 내용](../../platform/using/access-management-folders.md)

* 이제 Campaign Classic을 영국, 인도 및 캐나다 지역에서 호스팅되는 Microsoft Dynamics CRM 계정에 연결할 수 있습니다. 이는 Office 365 및 온-프레미스(Dynamics 2015) 배포 유형에 적용됩니다.

* 이제 Campaign에서 TLS 확인을 수행하여 서버의 호스트 이름이 제공된 인증서의 호스트 이름과 일치하는지 확인합니다.

* 이제 게재 및 추적 통계 표에는 게재 수신자당 하나의 항목이 아니라 SMS 채널에 대해 게재당 하나의 항목이 표시됩니다.

* 다운로드한 파일이 디스크 공간보다 클 때 사용자에게 경고하기 위해 로그 파일에 오류 메시지가 추가되었습니다.

* 이제 Snowflake 커넥터에 다음 기능을 사용할 수 있습니다. MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**기술 진화**

이 새로운 빌드는 공유 메모리를 업데이트하며 업그레이드를 수행하는 추가 단계가 필요합니다. Campaign 관리자는 메모리 세그먼트를 제거해야 합니다. 이전 세그먼트로 인해 nlserver/nlsrvmod가 시작되지 않게 되므로 이러한 단계는 필수입니다.

Windows에서는 시스템을 다시 시작해야 합니다.

Debian/CentOs에서 공유 메모리 삭제가 필요합니다. 다음은 단계입니다.

업그레이드 전에 다음 단계를 수행해야 합니다.

1. 실행 중인 경우 apache2(CentOS의 http2) 서비스를 중지합니다.
1. 실행 중인 경우 nlserver(이전 빌드의 경우 nlserver6) 서비스를 중지합니다.

업그레이드 후:

1. 버전이 현재 버전보다 오래된 경우 **ipcrm** 명령을 사용하여 공유 메모리를 제거합니다.
1. 실행 중인 경우 nlserver 서비스를 시작합니다.
1. 실행 중인 경우 Apache2서비스를 시작합니다.

다음은 Debian의 명령줄입니다.

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Linux의 예는 이 [페이지](../../configuration/using/additional-parameters.md#redirection-server-configuration)에서 확인할 수 있습니다.

**패치**

* 정리 워크플로우 로그에서 사소한 회귀 문제를 해결했습니다.
* WSDL 파일을 구문 분석할 때 워크플로우 **로딩(SOAP)** 활동의 문제를 해결했습니다.
* 많은 수의 워크플로우를 효율적으로 처리하기 위해 **설문 조사** 활동을 사용하여 많은 워크플로우를 업그레이드할 때 오류가 발생하는 문제를 해결했습니다.
* 향상된 MTA에서 inMail 메시지를 처리하는 동안 일시적인 연결 문제를 해결했습니다. (NEO-20380)
* HTML에서 이미지가 100% 폭으로 표시될 때 핫 클릭 비율이 제대로 표시되지 않는 문제를 해결했습니다. (NEO-23203)
* 게재 조건부 콘텐츠가 핫 클릭 보고서에 완전히 표시되지 않는 문제를 해결했습니다. (NEO-18729)
* 반복 게재를 보내는 워크플로우를 다시 시작할 때 대상 승인 단계를 건너뛰던 문제를 해결했습니다. (NEO-18166)
* 워크플로우에서 오류를 수정한 후 **메시지 다시 시작 준비** 단추가 게재를 다시 시작하지 못하는 문제를 해결했습니다. (NEO-13488)
* 대상이 일본어 전자 메일 형식에 수신자를 포함하는 램프 업 단계 중에 중간 소싱 모드에서 게재가 실패할 수 있는 문제를 해결했습니다. (NEO-23846)
* Snowflake 커넥터의 표준 시간대 변환 문제를 해결했습니다.(NEO-20105).
* SSL을 통해 FTP를 사용하는 외부 계정 문제를 해결했습니다. (NEO-20498)
* 라인 게재에서 이미지가 표시되지 않는 문제를 해결했습니다. (NEO-23207)
* 오퍼를 게시할 때 오류가 발생하던 문제를 해결했습니다. (NEO-23312)
* 인증서가 만료된 경우에도 모바일 애플리케이션에서 테스트 연결이 작동되도록 허용하는 푸시 알림 문제를 해결했습니다. (NEO-22991)
* 높은 빈도로 전송할 때 푸시 알림에 영향을 줄 수 있는 문제를 해결했습니다. (NEO-20516)
* 추적 로그가 기록하지 않았음에도 불구하고 추적 데이터에 중복 항목이 포함되는 문제를 해결했습니다. (NEO-20040)
* 추적 서버 통신 오류가 해결된 후 중복 트랜잭션 전자 메일이 전송되던 문제를 해결했습니다. (NEO-23640)
* 추적 URL에서 리디렉션할 때 인코딩 매개 변수 값을 삭제한 문제를 해결했습니다(일본어 문자에 영향을 미침). (NEO-25637)
* 부동 소수를 비교할 때 쿼리가 작동하지 않던 문제를 해결했습니다. (NEO-23243)
* 워크플로우를 다시 시작한 후 **수정한 사람** 열 콘텐츠가 표시되지 않는 문제를 해결했습니다. (NEO-23035)
* 두 번째 컨테이너에서 로그를 다운로드할 때 추적 기술 워크플로우가 실패하는 문제를 해결했습니다. (NEO-23159)
* **보강** 활동을 실행할 때 워크플로우가 실패할 수 있는 문제를 해결했습니다. (NEO-17338)
* null 또는 음수 값을 입력할 수 없도록 **중복 제거** 워크플로우 활동 내 **Double 유지** 필드에 확인이 추가되었습니다.
* 시간 및 분이 언급되지 않도록 반복 캠페인에서 **스케줄러 마법사**&#x200B;를 제거했습니다. 날짜만 고려합니다.
* **스크립트** 워크플로우 활동의 **스크립트로 계산됨 옵션**&#x200B;을 통해 게재를 만들 때 추가 스토리지 필드의 문제를 해결했습니다. (NEO-20609)
* 데이터베이스 정리 작업 내에서 유령 워크플로우가 삭제되지 않는 문제를 해결했습니다.
* **청구(활성 프로필)** 기술 워크플로우가 실패하는 문제를 해결했습니다. (NEO-19777)
* ACS 커넥터 기능을 사용할 때 Campaign Standard 인스턴스에 연결할 수 없는 회귀 문제를 해결했습니다(FOH/FOH2 연결의 잘못된 관리). (NEO-23433)
* Hadoop 테이블이 있는 열이 여러 개인 기본 키에 스키마 확장을 만들 수 없는 문제를 해결했습니다. (NEO-17390)
* WSDL 파일이 URL에서 로드되지 않도록 하는 **로딩 (SOAP)** 활동의 문제를 해결했습니다. (NEO-16924)
* 여러 활성 워크플로우 서버가 부하 분산을 했을 때 콘솔을 통해 **무조건적 정지**&#x200B;를 수행하지 못하는 문제를 해결했습니다. (NEO-19556)
* 정리 워크플로우가 충돌하는 회귀 문제를 해결했습니다.
* 실행 인스턴스에 템플릿을 게시할 때 발생할 수 있는 문제를 해결했습니다.
* collectPrivacyRequests 기술 워크플로우가 실행되지 않는 문제를 해결했습니다. (NEO-20513, NEO-25169)
* 빌드 9080으로 업그레이드한 후 Audience Manager에 연결하려고 할 때 발생할 수 있는 문제를 해결했습니다. (NEO-20511, NEO-25167)
* 보고서를 PDF 또는 XLS 형식으로 내보낼 때 발생하는 문제를 해결했습니다. (NEO-20982, NEO-23493, NEO-23348)
* 전송 후 게재 목록에 게재를 두 번 표시할 수 있는 문제를 해결했습니다.
* 중간 소싱을 통해 게재를 전송하도록 라우팅 구성을 설정할 때 발생할 수 있는 게재 준비 문제를 해결했습니다.
* 라인 메시지 내에서 웹 애플리케이션 링크를 클릭할 때 오류 메시지가 표시되는 문제를 해결했습니다.
* 정리 워크플로우를 실행한 후 **증분 쿼리** 활동 내역을 삭제하는 문제를 해결했습니다.
* 중간 소싱 외부 계정을 만들 때 NmsMidSourcing_LastBroadLog_&lt;InternalName> 옵션이 누락되는 문제를 해결했습니다..
* 데이터베이스 인코딩 문제로 웹 서버가 지속적으로 다시 시작되는 데이터베이스 연결의 회귀 문제를 해결했습니다. 이는 과소비를 야기할 수 있습니다. (NEO-23264)


## 릴리스 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) 릴리스 20.1.4 - 빌드 9126 {#release-20-1-4-build-9126}

_2021년 4월 15일_

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2021년 3월 22일_

* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453, NEO-31454)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2020년 12월 23일_

>[!CAUTION]
>
> * 이 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Adobe IMS(ID 관리 서비스)를 통해 Campaign에 연결할 경우, **2021년 6월 30일** 이후부터 Campaign 서버 및 클라이언트 콘솔은 Campaign에 연결할 수 있도록 업그레이드를 해야 합니다. [자세히 알아보기](../../technotes/using/ims-updates.md)
>
> * 이 릴리스는 [보안 픽스](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.

* 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다.
* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)

### ![](assets/do-not-localize/red_2.png) 릴리스 20.1.3 - 빌드 9124{#release-20-1-3-build-9124}

_2020년 5월 6일_

* SFTP 키 기반 인증이 Debian 9에서 작동하지 않는 **파일 전송** 활동 문제를 해결했습니다. (NEO-23183)

### ![](assets/do-not-localize/red_2.png) 릴리스 20.1.2 - 빌드 9123{#release-20-1-2-build-9123}

_2020년 3월 13일_

* Red Hat 7 서버에 버전을 배포하지 못하는 문제를 해결했습니다. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) 릴리스 20.1 - 빌드 9122{#release-20-1-build-9122}

_2020년 2월 17일_

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA 커넥터</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake은 스토리지와 컴퓨팅 수준 모두에서 확장할 수 있도록 구축된 완전히 관리되는 클라우드 데이터 웨어하우스입니다. 이 새로운 커넥터를 통해 Adobe Campaign은 이제 강력한 Snowflake 기능을 활용하여 빅 데이터 세분화를 수행할 수 있습니다. 이 커넥터는 Adobe에서 호스팅하는 것을 포함하여 모든 고객이 사용할 수 있습니다.</p>
    <p>자세한 내용은 <a href="../../installation/using/configure-fda-snowflake.md">자세한 설명서</a> 및 <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">튜토리얼 비디오</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Hadoop FDA 커넥터 개선 사항</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>hadoop FDA 커넥터가 Cloudera와 Hadoop 3.0을 지원하도록 개선되었습니다.</p>
    <p>자세한 내용은 <a href="../../installation/using/configure-fda-hadoop.md">세부 설명서</a>를 참조하세요.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 클릭재킹으로부터 보호하기 위해 보고서 구성의 보안이 개선되었습니다. 이는 새 보고서에 적용됩니다. 이전 보고서의 경우 변경 사항을 적용하려면 이전 보고서를 다시 게시해야 합니다. (NEO-13282)

* cryptString의 작은 메모리 문제를 해결합니다. (NEO-20071)

* 내부 IP 공개를 수정하기 위해 모니터 JSP가 개선되었습니다. (NEO-16821)

* 관리자가 아닌 사용자에게 스택 추적 정보를 표시할 수 있는 문제를 해결했습니다. (NEO-12388)

* 이전 세션에서 캐시된 데이터의 관리를 개선했습니다. (NEO-17039)

* logins.log 파일이 IMS를 통해 성공한 로그인 시도를 기록할 수 없는 문제를 해결했습니다. (NEO-11004)

**개선 사항**

* iOS 13은 이제 HTTP2 커넥터에서 지원됩니다.

* 푸시 알림 기능(nms:address 및 nms:appSubscriptionRcp)에서 사용하는 테이블의 격리 관리 및 정리 기능이 개선되었습니다. iOS(HTTP2 커넥터만 해당)의 경우 이제 비활성화된 토큰이 Android와 동일한 방식으로 처리됩니다. 이제 비활성화 플래그가 NmsAppSubscriptionRcp 테이블에 설정됩니다. [자세히 보기](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* 에 새 옵션이 추가되었습니다. **JavaScript 코드** 및 **고급 JavaScript 코드** 워크플로우 활동을 통해 시간 초과 기간을 정의할 수 있습니다. 이렇게 하면 JavaScript 실행 단계가 너무 오래 실행되지 않습니다. 시간 초과 기간이 경과하면 워크플로우가 중지됩니다. 기본 시간 제한은 1시간입니다. [자세히 보기](../../workflow/using/sql-code-and-javascript-code.md)

* 이제 중간 소싱 서버에서 일치하는 선호도를 찾을 수 없으면 게재 분석이 중지되며, 해당 오류 메시지가 표시됩니다.

* 이제 Postgres에 대한 데이터베이스 장애 조치가 지원됩니다. 데이터베이스 서버가 충돌하고 다시 시작할 때 Campaign이 이제 데이터베이스 서버에 자동으로 다시 연결합니다.

* 다음 **시작 보류 중** 보기가 관리 > 감사 > 워크플로우 상태 노드에 추가되었습니다. 이렇게 하면 의 시작을 기다리는 인스턴스의 모든 워크플로를 모니터링할 수 있습니다. **operationManager** 프로세스. 이 보기는 마케팅 캠페인 패키지와 함께 제공됩니다. [자세히 표시](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**기타 변경 사항**

* Linux에서 이제 nlserver 서비스 시작은 /etc/init.d/nlserver6 스크립트 대신 시스템 단위를 사용합니다. 20.1 패키지를 설치하면 새 시작 구성표로의 마이그레이션이 자동으로 수행됩니다. /etc/init.d/nlserver6는 계속 제공되지만 nlserver 서비스(시작, 재시작, 중지 등)와 상호 작용하려면 systemctl 명령을 직접 사용하는 것이 좋습니다.

* 가장 자주 사용하는 사용자 지정 테이블이에서 이동되었습니다. **xtkNewId** 전용 시퀀스에 대한 시퀀스.

* 불필요한 데이터베이스 연결의 영향을 받을 수 있는 쿼리 성능이 개선되었습니다.

* 응답 시간을 최적화하기 위해 더 적은 SQL 문을 만들 수 있도록 데이터베이스 업데이트 마법사의 성능이 향상되었습니다.

* 데이터베이스 레코드 관리가 향상되었습니다.

* 연결 풀의 견고성이 개선되어 예기치 않은 연결 오류가 너무 자주 발생하는 것을 방지할 수 있습니다.

* 소프트 오류가 발생한 경우 격리할 주소를 보내는 이메일 주소 유효성 검사 규칙이 개선되었습니다. [자세히 보기](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* 이제 Debian의 경우 Campaign은 시스템 PCRE 라이브러리가 있는 경우 이를 사용합니다.

* 이제 Campaign에서 최신 시스템 ODBC 라이브러리를 사용할 수 있습니다.

* 연결을 열어 리치 이미지를 로드할 때 LINE 서블릿에 시간 초과가 추가되었습니다. 이미지를 로드하는 데 시간이 너무 오래 걸리는 경우 서블릿이 병목 현상을 방지하기 위해 연결을 중지합니다.

**패치**

* hadoop 커넥터를 사용할 때 계정 키 암호화 문제를 해결했습니다.

* Windows 서버에서 사용자 연결이 실패하는 SSL 인증 구현으로 인한 회귀 문제를 해결했습니다. (NEO-20629)

* 음수 워크플로우 ID의 경우 증분 쿼리 활동 문제를 해결했습니다. (NEO-19779)

* netezza FDA 커넥터를 통해 쿼리를 실행할 때 발생하는 인코딩 문제를 해결했습니다. (NEO-19594)

* 에서 POST 방법을 사용할 때 오류가 발생하는 문제를 해결했습니다. **웹 다운로드** 워크플로우 이벤트 활동.

* 오퍼 제안 생성 관련 문제가 해결되었습니다. (NEO-18176)

* 획득 웹 양식 템플릿을 사용할 때 바닥글 표시 문제를 수정했습니다.

* 연속 게재 콘텐츠의 URL을 구문 분석할 때 충돌할 수 있는 문제를 해결했습니다. (NEO-16910)

* 의 문제가 해결되었습니다. **시작** 및 **종료** 새 캠페인을 만들 때 필드가 계산되지 않습니다.

* 의 문제가 해결되었습니다. **파일 다운로드** url을 사용할 때의 워크플로우 활동입니다.

* 보고서의 쿼리 활동에서 가져온 목록을 미리 볼 때 발생하는 문제를 수정했습니다. (NEO-13119)

* 을(를) 선택할 때 오래된 이미지가 표시되는 문제를 해결했습니다. **Campaign 제공** 이메일 편집기의 개인화 블록.

* 클라이언트와 서버 간의 네트워크 통신이 개선되었습니다.

* 동일한 캠페인에서 너무 많은 워크플로우가 만들어지는 문제를 해결했습니다. 이제 28개 이상의 워크플로우를 만들 수 없습니다. 경고가 표시됩니다.

* 을(를) 사용할 때 발생하는 문제를 해결했습니다. **열 선택** 의 조정 옵션 **합집합** 워크플로우 활동.

* 워크플로우에서 손상된 데이터 보강 목록을 사용할 때 발생할 수 있는 콘솔 충돌 문제를 수정했습니다. (NEO-18096)

* 워크플로우에서 발생할 수 있는 다양한 콘솔 충돌 문제를 해결했습니다(NEO-18010, NEO-18032).

* 을(를) 실행할 수 있는 문제를 해결했습니다. **외부 신호** 비활성화된 경우에도 워크플로우 활동. (NEO-17524)

* 새 스키마를 만들 때 발생하는 문제를 해결했습니다.

* SMS 메시지를 보낼 때 발생하는 추적 문제를 수정했습니다. (NEO-19595)

* 게재 표시기에서 잘못된 타겟팅된 대상 번호를 표시하는 문제를 해결했습니다.

* 워크플로우 활동을 통해 설명 보고서를 생성할 때 잘못된 백분율을 표시하는 문제를 해결했습니다. (NEO-14314)

* 시간 보기 매개 변수 시 게재 처리량 보고서의 숫자가 다르게 표시되는 문제를 수정했습니다. (NEO-11783)

* 추적 워크플로우에서 트랜잭션 메시지 추적 지표를 업데이트하지 못하는 문제를 해결했습니다. (NEO-17770)

* SOAP를 통해 오퍼를 요청할 때 웹 프로세스가 충돌하고 다시 시작되는 회귀 문제를 해결했습니다. (NEO-19482)

* 업로드 디렉터리가 원격 공유 위치인 경우 데이터를 공개 리소스에 업로드할 수 없는 문제를 해결했습니다. (NEO-19361)

* 의 원인이 되는 문제가 해결되었습니다. **Adobe Experience Cloud에서 대상자 가져오기** 기술 워크플로우 tp가 지속적으로 실패합니다. (NEO-18463)

* Experience Manager에서 가져온 템플릿을 사용할 때 게재를 보낼 수 없는 문제를 해결했습니다. (NEO-17540)

* 빌드 9032로 업그레이드하여 인스턴스가 SSL 프로토콜을 통해 FTP 서버에 연결할 수 없는 후 발생하는 문제를 해결했습니다. (NEO-20498)

* 에서 대량의 데이터를 삭제, 삽입 또는 업데이트할 때 발생하는 문제를 수정했습니다. **데이터 업데이트** 타겟팅 차원으로 FDA 스키마를 사용하는 워크플로우의 활동. (NEO-13280)

* HTML 컨텐츠 태그 외부에 Javascript 코드가 있을 때 이메일이 전송되지 않는 문제를 수정했습니다. (NEO-18628)

* 보낸 메시지의 게재 로그에서 미러 페이지를 표시하려고 할 때 발생하는 문제를 해결했습니다. (NEO-17976)

* 을(를) 방해하는 문제가 해결되었습니다. **미러 페이지 링크** 에 표시되는 개인화 블록 **텍스트 컨텐츠** 클릭 후 탭 **가져오기 HTML** 게재 중. (NEO-17568)

* 만료된 미러 페이지 링크를 클릭할 때 표시되는 오류 메시지가 명확해졌습니다. (NEO-17340)

* 에서 일부 버튼을 사용할 수 없는 문제를 해결했습니다. **데이터 배포** 만들기 화면입니다.

* 아시아/콜카타를 시간대로 하는 인스턴스에서 게재 활동을 예약할 때 발생하는 문제를 해결했습니다. (NEO-20001)

* 이제 게재에 선호도 구성 문제가 있는 경우 오류가 표시됩니다.

* 에서 잘못된 버전 태그 번호를 표시하는 문제를 해결했습니다. **정보** 메뉴 아래의 제품에서 사용할 수 있습니다.

* 워크플로우에서 반복 게재의 속성에서 라우팅 계정을 업데이트하려고 할 때 발생하는 문제를 해결했습니다. (NEO-18684)

* 리디렉션 모듈을 통해 인스턴스에 연결할 때 종료된 후 연결이 제대로 정리되지 않는 문제를 해결했습니다.
