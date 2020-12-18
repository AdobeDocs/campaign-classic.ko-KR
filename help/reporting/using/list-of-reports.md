---
solution: Campaign Classic
product: campaign
title: 보고서 목록
description: 보고서 목록
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---


# 보고서 목록{#list-of-reports}

## 게재 보고서 {#reports-on-deliveries}

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에서 찾을 수 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../reporting/using/delivery-reports.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 활동(recipientActivity)<br /> </td> 
   <td> 기간별로 열기, 클릭 및 거래의 분류<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 처리량(처리량)<br /> </td> 
   <td> 배달 처리량 차트, 메시지/시간 및 Mbits/s.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 실패 및 바운스(오류)<br /> </td> 
   <td> 원인 및 도메인별로 바운스 및 비제공 서비스.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(deliveryFeedback)<br /> </td> 
   <td> 받는 사람 동작 추적을 위한 주요 지표의 요약입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 모바일 응용 프로그램에 대한 배달의 추적 표시기.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 브라우저(browserStatistics)<br /> </td> 
   <td> 메시지를 클릭한 수신자가 사용하는 브라우저에 대한 통계입니다.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 네트워크에 공유(deliveryForward)<br /> </td> 
   <td> 활동 및 메일 열기 통계를 공유합니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 핫 클릭(선택 사항)<br /> </td> 
   <td> 메시지 및 클릭 비율이 겹쳐진 메시지를 표시합니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 가설 보고서(delivery가설)<br /> </td> 
   <td> 배달 가설에 대한 측정 단위 요약을 표시합니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 통계(statisticsPerDelivery)<br /> </td> 
   <td> 이메일 도메인당 통계(처리된 메시지, 배달된 메시지, 하드 바운스, 소프트 바운스, 클릭 수, 구독 취소).<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 활동 통계 공유(forwardActivities)<br /> </td> 
   <td> 기간당 공유 활동, 열기 및 구독에 대한 분석.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 통계(trackingStatistics)<br /> </td> 
   <td> 거래 비율 보고서를 열고 클릭합니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 요약(deliverySending)<br /> </td> 
   <td> 배달 지표의 요약:대상, 제외 및 메시지를 보냈습니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 요약(deliveryStatistics)<br /> </td> 
   <td> 선택한 게재에 대한 요약 테이블:Target, 제외 및 메시지 전송.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 운영 체제(osStatistics)<br /> </td> 
   <td> 메시지를 클릭한 수신자가 사용하는 운영 체제에 대한 통계입니다.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 재활동 비율(deliveryFeedbackSocial)<br /> </td> 
   <td> 배달 재활동 비율 및 반응 분류입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL 및 클릭 처리량(topUrlDelivery)<br /> </td> 
   <td> 대부분의 반응형 URL 및 연결된 클릭 스트림입니다.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 캠페인 {#reports-on-campaigns} 보고서

캠페인에 대한 보고서는 **nms:operation** 테이블의 데이터에 영향을 줍니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에서 찾을 수 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../campaign/using/designing-marketing-campaigns.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 활동(operationRecipientActivity)<br /> </td> 
   <td> 기간별로 열린 횟수, 클릭 수 및 거래의 분류는 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 처리량(operationThroughput)<br /> </td> 
   <td> 배달 처리량 차트, 이메일/시간 및 Mbits/s는 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 비용(budgetOperationExpenses)<br /> </td> 
   <td> 캠페인에 따라 캠페인 라인 항목을 자세히 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 실패 및 바운스(operationErrors)<br /> </td> 
   <td> 원인 및 도메인별로 바운스 및 비산출물은 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerOperation)<br /> </td> 
   <td> 비용 라인에 대한 설명 분석, MRM<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(operationFeedback)<br /> </td> 
   <td> 주요 추적 지표 개요:열기, 클릭 및 거래는 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 네트워크에 공유(operationForward)<br /> </td> 
   <td> 활동 및 메일 열기 통계를 공유하는 것은 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 가설 보고서(operation가설)<br /> </td> 
   <td> 캠페인에 따라 캠페인 게재에 대한 가설 측정 요약을 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 활동 통계 공유(forwardActivityOpt)<br /> </td> 
   <td> 기간 동안의 공유 활동, 열기 및 구독에 대한 분석은 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 요약(operationStatistics)<br /> </td> 
   <td> 캠페인 배달의 요약 차트:Target, 제외 및 메시지 전송.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL 및 클릭 처리량(operationTopUrlDelivery)<br /> </td> 
   <td> 대부분의 반응형 URL 및 연결된 클릭 스트림은 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 서비스 보고서 {#reports-on-services}

서비스에 대한 보고서는 **nms:service** 테이블의 데이터와 관련이 있습니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에서 찾을 수 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 관련 가이드를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 팬 확보(socialAcquisitionByWebapp)<br /> </td> 
   <td> 잠재 고객 확보를 가능하게 한 웹 애플리케이션은 무엇입니까? 소셜 마케팅 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 분류(mobileAppDistribution)<br /> </td> 
   <td> 모바일 응용 프로그램당 활성 구독의 분류는 모바일 앱 채널 Add-on에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 추적(subscriptionsProgress)<br /> </td> 
   <td> 정보 서비스<br />에 대한 구독 진행 </td> 
  </tr> 
  <tr> 
   <td> 재활동 비율(socialResponsiveRate)<br /> </td> 
   <td> 최근 배달의 재활동 비율은 얼마입니까? 소셜 마케팅 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 재활동 비율(mobileAppReactivityRate)<br /> </td> 
   <td> 최신 게재에 대한 재활동 비율은 모바일 앱 채널 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 예산 보고서 {#budget-reports}

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에서 찾을 수 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../campaign/using/designing-marketing-campaigns.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 프로그램에 연결된 비용(budgetProgramCost)<br /> </td> 
   <td> 프로그램 비용 분류.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산 진행 과정(budgetEvolution)<br /> </td> 
   <td> 약정 수준별로 예산 비용 진행<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산의 누적 진행(budgetCumulativeEvolution)<br /> </td> 
   <td> 누적된 예산 비용의 진화는 각급별<br /> 개각 수준으로 분류된다. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerBudget)<br /> </td> 
   <td> 비용 라인의 설명 분석.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorer)<br /> </td> 
   <td> 비용 라인의 설명 분석.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerPlan)<br /> </td> 
   <td> 비용 라인의 설명 분석.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerProgram)<br /> </td> 
   <td> 비용 라인의 설명 분석.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산 요약(예산)<br /> </td> 
   <td> 기본 비용, 비용 범주 및 예산의 요약.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 시뮬레이션 보고서 {#reports-on-simulations}

시뮬레이션에 대한 보고서는 **nms:simulation** 표의 데이터에 대해 우려를 갖습니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에서 찾을 수 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 관련 가이드를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션 제외 세부 정보(dlvSimuLossDetail)<br /> </td> 
   <td> 제외의 모든 원인 상세 표<br /> </td> 
  </tr> 
  <tr> 
   <td> 순위(offerSimulationRanking)<br /> </td> 
   <td> 시뮬레이션에서 오퍼의 등급을 기준으로 분류<br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션 요약(dlvSimuLossSummary)<br /> </td> 
   <td> 시뮬레이션 볼륨 및 제외 요약.<br /> </td> 
  </tr> 
  <tr> 
   <td> 겹치는 통계(dlvSimuOverlapping)<br /> </td> 
   <td> 배달 대상이 볼륨을 겹칩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션으로 인한 제외 요약(dlvSimuLossSimu)<br /> </td> 
   <td> 시뮬레이션으로 인한 제외 테이블<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 웹 응용 프로그램 보고서 {#reports-on-web-applications}

웹 응용 프로그램에 대한 보고서는 **nms:WebApp** 테이블의 데이터에 대해 우려를 갖습니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에서 찾을 수 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션](../../web/using/about-web-applications.md)을 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 설명서(surveyDictionary)<br /> </td> 
   <td> 설문 조사 구조에 대한 설명은 설문 조사 관리자 추가 기능에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 기본(surveyProperties)<br /> </td> 
   <td> 설문 조사 속성<br /> </td> 
  </tr> 
  <tr> 
   <td> 응답 분류(surveyDistribution)<br /> </td> 
   <td> 질문에 대한 응답 분류.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 다른 otb 보고서 {#other-ootb-reports}

다음 보고서도 기본 제공됩니다. 자세한 내용은 관련 기능에 대한 문서를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 분석(offerAnalysis)<br /> </td> 
   <td> 날짜 및 채널당 오퍼 분석은 상호 작용 추가 기능에 따라 달라집니다.<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 재마케팅 효율성(remarketingEffect)<br /> </td> 
   <td> 재마케팅 효율성 측정<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 잠재 고객 확보 내역(socialVisitorStatistics)<br /> </td> 
   <td> Twitter 및 Facebook 잠재 고객 확보 내역은 Social 마케팅 추가 기능에 따라 다릅니다.<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> 최근 제안 추적(최근 제안)<br /> </td> 
   <td> 실시간 제안 추적<br /> </td> 
   <td> nms:provisionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

