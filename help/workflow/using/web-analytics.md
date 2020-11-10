---
title: 웹 분석
description: 웹 분석 패키지에 대한 자세한 내용
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 웹 분석{#web-analytics}

아래에 자세히 설명된 워크플로우는 기본적으로 **웹 분석 커넥터** 모듈과 함께 설치됩니다. For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">지표 및 캠페인 속성 전송</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 이 워크플로우에서는 Adobe® Genesis 커넥터를 통해 Adobe Campaign에서 Adobe Experience Cloud Suite로 이메일 캠페인 표시기를 전송할 수 있습니다. 관련 지표는 다음과 같습니다. <strong>전송</strong> (iSent), <strong>총 열린</strong> 수(iTotalRecipientOpen), <strong>클릭한</strong> 받는 사람 <strong>총 수(iTotalRecipient), 받는 사람</strong> 오류 <strong></strong> (ErrorsIError), 옵트아웃(Opt-Out)(OptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">전환된 연락처의 식별</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 이 워크플로우는 재마케팅 캠페인 후 구매를 완료한 사이트 방문자를 인덱싱합니다. 이 워크플로우가 복구한 데이터는 <span class="uicontrol">재마케팅 효율성 보고서에서</span> 액세스할 수 있습니다(이 <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> 페이지</a>참조). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">이벤트 제거</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 이 워크플로우에서는 [수명] 필드에 구성된 기간에 따라 데이터베이스 필드에서 모든 이벤트를 삭제할 <span class="uicontrol">수</span> 있습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">웹 이벤트 복구</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 이 워크플로우는 매시간마다 특정 사이트의 인터넷 사용자 동작에 대한 세그먼트를 다운로드하고, Adobe Campaign 데이터베이스에 추가하고, 다시 마케팅 워크플로우를 실행합니다. <br /> </td> 
  </tr> 
 </tbody> 
</table>

