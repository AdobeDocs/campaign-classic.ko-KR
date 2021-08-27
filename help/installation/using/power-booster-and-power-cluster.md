---
product: campaign
title: 전원 부스터 및 전원 클러스터
description: 전원 부스터 및 전원 클러스터
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# 전원 부스터 및 전원 클러스터{#power-booster-and-power-cluster}

![](../../assets/v7-only.svg)

## 개요 {#overview}

Adobe Campaign에서는 배포를 차원화하기 위해 두 개의 사전 패키지된 아키텍처 옵션 세트를 제공합니다.

* **전원 부스터**

   이 옵션은 기본 Adobe Campaign 애플리케이션 인스턴스에서 분리되는 단일 추가 실행 인스턴스를 지원합니다. 전용 실행 인스턴스는 원격으로 또는 타사에서 호스팅할 수 있습니다. 구현되면 이메일 실행, 추적, 미러 페이지 및 바운스 메시지는 중앙 애플리케이션 기능과 독립적으로 처리됩니다.

* **전원 클러스터**

   이 옵션은 지정된 애플리케이션과 관련하여 기본 Adobe Campaign 애플리케이션 인스턴스에서 분리되는 2~N개의 클러스터된 실행 인스턴스를 지원합니다. 클러스터는 원격으로, 분산 배포 및 타사에서 호스팅할 수 있습니다. 프로세스 분리의 이점 외에도 Adobe Campaign 전원 클러스터 옵션을 사용하면 SLA 또는 성능을 단순화하기 위해 상품 하드웨어를 사용하여 중복성과 확장 전략을 수행할 수 있습니다.

![](assets/architectural_options_diagram.png)

## 적합한 애플리케이션 {#eligible-applications}

전원 부스터 및 전원 클러스터 옵션은 다음 응용 프로그램에서 사용할 수 있습니다.

* 캠페인
* 게재
* 메시지 센터

## 아키텍처 권장 사항 매트릭스 {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>표준 아키텍처</strong><br /> </td> 
   <td> <strong>전원 부스터</strong><br /> </td> 
   <td> <strong>전원 클러스터</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 이메일 캠페인 및 아웃바운드 상호 작용<br /> </td> 
   <td> 매월 최대 3,000만 개의 이메일<br /> </td> 
   <td> 매월 30~1억 개의 이메일<br /> </td> 
   <td> 매월 1억 개 이상의 이메일<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 <br /> </td> 
   <td> 실행 서버당 시간당 50,000개<br /> </td> 
   <td> 실행 서버당 시간당 50,000개<br /> </td> 
   <td> 실행 서버당 시간당 50,000개<br /> </td> 
  </tr> 
  <tr> 
   <td> 가용성<br /> </td> 
   <td> 기본 데이터베이스<br /> </td> 
   <td> 24/7 실행 인스턴스에 대한 유지 관리 기간 및 다운타임을 제외한 경우<br /> </td> 
   <td> 24/7/365 서비스 가능<br /> </td> 
  </tr> 
  <tr> 
   <td> 보안<br /> </td> 
   <td> 데이터 마트는 공용 인터넷<br />에서 액세스할 수 있습니다. </td> 
   <td> 데이터 마트는 인터넷 접점 구성 요소<br />에서 분리됩니다. </td> 
   <td> 데이터 마트는 인터넷 접점 구성 요소<br />에서 분리됩니다. </td> 
  </tr> 
  <tr> 
   <td> 배포 템플릿<br /> </td> 
   <td> 한 사이트의 모든 사이트(온-프레미스 또는 클라우드에 있을 수 있음)<br /> </td> 
   <td> 클라우드에서 실행되며 온-프레미스 마케팅<br /> </td> 
   <td> 클라우드에서 실행되는 On-Premise 마케팅 다른 지리적 위치에서 가능한 실행<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 추천 {#recommendations}

* 실행 인스턴스는 서비스 전용이어야 합니다. 구독하지 않은 서비스에 대한 패키지를 설치할 수 없습니다. 예를 들어 **메시지 센터** 서비스의 **전원 부스터** 옵션에 가입하는 경우 전용 실행 인스턴스에만 **[!UICONTROL Execution of transactional messages]** 패키지를 설치할 수 있습니다. 사용권 계약을 확인하십시오.
* 전용 인스턴스(또는 클러스터)는 Adobe Campaign 인스턴스이므로, 권장 사항은 기본 인스턴스와 동일합니다. 자세한 내용은 [이 문서](../../production/using/foreword.md)를 참조하십시오.
* 데이터베이스/하드웨어 구성 요소 POV에서 인스턴스를 올바르게 구성하려면 Adobe Campaign Professional Services에 문의하십시오.
