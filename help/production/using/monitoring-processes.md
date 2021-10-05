---
product: campaign
title: 프로세스 모니터링
description: Campaign 프로세스를 모니터링하는 방법 알아보기
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '3606'
ht-degree: 0%

---

# 프로세스 모니터링{#monitoring-processes}

![](../../assets/v7-only.svg)

응용 프로그램 서버와 리디렉션 서버(**tracking**)는 수동으로 또는 자동으로 모니터링할 수 있습니다.

## 수동 모니터링 {#manual-monitoring}

**[!UICONTROL Monitoring]** 로 이동하고 **[!UICONTROL Overview]** 링크를 클릭하여 Adobe Campaign 프로세스 모니터링 페이지를 표시합니다.

![](assets/d_ncs_monitoring.png)

표시된 페이지를 사용하여 연결된 인스턴스의 상태(예:

* 인스턴스에 대한 정보: 버전, 이름, 데이터베이스 엔진, 설치된 패키지, 서버 시스템 표시기
* 누락된 프로세스 및 실행 정보 목록(시작 날짜, PID 등),
* 워크플로우 및 게재 보기.

다른 Campaign 프로세스를 모니터링하는 추가 방법은 이 페이지](../../production/using/monitoring-guidelines.md)에 나와 있습니다.[

### 로그 저널 {#log-journal}

프로세스와 관련된 로그 저널을 표시할 수 있습니다. 이렇게 하려면 프로세스 **mta**&#x200B;를 클릭한 다음 **[!UICONTROL Open the log journal]** 를 클릭합니다.

![](assets/d_ncs_monitoring2.png)

### 시스템 표시기 {#system-indicators}

시스템 표시기 목록을 사용하면 물리적 및 가상 메모리, 활성 프로세스, 사용 가능한 디스크 공간 등 컴퓨터에 대한 정보를 표시할 수 있습니다. Linux 및 Windows 운영 체제에는 지표가 다릅니다. **[!UICONTROL Instance Monitoring]** 페이지로 이동하고 **[!UICONTROL Display]** 링크를 클릭하여 표시기 목록을 엽니다

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]** : 메시지  **센터용 표시기**. 자세한 내용은 [이 섹션](../../message-center/using/additional-configurations.md#monitoring-thresholds)을 참조하십시오.

* **[!UICONTROL Memory]** : 실제 메모리(RAM)에 대한 정보입니다.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 설치된 총 메모리 양.

   **[!UICONTROL Available]** : 사용 가능한 메모리 양.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 전체 용량의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 사용량이 전체 용량의 90%에 도달하면 표시됩니다.

   **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 Adobe Campaign 서버가 설치된 컴퓨터에 RAM을 추가하여 문제를 해결할 수 있습니다. 전용 컴퓨터에 Adobe Campaign 서버를 설치하기로 결정할 수도 있습니다.

* **[!UICONTROL Swap Memory]** : 페이징 파일과 일치하는 가상 메모리와 관련된 정보: Windows에서 RAM처럼 사용하는 하드 디스크의 영역입니다.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 총 메모리 양.

   **[!UICONTROL Available]** : 사용 가능한 메모리 양.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 전체 용량의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 사용량이 전체 용량의 90%에 도달하면 표시됩니다.

   **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 고급 Windows 설정에서 Exchange 파일의 크기를 늘려 문제를 해결할 수 있습니다.

* **[!UICONTROL Disk XXX]** : 컴퓨터 판독기에 대한 정보입니다.

   **[!UICONTROL Current value]** : 실제로 사용되는 디스크 공간입니다.

   **[!UICONTROL Max Value]** : 총 디스크 용량.

   **[!UICONTROL Available]** : 사용 가능한 디스크 공간

   **[!UICONTROL Used]** : 사용된 디스크의 백분율입니다.

   **[!UICONTROL Warning]** : 사용 가능한 디스크 공간이 전체 용량의 80%에 도달하면 이 표시기가 표시됩니다.

   **[!UICONTROL Alert]** : 사용 가능한 디스크 공간이 전체 용량의 90%에 도달하면 이 표시기가 표시됩니다.

* **[!UICONTROL Number of processes too old]** : 이틀 이상 활성화된 Adobe Campaign 프로세스에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 활성화된 프로세스 수

   **[!UICONTROL Max Value]** : 허용된 최대 프로세스 수(1)

   **[!UICONTROL Alert]** : 프로세스 수가 1인 경우 이 표시기가 표시됩니다.

   **[!UICONTROL Alert]** 표시기가 표시되면 관련 프로세스가 SQL 데이터베이스 엔진에 의해 잠겨있거나 무한 루프에 포함되어 있을 수 있습니다. Adobe Campaign에서 제공하는 **watchdog** 프로세스는 매일 모든 프로세스를 자동으로 다시 시작하고 이 문제를 해결할 수 있도록 합니다. 하지만, 여러분은 또한 재시작을 강요하기 위해 관련된 과정을 멈출 수 있습니다.

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]** : 메시지  **센터용 표시기**. 자세한 내용은 [이 섹션](../../message-center/using/additional-configurations.md#monitoring-thresholds)을 참조하십시오.

* **[!UICONTROL Load average (1/5/15 minutes)]** : 부하에 관한 정보, 즉 지난 분, 5분 또는 15분 동안 컴퓨터에서 실행되는 프로세스에 의한 프로세서 사용 속도

   **[!UICONTROL Current value]** : 시스템의 실제 로드.

   **[!UICONTROL Max value]** : 시스템에서 프로세스의 최대 사용 로드

   **[!UICONTROL Warning]** : 이 표시기는 로드가 마지막 분, 5분 또는 15분 동안 허용되는 최대 값의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 로드가 마지막 분, 5분 또는 15분의 최대 승인 값의 90%에 도달하면 표시됩니다.

* **[!UICONTROL Memory]** : 실제 메모리(RAM)에 대한 정보입니다.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 설치된 총 메모리 양.

   **[!UICONTROL Available]** : 사용 가능한 메모리 양.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 전체 용량의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 사용량이 전체 용량의 90%에 도달하면 표시됩니다.

   **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 Adobe Campaign 서버가 설치된 컴퓨터에 RAM을 추가하여 문제를 해결할 수 있습니다. 전용 컴퓨터에 Adobe Campaign 서버를 설치하기로 결정할 수도 있습니다.

* **[!UICONTROL Swap Memory]** : 페이징 파일과 일치하는 가상 메모리와 관련된 정보: Windows에서 RAM처럼 사용하는 하드 디스크의 영역입니다.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 총 메모리 양.

   **[!UICONTROL Available]** : 사용 가능한 메모리 양.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 전체 용량의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 사용량이 전체 용량의 90%에 도달하면 표시됩니다.

   **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 교환 파일의 크기를 늘려서 문제를 해결할 수 있습니다.

* **[!UICONTROL Core Files]** : Adobe Campaign 프로세스 충돌 후 생성된 파일에 대한 정보입니다. 이러한 파일을 통해 충돌 원인을 진단할 수 있습니다.

   **[!UICONTROL Current Value]** : 기존 파일 수.

   **[!UICONTROL Max Value]** : 허용된 최대 파일 수(1)

   **[!UICONTROL Warning]** : 이 표시기는 파일 수가 1에 근접하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 파일 수가 1일 때 표시됩니다.

   충돌로 인해 프로세스가 누락된 경우 프로세스 목록에 빨간색으로 표시되며 Adobe Campaign에서 제공하는 **watchdog** 프로세스에 의해 자동으로 다시 시작됩니다.

* **[!UICONTROL Number of shared memory segments]** : 모든 Adobe Campaign 프로세스에서 공유하는 메모리 세그먼트에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 사용 중인 메모리 세그먼트 수입니다.

   **[!UICONTROL Max Value]** : 허용된 최대 메모리 세그먼트 수(2)

   **[!UICONTROL Warning]** : 메모리 세그먼트 수가 1에 도달하면 이 표시기가 표시됩니다.

   **[!UICONTROL Alert]** : 메모리 세그먼트 수가 2에 도달하면 이 표시기가 표시됩니다.

* **[!UICONTROL Number of processes too old]** : 하루 이상 활성 상태인 프로세스에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 활성화된 프로세스 수

   **[!UICONTROL Max Value]** : 허용된 최대 프로세스 수

   **[!UICONTROL Warning]** : 프로세스 수가 인증된 임계값의 80%에 도달하면 이 표시기가 표시됩니다.

   **[!UICONTROL Alert]** : 프로세스 수가 인증된 임계값의 90%에 도달하면 이 표시기가 표시됩니다.

* **[!UICONTROL File Handles]** : 파일 설명자에 대한 정보(즉, 프로세스당 열린 파일 수)입니다.

   **[!UICONTROL Current value]** : 현재 파일 설명자 수

   **[!UICONTROL Max Value]** : 운영 체제에서 인증한 최대 파일 설명자 수

   **[!UICONTROL Warning]** : 권한이 있는 파일 설명자 수가 80% 임계값에 도달하면 이 표시기가 표시됩니다.

   **[!UICONTROL Alert]** : 권한이 있는 파일 설명자 수가 90% 임계값에 도달하면 이 표시기가 표시됩니다.

* **[!UICONTROL Processes]** : 시스템 프로세스에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 활성화된 프로세스 수

   **[!UICONTROL Max Value]** : 허용된 최대 프로세스 수

   **[!UICONTROL Active Processes]** : 활성 프로세스 수

   **[!UICONTROL Inactive Processes]** : 비활성 프로세스 수.

   **[!UICONTROL Warning]** : 승인된 프로세스 수가 80% 임계값에 도달하면 이 표시기가 표시됩니다.

   **[!UICONTROL Alert]** : 승인된 프로세스 수가 90% 임계값에 도달하면 이 표시기가 표시됩니다.

* **[!UICONTROL Zombie Processes]** : 중지되었지만 여전히 프로세스 식별자(PID)가 있으며 프로세스 테이블에 계속 표시되는 프로세스에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 활성 상태인 좀비 프로세스 수입니다.

   **[!UICONTROL Max Value]** : 최대 권한 부여 좀비 프로세스 수(2)

   **[!UICONTROL Warning]** : 이 표시기는 좀비 프로세스 수가 2에 근접하면 표시됩니다.

   **[!UICONTROL Alert]** 이 표시기는 좀비 프로세스 수가 2에 도달하면 표시됩니다.

#### 사용자 지정된 표시기 {#customized-indicators}

Adobe Campaign을 사용하면 표시기를 사용자 지정할 수 있습니다. 방법은 다음과 같습니다.

1. **.sh** 파일을 만들고 이름을 **[!UICONTROL cust_indicators.sh]** 로 지정합니다.
1. 사용자 지정된 표시기를 이 파일에 추가합니다. 예제:

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   또는

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. **[!UICONTROL usr/local/neolane/nl6]** 폴더에 파일을 넣습니다.

이 파일은 Adobe Campaign에서 호출됩니다.

## SMTP 보고서 {#smtp-reports}

SMTP 배달 모니터링 보고서가 Adobe Campaign 플랫폼에 통합됩니다. 콘솔 또는 웹 액세스를 통해 액세스할 수 있습니다.

이러한 보고서에는 도메인별 SMTP 배달 통계와 SMTP 오류가 표시됩니다.

액세스하려면 운영자에게 관리 권한이 있어야 합니다.

이러한 구성 요소는 **모니터링** > &#39;SMTP 모니터링&#39; 아래에 그룹화됩니다.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* SMTP 모니터링과 관련된 정보는 전자 메일 채널이 활성화된 경우에만 사용할 수 있습니다.
>* **[!UICONTROL SMTP sending statistics]** 은 통계 서버가 인스턴스에서 시작된 경우에만 제공됩니다.

>


### SMTP 전송 통계 {#smtp-sending-statistics}

**[!UICONTROL SMTP sending statistics]** 보고서를 사용하면 서버 활동을 제어할 수 있습니다. 각각의 매칭 합성을 표시합니다.

![](assets/smtp_stats_report.png)

이 보고서의 지표 목록은 차트 아래에 나와 있습니다.

1. 보낸 총 메시지 수입니다.
1. 
   * 파란색 선: SMTP를 보내기 전 마지막 단계(들어오는 데이터와 일치함)와 같이 Shaper에 도착한 메시지를 보낼 준비가 되었습니다.

   * 녹색 선: 메시지를 성공적으로 보냈습니다(보내는 데이터와 일치함).

   * 빨간색 선: Shaper에 의해 중단된 메시지가 **mta**&#x200B;로 반환됩니다(이 복구에서 거부된 데이터와 일치함).

   이러한 값은 시간당 메시지 수로 표시됩니다.

1. Shaper의 두 대기열을 나타냅니다.

   * 파란색 곡선: 활성 메시지 큐. 이러한 메시지는 가능한 한 빨리 전송됩니다.

   * 키 곡선: &#39;지연된&#39; 큐. 전송률 조절 때문에 또는 대상에 대한 연결을 사용할 수 없으므로 잠시 동안 이러한 메시지를 반환할 수 없습니다. 다시 시도는 5초, 10초, 20초, 40초, 2분 등에 발생합니다. **MaxAgeSec** 시간을 지정한 후 작업을 중단합니다.

1. 이 차트는 중단된 메시지(두 번째 차트의 빨간색 곡선)의 세부 정보를 보여줍니다. 다시 시도 없이 중단된 메시지(마우브)의 비율을 보내지 못한 메시지(빨간색)와 비교하여 보여줍니다. 따라서 통계 서버의 제한(제한) 또는 원격 서버의 비가용성 때문에 주어진 기간 내에 처리되지 않은 메시지의 비율을 볼 수 있습니다.
1. SMTP 연결이 열려 있거나 열려 있습니다.
1. **mtachild** 개수의 예상

>[!NOTE]
>
>이 보고서는 이메일 트래픽 맵 구성 요소의 상태와 관련되어 있습니다.

### 도메인당 SMTP 오류 {#smtp-errors-per-domain}

이 보고서를 사용하면 설정된 기간 동안 도메인별로 분류된 게재 오류를 볼 수 있습니다.

>[!NOTE]
>
>**serverConf.xml** 파일의 **minConnectionsToLog**, **minErrorsToLog** 및 **minMessagesToLog** 옵션은 연결 통계를 고려하는 위의 임계값을 정의합니다.

![](assets/smtp_error_report.png)

이 보고서의 지표 목록은 표 아래에 나와 있습니다.

* **도메인** 열에는 메시지가 전송될 도메인의 이름(예: yahoo.com의 경우 실제 도메인 이름)이 포함되어 있습니다.
* **Cnx** 열에는 이 도메인에 대해 열려 있는 SMTP 연결 수가 표시됩니다.
* **Sent** 열은 이 도메인에 전송된 메시지 수에 해당합니다.
* **볼륨** 열에는 이 도메인으로 전송하려고 시도한 메시지의 볼륨이 표시됩니다(대략적인 값).
* **오류** 열에는 해당 기간 동안 이 도메인에 대한 오류의 볼륨 표시기가 표시됩니다.
* **마지막 응답** 열에는 이 도메인에 대해 받은 마지막 SMTP 응답 메시지가 표시됩니다.
* **날짜** 열에는 이 도메인에 대해 받은 마지막 SMTP 응답 날짜가 표시됩니다.

>[!NOTE]
>
>**Cnx**, **Sent** 및 **Volume** 열에 표시되는 값은 **[!UICONTROL Period]** 필드에서 선택한 기간에 대해 계산됩니다.

오류를 보려면 도메인 이름을 클릭합니다.

PublicId로 분류됩니다. 이 식별자는 라우터 뒤에 있는 여러 Adobe Campaign 태그가 공유하는 IP 주소에 해당합니다. 통계 서버는 이 식별자를 사용하여 이 시작점과 대상 서버 사이의 연결 및 전달 통계를 암기합니다.

![](assets/smtp_error_report_details.png)

**[!UICONTROL Owner of domain]** 필드를 사용하면 동일한 레이블 아래에 다양한 도메인 이름을 그룹화할 수 있습니다. 초기 보고서 보기에서 모든 MX 도메인 이름이 이 소유자와 연결됩니다.

자세한 내용을 보려면 PublicId 식별자를 클릭합니다.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>오류 비율은 두 개의 차트로 표시됩니다. 첫 번째는 검정색 배경에 있는 가로 진행률 표시줄입니다. 두 번째 차트는 시간 단위입니다. 선택한 기간은 12개의 시간 간격으로 구분되며 각각 세로 진행률 표시줄로 표시됩니다. 두 표현 모두에서 오류가 감지되지 않으면 막대가 검정색으로 표시됩니다. 막대의 색상은 발생한 오류 비율(노란색, 주황색, 마지막, 빨간색)에 따라 달라집니다. 회색은 중요한 데이터 볼륨을 찾을 수 없음을 의미합니다. 차트에 커서를 올려 정확한 오류 백분율을 표시할 수 있습니다.

>[!NOTE]
>
>SMTP 오류 및 Adobe Campaign에서 관리하는 방법에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md)을 참조하십시오.

## 청구 보고서 {#billing-report}

**[!UICONTROL Billing]** 기술 워크플로우는 &#39;청구&#39; 운영자에게 이메일로 시스템 활동 보고서를 보냅니다. 마케팅 인스턴스에서 매월 25일에 기본적으로 트리거됩니다.

기술 워크플로우는 다음 노드의 하위 폴더에서 찾을 수 있습니다. **관리** > **프로덕션** > **기술 워크플로우**

![](assets/billing.png)

매월 25일마다 워크플로우가 시작되면, 청구 운영자는 다음 보고서를 받은 편지함에서 받게 됩니다.

![](assets/billing_2.png)

다음 지표를 사용하여 게재를 추적할 수 있습니다.

* **[!UICONTROL Start date]** : 게재 시작 날짜입니다. 보고서의 &quot;보낸 사람&quot; 날짜보다 빨라질 수 있습니다.
* **[!UICONTROL Label]** : 게재의 레이블입니다. 전송할 메시지가 100개 미만인 게재는 너무 작은 것으로 간주되므로 시작 날짜별로 집계됩니다. 이 경우 레이블에 집계 수가 표시됩니다(예: ). [3개의 작은 게재 집계].
* **[!UICONTROL Total volume]** : 게재에 대해 전송된 총 바이트 수입니다.
* **[!UICONTROL Avg volume]** : 전송된 평균 바이트 볼륨. **[!UICONTROL Multiplier]** 지표의 계산 기반인 수식 **(total volume / messages)**&#x200B;의 결과입니다.
* **[!UICONTROL Messages]** : 보낸 메시지 수입니다. 여기에는 성공적으로 전송된 메시지와 다시 시도(연결된 서버에서 바운스 메시지를 받은 후)가 모두 포함됩니다.
* **[!UICONTROL Multiplier (x)]** : 승수의 값은 메시지의 평균 볼륨으로부터 추론됩니다.
* **[!UICONTROL Count]** : 메시지와 승수의 곱하기 결과.

## 자동 모니터링 {#automatic-monitoring}

Adobe Campaign에서는 다음과 같은 몇 가지 자동 모니터링 방법을 제공합니다.

### 명령줄 {#command-line}

명령

**nlserver 모니터**

Adobe Campaign 모듈 및 시스템에 대한 지표 세트를 나열할 수 있습니다.

쉽게 처리된 XML 형식으로 출력을 생성합니다.

이 명령은 **-missing** 매개 변수를 사용하여 실행할 수도 있습니다. 이 매개 변수에는 구성 파일이 실행해야 한다고 말할 때 이 인스턴스에서 누락된 프로세스가 나열됩니다.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### 서버에서 게시한 정보 {#information-published-by-the-server}

#### /r/test {#r-test}

**http(s)://`<application>`/r/test** 페이지는 리디렉션 서버를 테스트하는 데 사용됩니다. 이와 동일한 방법을 사용하여 추적에 사용되는 전방 서버를 테스트하는 것이 좋습니다. 이 페이지를 사용하여 로드 디스패처를 테스트할 수도 있습니다.

다음과 같은 행을 XML 형식으로 표시합니다.

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**빈도**: 이 테스트는 로드를 사용하지 않으므로 매우 자주(예: 매 초마다 한 번) 실행할 수 있습니다.

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

이 **http(s)://`<Application server url>`/nl/jsp/ping.jsp** 페이지는 해당 네트워크 상대와 동일한 방식으로 작동합니다. apache/tomcat/web module/database를 통해 클라이언트에 업로드하는 전체 쿼리를 테스트합니다. 모든 것이 제대로 작동하면 &quot;OK&quot;가 반환됩니다. 데이터베이스(예: mtas 및 설문 조사)에 액세스할 수 있는 시스템에서 이 테스트를 실행하는 것이 좋습니다.

**사용**: 원격으로 로그인하려면 연산자 로그인과 연결된 세션 토큰을 인수로 전달해야 합니다(Adobe Campaign 스크립트를 통한  [자동 모니터링의 팁](#automatic-monitoring-via-adobe-campaign-scripts) 참조).

예제:

![](assets/ncs_monitoring_ping.png)

운영자 이름 및 로그인은 데이터베이스 권한이 있는 Adobe Campaign 클라이언트 콘솔에서 이전에 구성해야 합니다.

![](assets/ncs_operators_rights_01.png)

**빈도**: 이 테스트는 아주 적은 대역폭을 사용합니다. 따라서 1분에 한 번 이상 실행되는 경우가 거의 없습니다.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

이 테스트는 운영자가 웹 페이지를 통해 Adobe Campaign 서버에 액세스할 수 있는지 확인하는 테스트입니다. 클라이언트 콘솔 메뉴를 통해 액세스한 웹 페이지와 동일합니다. 감시 도구(Tivoli, Nagios 등)에서 이 페이지를 호출할 수 있습니다.

![](assets/ncs_monitoring_web.png)

**사용**: 인스턴스에 연결할 수 있는 운영자 로그인과 연결된 세션 토큰은 인수로 사용해야 합니다(Adobe Campaign 스크립트를 통한  [자동 모니터링의 팁](#automatic-monitoring-via-adobe-campaign-scripts) 참조).

적절한 데이터베이스 권한 및 제한 사항을 사용하여 이전에 Adobe Campaign 클라이언트 콘솔에서 운영자 및 해당 로그인을 구성해야 합니다.

**빈도**: 전체 서버 테스트이며 자주 실행할 필요가 없습니다(예: 10분마다 한 번씩 수행할 수 있음).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

이 **jsp**&#x200B;는 Adobe Campaign 애플리케이션 API의 시작 지점을 나타냅니다. 따라서 응용 프로그램의 세부 모니터링을 제공할 수 있습니다. Adobe Campaign 웹 서비스를 모니터링하는 데에도 사용할 수 있습니다. 모니터링 스크립트에는 사용되지만 고급 사용자용으로만 사용됩니다.

### 배포 유형 기반 모니터링 {#monitoring-based-on-deployment-types}

Adobe Campaign에서는 다양한 배포 구성을 활성화합니다(자세한 내용은 [이 섹션](../../installation/using/hosting-models.md) 참조). 이 섹션에서는 설치 유형에 따라 적용되는 다양한 자동 모니터링 기술에 대해 자세히 설명합니다.

<table> 
 <thead> 
  <tr> 
   <th> 배포 유형 </th> 
   <th> 모니터링 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 독립형 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/monitor.</span> jspon(Adobe Campaign 서버)</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 표준 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/ping.</span> 정측 서버</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.</span> jspon 애플리케이션 서버</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Enterprise </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/ping.</span> 정측 서버</p> </li> 
     <li><p> <span class="uicontrol">/r/</span> testand  <span class="uicontrol">/nl/jsp/monitor.</span> jspon 애플리케이션 서버</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.</span> jspon 애플리케이션 서버</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Adobe Campaign 스크립트를 통한 자동 모니터링 {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign에서는 감지된 예외 항목에 대한 보고서를 이메일로 전송할 수 있는 인스턴스 모니터링 도구(넷보고서)를 제공할 수 있습니다.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>이 도구는 인스턴스를 모니터링하는 데 사용할 수 있지만 Adobe Campaign에서 지원하지 않습니다. 자세한 내용은 캠페인 관리자에게 문의하십시오.

### 필수 요소 {#required-elements}

자동 모니터링에는 다음과 같은 사전 설치 주의가 필요합니다.

* **netreport.tgz**(Linux 설치) 또는 **netreport.zip**(Windows 설치) 파일이 있어야 합니다.
* 모니터링하기 위해 컴퓨터에 모니터링을 설치하지 않는 것이 좋습니다.
* JRE 또는 JDK가 설치된 컴퓨터에 설치해야 합니다.
* Linux에서 모니터링할 컴퓨터에 **bc** 패키지가 있어야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages)을 참조하십시오.

### 설치 절차 {#installation-procedure}

설치 절차는 다음과 같습니다.

1. 필요한 경우 콘솔에서 새 연산자(&#39;모니터링&#39; 사용자가 이미 있음)를 만들지만 권한을 할당하지는 않습니다.
1. 아카이브 추출을 실행합니다.
1. **readme** 파일을 읽습니다.
1. **netconf.xml** 구성 파일을 업데이트합니다.
1. **netreport.bat**(Windows) 또는 **netreport.sh**(Linux) 파일을 업데이트합니다.

### netconf.xml 파일 구성 {#configuring-the-netconf-xml-file}

XML 구성 파일에는 다음 요소가 포함됩니다.

* [&#39;Properties&#39; 요소](#properties--element)
* [&#39;Instance&#39; 요소](#instance--element)
* [&#39;호스트&#39; 요소](#host--element)
* [하위 요소](#sub-elements)

다음은 구성 예입니다.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>**netconf.xml** 파일에 접미사를 추가하여 다양한 구성을 지정할 수 있습니다(예: **netconf-dev.xml**, **netconf-prod.xml** 등). 그런 다음 **$JAVA_HOME/bin/java netreport** 또는 **@%JAVA_HOME%binjnetreport prod**&#x200B;를 추가하여 **netreport.bat** 또는 **netreport.sh** 파일에서 netreport를 실행하는 데 사용할 구성을 지정합니다.

>[!IMPORTANT]
>
>**모니터링** 연산자가 작동하려면 netreport가 실행되는 컴퓨터가 **sessionTokenOnly** 모드에 있는 보안 영역에 있어야 합니다. 이 연산자에 대해 신뢰할 수 있는 IP 마스크를 지정하지 않은 경우 보안 영역도 **allowEmptyPassword** 및 **allowUserPassword** 모드여야 합니다.

#### &#39;Properties&#39; 요소 {#properties--element}

이 요소는 이메일 구성을 채우는 데 사용됩니다(예:

* **mailServer**: 전자 메일을 보내는 데 사용되는 SMTP 서버(예: smtp.domain.net).
* **mailFrom**: 보고서 발신자의 이메일 주소(예: monitoring@domain.net).
* **recipientList**: 모니터링 수신자의 이메일 주소 목록입니다. 주소는 쉼표(공백 없음)로 구분해야 합니다.
* &#39;**night**&#39; 모드(선택 사항)는 지정된 기간 사이에 전자 메일을 보내지 않도록 하는 데 사용됩니다. 대신 데이터가 통합되고 종료 시간(기본적으로 7:00) 후에 야간 활동에 대한 이메일이 전송됩니다.
* **buildRange** 하위 요소(선택 사항)를 사용하면 최소 및 최대 빌드 번호를 지정할 수 있습니다. 빌드 번호가 이 범위에 포함되지 않은 모든 컴퓨터에 대해 오류가 생성됩니다

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* **속성** 요소에 **`<sla>`**(선택 사항) 하위 요소를 추가할 수 있습니다. 네트워크 보고서가 실행될 때마다 로그 파일이 생성됩니다. 파일 이름은 구성 이름과 날짜 및 시간(예: **dev_06_12_13_16_47_05.tmp**)을 포함합니다. 파일에는 다음 정보가 포함되어 있습니다. 인스턴스 이름, 시스템 이름, 심각도 수준, (0~3, 가장 중요도에서 가장 중요도에 이르기까지), 날짜(타임스탬프 형식), 쿼리와 응답 사이의 경과 시간(밀리초), 사용된 서비스(http, ncs, ncsex, 리디렉션). 이 정보는 각 서비스 끝에 있는 표 및 줄 바꿈으로 구분됩니다.

>[!NOTE]
>
>**`<property>`** 요소에서 값이 &quot;true&quot;인 **persistHtmlFile** 속성은 **netreport.md** 파일에 최신 모니터링 상태를 기록하는 데 사용됩니다. 이 파일은 설치 디렉토리에 저장됩니다.

#### &#39;Instance&#39; 요소 {#instance--element}

이 요소를 사용하면 여러 시스템(호스트)을 동일한 인스턴스로 다시 그룹화할 수 있습니다. 인스턴스 이름은 모니터링 이메일의 첫 부분에 나타납니다. 인스턴스 이름을 클릭하여 각 컴퓨터에 대한 세부 정보에 액세스할 수 있습니다.

```
instance name="instanceName" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **이름**: 이메일의 첫 부분에 표시되는 인스턴스 이름입니다.
* **recipientList** (선택 사항): 을(를) 통해 특정 인스턴스에 대한 모니터링 보고서를 이메일로 보낼 수 있습니다.

#### &#39;호스트&#39; 요소 {#host--element}

이 요소는 호스트에 지정된 서버(예:

* **이름**: 모니터링할 시스템의 이름입니다.
* **별칭** (선택 사항): 보고서에 표시될 모니터된 컴퓨터의 이름입니다.
* **sessionToken**: 인증된 세션 토큰을 통해 로그인 인증을 제공합니다.

   세션 토큰을 구성하려면 Adobe Campaign 콘솔에서 **모니터링** 연산자를 선택합니다. **액세스 권한** 탭에서 이 인스턴스를 모니터링할 권한이 있는 컴퓨터의 IP 주소를 지정합니다. 그런 다음 **모니터링** 식별자를 사용하여 암호를 지정하지 않고도 해당 시스템에서 모니터링 페이지에 연결할 수 있습니다.

   ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** (선택 사항): 심각도 수준별로 표시할 오류를 정렬할 수 있습니다. 가능한 값은 &#39;0&#39;(모든 레벨이 표시됨), &#39;1&#39;(높음 및 중요 오류만 표시됨) 및 &#39;2&#39;(위험 오류만 표시됨)입니다. 이 속성을 제공하지 않으면 모든 오류 수준이 표시됩니다.
* **필터** (선택 사항): filter=&quot;wkf;wkf1&quot; ****&#x200B;과 같은 특정 워크플로우 오류를 제외할 수 있습니다. 워크플로우 레이블은 세미콜론으로 구분해야 합니다.

#### 하위 요소 {#sub-elements}

* **tcp**: 서버가 작동 중인지 확인합니다. 포트 번호를 입력해야 합니다.
* **http**: 웹 서버가 있는지 확인합니다(응용 프로그램 서버가 작동 중임).
* **ncs**: &#39;instance&#39; 속성에 입력된 인스턴스의 프로세스(워크플로우 오류, 메모리 사용 등)를 확인합니다. **included** (필수) 속성은 데드 프로세스(&#39;true&#39; 또는 &#39;false&#39; 값)를 표시하는 옵션을 제공합니다.
* **리디렉션**: 추적을 확인합니다.

대부분의 경우 **ncs** 및 **리디렉션** 하위 요소만 유지할 수 있습니다.

어떤 경우든 하위 요소(예: **port=75** 노드)에서 특정 노드를 오버로드하여 http, ncs 또는 리디렉션 연결에 사용되는 포트를 오버로드할 수 있습니다.

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

**ncs**, **리디렉션** 및 **http** 하위 요소에서 **isSecure** 속성(선택 사항)을 추가하여 https 프로토콜(&#39;true&#39; 또는 &#39;false&#39; 값)을 사용할지 여부를 선택할 수 있습니다. 이 속성을 제공하지 않으면 http 프로토콜이 사용됩니다.

### netreport.bat 또는 netreport.sh 파일 구성 {#configuring-the-netreport-bat-or-netreport-sh--file}

이 파일을 구성하려면 이 파일을 편집하고 JRE 또는 JDK가 설치된 디렉토리를 지정합니다.

### 모니터링 시작 {#launching-monitoring}

모니터링을 시작하려면 스크립트를 통해 정기적으로 **netreport.bat** 또는 **netreport.sh** 파일을 실행합니다. 보고서는 첫 번째 실행 후 전송되고 상태가 변경된 경우에만 전송됩니다.

### 모니터링 테스트 {#testing-monitoring}

모니터링을 테스트하려면 **netreport.bat** 또는 **netreport.sh** 파일을 실행합니다.

**netconf.xml** 파일의 **recipientList**&#x200B;에 지정된 수신자에게 전자 메일이 전송됩니다.
