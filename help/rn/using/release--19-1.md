---
title: 릴리스 19.1
seo-title: 릴리스 19.1
description: 릴리스 19.1
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# 릴리스 19.1{#release-19-1}

## 릴리스 19.1.6 - 빌드 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>이 빌드는 온-프레미스 설치용입니다. 하이브리드 배포의 경우 호스팅된 인스턴스는 9032 빌드를 계속 실행합니다. 9032와 호환되지 않으므로 마케팅 인스턴스를 9035 빌드로 업그레이드하지 마십시오.

2019년 10월 3일

**향상된 기능**

* Salesforce용 CRM 커넥터를 사용할 때 발생하는 문제가 해결되었습니다. (NEO 파섹)
* 트랜잭션 메시지를 보낼 때 성능 문제가 발생할 수 있는 색인 문제를 수정했습니다.
* 메시지를 보낼 때 성능 문제가 수정되었습니다. (NEO 파섹
* Mid-Sourcing 서버에서 특정 메시지가 처리되지 않는 문제를 해결했습니다. (NEO 파섹)
* SQL 데이터 관리 작업의 전체 사용을 방해하는 문제를 수정했습니다(right라는 &quot;SQL 데이터 관리&quot;가 누락됨).

## 릴리스 19.1.5 - 빌드 9033{#release-19-1-5-build-9033}

2019년 8월 13일

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

**향상된 기능**

* 데이터 관리 작업의 데이터 추출 중에 FDA 데이터베이스가 아닌 기본 데이터베이스에서 실행된 SQL 문 &#39;SELECT COUNT&#39; 문제를 수정했습니다.
* 이제 고객 인프라 기능을 개선하기 위해 서버 구성 파일에서 SFTP 프록시 선언을 사용할 수 있습니다.
* 테이블 이름이 없는 데이터 로드(RDBMS) 워크플로우 활동에서 &quot;연결된 테이블을 추가&quot;할 때 클라이언트 콘솔 충돌이 해결되었습니다. (NEO 파섹
* 명령줄을 통해 midMeetter 패키지를 설치하는 문제를 수정했습니다.
* Microsoft Dynamics의 AC 커넥터 내에서 OAuth 자격 증명을 지원하기 위해 새로운 인증 옵션이 추가되었습니다. (NEO 파섹)
* UUID(고유 유니버설 식별자) 문제를 수정하면 Hive FDA에서 농축된 활동이 실패합니다.

## 릴리스 19.1.4 - 빌드 9032{#release-19-1-4-build-9032}

**2019년 12월 17일**:다음 수정 사항이 포함된 새 빌드(9032-9d34fb17e)를 참조하십시오.

* 다음 통신 채널에 대한 추적 문제를 수정했습니다.모바일(SMS, MMS), 푸시(iOS, Android) 및 소셜 네트워크(Facebook, Twitter).
(NEO 파섹)

**2019년 12월 11일**:다음과 같은 수정 사항이 포함된 새 빌드(9032-e28b428b7)가 포함되어 있습니다.

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

* MSSQL 데이터베이스를 사용하여 메시지를 전송할 때 성능 문제가 해결되었습니다. (NEO 파섹

**2019년 11월 20일**:다음 수정 사항이 포함된 새 빌드(9032-3468c7bb5)를 참조하십시오.

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

* IMS 인증을 통한 로그인 문제가 해결되었습니다. (NEO 파섹)
* 여러 게시에 누적 보고서를 표시할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 웹 서버 충돌을 차단하거나 차단할 수 있는 문제를 수정했습니다.

**2019년 9월 19일**:다음 수정 사항이 포함된 새 빌드(9032-cee805c93):

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

* Salesforce용 CRM 커넥터를 사용할 때 발생하는 문제가 해결되었습니다. (NEO 파섹)
* 트랜잭션 메시지를 보낼 때 성능 문제가 발생할 수 있는 색인 문제를 수정했습니다.

**2019년 8월 13일**:다음 수정 사항이 포함된 초기 19.1.4 빌드:

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

* 마법사 구성 중에 원하지 않는 오류 메시지를 생성하는 스케줄러 작업 문제를 수정했습니다. NEO 파섹 (NEO 파섹)
* 테스트 활동이 두 번 실행될 때 워크플로가 중지될 수 있는 NEO-12727에 의해 발생하는 회귀 문제를 수정했습니다. (NEO 파섹)
* API 호출에서 유효하지 않거나 만료된 세션 토큰이 사용된 경우 잘못된 HTTP 코드 반환(HTTP 403 금지 대신 HTTP 200 OK)이 발생하는 문제를 해결했습니다. (NEO 파섹)
* 더 이상 이메일에 포함되지 않아 배달 문제가 발생하는 DKIM 키 문제를 수정했습니다. (NEO 파섹)
* 워크플로우 예약과 관련된 다양한 문제를 수정했습니다. 워크플로우는 스케줄러 구성을 고려하지 않고 하루에 한 번 실행되도록 예약되었습니다. (NEO 파섹 16619, NEO 파섹 16426)

## 릴리스 19.1.2 - 빌드 9029{#release-19-1-2-build-9029}

2019년 6월 21일

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

**향상된 보안 기능**

* 보안을 최적화하기 위해 Java 라이브러리(Netty)가 최신 버전(4.1.34)으로 업데이트되었습니다. (NEO 파섹)

**향상된 기능**

* 특정 구성에서 이메일을 보내지 못하게 하는 도메인 열 관리에 연결된 회귀 문제를 해결했습니다.
* 성능을 개선하기 위해 _operation=&quot;none&quot; 속성이 &quot;SELECT FOR UPDATE&quot; 요청을 피하도록 rtEvent SOAP 호출에 추가되었습니다.
* 테스트 작업 후 아웃바운드 전환 관련 워크플로우 표시 문제를 수정했습니다. (NEO 파섹)
* 이제 가져오기 작업 과정 동안 Microsoft Dynamics에서 만든 더미 레코드를 삭제할 수 있습니다.
* 내부 계정을 사용할 때 보안 영역 패키지를 실행하기 위한 권한이 개선되었습니다.

## 릴리스 19.1 - 빌드 9026{#release-19-1-build-9026}

2019년 5월 30일

>[!CAUTION]
>
>이 건물은 회수되었습니다. 최신 빌드로 [업그레이드하거나](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 기술 지원에 [](https://support.neolane.net/)문의하십시오.

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> 기능<br /> </th> 
   <th> 설명<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 컨트롤 패널<br /> </td> 
   <td> <p>관리 사용자로서의 작업의 효율성을 높이려면 저장소 모니터링, 화이트리스트 IP 주소, 각 인스턴스에 대한 SSH 키 설치를 통해 SFTP 서버의 설정을 관리합니다. 제어판은 현재 AWS에서 호스팅된 고객에게만 제공됩니다(지금 Experience Cloud를 통해<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">로그인</a>).</p> <p>자세한 내용은 <a href="https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html">자세한 설명서</a> 및 <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">방법 비디오를</a>참조하십시오. </p><p>참고:제어판에 액세스하려면 최신 캠페인 빌드로 업그레이드할 필요가 없습니다.</p> </td> 
  </tr> 
    <tr> 
   <td> 감사 추적<br /> </td> 
   <td> <p>관리자는 Adobe Campaign Classic 인스턴스 내에서 수행된 변경 사항을 모니터링하고 관리하여 생산성을 높입니다. 감사 추적은 소스 스키마, 워크플로우 및 옵션에서 수행한 작업을 기록합니다. 요소가 만들어졌는지, 수정되었는지 또는 삭제되었는지 빠르게 확인할 수 있습니다.</p><p>자세한 내용은 <a href="../../production/using/audit-trail.md">자세한 설명서</a> 및 <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">방법 비디오를</a>참조하십시오.</p></td> 
  </tr> 
  <tr> 
   <td> 보안, 견고함 및 확장성<br /> </td> 
   <td> 일련의 개선 사항이 Campaign Classic에 추가되었습니다. 다음은 보안, 견고함 및 확장성 개선 사항입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 호환성 매트릭스 업데이트<br /> </td> 
   <td> 이제 Adobe Campaign이 이 새 버전을 사용하여 다음 데이터베이스 시스템을 지원합니다. 호환성 <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">매트릭스를 참조하십시오</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7(FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16(FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 보안상의 이유로 워크플로우 활동에서 **[!UICONTROL Pre-process the file]** **[!UICONTROL Data loading (file)]** 옵션을 사용할 때 임의의 명령을 더 이상 삽입할 수 없습니다. 이제 3가지 옵션 중에서 선택할 수 있는 드롭다운 목록을 사용할 수 있습니다. **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) 또는 **[!UICONTROL Decrypt]** (gpg). XtkSecurity_Disable_Preproc 보안 플래그가 추가되었습니다. 신규 고객의 경우 이 옵션이 0으로 설정됩니다. 기존 고객의 경우 이전 동작을 유지하기 위해 이 옵션이 업그레이드 후 1로 설정됩니다. 이 [섹션을](../../workflow/using/data-loading--file-.md)참조하십시오.
* 표준 시간대가 설정되지 않은 FDA 외부 계정의 연결을 테스트할 때 발생하는 암호 표시 문제를 수정했습니다.
* PDFBox 라이브러리가 제거되었습니다.
* Tomcat이 버전 7.0.93으로 업데이트되었습니다.
* 보안 토큰이 유효하지 않을 때 발생하는 토큰 가시성 문제를 해결했습니다.
* WSDL JSP(schemawsdl.jsp)의 잠재적 XTK 삽입 문제를 해결했습니다.
* 응용 프로그램의 소스 코드 및 메모리의 자격 증명 및 암호 저장소가 최적화되었습니다.
* PII 보기 제한이 최적화되었습니다. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* 비밀 키 관리의 불일치 문제가 해결되었습니다.
* 이제 유효한 사용자 이름 또는 잘못된 사용자 이름으로 실패한 로그인 시도에 대해 동일한 일반 오류가 표시됩니다.
* 업로드된 파일의 이름이 향상되었습니다.
* setEnv 및 getEnv 함수 사용을 차단하기 위해 새로운 XtkSecurity_Disable_GetSetEnv 옵션이 추가되었습니다.
* 이제 애플리케이션 스택 추적에 중요한 정보가 숨겨집니다.

**향상된 보안, 견고함 및 확장성**

* 수명 - XtkNewId 시퀀스 사용 최적화:xtkNewId 시퀀스에서 가장 많이 사용되는 테이블이 전용 시퀀스로 이동되었습니다. [자세한 내용](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* HTTP v2를 통한 FDA:http를 통한 FDA 프로토콜은 Hybrid 배포, 특히 broadLog 검색 및 전달 준비에 널리 사용됩니다. 데이터 검색 또는 푸시 시 네트워크 문제와 가능한 오류를 방지하기 위해 견고성이 향상되었습니다. 이렇게 하려면 연결의 양쪽 끝에서 빌드가 최신 버전이어야 하며, 그렇지 않으면 이전 프로토콜이 계속 사용됩니다.
* 추적 워크플로우:추적 워크플로우 견고성이 향상되었습니다. 추적 로그 삽입/업데이트 및 URL 추적 사용자 지정과 관련된 몇 가지 문제가 수정되었습니다. 또한 이제 추적 워크플로우는 오류를 발생시키고 워크플로우를 중지할 수 있는 추적 로그 문제를 감지합니다. 이제 이러한 문제는 무시되고 처리되지 않습니다.
* 정리 워크플로우:잠재적인 오류 및 중지를 방지하기 위해 정리 워크플로우가 개선되었습니다. 데이터베이스 크기와 성능을 최적화합니다.
* 트랜잭션 메시지에 포함된 이미지:트랜잭션 메시지에 포함된 이미지를 완벽하게 지원하므로 가능한 충돌 또는 누락된 이미지를 방지할 수 있습니다.
* 데이터베이스 크기 - XtkJobLog:이 표에 제거 메커니즘이 추가되었습니다. 이는 데이터베이스 크기에 긍정적인 영향을 줍니다.
* 숨은 참조 보관:bcc 보관에 대한 기본 매개 변수가 보관 속도를 향상하도록 변경되었습니다. [자세한 내용](../../installation/using/email-archiving.md#parameters)
* 데이터베이스 구조 업데이트:데이터베이스 구조 업데이트 마법사로 생성된 SQL 요청이 개선되어 보다 빠르게 실행되었습니다.
* 연산자 작업의 보장:이동통신사가 플랫폼의 무결성에 영향을 미칠 수 있는 작업을 수행하지 못하도록 몇 가지 보증서가 구현되었습니다. 기본 제공 스키마는 더 이상 인터페이스를 통해 삭제할 수 없습니다. 또한 워크플로우 소스 XML은 관리자가 아닌 사용자가 더 이상 편집할 수 없습니다.
* 두 가지 새로운 옵션을 사용할 수 있습니다.XtkSecurity_ **Restrict_EditXML** (게재 버전의 XML 코드 사용 안 함) 및 NmsOperation_OperationMgtDebug( **작업Mgt** 기술 워크플로우 실행을 모니터링할 수 있음). [자세한 내용](../../installation/using/configuring-campaign-options.md)

**기타 변경 사항**

* 푸시 알림:이제 iOS 푸시에 대한 스레드 ID 옵션을 지원합니다.
* 업그레이드 후 문제를 야기할 수 있는 긴 이름 인덱스의 관리를 개선했습니다.
* 이제 디컴파일 배달을 분석하는 동안 게시 모드가 배포 마법사로 설정되어 있으면 오류가 기록되고 분석이 중지됩니다. **[!UICONTROL None]** &quot;게시 모드가 &#39;없음&#39;으로 설정되어 있습니다.이미지를 포함할 수 없습니다. 기능폰에 이미지가 표시되지 않습니다.&quot; (NEO 파섹
* 트랜잭션 메시징에 대한 브로드캐스트 로그 관리가 향상되었습니다. 브로드로그가 실행 인스턴스에서 제어 인스턴스로 동기화되면 @lastModified 필드가 시스템의 현재 날짜로 업데이트됩니다. 제어 인스턴스에 대해 MC_Update_BlLastModified 옵션이 추가되었습니다. True는 현재 날짜가 제어 인스턴스(기본 동작)에 사용됨을 의미합니다. False는 실행 인스턴스 브로드로그의 @lastModified 날짜를 사용함을 의미합니다. (NEO 파섹)
* 배달 전송을 최적화하기 위해 쿠폰 임시 테이블에 인덱스가 추가되었습니다. (NEO 파섹)
* 이제 Analytics 통합에서 % 문자를 포함하는 AAM 세그먼트 데이터를 검색할 수 있습니다. (NEO 파섹)
* Workflow Heatmap에서 누락된 데이터 문제를 해결하기 위해 10,000개의 레코드 제한을 제거했습니다. (NEO 파섹)
* Open Office는 지원되지 않으며 이제 애플리케이션에서 완전히 제거됩니다. 계속 사용하고 있는 경우 19.1부터 더 이상 작동하지 않으므로 Libre Office로 이동합니다.
* 이제 sysfilter 속성을 사용하여 워크플로에서 데이터 활동 업데이트에 대한 쓰기 액세스를 제한할 수 있습니다. [자세한 내용](../../configuration/using/filtering-schemas.md)

**패치**

* iOS 모바일 푸시 알림에 대해 인증서가 업로드되지 않는 문제를 해결했습니다.
* 트랜잭션 푸시 알림에 대한 잠재적인 재귀 서버 충돌을 수정했습니다. 다른 충돌 문제가 해결되었습니다.
* 열려 있는 배달 표시기에 대한 사용자 활동 및 추적 보고서 간에 보고가 불일치하는 문제를 해결했습니다. (NEO 파섹)
* IMS 로그인 문제를 수정했습니다.
* 라이브러리에서 이미지를 추가할 때 배달에 이미지가 누락되는 문제를 해결했습니다. (NEO 파섹)
* 직접 메일 배달에서 오퍼 세부 정보를 추출할 때 발생할 수 있는 문제를 수정했습니다. (NEO 파섹)
* SMS 트랜잭션 메시지 성능에 영향을 줄 수 있는 문제를 수정했습니다. (NEO 파섹)
* 전달의 기본 대상에 대해 외부 파일에 정의 옵션을 사용할 때 발생할 수 있는 콘솔 충돌을 수정했습니다. (NEO 파섹)
* 일본어(.JP) 도메인에 대해 타깃팅된 받는 사람을 분석할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 1:N 링크와 함께 값 배포를 사용할 때의 표시 문제를 수정했습니다. (NEO 파섹 12212, NEO 파섹 11820)
* 업그레이드 후 MTA 로그에서 NmsMxDomain 오류가 발생하는 문제를 수정했습니다. (NEO 파섹
* 보충 워크플로우 활동에서 &quot;기본 세트에 추가 데이터 모두 유지&quot; 옵션을 사용할 때 발생하는 문제가 해결되었습니다. (NEO 파섹)
* HTTP2를 사용하여 푸시 알림을 전송할 때 발생하는 Tomcat 충돌 문제가 해결되었습니다. (NEO 파섹
* 일부 콜백이 완료될 때까지 기다리지 않았던 HTTPRequest API 관련 문제를 수정했습니다. (NEO 파섹)
* 트랜잭션 메시지에 대한 추적 표시기의 컴퓨팅 프로세스 문제를 수정했습니다. (NEO 파섹)
* 오퍼 관리에서 테마를 사용하는 문제를 수정했습니다. (NEO 파섹)
* 푸시 알림을 전송할 때 성능 문제가 해결되었습니다. (NEO 파섹)
* 직접 메일 배달을 위해 오퍼 관리에서 아웃바운드 XML 또는 CSV 파일을 미리 볼 때 문제가 해결되었습니다. (NEO 파섹)
* 소셜 네트워크 **** 관리(소셜 마케팅) 패키지를 설치할 때 발생하는 문제를 해결했습니다. (NEO 파섹)
* 올바른 액세스 권한이 있더라도 웹 애플리케이션을 삭제하지 못했던 문제를 수정했습니다. (NEO 파섹
* XML을 통해 객체를 내보내고 가져올 때 일부 값을 덮어쓸 수 있는 문제를 해결했습니다. XtkExport_IncludeDefaultValues 옵션이 추가되었습니다. True(기본 동작)로 설정하면 모든 값이 내보내집니다. [False]로 설정하면 수정 내용이 기본값으로 덮어쓰기됩니다. (NEO 파섹)
* 쿼리 후에 추가 활동이 추가되면 **[!UICONTROL Alert]** 워크플로우 활동이 실패하는 문제를 해결했습니다. (NEO 파섹
* 데이터베이스에서 파이프라인(트리거) 오프셋이 성공적으로 검색되지 않아 중복 항목이 발생하는 Oracle 설정 문제를 해결했습니다. (NEO 파섹
* Analytics 통합 사용 시 피벗 테이블에 표시 오류를 발생시킬 수 있는 문제를 수정했습니다(NEO-12103).
* 설명 분석 보고서 문제를 수정했습니다. (NEO 파섹)
* 원격 테이블에 이름에 밑줄이 있는 필드가 들어 있을 때 CRM 커넥터 문제를 해결했습니다.
* 가설 보고서에서 통화 기호에 대한 표시 문제를 야기할 수 있는 문제를 해결했습니다. (NEO 파섹)
* 추적 링크에서 특정 문자를 사용할 때 리디렉션 및 추적 문제가 해결되었습니다.
* 오퍼 미리 보기가 제대로 작동하지 않는 문제를 해결했습니다.
* 주소 테이블에서 소프트 바운스가 제거되지 않는 문제를 해결했습니다.
* 바코드를 사용할 때 JAVA 오류가 수정되었습니다.
* 웹 응용 프로그램의 번역 문제가 해결되었습니다(NEO 파섹
* s3 파일 전송 워크플로우 활동 문제를 수정했습니다. (NEO 파섹)
* 웹 애플리케이션의 날짜 필드 문제를 수정했습니다. (NEO 파섹)
* 배달에서 시드 주소를 사용할 때 ID 소모 문제가 해결되었습니다. (NEO 파섹
* phantomjs 및 Debian 9 호환성 문제를 해결했습니다.
* 증명 내용을 승인할 때 발생하는 오류를 수정했습니다. (NEO 파섹)
* &quot;모집단에서 이 하위 집합 제외&quot; 워크플로우 기능 문제를 수정했습니다. (NEO 파섹)
* 일부 콜백이 완료될 때까지 기다리지 않았던 HTTPRequest-wait API 관련 문제를 수정했습니다. (NEO 파섹)
* 분할 활동에서 &quot;공유 대상자 업데이트&quot; 작업의 문제를 수정했습니다. (NEO 파섹
* 웹 서버 충돌 문제가 수정되었습니다. (NEO 파섹)
* 트랜잭션 템플릿의 Nature 매개 변수 문제를 수정했습니다. (NEO 파섹)
* 이메일 텍스트 편집기에서 추적된 URL을 표시할 때 콘솔 충돌 문제가 해결되었습니다. (NEO 파섹)
* Audience Manager에서 대상을 가져올 때 파일 분할 작업 문제를 수정했습니다. (NEO 파섹
* 핫 클릭 보고서에서 오류가 발생하는 문제를 해결했습니다. (NEO 파섹)
* 오퍼 렌더링 문제를 수정했습니다. (NEO 파섹)
* Audience Manager에서 대상을 가져올 때 목록 업데이트 활동 문제가 해결되었습니다. (NEO 파섹)
* 예약 활동 및 시간대 구성 문제를 수정했습니다. (NEO 파섹)
* 잘못된 형식의 URL에 대해 추적 워크플로가 실패하는 문제를 해결했습니다.
* 모바일 응용 프로그램 패키지를 가져온 후 외부 계정 문제를 수정했습니다.
* 연산자에 표준 시간대를 할당할 때 발생하는 문제가 해결되었습니다. (NEO 파섹)
* 일치 로그 오류를 발생시킬 수 있는 문제를 수정했습니다. (NEO-11539, NEO-8978)
* 저장된 보고서에서 내역 아이콘을 클릭할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
* 보고서에서 피벗 테이블을 편집할 때 발생하는 문제를 수정했습니다. (NEO 파섹)
