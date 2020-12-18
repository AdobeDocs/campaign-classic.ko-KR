---
solution: Campaign Classic
product: campaign
title: 호환성 매트릭스
description: 호환성 매트릭스
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: aabab5367ea4a26837fa3dc94a36fbbfa48d59e3
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 83%

---


# 호환성 매트릭스{#compatibility-matrix}

이 문서에는 최신 빌드 **Adobe Campaign Classic(v6.11 및 v7)**&#x200B;에 대해 지원되는 모든 시스템 및 구성 요소가 나열됩니다. 이 목록에 포함되지 않은 제품 및 버전은 Adobe Campaign과 호환되지 않습니다.

## 중요 정보{#important-notes}

이 매트릭스는 지원되는 새 항목이 추가되고 더 이상 사용되지 않는 항목이 제거되면서 정기적으로 업데이트됩니다.

별도로 언급되지 않는 한 모든 부 릴리스가 지원됩니다.

Adobe Campaign Classic은 이 페이지에 나열된 모든 시스템 및 도구와 호환됩니다. 이러한 타사 시스템 및 도구의 특정 버전이 각각의 작성자와 EOL(End-of-Life)에 도달함에 따라 Adobe Campaign은 더 이상 해당 버전과 호환되지 않으며 이후 제품 릴리스의 호환성 매트릭스에서 제거됩니다. 호환성 매트릭스에 나와 있는 모든 시스템의 지원 버전을 사용하고 있는지 확인하십시오.

더 이상 사용되지 않는 항목에 대한 자세한 내용은 [이 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

## 운영 체제{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>7.x(64비트)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>8(64비트)</p>
<p>9(64비트)</p>
<p>10(64비트)</p>
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
<p>2012</p>
<p>2012 R2</p>
<p>2016</p>
</td>
</tr>
</tbody>
</table>

## 웹 서버{#WebServers}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>Windows Server 2012의 8.0 - Windows 8</p>
<p>Windows Server 2012 R2의 8.5</p>
<p>Windows Server 2016의 10.0</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>RHEL7용 2.4 - CentOS 7, Debian 8/9, Windows(64비트)</p>
</td>
</tr>
</tbody>
</table>

## 도구{#Tools}

<table>
<tbody>
<tr>
<td>JDK(Java Development Kit)</td>
<td>
<p>8</p>
<p>9</p>
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

## RDBMS 드라이버{#RDBMSdrivers}

다음 RDBMS 드라이버가 지원됩니다.

* Oracle SQL*Net 11

* Oracle SQL*Net 12

* PostgreSQL(libpq)

* SQLServer

* DB2(ODBC 드라이버)


>[!NOTE]
>
>RDBMS 드라이버는 RDBMS 서버 버전과 일치해야 합니다.

## RDBMS 서버{#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>11g R2</p>
<p>12c</p>
<p>18c</p>
<p>19c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
<p>참고: 위에 지정된 버전으로 PostgreSQL용 Amazon RDS를 사용할 수도 있습니다.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2012 - SP1 및 SP2</p>
<p>2014</p>
<p>2016년</p>
<p>2017</p>
<p>경고: Adobe Campaign 서버가 Linux에서 실행 중인 경우 Microsoft SQL Server가 기본 데이터베이스로 지원되지 않습니다. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">자세히 알아보기</a></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL은 호스팅 환경을 위한 기본 데이터베이스 서버입니다.

## CRM 커넥터{#CRMconnectors}

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
<p>API 버전 15</p>
<p>API 버전 21</p>
</td>
</tr>
<tr><td>Oracle On Demand API</td>
<td>
<p>웹 서비스 v1.0 API</p>
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

## FDA (FEDERATED DATA ACCESS){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>11g</p>
<p>12c</p>
<p>18c</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>9.4.x</p>
<p>9.5.x</p>
<p>9.6.x</p>
<p>10.x</p>
<p>11.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2012 SP1 및 SP2</p>
<p>2014년</p>
<p>2016년</p>
<p>2017년</p>
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
<p>15.0</p>
<p>15.10</p>
<p>16</p>
<p>16.20</p>
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
<p>버전 1 SP12 이상</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4(HDP 2.4), 3.5(HDP 2.5), 3.6(HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## 클라이언트 콘솔 운영 체제{#ClientConsoleoperatingsystems}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2012년</p>
<p>2016년</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>8</p>
<p>10(일본어 인스턴스에 권장)</p>
</td>
</tr>
</tbody>
</table>

## 모바일 SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x</p>
<p>8.x</p>
<p>9.0</p>
<p>모바일 SDK 빌드 1.0.27과 함께 사용할 수 있습니다.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9</p>
<p>iOS 10</p>
<p>iOS 11</p>
<p>iOS 12</p>
<p>iOS 13</p>
<p>모바일 SDK 빌드 1.0.26과 함께 사용할 수 있으며 32비트 및 64비트 버전 호환됩니다.</p>
</td>
</tr>
</tbody>
</table>

## 브라우저{#Browsers}

Internet Explorer 버전 11이 지원됩니다.

다음 브라우저의 경우 최신 버전이 지원됩니다.

* Microsoft Edge

* Firefox

* Chrome

* Safari

## Experience Cloud 통합{#ExperienceCloudintegrations}

Adobe 솔루션과의 통합은 이 [섹션](https://docs.adobe.com/content/help/en/campaign-classic/using/integrating-with-adobe-experience-cloud/about-campaign-integrations.html#experience-cloud-integrations)을 참조하십시오.

## 비슷한 항목 더 보기{#Morelikethis}

* [Campaign Classic 릴리스 노트](https://docs.adobe.com/content/help/ko-KR/campaign-classic/using/release-notes/latest-release.html)
* [설치 안내서](https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/general-architecture.html)
* [사용되지 않는 기능 및 시스템](https://helpx.adobe.com/kr/campaign/kb/deprecated-and-removed-features.html)
* [빌드 업그레이드 프로시저](https://helpx.adobe.com/kr/campaign/kb/acc-build-upgrade.html)
* [19.0 릴리스의 Campaign Classic 호환성 표](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix-19-0.html)
* [19.1 릴리스의 Campaign Classic 호환성 표](https://helpx.adobe.com/kr/campaign/kb/compatibility-matrix-19-1.html)

