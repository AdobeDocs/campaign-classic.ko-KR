---
title: 릴리스 19.2
seo-title: 릴리스 19.2
description: 릴리스 19.2
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 3d6515ca291715e5e02f9b5404803e9087555284
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 8%

---


# 릴리스 19.2{#release-19-2}

## ![](assets/do-not-localize/orange_2.png) 릴리스 19.2.3 - 빌드 9081 {#release-19-2-3-build-9081}

_2020년 2월 07일_

**개선 사항**

* Windows 서버에서 사용자 연결이 실패하는 SSL 인증 구현으로 인한 회귀 문제를 해결했습니다. (NEO-20629)
* 정보 메뉴에 잘못된 버전 태그 번호가 표시되던 **문제를** 수정했습니다.

## ![](assets/do-not-localize/orange_2.png) 릴리스 19.2 - 빌드 9080 {#release-19-2-build-9080}

_2019년 12월 02일_

**새로운 기능**

<table> 
 <thead> 
  <tr> 
   <th> <strong>CPA(California Consumer Privacy Act)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA는 2020년 1월 1일부터 시행되는 데이터 보호 요건을 통합하고 현대화한 캘리포니아 주 새로운 개인 정보 보호법입니다. CPA는 캘리포니아에 있는 데이터 주체의 데이터를 보유하고 있는 Adobe Campaign 고객에게 적용됩니다.</p>
    <p>Adobe Campaign은 이미 사용 가능한 개인 정보 보호 기능(동의 관리, 데이터 유지 설정 및 사용자 역할 포함) 이외에도 CPA에 대한 준비를 용이하게 하는 데 도움이 됩니다.</p>
    <ul>
      <li>액세스 권한 및 삭제 권한:우리는 GDPR에 추가된 기능을 활용하고 있습니다. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">자세한 내용</a></li>
      <li>소비자가 개인 정보 판매를 수신 거부했는지 여부를 추적할 수 있습니다. 이를 위해 프로필 테이블을 확장하고 CPA에 대한 <strong>옵트아웃 필드를 추가해야</strong> 합니다. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">자세한 내용</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>워크플로우 라이브 모니터링</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>이제 사전 정의된 보기를 사용하여 인스턴스의 모든 워크플로우의 실행 상태를 모니터링할 수 있습니다.</p>
   <p>자세한 내용은 <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">세부 설명서</a>를 참조하십시오.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>AMP를 사용한 인터랙티브한 컨텐츠</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Adobe Campaign을 사용하면 새로운 인터랙티브한 <a href="https://amp.dev/about/email/">이메일</a> 포맷용 AMP를 사용해 볼 수 있습니다. 이 포맷을 통해 마케터는 메시지 내에 AMP 구성 요소를 포함시켜 메시지 자체에서 직접 실행 가능한 풍부하고 다이내믹한 인터랙티브한 컨텐츠로 이메일 경험을 향상시킬 수 있습니다.</p>
   <p>이 기능은 공개 베타 버전으로 출시됩니다.</p>
   <p>자세한 내용은 <a href="../../delivery/using/defining-interactive-content.md">세부 설명서</a> 및 <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">튜토리얼 비디오</a>를 참조하십시오.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>TLS(안전한 SMS 메시징)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>보안 SMS는 이제 확장 범용 SMPP 커넥터를 통해 지원됩니다. 이렇게 하면 공급자에 대한 암호화된 연결이 가능합니다.</p> <p><strong>경고</strong> 이 기능을 사용하려면 모든 서버에 최신 인증서가 필요합니다. 인증서가 잘못되거나, 취소되거나, 만료된 경우 전체 SMS 전송 기능에 영향을 주는 오류가 발생합니다.</p><p>자세한 내용은 <a href="https://helpx.adobe.com/kr/campaign/kb/sms-connector-protocol-and-settings.html">세부 설명서</a>를 참조하십시오. </p> </td> 
  </tr> 
 </tbody> 
</table>

**향상된 보안 기능**

* 입력 데이터 유효성 검사 및 출력 인코딩인 캠페인 인터페이스의 저장된 사이트 간 스크립팅 취약점을 수정했습니다. (NEO-16810)
* 로그인 제한 정책을 강화하여 권한이 없는 데이터에 액세스할 수 있는 프로필 권한 부여에 대한 보안 문제가 해결되었습니다. (NEO-14445)

**개선 사항**

* 푸시 알림에 대한 메모리 소비 최적화.
* 성능 및 저장 최적화를 위해 logins.log **** 파일의 처리가 향상되었습니다. 이제 파일이 여러 파일로 분할되어 매일 최대 365개의 파일이 유지됩니다. [자세한 내용](../../production/using/log-files.md)
* 이제 암호 자격 증명(암호 + 사용자 이름) 또는 인증서(개인 키)를 사용하여 Microsoft Dynamics CRM 외부 계정을 구성할 수 있습니다. [자세한 내용](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* 안정성을 개선하기 위해 일부 개선 사항이 Hadoop FDA 커넥터에 추가되었습니다.
* 서버에 공개 리소스를 업로드하기 전에 디스크 공간을 확인하는 특정 보증인이 추가되었습니다.
* 새 [캠페인](../../installation/using/configuring-campaign-options.md) 옵션이 추가되었습니다.
   * WdbcKillSession **Policy** 구성 옵션을 사용하면 모든 워크플로 및 PostgreSQL 데이터베이스 쿼리의 **무조건부 중지** 동작에 영향을 줄 수 있습니다.
   * NmsOperation_ **DeliveryPreparationWindow** 옵션을 사용하면 일관되지 않은 상태의 배달이 실행 중인 배달 수에서 제외되는 일 수를 정의할 수 있습니다.
   * WdbcOptions_ **TempDbName** 옵션을 사용하면 Microsoft SQL Server에서 작업 테이블에 대해 별도의 데이터베이스를 구성할 수 있습니다. 백업 및 복제를 최적화합니다. [자세한 내용](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * PostgreSQL이 **데이터베이스 정리 워크플로의 저장소 최적화 단계의 동작을 보다 잘 제어하도록 XtkCleanup_NoStats** 옵션이 개선되었습니다. [자세한 내용](../../production/using/database-cleanup-workflow.md#statistics-update)
* 계정 잠금 메커니즘이 **logon()** API에 추가되었습니다. 지정된 기간 내에 연속적으로 실패한 일정한 수의 로그인 시도 이후 추가적인 로그인 시도를 차단합니다.
* 게재 속성의 새로운 **최대 개인화 실행 시간** 옵션을 사용하면 개인화 단계가 너무 오랫동안 실행되지 않도록 하기 위해 개인화 실행 시간에 대한 시간 초과 기간을 정의할 수 있습니다. [자세한 내용](../../delivery/using/personalization-fields.md#timing-out-personalization)
* SFTP 연결에 프록시 구성을 사용할 수 있도록 **ftp 프로토콜** 옵션이 추가되었습니다. [자세한 내용](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* 온-프레미스 환경을 위한 SFTP 외부 서버에 대한 프록시 액세스 새로운 지원
* 캠페인 인스턴스와 호환되지 않는 패키지를 설치하지 못하도록 특정 보증인이 추가되었습니다. [자세한 내용](../../installation/using/installing-campaign-standard-packages.md)

_사용되지 않는 시스템_

The following systems are now [deprecated](https://helpx.adobe.com/kr/campaign/kb/deprecated-and-removed-features.html) for Campaign Classic implementations:
* Apache 2.2
* Centos 6

최신 캠페인 호환성 매트릭스에 나열된 시스템의 지원 버전을 사용하고 있는지 확인하십시오. [자세한 내용](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

이제 iOS SDK의 빌드 1.0.26을 사용할 수 있습니다. 이 새로운 빌드에서 iOS 13에 대한 지원이 추가되었습니다. 이제 이 새 버전은 알림 우선 순위 및 iOS 13 푸시 알림에 대한 새로운 등록 토큰 관리 프로세스를 지원합니다. 이전 버전의 SDK에서 애플리케이션을 실행하는 경우 새로운 SDK를 사용하여 애플리케이션을 다시 컴파일해야 합니다. SDK를 받으려면 Adobe 고객 지원 센터에 문의하십시오.

**패치**

* 연결된 테이블 **추가** 필드가 RDBMS( **Data Loading)** 워크플로우 활동에서 비어 있는 충돌 문제가 해결되었습니다. (NEO-12213)
* Mid-Sourcing 서버에서 특정 메시지를 처리하지 못하는 문제를 해결했습니다. (NEO-12395)
* Teradata에서 쿼리 밴딩 옵션을 사용할 때 데이터베이스 정리 워크플로우의 문제를 해결했습니다. (NEO-12399)
* ne.jp 도메인을 포함한 분류 규칙이 있는 배달 분석에 영향을 주는 문제를 수정했습니다. (NEO-12609)
* 보다 제한적인 인증서 정책에 암시된 TLS 업데이트에 대한 SMS 관련 문제를 수정했습니다. 이러한 업데이트는 오래된 인증서의 경우 마케팅과 미드소싱 서버 간의 연결 실패를 초래할 수 있습니다. (NEO-17698)
* 저장소 인증이 있는 중간 소싱 환경의 외부 계정에서 연결 **테스트** 단추를 사용할 때 발생하는 문제를 수정했습니다. (NEO-12722)
* FDA Hadoop 연결의 날짜 함수를 사용하는 쿼리의 문제를 수정했습니다. (NEO-12847)
* 이메일 편집기에서 이미지를 교체할 때 발생하는 문제가 해결되었습니다. (NEO-13098)
* 삭제되었거나 다른 위치로 이동한 폴더에 대해 업그레이드 후 오류가 발생할 수 있는 문제를 수정했습니다. (NEO-13118)
* LINE 메시지에서 장치 화면 크기당 이미지 **정의 옵션을 사용할 때 이미지 표시** 문제가 해결되었습니다. (NEO-13228)
* 배달 **** 중 중복 주소 제외 옵션을 선택하지 않은 경우 배달 준비 문제가 해결되었습니다. (NEO-13240)
* 전송 **후 소스 파일** 삭제 옵션을 사용하여 파일을 다운로드할 때 공백 문자를 포함하는 이름으로 작업 **** 중인 워크플로우의 문제를 수정했습니다. (NEO-13411)
* 메모리 문제를 야기할 수 있는 Tomcat 캐시 정리 문제를 해결했습니다. (NEO-13456)
* Microsoft SQL 2017에서 실행 중인 기존 제어 인스턴스에 실행 인스턴스 **** 내장 패키지와 함께 오퍼 엔진 제어 기능을 설치할 때 발생하는 문제를 수정했습니다. (NEO-13539)
* 초기화되지 않은 변수로 인해 이메일의 추적된 URL을 **텍스트 컨텐츠** 탭에서 확인하지 않을 때 발생할 수 있는 콘솔 충돌 문제를 수정했습니다. (NEO-13545)
* 중국어 보낸 사람 이름에 대한 인코딩 문제가 해결되었습니다. (NEO-13837)
* 탐색기에서 설문 조사 응답 데이터를 표시할 때 발생할 수 있는 오류를 수정했습니다. (NEO-14590)
* 배달 로그 분류와 격리 테이블 간 불일치가 발생하는 문제를 해결했습니다. (NEO-16547)
* 이메일에 포함되지 않은 DKIM 키 관련 문제가 해결되었습니다. (NEO-16804)
* 잘못된 세션 토큰을 API 호출 컨텍스트에서 사용하여 이벤트를 트리거하는 경우 잘못된 오류 코드를 표시하는 문제를 해결했습니다. 오류 코드는 &#39;HTTP 403 금지&#39; 대신 &#39;HTTP 200 OK&#39;였습니다. (NEO-16826)
* 웹 액세스를 통해 배달 보고서를 표시할 때 발생하는 문제가 해결되었습니다. (NEO-17015)
* Adobe Campaign에 로그인할 때 발생하는 IMS 인증 문제가 해결되었습니다. (NEO-17312)
* 격리된 이메일이 개인 정보 관리 프로세스에서 삭제되지 않는 문제를 해결했습니다. (NEO-17314)
* SQL 데이터베이스를 사용하여 9031로 업그레이드한 후 처리량 문제가 해결되었습니다. (NEO-17558)
* Salesforce의 CRM 커넥터에 영향을 주는 문제가 해결되었습니다. (NEO-17712)
* 외부 SFTP에서 데이터를 가져올 때 시간 초과 문제가 해결되었습니다. (NEO-19723)
* 예측 모델에 액세스할 때 발생하는 문제가 해결되었습니다. (NEO-19713)
* Hadoop FDA 데이터베이스를 사용하는 **Split** Workflow 활동에서 임의 샘플링에 영향을 주는 문제를 수정했습니다. (NEO-16636)
* 업그레이드 후 일부 기능이 잘못된 것으로 간주되도록 Oracle의 회귀 문제를 해결했습니다. (NEO-12759)


