---
product: campaign
title: Campaign Classic용 호환성 매트릭스
description: Campaign Classic 호환성 매트릭스
feature: Overview
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 1bb1365ce5a4eb89447c5d736a42cd470c7f3bba
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 100%

---

# 호환성 매트릭스{#compatibility-matrix}

![](../../assets/v7-only.svg)

이 문서에는 **Adobe Campaign Classic v7**&#x200B;의 [최신 빌드](../../rn/using/latest-release.md)를 지원하는 모든 시스템 및 구성 요소가 나열되어 있습니다. 이 목록에 포함되지 않은 제품과 버전은 Adobe Campaign과 호환되지 않습니다.

[!DNL Gold Standard]사용자인 경우 [[!DNL Gold Standard] 호환성 매트릭스](../../rn/using/gold-standard.md#compatibility-matrix-gs)를 참조하십시오.

## 중요 정보{#important-notes}

별도로 언급되지 않는 한 모든 부 릴리스가 지원됩니다.

[최신 빌드](../../rn/using/latest-release.md)에서 Adobe Campaign Classic은 이 페이지에 나열된 모든 시스템 및 도구와 호환됩니다. 이러한 타사 시스템 및 도구의 특정 버전이 각각의 작성자와 EOL(End-of-Life)에 도달함에 따라 Adobe Campaign은 더 이상 해당 버전과 호환되지 않으며 이후 제품 릴리스의 호환성 매트릭스에서 제거됩니다. 호환성 매트릭스에 나와 있는 모든 시스템의 지원 버전을 사용하고 있는지 확인하십시오.

더 이상 사용되지 않는 항목에 대한 자세한 내용은 [이 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

>[!CAUTION]
>
>이 매트릭스는 지원되는 새 항목이 추가되고 더 이상 사용되지 않는 항목이 제거되면서 정기적으로 업데이트됩니다.

## 운영 체제{#OperatingSystems}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x(64비트) </br><strong>중요 사항:</strong> CentOS Linux 8은 2021년 12월 31일에 EOL(수명 종료)됩니다. 자세한 내용은 <a href="../../rn/using/deprecated-features.md">더 이상 사용하지 않는 기능</a> 페이지를 참조하세요.</p>
<p>7.x(64비트)</p>
<p><strong>중요:</strong> RHEL을 사용하는 경우 SELinux를 비활성화하거나 설계자가 사용자 지정 SELinux 규칙을 작성하여 활성화된 SELinux가 Campaign 작업에 문제를 일으키지 않는지 확인해야 합니다.</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>10(64비트)</p>
<p>9(64비트)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x(64비트)</p>
<p>7.x(64비트)</p>
<p><strong>중요:</strong> RHEL을 사용하는 경우 SELinux를 비활성화하거나 설계자가 사용자 지정 SELinux 규칙을 작성하여 활성화된 SELinux가 Campaign 작업에 문제를 일으키지 않는지 확인해야 합니다.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2019(7.2.1 릴리스 시작)</p>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
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
<p>Windows Server 2016의 10.0 및 2019</p>
<p>Windows Server 2012 R2의 8.5</p>
<p>Windows Server 2012의 8.0 - Windows 8</p>
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
<p>11</p>
<p>9</p>
<p>8</p>
<p>이 애플리케이션은 OpenJDK뿐만 아니라 Oracle에서 개발한 JDK(Java Development Kit)에 대해 승인되었습니다.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>7(시스템에 임베드된 경우 이전 버전)</p>
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

## RDBMS(관계 데이터베이스 관리 시스템){#RDBMSservers}

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p><strong>참고:</strong> 위에 지정된 버전을 통해 PostgreSQL용 Amazon RDS도 사용할 수 있습니다.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016년</p>
<p>2014</p>
<p>2012 - SP1 및 SP2</p>
<p><strong>중요:</strong> Campaign 서버가 Linux에서 실행 중인 경우 Microsoft SQL Server가 기본 데이터베이스로 지원되지 않습니다. <a href="../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers">자세히 알아보기</a></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS 드라이버는 RDBMS 서버 버전과 일치해야 합니다.
>
>* PostgreSQL은 호스팅 환경용 RDBMS입니다.


## CRM 커넥터{#CRMconnectors}

Adobe Campaign과 호환되는 CRM(고객 관계 관리) 시스템 목록은 다음과 같습니다. Campaign CRM 커넥터에 대해 [자세히 알아보세요](../../platform/using/crm-connectors.md).

<table>
<tbody>
<tr>
<td>Salesforce 커넥터 API</td>
<td>
<p>API 버전 49</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics 커넥터</td>
<td>
<p>웹 API</p>
</td>
</tr>
</tbody>
</table>

## FDA(Federated Data Access){#FederatedDataAccessFDA}

Adobe Campaign [Federated Data Access 모듈](../../installation/using/about-fda.md)과 호환되는 외부 데이터베이스 목록은 다음과 같습니다. 호환성은 [호스팅 모델](../../installation/using/hosting-models.md)에 따라 다릅니다.

**Managed Services**(호스팅), **하이브리드**, **온프레미스** 환경에서는 다음 외부 데이터베이스 시스템과 Campaign을 연결할 수 있습니다.

<table>
<tbody>
<td><strong>데이터베이스 시스템</strong></td>
<td><strong>데이터베이스 버전</strong></td>
<td><strong>Campaign 버전</strong></td>
<tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>최소 7.2.1</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>최소 7.2.1</td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>최소 v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
</td>
<td>최소 v7.0 19.1.4</td>
</tr>
</tbody>
</table>

또한 **하이브리드** 및 **온프레미스** 환경에서는 Campaign을 다음과도 연결할 수 있습니다.

<table>
<tbody>
<td><strong>데이터베이스 시스템</strong></td>
<td><strong>데이터베이스 버전</strong></td>
<td><strong>Campaign 버전</strong></td>
<tr>
<td>Vertica</td>
<td> </td>
<td>최소 v7.0 19.1.4</td>
</tr>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td>최소 v7.0 19.1.4</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>최소 v7.0</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019년</p>
<p>2017년</p>
<p>2016년</p>
<p>2014년</p>
<p>2012 SP1 및 SP2</p>
</td>
<td>최소 v7.0</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
<td>최소 v7.0</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
<td>최소 v7.0</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
<td>최소 v7.0</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td>최소 v7.0</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>버전 1 SPS 12</p>
</td>
<td>최소 v7.0</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4(HDP 2.4), 3.5(HDP 2.5), 3.6(HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td>최소 v7.0</td>
</tr>
</tbody>
</table>





## 클라이언트 콘솔 {#ClientConsoleoperatingsystems}

[Campaign 클라이언트 콘솔](../../installation/using/installing-the-client-console.md)을 사용하려면 다음 운영 체제와 브라우저가 **필요**&#x200B;합니다.

### 운영 체제

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2019(7.2.1 릴리스 시작)</p>
<p>2016년</p>
<p>2012년</p>
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

### 브라우저

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


## 모바일 SDK{#MobileSDK}

Campaign을 사용하여 아래 목록의 운영 체제에서 [푸시 알림을 보낼](../../delivery/using/about-mobile-app-channel.md) 수 있습니다. 연결된 [모바일 SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)를 사용합니다.

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

## 브라우저{#Browsers}

다음 브라우저는 [웹 액세스](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-)용 Campaign과 호환됩니다.

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


## 비슷한 항목 더 보기{#Morelikethis}

* [Campaign Classic 릴리스 정보](../../rn/using/latest-release.md)
* [Campaign 일반 아키텍처](../../installation/using/general-architecture.md)
* [하드웨어 크기 조정 권장 사항](../../technotes/using/hardware-sizing.md)
* [사용되지 않는 기능 및 시스템](../../rn/using/deprecated-features.md)
* [업그레이드 프로시저 빌드](../../production/using/build-upgrade.md)
