---
product: campaign
title: 네트워크 구성
description: 시스템 통신 지침 학습
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---

# 네트워크 구성{#network-configuration}

![](../../assets/v7-only.svg)

## 프로세스 간 통신 {#communication-between-processes}

애플리케이션의 특정 프로세스는 다른 사용자와 통신하거나 LAN 및 인터넷에 액세스해야 합니다. 즉, 이러한 프로세스에 대해 일부 TCP 포트를 열어야 합니다.

Adobe Campaign 플랫폼의 다양한 애플리케이션 서버 간 내부 통신을 위해 포함된 Apache Tomcat 포트를 우선 순위(기본적으로 8080)로 사용하십시오.

### 배달 서버 {#delivery-server}

게재 서버(**nlserver mta**). 다음 포트를 열어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 대상<br /> </td> 
   <td> 댓글<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 어디에서나<br /> </td> 
   <td> 전자 메일 브로드캐스트에 대한 SMTP 트래픽.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp(도메인)<br /> </td> 
   <td> DNS 서버<br /> </td> 
   <td> DNS 쿼리<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp(기본 포트)<br /> </td> 
   <td> SMS 게이트웨이<br /> </td> 
   <td> NetSize SMS 라우터 [옵션]로 SMS 트래픽을 보내는 데 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> 통계 서버<br /> </td> 
   <td> 통계 서버에 액세스합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 인바운드 메일 {#inbound-mail}

인바운드 메일 복구 프로세스(**nlserver inMail**). 다음 포트를 열어야 합니다.

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
   <td> 바운스 메시지를 선택하는 POP3 트래픽.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp(smtp)<br /> </td> 
   <td> 내부 메일 서버<br /> </td> 
   <td> 사전 정의된 규칙에 의해 자동으로 처리되지 않는 나머지 바운스 메시지를 보내기 위한 SMTP 트래픽.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 애플리케이션 서버 {#application-server}

애플리케이션 서버(**nlserver 웹**). 다음 포트를 열어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 포트<br /> </td> 
   <td> 대상<br /> </td> 
   <td> 댓글<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp(http)<br /> 443/tcp(https)<br /> </td> 
   <td> 어디에서나<br /> </td> 
   <td> HTTP 또는 HTTPS 트래픽(게재 기능 오퍼용 포함).<br /> </td> 
  </tr> 
 </tbody> 
</table>

Adobe Campaign 플랫폼의 여러 애플리케이션 서버가 서로 통신해야 하는 경우 Apache Tomcat 서버의 포트를 사용하는 것이 좋습니다(기본적으로: 리디렉션 모듈 통합이 수행된 웹 서버의 HTTP 포트보다 8080). 즉, 이 서버 간에 포트를 열어야 합니다.

### SMS 게재 상태 {#sms-delivery-status}

SMS 게재를 추적하려면 (**nlserver sms**). 다음 포트를 열어야 합니다.

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
   <td> NetSize SMS 게이트웨이 [옵션]에서 관리하는 게재 큐 상태를 쿼리합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 리치 클라이언트 {#rich-client}

Adobe Campaign 리치 클라이언트의 경우(**nlclient**). 다음 포트를 열어야 합니다.

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

데이터베이스를 사용하는 모든 구성 요소는 해당 데이터베이스에 연결할 수 있어야 합니다. 이는 리디렉션 서버를 제외한 대부분의 구성 요소에 대해 단독으로 작동할 수 있으며 HTTP(또는 HTTPS)만 사용하여 응용 프로그램 서버와 통신하는 가상 Win32 클라이언트를 사용합니다.

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

또한 Adobe Campaign에서 직접 실행된 이메일 캠페인을 볼 수 있도록 특정 구성 요소를 공개 인터넷에서 액세스할 수 있어야 합니다. 즉, 일부 포트는 구성 요소에 대해 열어야 합니다.

### 리디렉션 서버 {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> 수신 대기 포트<br /> </td> 
   <td> 위치<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 어디든지 추적된 링크를 클릭할 때마다 서버에서 HTTP 요청이 생성됩니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 외부 웹 서버 {#external-web-server}

이 서버는 웹 양식, 미러 페이지 등을 호스팅합니다. 다음 포트를 열어야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> 수신 대기 포트<br /> </td> 
   <td> 위치<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 어디든지 Adobe Campaign 플랫폼에서 직접 웹 양식을 관리하거나 미러 페이지를 사용할 때 필요합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 내부 응용 프로그램 서버(웹) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> 수신 대기 포트<br /> </td> 
   <td> 위치<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp(http)</p><p> 443/tcp(https)</p><br /> </td> 
   <td> 씬 클라이언트 또는 리치 클라이언트를 실행하는 모든 컴퓨터<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Adobe Experience Manager과 통합 {#integration-with-adobe-experience-manager}

Adobe Campaign과 Adobe Experience Manager을 통합하려면 설치가 &quot;온-프레미스&quot;인 경우 몇 개의 포트를 열어야 합니다. 이 통합 구성에 대한 자세한 내용은 [세부 설명서](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> 수신 대기 포트<br /> </td> 
   <td> 설명<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> Adobe Campaign에 대한 AEM 연결<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502년</p><p> 4503년</p><br /> </td> 
   <td> AEM "작성" 및 "게시" 인스턴스에 Adobe Campaign이 연결됩니다. 열 포트는 AEM 구성에 따라 기본 포트와 다를 수 있습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 대역폭 {#bandwidth}

고려할 네트워크 구성의 다른 키 매개 변수입니다. 이메일 방송 중에 거의 항상 아웃바운드 및 많은 수요가 발생합니다. 다음은 Adobe 경험을 기반으로 한 몇 가지 구성 예입니다.

* 시간당 10,000개의 이메일에 대해 1Mb/s(평균 크기 30Kb)
* 시간당 100,000개의 이메일에 대해 8~10Mb/s(평균 크기 30Kb)

대역폭 측면에서 제한이 있는 경우 수요가 낮은 밤 동안 캠페인 실행을 예약할 수 있습니다.
