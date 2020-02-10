---
title: Power Bourter 및 Power Cluster
seo-title: Power Bourter 및 Power Cluster
description: Power Bourter 및 Power Cluster
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a5072ba55690d4d88c12ac7ff647f163deddbf32

---


# Power Bourter 및 Power Cluster{#power-booster-and-power-cluster}

## 개요 {#overview}

Adobe Campaign은 배포의 크기를 조정할 수 있도록 사전 패키지된 두 가지 아키텍처 옵션 세트를 제공합니다.

* **전원 부스터**

   이 옵션은 기본 Adobe Campaign 애플리케이션 인스턴스에서 분리된 단일 추가 실행 인스턴스에 대한 지원을 제공합니다. 전용 실행 인스턴스는 원격으로 또는 타사에서 호스팅할 수 있습니다. 구현 시 이메일 실행, 추적, 미러 페이지 및 바운스 메시지는 중앙 애플리케이션 기능과 독립적으로 처리됩니다.

* **전원 클러스터**

   이 옵션은 지정된 애플리케이션과 관련하여 기본 Adobe Campaign 애플리케이션 인스턴스에서 분리된 2-N의 클러스터된 실행 인스턴스를 지원합니다. 클러스터는 분산 배포와 제3자에 의해 원격으로 호스팅될 수 있습니다. Adobe Campaign Power Cluster 옵션을 사용하면 프로세스 격리 기능을 통해 얻을 수 있는 이점 외에도 SLA 또는 성능을 간소화하기 위해 상품 하드웨어를 사용하여 중복성을 강화하고 전략을 확장할 수 있습니다.

![](assets/architectural_options_diagram.png)

## 자격 조건을 갖춘 애플리케이션 {#eligible-applications}

Power Boxer 및 Power Cluster 옵션은 다음 애플리케이션에서 사용할 수 있습니다.

* 캠페인
* 리드
* 게재
* 메시지 센터

## 건축 추천 매트릭스 {#matrix-of-architectural-recommendations}

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
   <td> 매월 최대 3천만 개의 이메일<br /> </td> 
   <td> 매월 3,000~1,000개의 이메일<br /> </td> 
   <td> 매월 1억 개 이상의 이메일<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지<br /> </td> 
   <td> 실행 서버당 시간당 50,000<br /> </td> 
   <td> 실행 서버당 시간당 50,000<br /> </td> 
   <td> 실행 서버당 시간당 50,000<br /> </td> 
  </tr> 
  <tr> 
   <td> 가용성<br /> </td> 
   <td> 기본 데이터베이스<br /> </td> 
   <td> 실행 인스턴스에 대한 유지 관리 기간 및 다운로드 시간을 제외한 24/7<br /> </td> 
   <td> 24/7/365 서비스 가능<br /> </td> 
  </tr> 
  <tr> 
   <td> 보안<br /> </td> 
   <td> Data Mart는 잠재적으로 공용 인터넷에서 액세스할 수 있습니다.<br /> </td> 
   <td> 데이터 마트는 정면, 인터넷 측면 구성 요소에서 분리됩니다.<br /> </td> 
   <td> 데이터 마트는 정면, 인터넷 측면 구성 요소에서 분리됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 배포 템플릿<br /> </td> 
   <td> 하나의 사이트에서 모두(사내 또는 클라우드에 있을 수 있음)<br /> </td> 
   <td> 클라우드에서 실행되는 사내 마케팅<br /> </td> 
   <td> 클라우드에서 실행되는 사내 마케팅다른 위치에서 실행 가능<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Recommendations {#recommendations}

* 실행 인스턴스는 서비스에 대한 전용이어야 합니다. 가입하지 않은 서비스에는 패키지를 설치할 수 없습니다. 예를 들어 메시지 센터 서비스에 대해 **Power** Boxer 옵션을 구독하는 **경우** 전용 실행 인스턴스에만 **[!UICONTROL Execution of transactional messages]** 패키지를 설치할 수 있습니다. 사용권 계약을 확인하십시오.
* 전용 인스턴스(또는 클러스터)는 Adobe Campaign 인스턴스이므로, 권장 사항은 기본 인스턴스와 동일합니다. For more on this, refer to [this document](../../production/using/foreword.md).
* 데이터베이스/하드웨어 구성 요소 POV에서 인스턴스를 제대로 구성하려면 Adobe Campaign Professional Services에 문의하십시오.

