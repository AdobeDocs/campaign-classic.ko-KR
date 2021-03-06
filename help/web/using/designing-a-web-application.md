---
product: campaign
title: 웹 애플리케이션 디자인
description: 웹 애플리케이션 디자인
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 0ad183ae68faf41ac0b14bb37639a4b1da9d8776
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 4%

---

# 웹 애플리케이션 디자인{#designing-a-web-application}

![](../../assets/common.svg)

웹 애플리케이션은 [웹 양식](about-web-forms.md).

>[!CAUTION]
>
>를 사용하십시오 **[!UICONTROL Preview]** 하위 탭을 사용하여 웹 응용 프로그램 디자인 중 오류를 확인합니다. 웹 애플리케이션을 미리 보는 데 사용되는 프로필 테스트는 **[!UICONTROL Access rights]** 대상 **[!UICONTROL Web application agent]** 연산자를 사용할 수 있습니다. </br>웹 응용 프로그램이 게시될 때까지 변경 사항은 최종 사용자에게 표시되지 않습니다.

## 웹 응용 프로그램에 차트 삽입 {#inserting-charts-in-a-web-application}

웹 응용 프로그램에 차트를 포함할 수 있습니다. 이렇게 하려면 작업 표시줄에서 차트 드롭다운 목록을 사용하여 삽입할 차트 유형을 선택합니다.

![](assets/s_ncs_admin_webapps_bar_graph.png)

을(를) 선택할 수도 있습니다 **[!UICONTROL Add a chart]** 메뉴 아래의 제품에서 사용할 수 있습니다.

![](assets/s_ncs_admin_webapps_graph.png)

## 웹 응용 프로그램에 테이블 삽입 {#inserting-tables-in-a-web-application}

테이블을 추가하려면 작업 표시줄에서 테이블 드롭다운 목록을 사용하여 사용할 테이블 유형을 선택합니다.

![](assets/s_ncs_admin_webapps_bar_table.png)

드롭다운 메뉴에서 테이블 유형을 선택할 수도 있습니다.

![](assets/s_ncs_admin_webapps_table.png)

## 개요 유형 웹 애플리케이션 {#overview-type-web-applications}

Adobe Campaign 인터페이스는 많은 웹 애플리케이션을 사용하여 수신자, 게재, 캠페인, 주식 등에 액세스하고, 관리하고, 상호 작용합니다.

인터페이스는 한 페이지만 있는 대시보드 형태로 표시됩니다.

기본 웹 응용 프로그램은 **[!UICONTROL Administration > Configuration > Web applications]** 노드 아래에 있어야 합니다.

## 양식 형식의 웹 응용 프로그램 편집 {#edit-forms-type-web-applications}

엑스트라넷용 양식 웹 응용 프로그램은 다음과 같은 특징이 있습니다.

* 사전 로드 상자

   대부분의 경우 표시할 데이터를 미리 로드해야 합니다. 이러한 양식에 액세스하는 사용자는 액세스 제어를 통해 식별되므로 사전 로딩이 반드시 암호화되지는 않습니다.

* 저장 상자
* 페이지 추가

   &quot;개요&quot; 유형 웹 응용 프로그램에는 모두 단일 페이지가 있지만, 편집 양식은 특정 기준(테스트, 선택, 연결된 연산자의 프로필 등)에 따라 일련의 페이지를 제공할 수 있습니다.

