---
product: campaign
title: 웹 분석
description: 웹 분석 패키지에 대해 자세히 알아보기
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 웹 분석{#web-analytics}

![](../../assets/common.svg)

아래 자세히 설명된 워크플로우는 기본적으로 **웹 Analytics 커넥터** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션](../../platform/using/adobe-analytics-connector.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">지표 및 캠페인 속성 보내기</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 이 워크플로우에서는 Adobe® Analytics 커넥터를 통해 Adobe Campaign에서 Adobe Experience Cloud Suite로 이메일 캠페인 표시기를 보낼 수 있습니다. 관련 지표는 다음과 같습니다. <strong>전송됨</strong> (iSent), <strong>총 열기 수</strong> (iTotalRecipientOpen), <strong>Errors</strong> (iError), <strong>Opt-Out</strong> (opt-out) (iOpt-out)<br /></strong><strong> </strong></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">전환된 연락처 식별</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 이 워크플로우는 재마케팅 캠페인 후 구매를 마친 사이트 방문자를 인덱싱합니다. 이 워크플로우에서 복구한 데이터는 <span class="uicontrol">리마케팅 효율성 보고서</span>에서 액세스할 수 있습니다(<a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign"> 페이지</a> 참조). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">이벤트 삭제</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 이 워크플로우에서는 <span class="uicontrol">수명</span> 필드에 구성된 기간에 따라 데이터베이스 필드에서 모든 이벤트를 삭제할 수 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">웹 이벤트 복구</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 매시간마다 이 워크플로우는 주어진 사이트의 인터넷 사용자 동작에 있는 세그먼트를 다운로드하고, Adobe Campaign 데이터베이스에 지정하고, 리마케팅 워크플로우를 시작합니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

