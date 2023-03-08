---
product: campaign
title: 파이프라인 모니터링
description: 파이프라인 모니터링
audience: integrations
content-type: reference
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 36b10a49fe92853f98beeb9e7d2fea3f59b10b6f
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 1%

---

# 파이프라인 모니터링 {#pipeline-monitoring}

![](../../assets/common.svg)

다음 [!DNL pipelined] 상태 웹 서비스는 의 상태에 대한 정보를 제공합니다. [!DNL pipelined] 프로세스.

브라우저를 사용하여 수동으로 또는 모니터링 응용 프로그램으로 자동으로 액세스할 수 있습니다.

아래에 설명되어 있는 REST 형식입니다.

![](assets/triggers_8.png)

## 지표 {#indicators}

이 섹션에는 상태 웹 서비스의 지표가 나열됩니다.

모니터링할 권장 표시기가 강조 표시됩니다.

* 소비자: 트리거를 적용하는 클라이언트의 이름입니다. 파이프라인 옵션에서 구성됩니다.
* http 요청
   * last-alive-ms-ago: 연결 확인 이후 ms의 시간.
   * last-failed-cnx-ms-ago: 연결 검사가 마지막으로 실패한 이후 ms 단위 시간입니다.
   * pipeline-host: 파이프라인 데이터를 가져오는 호스트의 이름입니다.
* 포인터
   * current-offsets: 하위 스레드당 파이프라인에 있는 포인터의 값입니다.
   * last-flush-ms-ago: 트리거 일괄 처리가 검색된 이후의 시간(ms)입니다.
   * next-offsets-flush: 완료되면 다음 배치까지 대기할 시간입니다.
   * processed-since-last-flush: 마지막 배치에서 처리된 트리거 수입니다.
* 라우팅
   * 트리거: 트리거 목록을 검색했습니다. 에서 구성됨 [!DNL pipelined] 옵션을 선택합니다.
* 통계
   * average-pointer-flush-time-ms: 트리거 배치 1개에 대한 평균 처리 시간입니다.
   * average-trigger-processing-time-ms: 트리거 데이터를 구문 분석하는 데 걸린 평균 시간입니다.
   * bytes-read: 프로세스가 시작된 후 큐에서 읽은 바이트 수입니다.
   * current-messages: 대기열에서 가져와서 처리 대기 중인 보류 중인 현재 메시지 수입니다. **이 표시기는 0에 가까워야 합니다.**.
   * current-retries: 처리에 실패하여 재시도 대기 중인 현재 메시지 수입니다.
   * 피크 메시지: 프로세스가 시작된 후 처리한 최대 보류 메시지 수입니다.
   * 포인터 플러시: 시작 이후 처리된 메시지 배치 수입니다.
   * routing-JS-custom: 사용자 지정 JS에서 처리된 메시지 수입니다.
   * trigger-discarded: 처리 오류로 인해 너무 많은 다시 시도 후 삭제된 메시지 수입니다.
   * trigger-processed: 오류 없이 처리된 메시지 수.
   * trigger-received: 큐에서 받은 메시지 수입니다.

이러한 통계는 처리 스레드별로 표시됩니다.

* average-trigger-processing-time-ms: 트리거 데이터를 구문 분석하는 데 걸린 평균 시간입니다.
* is-JS-processor: 이 스레드가 사용자 지정 JS를 사용하는 경우 값 &quot;1&quot;.
* trigger-discarded: 처리 오류로 인해 너무 많은 다시 시도 후 삭제된 메시지 수입니다. **이 표시기는 0이어야 합니다.**.
* trigger-failures: JS의 처리 오류 수. **이 표시기는 0이어야 합니다.**.
* trigger-received: 큐에서 받은 메시지 수입니다.

* 설정: 구성 파일에 설정됩니다.
   * flush-pointer-msg-count: 일괄 처리의 메시지 수입니다.
   * flush-pointer-period-ms: 두 배치 사이의 시간(밀리초)입니다.
   * processing-threads-JS: 사용자 지정 JS를 실행하는 처리 스레드 수입니다.
   * 재시도 기간-ms: 처리 오류가 발생할 때 두 재시도 사이의 시간입니다.
   * retry-validity-duration-ms: 메시지가 삭제될 때까지 처리를 재시도할 때까지의 기간입니다.
   * 파이프라인 메시지 보고서

## 파이프라인 메시지 보고서 {#pipeline-report}

이 보고서에는 지난 5일 동안 시간당 메시지 수가 표시됩니다.

![](assets/triggers_9.png)
