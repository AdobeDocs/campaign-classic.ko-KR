---
product: campaign
title: 전원 부스터 및 전원 클러스터
description: 전원 부스터 및 전원 클러스터
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 7%

---

# 전원 부스터 및 전원 클러스터{#power-booster-and-power-cluster}



## 개요 {#overview}

Adobe Campaign은 배포 차원을 높이기 위한 두 가지 미리 패키지된 아키텍처 옵션 세트를 제공합니다.

* **전원 부스터**

   이 옵션은 기본 Adobe Campaign 애플리케이션 인스턴스에서 분리된 단일 추가 실행 인스턴스를 지원합니다. 전용 실행 인스턴스는 원격으로 또는 서드파티에 의해 호스팅될 수 있습니다. 구현 시 이메일 실행, 추적, 미러 페이지 및 바운스 메시지는 중앙 애플리케이션 기능과 독립적으로 처리됩니다.

* **전원 클러스터**

   이 옵션은 지정된 애플리케이션과 관련하여 기본 Adobe Campaign 애플리케이션 인스턴스에서 분리된 2~N 클러스터된 실행 인스턴스를 지원합니다. 클러스터는 원격, 분산 배포 시 및 서드파티가 호스팅할 수 있습니다. Adobe Campaign Power Cluster 옵션은 프로세스 격리의 이점 외에도 상용 하드웨어를 사용하여 이중화 및 확장 전략을 지원하여 SLA 또는 성능 향상을 단순화합니다.

![](assets/architectural_options_diagram.png)

## 적격한 애플리케이션 {#eligible-applications}

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
   <td> 매월 최대 약 3,000만 개의 이메일<br /> </td> 
   <td> 매월 3,000만~1억 개의 이메일<br /> </td> 
   <td> 매월 1억 건 이상의 이메일<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션 메시지 <br /> </td> 
   <td> 실행 서버당 시간당 50,000<br /> </td> 
   <td> 실행 서버당 시간당 50,000<br /> </td> 
   <td> 실행 서버당 시간당 50,000<br /> </td> 
  </tr> 
  <tr> 
   <td> 가용성<br /> </td> 
   <td> 기본 데이터베이스의 ID<br /> </td> 
   <td> 실행 인스턴스에 대한 유지 관리 기간 및 가동 중지 시간 제외 24/7<br /> </td> 
   <td> 24/7/365 서비스 가능<br /> </td> 
  </tr> 
  <tr> 
   <td> 보안<br /> </td> 
   <td> 데이터 마트는 잠재적으로 공용 인터넷에서 액세스할 수 있습니다.<br /> </td> 
   <td> 데이터 마트는 전면, 인터넷 연결 구성 요소에서 분리되어 있습니다.<br /> </td> 
   <td> 데이터 마트는 전면, 인터넷 연결 구성 요소에서 분리되어 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 배포 템플릿<br /> </td> 
   <td> 하나의 사이트에 모두 있음(온프레미스 또는 클라우드에서 있을 수 있음)<br /> </td> 
   <td> 클라우드에서 실행 가능한 온프레미스 마케팅<br /> </td> 
   <td> 클라우드에서 실행 중인 온프레미스 마케팅, 다른 지역에서 실행 가능<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 권장 사항 {#recommendations}

* 실행 인스턴스는 서비스 전용이어야 합니다. 구독하지 않은 서비스에 대한 패키지를 설치할 수 없습니다. 예를 들어 을 구독하는 경우 **전원 부스터** 옵션 **메시지 센터** 서비스에서는 **[!UICONTROL Execution of transactional messages]** 전용 실행 인스턴스에 패키지합니다. 사용권 계약을 확인하십시오.
* 전용 인스턴스(또는 클러스터)는 Adobe Campaign 인스턴스이므로 권장 사항은 기본 인스턴스와 동일합니다. 자세한 내용은 다음을 참조하십시오. [이 문서](../../production/using/foreword.md).
* 데이터베이스/하드웨어 구성 요소 관점에서 인스턴스를 올바르게 구성하려면 Adobe Campaign Professional Services에 문의하십시오.
