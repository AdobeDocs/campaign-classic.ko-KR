---
title: 보고서 목록
seo-title: 보고서 목록
description: 보고서 목록
seo-description: null
page-status-flag: never-activated
uuid: 79a914d0-7828-4fe1-b1b7-b055d4bf1f82
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: 3e593527-5580-44ea-93dc-9084d862537e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7655cd93a7dc8ecd35cd379da350ad279cae725

---


# 보고서 목록{#list-of-reports}

## 배달 보고서 {#reports-on-deliveries}

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션을](../../reporting/using/delivery-reports.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 활동(recipientActivity)<br /> </td> 
   <td> 기간별로 개설, 클릭 및 거래 분류<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivery throughput (throughput)<br /> </td> 
   <td> Delivery throughput charts, in message/hour and Mbit/s.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 실패 및 바운스(오류)<br /> </td> 
   <td> 원인 및 도메인별로 바운스 및 비제공 서비스<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(deliveryFeedback)<br /> </td> 
   <td> 수신자 동작 추적을 위한 주요 지표 요약<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 모바일 애플리케이션에 대한 전달의 추적 표시기.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 브라우저(browserStatistics)<br /> </td> 
   <td> 메시지를 클릭한 수신자가 사용하는 브라우저에 대한 통계입니다.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 네트워크에 공유(deliveryForward)<br /> </td> 
   <td> 활동 및 메일 열기 통계 공유<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 핫 클릭(홈)<br /> </td> 
   <td> 메시지와 겹쳐진 클릭률을 표시합니다.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 가설 보고서(delivery가설)<br /> </td> 
   <td> 전달 가설에 대한 측정 요약을 표시합니다.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 통계(통계전달당)<br /> </td> 
   <td> 이메일 도메인당 통계(처리된 메시지, 배달된 메시지, 하드 바운스, 소프트 바운스, 클릭 수, 구독 취소)입니다.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 활동 통계 공유(forwardActivities)<br /> </td> 
   <td> 기간별 공유 활동, 열기 및 가입 분석<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 통계(trackingStatistics)<br /> </td> 
   <td> 거래 비율 보고서를 엽니다.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 요약(deliverySending)<br /> </td> 
   <td> 배달 지표 요약:대상, 제외 및 메시지를 보냈습니다.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 요약(deliveryStatistics)<br /> </td> 
   <td> 선택한 게재에 대한 요약 테이블:전송된 타겟, 제외 및 메시지.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> 운영 체제(osStatistics)<br /> </td> 
   <td> 메시지를 클릭한 수신자가 사용하는 운영 체제에 대한 통계입니다.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 재활동 비율(deliveryFeedbackSocial)<br /> </td> 
   <td> 배달 재활동 비율 및 반응 분류.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
  <tr> 
   <td> URL 및 클릭 처리량(topUrlDelivery)<br /> </td> 
   <td> 대부분의 반응형 URL 및 연결된 클릭 스트림입니다.<br /> </td> 
   <td> nms:배달<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 캠페인에 대한 보고서 {#reports-on-campaigns}

캠페인에 대한 보고서는 **nms:operation** 테이블의 데이터에 영향을 줍니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션을](../../campaign/using/designing-marketing-campaigns.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 활동(operationRecipientActivity)<br /> </td> 
   <td> 기간별 열기, 클릭 및 거래의 분류는 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivery throughput (operationThroughput)<br /> </td> 
   <td> Delivery throughput charts, in mail/hour and Mbit/s, depends on Campaign.<br /> </td> 
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
   <td> 비용 라인에 대한 설명 분석은 MRM에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 추적 표시기(operationFeedback)<br /> </td> 
   <td> 주요 추적 지표 개요:열기, 클릭 및 거래는 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 네트워크에 공유(operationForward)<br /> </td> 
   <td> 활동 및 메일 열기 통계 공유는 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 가설 보고서(operation가설)<br /> </td> 
   <td> 캠페인에 따라 캠페인 게재에 대한 가설 측정 요약을 표시합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 활동 통계 공유(forwardActivityOpt)<br /> </td> 
   <td> 기간별 공유 활동, 열기 및 구독에 대한 분석은 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달 요약(operationStatistics)<br /> </td> 
   <td> 캠페인 게재의 요약 차트:전송된 타겟, 제외 및 메시지.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL 및 클릭 처리량(operationTopUrlDelivery)<br /> </td> 
   <td> 대부분의 반응형 URL 및 연결된 클릭 스트림은 캠페인에 따라 다릅니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 서비스에 대한 보고서 {#reports-on-services}

서비스에 대한 보고서는 **nms:service** 테이블의 데이터와 관련이 있습니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 관련 가이드를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 팬 확보(socialAcquisitionByWebapp)<br /> </td> 
   <td> 잠재 고객 확보를 가능하게 한 웹 애플리케이션은 무엇입니까? Social 마케팅 Add-on에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 분류(mobileAppDistribution)<br /> </td> 
   <td> 모바일 애플리케이션별 활성 구독 분류는 모바일 앱 채널 Add-on에 따라 달라집니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 추적(subscriptionsProgress)<br /> </td> 
   <td> 정보 서비스에 대한 구독 발전<br /> </td> 
  </tr> 
  <tr> 
   <td> 재활동 비율(socialResponsiveRate)<br /> </td> 
   <td> 최근 배달의 재활동 비율은 얼마입니까? Social 마케팅 Add-on에 따라 다릅니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 재활동 비율(mobileAppReactivityRate)<br /> </td> 
   <td> 최신 게재의 재활동 비율은 모바일 앱 채널 Add-on에 따라 다릅니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 예산 보고서 {#budget-reports}

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션을](../../campaign/using/designing-marketing-campaigns.md)참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 프로그램에 연결된 비용(budgetProgramCost)<br /> </td> 
   <td> 프로그램 비용 분류<br /> </td> 
   <td> nms:프로그램<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산 발전(budgetEvolution)<br /> </td> 
   <td> 약정 수준별 예산 비용 향상<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산의 누적 발전(budgetCumulativeEvolution)<br /> </td> 
   <td> 누적된 예산 비용의<br /> 발전. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerBudget)<br /> </td> 
   <td> 원가 라인에 대한 설명 분석.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorer)<br /> </td> 
   <td> 원가 라인에 대한 설명 분석.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerPlan)<br /> </td> 
   <td> 원가 라인에 대한 설명 분석.<br /> </td> 
   <td> nms:계획<br /> </td> 
  </tr> 
  <tr> 
   <td> 비용 라인 탐색(budgetExplorerProgram)<br /> </td> 
   <td> 원가 라인에 대한 설명 분석.<br /> </td> 
   <td> nms:프로그램<br /> </td> 
  </tr> 
  <tr> 
   <td> 예산 요약(예산)<br /> </td> 
   <td> 주요 비용, 비용 범주 및 예산의 요약<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 시뮬레이션에 대한 보고서 {#reports-on-simulations}

시뮬레이션에 대한 보고서는 **nms:simulation** 표의 데이터에 대해 다룹니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 관련 가이드를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션 제외 세부 사항(dlvSimuLossDetail)<br /> </td> 
   <td> 모든 제외 사유에 대한 세부 표.<br /> </td> 
  </tr> 
  <tr> 
   <td> 등급별 오퍼 분류(offerSimulationRanking)<br /> </td> 
   <td> 등급별 시뮬레이션에서 오퍼 분류<br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션 요약(dlvSimuLossSummary)<br /> </td> 
   <td> 시뮬레이션 볼륨 및 제외 사항의 요약<br /> </td> 
  </tr> 
  <tr> 
   <td> 겹치기 통계(dlvSimuOverlapping)<br /> </td> 
   <td> 전달 대상이 볼륨을 겹칩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 시뮬레이션으로 인한 제외 요약(dlvSimuLossSimu)<br /> </td> 
   <td> 시뮬레이션으로 인한 제외 테이블<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 웹 응용 프로그램에 대한 보고서 {#reports-on-web-applications}

웹 응용 프로그램에 대한 보고서는 nms:WebApp **테이블의 데이터에** 대해 다룹니다.

Adobe Campaign에서 제공하는 내장 보고서는 아래 표에 있습니다.

이러한 보고서의 내용에 대한 자세한 내용은 [이 섹션을](../../web/using/about-web-applications.md)참조하십시오.

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

## 기타 otb 보고서 {#other-ootb-reports}

다음 보고서도 기본으로 제공됩니다. 자세한 내용은 관련 기능에 대한 문서를 참조하십시오.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블 및 내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>스키마</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼 분석(offerAnalysis)<br /> </td> 
   <td> 날짜 및 채널별 오퍼 분석은 상호 작용 추가 기능에 따라 다릅니다.<br /> </td> 
   <td> nms:오퍼<br /> </td> 
  </tr> 
  <tr> 
   <td> 재마케팅 효율성(리마케팅 효과)<br /> </td> 
   <td> 재마케팅 효율성 측정<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 소셜 잠재 고객 확보 내역(socialVisitorStatistics)<br /> </td> 
   <td> Twitter 및 Facebook 잠재 고객 확보 내역은 Social 마케팅 Add-on에 따라 다릅니다.<br /> </td> 
   <td> nms:방문자<br /> </td> 
  </tr> 
  <tr> 
   <td> 최근 제안 추적(최근 제안)<br /> </td> 
   <td> 실시간 제안 추적<br /> </td> 
   <td> nms:provisionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

