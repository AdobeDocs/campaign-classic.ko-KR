---
solution: Campaign Classic
product: campaign
title: 캠페인
description: 캠페인
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# 캠페인{#campaign}

아래에 자세히 설명된 워크플로우는 기본적으로 **캠페인** 모듈과 함께 설치됩니다. For more on this module, refer to this [section](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>캠페인 프로세스가 캠페인 수준에서 실행되도록 하려면 이러한 워크플로우를 시작해야 합니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">비용 계산</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> 이 워크플로우는 예산, 계획, 프로그램, 캠페인, 납품 및 태스크의 비용 및 원가 라인 계산을 시작합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock:주문 및 경고</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> 이 워크플로우는 주문 라인에 대해 재고 계산을 실행하고 경고 임계값을 관리합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">캠페인의 배달 작업</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> 이 워크플로우는 승인된 전달을 트리거하고 외부 배달을 위해 서비스 제공자의 사후 처리를 시작합니다. 또한 승인 알림과 미리 알림을 보냅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">캠페인 작업</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> 이 워크플로우는 마케팅 캠페인(타깃팅, 파일 추출 등)에 대한 작업을 관리합니다. 또한 반복되는 캠페인과 관련된 워크플로우를 만듭니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">서비스 제공업체의 작업</span> <br /> </td> 
   <td> <span class="uicontrol">supplierMgt</span> <br /> </td> 
   <td> 배달이 승인되면 이 워크플로우는 공급자(라우터에 이메일 및 사후 처리)를 처리하기 시작합니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

