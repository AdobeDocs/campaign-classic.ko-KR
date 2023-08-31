---
product: campaign
title: 추적 시작
description: Adobe Campaign에서의 추적을 위한 일반 지침 자세히 알아보기
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 10%

---

# 메시지 추적 시작 {#get-started-tracking}



추적 기능 덕분에 Adobe Campaign을 사용하면 보낸 메시지를 추적하고 열기, 링크 클릭, 구독 취소 등과 같은 수신자의 동작을 확인할 수 있습니다.

이 정보는 **[!UICONTROL Tracking]** 게재 각 수신자 프로필의 탭입니다. 이 탭에는 목록에서 선택한 수신자가 추적하고 클릭한 모든 URL 링크가 표시됩니다. 게재 화면에 여전히 존재하는 게재에서 추적된 모든 URL의 누적입니다. 목록을 구성할 수 있으며 일반적으로 에는 클릭한 URL, 클릭한 날짜 및 시간, URL이 발견된 문서가 포함됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/editing-a-profile.md#tracking-tab)을 참조하십시오.

다음 **게재 대시보드** 는 또한 메시지를 보내는 동안 발생하는 게재 및 최종 문제를 모니터링하는 키입니다. 자세한 내용은 다음을 참조하십시오. [이 섹션](delivery-dashboard.md).

다음 다이어그램은 사용자와 여러 서버 간의 대화 단계를 보여 줍니다.

![](assets/tracking-diagram.png)

## 추적 구성 {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**운영 원칙**

추적을 사용하기 전에 먼저 인스턴스에 대해 구성해야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#operating-principle)

**추적 서버**

추적을 구성하려면 인스턴스를 선언하고 추적 서버에 등록해야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#tracking-server)

**추적 저장 중**

추적이 구성되고 URL이 채워지면 추적 서버를 등록해야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#saving-tracking)

## 메시지 추적 {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**추적된 링크**

메시지 수신 및 메시지 콘텐츠에 삽입된 링크의 활성화를 추적하여 수신자의 동작을 더 잘 이해할 수 있습니다. [자세히 알아보기](how-to-configure-tracked-links.md)

**URL 추적**

추적 옵션은 추적된 URL을 활성화하거나 비활성화하여 구성할 수 있습니다. [자세히 알아보기](personalizing-url-tracking.md)

**추적된 링크 개인화**

Campaign Classic 추적 기능을 사용하면 개인화할 수 있고 추적을 지원하는 이메일에 링크를 추가할 수 있습니다. [자세히 알아보기](tracking-personalized-links.md)

**추적 로그**

추적 기술 워크플로우는 게재가 전송되고 추적이 활성화되면 추적 데이터를 검색합니다. 이 데이터는 게재의 추적 탭에서 찾을 수 있습니다. [자세히 알아보기](accessing-the-tracking-logs.md)

**추적 테스트**

추적을 사용하여 메시지를 보내기 전에 미러 페이지, 이메일 로그 및 링크에서 추적을 테스트할 수 있습니다. [자세히 알아보기](testing-tracking.md)

## 웹 애플리케이션 추적 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**웹 애플리케이션 추적**

추적 태그를 사용하여 웹 애플리케이션 페이지에서 방문을 추적하고 측정할 수도 있습니다. 이 기능은 양식 및 랜딩 페이지와 같은 모든 웹 애플리케이션 유형에 사용할 수 있습니다. [자세히 알아보기](../../web/using/tracking-a-web-application.md)

**웹 애플리케이션 추적 옵트아웃**

웹 애플리케이션 추적 옵트아웃을 사용하면 행동 추적을 옵트아웃한 최종 사용자의 웹 행동 추적을 중지할 수 있습니다. 웹 애플리케이션이나 랜딩 페이지에 배너를 표시하여 사용자가 옵트아웃할 수 있도록 하는 기능을 포함할 수 있습니다. [자세히 알아보기](../../web/using/web-application-tracking-opt-out.md)

## 추적 보고서 {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**추적 통계**

이 보고서는 열기, 클릭 및 트랜잭션에 대한 통계를 제공하며 게재의 마케팅 영향을 추적할 수 있습니다. [자세히 알아보기](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL 및 클릭 스트림**

이 보고서는 게재 후 방문한 페이지 목록을 보여줍니다. [자세히 알아보기](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**개인/사용자 및 수신자**

이 예제를 통해 Adobe Campaign의 사용자/사용자와 수신자 간의 추적 차이를 더 잘 이해할 수 있습니다. [자세히 알아보기](../../reporting/using/person-people-recipients.md)

**지표 추적**

이 보고서는 열기, 클릭스루 비율 및 클릭 스트림과 같은 게재 수신 시 수신자의 동작을 추적하기 위한 주요 지표를 결합합니다. [자세히 알아보기](../../reporting/using/delivery-reports.md#tracking-indicators)

**지표 계산**

다른 테이블은 배달 유형에 따라 다른 보고서에서 사용되는 지표 목록과 해당 계산 공식을 제공합니다. [자세히 알아보기](../../reporting/using/indicator-calculation.md)

## 추적 문제 해결 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

다음 문제 해결 팁은 Adobe Campaign Classic에서 추적을 사용할 때 발생하는 가장 일반적인 문제를 해결하는 데 도움이 됩니다. 고급 문제 해결은 다음을 참조하십시오. [이 섹션](tracking-troubleshooting.md).

* trackinglogd 프로세스가 실행 중인지 확인

  이 프로세스는 IIS/웹 서버 공유 메모리를 읽고 리디렉션 로그를 기록합니다.

  인스턴스의 모니터링 탭을 선택하여 홈페이지에서 액세스할 수 있습니다. 인스턴스에서 다음 명령을 실행할 수도 있습니다. `<user>@<instance>:~$ nlserver pdump`

  trackinglogd 프로세스가 목록에 표시되지 않으면 인스턴스에서 다음 명령을 사용하여 시작합니다. `<user>@<instance>:~$ nlserver start trackinglogd`

* 추적 기술 워크플로우가 최근에 실행되었는지 확인합니다.

  폴더 관리 > 프로덕션 > 기술 워크플로우에서 추적 기술 워크플로우를 찾을 수 있습니다.
