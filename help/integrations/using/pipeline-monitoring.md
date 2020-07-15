---
title: 통합 구성
seo-title: 통합 구성
description: 통합 구성
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# 파이프라인 모니터링 {#pipeline-monitoring}

상태 웹 서비스는 [!DNL pipelined] [!DNL pipelined] 프로세스 상태에 대한 정보를 제공합니다.

브라우저를 사용하여 수동으로 액세스하거나 모니터링 애플리케이션을 통해 자동으로 액세스할 수 있습니다.

REST 형식으로 되어 있으며 아래에 설명되어 있습니다.

![](assets/triggers_8.png)

## 지표 {#indicators}

이 섹션에는 상태 웹 서비스의 지표가 나열됩니다.

모니터링할 권장 표시기가 강조 표시됩니다.

* 소비자: 트리거를 가져오는 클라이언트의 이름입니다. 파이프라인 옵션에 구성되었습니다.
* http-request
   * last-alive-ms-ago: 연결 검사가 수행된 이후 ms의 시간.
   * last-failed-cnx-ms-ago: 연결 검사가 실패한 마지막 시간 이후(ms)
   * pipeline-host: 파이프라인 데이터를 가져오는 호스트의 이름입니다.
* 포인터
   * 현재 오프셋: 파이프라인 내 자식 스레드당 포인터 값
   * last-flush-ms-ago: 트리거 일괄 처리가 검색되었기 때문에 밀리초 단위의 시간이 소요됩니다.
   * next-offsets-flush: 다음 일괄 처리가 완료될 때까지 기다리는 시간.
   * processed-since-last-flush: 마지막 일괄 처리에서 처리된 트리거 수입니다.
* 라우팅
   * 트리거: 검색된 트리거 목록입니다. 옵션에서 [!DNL pipelined] 구성됨
* stats
   * average-pointer-flush-time-ms: 하나의 트리거 묶음에 대한 평균 처리 시간입니다.
   * average-trigger-processing-time-ms: 트리거 데이터를 구문 분석하는 데 걸린 평균 시간입니다.
   * bytes-read: 프로세스가 시작된 이후 대기열에서 읽은 바이트 수입니다.
   * 현재 메시지: 대기열에서 가져와 처리 대기 중인 보류 중인 메시지의 현재 수입니다. **이 표시기는 0에 가까워야 합니다**.
   * 현재 재시도: 처리가 실패하고 재시도를 기다리는 현재 메시지 수입니다.
   * 최대 메시지: 프로세스가 시작된 이후 처리 중인 보류 중인 최대 메시지 수입니다.
   * 포인터 플러시: 시작 이후 처리된 메시지 일괄 처리 수입니다.
   * routing-JS-custom: 사용자 지정 JS가 처리한 메시지 수입니다.
   * 트리거 폐기됨: 처리 오류로 인해 너무 많은 재시도 후 폐기된 메시지 수입니다.
   * 트리거 처리: 오류 없이 처리된 메시지 수입니다.
   * trigger-received: 큐에서 받은 메시지 수입니다.

이러한 통계는 처리 스레드당 표시됩니다.

* average-trigger-processing-time-ms: 트리거 데이터를 구문 분석하는 데 걸린 평균 시간입니다.
* is-JS-processor: 이 스레드에서 사용자 지정 JS를 사용하는 경우 값 &quot;1&quot;입니다.
* 트리거 폐기됨: 처리 오류로 인해 너무 많은 재시도 후 폐기된 메시지 수입니다. **이 표시기는 0이어야**&#x200B;합니다.
* 트리거 실패: JS의 처리 오류 수입니다. **이 표시기는 0이어야**&#x200B;합니다.
* trigger-received: 큐에서 받은 메시지 수입니다.

* 설정: 구성 파일에 설정됩니다.
   * flush-pointer-msg-count: 일괄 처리에서의 메시지 수입니다.
   * flush-pointer-period-ms: 두 배치 간 시간(밀리초 단위)
   * processing-threads-JS: 사용자 지정 JS를 실행하는 처리 스레드 수입니다.
   * retry-period-ms: 처리 오류가 발생할 때 두 재시도 사이의 시간입니다.
   * retry-validity-duration-ms: 메시지가 삭제될 때까지 처리가 다시 시도될 때까지 기간입니다.
   * 파이프라인 메시지 보고서

## 파이프라인 메시지 보고서 {#pipeline-report}

이 보고서에는 지난 5일 동안의 시간당 메시지 수가 표시됩니다.

![](assets/triggers_9.png)
