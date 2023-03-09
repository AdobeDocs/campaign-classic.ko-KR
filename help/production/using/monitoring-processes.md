---
product: campaign
title: 프로세스 모니터링
description: Campaign 프로세스를 모니터링하는 방법 알아보기
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: f2ec24a122eff94f62bd79e656e771fecd803659
workflow-type: tm+mt
source-wordcount: '3610'
ht-degree: 0%

---

# 프로세스 모니터링{#monitoring-processes}

![](../../assets/v7-only.svg)

애플리케이션 서버 및 리디렉션 서버(**추적**)은 수동 또는 자동으로 모니터링할 수 있습니다.

## 수동 모니터링 {#manual-monitoring}

다음으로 이동 **[!UICONTROL Monitoring]** 을(를) 클릭하고 **[!UICONTROL Overview]** Adobe Campaign 프로세스 모니터링 페이지를 표시하는 링크입니다.

![](assets/d_ncs_monitoring.png)

표시된 페이지에서는 연결된 인스턴스의 상태를 확인할 수 있습니다(예:

* 인스턴스에 대한 정보: 버전, 이름, 데이터베이스 엔진, 설치된 패키지, 서버 시스템 표시기
* 누락된 프로세스 및 실행 정보 목록(시작 날짜, PID 등),
* 워크플로우 및 게재 보기.

다양한 Campaign 프로세스를 모니터링하는 추가 방법이에 나와 있습니다. [이 페이지](../../production/using/monitoring-guidelines.md).

### 로그 저널 {#log-journal}

프로세스와 관련된 로그 저널을 표시할 수 있습니다. 이렇게 하려면 프로세스를 클릭하고 **mta** 예를 들어 를 클릭한 다음 **[!UICONTROL Open the log journal]** .

![](assets/d_ncs_monitoring2.png)

### 시스템 지표 {#system-indicators}

시스템 표시기 목록을 사용하면 물리적 및 가상 메모리, 활성 프로세스 및 사용 가능한 디스크 공간 등 시스템에 대한 정보를 표시할 수 있습니다. Linux 및 Windows 운영 체제에서는 표시기가 다릅니다. 로 이동 **[!UICONTROL Instance Monitoring]** 페이지를 클릭하고 **[!UICONTROL Display]** 표시기 목록을 여는 링크

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]** : 관련 표시기 **메시지 센터**. 을(를) 참조하십시오 [이 섹션](../../message-center/using/additional-configurations.md#monitoring-thresholds) 추가 정보.

* **[!UICONTROL Memory]** : 물리적 메모리(RAM)에 대한 정보.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 설치된 총 메모리 양입니다.

   **[!UICONTROL Available]** : 사용 가능한 메모리의 양입니다.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 총 양의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 소비가 총 양의 90%에 도달하면 표시됩니다.

   다음의 경우 **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 Adobe Campaign 서버가 설치된 시스템에 RAM을 추가하여 문제를 해결할 수 있습니다. 전용 컴퓨터에 Adobe Campaign 서버를 설치하도록 결정할 수도 있습니다.

* **[!UICONTROL Swap Memory]** : 페이징 파일과 일치하는 가상 메모리 관련 정보: Windows에서 RAM인 것처럼 사용하는 하드 디스크의 영역입니다.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 총 메모리 양입니다.

   **[!UICONTROL Available]** : 사용 가능한 메모리의 양입니다.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 총 양의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 소비가 총 양의 90%에 도달하면 표시됩니다.

   다음의 경우 **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 고급 Windows 설정에서 exchange 파일 크기를 늘려 문제를 해결할 수 있습니다.

* **[!UICONTROL Disk XXX]** : 기계 판독기에 관한 정보

   **[!UICONTROL Current value]** : 실제로 사용된 디스크 공간

   **[!UICONTROL Max Value]** : 총 디스크 용량

   **[!UICONTROL Available]** : 사용 가능한 디스크 공간

   **[!UICONTROL Used]** : 사용된 디스크의 백분율입니다.

   **[!UICONTROL Warning]** : 이 표시기는 사용 가능한 디스크 공간이 총 용량의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 사용 가능한 디스크 공간이 총 용량의 90%에 도달하면 표시됩니다.

* **[!UICONTROL Number of processes too old]** : 하루 이상 활성 상태인 Adobe Campaign 프로세스에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 활성 상태인 프로세스의 수입니다.

   **[!UICONTROL Max Value]** : 인증된 최대 프로세스 수(1).

   **[!UICONTROL Alert]** : 이 표시기는 프로세스 수가 1인 경우에 표시됩니다.

   다음의 경우 **[!UICONTROL Alert]** 관련 프로세스가 SQL 데이터베이스 엔진에 의해 잠기거나 무한 루프에 갇혀 있다는 표시기가 표시됩니다. 다음 **감시** Adobe Campaign에서 제공한 프로세스를 매일 자동으로 모든 프로세스가 다시 시작되며 이 문제를 해결할 수 있습니다. 그러나 직접 관련 프로세스를 중지하여 강제로 다시 시작할 수도 있습니다.

#### 리눅스 {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]** : 관련 표시기 **메시지 센터**. 을(를) 참조하십시오 [이 섹션](../../message-center/using/additional-configurations.md#monitoring-thresholds) 추가 정보.

* **[!UICONTROL Load average (1/5/15 minutes)]** : 지난 1분, 5분 또는 15분 동안 시스템에서 실행되는 프로세스에 의한 프로세서 사용률 등 로드에 관한 정보

   **[!UICONTROL Current value]** : 컴퓨터의 실제 로드.

   **[!UICONTROL Max value]** : 시스템에서 프로세스의 최대 사용 로드

   **[!UICONTROL Warning]** : 이 표시기는 마지막 1분, 5분 또는 15분 동안 로드가 최대 인증 값의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 마지막 분, 5분 또는 15분 동안 최대 인증 값의 90%에 로드가 도달하면 표시됩니다.

* **[!UICONTROL Memory]** : 물리적 메모리(RAM)에 대한 정보.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 설치된 총 메모리 양입니다.

   **[!UICONTROL Available]** : 사용 가능한 메모리의 양입니다.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 총 양의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 소비가 총 양의 90%에 도달하면 표시됩니다.

   다음의 경우 **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 Adobe Campaign 서버가 설치된 시스템에 RAM을 추가하여 문제를 해결할 수 있습니다. 전용 컴퓨터에 Adobe Campaign 서버를 설치하도록 결정할 수도 있습니다.

* **[!UICONTROL Swap Memory]** : 페이징 파일과 일치하는 가상 메모리 관련 정보: Windows에서 RAM인 것처럼 사용하는 하드 디스크의 영역입니다.

   **[!UICONTROL Current value]** : 실제 메모리 사용량.

   **[!UICONTROL Max Value]** : 총 메모리 양입니다.

   **[!UICONTROL Available]** : 사용 가능한 메모리의 양입니다.

   **[!UICONTROL Warning]** : 이 표시기는 메모리 사용량이 총 양의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 소비가 총 양의 90%에 도달하면 표시됩니다.

   다음의 경우 **[!UICONTROL Warning]** 및 **[!UICONTROL Alert]** 표시기가 표시되면 exchange 파일 크기를 늘려 문제를 해결할 수 있습니다.

* **[!UICONTROL Core Files]** : Adobe Campaign 프로세스 충돌 후 생성된 파일에 대한 정보입니다. 이러한 파일을 사용하면 충돌 원인을 진단할 수 있습니다.

   **[!UICONTROL Current Value]** : 기존 파일 수.

   **[!UICONTROL Max Value]** : 권한이 부여된 최대 파일 수 (1).

   **[!UICONTROL Warning]** : 이 표시기는 파일 수가 1에 가까워지면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 파일 수가 1일 때 표시됩니다.

   충돌로 인해 프로세스가 누락된 경우 프로세스 목록에 빨간색으로 표시되며 **감시** Adobe Campaign에서 제공한 프로세스입니다.

* **[!UICONTROL Number of shared memory segments]** : 모든 Adobe Campaign 프로세스에서 공유하는 메모리 세그먼트에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 사용 중인 메모리 세그먼트 수입니다.

   **[!UICONTROL Max Value]** : 권한이 부여된 최대 메모리 세그먼트 수 (2).

   **[!UICONTROL Warning]** : 이 표시기는 메모리 세그먼트 수가 1에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 메모리 세그먼트 수가 2개에 도달하면 표시됩니다.

* **[!UICONTROL Number of processes too old]** : 하루 이상 활성 상태인 프로세스에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 활성 상태인 프로세스의 수입니다.

   **[!UICONTROL Max Value]** : 인증된 최대 프로세스 수.

   **[!UICONTROL Warning]** : 이 표시기는 프로세스 수가 승인된 임계값의 80%에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 프로세스 수가 승인된 임계값의 90%에 도달하면 표시됩니다.

* **[!UICONTROL File Handles]** : 파일 설명자에 대한 정보(예: 프로세스당 열린 파일 수)

   **[!UICONTROL Current value]** : 현재 파일 설명자 수입니다.

   **[!UICONTROL Max Value]** : 운영 체제에서 승인된 최대 파일 설명자 수입니다.

   **[!UICONTROL Warning]** : 이 표시기는 승인된 파일 설명자의 수가 80% 임계값에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 승인된 파일 설명자의 수가 90% 임계값에 도달하면 표시됩니다.

* **[!UICONTROL Processes]** : 기계 공정에 관한 정보.

   **[!UICONTROL Current value]** : 현재 활성 상태인 프로세스의 수입니다.

   **[!UICONTROL Max Value]** : 인증된 최대 프로세스 수.

   **[!UICONTROL Active Processes]** : 활성 프로세스 수

   **[!UICONTROL Inactive Processes]** : 비활성 프로세스 수

   **[!UICONTROL Warning]** : 이 표시기는 승인된 프로세스의 수가 80% 임계값에 도달하면 표시됩니다.

   **[!UICONTROL Alert]** : 이 표시기는 승인된 프로세스의 수가 90% 임계값에 도달하면 표시됩니다.

* **[!UICONTROL Zombie Processes]** : 중단되었지만 PID(프로세스 식별자)가 있으며 프로세스 테이블에 계속 표시되는 프로세스에 대한 정보입니다.

   **[!UICONTROL Current value]** : 현재 활성화된 좀비 프로세스 수.

   **[!UICONTROL Max Value]** : 최대 좀비 프로세스 승인 수 (2).

   **[!UICONTROL Warning]** : 이 표시기는 좀비 프로세스 수가 2에 가까워지면 표시됩니다.

   **[!UICONTROL Alert]** 이 표시기는 좀비 프로세스 수가 2개에 도달하면 표시됩니다.

#### 맞춤화된 지표 {#customized-indicators}

Adobe Campaign을 사용하면 지표를 사용자 지정할 수 있습니다. 방법은 다음과 같습니다.

1. 만들기 **.sh** 파일 및 이름 지정 **[!UICONTROL cust_indicators.sh]** .
1. 사용자 지정된 지표를 이 파일에 추가합니다. 예제:

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

1. 파일을 **[!UICONTROL usr/local/neolane/nl6]** 폴더를 삭제합니다.

이 파일은 Adobe Campaign에 의해 호출됩니다.

## SMTP 보고서 {#smtp-reports}

SMTP 게재 모니터링 보고서는 Adobe Campaign 플랫폼에 통합됩니다. 콘솔을 통해 또는 웹 액세스를 사용하여 액세스할 수 있습니다.

이러한 보고서에는 도메인별 SMTP 게재 통계 및 SMTP 오류가 표시됩니다.

액세스하려면 운영자에게 관리 권한이 있어야 합니다.

아래에 그룹화됩니다. **모니터링** > &#39;SMTP 모니터링&#39;.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* SMTP 모니터링 관련 정보는 전자 메일 채널이 활성화된 경우에만 사용할 수 있습니다.
>* 다음 **[!UICONTROL SMTP sending statistics]** 인스턴스에서 통계 서버가 시작된 경우에만 제공됩니다.
>


### SMTP 전송 통계 {#smtp-sending-statistics}

다음 **[!UICONTROL SMTP sending statistics]** 보고서를 사용하면 서버 활동을 제어할 수 있습니다. 각 일정의 합성을 표시합니다.

![](assets/smtp_stats_report.png)

이 보고서에 대한 지표 목록은 차트 아래에 표시됩니다.

1. 보낸 총 메시지 수.
1. 인/아웃 메시지를 나타냅니다.

   * 파란색 선: 셰이퍼(SMTP 전송 전 마지막 단계)에 도착한 전송 준비 메시지(수신 데이터와 일치).

   * 녹색 줄: 성공적으로 보낸 메시지(보내는 데이터와 일치).

   * 빨간색 라인: 셰이퍼가 포기한 메시지가 (으)로 반환됨 **mta** (이 복구에서 거부된 데이터와 일치함).

   이 값은 시간당 메시지 수로 표시됩니다.

1. 셰이퍼의 두 대기열을 나타냅니다.

   * 파란색 곡선: 활성 메시지 큐. 이 메시지는 가능한 한 빨리 전송됩니다.

   * 카키 곡선: &#39;지연된&#39; 큐. 조절이나 타겟에 연결할 수 없기 때문에 이러한 메시지는 즉시 반환할 수 없습니다. 5초, 10초, 20초, 40초, 2분 간격으로 다시 시도합니다. ( 정의된 경우) **최대 수명 초** 버리기 전 시간입니다.

1. 이 차트에서는 중단된 메시지의 세부 정보(두 번째 차트의 빨간색 곡선)를 보여 줍니다. 다시 시도 없이 중단된 메시지의 비율(무브)을 전송이 실패한 메시지(빨간색)와 비교하여 보여 줍니다. 이렇게 하면 통계 서버의 제한(제한) 또는 원격 서버를 사용할 수 없기 때문에 허용된 기간 내에 처리되지 않은 메시지의 비율을 볼 수 있습니다.
1. SMTP 연결이 열려 있거나 열려 있습니다.
1. 예상 개수 **일치 항목**.

>[!NOTE]
>
>이 보고서는 전자 메일 트래픽 셰이퍼 구성 요소의 상태와 관련이 있습니다.

### 도메인당 SMTP 오류 {#smtp-errors-per-domain}

이 보고서를 사용하면 지정된 기간 동안 도메인별로 분류된 게재 오류를 볼 수 있습니다.

>[!NOTE]
>
>다음 **minConnectionsToLog**, **minErrorsToLog** 및 **minMessageToLog** 옵션 **serverConf.xml** 파일 은 연결 통계를 고려하는 임계값을 정의합니다.

![](assets/smtp_error_report.png)

이 보고서에 대한 지표 목록은 표 아래에 나와 있습니다.

* 다음 **도메인** 열에는 메시지가 전송되는 도메인의 이름(또는 실제 도메인 이름, yahoo.fr의 경우 yahoo.com)이 포함되어 있습니다.
* 다음 **Cnx** 열에는 이 도메인에 대해 열려 있는 SMTP 연결 수가 표시됩니다.
* 다음 **전송됨** 열은 이 도메인으로 보낸 메시지 수에 해당합니다.
* 다음 **볼륨** 열에는 이 도메인으로 전송하려고 한 메시지의 양(근사값)이 표시됩니다.
* 다음 **오류** 열에는 해당 기간 동안 이 도메인의 오류에 대한 볼륨 표시기가 표시됩니다.
* 다음 **마지막 응답** 열에는 이 도메인에 대해 받은 마지막 SMTP 응답 메시지가 표시됩니다.
* 다음 **날짜** 열에는 이 도메인에 대해 마지막으로 받은 SMTP 응답의 날짜가 표시됩니다.

>[!NOTE]
>
>에 표시되는 값 **Cnx**, **전송됨**, 및 **볼륨** 열은에서 선택한 기간을 기준으로 계산됩니다. **[!UICONTROL Period]** 필드.

도메인 이름을 클릭하여 오류를 확인합니다.

PublicId로 분류됩니다. 이 식별자는 라우터 뒤에서 여러 Adobe Campaign mta가 공유하는 IP 주소에 해당합니다. 통계 서버는 이 식별자를 사용하여 이 시작점과 대상 서버 사이의 연결 및 전달 통계를 기억한다.

![](assets/smtp_error_report_details.png)

다음 **[!UICONTROL Owner of domain]** 필드를 사용하면 여러 도메인 이름을 동일한 레이블 아래에 그룹화할 수 있습니다. 초기 보고서 보기에서 모든 MX 도메인 이름이 이 소유자에 연결됩니다.

자세한 내용을 보려면 PublicId 식별자를 클릭하십시오.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>오류 비율은 두 개의 차트로 표시됩니다. 첫 번째는 검정색 배경에 있는 가로 진행률 표시줄입니다. 두 번째 차트는 연대순입니다. 선택된 기간은 12개의 시간 간격으로 나누어지며, 각각 수직 진행률 막대로 표현된다. 두 표현 모두에서 오류가 감지되지 않으면 막대는 검정색입니다. 막대의 색상은 발생한 오류의 비율에 따라 달라집니다(노란색, 주황색, 마지막 빨간색). 색상이 회색이면 중요한 데이터 볼륨이 없음을 의미합니다. 차트 위에 커서를 놓으면 정확한 오류 비율을 표시할 수 있습니다.

>[!NOTE]
>
>SMTP 오류 및 Adobe Campaign 관리에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](../../installation/using/email-deliverability.md).

## 과금 보고서 {#billing-report}

다음 **[!UICONTROL Billing]** 기술 워크플로우에서는 &#39;과금&#39; 운영자에게 이메일로 시스템 활동 보고서를 보냅니다. 기본적으로 마케팅 인스턴스에서 매월 25일에 트리거됩니다.

기술 워크플로우는 다음 노드의 하위 폴더에서 찾을 수 있습니다. **관리** > **프로덕션** > **기술 워크플로우**.

![](assets/billing.png)

워크플로우가 매월 25일에 시작되면 청구 운영자는 받은 편지함에 다음 보고서를 받게 됩니다.

![](assets/billing_2.png)

게재를 추적하는 데 다음 지표를 사용할 수 있습니다.

* **[!UICONTROL Start date]** : 게재 시작일. 보고서의 &quot;시작&quot; 날짜보다 빠를 수 있습니다.
* **[!UICONTROL Label]** : 게재 레이블. 전송할 메시지가 100개 미만인 게재는 너무 적어 시작 날짜별로 집계됩니다. 이 경우 레이블에는 합계 수가 표시됩니다(예: ). [3개의 작은 게재 집계].
* **[!UICONTROL Total volume]** : 전송을 위해 전송된 총 바이트 볼륨입니다.
* **[!UICONTROL Avg volume]** : 전송된 평균 바이트 볼륨입니다. 이는 다음 수식의 결과입니다 **(총 볼륨 / 메시지 수)**, 이는 의 계산 기준입니다. **[!UICONTROL Multiplier]** 지표.
* **[!UICONTROL Messages]** : 보낸 메시지 수 여기에는 성공적으로 전송된 메시지와 (접속된 서버에서 바운스 메시지를 수신한 후) 재시도 메시지가 모두 포함됩니다.
* **[!UICONTROL Multiplier (x)]** : 승수의 값은 메시지의 평균 볼륨에서 추론됩니다.
* **[!UICONTROL Count]** : 메시지 곱하기 및 곱하기 결과입니다.

## 자동 모니터링 {#automatic-monitoring}

Adobe Campaign은 아래에 나와 있는 몇 가지 자동 모니터링 방법을 제공합니다.

### 명령줄 {#command-line}

명령

**nlserver 모니터**

Adobe Campaign 모듈 및 시스템에 지표 세트를 나열할 수 있습니다.

쉽게 처리되는 XML 형식으로 출력을 생성합니다.

이 명령은 **-missing** 매개 변수 : 구성 파일에서 실행 중임을 알리는 경우 이 인스턴스에서 누락된 프로세스를 나열합니다.

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### 서버에서 게시한 정보 {#information-published-by-the-server}

#### /r/test {#r-test}

다음 **http(s):/`<application>`/r/test** 페이지는 리디렉션 서버를 테스트하는 데 사용됩니다. 추적에 사용되는 전면 서버를 테스트하려면 이와 동일한 방법을 사용하는 것이 좋습니다. 이 페이지는 로드 Dispatcher를 테스트하는 데에도 사용할 수 있습니다.

다음과 같은 선을 XML 형식으로 표시합니다.

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**빈도**: 이 테스트는 부하를 사용하지 않으므로 매우 자주 실행할 수 있습니다(예: 1초에 한 번).

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

이 **http(s):/`<Application server url>`/nl/jsp/ping.jsp**  페이지는 네트워크 대응물과 동일한 방식으로 작동합니다. apache/tomcat/웹 모듈/데이터베이스를 통과하고 클라이언트에 업로드하는 전체 쿼리를 테스트합니다. 모든 것이 제대로 작동하는 경우 &quot;OK&quot;를 반환합니다. 데이터베이스에 액세스할 수 있는 컴퓨터(예: mta 및 설문 조사)에서 이 테스트를 실행하는 것이 좋습니다.

**사용**: 원격으로 로그인하려면 운영자 로그인과 연결된 세션 토큰을 인수로 전달해야 합니다( 팁인 참조) [Adobe Campaign 스크립트를 통한 자동 모니터링](#automatic-monitoring-via-adobe-campaign-scripts)).

예제:

![](assets/ncs_monitoring_ping.png)

운영자 이름 및 로그인은 이전에 데이터베이스 권한을 사용하여 Adobe Campaign 클라이언트 콘솔에 구성해야 합니다.

![](assets/ncs_operators_rights_01.png)

**빈도**: 대역폭을 거의 사용하지 않는 테스트입니다. 따라서 1분에 두 번 이상 실행할 수는 없지만 상당히 자주 실행할 수 있습니다.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

운영자가 클라이언트 콘솔 메뉴를 통해 액세스하는 웹 페이지와 동일한 웹 페이지를 통해 Adobe Campaign 서버에 액세스할 수 있는지 확인하는 테스트입니다. 감시 도구 (Tivoli, Nagios 등)에서 이 페이지를 호출할 수 있습니다.

![](assets/ncs_monitoring_web.png)

**사용**: 인스턴스에 연결할 수 있는 연산자 로그인과 연결된 세션 토큰을 인수로 사용해야 합니다( 의 팁 참조). [Adobe Campaign 스크립트를 통한 자동 모니터링](#automatic-monitoring-via-adobe-campaign-scripts)).

연산자와 해당 로그인은 이전에 Adobe Campaign 클라이언트 콘솔에서 적절한 데이터베이스 권한과 제한을 사용하여 구성해야 합니다.

**빈도**: 전체 서버 테스트이며 자주 실행할 필요가 없습니다(예: 10분에 한 번 수행 가능).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

이 **jsp** Adobe Campaign 애플리케이션 API의 시작 지점을 나타냅니다. 따라서 애플리케이션에 대한 자세한 모니터링을 제공할 수 있습니다. Adobe Campaign 웹 서비스를 모니터링하는 데에도 사용할 수 있습니다. 모니터링 스크립트에서 사용되지만 고급 사용자용으로만 사용됩니다.

### 배포 유형 기반 모니터링 {#monitoring-based-on-deployment-types}

Adobe Campaign은 다양한 배포 구성을 활성화합니다(자세한 내용은 다음을 참조하십시오.) [이 섹션](../../installation/using/hosting-models.md)). 이 섹션에서는 설치 유형에 따라 적용할 다양한 자동 모니터링 기술에 대해 자세히 설명합니다.

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
     <li><p> <span class="uicontrol">/r/test</span> 및 <span class="uicontrol">/nl/jsp/monitor.jsp</span> Adobe Campaign 서버에서</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 표준 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 및 <span class="uicontrol">/nl/jsp/ping.jsp</span> 전면 서버에서</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> 애플리케이션 서버에서</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 엔터프라이즈 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> 및 <span class="uicontrol">/nl/jsp/ping.jsp</span> 전면 서버에서</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> 및 <span class="uicontrol">/nl/jsp/monitor.jsp</span> 애플리케이션 서버에서</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 중간 소싱 </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> 애플리케이션 서버에서</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Adobe Campaign 스크립트를 통한 자동 모니터링 {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign은 감지된 예외 항목과 관련하여 보고서를 이메일로 보낼 수 있는 인스턴스 모니터링 도구(네트워크)를 제공할 수 있습니다.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>이 도구를 사용하여 인스턴스를 모니터링할 수 있지만 Adobe Campaign에서는 지원되지 않습니다. 자세한 내용은 Campaign 관리자에게 문의하십시오.

### 필수 요소 {#required-elements}

자동 모니터링을 위해서는 다음과 같은 사전 설치 주의 사항이 필요합니다.

* 다음을 보유해야 합니다. **netreport.tgz** (Linux 설치) 또는 **netreport.zip** (Windows 설치) 파일,
* 모니터링할 시스템에 모니터링을 설치하지 않는 것이 좋습니다.
* jre 또는 JDK가 설치된 시스템에 설치해야 합니다.
* linux에서 모니터링할 시스템은 **bc** 패키지. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages)을 참조하십시오.

### 설치 절차 {#installation-procedure}

설치 절차는 다음과 같습니다.

1. 필요한 경우 콘솔에서 새 연산자를 만들되(&#39;모니터링&#39; 사용자가 이미 있음), 권한은 할당하지 않습니다.
1. 아카이브 추출 실행
1. 읽기 **readme** 파일.
1. 업데이트 **netconf.xml** 구성 파일입니다.
1. 업데이트 **netreport.bat** (Windows) 또는 **netreport.sh** (Linux) 파일입니다.

### netconf.xml 파일 구성 {#configuring-the-netconf-xml-file}

XML 구성 파일에는 다음 요소가 포함되어 있습니다.

* [&#39;속성&#39; 요소](#properties--element)
* [&#39;인스턴스&#39; 요소](#instance--element)
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
>에 접미사를 추가하여 다양한 구성을 지정할 수 있습니다. **netconf.xml** 파일(예: ) **netconf-dev.xml**, **netconf-prod.xml**&#x200B;등 그런 다음 에서 연결을 실행하는 데 사용할 구성을 지정합니다. **netreport.bat** 또는 **netreport.sh** 를 추가하여 파일 **$JAVA_HOME/bin/java netreport 개발** 또는 **@%JAVA_HOME%binjava netreport prod** 예.

>[!IMPORTANT]
>
>의 경우 **모니터링** 연산자가 작동하려면 네트워크가 실행되는 시스템이 의 보안 영역에 있어야 합니다. **sessionTokenonly** 모드. 이 연산자에 대해 신뢰할 수 있는 IP 마스크가 지정되지 않은 경우 보안 영역도 **allowEmptyPassword** 및 **allowUserpassword** 모드.

#### &#39;속성&#39; 요소 {#properties--element}

이 요소는 이메일 구성(예: )을 채우는 데 사용됩니다.

* **mailServer**: 이메일을 보내는 데 사용되는 SMTP 서버(예: smtp.domain.net).
* **mailFrom**: 보고서를 보낸 사람의 이메일 주소(예: monitoring@domain.net).
* **recipientList**: 모니터링 수신자의 이메일 주소 목록. 주소는 공백 없이 쉼표로 구분해야 합니다.
* &#39;**밤**&#39; 모드(선택 사항)는 지정된 기간 사이에 이메일을 보내지 않도록 하는 데 사용됩니다. 대신, 데이터가 통합되고, 밤 활동과 관련된 이메일이 종료 시간(기본적으로 7:00) 이후에 전송됩니다.
* 다음 **buildRange** 하위 요소(선택 사항)를 사용하면 최소 및 최대 빌드 번호를 지정할 수 있습니다. 빌드 번호가 이 범위에 속하지 않는 모든 컴퓨터에 대해 오류가 생성됩니다.

   ```
   <buildRange minimum="0000" maximum="9999"/>
   ```

* 다음을 추가할 수 있습니다. **`<sla>`** (선택 사항) **속성** 요소를 생성하지 않습니다. 보고서가 실행될 때마다 로그 파일이 생성됩니다. 예를 들어 파일 이름에는 구성 이름과 날짜 및 시간이 포함되어 있습니다 **dev_06_12_13_16_47_05.tmp**. 파일에는 인스턴스 이름, 컴퓨터 이름, 심각도 수준, (0~3, 가장 덜 중요한 것부터 가장 중요한 것까지), 날짜(타임스탬프 형식), 쿼리와 응답 사이의 경과 시간(밀리초), 사용된 서비스(http, ncs, ncsex, redir) 등의 정보가 포함되어 있습니다. 이 정보는 각 서비스가 끝날 때 표 표시와 줄 바꿈으로 구분됩니다.

>[!NOTE]
>
>다음 **persistHtmlFile** 값이 &quot;true&quot;인 속성 **`<property>`** 요소를 사용하여 파일의 최신 모니터링 상태를 기록합니다. **netreport.md**. 이 파일은 설치 디렉토리에 저장됩니다.

#### &#39;인스턴스&#39; 요소 {#instance--element}

이 요소를 사용하면 여러 컴퓨터(호스트)를 동일한 인스턴스로 다시 그룹화할 수 있습니다. 인스턴스 이름이 모니터링 이메일의 첫 번째 부분에 나타납니다. 인스턴스 이름을 클릭하여 각 컴퓨터에 대한 세부 정보에 액세스할 수 있습니다.

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
* **recipientList** (선택 사항): 특정 인스턴스에 대한 모니터링 보고서를 전자 메일로 보낼 수 있습니다.

#### &#39;호스트&#39; 요소 {#host--element}

이 요소는 호스트의 주어진 서버(예: )에 대한 모니터링을 구성합니다.

* **이름**: 모니터링할 컴퓨터의 이름.
* **별칭** (선택 사항): 보고서에 표시되는 모니터링 컴퓨터의 이름입니다.
* **sessionToken**: 인증된 세션 토큰을 통해 로그인 인증을 제공합니다.

   세션 토큰을 구성하려면 **모니터링** Adobe Campaign 콘솔의 연산자입니다. 다음에서 **액세스 권한** 탭에서 이 인스턴스를 모니터링하도록 승인된 컴퓨터의 IP 주소를 지정합니다. 그런 다음 를 사용하여 해당 컴퓨터에서 모니터링 페이지에 연결할 수 있습니다. **모니터링** 및 를 식별하며 암호를 지정할 필요가 없습니다.

   ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** (선택 사항): 심각도 수준별로 표시할 오류를 정렬할 수 있습니다. 가능한 값은 &#39;0&#39;(모든 레벨이 표시됨), &#39;1&#39;(높은 오류와 심각한 오류만 표시됨) 및 &#39;2&#39;(심각한 오류만 표시됨)입니다. 이 속성이 제공되지 않으면 모든 오류 레벨이 표시됩니다.
* **필터** (선택 사항): 예를 들어 특정 워크플로우 오류를 제외할 수 있습니다 **filter=&quot;wkf;wkf1&quot;**. 워크플로우 레이블은 세미콜론으로 구분해야 합니다.

#### 하위 요소 {#sub-elements}

* **tcp**: 서버가 작동 중인지 또는 작동 중지 상태인지 확인합니다. 포트 번호를 입력해야 합니다.
* **http**: 웹 서버가 있는지(애플리케이션 서버가 작동 중인지) 확인합니다.
* **ncs**: &#39;instance&#39; 속성에 입력한 인스턴스의 프로세스(워크플로 오류, 메모리 사용 등)를 확인합니다. 다음 **포함됨** (필수) 속성은 중단 프로세스(&#39;true&#39; 또는 &#39;false&#39; 값)를 표시하는 옵션을 제공합니다.
* **리디렉터**: 추적을 확인합니다.

대부분의 경우 **ncs** 및 **리디렉터** 하위 요소를 유지할 수 있습니다.

어떤 경우든 특정 노드는 하위 요소(예: 노드)에 오버로드될 수 있습니다 **port=75** http, ncs 또는 redir 연결에 사용되는 포트를 오버로드하려면 다음을 수행합니다.

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

다음에서 **ncs**, **리디렉터** 및 **http** 하위 요소, 다음을 추가할 수 있습니다. **isSecure** attribute(선택 사항): https 프로토콜(&#39;true&#39; 또는 &#39;false&#39; 값)을 사용할지 여부를 선택합니다. 이 속성을 제공하지 않으면 http 프로토콜이 사용됩니다.

### netreport.bat 또는 netreport.sh 파일 구성 {#configuring-the-netreport-bat-or-netreport-sh--file}

이를 구성하려면 이 파일을 편집하고 JRE 또는 JDK가 설치된 디렉토리를 지정합니다.

### 모니터링 시작 {#launching-monitoring}

모니터링을 시작하려면 다음을 실행합니다 **netreport.bat** 또는 **netreport.sh** 스크립트를 통해 일정한 간격으로 파일을 만듭니다. 보고서는 첫 번째 실행 후에 전송되며 상태가 변경되는 경우에만 전송됩니다.

### 모니터링 테스트 {#testing-monitoring}

모니터링을 테스트하려면 **netreport.bat** 또는 **netreport.sh** 파일.

에 지정된 수신자에게 이메일이 전송됩니다. **recipientList** / **netconf.xml** 파일.
