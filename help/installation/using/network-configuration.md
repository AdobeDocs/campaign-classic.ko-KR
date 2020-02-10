---
title: 네트워크 구성
seo-title: 네트워크 구성
description: 네트워크 구성
seo-description: null
page-status-flag: never-activated
uuid: 17357170-7440-4603-bea6-2e4b9086ae72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 639d2f42-e397-4694-942c-b2b8ad94ce9c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 네트워크 구성{#network-configuration}

## 프로세스 간 커뮤니케이션 {#communication-between-processes}

애플리케이션의 특정 프로세스는 다른 사용자와 통신하거나 LAN 및 인터넷에 액세스해야 합니다. 즉, 이러한 프로세스에 대해 일부 TCP 포트를 열어야 합니다.

Adobe Campaign 플랫폼의 다양한 애플리케이션 서버 간 내부 통신에 대해 임베드된 Apache Tomcat 포트를 우선 순위(기본적으로 8080)로 사용합니다.

### 배달 서버 {#delivery-server}

배달 서버(**nlserver mta**)의 경우 다음 포트를 열어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 대상<br /> </td> 
   <td> 댓글<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> 전자 메일 브로드캐스트용 SMTP 트래픽입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp(도메인)<br /> </td> 
   <td> DNS 서버<br /> </td> 
   <td> DNS 쿼리<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp(기본 포트)<br /> </td> 
   <td> SMS 게이트웨이<br /> </td> 
   <td> SMS 트래픽을 NetSize SMS 라우터 [옵션]로 전송하는 데 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 통계 서버<br /> </td> 
   <td> 통계 서버에 액세스합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 인바운드 메일 {#inbound-mail}

인바운드 메일 복구 프로세스(**nlserver inMail**)의 경우 다음 포트를 열어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 대상<br /> </td> 
   <td> 댓글<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp(pop3)<br /> </td> 
   <td> 내부 메일 서버<br /> </td> 
   <td> POP3 트래픽을 사용하여 바운스 메시지를 선택합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> 내부 메일 서버<br /> </td> 
   <td> 사전 정의된 규칙에 의해 자동으로 처리되지 않은 나머지 바운스 메시지를 보내는 SMTP 트래픽입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 애플리케이션 서버 {#application-server}

응용 프로그램 서버(**nlserver 웹**)의 경우 다음 포트를 열어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 대상<br /> </td> 
   <td> 댓글<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp(http)<br /> 443/tcp(https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> HTTP 또는 HTTPS 트래픽(전달 가능 오퍼에 대한 포함)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Adobe Campaign 플랫폼의 여러 애플리케이션 서버가 서로 통신해야 하는 경우 Apache Tomcat 서버 포트를 사용하는 것이 좋습니다(기본적으로:8080)을 참조하십시오. 즉, 이러한 서버 사이에 포트를 열어야 합니다.

### SMS 배달 상태 {#sms-delivery-status}

SMS 배달(**nlserver sms**)을 추적하려면 다음 포트가 열려 있어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 대상<br /> </td> 
   <td> 댓글<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp(기본 포트)<br /> </td> 
   <td> SMS 게이트웨이<br /> </td> 
   <td> NetSize SMS 게이트웨이 [옵션]에서 관리하는 배달 큐 상태를 쿼리합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 리치 클라이언트 {#rich-client}

Adobe Campaign 리치 클라이언트(**nlclient**)의 경우 다음 포트가 열려 있어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 대상<br /> </td> 
   <td> 댓글<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p>443/tcp(https)</p><br /> </td> 
   <td> 애플리케이션 서버<br /> </td> 
   <td> SOAP 트래픽(HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 데이터베이스 액세스 {#database-access}

데이터베이스를 사용하는 모든 구성 요소는 데이터베이스에 연결할 수 있어야 합니다. 이는 리디렉션 서버를 제외하고 단독으로 작동할 수 있는 대부분의 구성 요소와 HTTP(또는 HTTPS)만 사용하여 응용 프로그램 서버와 통신하는 가상 Win32 클라이언트를 제외한 대부분의 구성 요소에 대한 경우입니다.

기본 포트는 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td> 데이터베이스 유형<br /> </td> 
   <td> 포트(기본값)<br /> </td> 
   <td> 대상<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> 데이터베이스 서버<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 외부 액세스 {#external-access}

또한 Adobe Campaign에서 직접 실행한 이메일 캠페인을 볼 수 있도록 특정 구성 요소를 공개 인터넷에서 액세스할 수 있어야 합니다. 즉, 구성 요소에 대해 일부 포트를 열어야 합니다.

### 리디렉션 서버 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 수신 포트<br /> </td> 
   <td> 위치<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 어디에서나 추적된 링크를 클릭할 때마다 서버에 HTTP 요청이 생성됩니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 외부 웹 서버 {#external-web-server}

이 서버는 웹 양식, 미러 페이지 등을 호스팅합니다. 다음 포트를 열어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 수신 포트<br /> </td> 
   <td> 위치<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 어디에서나 웹 양식을 Adobe Campaign 플랫폼에서 직접 관리하거나 미러 페이지를 사용할 때 필요합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 내부 응용 프로그램 서버(웹) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> 수신 포트<br /> </td> 
   <td> 위치<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 씬 클라이언트 또는 리치 클라이언트를 실행하는 모든 컴퓨터<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Adobe Experience Manager와 통합 {#integration-with-adobe-experience-manager}

설치가 &quot;온-프레미스&quot;인 경우 Adobe Campaign과 Adobe Experience Manager를 통합하려면 여러 포트를 열어야 합니다. 이 통합 구성에 대한 자세한 내용은 [자세한 설명서를](../../integrations/using/about-adobe-experience-manager.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> 수신 포트<br /> </td> 
   <td> 설명<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Adobe Campaign에 대한 AEM 연결<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> AEM의 "작성" 및 "게시" 인스턴스에 Adobe Campaign이 연결됩니다. 열 포트는 AEM 구성에 따라 기본 포트와 다를 수 있습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 대역폭 {#bandwidth}

고려할 네트워크 구성의 다른 키 매개 변수입니다. 이메일 방송 중에는 거의 항상 널리 발송되고 수요가 많습니다. 다음은 Adobe 경험을 기반으로 한 구성의 몇 가지 예입니다.

* 시간당 10,000개의 이메일에 대해 1MB/s(평균 크기 30KB)
* 시간당 100,000개의 이메일에 대해 8-10Mb/s(평균 크기 30Kb)

대역폭에 대한 제약 조건이 있는 경우 수요가 낮은 밤 동안 캠페인을 실행하도록 예약할 수 있습니다.
