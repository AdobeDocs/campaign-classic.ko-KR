---
solution: Campaign Classic
product: campaign
title: Adobe Campaign 시작
description: Adobe Campaign 시작
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 8%

---


# Adobe Campaign 시작{#launching-adobe-campaign}

캠페인 클라이언트 콘솔은 캠페인 응용 프로그램 서버에 연결할 수 있는 리치 클라이언트입니다. [이 페이지](../../installation/using/installing-the-client-console.md)에서 클라이언트 콘솔을 다운로드하고 구성하는 방법에 대해 알아봅니다.

## Adobe Campaign {#starting-adobe-campaign} 시작

**[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**&#x200B;을 선택하여 Adobe Campaign을 시작할 수 있습니다.

클라이언트 콘솔 연결 창에서 기존 데이터베이스를 선택하거나 구성하고 사용자 이름과 암호를 사용하여 데이터베이스에 연결할 수 있습니다.

![](assets/acc-logon.png)

## Adobe Campaign {#connecting-to-adobe-campaign}에 연결 중

Adobe ID을 사용하여 Adobe Campaign에 연결할 수 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

전용 로그인/암호를 사용하여 연결할 수도 있습니다.

1. **[!UICONTROL login]** 필드에 연산자 계정 식별자를 입력합니다.

   식별자는 Adobe Campaign 플랫폼 관리자가 제공합니다.

1. **[!UICONTROL Password]** 필드에 암호를 입력합니다.

   데이터베이스에 처음 액세스하면 관리자가 사용자에게 부여한 암호가 됩니다. 인터넷에 연결되면 **[!UICONTROL Tools > Change password...]** 메뉴를 통해 암호를 변경할 수 있습니다. 연산자 및 연결에 대한 자세한 내용은 [액세스 관리](../../platform/using/access-management.md)에서 확인할 수 있습니다.

1. **[!UICONTROL LOG IN]**&#x200B;을 클릭하여 확인합니다.

이제 [Adobe Campaign 작업 영역](../../platform/using/adobe-campaign-workspace.md)에 액세스할 수 있습니다.

## 연결 설정 {#setting-up-connections}

입력 영역 위의 링크를 통해 서버 연결 설정에 액세스할 수 있습니다.

![](assets/s_ncs_user_connections_management.png)

**[!UICONTROL Connections]** 창에서 **[!UICONTROL Add > Connection]**&#x200B;을 클릭합니다.

그런 다음 연결 설정을 정의해야 합니다. 방법은 다음과 같습니다.

1. 데이터베이스 연결에 이름을 지정하려면 **[!UICONTROL Label]**&#x200B;을 입력합니다.

1. **[!UICONTROL URL]** 필드에 응용 프로그램 서버의 주소를 추가합니다. 연결 URL을 모르는 경우 관리자에게 문의하십시오.

1. 연산자가 Adobe ID을 사용하여 콘솔에 연결하려면 **[!UICONTROL Connect with an Adobe ID]**&#x200B;을 선택합니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

1. 유효성을 확인하려면 **[!UICONTROL OK]**&#x200B;을 클릭합니다.

## 연산자 및 권한 {#operators-and-permissions}

소프트웨어에 대한 액세스 권한과 해당 권한이 있는 연산자의 식별자 및 암호는 Adobe Campaign 트리의 **[!UICONTROL Administration > Access management > Operators]** 노드에서 Adobe Campaign 시스템 관리자가 정의합니다.

이 기능은 [액세스 관리](../../platform/using/access-management.md) 섹션에 자세히 설명되어 있습니다.

## Adobe Campaign {#disconnecting-from-adobe-campaign} 연결 해제

Adobe Campaign 연결을 끊으려면 아이콘 막대에서 첫 번째 아이콘을 사용합니다.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>먼저 로그오프하지 않고 응용 프로그램을 닫을 수도 있습니다.

## Adobe Campaign 버전 {#getting-your-campaign-version}을(를) 가져오는 중

**[!UICONTROL Help > About...]** 메뉴를 통해 다음 정보에 액세스할 수 있습니다.

* **버전** 캠페인 클라이언트 콘솔 및 응용 프로그램 서버에 대한 번호
* **캠페인 클라이언트 콘솔 및 애플리케이션 서버에 대한** 빌드 번호
* Adobe 고객 지원 센터에 연락하는 링크
* Adobe 개인정보 보호정책, 사용 약관 및 쿠키 정책에 대한 링크

![](assets/about-acc.png)

Adobe 고객 지원 센터에 문의할 때마다 Adobe Campaign 클라이언트 콘솔 및 애플리케이션 서버의 버전 번호와 빌드 번호를 제공해야 합니다.

[Campaign Gold Standard 버전](../../rn/using/gold-standard.md)에서 실행 중인 경우 **[!UICONTROL About]** 상자에 표시된 SHA/1 문자도 공유해야 합니다. 예를 들어 Gold **Standard 10 릴리스**&#x200B;의 경우 빌드 번호는 아래와 같이 **빌드 9032@efd8a94**&#x200B;로 표시됩니다.

![](assets/about-acc-gs.png)

본 문서](https://helpx.adobe.com/kr/campaign/kb/gold-standard.html)에서 Gold Standard [에 대해 자세히 알아보십시오.

**관련 항목**:

* [Adobe Campaign 도움말 및 지원 옵션](https://helpx.adobe.com/kr/campaign/kb/ac-support.html#acc-support)
* [Adobe 소프트웨어 배포](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Adobe Experience Cloud 지원 및 전문가 세션](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
