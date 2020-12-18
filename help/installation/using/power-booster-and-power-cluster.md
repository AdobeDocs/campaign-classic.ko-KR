---
solution: Campaign Classic
product: campaign
title: 전원 부스터 및 전원 클러스터
description: 전원 부스터 및 전원 클러스터
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---


# 전원 부스터 및 전원 클러스터{#power-booster-and-power-cluster}

## 개요 {#overview}

Adobe Campaign은 배포 크기를 조정할 수 있는 사전 패키지된 아키텍처 옵션 2개를 제공합니다.

* **전력 부스터**

   이 옵션은 기본 Adobe Campaign 응용 프로그램 인스턴스에서 분리된 단일 추가 실행 인스턴스를 지원합니다. 전용 실행 인스턴스는 원격으로 또는 제3자에 의해 호스팅될 수 있습니다. 구현 시, 이메일 실행, 추적, 미러 페이지 및 바운스 메시지는 중앙 애플리케이션 기능과 독립적으로 처리됩니다.

* **전원 클러스터**

   이 옵션은 해당 응용 프로그램과 관련하여 기본 Adobe Campaign 응용 프로그램 인스턴스에서 분리된 2-N의 클러스터형 실행 인스턴스를 지원합니다. 클러스터는 원격으로, 분산 배포에서는 그리고 제3자에 의해 호스팅될 수 있습니다. 프로세스 격리 기능을 통해 얻을 수 있는 이점 외에도 Adobe Campaign Power Cluster 옵션을 사용하면 SLA 또는 성능을 간소화하기 위해 상업용 하드웨어를 사용하여 중복성을 지원하고 전략을 확장할 수 있습니다.

![](assets/architectural_options_diagram.png)

## 자격 조건을 갖춘 응용 프로그램 {#eligible-applications}

Power Boxer 및 Power Cluster 옵션은 다음 응용 프로그램에서 사용할 수 있습니다.

* 캠페인
* 게재
* 메시지 센터

## 아키텍처 추천 매트릭스 {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>표준 아키텍처</strong><br /> </td> 
   <td> <strong>전력 부스터</strong><br /> </td> 
   <td> <strong>전원 클러스터</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 이메일 캠페인 및 아웃바운드 상호 작용<br /> </td> 
   <td> 매월 최대 3천만 개의 이메일<br /> </td> 
   <td> 매월 30~1억 개의 이메일<br /> </td> 
   <td> 매월 1억 개 이상의 이메일<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 <br /> </td> 
   <td> 실행 서버당 시간당 50,000회<br /> </td> 
   <td> 실행 서버당 시간당 50,000회<br /> </td> 
   <td> 실행 서버당 시간당 50,000회<br /> </td> 
  </tr> 
  <tr> 
   <td> 가용성<br /> </td> 
   <td> 기본 데이터베이스<br /> </td> 
   <td> 실행 인스턴스<br />에 대한 유지 관리 기간 및 다운타임을 제외한 24/7 </td> 
   <td> 24/7/365 서비스 가능<br /> </td> 
  </tr> 
  <tr> 
   <td> 보안<br /> </td> 
   <td> 데이터 마트는 공용 인터넷<br />에서 액세스할 수 있습니다. </td> 
   <td> 데이터 마트는 정면형 인터넷 지원 구성 요소<br /> </td> 
   <td> 데이터 마트는 정면형 인터넷 지원 구성 요소<br /> </td> 
  </tr> 
  <tr> 
   <td> 배포 템플릿<br /> </td> 
   <td> 하나의 사이트에서 모두(사내 또는 클라우드에 있을 수 있음)<br /> </td> 
   <td> 클라우드에서 실행할 수 있는 사내 마케팅<br /> </td> 
   <td> 클라우드에서 실행하는 사내에서의 마케팅;가능한 다른 geos의 실행<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 추천 {#recommendations}

* 실행 인스턴스는 서비스 전용이어야 합니다. 가입하지 않은 서비스용 패키지를 설치할 수 없습니다. 예를 들어 **Message Center** 서비스에 대한 **Power Boxth** 옵션을 구독하는 경우 전용 실행 인스턴스에만 **[!UICONTROL Execution of transactional messages]** 패키지를 설치할 수 있습니다. 사용권 계약을 확인하십시오.
* 전용 인스턴스(또는 클러스터)는 Adobe Campaign 인스턴스이므로, 권장 사항은 기본 인스턴스와 같습니다. 자세한 내용은 [이 문서](../../production/using/foreword.md)를 참조하십시오.
* 데이터베이스/하드웨어 구성 요소 POV에서 인스턴스를 올바르게 구성하려면 Adobe Campaign Professional Services에 문의하십시오.

