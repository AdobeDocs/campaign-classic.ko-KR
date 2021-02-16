---
solution: Campaign Classic
product: campaign
title: 추적 시작
description: Adobe Campaign Classic에서 추적을 위한 일반적인 지침을 자세히 알아보십시오.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 55cc09c0446e389029890e45b790bb5ec6ffdc27
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 8%

---


# 메시지 추적 {#get-started-tracking} 시작하기

Adobe Campaign의 추적 기능 덕분에에서 전송한 메시지를 추적하고 수신자의 동작을 확인할 수 있습니다.열기, 링크 클릭, 구독 취소 등.

이 정보는 배달된 각 수신자의 프로필의 **[!UICONTROL Tracking]** 탭에서 검색됩니다. 이 탭에는 목록에서 선택한 수신자가 추적하고 클릭한 모든 URL 링크가 표시됩니다. 이것은 배달 화면에 여전히 있는 배달에서 추적된 모든 URL의 축적입니다. 목록을 구성할 수 있으며 일반적으로 다음이 포함됩니다.클릭한 URL, 클릭 날짜 및 시간, URL이 있는 문서. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/editing-a-profile.md#tracking-tab)을 참조하십시오.

**배달 대시보드**&#x200B;는 메시지를 보내는 동안 발생하는 배달 및 최종 문제를 모니터링하는 키이기도 합니다. 이에 대한 자세한 내용은 [이 섹션](../../delivery/using/delivery-dashboard.md)을 참조하십시오.

다음 다이어그램은 사용자와 다양한 서버 사이의 대화 상자 단계를 보여줍니다.

![](assets/tracking-diagram.png)

## 추적 {#configure-tracking} 구성

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**운영 원칙**

추적을 사용하기 전에 먼저 인스턴스에 대해 추적을 구성해야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#operating-principle)

**추적 서버**

추적을 구성하려면 인스턴스를 선언하여 추적 서버에 등록해야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#tracking-server)

**추적 저장 중**

추적을 구성하고 URL을 채운 후 추적 서버를 등록해야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#tracking-configuration#saving-tracking)

## 메시지 추적 {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**추적된 링크**

메시지 수신과 메시지 내용에 삽입된 링크의 활성화를 추적하여 받는 사람의 행동을 더 잘 이해할 수 있습니다. [자세히 알아보기](../../delivery/using/how-to-configure-tracked-links.md)

**URL 추적**

추적 옵션은 추적된 URL을 활성화 또는 비활성화하여 구성할 수 있습니다. [자세히 알아보기](../../delivery/using/personalizing-url-tracking.md)

**추적된 링크 개인화**

Campaign Classic 추적 기능을 사용하면 개인화할 수 있고 추적을 지원하는 이메일에 링크를 추가할 수 있습니다. [자세히 알아보기](https://helpx.adobe.com/campaign/kb/tracking-personnalized-links.html)

**추적 로그**

추적 기술 워크플로우는 게재를 보내고 추적을 활성화하면 추적 데이터를 검색합니다. 이 데이터는 배달의 추적 탭에서 찾을 수 있습니다. [자세히 알아보기](../../delivery/using/accessing-the-tracking-logs.md)

**추적 테스트**

추적을 사용하여 메시지를 보내기 전에 미러 페이지, 이메일 로그 및 링크에서 추적을 테스트할 수 있습니다. [자세히 알아보기](../../delivery/using/testing-tracking.md)

## 웹 응용 프로그램 추적 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**웹 애플리케이션 추적**

추적 태그를 사용하여 웹 애플리케이션 페이지의 방문을 추적하고 측정할 수도 있습니다. 이 기능은 양식 및 온라인 설문 조사와 같은 모든 웹 응용 프로그램 유형에 사용할 수 있습니다. [자세히 알아보기](../../web/using/tracking-a-web-application.md)

**웹 애플리케이션 추적 옵트아웃**

웹 애플리케이션 추적 옵트아웃을 사용하면 행동 추적을 옵트아웃한 최종 사용자의 웹 동작 추적을 중지할 수 있습니다. 사용자가 옵트아웃할 수 있도록 웹 애플리케이션 또는 랜딩 페이지에 배너를 표시하는 기능을 포함할 수 있습니다. [자세히 알아보기](../../web/using/web-application-tracking-opt-out.md)

## 추적 보고서 {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**통계 추적**

이 보고서는 열기, 클릭 및 거래에 대한 통계를 제공하며 배달이 미치는 마케팅 영향을 추적할 수 있도록 해줍니다. [자세히 알아보기](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL 및 클릭 스트림**

이 보고서는 배달 후 방문한 페이지 목록을 보여줍니다. [자세히 알아보기](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**개인/사용자 및 수신자**

이 예에서는 Adobe Campaign에서 사람/사람과 받는 사람 간의 추적 차이를 보다 잘 이해할 수 있습니다. [자세히 알아보기](../../reporting/using/person-people-recipients.md)

**지표 추적**

이 보고서는 열림, 클릭스루 비율 및 클릭스트림 등 전달 시 받는 사람의 행동을 추적하기 위한 주요 표시기를 결합합니다. [자세히 알아보기](../../reporting/using/delivery-reports.md#tracking-indicators)

**지표 계산**

다른 테이블에서는 배달 유형에 따라 다른 보고서에 사용된 지표 목록과 계산 공식을 제공합니다. [자세히 알아보기](../../reporting/using/indicator-calculation.md)

## 추적 문제 해결 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

다음 문제 해결 팁은 Adobe Campaign Classic에서 추적을 사용할 때 발생하는 가장 일반적인 문제를 해결하는 데 도움이 됩니다. 고급 문제 해결에 대한 자세한 내용은 [이 섹션](../../delivery/using/tracking-troubleshooting.md)을 참조하십시오.

* 추적 로그 프로세스가 실행 중인지 확인

   이 프로세스는 IIS/웹 서버 공유 메모리에서 읽고 리디렉션 로그를 씁니다.

   인스턴스에서 모니터링 탭을 선택하여 홈 페이지에서 액세스할 수 있습니다. 인스턴스에서 다음 명령을 실행할 수도 있습니다.`<user>@<instance>:~$ nlserver pdump`

   추적 로그 프로세스가 목록에 나타나지 않으면 인스턴스에서 다음 명령을 사용하여 해당 프로세스를 시작합니다.`<user>@<instance>:~$ nlserver start trackinglogd`

* 추적 기술 작업 과정이 최근에 실행되었는지 확인합니다.

   [관리] > [프로덕션] > [기술 워크플로우] 폴더에서 [추적] 기술 워크플로우를 찾을 수 있습니다.
