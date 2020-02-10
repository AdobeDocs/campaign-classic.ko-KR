---
title: 웹 분석
seo-title: 웹 분석
description: 웹 분석
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 웹 분석{#web-analytics}

아래에 자세히 설명된 워크플로우는 기본적으로 웹 **분석 커넥터** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [섹션을](../../platform/using/adobe-analytics-data-connector.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">지표 및 캠페인 속성</span> 보내기 <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> 이 워크플로우에서는 Adobe® Genesis 커넥터를 통해 Adobe Campaign의 이메일 캠페인 표시기를 Adobe Experience Cloud Suite로 보낼 수 있습니다. 관련 지표는 다음과 같습니다.전송 <strong></strong><strong></strong> (iSent), <strong>총 열기</strong> 수(iTotalRecipientOpen), <strong>클릭한</strong> 총 받는 사람 수(iTotalTotalRecipientRecipientClickErrorsIError), Opt-Out <strong></strong> (I-Out)<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">전환된 연락처의</span> 식별 <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> 이 워크플로우는 재마케팅 캠페인 후 구매를 완료한 사이트 방문자를 인덱싱합니다. 이 워크플로우로 복구된 데이터는 재마케팅 효율성 보고서에서 <span class="uicontrol">액세스할 수 있습니다(이</span> 페이지 <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"></a>참조). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">이벤트 제거</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> 이 워크플로우에서는 [수명] 필드에 구성된 기간에 따라 데이터베이스 필드에서 모든 이벤트를 삭제할 <span class="uicontrol">수</span> 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">웹 이벤트</span> 복구 <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> 이 워크플로우는 매시간 특정 사이트의 인터넷 사용자 동작에 대한 세그먼트를 다운로드하고 Adobe Campaign 데이터베이스에 삽입하여 다시 마케팅 워크플로우를 시작합니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

