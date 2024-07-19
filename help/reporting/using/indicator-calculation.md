---
product: campaign
title: 지표 계산
description: 지표 계산
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Reporting, Monitoring
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3049'
ht-degree: 3%

---

# 지표 계산 {#indicator-calculation}



## 사용자 활동 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 열기<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL 기본 @totalClicks이 1.<br />인 모든 URL의 합계 </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL 유형이 "이메일 클릭"과 같은 모든 @totalClicks 요소의 합계입니다.<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL 유형이 "Transaction"과 같은 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

이 보고서는 **[!UICONTROL Consolidated tracking]** 테이블(nms:trackingStats)을 기반으로 합니다. 이 집계 테이블은 보고서를 표시할 때 **[!UICONTROL Recipient tracking logs]** 테이블(nms:trackingLogRcp) 대신 성능상의 이유로 사용되며 실시간으로 계산되지 않습니다. 이 테이블은 추적 로그를 검색한 후 몇 분 후에 생성됩니다. 지표가 최신 상태이면 **지표 추적** 보고서의 지표와 같은 결과가 나옵니다. @totalclicks 표시기는 5분 동안 총 클릭 수를 표현합니다.

## 게재 불가 및 이탈 {#non-deliverables-and-bounces-1}

**오류 유형별 분류**

이 보고서는 **[!UICONTROL Delivery and tracking statistics]** 테이블(nms:deliveryLogStats)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 처리된 총 메시지 수<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> "준비", "보냄" 또는 "실패"와 같은 상태의 메시지 합계입니다.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 알 수 없는 사용자<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 상태가 "실패"와 같고 이유가 "사용자 알 수 없음"과 같은 모든 메시지 수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 연결할 수 없는 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 상태가 "실패"와 같고 이유가 "연결할 수 없음"과 같은 모든 메시지의 개수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 거부됨<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 상태가 "실패"와 같고 이유가 "거부됨"과 같은 모든 메시지의 개수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 도메인<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 상태가 "실패"와 같고 이유가 "잘못된 도메인"과 같은 모든 메시지의 개수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용하지 않는 계정<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "계정 사용 안 함"인 모든 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 편지함 가득 참<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 상태가 "실패함"이고 사유가 "받은 편지함 가득 참"인 모든 메시지 수입니다. <br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류<br /> </td> 
   <td> @value<br /> </td> 
   <td> 이 유형의 오류에 대해 실패한 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason="오류 유형의 값")<br /> </td> 
  </tr> 
  <tr> 
   <td> 기여도<br /> </td> 
   <td> -<br /> </td> 
   <td> 총 오류 메시지 수와 비교한 이 형식의 오류 비율입니다.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> -<br /> </td> 
   <td> 처리된 총 메시지 수와 비교한 이 유형의 오류 비율입니다.<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**도메인별 분류**

보고서의 두 번째 부분에서는 오류 유형과 대조적으로 인터넷 도메인별로 실패한 메시지의 분류를 자세히 설명합니다. 이 경우 **오류** 표시기(@value)에 연결된 수식은 다음과 같습니다. Count(@status=2 및 @domain=&quot;도메인 이름 값&quot;)(즉, 이 도메인에 대해 실패한 상태인 모든 메시지의 수).

## 브라우저 {#browsers-1}

이 보고서는 **[!UICONTROL Internet Browser Statistics]** 테이블(nms:userAgentsStats)을 기반으로 합니다.

**전역 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 방문자<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 이 브라우저의 총 대상 받는 사람 수입니다.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 페이지 보기 수<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 모든 게재에 대해 이 브라우저를 사용하는 게재 링크의 총 클릭 수입니다.<br /> </td> 
   <td> 합계@pages <br /> </td> 
  </tr> 
  <tr> 
   <td> 사용률<br /> </td> 
   <td> -<br /> </td> 
   <td> 총 방문자 수와 비교한 이 브라우저의 방문자 비율입니다.<br /> </td> 
   <td> 백분율(@totalVisitors, 합계(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**브라우저당 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 사용률<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 이 브라우저를 사용하는 일일 방문자 수와 방문이 가장 많은 날에 측정된 방문자 수의 백분율입니다.<br /> </td> 
   <td> percent(sum(@visitors),max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 전역 속도<br /> </td> 
   <td> -<br /> </td> 
   <td> 모든 브라우저를 사용하는 총 방문자 수와 비교한 이 버전의 방문자 비율입니다.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 상대 가중치<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 브라우저를 사용하는 총 방문자 수와 비교한 이 버전에 대한 방문자의 비율입니다.<br /> </td> 
   <td> 백분율(@totalVisitors, 합계(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 소셜 네트워크에 공유 {#sharing-to-social-networks-1}

이 보고서는 **[!UICONTROL Delivery]**(nms:delivery), **[!UICONTROL Consolidated tracking]**(nms:trackingStats) 및 **[!UICONTROL Web tracking]**(nms:webTrackingLog) 테이블을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 게재할 메시지 수<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 게재 분석 중에 처리된 총 메시지 수입니다.<br /> </td> 
   <td> sum([속성/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공한 게재 수<br /> </td> 
   <td> @success<br /> </td> 
   <td> <br />개의 메시지를 처리했습니다. </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 전자 메일<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL 범주가 "@totalClicks"인 모든 항목의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL 범주가 "facebook"와 같은 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL 범주가 "twitter"와 같은 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 맛있음<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL 범주가 "@totalClicks"인 모든 URL의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL 범주가 "@totalClicks"인 모든 값의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL 범주가 "google"과 같은 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL 범주가 "linkedin"과 같은 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**공유**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 공유 수<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 이 소셜 네트워크에 공유된 총 메시지 수입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]="소셜 네트워크 유형의 값",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 총 공유 수와 비교한 이 소셜 네트워크의 공유 수의 백분율입니다.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> 공유 비율<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 게재할 메시지 수와 비교하여 이 네트워크의 공유 수입니다.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**열어 본 기록**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 열람 수 <br /> </td> 
   <td> @open<br /> </td> 
   <td> 웹 추적 테이블의 총 추적 줄 수입니다.<br /> </td> 
   <td> 개수<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 이 소셜 네트워크에 대한 총 열람 수와 비교한 열람 수의 백분율입니다.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기 비율<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 게재할 총 메시지 수와 비교한 이 소셜 네트워크의 열기 수입니다.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 공유 활동에 대한 통계 {#statistics-on-sharing-activities-1}

이 보고서는 **[!UICONTROL Delivery]**(nms:delivery), **[!UICONTROL Consolidated tracking]**(nms:trackingStats) 및 **[!UICONTROL Web tracking]**(nms:webTrackingLog) 테이블을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 새 연락처<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 받는 사람에게 연결된 방문자 수 수입니다.<br /> </td> 
   <td> 수식: count(@id)<br /> 필터: @recipient-id!= 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL 유형이 "Open"인 모든 @ids 수.<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 공유<br /> </td> 
   <td> @shared<br /> </td> 
   <td> 'email' , 'facebook' , 'twitter' , '맛있는' , 'digg' , 'google' , 'linkedin'<br />에 포함된 URL 범주: "email", "facebook", "twitter", "맛있는", "digg", "google" 또는 "linkedin"과 같은 URL 범주가 있는 모든 @totalClicks 수.<br /> </td> 
   <td> count (Iif([url/@category] IN (이메일' , 'facebook' , 'twitter' , '맛있는' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 운영 체제 {#operating-systems-1}

이 보고서는 **[!UICONTROL Internet Browser Statistics]** 테이블(nms:userAgentsStats)을 기반으로 합니다.

**전역 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 방문자<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 운영 체제에서 타겟팅한 총 수신자 수의 일별 평균.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 열람한 페이지<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 모든 게재에 대한 운영 체제당 게재 링크의 총 클릭 수의 일별 평균입니다.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용률<br /> </td> 
   <td> -<br /> </td> 
   <td> 전체 방문자 수와 비교한 운영 체제당 방문자 수 분석.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**운영 체제별 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 사용률<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 가장 많은 방문이 있는 날에 측정된 방문자 수와 비교한 이 운영 체제의 일일 방문자 수의 백분율입니다.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 전역 속도<br /> </td> 
   <td> -<br /> </td> 
   <td> 모든 운영 체제에 있는 총 방문자 수와 비교한 버전당 방문자의 비율입니다.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 상대 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 운영 체제를 사용하는 총 방문자 수와 비교한 버전당 방문자의 비율입니다.<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 구독 추적 {#subscription-tracking-1}

이 보고서는 **[!UICONTROL Services]** 테이블(nms:service)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 등록됨<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 전날 등록된 사람 수입니다.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 전날 구독 수(@action = 1)입니다.<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 전날 구독 취소 수(작업 = 0).<br /> </td> 
   <td> sum(Iif(@action = 0 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 발전<br /> </td> 
   <td> -<br /> </td> 
   <td> 구독 수에서 구독 취소 수를 뺀 것입니다. 요금은 총 구독자 수와 관련하여 계산됩니다.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%)',')<br /> </td> 
  </tr> 
  <tr> 
   <td> 충성도<br /> </td> 
   <td> -<br /> </td> 
   <td> 관련 기간의 구독자 충성도 비율입니다.<br /> </td> 
   <td> 1%(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 지표 추적 {#tracking-indicators-1}

이 보고서는 **[!UICONTROL Delivery and tracking statistics]**(nms:deliveryLogStats) 및 **[!UICONTROL Consolidated tracking]**(nms:trackingStats) 테이블을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 게재할 메시지<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 대상 분석 후 broadLogs 수 카운트.<br /> </td> 
   <td> sum([속성/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> "시드 주소" 필드가 "아니요"이고 상태가 "서비스 공급자가 고려함" 또는 "전송됨" 또는 "모바일에서 수신됨"인 메시지 수입니다.<br /> </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> <br />에 도달한 모집단에서 고유 열기 </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> html 형식의 전자 메일에 대한 고유 열기 수를 기반으로 모든 전자 메일에 대한 고유 열기 수를 추정합니다.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 모집단에서 열람 수 합계가 <br />에 도달했습니다. </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> HTML 형식의 총 이메일 열기 수를 기반으로 모든 이메일에 대한 총 열기 수를 추정합니다.<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소 링크 <br />을(를) 클릭합니다. </td> 
   <td> @optOut<br /> </td> 
   <td> URL 범주가 "옵트아웃"과 같은 모든 @ids 수.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 미러 페이지 링크 클릭<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL 범주가 "미러 페이지"와 같은 모든 @ids 수.<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 발송 예상<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 한 번 이상 이메일을 클릭한 고유 사용자 수와 고유 수신자 수 간의 차이입니다.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 전송<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> "시드 주소" 필드가 "아니요"이고 상태가 "받는 사람이 고려함", "보낸 사람" 또는 "모바일에서 받음"인 메시지 수입니다.<br /> </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 컴플레인<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "주소 차단 목록"인 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 및 msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 모든 추적 @broadLog-ids의 모든 게재 수입니다.<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL 유형이 "이메일 클릭"과 동일한 @broadLog-ids의 고유 개수. <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 원시 재활동<br /> </td> 
   <td> -<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 수신자 수와 게재를 한 번 이상 연 수신자 수의 백분율입니다.<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 모집단의 고유 클릭 수가 <br />에 도달했습니다. </td> 
   <td> @personClick<br /> </td> 
   <td> URL 범주가 "이메일 클릭"과 같은 모든 @source-ids 수.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 누적된 클릭 수<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 범주가 있는 모든 @ids 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 받는 사람이 <br />을(를) 클릭함 </td> 
   <td> @recipientClick<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 유형을 가진 @broadLog-ids의 고유 개수.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 예상 반응성<br /> </td> 
   <td> -<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 수신자 수와 게재를 한 번 이상 연 수신자의 예상 수의 비율.<br /> </td> 
   <td> percent(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 방문한 페이지 <br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL 유형이 "Web" 또는 "Transaction"인 모든 @ids 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=4 또는 [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL 유형이 "Transaction"과 같은 모든 @ids 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 총 금액<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL 유형이 "트랜잭션"과 같은 webTrackingLog/@amounts 합계입니다. <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 평균 트랜잭션 금액<br /> </td> 
   <td> -<br /> </td> 
   <td> 거래 수와 비교한 총 금액의 비율입니다.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 항목<br /> </td> 
   <td> @article<br /> </td> 
   <td> "Transaction"과 같은 URL 유형이 있는 webTrackingLog/@articles 합계입니다.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션당 평균 항목 수<br /> </td> 
   <td> -<br /> </td> 
   <td> 트랜잭션 수와 비교한 항목 수의 비율입니다.<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지당 평균 양<br /> </td> 
   <td> -<br /> </td> 
   <td> 게재할 메시지 수와 비교한 총 금액의 비율입니다.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 전자 메일<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL 범주가 "@totalClicks"인 모든 전자 메일의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> "facebook"와 같은 URL 범주가 있는 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> "twitter"과 같은 URL 범주가 있는 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 맛있음<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> "맛있는"과 같은 URL 범주가 있는 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> "digg"와 같은 URL 범주가 있는 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL 범주가 "google"인 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> "linkedin"과 같은 URL 범주가 있는 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 및 클릭 스트림 {#urls-and-click-streams-1}

이 보고서는 **[!UICONTROL Delivery]** 테이블(nms:delivery)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 반응성<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 게재를 한 번 이상 클릭한 대상 수신자 수와 게재를 한 번 이상 연 예상 대상 수신자 수의 비율.<br /> </td> 
   <td> percent([표시기/@recipientClick], [표시기/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 고유 클릭 수<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 배달된 메시지 수와 비교하여 배달을 한 번 이상 클릭한 고유 사용자 수의 비율입니다.<br /> </td> 
   <td> percent([표시기/@personClick], [표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 누적된 클릭 수<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 성공으로 배달된 메시지 수와 비교하여 타겟팅된 수신자의 총 클릭 수의 비율입니다.<br /> </td> 
   <td> percent([표시기/@totalRecipientClick], [표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL 기본 키가 1<br />과(와) 다른 모든 @totalClicks 수 </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭수(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 총 누적 클릭 수와 비교한 클릭 수의 백분율입니다.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 게재 요약 {#delivery-summary-1}

이 보고서는 **[!UICONTROL Delivery]** 테이블(nms:delivery)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 초기 모집단<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 게재 대상의 총 수신자 수입니다.<br /> </td> 
   <td> sum([속성/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> 규칙에 의해 거부된 메시지 </td> 
   <td> @reject<br /> </td> 
   <td> 유형화 규칙을 준수하며 분석 중에 무시된 주소 수: 주소가 지정되지 않음, 격리됨, 차단 목록에 추가하다 등<br /> </td> 
   <td> sum([속성/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 게재할 메시지<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 게재 분석 후 게재할 총 메시지 수입니다.<br /> </td> 
   <td> sum([속성/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공<br /> </td> 
   <td> @success<br /> </td> 
   <td> 성공으로 처리된 메시지 수입니다.<br /> </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류<br /> </td> 
   <td> @error<br /> </td> 
   <td> 게재 및 자동 바운스 처리 중 누적된 총 오류 수입니다.<br /> </td> 
   <td> sum([표시기/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 격리<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 게재 실패 후 격리된 주소 수(사용자 알 수 없음, 잘못된 도메인)입니다.<br /> </td> 
   <td> sum([표시기/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 핫 클릭 {#hot-clicks-1}

이 보고서는 Delivery(nms:delivery) 및 **[!UICONTROL Consolidated tracking]**(nms:trackingStats) 테이블을 기반으로 합니다.

이 보고서에는 메시지 콘텐츠(HTML 및/또는 텍스트)와 각 링크의 링크 클릭 비율이 표시됩니다. 개인화 블록 구독 취소 링크 및 미러 페이지 링크는 누적된 총 클릭 수에서 고려되지만 보고서에 표시되지 않습니다.

## 추적 통계 {#tracking-statistics-1}

이 보고서는 **[!UICONTROL Delivery]** 테이블(nms:delivery)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL 유형이 "Transaction"인 모든 @totalClicks 수의 합계입니다.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL 유형이 "이메일 클릭"과 같은 모든 @totalClicks 요소의 합계입니다.<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> 열기 </td> 
   <td> @opens<br /> </td> 
   <td> URL 기본 키가 1.<br />인 모든 @totalClicks 수의 합계 </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 게재 통계 {#delivery-statistics-1}

이 보고서는 **[!UICONTROL Delivery and tracking statistics]** 테이블(nms:deliveryLogStats)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 처리된 전자 메일<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 상태가 "준비", "전송됨" 또는 "실패"인 총 메시지 수입니다.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 배달됨<br /> </td> 
   <td> @success<br /> </td> 
   <td> 처리된 메시지 수입니다.<br /> </td> 
   <td> 표시기/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 하드 바운스<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "사용자 알 수 없음"인 총 메시지 수입니다.<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 소프트 바운스<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "연결할 수 없음", "받은 편지함 가득 참", "잘못된 도메인", "사용할 수 없는 계정", "연결되지 않음" 또는 "거부됨"인 총 메시지<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 추적 로그의 총 @broadLog-ids 수입니다.<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL 범주가 "이메일 클릭"과 같은 총 @source-ids 수입니다. <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL 범주가 "옵트아웃"과 같은 총 @ids 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 열람수 분류 {#breakdown-of-opens-1}

이 보고서는 **게재**(nms:delivery) 및 **추적 로그**(nms:trackingLogRcp) 테이블을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>지표 계산 수식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 열기<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL 기본 @id이 1(열기)인 모든 히트의 합계입니다. <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 기타 표시기 {#other-indicators}

**게재(nms:delivery) > 표시기** 노드를 통해 액세스되는 **Sent** 표시기(@sent)는 서비스 공급자에게 보낸 총 SMS 수에 해당합니다. 이 지표는 SMS 게재에만 사용되며 다른 유형의 게재에는 사용할 수 없습니다(**@success** 및 **@processed** 지표와 혼동하지 마십시오).

## 표시기 동기화 {#indicator-synchronization}

특정 표시기에 대해 비동기화 또는 불일치가 발생하는 경우 Adobe Campaign 탐색기에서 관련 게재를 선택하고 마우스 오른쪽 단추를 클릭한 다음 **[!UICONTROL Action>Recompute delivery and tracking indicators]**&#x200B;을(를) 선택합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Finish]**&#x200B;을(를) 클릭합니다.

![](assets/s_ncs_user_recalculate_indicators.png)

## 열람 추적 {#tracking-opens-}

Adobe Campaign에서 메시지 열기를 감지하려면 수신자가 이메일의 이미지를 다운로드해야 합니다. HTML 및 다중 파트/대체 이메일에는 열람된 메시지를 감지할 수 있는 0픽셀 이미지가 포함되어 있습니다. 텍스트 포맷의 메시지에는 이미지가 포함되어 있지 않으므로 열람되었는지 여부를 감지할 수 없습니다. 메시지 열람 수를 기준으로 계산된 값은 이미지 표시와 관련된 오차 범위로 인해 언제까지나 추정치에 불과합니다.

## 타겟팅된 사람/수신자 {#targeted-persons---recipients}

일부 보고서에서 Adobe Campaign은 타겟팅된 사용자와 타겟팅된 수신자를 구별합니다.

대상 수신자는 게재를 보낸 모든 수신자입니다.

사람 수에는 타겟팅된 수신자와 이메일이 전달된 모든 사람이 포함됩니다. 새 브라우저(메시지가 아직 열리지 않음)를 열거나 클릭할 때마다 다른 사용자가 통계에 추가됩니다.

예를 들어 직장에서 이메일(Adobe Campaign에서 보냄)을 받고 열거나 클릭하면 타겟팅된 수신자(즉, 수신자=1, 개인=1)로 계산됩니다. 이 이메일을 친구 2명에게 전달하면 타겟팅된 수신자의 수는 여전히 1명이고 사람 수는 3명입니다. 값 3은 새 브라우저에서 열기/클릭할 때마다 일치합니다.
