---
product: campaign
title: 전반적 보고서
description: 전반적 보고서
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Reporting, Monitoring
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '2292'
ht-degree: 6%

---

# 전반적 보고서 {#global-reports}



이러한 보고서는 전체 데이터베이스의 데이터 활동과 관련이 있습니다. 보고서 대시보드를 보려면 **[!UICONTROL Reports]** 탭.

![](assets/s_ncs_user_report_delivery_link.png)

보고서를 표시하려면 보고서 이름을 클릭합니다. 기본적으로 다음 보고서를 사용할 수 있습니다.

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>이 섹션에는 게재에 연결된 보고서만 표시됩니다.

* **[!UICONTROL Delivery throughput]** : 를 참조하십시오. [게재 처리량](#delivery-throughput).
* **[!UICONTROL Browsers]** : 를 참조하십시오. [브라우저](#browsers).
* **[!UICONTROL Sharing to social networks]** : 를 참조하십시오. [소셜 네트워크에 공유](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** : 를 참조하십시오. [공유 활동에 대한 통계](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** : 를 참조하십시오. [운영 체제](#operating-systems).
* **[!UICONTROL URLs and click streams]** : 를 참조하십시오. [URL 및 클릭 스트림](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** : 를 참조하십시오. [지표 추적](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** : 를 참조하십시오. [게재 불가 및 이탈](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** : 를 참조하십시오. [사용자 활동](#user-activities).
* **[!UICONTROL Subscription tracking]** : 를 참조하십시오. [구독 추적](#subscription-tracking).
* **[!UICONTROL Delivery summary]** : 를 참조하십시오. [게재 요약](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** : 를 참조하십시오. [게재 통계](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** : 를 참조하십시오. [열람 분류](#breakdown-of-opens).

## 게재 처리량 {#delivery-throughput}

이 보고서에는 주어진 기간 동안 전체 플랫폼의 게재 처리량에 대한 정보가 포함되어 있습니다. 메시지가 게재되는 속도를 측정하기 위한 기준은 시간당 전송된 메시지 수와 메시지 크기(초당 비트 수)입니다. 아래 예에서는 첫 번째 그래프에 성공한 게재 수는 파란색으로, 잘못된 게재 수는 주황색으로 표시됩니다.

![](assets/s_ncs_user_report_toolbar.png)

시간 표시 막대를 변경하여 표시되는 값을 구성할 수 있습니다(1시간 보기, 3시간 보기, 24시간 보기 등). 클릭 **[!UICONTROL Refresh]** 을 클릭하여 선택 항목을 확인합니다.

>[!NOTE]
>
>인스턴스가 AWS에서 호스팅되는 경우 Campaign Classic을 사용하여 시간당 전송된 게재 수를 모니터링할 수도 있습니다 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). 인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=ko)에 설명된 단계를 수행합니다.
>
>컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel)에 자세히 설명되어 있습니다.
>
>인스턴스를 최신 버전으로 업그레이드해야 합니다. [Gold 표준](../../rn/using/gold-standard.md) 또는 [최신 GA 빌드(21.1.3)](../../rn/using/latest-release.md). 에서 버전을 확인하는 방법을 알아봅니다. [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## 사용자 활동 {#user-activities}

이 보고서는 30분, 시간 또는 일별 열기, 클릭 수 및 거래 분류를 차트의 형식으로 표시합니다.

![](assets/s_ncs_user_user_report.png)

다음 옵션을 사용할 수 있습니다.

* **[!UICONTROL Opens]** : 열린 총 메시지 수입니다. 텍스트 형식의 이메일은 고려되지 않습니다. 열기 추적에 대한 자세한 내용은 [열람 추적](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : 게재의 총 링크 클릭 수입니다. 구독 취소 링크 및 미러 페이지에 대한 클릭은 고려되지 않습니다.
* **[!UICONTROL Transactions]** : 메시지를 받은 후 총 트랜잭션 수 트랜잭션을 고려하려면 트랜잭션 유형 웹 추적 태그를 일치하는 웹 페이지에 삽입해야 합니다. 웹 추적 구성은에 표시됩니다. [이 섹션](../../configuration/using/about-web-tracking.md).

## 게재 불가 및 이탈 {#non-deliverables-and-bounces}

이 보고서는 비게재 항목 분류와 인터넷 도메인별 바운스 수 분류를 보여줍니다.

다음 **[!UICONTROL Number of messages processed]** 게재 서버에서 처리된 총 메시지 수를 나타냅니다. 이 값은 일부 게재가 중지 또는 일시 중지되었을 때(서버에서 처리되기 전에) 게재할 메시지 수보다 적습니다.

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>이 보고서에 표시된 오류는 격리 프로세스를 트리거합니다. 격리 관리에 대한 자세한 내용은 다음을 참조하십시오. [격리 관리](../../delivery/using/understanding-quarantine-management.md).

이 보고서의 첫 번째 섹션은 게재 불가 분류를 값 테이블 및 차트 형태로 보여줍니다.

각 오류 유형에 대해 다음이 제공됩니다.

* 이 유형의 오류 메시지 수,
* 오류가 있는 총 메시지 수와 비교한 이 유형의 오류가 있는 메시지의 비율입니다.
* 처리된 총 메시지 수와 비교한 이 유형의 오류 메시지 비율입니다.

다음 지표가 사용됩니다.

* **[!UICONTROL User unknown]** : 이메일 주소가 잘못되었음을 나타내기 위해 게재 중에 생성된 오류 유형.
* **[!UICONTROL Invalid domain]** : 이메일 주소의 도메인이 잘못되었거나 존재하지 않음을 나타내기 위해 게재를 보낼 때 생성되는 오류 유형입니다.
* **[!UICONTROL Inbox full]** : 5회 게재 시도 후 생성된 오류 유형은 수신자의 받은 편지함에 메시지가 너무 많음을 나타냅니다.
* **[!UICONTROL Account disabled]** : 주소가 더 이상 존재하지 않음을 나타내기 위해 게재를 보낼 때 생성된 오류 유형.
* **[!UICONTROL Rejected]** : IAP(인터넷 액세스 공급자)에서 주소를 거부할 때 오류 유형 이 생성됩니다(예: 보안 규칙 적용 후).
* **[!UICONTROL Unreachable]** : 메시지 배포 문자열에서 발생하는 오류 유형: SMTP 릴레이 장애, 일시적으로 도메인에 연결할 수 없음 등
* **[!UICONTROL Not connected]** : 전송 시 수신자의 휴대폰이 꺼져 있거나 네트워크에서 연결이 끊겼음을 나타내는 오류 유형입니다.

  >[!NOTE]
  >
  >이 표시기는 모바일 채널 게재에만 관련됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/sms-channel.md)을 참조하십시오.

  다음을 눌러 값 테이블의 각 행을 열 수 있습니다. `[+]` 기호. 각 오류 유형에 대해 도메인별 오류 메시지 분류를 표시할 수 있습니다.

  ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

이 보고서의 두 번째 섹션은 값 테이블 및 차트 형태로 인터넷 도메인별 오류 분류를 보여 줍니다.

각 도메인 이름에는 다음이 있습니다.

* 이 도메인에 대한 오류가 있는 메시지 수,
* 이 도메인에 대해 처리된 총 메시지 수와 비교한 이 도메인에 대해 오류가 있는 메시지의 비율입니다.
* 총 오류 메시지 수와 비교한 이 도메인에 대한 오류 메시지의 비율입니다.

다음을 눌러 값 테이블의 각 행을 열 수 있습니다. [+] 기호. 각 도메인 유형에 대해 오류 유형별로 오류 메시지 분류를 표시할 수 있습니다.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>이 보고서에 표시되는 도메인 이름은 큐브 수준에서 정의됩니다. 이러한 값을 변경하려면 **[!UICONTROL Delivery logs (broadlogrcp)]** 큐브. 자세한 내용은 다음을 참조하십시오. [이 섹션](../../reporting/using/ac-cubes.md). 다음 **[!UICONTROL Others]** 카테고리에는 특정 클래스에 속하지 않는 도메인 이름이 포함되어 있습니다.

## 브라우저 {#browsers}

이 보고서는 게재 수신자가 관련 기간 동안 사용한 인터넷 브라우저의 분류를 보여줍니다.

>[!NOTE]
>
>이 보고서에 표시된 값은 예상 값입니다. 게재를 클릭한 수신자만 고려됩니다.

**전역 통계**

브라우저 사용에 대한 전역 통계는 값 테이블 및 차트 형태로 표시됩니다.

![](assets/dlv_explorers_report.png)

다음 지표가 사용됩니다.

* **[!UICONTROL Visitors]** : 타겟팅하고(인터넷 브라우저당) 한 번 이상 게재를 클릭한 총 수신자 수입니다.
* **[!UICONTROL Pages viewed]** : 모든 게재에 대한 게재(인터넷 브라우저당)의 총 링크 클릭 수입니다.
* **[!UICONTROL Usage rate]** : 이 비율은 총 방문자 수와 관련된 방문자 수 (인터넷 브라우저당)의 분류를 나타냅니다.

**브라우저당 통계**

글로벌 통계 값 테이블에서 각 브라우저 이름을 눌러 해당 사용 통계를 볼 수 있습니다.

![](assets/s_ncs_user_explorers_report2.png)

통계는 곡선, 도표 및 값 표의 형태로 제시된다.

다음 **[!UICONTROL History]** curve는 이 브라우저의 일별 출석률을 나타냅니다. 이 비율은 방문자가 가장 높은 방문율을 보인 날에 측정된 방문자 수와 비교한 일일 방문자 수 (이 브라우저의 방문자 수)의 비율입니다.

다음 **[!UICONTROL Breakdown per version]** 차트는 (이 브라우저의) 총 방문자 수와 비교한 버전당 방문자 수를 나타냅니다.

값 테이블에서는 다음 지표를 사용합니다.

* **[!UICONTROL Global rate]** : 이 비율은 (모든 브라우저에서) 총 방문자 수와 비교한 버전당 방문자 수를 나타냅니다.
* **[!UICONTROL Relative rate]** : 이 비율은 (이 브라우저의) 총 방문자 수와 비교한 버전당 방문자 수를 나타냅니다.

### 소셜 네트워크에 공유 {#sharing-to-social-networks}

바이럴 마케팅을 통해 게재 수신자는 연락처 네트워크와 정보를 공유할 수 있습니다. 프로필에 링크를 추가할 수 있습니다(Facebook, X - 이전 명칭: Twitter 등) 또는 친구에게 메시지를 보냅니다. 각 공유 및 공유 정보에 대한 각 액세스는 게재 내에서 추적됩니다. 바이럴 마케팅에 대한 자세한 내용은 [이 섹션](../../delivery/using/viral-and-social-marketing.md).

이 보고서는 소셜 네트워크(Facebook, X 등)당 공유 및 열린 메시지의 분류를 보여줍니다. 및/또는 이메일당.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

이메일 게재 통계에는 두 가지 값이 표시됩니다.

* **[!UICONTROL Number of messages to be delivered]** : 게재 분석 중에 처리된 총 메시지 수입니다.
* **[!UICONTROL Number of successful deliveries]** : 정상적으로 처리된 메시지 수.

**[!UICONTROL Sharing activities and mail open statistics]**

중앙 테이블은 이메일 공유 및 열람에 대한 통계를 보여 줍니다.

다음에서 **[!UICONTROL Shares]** 열에는 다음과 같은 표시기가 있습니다.

* **[!UICONTROL No. of sharing activities]** : 각 소셜 네트워크에서 공유되는 총 메시지 수입니다. 이 값은 일치 아이콘의 총 클릭 수와 같습니다 **[!UICONTROL Links for sharing to social networks]** 개인화 블록.
* **[!UICONTROL Breakdown]** : 이 비율은 총 주식 수와 관련된 소셜 네트워크당 주식 분류를 나타냅니다.
* **[!UICONTROL Sharing rate]** : 이 비율은 게재할 메시지 수와 관련된 소셜 네트워크당 주식 분류를 나타냅니다.

다음에서 **[!UICONTROL Opens]** 열에는 다음과 같은 표시기가 있습니다.

* **[!UICONTROL No. of opens]** : (를 통해) 메시지가 전달된 사람이 연 총 메시지 수 **[!UICONTROL Links for sharing to social networks]** 개인화 블록). 이 값은 미러 페이지가 표시된 횟수와 같습니다. 게재 수신자가 연 횟수는 고려하지 않습니다.
* **[!UICONTROL Breakdown]** : 이 비율은 총 열람 수와 관련된 소셜 네트워크당 열람 수 분류를 나타냅니다.
* **[!UICONTROL Rate of opens]** : 이 비율은 총 공유 수와 관련된 소셜 네트워크당 열기 수를 분류합니다.

**[!UICONTROL Breakdown of sharing activities and opens]**

이 섹션에는 공유 활동 및 소셜 네트워크당 열기 수를 보여 주는 두 개의 차트가 포함되어 있습니다.

## 공유 활동에 대한 통계 {#statistics-on-sharing-activities}

이 보고서는 소셜 네트워크(Facebook, X - 이전에는 Twitter, 이메일 등으로 알려짐)에 대한 공유를 발전시킨 모습을 보여줍니다. 늦지 않게

바이럴 마케팅에 대한 자세한 내용은 [이 섹션](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

통계는 값 표 및 차트 형태로 제공됩니다.

다음 지표가 사용됩니다.

* **[!UICONTROL New contacts]** : 이메일을 통해 공유한 메시지 수신 후 새로 가입한 수입니다. 이 값은 이메일을 통해 공유되고 을(를) 클릭한 메시지를 받은 사람 수와 일치합니다. **[!UICONTROL Subscription link]** 구독 양식에 을(를) 입력했습니다.
* **[!UICONTROL Opens]** : 메시지를 (을)를 통해 전송한 사람이 연 총 메시지 수 **[!UICONTROL Link for sharing to social networks]** 개인화 블록). 이 값은 미러 페이지가 표시된 횟수와 같습니다. 게재 수신자가 연 횟수는 고려하지 않습니다.
* **[!UICONTROL Sharing activities]** : 소셜 네트워크를 통해 공유된 총 메시지 수입니다. 이 값은 의 아이콘에 대한 총 클릭 수와 일치합니다. **[!UICONTROL Links for sharing to social networks]** 개인화 블록.

## 운영 체제 {#operating-systems}

이 보고서는 관련 기간 동안 게재 수신자가 사용한 운영 체제의 분류를 보여줍니다.

>[!NOTE]
>
>이 보고서에 표시된 값은 예상 값입니다. 게재를 클릭한 수신자만 고려됩니다.

**전역 통계**

운영 체제의 전역 사용 통계는 값 표 및 차트 형태로 제공됩니다.

![](assets/s_ncs_user_os_report.png)

다음 지표가 사용됩니다.

* **[!UICONTROL Visitors]** : 한 번 이상 게재를 클릭한 총 대상 수신자 수(운영 체제당)의 일일 평균.
* **[!UICONTROL Pages viewed]** : 모든 게재에 대한 게재 링크의 총 클릭 수(운영 체제당)의 일일 평균.
* **[!UICONTROL Rate of use]** : 이 비율은 총 방문자 수와 관련된 방문자 수(운영 체제당)의 분류를 나타냅니다.

**운영 체제별 통계**

글로벌 통계 값 테이블에서 각 운영 체제의 이름을 눌러 운영 체제별 통계를 확인합니다.

![](assets/s_ncs_user_os_report2.png)

통계는 곡선, 도표 및 값 표의 형태로 제시된다.

다음 **[!UICONTROL History]** 곡선은 하루 이 운영 체제의 사용률을 나타냅니다. 이 비율은 가장 높은 방문자가 있는 날에 측정된 방문자 수와 관련된 일일 방문자 수(이 운영 체제에서)의 비율입니다.

다음 **[!UICONTROL Breakdown by version]** 차트는 이 운영 체제의 총 방문자 수와 관련된 버전별 방문자 수 분류를 나타냅니다.

값 테이블에서는 다음 지표를 사용합니다.

* **[!UICONTROL Global rate]** : 이 비율은 운영 체제 전체의 총 방문자 수와 관련된 방문자 수 (버전당)의 분류를 나타냅니다.
* **[!UICONTROL Relative rate]** : 이 비율은 이 운영 체제에 대한 총 방문자 수와 관련된 방문자 수(버전당)의 분류를 나타냅니다.

## 구독 추적 {#subscription-tracking}

이 보고서를 사용하면 정보 서비스 구독을 모니터링할 수 있습니다. 여기에는 구독 및 구독 취소가 표시됩니다.

![](assets/s_ncs_user_services_report.png)

다음을 클릭하여 구독에 대해 표시할 수 있습니다. **[!UICONTROL Profiles and targets > Services and subscriptions]** 홈 페이지 또는 탐색기의 노드입니다. 원하는 구독을 선택하고 **[!UICONTROL Reports]** 탭. 다음 **[!UICONTROL Subscriptions tracking]** 보고서는 기본적으로 사용할 수 있습니다. 일정 기간 동안의 구독 및 구독 취소 트렌드와 충성도 비율을 확인할 수 있습니다. 드롭다운 목록을 통해 이 데이터의 표현을 구성할 수 있습니다. 클릭 **[!UICONTROL Refresh]** 을 눌러 선택한 구성의 유효성을 검사합니다.

자세한 내용은 다음을 참조하십시오. [이 페이지](../../delivery/using/managing-subscriptions.md).

다음 **[!UICONTROL Number subscribed to date]** 현재 구독한 총 사람 수를 나타냅니다.

**[!UICONTROL Overall evolution of subscriptions]**

값 테이블에서는 다음 지표를 사용합니다.

* **[!UICONTROL Subscribers]** : 해당 기간의 총 구독자 수
* **[!UICONTROL Subscriptions]** : 해당 기간의 구독 수.
* **[!UICONTROL Unsubscriptions]** : 해당 기간의 구독 취소 수
* **[!UICONTROL Evolution]** : 구독 취소에서 구독 수를 뺀 수입니다. 요금은 총 가입자 수를 기준으로 계산됩니다.
* **[!UICONTROL Loyalty]** : 해당 기간 동안 구독자의 충성도 비율입니다.

**[!UICONTROL Subscription evolution curves]**

이 차트는 관련 기간에 대한 구독 및 구독 취소의 진화를 보여 줍니다.

## 게재 통계 {#delivery-statistics}

이 보고서는 인터넷 도메인별, 처리 및 전송된 모든 메시지, 하드 및 소프트 바운스, 열기, 클릭 및 구독 취소에 대한 분류를 보여줍니다.

![](assets/s_ncs_user_broadcast_report.png)

다음 지표가 사용됩니다.

* **[!UICONTROL Emails processed]** : 게재 서버에서 처리된 총 메시지 수입니다.
* **[!UICONTROL Delivered]** : 처리된 총 메시지 수와 비교하여 성공적으로 처리된 메시지 수의 백분율입니다.
* **[!UICONTROL Hard bounces]** : 처리된 총 메시지 수 대비 &quot;하드&quot; 바운스 수의 백분율입니다.
* **[!UICONTROL Soft bounces]** : 처리된 총 메시지 수 대비 &quot;소프트&quot; 바운스 수의 백분율입니다.

  >[!NOTE]
  >
  >하드 및 소프트 바운스에 대한 자세한 내용은 [격리 관리](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** : 성공적으로 처리된 메시지 수와 비교하여 메시지를 한 번 이상 연 타겟팅된 수신자 수의 백분율입니다.
* **[!UICONTROL Clicks]** : 성공적으로 처리된 메시지 수와 비교하여 게재를 한 번 이상 클릭한 사람 수의 백분율입니다.
* **[!UICONTROL Unsubscription]** : 성공적으로 처리된 메시지 수와 비교한 구독 취소 링크의 클릭 수의 백분율입니다.

## 열람수 분류 {#breakdown-of-opens}

이 보고서는 해당 기간에 대한 운영 체제, 장치 및 브라우저별 열기 분석을 보여 줍니다. 각 범주별로 두 개의 차트가 사용됩니다. 첫 번째 차트에는 컴퓨터 및 모바일 디바이스에서의 열람과 관련된 통계가 표시됩니다. 두 번째 차트에는 모바일 디바이스에서의 열람과 관련된 통계만 표시됩니다.

열기 횟수는 열린 총 메시지 수에 해당합니다. 텍스트 형식 이메일은 카운트되지 않습니다. 열기 추적에 대한 자세한 내용은 [열람 추적](../../reporting/using/indicator-calculation.md#tracking-opens-) 섹션.

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>브라우저 및 운영 체제 이름은 메시지가 열린 브라우저의 사용자 에이전트에서 보낸 정보의 일부를 구성합니다. Adobe Campaign은 장치 정보를 사용하여 장치 유형을 추론합니다.
