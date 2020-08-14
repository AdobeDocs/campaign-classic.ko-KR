---
title: Campaign Classic deprecated and removed features
description: 이 페이지에는 Adobe Campaign Classic의 사용이 중단되거나 제거된 기능이 나열됩니다.
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 63f07746d39fff22a98b3cd4ab7f2294da778ab3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 100%

---


# 사용이 중단되거나 제거된 기능 {#deprecated-and-removed-features}

Adobe는 항상 이전 버전과의 호환성을 신중하게 고려하여 전반적인 고객 가치를 향상시키기 위해 제품 기능을 지속적으로 평가하여 보다 현대적인 대체 요소로 대체해야 하는 기존 기능을 식별합니다. Adobe Campaign Classic은 타사 도구와 연동되므로 지원되는 버전만 구현하기 위해 정기적으로 호환성이 업데이트됩니다. Adobe Campaign Classic과 더 이상 호환하지 않는 버전은 아래와 [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)에 나와 있습니다.

Campaign Classic 기능을 제거/교체하기 위해 다음 규칙이 적용됩니다.

* 사용 중단 발표가 우선입니다. 기존 사용자는 사용 중단되는 기능을 계속 사용할 수 있고 지원되지만 더 이상 향상 또는 문서화되지 않습니다.
* 사용 중단되는 기능은 빠른 시일 내에 다음 릴리스에서 제거됩니다. 제거에 대한 실제 타겟 날짜가 이 페이지에 표시되어 있습니다.

이 프로세스를 통해 고객은 실제 제거하기 전에 새로운 버전이나 사용 중단되는 기능의 후속 버전에 맞게 구현을 조정할 수 있는 릴리스 주기를 적어도 하나 이상 확보할 수 있습니다.

>[!NOTE]
>Adobe Campaign 릴리스 및 새 기능은 [릴리스 정보](../../rn/using/latest-release.md)에 나와 있습니다.

## 사용 중단되는 기능{#deprecated-features}

이 섹션에는 최신 Campaign Classic 릴리스에서 사용 중단되는 것으로 표시된 기능 및 성능이 나열됩니다.

일반적으로 향후 릴리스에서 제거될 예정인 기능은 먼저 사용 중단되는 것으로 설정됩니다. 이러한 기능과 기능은 새 Campaign Classic 고객에게 더 이상 제공되거나 새로운 구현에 사용되어서는 안됩니다. 제품 설명서에서도 제거됩니다.

고객은 현재 배포에서 기능/성능을 사용하는지 검토하고 구현 변경을 계획해야 합니다. 타겟 제거 날짜를 참조하여 환경 및 프로젝트 업데이트를 계획하십시오.

<table> 
 <tbody> 
   <tr>
   <td><strong>기능</strong></td>
   <td><strong>교체</strong></td> 
  </tr>
   <tr>
  <td>SMS 커넥터<br></td>
  <td><p> 20.2 릴리스부터 다음 SMS 커넥터는 사용 중단됩니다.<p>
   <ul>
   <li>NetSize</li>
   <li>일반 SMPP(SMPP 버전 3.4 지원 바이너리 모드)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX 커뮤니케이션</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>이러한 커넥터 중 하나를 사용하는 경우 그에 따라 구현을 조정해야 합니다. <a href="../../delivery/using/sms-channel.md">자세히 알아보기</a></p> 
  <p><a href="https://helpx.adobe.com/kr/campaign/kb/sms-connector.html">이 기술 문서</a>에서 레거시 커넥터를 마이그레이션하는 방법을 배웁니다.</p>
  <p><em>타겟 제거 날짜: 2021년</em></p>
  </td> 
 </tr>
  <tr>  
   <td>팩스 채널<br></td>
   <td><p>20.2 릴리스부터 팩스 채널은 사용 중단됩니다.</p> 
   <p>이 채널을 사용하는 경우 그에 따라 구현을 조정해야 합니다. Campaign 채널에 대해 <a href="../../delivery/using/steps-about-delivery-creation-steps.md">자세히 알아보십시오</a>.</p>
   <p><em>타겟 제거 날짜: 2021년</em></p></td>
  </tr>
 </tbody> 
</table>

## 제거된 기능 {#removed-features}

이 섹션에는 Campaign Classic에서 제거된 기능과 기능이 나열됩니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>영역 - 기능</strong></td>
   <td><strong>교체</strong></td> 
  </tr> 
   <tr> 
   <td>파일 기반의 전자 메일 보관<br></td>
   <td><p>Campaign 20.2 릴리스를 시작으로 파일 기반 전자 메일 보관을 더 이상 사용할 수 없습니다. 이제 전용 숨은 참조 전자 메일 주소를 통해 전자 메일 보관 기능을 사용할 수 있습니다. <a href="../../installation/using/email-archiving.md">자세히 알아보기</a></p></td>
  </tr> 
   <tr> 
   <td>리드 관리</td>
   <td><p>Campaign 20.2 릴리스를 시작하면 더 이상 리드 관리 패키지를 사용할 수 없습니다. 다른 기본 워크플로우 활동 및 데이터 모델 수정을 통해 유사한 기능을 구현할 수 있습니다.</p></td>
   </tr>
   <tr>
   <td>Campaign API 설명서 - jsapi.chm 파일</td>
   <td>Campaign 19.1 릴리스를 시작하면 Campaign Classic API는 전용 페이지에서 사용할 수 있습니다. 기존 jsapi.chm 파일을 사용하는 경우 이제 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">새 온라인 버전</a>을 참조해야 합니다.</td>
  </tr> 
  <tr> 
   <td>Campaign 오케스트레이션 - 예측 마케팅</td>
   <td>Campaign 18.10 릴리스를 시작하면 더 이상 예측 마케팅 기능을 사용할 수 없습니다.</td>
  </tr> 
  <tr> 
   <td>웹 애플리케이션 - 마이크로사이트</td>
   <td>Campaign 18.10 릴리스부터 마이크로사이트를 더 이상 사용할 수 없습니다. Adobe Campaign 구성 파일의 전용 도메인에만 대한 액세스를 제한하여 보안을 강화할 수 있고 DNS 별칭을 사용하여 Campaign에서 개인화된 URL을 사용할 수 있습니다. <a href="https://helpx.adobe.com/kr/campaign/kb/domain-name-delegation.html">자세히 알아보기</a></td>
  </tr> 
  <tr> 
   <td>푸시 알림 - iOS 이진 커넥터</td>
   <td>Apple의 권장 사항에 따라 Adobe는 Campaign 18.10 릴리스부터 이전의 iOS 이진 커넥터를 제거했습니다. 보다 강력하고 효율적인 HTTP/2 기반 커넥터를 이미 사용할 수 있습니다.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>보안상의 이유로 Campaign 18.6 릴리스부터는 <em>decryptString</em> API는 기본적으로 더 이상 새로 설치할 수 없습니다.</p> 
   <p>18.6 또는 그 이상으로 업그레이드 후 컨텍스트에서 이 API는 더 이상 활성화되지 않으며 <em>decryptPassword</em> 함수로 대체되었습니다. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">자세히 알아보기</a></p></td>
  </tr> 
   <tr> 
   <td>모바일 채널 - MMS 및 WAP 푸시 메시지</td>
   <td>Campaign 18.4 릴리스를 시작하면 MMS 및 Wap 푸시 채널을 더 이상 사용할 수 없습니다. 대신 <a href="../../delivery/using/sms-channel.md">SMS</a> 및 <a href="../../delivery/using/about-mobile-app-channel.md">푸시</a> 게재를 활용할 수 있습니다.</td>
  </tr> 
   <tr> 
   <td>모바일 채널 - LINE v1</td>
   <td>Campaign 18.4 릴리스를 시작하는 경우 LINE Connect 패키지를 더 이상 사용할 수 없습니다. 새 LINE 채널 패키지를 대체용으로 사용하는 것이 좋습니다. <a href="../../delivery/using/line-channel.md">자세히 알아보기</a></td>
  </tr> 
 </tbody> 
</table>

## 사용 중단된 호환성 {#deprecated-compatibility}

다음 시스템은 Campaign Classic에서 사용 중단됩니다. 호환성이 종료되기 전에 최신 버전으로 업그레이드하거나 새 시스템으로 이동하려면 [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.

### Adobe Campaign 20.2 릴리스 {#compat-20-2-release}

20.2 릴리스부터 다음 시스템은 Campaign Classic에서 사용 중단됩니다. 호환성은 20.3 릴리스 - 2020년 9월에 종료됩니다.

* 클라이언트 콘솔: Windows 7
* 레거시 SMS 커넥터(아래의 사용 중단되는 기능 섹션 참조)

### Adobe Campaign 19.2 릴리스  {#compat-19-2-release}

19.2 릴리스부터 다음 운영 체제는 Campaign Classic에서 더 이상 사용되지 않습니다. 호환성은 2020년 말에 종료됩니다.

* 웹 서버: Apache 2.2.
* 운영 체제: CentOS 6.

최신 버전으로 업그레이드하거나 새 시스템으로 이동하려면 [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.

## 호환성 종료 {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic은 [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)에 나열된 모든 시스템 및 도구와 호환됩니다. 이러한 타사 시스템 및 도구의 특정 버전이 각각의 작성자와 EOL(End-of-Life)에 도달하면 더 이상 사용되지 않으며 이후 제품 릴리스의 호환성 매트릭스에서 제거되어 Adobe Campaign은 해당 버전과 더 이상 호환되지 않습니다. 호환성 매트릭스에 나와 있는 모든 시스템의 지원 버전을 사용하고 있는지 확인하십시오.

### 클라이언트 콘솔 {#client-console-eol}

편집기에서 사용 중단되었으므로 다음 시스템에서는 Adobe Campaign Classic 클라이언트 콘솔을 더 이상 실행할 수 없습니다. 이러한 버전 중 하나에서 Campaign 클라이언트 콘솔을 실행하는 고객은 타겟 제거 날짜 전에 최신 버전으로 업그레이드해야 합니다. [호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>Campaign 20.1 릴리스부터 Campaign Classic 클라이언트 콘솔 32비트는 더 이상 Campaign 최신 버전과 호환되지 않습니다. 64비트 클라이언트 콘솔을 사용해야 합니다.


### 운영 체제 {#o-s-eol}

19.1 릴리스부터 Adobe Campaign은 더 이상 다음 운영 체제와 호환되지 않습니다.

* Debian 7. [자세히 알아보기](https://wiki.debian.org/DebianReleases)
* RHEL 6.x. [자세한 내용](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [자세히 알아보기](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [자세히 알아보기](https://www.suse.com/lifecycle)

### 웹 서버 {#web-server-eol}

19.1 봄 릴리스부터 Adobe Campaign은 더 이상 다음 웹 서버와 호환되지 않습니다.

* Microsoft IIS 7. [자세히 알아보기](https://support.microsoft.com/en-us/lifecycle/search/810)

### 도구 {#tools-eol}

19.1 봄 릴리스부터 Adobe Campaign은 더 이상 다음 도구와 호환되지 않습니다.

* Java JDK 7. [자세히 알아보기](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5 / 4.3 / 5.x(다른 도구에 내장된 경우 제외) [자세히 알아보기](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### 데이터베이스 엔진 {#dbe-eol}

편집기에서 사용 중단되었으므로 Adobe는 더 이상 다음 데이터베이스 엔진을 지원하지 않습니다. 이러한 버전을 실행하는 고객은 최신 버전으로 업그레이드하거나 다른 버전으로 이동해야 합니다.

호환 버전 목록에 액세스하려면 [Campaign Classic 호환성 매트릭스](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix.html)를 참조하십시오.

**FDA (FEDERATED DATA ACCESS)**

19.1 봄 릴리스부터 Adobe Campaign은 더 이상 다음 FDA 서버와 호환되지 않습니다.

* PostgreSQL 9.3. [자세히 알아보기](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [자세히 알아보기](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [자세히 알아보기](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14 - 14.1. [자세히 알아보기](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic은 FDA(Federated Data Access)의 다음 서버와 호환되지 않습니다.

* DB2 UDB 9.5, 9.7. DB2의 최신 버전은 FDA(Federated Data Access)를 통해 지원됩니다. [자세히 알아보기](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. 최신 버전의 Oracle은 FDA(Federated Data Access)를 통해 지원됩니다. [자세히 알아보기](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. 최신 버전의 PostgreSQL은 FDA(Federated Data Access)를 통해 지원됩니다. [자세히 알아보기](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. 최신 버전의 SQL Server는 FDA(Federated Data Access)를 통해 지원됩니다. [자세히 알아보기](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. 최신 버전의 MySQL은 FDA(Federated Data Access)를 통해 지원됩니다. [자세히 알아보기](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB는 수명이 종료되었습니다. [자세히 알아보기](https://www.mysql.com/support)
* Teradata 13, 13.1. 최신 버전의 Teradata는 FDA(Federated Data Access)를 통해 지원됩니다. [자세히 알아보기](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza는 수명이 종료되었습니다. [자세히 알아보기](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData는 수명이 종료되었습니다. [자세히 알아보기](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 및 Sybase ASE 15.0이 지원됩니다. Sybase의 최신 버전은 FDA(Federated Data Access)를 통해 지원됩니다. [자세히 알아보기](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* HiveSQL을 통한 Hadoop: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic에서는 여전히 FDA(Federated Data Access)를 통해 HiveSQL을 통해 나열된 Hadoop 버전을 지원하지만, 이러한 버전은 다음과 병합됩니다. HortonWorks(HDP 2.4.X, 2.5.x, 2.6.x) 및 HDInsight 3.4(HDP 2.4), 3.5(HDP 2.5), 3.6(HDP 2.6)

**RDBMS 서버**

Adobe Campaign은 다음 RDBMS 서버와 호환되지 않습니다.
* Oracle 10GR2
* PostgreSQL 9.0 - 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
