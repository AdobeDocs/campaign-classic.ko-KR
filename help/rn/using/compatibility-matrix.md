---
product: campaign
title: Campaign Classic용 호환성 매트릭스
description: Campaign Classic 호환성 매트릭스
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 9d5519bf66baace9b3ccf5275727a44cb58f4795
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 99%

---

# 호환성 매트릭스 {#compatibility-matrix}

Adobe Campaign Classic v7 [최신 빌드](../../rn/using/latest-release.md)는 이 페이지의 목록에 있는 모든 시스템 및 도구와 호환됩니다. 이 서드파티 시스템 및 도구의 특정 버전이 각 제작자가 발표한 EOL(End-of-Life)에 도달하면 해당 버전은 더 이상 Adobe Campaign과 호환되지 않으며, 이후 제품 릴리스의 호환성 매트릭스에서 제거됩니다. 문제가 생기지 않도록 호환성 매트릭스에 나와 있는 모든 시스템에 대해 지원 버전을 사용하고 있는지 확인하십시오. 더 이상 사용되지 않는 항목에 대한 자세한 내용은 [이 페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

별도로 언급되지 않는 한 모든 마이너 릴리스도 지원됩니다.

>[!CAUTION]
>
>이 매트릭스는 정기적으로 새로 지원되는 시스템 및 도구를 추가하고 더 이상 사용되지 않는 항목을 제거하는 방식으로 업데이트됩니다.

## 운영 체제 {#OperatingSystems}

온-프레미스/하이브리드 고객은 아래 나열된 운영 체제 중 하나에 Adobe Campaign을 설치해야 합니다. [이 페이지](../../installation/using/application-server.md)에서 Campaign Classic v7 설치 단계에 대해 자세히 알아보십시오.

<table> 
<tbody> 
<td><strong>운영 체제</strong></td>
<td><strong>운영 체제 버전</strong></td>
<td><strong>최소 Campaign 버전</strong></td>
<tr>
<td>
<p>Debian</p>
</td>
<td>
<p>11</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>RHEL(Red Hat Enterprise Linux)</p>
</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Windows Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>RHEL을 사용하려면 [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux)를 비활성화하거나, 아키텍트에게 활성화된 SELinux가 Campaign 작업에 문제를 일으키지 않는지 확인하기 위한 사용자 정의 SELinux 규칙 작성을 요청해야 합니다.

## 웹 서버 {#WebServers}

온프레미스/하이브리드 고객은 운영 체제에 따라 Campaign을 아래 나열된 웹 서버 중 하나에 통합해야 합니다. [이 페이지](../../installation/using/integration-into-a-web-server-for-windows.md)(Windows의 경우) 및 [이 페이지](../../installation/using/integration-into-a-web-server-for-linux.md)(Linux의 경우)에서 웹 서버 구성 단계에 대해 자세히 알아보십시오.

<table>
<tbody>
<td><strong>웹 서버</strong></td>
<td><strong>웹 서버 버전</strong></td>
<tr>
<td>
<p>Microsoft IIS</p>
</td>
<td>
<p>10.0</p>
</td>
</tr>
<tr>
<td>
<p>Apache</p>
</td>
<td>
<p>2.4</p>
</td>
</tr>
</tbody>
</table>

## 도구 {#Tools}

온-프레미스/하이브리드 고객은 아래 나열된 도구를 설치 및 구성해야 합니다. [자세히 알아보기](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>도구</strong></td>
<td><strong>버전</strong></td>
<td><strong>최소 Campaign 버전</strong></td>
<tr>
<td><p>JDK(Java Development Kit)</p>
<p><a href="../../installation/using/application-server.md#jdk" target="_blank">이 페이지</a>에서 자세히 알아보십시오.</p>
</td>
<td>
<p>17</p>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>v7.4.1부터 필수</p>
<p>v7.4.1부터 필수</p>
<p>v7.4.1까지</p>
<p>v7.4.1까지</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7(시스템에 임베드된 경우 이전 버전)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## RDBMS(관계 데이터베이스 관리 시스템) {#RDBMSservers}

온-프레미스/하이브리드 고객은 아래 나열된 데이터베이스 중 하나를 설치 및 구성해야 합니다. [자세히 알아보기](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>데이터베이스 시스템</strong></td>
<td><strong>데이터베이스 버전</strong></td>
<td><strong>최소 Campaign 버전</strong></td>
<tr>
<td>
<p>Oracle</p>
</td>
<td>
<p>23c</p>
<p>21c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>PostgreSQL</p>
</td>
<td>
<p>16.x</p>
<p>15.x</p>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.4.1</p>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Microsoft SQL Server</p>
</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS 드라이버는 RDBMS 서버 버전과 일치해야 합니다.
>
>* Campaign 서버가 Linux에서 실행 중인 경우 Microsoft SQL Server가 기본 데이터베이스로 지원되지 않습니다. [자세히 알아보기](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* 위에 지정된 버전으로 PostgreSQL용 Amazon RDS를 사용할 수도 있습니다.
>
>* PostgreSQL은 호스팅/관리 클라우드 서비스 환경용 RDBMS입니다.


## CRM 커넥터 {#CRMconnectors}

Adobe Campaign과 호환되는 CRM(고객 관계 관리) 시스템 목록은 다음과 같습니다. Campaign CRM 커넥터에 대해 [자세히 알아보세요](../../platform/using/crm-connectors.md).

<table>
<tbody>
<tr>
<td>
<p>Salesforce 커넥터 API</p>
</td>
<td>
<p>API 버전 49</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Dynamics 커넥터</p>
</td>
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
<td><strong>최소 Campaign 버전</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

또한, **하이브리드** 및 **온프레미스** 환경에서는 다음 외부 데이터베이스 시스템과 Campaign을 연결할 수 있습니다. 이러한 시스템은 Campaign **Managed Services**(호스팅된) 환경과 **호환되지 않습니다**.

<table>
<tbody>
<td><strong>데이터베이스 시스템</strong></td>
<td><strong>데이터베이스 버전</strong></td>
<td><strong>최소 Campaign 버전</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>21c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>버전 1 SPS 12</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022(Campaign v7.4부터)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 및 SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x(최신 버전)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4(HDP 2.4), 3.5(HDP 2.5), 3.6(HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## 클라이언트 콘솔 {#ClientOS}

[Campaign 클라이언트 콘솔](../../installation/using/installing-the-client-console.md)을 사용하려면 다음 운영 체제와 브라우저가 **필요**&#x200B;합니다.

### 운영 체제

<table>
<tbody>
<td><strong>시스템</strong></td>
<td><strong>OS 버전</strong></td>
<td><strong>최소 Campaign 버전</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2 런타임 {#webview}

Campaign 클라이언트 콘솔을 사용하려면 Microsoft Edge WebView2 런타임 최신 버전이 필수입니다.

[Microsoft 개발자 사이트](https://www.adobe.com/go/acc-ms-webview2-runtime-download_kr)에서 Microsoft Edge WebView2를 다운로드합니다.


## 모바일 SDK {#MobileSDK}

데이터 수집 UI에서 Adobe Campaign 확장을 구성하여 Adobe Experience Platform 모바일 SDK를 통해 Campaign을 [푸시 알림 보내기](../../delivery/using/about-mobile-app-channel.md)에 사용할 수 있습니다.

Campaign v7.4부터 Campaign SDK는 [더 이상 사용되지 않습니다](deprecated-features.md). 기존 구현을 AEP 모바일 SDK로 원활하게 전환할 수 있도록 아래 목록의 운영 체제에서는 계속 사용할 수 있습니다<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7 - 14</p>
<p>모바일 SDK 빌드 1.1.1과 함께 사용할 수 있습니다</p>
<p>Android 13 및 14은 Campaign v7.4부터 지원됩니다.</p>
<p>Android 12는 Campaign v7.3부터 지원됩니다</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9 - 17</p>
<p>모바일 SDK 빌드 1.0.26과 함께 사용할 수 있습니다.</p>
<p>Apple iOS 15은 Campaign v7.3부터 지원됩니다 </p>
<p>Apple iOS 16 및 17은 Campaign v7.4부터 지원됩니다.</p>
</td>
</tr>
</tbody>
</table>

## 브라우저 {#Browsers}

다음 브라우저의 최신 버전은 웹용 Campaign 액세스와 호환됩니다. 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=ko#use-the-web-interface-){target=_blank}를 참조하십시오.

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Campaign Classic 릴리스 정보](../../rn/using/latest-release.md)
>* [Campaign 일반 아키텍처](../../installation/using/general-architecture.md)
>* [하드웨어 크기 조정 권장 사항](../../technotes/using/hardware-sizing.md)
>* [사용되지 않는 기능 및 시스템](../../rn/using/deprecated-features.md)
>* [빌드 업그레이드 프로시저](../../production/using/build-upgrade.md)
