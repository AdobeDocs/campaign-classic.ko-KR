---
title: 최신 릴리스
description: 최신 Campaign Classic 릴리스 노트
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 3%

---


# 최신 릴리스{#latest-release}

이 페이지에는 **최신 Campaign Classic 릴리스 후보 버전에 포함된 새로운 기능, 개선 사항 및 수정 사항이 나와 있습니다**.

Campaign Classic Gold Standard 버전(최신 GA 빌드)의 경우 이 페이지를 [참조하십시오](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) 릴리스 20.3.1 - 빌드 9228 {#release-20-3-1-build-9228}

_2020년 10월 27일_

**새로운 기능**

<table> 
<thead>
<tr> 
<th> <strong>iOS 푸시 알림 개선</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>모바일 앱을 Campaign과 통합할 때 Apple 푸시 알림 서비스(APNs)와의 통신 보안을 유지해야 합니다. 인증서 기반 인증 또는 토큰 기반 인증을 사용할 수 있습니다.
</p>
<p>이제 Campaign Classic의 iOS 모바일 앱에서 다음 두 가지 인증 모드를 사용할 수 있습니다.
</p>
<ul> 
<li><p>토큰 기반 인증(권장):이 인증 모드는 .p8 파일을 기반으로 합니다. APNs에 대한 각 요청에 토큰이 포함되어 있으므로 이 인증 모드가 더 빠릅니다. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">자세히 알아보기</a></p></li>
<li><p>인증서 기반 인증:이 인증 모드는 .p12 파일을 기반으로 합니다. 모든 앱에 대해 별도의 인증서가 필요합니다. 이 인증서는 개발자 계정을 통해 Apple에서 제공합니다. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">자세히 알아보기</a></p></li> 
</ul>
<p>자세한 설명서에서 Campaign에서 인증 모드를 선택하는 방법을 <a href="../../delivery/using/configuring-the-mobile-application.md">알아봅니다</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>향상된 Android 푸시 알림</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Android 푸시 채널 인증을 위한 FCM HTTP v1 API를 지원하도록 Android 푸시 알림이 개선되었습니다. </p>
<p>새롭게 지원되는 API 버전을 사용하면 향상된 리치 푸시 메시지 기능을 제공하는 FCM 알림 메시지를 전송할 수 있습니다. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">자세히 알아보기</a></p> 
<p>Adobe Campaign에서 Android용 FCM HTTP v1 API를 구성하는 방법 <a href="../../delivery/using/configuring-the-mobile-application-android.md">을 살펴보십시오</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**향상된 보안 기능**

* 라이브러리의 안전한 로드:이제 DLL 사전 로드 공격으로부터 보호하기 위해 Campaign 클라이언트(클라이언트)를 로드하는 동안 Windows 기본 시스템 DLL 경로에서만 Windows DLL이 로드됩니다. [자세한](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) 내용(NEO-24147)
* SSRF(Server Side Request 위조) 공격으로부터 보호를 강화하려는 보안 문제가 해결되었습니다. (NEO-25661)
* 받는 사람 테이블에 대한 두 번째 수준 관계가 있는 사용자 지정 테이블에서 레코드가 삭제되지 않는 GDPR 개인 정보 요청을 처리하는 동안 발생하는 문제를 수정했습니다. (NEO-25967)
* Adobe Experience Manager 템플릿을 동기화하려고 할 때 관리자가 아닌 사용자가 API 호출을 사용하는 보안 문제가 해결되었습니다. (NEO-23487)

**호환성 업데이트**

이제 다음 시스템이 Campaign에서 지원됩니다.
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**사용되지 않는 기능**

다음 기능은 20.3에서 더 이상 사용되지 않습니다.

* 대상을 Adobe Experience Cloud으로 가져오고 내보내는 데 사용되는 demdex 도메인은 더 이상 사용되지 않습니다. 외부 계정 가져오기/내보내기에 demdex 도메인을 사용하는 경우 그에 따라 구현을 조정해야 합니다. [자세히 알아보기](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* oAUTH 인증 설정을 기반으로 한 트리거 통합 인증이 변경되었으며 Adobe I/O로 이동되었습니다. [자세한 내용](../../integrations/using/about-triggers.md)

더 자세한 내용은 [더 이상 사용되지 않는 기능 및 제거된 기능 페이지를 참조하십시오](../../rn/using/deprecated-features.md).

**개선 사항**

* 클라이언트 **콘솔에 몇 가지 기능이 개선되었습니다**.
   * 일부 인터넷 보안 GPO 규칙 제한 사항과 비호환되지 않도록 하기 위해 캠페인 클라이언트 콘솔 로그온 화면이 기본 제공 표준 Windows 양식으로 대체되었습니다.
   * 워크플로우에서 64비트 클라이언트 콘솔을 사용하여 활동을 복사/붙여넣을 때 발생하는 문제를 수정했습니다. (NEO-27635)
   * [ **정보** ] 메뉴에서 64비트 및 32비트 콘솔을 구분하는 정보가 추가되었습니다.
* 이제 워크플로우를 다시 시작할 때 워크플로우 식별자가 로그에 표시되므로 다시 시작된 워크플로우를 보다 잘 식별할 수 있습니다.
* 새로운 영구 쿠키가 도입되었습니다.nllastdelid 이 쿠키(UUID230 제외)는 deliveryId를 저장합니다. 세션 쿠키가 없으면 이 쿠키에 있는 deliveryId에서 브로드로그 정보를 가져옵니다.
이 변경 사항은 브라우저 세션이 종료될 때 발생하는 문제를 해결합니다.deliveryId 및 broadlogId가 포함된 세션 쿠키가 삭제되었습니다. deliveryId가 없으면 브로드로그 정보를 찾을 수 없으며 영구 추적(마지막 배달)의 경우 추적 테이블 정보가 누락됩니다.
쿠키에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../platform/using/privacy-and-recommendations.md#cookies).
* 배달 전송 전에 MTA 프로세스를 다시 시작하여 배달 가능 서버를 통해 대량 배달 처리량 성능을 개선했습니다.

**기타 변경 사항**

* SFTP에 상대 경로를 사용할 때 문자가 `~/` 더 이상 자동으로 추가되지 않습니다. 필요한 경우 경로에 `~/` 문자를 수동으로 추가할 수 있지만 **절대 경로를 사용하는 것이 좋습니다**.
* Microsoft SQL Server로 새 데이터베이스를 구성할 때 사용 가능한 인증 방법에서 Windows NT 인증이 제거되었습니다. [자세한 내용](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* 데이터베이스 정리 워크플로우는 성능을 개선하기 위해 Teradata에 맞게 최적화되었습니다. (NEO-19959)
* Adobe Target에서 이미지를 삽입할 때 표시되는 오류 메시지가 개선되었으며 테넌트 이름이 외부 계정에서 비어 있었습니다.
* 배달 속성에서 옵션 **[!UICONTROL Archive emails]** 이름이 변경되었습니다 **[!UICONTROL Email BCC]**.
* 견고성을 향상시키려면 노드가 잘못된 모든 쿼리가 거부됩니다. 검사를 비활성화하고 이전 동작으로 돌아가야 하는 경우 XtkSecurity_Disable_QueryCheck를 0으로 설정할 수 있습니다.

**기술 진화**

Tomcat이 버전 7(7.0.103)에서 버전 8(8.5.57)로 업데이트되었습니다.

디렉토리 `tomcat-7` 가 `tomcat-8` 디렉터리로 대체됩니다.

Windows의 경우 _이전에 사용되지 않은 디렉토리_ 에 _iis_neolane_setup.vbs_ 및 `conf` apache_neolane.conf가 `tomcat-7/conf` 설치됩니다.

linux에서 _apache_neolane.conf_ 가 이제 `conf` 디렉토리에 설치됩니다.

**패치**

* 배달 통계가 다시 계산되지 않도록 하는 문제를 해결했습니다.
* 이전 빌드를 사용하여 서버에 연결된 Campaign Classic 9080 빌드를 사용할 때 CSV 파일을 업로드할 때 오류 메시지가 표시되는 문제를 해결했습니다. (NEO-23218)
* 외부 계정에 대해 Microsoft Dynamics CRM 마법사를 구성할 때 오류 메시지를 표시하는 문제를 해결했습니다. 이는 최신 MS Dynamics CRM API 버전과의 호환성 문제 때문입니다. (NEO-24528)
* CRM 커넥터를 사용하여 검색 형식 레코드(다른 테이블과 연결된 외래 키 레코드로 구성된 데이터)를 Campaign Classic에서 Microsoft Dynamics로 내보낼 수 없는 문제를 해결했습니다. (NEO-23864)
* CRM 커넥터에서 [ **자동 색인** ] 옵션을 활성화한 경우 Microsoft Dynamics 데이터를 가져올 수 없는 문제를 해결했습니다. (NEO-25981)
* 연결이 종료된 경우에도 열려 있을 수 있는 IMS 인증 문제가 해결되었습니다. 연결이 누적되고 시스템 리소스가 소모되는 것을 방지하기 위해 이제 연결이 종료되는 즉시 자동으로 닫힙니다. (NEO-25996)
* 외부 계정의 잘못된 구성(잘못된 계정 또는 암호)으로 인해 배달에 대한 Adobe Experience Manager 컨텐츠 동기화가 실패할 때 오류 메시지가 표시되지 않는 문제를 해결했습니다. 이제 실패 시 메시지가 표시되므로 문제를 보다 쉽게 식별할 수 있습니다. (NEO-25586)
* 데이터 **업데이트 활동에서** 업데이트 **작업 유형을 선택할 때 발생하는 문제를** 수정했습니다. 업데이트할 데이터가 올바르지 않으면 워크플로우는 오류가 발생하여 실패합니다. 데이터가 잘못된 경우 워크플로우는 실패하지 않으며 레코드는 **거부 아웃바운드 전환** 에 저장됩니다. (NEO-23794)
* 하위 워크플로가 포함된 워크플로우가 작동하지 않는 문제를 해결했습니다. (NEO-24036)
* 기호 복사(예: 일본어 문자)를 붙여넣을 때 **저장** 단추가 표시되지 않는 캠페인 템플릿 설명을 편집할 때 발생하는 문제를 수정했습니다. (NEO-27071)
* 인스턴스 구성 마법사에서 추적 서버를 변경할 수 없는 문제를 수정했습니다.
* [ **저장** ] 단추를 클릭하기 전에 창 외부를 클릭할 때 캠페인 또는 캠페인 템플릿의 설명이 저장되지 않는 문제를 해결했습니다. (NEO-27449)
* 활성 청구 프로필 **** 수(billingActiveContactCount) 기술 워크플로우가 작동하지 않는 문제를 해결했습니다. 스키마 확장의 계산된 필드에서 링크가 수행된 경우 이 문제가 발생할 수 있습니다. 많은 양의 데이터가 생성되었으며, 이로 인해 데이터베이스가 임시 공간이 부족해질 수 있습니다. (NEO-24062)
* 텍스트 및 csv 파일의 일본어 문자를 파일 끝에 **배치하면 가져올 수 없는** 데이터 로드(파일)작업 문제를 수정했습니다. (NEO-24957)
* 분석 시작 **및** 분석 완료 **** 필드가 올바로 채워지지 않도록 하는 연속 배달 문제를 수정했습니다. (NEO-20755)
* 받는 사람(nms:recipient)이 아닌 다른 스키마에서 쿼리 후에 SMS 메시지를 미리 볼 때 오류 메시지 **를** 표시하는 문제를 해결했습니다. (NEO-27517)
* Snowflake FDA 커넥터를 사용할 때 발생하는 문제가 해결되었습니다. Snowflake FDA 액세스 이름 권한이 있는 사용자가 Snowflake 스키마에 대한 쿼리를 실행할 수 없습니다. 로그에 &quot;암호를 찾을 수 없음&quot; 유형의 오류가 표시되었습니다. (NEO-23851)
* 연결된 FDA 스키마 이름이 현재 스키마의 요소 이름의 하위 문자열에서 발생하던 FDA 커넥터를 사용하는 경우 발생하는 문제가 해결되었습니다. 예를 들어 FDA 스키마가 &quot;cust&quot;이고 수신자 스키마 내의 요소 중 하나가 &quot;고객&quot;인 경우 이러한 문제가 발생했습니다. &quot;customer&quot; 요소 내에서 열을 가져오고 &quot;cust&quot; FDA 스키마에서 열을 추가할 때 로컬 열에 대한 값이 누락되었습니다. (NEO-20193)
* 외부 데이터베이스에서 레코드를 가져와 캠페인 데이터베이스에 삽입할 때의 워크플로우 문제를 해결했습니다. (NEO-26359)
* 업데이트 이벤트 상태 **기술 워크플로우의** 문제를 수정했습니다.배달 통계 **활동에서 들어오는 해당 필드의 크기 조정을 일치시키기 위해** 업데이트 배달 통계 **** 활동에서 3개의 대상 필드 크기가 32비트에서 64비트로 변경되었습니다. (NEO-11557) **이 섹션에서 이벤트 상태** 업데이트 워크플로우에 대한 자세한 내용을 [살펴보십시오](../../workflow/using/message-center--execution-.md).
* 필터를 적용하려고 할 때 **스크립트 오류가 발생하고 날짜 범위별로 필터를 사용할 수 없게 하는 메시지 센터 이벤트 내역** 보고서의 문제를 수정했습니다. (NEO-23365)
* 캠페인 작업 **(operationMgt)과** 미리 보기 **** (예측) 기술 워크플로우 간의 간섭 문제를 수정했습니다. 이 문제는 예약된 배달이 &quot;Target 준비&quot; 또는 &quot;배달될 준비가 됨&quot; 상태에 있을 때 발생했습니다. (NEO-20819)
* xtkOperator의 mdata 필드에 XML 식별자가 없을 때 XML 구문 분석 문제가 해결되었습니다. 업그레이드 후 오류가 발생했습니다. (NEO-26113)
* SSL에서 암호화된 Azure 외부 계정에 연결된 **파일 전송** 활동을 사용할 때 HTTPS 대신 HTTP로 연결이 되는 문제가 해결되었습니다. (NEO-26720)
* 정리 워크플로 중 up_updates 프로시저에서 오류가 발생할 수 있는 MSSQL 데이터베이스에 대한 문제를 수정했습니다.
* 상호 작용 요청이 계속 처리되는 경우 웹 프로세스 종료 중에 발생하는 충돌을 해결했습니다. (NEO-26447)
* Oracle DB의 **NoNull** 함수가 업그레이드 후 더 이상 작동하지 않던 문제를 수정했습니다. (NEO-26488)
* LINEV2 패키지가 메시지 센터 패키지 없이 설치된 경우 9171 업그레이드 후 추적 워크플로우가 실패하는 문제가 해결되었습니다.
* &#39;APP&#39; 특성에 대한 데이터베이스 연결 문자열이 잘못된 값을 얻음으로써 연결 풀이 원하는 연결 수로 증가하지 못하는 확장성 문제를 해결했습니다. (NEO-25105)
* 최신 Windows 10 업데이트 후 Adobe Campaign에 로그인할 수 없는 프록시 구성 수준의 문제를 수정했습니다. (NEO-27813)
* 추적 링크가 포함된 HTML 템플릿을 가져온 후 배달된 이메일에 원하지 않는 URL이 표시되는 문제를 해결했습니다. (NEO-25909)
* 워크플로에서 나머지 작업 중 나머지 부분의 대상 데이터를 표시할 때 서버가 **충돌하는** 문제를 해결했습니다.
* 식 구문 분석기를 지울 때 메모리 손상을 방지하여 서버 충돌 문제가 해결되었습니다. (NEO-26856)
* 관리자가 아닌 사용자가 인스턴스 변수를 정의했던 데이터 연계 강화 작업의 문제를 수정했습니다. (NEO-25653)