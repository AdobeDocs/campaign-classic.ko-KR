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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 84f06afb36aa6a9fa13db1fda7034389b762eb99
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Adobe Campaign 시작{#launching-adobe-campaign}

캠페인 클라이언트 콘솔은 캠페인 응용 프로그램 서버에 연결할 수 있는 리치 클라이언트입니다. 이 페이지에서 클라이언트 콘솔을 다운로드 및 구성하는 방법 [을 알아봅니다](../../installation/using/installing-the-client-console.md).

## 시작 Adobe Campaign {#starting-adobe-campaign}

을 선택하여 Adobe Campaign을 시작할 수 있습니다 **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

클라이언트 콘솔 연결 창을 사용하면 기존 데이터베이스를 선택하거나 구성하고 사용자 이름과 암호를 사용하여 데이터베이스에 연결할 수 있습니다.

![](assets/s_ncs_user_login.png)

## Adobe Campaign에 연결 {#connecting-to-adobe-campaign}

Adobe ID을 사용하여 Adobe Campaign에 연결할 수 있습니다. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).

전용 로그인/암호와 연결할 수도 있습니다.

1. 필드에 연산자 계정 식별자를 **[!UICONTROL login]** 입력합니다.

   식별자는 Adobe Campaign 플랫폼 관리자가 제공합니다.

1. 필드에 암호를 **[!UICONTROL Password]** 입력합니다.

   데이터베이스에 처음 액세스할 때 암호는 관리자가 사용자에게 부여하는 암호입니다. 인터넷에 연결되면 **[!UICONTROL Tools > Change password...]** 메뉴를 통해 암호를 변경할 수 있습니다. 연산자 및 연결에 대한 자세한 내용은 [액세스 관리에서 확인할 수 있습니다](../../platform/using/access-management.md).

1. 을 **[!UICONTROL Log in]** 클릭하여 확인합니다.

이제 [Adobe Campaign 작업 영역에 액세스할 수 있습니다](../../platform/using/adobe-campaign-workspace.md).

## 연결 설정 {#setting-up-connections}

입력 영역 위의 링크를 통해 서버 연결 설정에 액세스할 수 있습니다.

![](assets/s_ncs_user_connections_management.png)

창에서 **[!UICONTROL Connections]** 을 클릭합니다 **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

그런 다음 연결 설정을 정의해야 합니다. 이렇게 하려면:

1. 데이터베이스 연결 **[!UICONTROL Label]** 에 이름을 지정할 을 입력합니다.

1. 필드에 응용 프로그램 서버의 주소를 **[!UICONTROL URL]** 추가합니다. 연결 URL을 모르는 경우 관리자에게 문의하십시오.

1. Adobe ID **[!UICONTROL Connect with an Adobe ID]** 를 사용하여 콘솔에 연결할 연산자가 있는지 확인합니다. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).

1. 을 **[!UICONTROL OK]** 클릭하여 유효성을 확인합니다.

## 연산자 및 권한 {#operators-and-permissions}

소프트웨어 및 해당 권한에 대한 액세스 권한이 있는 연산자의 식별자 및 암호는 Adobe Campaign 트리 **[!UICONTROL Administration > Access management > Operators]** 의 노드에 있는 Adobe Campaign 시스템 관리자가 정의합니다.

이 기능은 [액세스 관리](../../platform/using/access-management.md) 섹션에 자세히 설명되어 있습니다.

## Adobe Campaign 연결 해제 {#disconnecting-from-adobe-campaign}

Adobe Campaign에서 연결을 끊으려면 아이콘 막대의 첫 번째 아이콘을 사용합니다.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>먼저 로그오프하지 않고 응용 프로그램을 닫을 수도 있습니다.

## 캠페인 버전 가져오기 {#getting-your-campaign-version}

이 **[!UICONTROL Help > About...]** 메뉴를 통해 다음 정보에 액세스할 수 있습니다.

* **버전** 번호,
* **빌드** 번호,
* Adobe Campaign 지원에 문의하는 링크입니다.

   >[!CAUTION]
   >
   >Adobe 지원 팀에 문의할 때마다 버전 번호와 Campaign 클라이언트 콘솔 및 애플리케이션 서버의 빌드 번호를 제공해야 합니다.

