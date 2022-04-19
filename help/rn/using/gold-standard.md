---
product: campaign
title: '"[!DNL Gold Standard] 릴리스"'
description: Campaign Classic 릴리스 정보 및 호환성 매트릭스 [!DNL Gold Standard]
feature: Overview
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: ht
source-wordcount: '1670'
ht-degree: 100%

---

# [!DNL Gold Standard] 릴리스{#gold-standard}

![](../../assets/v7-only.svg)

이 페이지에서 [!DNL Gold Standard] 릴리스의 릴리스 정보 및 호환성 매트릭스를 확인할 수 있습니다.

## [!DNL Gold Standard]년 릴리스 정보


### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] 12 릴리스{#gs-12}

_2021년 9월 7일_

빌드 9032@554dbcd에는 다음 수정 사항이 포함되어 있습니다.

* 추적이 활성화된 Line 게재에서 웹 애플리케이션에 대한 링크를 열 때 500 오류가 발생하는 문제를 수정했습니다.

_2021년 8월 27일_

빌드 9032@99a3894에는 다음 수정 사항이 포함되어 있습니다.

* 서드파티 도구(이메일 클라이언트, 인터넷 브라우저 등)의 특수문자 처리 방식과 관련된 오류를 방지하기 위해 추적 서명 기능이  개선되었습니다. 이제 URL 매개 변수가 인코딩됩니다.
* 콘솔에 차단기 오류 메시지가 표시될 수 있는 날짜 선택기 문제가 해결되었습니다. (NEO-36345)

### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] 11 릴리스{#gs-11}

_2021년 4월 14일_

빌드 9032@d030c36에는 다음 수정 사항을 포함합니다.

* IMS 연결 화면에서 지속적인 오류 메시지를 발생시킨 클라이언트 콘솔 회귀 문제를 수정했습니다. (NEO-34821)
* 이 콘솔 빌드는 [IMS 액세스](../../technotes/using/ims-updates.md)를 유지 관리하는 데 필요합니다.

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!CAUTION]
>
> * Adobe IMS(Identity Management Service)를 통해 Adobe ID로 Campaign에 연결하는 경우 **2021년 6월 30일** 이후부터 Campaign 서버와 클라이언트 콘솔을 모두 업그레이드해야 Campaign에 연결할 수 있습니다. [자세히 알아보기](../../technotes/using/ims-updates.md)
> * 이 릴리스는 [보안 픽스](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)와 함께 제공됩니다. 환경 보안을 강화하려면 업그레이드가 필요합니다.
> * oAuth 인증을 통해 Experience Cloud 트리거 통합을 사용할 경우 [이 페이지에서](../../integrations/using/configuring-adobe-io.md) 설명한 대로 Adobe I/O로 이동해야 합니다. Campaign의 [레거시 oAuth 인증 모드는](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411?profile.language=ko) **2021년 9월**&#x200B;부로 사용이 중단되었습니다. 호스팅 환경의 경우 **2022년 2월 23일**&#x200B;까지 연장 사용할 수 있습니다. 온프레미스 또는 하이브리드 고객은 Adobe 고객 지원 센터에 문의하면 2022년 2월까지 지원을 연장할 수 있습니다. Adobe에 [OAuth 애플리케이션의 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)를 제공해야 합니다.
>
>이 [[!DNL Gold Standard] 섹션](../../rn/using/gold-standard.md)에서 자세히 알아보기

_2021년 3월 2일_

빌드 9032@10c2709에는 다음 수정 사항을 포함합니다.

* 게재의 날짜 선택 및 이미지 관리와 같이 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 문제를 해결했습니다. (NEO-31453, NEO-31454)

**콘솔 업그레이드는 필수 사항입니다. 서버를 업그레이드할 필요가 없습니다.**

>[!NOTE]
>
> [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)에 연결하여 새 버전을 다운로드합니다. [이 페이지에서](../../installation/using/client-console-availability-for-windows.md) 모든 최종 사용자에게 콘솔 업데이트를 제안하는 방법을 알아봅니다.

_2020년 12월 22일_

빌드 9032@d3b452f는 다음과 같은 개선 사항 및 수정 사항을 포함합니다.

* 연결 프로토콜은 새 IMS 인증 메커니즘을 따르도록 업데이트되었습니다.

* 기존 oAUTH 인증 설정을 기반으로 파이프라인에 액세스하는 트리거 통합 인증이 변경되었으며 Adobe I/O로 이동되었습니다. [자세히 알아보기](../../integrations/using/configuring-adobe-io.md)

* [iOS APNs 레거시 이진 프로토콜에 대한 지원 종료](https://developer.apple.com/kr/news/?id=c88acm2b)에 따라 업그레이드 이후 이 프로토콜을 사용하는 모든 인스턴스는 HTTP/2 프로토콜로 업데이트됩니다.

* SSRF(Server Side Request Forgery) 공격으로부터 보호를 강화하기 위해 보안 문제를 해결했습니다. (NEO-27777)

* **보강** 활동을 실행할 때 워크플로우가 실패할 수 있는 문제를 해결했습니다. (NEO-17338)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 10 릴리스{#gs-10}

_2020년 7월 7일_

빌드 9032@efd8a94에는 다음 수정 사항이 포함되어 있습니다.

서명 기능이 비활성화되었을 때 추적을 수행할 수 없는 문제를 해결했습니다. (NEO-26411)

>[!CAUTION]
>
>이 릴리스에서 사용할 수 있는 클라이언트 콘솔을 업그레이드하는 것이 좋습니다. [이 페이지](../../installation/using/installing-the-client-console.md)를 참조하십시오

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 9 릴리스{#gs-9}

_2020년 6월 22일_

빌드 9032@800be2e에는 다음 수정 사항이 포함되어 있습니다.

* iOS HTTP2 커넥터가 개선되었습니다(타사 업데이트 및 오류 관리). (NEO-25904, NEO-25903, NEO-25799)

다음 수정 사항은 추적 링크 보안 메커니즘과 관련되어 있습니다(자세한 내용은 [보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/kr/campaign/kb/acc-security.html#signature-mechanism)에 있음).

* &quot;알림 클릭&quot; 추적이 작동하지 않는 문제를 해결했습니다(iOS 및 Android 푸시 알림). (NEO-25965)
* 특정 이전 버전의 Outlook을 사용할 때 추적 URL을 열거나 클릭하지 못하는 문제를 해결했습니다.  (NEO-25688)
* 개인화 매개 변수의 조각을 사용하여 URL을 추적할 수 없는 문제(파운드 기호가 있는 앵커 태그)를 해결했습니다. (NEO-25774)
* 피싱 방지 서비스 문제를 해결했습니다. (NEO-25283)
* 특정 사용자 지정 추적 공식을 사용할 때의 추적 문제를 해결했습니다. (NEO-25277)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 8 릴리스{#gs-8}

_2020년 4월 29일_

빌드 9032@3a9dc9c에는 다음 수정 사항이 포함되어 있습니다.

* 전자 메일의 링크 추적 보안이 개선되었습니다. 모든 고객에 대해 기본적으로 활성화됩니다. 고객 지원 센터에 연락하여 활성화할 수 있는 향상된 추가 보안 기능을 사용할 수 있습니다. 호스팅되지 않은 고객이 이 기능을 사용하도록 설정하는 기능 및 단계에 대한 자세한 내용은 [보안 및 개인 정보 보호 체크리스트](https://helpx.adobe.com/kr/campaign/kb/acc-security.html#signature-mechanism)에서 확인할 수 있습니다.

>[!CAUTION]
>
>추적 링크를 사용한 푸시 알림 또는 앵커 태그를 사용한 게재 관련 문제가 발생하는 경우 링크 추적을 위해 새 서명 메커니즘을 비활성화하는 것이 좋습니다. 프로시저는 [이 페이지](https://helpx.adobe.com/kr/campaign/kb/acc-security.html#signature-mechanism)에 자세히 설명되어 있습니다

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

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 6 릴리스{#gs-6}

_2020년 3월 9일_

빌드 9032@19f73c5에는 다음 수정 사항이 포함되어 있습니다.

* SSL을 통해 FTP를 사용하는 외부 계정 문제를 해결했습니다. (NEO-20498)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 5 릴리스{#gs-5}

_2019년 12월 17일_

빌드 9032@d6b8062에는 다음 수정 사항이 포함되어 있습니다.

* 모바일(SMS, MMS), 푸시(iOS, Android) 및 소셜 네트워크(Facebook, Twitter)와 같은 통신 채널의 추적 문제를 해결했습니다. (NEO-19595)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 4 릴리스{#gs-4}

_2019년 12월 11일_

빌드 9032@bc4a935에는 다음 수정 사항이 포함되어 있습니다.

* MSSQL 데이터베이스를 사용하여 메시지를 전송할 때 성능 문제를 해결했습니다. (NEO-17558)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 3 릴리스{#gs-3}

_2019년 11월 20일_

빌드 9032@3468c7b에는 다음 수정 사항이 포함되어 있습니다.

* IMS 인증을 통한 로그인 문제를 해결했습니다. (NEO-17312)
* 다중 게재에 대한 누적 보고서를 표시할 때 발생하는 문제를 해결했습니다. (NEO-18165)
* 웹 서버 충돌을 차단하거나 야기할 수 있는 문제를 해결했습니다.

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 2 릴리스{#gs-2}

_2019년 9월 19일_

빌드 9032@cee805c에는 다음 수정 사항이 포함되어 있습니다.

* Salesforce용 CRM 커넥터를 사용하는 경우 발생하는 문제를 해결했습니다. (NEO-17712)
* 트랜잭션 메시지를 보낼 때 성능 문제가 발생할 수 있는 인덱스 문제를 해결했습니다.

### ![](assets/do-not-localize/red_2.png) 릴리스 19.1.4 - 빌드 9032{#release-19-1-4-build-9032}

_2019년 8월 13일_

초기 19.1.4 빌드에는 다음 수정 사항이 포함되어 있습니다.

* 마법사 구성 중 원치 않는 오류 메시지를 생성하는 스케줄러 활동 문제를 해결했습니다. NEO-11662에서 업데이트를 되돌립니다. (NEO-17097)
* 테스트 활동이 두 번 실행될 때 워크플로우를 중지할 수 있는 NEO-12727에 의해 발생하는 회귀 문제를 해결했습니다. (NEO-16835)
* API 호출에서 유효하지 않거나 만료된 세션 토큰이 사용된 경우 잘못된 HTTP 코드(HTTP 403 대신 HTTP 200 OK)가 반환되는 문제를 해결했습니다. (NEO-16826)
* DKIM 키가 더 이상 전자 메일에 포함되지 않아 게재 문제가 발생하는 문제를 해결했습니다. (NEO-16804)
* 워크플로우 예약과 관련된 다양한 문제를 해결했습니다. 워크플로우는 스케줄러 구성을 고려하지 않고 하루에 한 번 실행되도록 예약되었습니다. (NEO-16619, NEO-16426)


## [!DNL Gold Standard] 호환성 매트릭스{#compatibility-matrix-gs}

이 문서에는 **Adobe Campaign Classic[!DNL Gold Standard]** 19.1 빌드에 대해 지원되는 시스템 및 구성 요소의 전체 목록이 있습니다. 이 목록에 포함되지 않은 제품 및 버전은 Adobe Campaign의 해당 버전과 호환되지 않습니다.

>[!CAUTION]
>별도로 언급되지 않는 한 모든 부 릴리스가 지원됩니다.
>
>Adobe Campaign Classic은 이 페이지에 나열된 모든 시스템 및 도구와 호환됩니다. 이러한 타사 시스템 및 도구의 특정 버전이 각각의 작성자와 EOL(End-of-Life)에 도달함에 따라 Adobe Campaign은 더 이상 해당 버전과 호환되지 않으며 이후 제품 릴리스의 호환성 매트릭스에서 제거됩니다. 호환성 매트릭스에 나와 있는 모든 시스템의 지원 버전을 사용하고 있는지 확인하십시오.

### 운영 체제{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x(64비트)</p>
<p>7.x(64비트)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9(64비트)</p>
<p>8(64비트)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x(64비트)</p>
<p><strong>중요:</strong> RHEL을 사용하는 경우 SELinux를 비활성화하거나 설계자가 사용자 지정 SELinux 규칙을 작성하여 활성화된 SELinux가 Campaign 작업에 문제를 일으키지 않는지 확인해야 합니다.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

### 웹 서버{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2016의 10.0</p>
<p>Windows Server 2012 R2의 8.5</p>
<p>Windows Server 2012의 8.0 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>RHEL7용 2.4 - CentOS 7, Debian 8/9, Windows(64비트)</p>
<p>RHEL6용 2.2 - CentOS 6만(64비트)</p>
</td>
</tr>
</tbody>
</table>

### 도구{#Tools-gs}

<table>
<tbody>
<tr>
<td>JDK(Java Development Kit)</td>
<td>
<p>8</p>
<p>이 애플리케이션은 OpenJDK뿐만 아니라 Oracle에서 개발한 JDK(Java Development Kit)에 대해 승인되었습니다.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6(시스템에 임베드된 경우 이전 버전)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

### RDBMS 서버{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS 드라이버는 RDBMS 서버 버전과 일치해야 합니다.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>참고: 위에 지정된 버전으로 PostgreSQL용 Amazon RDS를 사용할 수도 있습니다.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 및 SP2</p>
<p>경고: Adobe Campaign 서버가 Linux에서 실행 중이면 Microsoft SQL Server가 기본 데이터베이스로 지원되지 않습니다.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>경고: DB2 UDB는 새 설치에 허용되지 않습니다.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL은 호스팅 환경을 위한 기본 데이터베이스 서버입니다.

### CRM 커넥터{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce 커넥터 API</td>
<td>
<p>API 버전 37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API 버전 21</p>
<p>API 버전 15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap API - 온-프레미스: 2007년, 2015년, 2016년</p>
<p>Soap API - 온라인: 2015년, 2016년</p>
<p>웹 API - 온-프레미스 및 온라인: 365, 2016, 2016 업데이트 1</p>
</td>
</tr>
</tbody>
</table>

### FDA(Federated Data Access){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 및 SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>버전 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4(HDP 2.4), 3.5(HDP 2.5), 3.6(HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>


### 클라이언트 콘솔 {#ClientConsoleoperatingsystems}

:warning: Campaign 클라이언트 콘솔을 사용하려면 다음 운영 체제와 브라우저가 필요합니다.

### 운영 체제

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10(일본어 인스턴스에 권장)</p>
</td>
</tr>
</tbody>
</table>

#### 브라우저

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### 모바일 SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>모바일 SDK 빌드 1.0.27과 함께 사용할 수 있습니다.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9 - 14</p>
<p>모바일 SDK 빌드 1.0.26과 함께 사용할 수 있으며 32비트 및 64비트 버전 호환됩니다.</p>
</td>
</tr>
</tbody>
</table>

### 브라우저{#Browsers}

다음 브라우저는 웹 액세스에 대한 Campaign과 호환됩니다.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>최신 버전</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>최신 버전</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>최신 버전</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>최신 버전</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
