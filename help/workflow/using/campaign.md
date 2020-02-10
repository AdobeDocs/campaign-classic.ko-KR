---
title: 캠페인
seo-title: 캠페인
description: 캠페인
seo-description: null
page-status-flag: never-activated
uuid: 9e5cf203-e5e9-4383-b628-aa6f131491e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: de892ec4-c378-4b22-875e-aa9345f82552
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0d687b57f75b432547baef57021b716a8ce37ad4

---


# 캠페인{#campaign}

아래에 자세히 설명된 워크플로우는 기본적으로 캠페인 **모듈과** 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션을](../../campaign/using/designing-marketing-campaigns.md)참조하십시오.

>[!CAUTION]
>
>캠페인 프로세스가 캠페인 수준에서 실행되려면 이러한 워크플로우를 시작해야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">비용 계산</span><br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span><br /> </td> 
   <td> 이 워크플로우는 예산, 계획, 프로그램, 캠페인, 납품 및 태스크에 대한 비용 및 비용 라인의 계산을 시작합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock:주문 및 경고</span><br /> </td> 
   <td> <span class="uicontrol">stockMgt</span><br /> </td> 
   <td> 이 워크플로우는 주문 라인에 대해 재고 계산을 시작하고 경고 임계값을 관리합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">캠페인의</span> 배달 작업 <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span><br /> </td> 
   <td> 이 워크플로우는 승인된 배달을 트리거하고 외부 배달을 위해 서비스 공급자의 후처리를 시작합니다. 또한 승인 알림 및 미리 알림을 보냅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">캠페인 작업</span><br /> </td> 
   <td> <span class="uicontrol">operationMgt</span><br /> </td> 
   <td> 이 워크플로우는 마케팅 캠페인(타깃팅, 파일 추출 등)에 대한 작업을 관리합니다. 또한 반복되는 캠페인과 관련된 워크플로우를 만듭니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">서비스 제공업체의</span> 작업 <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span><br /> </td> 
   <td> 배달이 승인되면 이 워크플로우는 공급자(라우터로 이메일 및 사후 처리)를 처리하기 시작합니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

