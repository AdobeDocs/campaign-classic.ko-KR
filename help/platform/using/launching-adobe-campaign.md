---
title: Adobe Campaign 시작
seo-title: Adobe Campaign 시작
description: Adobe Campaign 시작
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
translation-type: tm+mt
source-git-commit: 285cf8c6521696a0a94f6ffd8fc1eb148977836d
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 7%

---


# Adobe Campaign 시작{#launching-adobe-campaign}

캠페인 클라이언트 콘솔은 캠페인 응용 프로그램 서버에 연결할 수 있는 리치 클라이언트입니다. 이 페이지에서 클라이언트 콘솔을 다운로드 및 구성하는 방법 [을 알아봅니다](../../installation/using/installing-the-client-console.md).

## Starting Adobe Campaign {#starting-adobe-campaign}

Adobe Campaign을 선택하여 시작할 수 있습니다 **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

클라이언트 콘솔 연결 창을 사용하면 기존 데이터베이스를 선택하거나 구성하고 사용자 이름과 암호를 사용하여 데이터베이스에 연결할 수 있습니다.

![](assets/acc-logon.png)

## Adobe Campaign 연결 중 {#connecting-to-adobe-campaign}

Adobe ID을 사용하여 Adobe Campaign에 연결할 수 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

전용 로그인/암호와 연결할 수도 있습니다.

1. 필드에 연산자 계정 식별자를 **[!UICONTROL login]** 입력합니다.

   식별자는 Adobe Campaign 플랫폼 관리자가 제공합니다.

1. 필드에 암호를 **[!UICONTROL Password]** 입력합니다.

   데이터베이스에 처음 액세스할 때 암호는 관리자가 사용자에게 부여하는 암호입니다. 인터넷에 연결되면 **[!UICONTROL Tools > Change password...]** 메뉴를 통해 암호를 변경할 수 있습니다. 연산자 및 연결에 대한 자세한 내용은 [액세스 관리에서 확인할 수 있습니다](../../platform/using/access-management.md).

1. 을 **[!UICONTROL LOG IN]** 클릭하여 확인합니다.

이제 [Adobe Campaign 작업 영역에 액세스할 수 있습니다](../../platform/using/adobe-campaign-workspace.md).

## 연결 설정 {#setting-up-connections}

입력 영역 위의 링크를 통해 서버 연결 설정에 액세스할 수 있습니다.

![](assets/s_ncs_user_connections_management.png)

In the **[!UICONTROL Connections]** window, click **[!UICONTROL Add > Connection]**.

그런 다음 연결 설정을 정의해야 합니다. 방법은 다음과 같습니다.

1. 데이터베이스 연결 **[!UICONTROL Label]** 에 이름을 지정할 을 입력합니다.

1. 필드에 응용 프로그램 서버의 주소를 **[!UICONTROL URL]** 추가합니다. 연결 URL을 모르는 경우 관리자에게 문의하십시오.

1. 연산자 **[!UICONTROL Connect with an Adobe ID]** 가 Adobe ID을 사용하여 콘솔에 연결되는지 확인합니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

1. 을 **[!UICONTROL OK]** 클릭하여 유효성을 확인합니다.

## 연산자 및 권한 {#operators-and-permissions}

소프트웨어 및 해당 권한에 대한 액세스 권한이 있는 연산자의 식별자 및 암호는 Adobe Campaign 트리 **[!UICONTROL Administration > Access management > Operators]** 의 노드에 있는 Adobe Campaign 시스템 관리자가 정의합니다.

이 기능은 [액세스 관리](../../platform/using/access-management.md) 섹션에 자세히 설명되어 있습니다.

## Adobe Campaign에서 연결 끊기 {#disconnecting-from-adobe-campaign}

Adobe Campaign에서 연결을 끊으려면 아이콘 막대에서 첫 번째 아이콘을 사용합니다.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>먼저 로그오프하지 않고 응용 프로그램을 닫을 수도 있습니다.

## Adobe Campaign 버전 다운로드 {#getting-your-campaign-version}

이 **[!UICONTROL Help > About...]** 메뉴를 통해 다음 정보에 액세스할 수 있습니다.

* **캠페인 클라이언트 콘솔 및 응용 프로그램 서버의 버전** 번호
* **캠페인 클라이언트 콘솔 및 응용 프로그램 서버의 빌드** 번호
* adobe 고객 지원 센터에 연락하는 링크
* adobe 개인정보 보호정책, 사용 약관 및 쿠키 정책에 대한 링크

![](assets/about-acc.png)

Adobe 고객 지원 센터에 문의할 때마다 Adobe Campaign 클라이언트 콘솔 및 애플리케이션 서버의 버전 번호와 빌드 번호를 제공해야 합니다.

Campaign Gold [Standard 버전에서](../../rn/using/gold-standard.md)실행 중인 경우 **[!UICONTROL About]** 상자에 표시된 SHA/1 문자도 공유해야 합니다. 예를 들어 Gold **Standard 10 릴리스의**&#x200B;경우 빌드 번호는 아래와 같이 **빌드 9032@efd8a94**&#x200B;으로 표시됩니다.

![](assets/about-acc-gs.png)

이 문서에서 Gold Standard [에 대한 자세한 내용을 살펴보십시오](https://helpx.adobe.com/kr/campaign/kb/gold-standard.html).

**관련 항목**:

* [Adobe Campaign 도움말 및 지원 옵션](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support)
* [Adobe 소프트웨어 배포](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Adobe Experience Cloud 지원 및 전문가 세션](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
