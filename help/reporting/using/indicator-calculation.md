---
solution: Campaign Classic
product: campaign
title: 지표 계산
description: 지표 계산
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 1%

---


# 지표 계산 {#indicator-calculation}

## 사용자 활동 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 열어 본 기록<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL 기본 키가 1인 모든 @totalClicks 합계<br /> </td> 
   <td> sum(if([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL 유형이 "이메일 클릭"인 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> sum(iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL 유형이 "Transaction"인 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> sum(iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

이 보고서는 **[!UICONTROL Consolidated tracking]** 테이블(nms:trackingStats)을 기반으로 합니다. 이 집계 테이블은 보고서를 표시할 때 성능상의 이유로 사용되며(nms:trackingLogRcp) 테이블 대신 사용됩니다. 이 표는 실시간으로 계산되지 않습니다. **[!UICONTROL Recipient tracking logs]** 추적 로그가 검색되면 몇 분 후에 테이블이 생성됩니다. 지표가 최신 상태인 경우 결과는 **추적 표시기** 보고서의 표시기와 같습니다. @totalclicks 표시기는 5분 동안의 총 클릭 수를 표시합니다.

## 게재 불가 및 이탈 {#non-deliverables-and-bounces-1}

**오류 유형별 분류**

이 보고서는 **[!UICONTROL Delivery and tracking statistics]** 테이블(nms:deliveryLogStats)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 처리된 총 메시지 수<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 상태가 "준비", "전송" 또는 "실패"인 메시지의 합계입니다.<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 알 수 없음<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 상태가 "실패"이고 "사용자 알 수 없음"인 모든 메시지 수입니다.<br /> </td> 
   <td> 개수(@status=2 and msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 연결할 수 없습니다. <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 상태가 "실패"이고 "연결할 수 없음"인 모든 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 거부됨<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "거부됨"인 모든 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 도메인<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 상태가 "실패"이고 이유가 "잘못된 도메인"인 모든 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 계정 비활성화<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 상태가 "실패"이고 "계정이 비활성화됨"인 이유를 가진 모든 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 받은 편지함 전체<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 상태가 "실패"이고 "받은 편지함 꽉 참"인 모든 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류<br /> </td> 
   <td> @value<br /> </td> 
   <td> 이 유형의 오류에 대한 실패한 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason="오류 유형의 값")<br /> </td> 
  </tr> 
  <tr> 
   <td> 기여도<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 유형의 오류 백분율과 총 오류 메시지 수입니다.<br /> </td> 
   <td> 퍼센트(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> -<br /> </td> 
   <td> 처리된 총 메시지 수와 비교한 이 유형의 오류 비율<br /> </td> 
   <td> 퍼센트(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**도메인별 분류**

보고서의 두 번째 부분에서는 오류 유형이 아닌 인터넷 도메인별 실패한 메시지 분류를 자세히 설명합니다. 이 경우 **Error** 표시기(@value)에 연결된 공식은 다음과 같습니다.카운트(@status=2 및 @domain=&quot;도메인 이름의 값&quot;), 즉 이 도메인에 대해 실패한 상태의 모든 메시지 수입니다.

## 브라우저 {#browsers-1}

이 보고서는 **[!UICONTROL Internet Browser Statistics]** 테이블(nms:userAgentsStats)을 기반으로 합니다.

**글로벌 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 방문자<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 배달을 한 번 이상 클릭한 이 브라우저의 총 대상 받는 사람 수입니다.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 페이지 보기 횟수<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 모든 게재에 대해 이 브라우저를 사용하여 배달 링크에 대한 총 클릭 수입니다.<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 사용량<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 브라우저에 대한 방문자 백분율을 총 방문자 수와 비교한 것입니다.<br /> </td> 
   <td> 퍼센트(@totalVisitors, sum(@totalVisitors) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**브라우저별 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 사용량<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 이 브라우저를 사용하는 일별 방문자 수의 백분율과 가장 많은 방문이 있는 날에 측정된 방문자 수입니다.<br /> </td> 
   <td> percent(sum(@visitors),max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 전역 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 버전의 방문자 백분율을 기준으로 모든 브라우저를 사용하는 총 방문자 수와 비교했습니다.<br /> </td> 
   <td> 퍼센트(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 상대적 무게<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 버전을 사용하는 총 방문자 수와 이 브라우저를 사용하는 방문자 수의 백분율입니다.<br /> </td> 
   <td> 퍼센트(@totalVisitors, sum(@totalVisitors) <br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 배달할 메시지 수<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 배달 분석 중에 처리된 총 메시지 수입니다.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공한 배달 수<br /> </td> 
   <td> @success<br /> </td> 
   <td> 성공적으로 처리된 메시지 수 <br /> </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 이메일<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL 카테고리가 "email"과 같은 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL 카테고리가 "facebook"과 같은 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL 카테고리가 "twitter"인 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL 카테고리가 "delicious"인 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL 카테고리가 "digg"인 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL 카테고리가 "google"과 같은 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL 카테고리가 "linkedin"인 모든 @totalClicks의 합계입니다.<br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 공유 수<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 이 소셜 네트워크에서 공유된 총 메시지 수입니다.<br /> </td> 
   <td> Sum(iIf([url/@category]="소셜 네트워크 형식의 값",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 이 소셜 네트워크의 공유 수 백분율과 총 공유 수 대비.<br /> </td> 
   <td> 퍼센트(@forward, sum(@forward)<br /> </td> 
  </tr> 
  <tr> 
   <td> 공유 속도<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 이 네트워크의 공유 수를 배달할 메시지 수와 비교했습니다.<br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 열기 횟수 <br /> </td> 
   <td> @open<br /> </td> 
   <td> 웹 추적 테이블의 총 추적 라인 수입니다.<br /> </td> 
   <td> 카운트<br /> </td> 
  </tr> 
  <tr> 
   <td> 분류<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 이 소셜 네트워크에서 여는 횟수의 백분율과 총 열기 횟수의 백분율입니다.<br /> </td> 
   <td> 퍼센트(@open, sum(@open)<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기 비율<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 이 소셜 네트워크에서 열 개수와 배달할 총 메시지 수를 비교했습니다.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 활동 공유 통계 {#statistics-on-sharing-activities-1}

이 보고서는 **[!UICONTROL Delivery]**(nms:delivery), **[!UICONTROL Consolidated tracking]**(nms:trackingStats) 및 **[!UICONTROL Web tracking]**(nms:webTrackingLog) 테이블을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 새 연락처<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 받는 사람에게 연결된 방문자 수<br /> </td> 
   <td> 공식:count(@id)<br /> 필터:@recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 열어 본 기록<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL 유형이 "열기"인 모든 @ids.<br /> </td> 
   <td> count([url/@type] = 2, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 공유<br /> </td> 
   <td> @shared<br /> </td> 
   <td> 'email', 'facebook', 'twitter', 'delicious', 'digg', 'google', 'linkedin'<br /> "email", "facebook", "twitter", "delicious", "digg", "google" 또는 "linkedin"과 같은 URL 카테고리가 있는 모든 @totalClicks 수입니다.<br /> </td> 
   <td> count ([url/@category] IN (email' , 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 운영 체제 {#operating-systems-1}

이 보고서는 **[!UICONTROL Internet Browser Statistics]** 테이블(nms:userAgentsStats)을 기반으로 합니다.

**글로벌 통계**

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 방문자<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 최소 한 번 이상 배달을 클릭한 운영 체제에서 대상으로 하는 총 받는 사람 수입니다.<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 본 페이지<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 모든 게재에 대해 운영 체제당 배달 링크에 대한 총 클릭 수의 일별 평균입니다.<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용량<br /> </td> 
   <td> -<br /> </td> 
   <td> 운영 체제당 방문자 수를 총 방문자 수와 비교하여 분류합니다.<br /> </td> 
   <td> 퍼센트(@totalVisitors, sum(@totalVisitors)<br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 사용량<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 이 운영 체제에서 일별 방문자 수의 백분율을 기준으로 해당 일에 측정된 방문자 수와 비교한 것입니다.<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 전역 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 모든 운영 체제의 총 방문자 수와 비교한 버전당 방문자 비율<br /> </td> 
   <td> 퍼센트(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 상대 비율<br /> </td> 
   <td> -<br /> </td> 
   <td> 이 운영 체제를 사용하는 총 방문자 수와 비교한 버전당 방문자 비율<br /> </td> 
   <td> 퍼센트(@totalVisitors, sum(@totalVisitors)<br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 등록됨<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 이전 날짜에 등록된 사람의 수입니다.<br /> </td> 
   <td> sum(if(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 이전 날의 구독 수(@action = 1).<br /> </td> 
   <td> sum(if(@action = 1 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 이전 날짜에 구독 취소 횟수(작업 = 0).<br /> </td> 
   <td> sum(if(@action = 0 and @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 진행<br /> </td> 
   <td> -<br /> </td> 
   <td> 구독 수를 뺀 값입니다. 이 비율은 총 구독자 수와 관련하여 계산됩니다.<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription), '+', ")+format(@_subscription - @_unsubscription, 'number', '###0')+ Iif(@_subscriber&gt;0,' + format(100*percent(@_subscription, @_subscriber), 'number', '#, '#,##0)')<br /> </td> 
  </tr> 
  <tr> 
   <td> 충성도<br /> </td> 
   <td> -<br /> </td> 
   <td> 관련 기간에 대한 가입자 충성도 비율입니다.<br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <br /> 배달할 메시지 </td> 
   <td> @toDeliver<br /> </td> 
   <td> 대상 분석 후 broadLogs 수입니다.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> "시드 주소" 필드가 "아니요"이고 상태가 "서비스 제공자에 의해 계산됨" 또는 "전송됨" 또는 "모바일에서 받음"인 메시지 수입니다.<br /> </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 모집단에서 <br />에 도달한 뚜렷한 열기 </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> html 형식의 이메일에 대해 개별 열기 횟수를 기반으로 모든 이메일에 대해 개별 열기 횟수를 추정하여 계산합니다.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> <br />에 도달한 모집단 열기 합계 </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> HTML 형식으로 연 총 이메일 수를 기준으로 모든 이메일에 대해 총 열기 수를 추정합니다.<br /> </td> 
   <td> Iif([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소 링크 클릭<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL 카테고리가 "옵트아웃"인 모든 @ids.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 미러 페이지<br /> 링크 클릭 </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL 카테고리가 "미러 페이지"인 모든 @ids의 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> 전달 예측 </td> 
   <td> @forward<br /> </td> 
   <td> 개별 사용자 수와 전자 메일을 한 번 이상 클릭한 별개의 받는 사람 수 간의 차이입니다.<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 전송<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> "시드 주소" 필드가 "아니요"이고 상태가 "받는 사람이 고려했습니다" 또는 "전송됨" 또는 "모바일 수신됨"인 메시지 수입니다.<br /> </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 컴플레인<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 상태가 "실패"이고 "의 주소"와 같은 원인차단 목록의 메시지 수입니다.<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 열어 본 기록<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 모든 추적 로그에 있는 모든 @broadLog-ids의 수입니다.<br /> </td> 
   <td> 고유([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL 유형이 "이메일 클릭"과 동일한 @broadLog-ids의 고유 수입니다.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 원시 재활동<br /> </td> 
   <td> -<br /> </td> 
   <td> 배달을 한 번 이상 클릭한 받는 사람 수입니다. 적어도 한 번 이상 배달을 연 받는 사람 수와 비교됩니다.<br /> </td> 
   <td> 퍼센트(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 모집단 클릭이<br />에 도달했습니다. </td> 
   <td> @personClick<br /> </td> 
   <td> URL 카테고리가 "이메일 클릭"인 모든 @source-ids의 수입니다.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 누적 클릭<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 카테고리가 있는 모든 @ids의 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 수신자가 <br />을(를) 클릭합니다. </td> 
   <td> @recipientClick<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 유형이 @broadLog-ids의 고유 수입니다.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 예상 재활동 <br /> </td> 
   <td> -<br /> </td> 
   <td> 배달을 한 번 이상 클릭한 받는 사람의 수와 적어도 한 번 이상 배달을 연 받는 사람의 예상과 비교한 받는 사람의 수입니다.<br /> </td> 
   <td> 퍼센트(@recipientClick, @estimatedRecipientOpen<br />) </td> 
  </tr> 
  <tr> 
   <td> 방문한 페이지<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL 유형이 "웹" 또는 "트랜잭션"인 모든 @ids.<br /> </td> 
   <td> count(Iif([url/@type]=4 또는 [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL 유형이 "Transaction"인 모든 @ids.<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 총 금액<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL 유형이 "Transaction"인 webTrackingLog/@amounts 합계.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 평균 거래 금액<br /> </td> 
   <td> -<br /> </td> 
   <td> 거래 수와 비교한 총 금액의 비율<br /> </td> 
   <td> div(@amount, @transaction<br /> </td> 
  </tr> 
  <tr> 
   <td> 항목<br /> </td> 
   <td> @article<br /> </td> 
   <td> "Transaction"과 같은 URL 유형이 있는 webTrackingLog/@articles의 합계입니다.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 트랜잭션당 평균 항목 수<br /> </td> 
   <td> -<br /> </td> 
   <td> 거래 수와 비교하여 항목 수의 비율입니다.<br /> </td> 
   <td> div(@article, @transaction<br /> </td> 
  </tr> 
  <tr> 
   <td> 메시지당 평균 금액<br /> </td> 
   <td> -<br /> </td> 
   <td> 배달할 메시지 수와 비교한 총 금액의 비율입니다.<br /> </td> 
   <td> div(@amount, @toDeliver<br /> </td> 
  </tr> 
  <tr> 
   <td> 이메일<br /> </td> 
   <td> @email<br /> </td> 
   <td> "email"과 같은 URL 카테고리가 있는 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> "facebook"과 같은 URL 카테고리가 있는 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> "twitter"와 같은 URL 카테고리가 있는 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> "맛있는" URL 카테고리와 함께 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> "digg"와 같은 URL 카테고리가 있는 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> "google"과 같은 URL 카테고리가 있는 모든 @totalClicks 합계.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> "linkedin"과 같은 URL 카테고리가 있는 모든 @totalClicks 합계.<br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 재활동<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 배달을 한 번 이상 클릭한 대상 받는 사람 수의 비율과 배달을 한 번 이상 연 대상 받는 사람 수의 예상 수와 비교됩니다.<br /> </td> 
   <td> 퍼센트([표시기/@recipientClick], [표시기/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 고유한 클릭<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 배달을 한 번 이상 클릭한 개별 사용자의 수와 성공과 함께 배달된 메시지의 수를 비교한 것입니다.<br /> </td> 
   <td> 퍼센트([표시기/@personClick], [표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 누적 클릭<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 성공과 함께 배달된 메시지 수와 비교하여 타깃팅된 받는 사람의 총 클릭 수 비율<br /> </td> 
   <td> 퍼센트([표시기/@totalRecipientClick], [표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL 기본 키가 1<br />과 다른 모든 @totalClicks 수 </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭 수(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 누적된 총 클릭 수와 비교한 클릭 수의 비율입니다.<br /> </td> 
   <td> 퍼센트(@_click, @_total)<br /> </td> 
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
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 초기 모집단<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 배달이 타깃팅한 총 받는 사람 수입니다.<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 규칙<br />에서 거부된 메시지 </td> 
   <td> @reject<br /> </td> 
   <td> 분류 규칙 유형에 맞게 분석 중에 무시된 주소 수:주소가 지정되지 않음, 격리됨,차단 목록에 있음<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> <br /> 배달할 메시지 </td> 
   <td> @toDeliver<br /> </td> 
   <td> 배달 분석 후 배달할 총 메시지 수입니다.<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 성공<br /> </td> 
   <td> @success<br /> </td> 
   <td> 성공한 상태로 처리된 메시지 수입니다.<br /> </td> 
   <td> sum([표시기/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류<br /> </td> 
   <td> @error<br /> </td> 
   <td> 배달 및 자동 바운스 처리 중 누적된 총 오류 수입니다.<br /> </td> 
   <td> sum([표시기/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 새 검역소<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 배달 실패 후 격리된 주소 수입니다(사용자 알 수 없음, 잘못된 도메인).<br /> </td> 
   <td> sum([표시기/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 핫 클릭 {#hot-clicks-1}

이 보고서는 배달(nms:delivery) 및 **[!UICONTROL Consolidated tracking]**(nms:trackingStats) 테이블을 기반으로 합니다.

이 보고서는 각 링크에 대한 클릭 비율(HTML 및/또는 텍스트)과 함께 메시지 내용을 보여줍니다. 개인화 블록은 누적된 총 클릭 수에 고려되지만 보고서에 표시되지 않습니다.

## 추적 통계 {#tracking-statistics-1}

이 보고서는 **[!UICONTROL Delivery]** 테이블(nms:delivery)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 트랜잭션<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> "Transaction"과 같은 URL 유형이 있는 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> sum(iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> "이메일 클릭"과 같은 URL 유형이 있는 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> sum(iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 열기<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL 기본 키가 1인 모든 @totalClicks의 합계입니다.<br /> </td> 
   <td> sum(iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 배달 통계 {#delivery-statistics-1}

이 보고서는 **[!UICONTROL Delivery and tracking statistics]** 테이블(nms:deliveryLogStats)을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 처리된 이메일<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 상태가 "준비", "전송" 또는 "실패"인 총 메시지 수입니다.<br /> </td> 
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
   <td> 상태가 "실패"이고 "사용자 알 수 없음"인 이유가 있는 총 메시지 수입니다.<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 소프트 바운스<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 상태가 "실패"이고 "연결할 수 없음", "받은 편지함 full", "잘못된 도메인", "사용할 수 없는 계정", "연결되지 않음" 또는 "거부됨" 상태의 모든 메시지 합계<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 열어 본 기록<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 추적 로그에 @broadLog-ids의 총 수입니다.<br /> </td> 
   <td> 고유([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 클릭<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL 카테고리가 "이메일 클릭"과 같은 총 @source-ids 수입니다.<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 구독 취소<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL 카테고리가 "옵트아웃"인 총 @ids 수입니다.<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 열기 {#breakdown-of-opens-1} 분류

이 보고서는 **배달**(nms:delivery) 및 **추적 로그**(nms:trackingLogRcp) 테이블을 기반으로 합니다.

<table> 
 <thead> 
  <tr> 
   <th> <strong>레이블</strong> <br /> </th> 
   <th> <strong>필드 이름</strong> <br /> </th> 
   <th> <strong>표시기 설명</strong> <br /> </th> 
   <th> <strong>표시기 계산 공식</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 열어 본 기록<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL 기본 키가 1인 모든 @id(열림)의 합계입니다.<br /> </td> 
   <td> count(iif([@url-id] = 1, @id, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 기타 표시기 {#other-indicators}

**Sent** 표시기(@sent)은 **배달(nms:delivery) > 지표** 노드를 통해 액세스되는 SMS 총 수에 해당합니다. 이 표시기는 SMS 전달에만 사용되며 다른 유형의 전달에 사용할 수 없습니다(**@success** 및 **@processed** 표시기와 혼동하지 마십시오).

## 표시기 동기화 {#indicator-synchronization}

특정 지표에 대한 비동기화 또는 불일치가 발생하는 경우 Adobe Campaign 탐색기에서 해당 배달을 선택하고 마우스 오른쪽 단추를 클릭한 후 **[!UICONTROL Action>Recompute delivery and tracking indicators]** 을 선택합니다. **[!UICONTROL Next]**&#x200B;을 클릭한 다음 **[!UICONTROL Finish]**&#x200B;을 클릭합니다.

![](assets/s_ncs_user_recalculate_indicators.png)

## 추적이 {#tracking-opens-} 열기

Adobe Campaign에서 메시지를 검색하려면 수신자가 이메일의 이미지를 다운로드해야 합니다. HTML 및 다중 부분/대체 이메일에는 열려 있는 메시지를 검색할 수 있도록 해주는 0픽셀 이미지가 포함되어 있습니다. 텍스트 형식의 메시지에는 이미지가 포함되어 있지 않으므로 메시지가 열려 있는지 여부를 감지할 수 없습니다. 이미지 표시에 연결된 오류 여백으로 인해 연 메시지를 기반으로 계산된 값은 항상 예측됩니다.

## 타깃팅된 사람/받는 사람 {#targeted-persons---recipients}

일부 보고서에서는 Adobe Campaign이 타깃팅된 사람과 타깃팅된 받는 사람을 차별화합니다.

대상화된 수신자는 배달을 받은 모든 수신자입니다.

대상자 수에는 타깃팅된 받는 사람과 이메일을 받은 사람이 모두 포함됩니다. 새 브라우저에 메시지가 아직 열려 있지 않은 열기 또는 클릭이 있을 때마다 다른 사람이 통계에 추가됩니다.

예를 들어, 직장에서 이메일(Adobe Campaign이 보낸 이메일)을 받고 이를 열거나 클릭하는 경우, 타깃팅된 수신자(예: 수신자=1, 사람=1)로 계산됩니다. 이 이메일을 두 친구에게 전달하면 타깃팅된 받는 사람 수는 여전히 1이고, 대상자 수는 3입니다. 값 3은 새 브라우저에서 각각 열린/클릭과 일치합니다.
