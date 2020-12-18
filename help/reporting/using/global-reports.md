---
solution: Campaign Classic
product: campaign
title: 글로벌 보고서
description: 글로벌 보고서
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 1%

---


# 글로벌 보고서 {#global-reports}

이러한 보고서는 전체 데이터베이스의 데이터 활동에 영향을 줍니다. 보고서 대시보드를 보려면 **[!UICONTROL Reports]** 탭으로 이동하십시오.

![](assets/s_ncs_user_report_delivery_link.png)

보고서를 표시하려면 해당 이름을 클릭합니다. 기본적으로 다음 보고서를 사용할 수 있습니다.

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>이 섹션에는 게재에 연결된 보고서만 표시됩니다.

* **[!UICONTROL Delivery throughput]** :전달  [처리량을 참조하십시오](#delivery-throughput).
* **[!UICONTROL Browsers]** :자세한 내용은  [브라우저를 참조하십시오](#browsers).
* **[!UICONTROL Sharing to social networks]** :소셜  [네트워크에 공유를 참조하십시오](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** :공유  [활동에 대한 통계를 참조하십시오](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** :자세한 내용은  [운영 체제를 참조하십시오](#operating-systems).
* **[!UICONTROL URLs and click streams]** :url을  [참조하고 스트림을 클릭합니다](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** :추적 표시기를  [참조하십시오](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** :비산출물  [및 바운스를 참조하십시오](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** :사용자  [활동을 참조하십시오](#user-activities).
* **[!UICONTROL Subscription tracking]** :구독  [추적을 참조하십시오](#subscription-tracking).
* **[!UICONTROL Delivery summary]** :배달  [요약을 참조하십시오](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** :전달  [통계를 참조하십시오](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** :열기  [분류를 참조하십시오](#breakdown-of-opens).

## 게재 처리량 {#delivery-throughput}

이 보고서에는 지정된 기간 동안 전체 플랫폼의 배달 처리량에 대한 정보가 포함되어 있습니다. 메시지가 전달되는 속도를 측정하기 위해 기준은 시간당 전송된 메시지 수와 메시지 크기(초당 비트 수)입니다. 아래 예에서 첫 번째 그래프는 성공적인 배달이 파란색으로 표시되고 잘못된 배달이 주황색으로 표시됩니다.

![](assets/s_ncs_user_report_toolbar.png)

시간 표시줄을 변경하여 표시되는 값을 구성할 수 있습니다.1시간 뷰, 3시간 뷰, 24시간 뷰 등 **[!UICONTROL Refresh]**&#x200B;을(를) 클릭하여 선택 항목을 확인합니다.

## 사용자 활동 {#user-activities}

이 보고서는 차트 형태로 30분, 시간 또는 일별 열기, 클릭 및 거래의 분류를 보여줍니다.

![](assets/s_ncs_user_user_report.png)

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Opens]** :연 총 메시지 수입니다. 텍스트 형식의 이메일은 고려되지 않습니다. 열기 추적에 대한 자세한 내용은 [추적 열기](../../reporting/using/indicator-calculation.md#tracking-opens-)를 참조하십시오.
* **[!UICONTROL Clicks]** :배달에서 링크에 대한 총 클릭 수입니다. 구독하지 않은 링크 및 미러 페이지에 대한 클릭은 고려되지 않습니다.
* **[!UICONTROL Transactions]** :메시지를 받은 후의 총 거래 수입니다. 트랜잭션을 고려하려면 트랜잭션 유형 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성은 [이 섹션](../../configuration/using/about-web-tracking.md)에 제공됩니다.

## 게재 불가 및 이탈 {#non-deliverables-and-bounces}

이 보고서는 인터넷 도메인별 바운스 수 분류와 비산출물의 분류를 보여줍니다.

**[!UICONTROL Number of messages processed]**&#x200B;은 배달 서버에서 처리한 총 메시지 수를 나타냅니다. 이 값은 일부 배달이 중지되거나 일시 중지되었을 때(서버에서 처리되기 전에) 배달될 메시지 수보다 작습니다.

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>이 보고서에 표시된 오류는 격리 프로세스를 트리거합니다. 격리 관리에 대한 자세한 내용은 [격리 관리](../../delivery/using/understanding-quarantine-management.md)를 참조하십시오.

이 보고서의 첫 번째 섹션에서는 비결과물의 분류를 값 테이블 및 차트 형태로 보여줍니다.

각 오류 유형에 대해 다음과 같습니다.

* 이 유형의 오류 메시지 수,
* 오류가 있는 총 메시지 수와 비교하여 이 유형의 오류가 있는 메시지의 백분율입니다.
* 처리된 총 메시지 수와 비교하여 이 유형의 오류 메시지의 백분율입니다.

다음 표시기가 사용됩니다.

* **[!UICONTROL User unknown]** :배달 중에 생성된 오류 유형으로 이메일 주소가 잘못되었음을 나타냅니다.
* **[!UICONTROL Invalid domain]** :이메일 주소 도메인이 잘못되었거나 존재하지 않음을 나타내는 배달을 보낼 때 생성되는 오류 유형입니다.
* **[!UICONTROL Inbox full]** :받는 사람의 받은 편지함에 너무 많은 메시지가 포함됨을 나타내는 5번의 배달 시도 후 생성되는 오류 유형입니다.
* **[!UICONTROL Account disabled]** :주소가 더 이상 존재하지 않는다는 것을 나타내기 위해 배달을 보낼 때 생성되는 오류 유형입니다.
* **[!UICONTROL Rejected]** :IAP(Internet Access Provider)에서 보안 규칙(스팸 방지 소프트웨어) 응용 프로그램의 경우와 같이 주소가 거부될 때 생성되는 오류 유형입니다.
* **[!UICONTROL Unreachable]** :메시지 배포 문자열에서 발생하는 오류 유형:SMTP 릴레이, 일시적으로 도메인 연결 불가 등의 장애
* **[!UICONTROL Not connected]** :전송 시 받는 사람의 휴대 전화가 꺼져 있거나 네트워크에서 연결이 끊겼음을 나타내는 오류 유형입니다.

   >[!NOTE]
   >
   >이 지표는 모바일 채널의 배달에만 해당됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/sms-channel.md)을 참조하십시오.

   `[+]` 기호를 클릭하여 값 테이블의 각 행을 열 수 있습니다. 각 오류 유형에 대해 도메인별 오류 메시지 분류를 표시할 수 있습니다.

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

이 보고서의 두 번째 섹션은 값 테이블 및 차트 형태로 인터넷 도메인별 오류 분류를 보여줍니다.

각 도메인 이름에 대해 다음과 같은 항목이 있습니다.

* 이 도메인에 대한 오류가 있는 메시지 수,
* 이 도메인에 대해 처리된 총 메시지 수와 비교하여 오류가 있는 메시지의 백분율입니다.
* 이 도메인에 대한 오류 메시지의 백분율과 총 오류 메시지 수입니다.

[+] 기호를 클릭하여 값 테이블의 각 행을 열 수 있습니다. 각 도메인 유형에 대해 오류 메시지 분류를 오류 유형별로 표시할 수 있습니다.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>이 보고서에 표시되는 도메인 이름은 큐브 수준에서 정의됩니다. 이 값을 변경하려면 **[!UICONTROL Delivery logs (broadlogrcp)]** 큐브를 편집합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/about-cubes.md)을 참조하십시오. **[!UICONTROL Others]** 범주는 특정 클래스에 속하지 않는 도메인 이름을 포함합니다.

## 브라우저 {#browsers}

이 보고서는 전달 받는 사람이 해당 기간 동안 사용한 인터넷 브라우저의 분류를 보여줍니다.

>[!NOTE]
>
>이 보고서에 표시되는 값은 다음과 같은 예상 값입니다.배달을 클릭한 수신자만 고려됩니다.

**글로벌 통계**

브라우저 사용에 대한 전역 통계는 값 테이블 및 차트 형태로 표시됩니다.

![](assets/dlv_explorers_report.png)

다음 표시기가 사용됩니다.

* **[!UICONTROL Visitors]** :최소 한 번 이상 배달을 클릭한 대상(인터넷 브라우저당)의 총 받는 사람 수입니다.
* **[!UICONTROL Pages viewed]** :모든 게재에 대한 배달의 링크(인터넷 브라우저당)에 대한 총 클릭 수입니다.
* **[!UICONTROL Usage rate]** :이 비율은 총 방문자 수와 관련된 방문자(인터넷 브라우저당) 분류를 나타냅니다.

**브라우저별 통계**

글로벌 통계 값 테이블에서 각 브라우저 이름을 클릭하여 사용 통계를 볼 수 있습니다.

![](assets/s_ncs_user_explorers_report2.png)

통계는 곡선, 차트 및 값 테이블의 형태로 표시됩니다.

**[!UICONTROL History]** 곡선은 일일 이 브라우저의 참석 비율을 나타냅니다. 비율은 일일 방문자 수(이 브라우저의 방문자 수)와 가장 높은 참여율을 기록한 날짜에 측정된 방문자 수를 비교한 것입니다.

**[!UICONTROL Breakdown per version]** 차트는 이 브라우저의 총 방문자 수와 비교한 버전당 방문자 수 분류를 나타냅니다.

값 표는 다음 표시기를 사용합니다.

* **[!UICONTROL Global rate]** :이 비율은 모든 브라우저에서 총 방문자 수와 비교하여 버전당 방문자 수를 나타냅니다.
* **[!UICONTROL Relative rate]** :이 비율은 전체 방문자 수(이 브라우저의 총 방문자 수)와 비교하여 버전당 방문자 수를 나타냅니다.

### 소셜 네트워크에 공유 {#sharing-to-social-networks}

바이럴 마케팅을 통해 배달 수신자는 연락처 네트워크와 정보를 공유할 수 있습니다.프로필(Facebook, Twitter 등)에 링크를 추가할 수 있습니다. 또는 친구에게 메시지를 보냅니다. 공유 정보에 대한 각 공유 및 각 액세스 권한은 배달 내에서 추적됩니다. 바이러스 마케팅에 대한 자세한 내용은 [이 섹션](../../delivery/using/viral-and-social-marketing.md)을 참조하십시오.

이 보고서는 소셜 네트워크(Facebook, Twitter 등)당 공유 및 열린 메시지의 분류를 보여줍니다. 및/또는 이메일별.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

이메일 배달 통계에서 2개의 값이 표시됩니다.

* **[!UICONTROL Number of messages to be delivered]** :배달 분석 중에 처리된 총 메시지 수입니다.
* **[!UICONTROL Number of successful deliveries]** :처리된 메시지 수입니다.

**[!UICONTROL Sharing activities and mail open statistics]**

중앙 표는 이메일 공유에 대한 통계를 보여주고 열립니다.

**[!UICONTROL Shares]** 열에는 다음과 같은 지표가 있습니다.

* **[!UICONTROL No. of sharing activities]** :각 소셜 네트워크에서 공유되는 총 메시지 수입니다. 이 값은 일치하는 **[!UICONTROL Links for sharing to social networks]** 개인화 블록의 아이콘에 대한 총 클릭 수와 같습니다.
* **[!UICONTROL Breakdown]** :이 비율은 총 공유 수와 관련하여 소셜 네트워크당 공유 수를 분류합니다.
* **[!UICONTROL Sharing rate]** :이 비율은 제공할 메시지 수와 관련하여 소셜 네트워크당 공유 수를 나타냅니다.

**[!UICONTROL Opens]** 열에는 다음과 같은 지표가 있습니다.

* **[!UICONTROL No. of opens]** :메시지를 전달받은 사람이 연 총 메시지  **[!UICONTROL Links for sharing to social networks]** 수입니다(개인화 블록을 통해). 이 값은 미러 페이지가 표시된 횟수와 같습니다. 배달 받는 사람이 여는 것은 고려되지 않습니다.
* **[!UICONTROL Breakdown]** :이 속도는 총 열기 수와 관련하여 소셜 네트워크당 열린 횟수를 나타냅니다.
* **[!UICONTROL Rate of opens]** :이 비율은 총 공유 수와 관련하여 소셜 네트워크당 열린 분산을 나타냅니다.

**[!UICONTROL Breakdown of sharing activities and opens]**

이 섹션에는 공유 활동 분류를 나타내며 소셜 네트워크별로 열리는 2개의 차트가 포함되어 있습니다.

## 활동 공유 통계 {#statistics-on-sharing-activities}

이 보고서는 소셜 네트워크(Facebook, Twitter, 이메일 등)로 공유의 진화를 보여줍니다. 적시에.

바이러스 마케팅에 대한 자세한 내용은 [이 섹션](../../delivery/using/viral-and-social-marketing.md)을 참조하십시오.

![](assets/s_ncs_user_social_report2.png)

통계는 값 테이블과 차트의 형태로 표시됩니다.

다음 표시기가 사용됩니다.

* **[!UICONTROL New contacts]** :이메일을 통해 공유된 메시지를 받은 후 새로 구독한 수. 이 값은 이메일을 통해 공유된 메시지를 받고 **[!UICONTROL Subscription link]**&#x200B;을 클릭한 후 구독 양식에 입력한 사람의 수와 일치합니다.
* **[!UICONTROL Opens]** :메시지를 전송한 사람이 연 총 메시지  **[!UICONTROL Link for sharing to social networks]** 수입니다(개인화 블록을 통해). 이 값은 미러 페이지가 표시된 횟수와 같습니다. 배달 받는 사람이 여는 것은 고려되지 않습니다.
* **[!UICONTROL Sharing activities]** :소셜 네트워크를 통해 공유된 총 메시지 수입니다. 이 값은 **[!UICONTROL Links for sharing to social networks]** 개인화 블록의 아이콘에 대한 총 클릭 수와 일치합니다.

## 운영 체제 {#operating-systems}

이 보고서는 전달 받는 사람이 해당 기간 동안 사용한 운영 체제의 분류를 보여줍니다.

>[!NOTE]
>
>이 보고서에 표시되는 값은 다음과 같은 예상 값입니다.배달을 클릭한 수신자만 고려됩니다.

**글로벌 통계**

운영 체제의 전역 사용량 통계는 값 테이블 및 차트 형태로 표시됩니다.

![](assets/s_ncs_user_os_report.png)

다음 표시기가 사용됩니다.

* **[!UICONTROL Visitors]** :최소 한 번 이상 배달을 클릭한 대상 받는 사람(운영 체제당)의 총 일별 평균입니다.
* **[!UICONTROL Pages viewed]** :모든 게재에 대한 배달 링크(운영 체제당)에 대한 총 클릭 수의 일별 평균입니다.
* **[!UICONTROL Rate of use]** :이 비율은 총 방문자 수와 관련하여 방문자 수(운영 체제당)를 분류합니다.

**운영 체제별 통계**

글로벌 통계 값 표에서 각 운영 체제의 이름을 클릭하여 운영 체제별 통계를 봅니다.

![](assets/s_ncs_user_os_report2.png)

통계는 곡선, 차트 및 값 테이블의 형태로 표시됩니다.

**[!UICONTROL History]** 곡선은 이 운영 체제의 일별 사용 비율을 나타냅니다. 이 비율은 하루(이 운영 체제에서) 가장 높은 참석으로 하루 측정된 방문자 수와 관련하여 일일 방문자 수의 비율입니다.

**[!UICONTROL Breakdown by version]** 차트는 이 운영 체제의 총 방문자 수와 관련된 버전당 방문자 수의 분류를 나타냅니다.

값 표는 다음 표시기를 사용합니다.

* **[!UICONTROL Global rate]** :이 비율은 운영 체제 전체의 총 방문자 수와 관련하여 방문자 수(버전당)의 분류를 나타냅니다.
* **[!UICONTROL Relative rate]** :이 비율은 이 운영 체제의 총 방문자 수와 관련하여 방문자 수(버전당)의 분류를 나타냅니다.

## 구독 추적 {#subscription-tracking}

이 보고서를 사용하면 정보 서비스 가입을 모니터링할 수 있습니다. 구독 및 구독 취소가 표시됩니다.

![](assets/s_ncs_user_services_report.png)

홈 페이지 또는 탐색기의 **[!UICONTROL Profiles and targets > Services and subscriptions]** 노드를 클릭하여 구독에 표시할 수 있습니다. 원하는 구독을 선택한 다음 **[!UICONTROL Reports]** 탭을 클릭합니다. 기본적으로 **[!UICONTROL Subscriptions tracking]** 보고서를 사용할 수 있습니다. 일정 기간 동안의 구독 및 구독 취소 트렌드와 로열티 비율을 확인할 수 있습니다. 드롭다운 목록을 통해 이 데이터의 표현을 구성할 수 있습니다. **[!UICONTROL Refresh]**&#x200B;을 클릭하여 선택한 구성을 확인합니다.

자세한 내용은 [이 페이지](../../delivery/using/managing-subscriptions.md)를 참조하십시오.

**[!UICONTROL Number subscribed to date]**&#x200B;은 현재 구독된 총 사용자 수를 나타냅니다.

**[!UICONTROL Overall evolution of subscriptions]**

값 표는 다음 표시기를 사용합니다.

* **[!UICONTROL Subscribers]** :해당 기간의 총 가입자 수입니다.
* **[!UICONTROL Subscriptions]** :해당 기간에 대한 구독 수입니다.
* **[!UICONTROL Unsubscriptions]** :해당 기간에 대한 미구독 수입니다.
* **[!UICONTROL Evolution]** :구독 취소 수를 뺀 값입니다. 이 비율은 총 가입자 수를 기반으로 계산됩니다.
* **[!UICONTROL Loyalty]** :해당 기간에 가입자의 충성도 비율

**[!UICONTROL Subscription evolution curves]**

이 차트는 해당 기간 동안의 가입 및 가입 해지 진행 상태를 보여줍니다.

## 배달 통계 {#delivery-statistics}

이 보고서는 인터넷 도메인, 처리 및 전송되는 모든 메시지, 하드 바운스, 열기, 클릭 수 및 구독 취소의 분류를 보여줍니다.

![](assets/s_ncs_user_broadcast_report.png)

다음 표시기가 사용됩니다.

* **[!UICONTROL Emails processed]** :배달 서버에서 처리한 총 메시지 수입니다.
* **[!UICONTROL Delivered]** :처리된 총 메시지 수와 비교하여 성공한 메시지 수의 백분율입니다.
* **[!UICONTROL Hard bounces]** :처리된 총 메시지 수와 비교하여 &quot;하드&quot; 바운스 수의 백분율입니다.
* **[!UICONTROL Soft bounces]** :처리된 총 메시지 수와 비교하여 &quot;소프트&quot; 바운스 수의 백분율입니다.

   >[!NOTE]
   >
   >하드 바운스 및 소프트 바운스에 대한 자세한 내용은 [격리 관리](../../delivery/using/understanding-quarantine-management.md)를 참조하십시오.

* **[!UICONTROL Opens]** :메시지를 최소한 한 번 이상 연 대상 받는 사람 수의 백분율과 처리된 메시지 수를 비교한 것입니다.
* **[!UICONTROL Clicks]** :배달을 한 번 이상 클릭한 사람의 백분율이며, 성공적으로 처리된 메시지 수와 비교하여 백분율입니다.
* **[!UICONTROL Unsubscription]** :처리되지 않은 링크에 대한 클릭 수의 백분율을 처리한 메시지 수와 비교하여 나타냅니다.

## 열기 {#breakdown-of-opens} 분류

이 보고서는 해당 기간에 대한 운영 체제, 장치 및 브라우저별 열기 분류를 보여줍니다. 각 카테고리에 대해 2개의 차트가 사용됩니다. 첫 번째 필드는 컴퓨터 및 모바일 장치에서 열리는 것과 관련된 통계를 표시합니다. 두 번째 슬라이드에는 모바일 장치에서 열리는 경우에만 관련된 통계가 표시됩니다.

연 수는 열린 총 메시지 수에 해당합니다. 텍스트 형식 이메일은 카운트되지 않습니다. 추적이 열리는 방법에 대한 자세한 내용은 [추적 열기](../../reporting/using/indicator-calculation.md#tracking-opens-) 섹션을 참조하십시오.

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>브라우저 및 운영 체제 이름은 메시지를 연 브라우저의 사용자 에이전트가 전송한 정보의 일부를 구성합니다. Adobe Campaign은 장치 정보를 사용하여 장치 유형을 추론합니다.