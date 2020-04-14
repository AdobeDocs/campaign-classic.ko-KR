---
title: Campaign Classic의 가치 하락 및 제거 기능
description: 이 페이지에는 Adobe Campaign Classic의 사용 중단되거나 제거된 기능이 나열됩니다.
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 10419ee0fb466bddd05ab67087ccdbfdda1e48c8

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe는 항상 이전 버전과의 호환성을 신중하게 고려하여 보다 현대적인 대체 요소로 대체해야 하는 이전 기능을 확인하기 위해 제품 기능을 지속적으로 평가합니다. Adobe Campaign Classic은 타사 툴과 연동되므로 지원되는 버전만 구현하기 위해 정기적으로 호환성이 업데이트됩니다. Adobe Campaign Classic과 더 이상 호환되지 않는 버전은 아래에 나와 있습니다.

Campaign Classic 기능의 임박한 제거/대체를 알리기 위해 다음 규칙이 적용됩니다.

* 사용 중단 발표가 우선입니다. 더 이상 사용되지 않는 기능을 기존 사용자도 사용할 수 있지만 더 이상 향상되거나 문서화되지 않습니다.
* 더 이상 사용되지 않는 기능은 빠른 시일 내에 다음 릴리스에서 제거됩니다. 제거에 대한 실제 대상 날짜가 이 페이지에 표시됩니다.

이 프로세스를 통해 고객은 실제로 제거하기 전에 새로운 버전 또는 더 이상 사용되지 않는 기능의 후속 버전에 맞게 구현을 조정할 수 있는 릴리스 주기를 하나 이상 제공할 수 있습니다.

>[!NOTE]
>Adobe Campaign 릴리스 및 새로운 기능은 릴리스 [노트에 나와 있습니다](../../rn/using/latest-release.md).


## 더 이상 사용되지 않는 기능 {#deprecated-features}

이 섹션에는 최신 Campaign Classic 릴리스에서 더 이상 사용되지 않는 것으로 표시된 기능 및 기능이 나열됩니다.

일반적으로 향후 릴리스에서 제거될 예정인 기능은 먼저 더 이상 사용되지 않도록 설정되며, 대신 제공된 기능이 있습니다. 이러한 기능 및 기능은 더 이상 새 Campaign Standard 고객에게 사용할 수 없거나 새로운 구현에 사용할 수 없습니다. 또한 제품 설명서에서 제거됩니다.

고객은 현재 배포에서 기능/기능을 사용하는지 검토하고 제공된 대체 요소를 사용하도록 구현을 변경할 계획을 수립하는 것이 좋습니다. 환경 및 프로젝트 업데이트를 계획하려면 대상 제거 날짜를 참조하십시오.

### Adobe Campaign 18.6 릴리스 {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>영역</strong></td>
   <td><strong>기능</strong></td> 
   <td><strong>교체</strong></td> 
  </tr> 
   <tr> 
   <td>Javascript SDK 보안<br></td>
   <td>decryptString<br></td>
   <td><p>보안상의 이유로, 암호 해독 문자열 API는 더 이상 새 설치에 기본적으로 사용할 수 없습니다.</p> 
   <p>18.6 이상으로 업그레이드 후 컨텍스트에서 이 API는 더 이상 활성화되지 않으며 암호 해독 함수로 대체되었습니다.</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 18.4 릴리스 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>영역</strong></td>
   <td><strong>기능</strong></td> 
   <td><strong>교체</strong></td> 
  </tr> 
   <tr> 
   <td>이메일 보관<br></td>
   <td>파일 기반 보관<br></td>
   <td><p>이제 전용 숨은 참조 이메일 주소를 통해 이메일 보관을 사용할 수 있습니다. <a href="../../installation/using/email-archiving.md">자세한 내용</a>.</p> 
   <p><em>대상 제거 날짜:Campaign 20.2 릴리스 - 2020년 6월</em></p><br> </td>
  </tr> 
   <tr> 
   <td>리드 관리<br></td>
   <td>리드<br></td>
   <td><p>Adobe Campaign Classic의 리드 관리 패키지는 전체 리드 관리 라이프사이클을 작성하고 유지 관리하는 프로세스를 간소화했습니다. 유사한 기능은 다른 기본 워크플로우 활동 및 데이터 모델 수정을 통해 구현할 수 있습니다.</p> 
   <p><em>대상 제거 날짜:Campaign 20.2 릴리스 - 2020년 6월</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## 더 이상 사용되지 않는 호환성 {#deprecated-compatibility}

### Adobe Campaign 20.1 릴리스 {#compat-20-1-release}

20.1 2월 릴리스부터 다음 시스템은 Campaign Classic에서 더 이상 사용되지 않습니다. 호환성은 20.2 릴리스 - 2020년 6월에 종료됩니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>영역</strong></td>
   <td><strong>교체</strong></td> 
  </tr> 
   <tr> 
   <td>Campaign Classic 클라이언트 콘솔 32비트<br></td>
   <td><p>Campaign Classic 클라이언트 콘솔 64비트</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 19.2 릴리스 {#compat-19-2-release}

19.2 가을 릴리스부터 다음 운영 체제는 Campaign Classic에서 더 이상 사용되지 않습니다. 호환성은 2020년 EOY에서 종료됩니다.

* 웹 서버:Apache 2.2.자세한 [내용](https://wiki.centos.org/About/Product)
* 운영 체제:CentOS 6. [자세한 내용](https://wiki.centos.org/About/Product)

최신 [버전으로 업그레이드하거나 새 시스템으로 이동하려면 호환성 매트릭스를](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 참조하십시오.

## 제거된 기능 {#removed-features}

이 섹션에는 Campaign Standard에서 제거된 기능 및 기능이 나열됩니다.

<table> 
 <tbody> 
  <tr> 
   <td><strong>영역 - 기능</strong></td>
   <td><strong>교체</strong></td> 
   <td><strong>버전</strong></td> 
  </tr> 
   <tr> 
   <td>캠페인 API 설명서 - jsapi.chm 파일<br></td>
   <td>이제 전용 페이지에서 Campaign Classic API를 사용할 수 있습니다. jsapi.chm 파일을 사용하는 경우 이제 <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">새로운 온라인 버전을</a>참조해야 합니다.</td>
   <td>&lt;19.1</td>
  </tr> 
  <tr> 
   <td>캠페인 통합 운영 - 예측 마케팅</td>
   <td>Adobe Campaign Classic의 예측 마케팅 기능은 예측 모델을 많이 사용했습니다. 예측 마케팅 워크플로우 활동은 예정된 버전에서 제거되지만 Adobe Campaign은 다른 워크플로우 활동을 통해 외부 소스의 예측 모델을 사용하고 사용할 수 있도록 계속 지원합니다.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>웹 애플리케이션 - 마이크로사이트</td>
   <td>Adobe Campaign 구성 파일의 전용 도메인에만 대한 액세스를 제한하여 보안을 향상시킵니다. DNS 별칭을 사용하여 Campaign에서 여전히 개인화된 URL을 사용할 수 있습니다. <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">자세한 내용</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>푸시 알림 - iOS 바이너리 커넥터<br></td>
   <td>Apple의 권장 사항에 따라 Adobe는 레거시 iOS 바이너리 커넥터를 제거할 것입니다. 보다 강력하고 효율적인 HTTP/2 기반 커넥터를 이미 사용할 수 있습니다.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>모바일 채널 - MMS 및 WAP 푸시 메시지</td>
   <td>MMS 및 Wap 푸시 채널을 더 이상 사용할 수 없습니다. 교체자는 SMS 및 푸시 <a href="../../delivery/using/sms-channel.md">전달을 활용할 수</a> 있습니다 <a href="../../delivery/using/about-mobile-app-channel.md"></a> .</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>모바일 채널 - LINE v1</td>
   <td>LINE Connect 패키지는 더 이상 Adobe Campaign Classic에서 설치할 수 없습니다. 새 LINE 채널 패키지를 사용하여 LINE 메시지를 보내는 것이 좋습니다. <a href="../../delivery/using/line-channel.md">자세한 내용</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## 호환성 종료 {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic은 호환성 매트릭스에 나열된 모든 시스템 및 도구와 [호환됩니다](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). 이러한 타사 시스템 및 도구의 특정 버전이 해당 개발자와 EOL(End-of-Life)에 도달하면 Adobe Campaign은 더 이상 해당 버전과 호환되지 않습니다.더 이상 사용되지 않는 것으로 알려지면 이후 제품 릴리스의 호환성 매트릭스에서 제거됩니다. 문제가 발생하지 않도록 호환성 매트릭스에 나열된 시스템의 지원 버전을 사용하고 있는지 확인하십시오.

### 클라이언트 콘솔 {#client-console-eol}

Adobe Campaign Classic Client Console은 편집기에서 더 이상 사용되지 않으므로 다음 시스템에서 더 이상 실행할 수 없습니다. 이러한 버전 중 하나에서 Campaign Client Console을 실행하는 고객은 타겟 제거 날짜 전에 최신 버전으로 업그레이드해야 합니다. 호환성 [매트릭스를](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)참조하십시오.

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### 운영 체제 {#o-s-eol}

19.1 릴리스부터 Adobe Campaign은 더 이상 다음 운영 체제와 호환되지 않습니다.

* 데비안 7. [자세한 내용](https://wiki.debian.org/DebianReleases).
* RHEL 6.x.자세한 [내용](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [자세한 내용](https://support.microsoft.com/en-us/lifecycle/search/1163).
* SLES 11. [자세한 내용](https://www.suse.com/lifecycle).

### 웹 서버 {#web-server-eol}

19.1 봄 릴리스부터 Adobe Campaign은 더 이상 다음 웹 서버와 호환되지 않습니다.

* Microsoft IIS 7. [자세한 내용](https://support.microsoft.com/en-us/lifecycle/search/810).

### 도구 {#tools-eol}

19.1 봄 릴리스부터 Adobe Campaign은 더 이상 다음 도구와 호환되지 않습니다.

* Java JDK 7. [자세한 내용](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Libre Office 3.5 / 4.3 / 5.x(다른 도구에 내장되어 있는 경우 제외) [자세한 내용](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### 데이터베이스 엔진 {#dbe-eol}

Adobe는 편집자가 사용하지 않으므로 다음 데이터베이스 엔진을 지원하지 않습니다. 이러한 버전을 실행하는 고객은 최신 버전으로 업그레이드하거나 다른 버전으로 이동해야 합니다.

호환 버전 [목록에 액세스하려면 Campaign Classic 호환성 매트릭스를](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) 참조하십시오.

**연합 데이터 액세스(FDA)**

19.1 봄 릴리스부터 Adobe Campaign은 더 이상 다음 FDA 서버와 호환되지 않습니다.

* Oracle 11G. [자세한 내용](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3.자세한 [내용](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[자세한 내용](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5.자세한 [내용](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradata 14 - 14.1.자세한 [내용](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

Campaign Classic은 FDA(Federated Data Access)의 다음 서버와 호환되지 않습니다.

* DB2 UDB 9.5, 9.7.DB2의 최신 버전은 Federated Data Access(FDA)를 통해 지원됩니다. [자세한 내용](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. 최신 버전의 Oracle은 Federated Data Access(FDA)를 통해 지원됩니다. [자세한 내용](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2.PostgreSQL의 최신 버전은 Federated Data Access(FDA)를 통해 지원됩니다. [자세한 내용](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. SQL Server의 최신 버전은 Federated Data Access(FDA)를 통해 지원됩니다. [자세한 내용](https://support.microsoft.com/en-us/lifecycle/search/1044).
* MySQL 5.1.MySQL의 최신 버전은 Federated Data Access(FDA)를 통해 지원됩니다. [자세한 내용](https://en.wikipedia.org/wiki/InfiniDB).
* InfiniDB가 수명이 다했습니다. [자세한 내용](https://www.mysql.com/support).
* Teradata 13, 13.1.최신 버전의 Teradata는 Federated Data Access(FDA)를 통해 지원됩니다. [자세한 내용](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0.Netezza는 수명이 다했습니다. [자세한 내용](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0.AsterData가 수명이 만료되었습니다. [자세한 내용](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 및 Sybase ASE 15.0.Sybase의 최신 버전은 Federated Data Access(FDA)를 통해 지원됩니다. [자세한 내용](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* HiveSQL을 통한 Hadoop:Hadoop 2.7.3, HiveSQL 1.2.1.Adobe Campaign Classic은 FDA(Federated Data Access)를 통해 HiveSQL을 통해 Hadoop의 나열된 버전을 계속 지원하지만 다음 버전은HortonWorks(HDP 2.4.X, 2.5.x, 2.6.x) 및 HDInsight 3.4(HDP 2.4), 3.5(HDP 2.5), 3.6(HDP 2.6)

**RDBMS SERVER**

Adobe Campaign은 다음 RDBMS 서버와 호환되지 않습니다.
* Oracle 10GR2, 11G
* PostgreSQL 9.0 - 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
