---
product: campaign
title: Adobe Campaign 시작
description: Adobe Campaign 시작
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 9%

---

# Adobe Campaign 시작{#launching-adobe-campaign}



Campaign 클라이언트 콘솔은 Campaign 애플리케이션 서버에 연결할 수 있는 리치 클라이언트입니다. [이 페이지](../../installation/using/installing-the-client-console.md)에서 클라이언트 콘솔을 다운로드하고 구성하는 방법에 대해 알아봅니다.

>[!CAUTION]
>
>[호환성 매트릭스](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)에서 Adobe Campaign 클라이언트 콘솔과의 시스템 및 도구 호환성을 확인합니다.

## Adobe Campaign 시작 {#starting-adobe-campaign}

**[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**&#x200B;을(를) 선택하여 Adobe Campaign을 시작할 수 있습니다.

클라이언트 콘솔 연결 창에서는 기존 데이터베이스를 선택하거나 구성하고 사용자 이름과 암호를 사용하여 기존 데이터베이스에 연결할 수 있습니다.

![](assets/acc-logon.png)

## Adobe Campaign에 연결 {#connecting-to-adobe-campaign}

Adobe ID을 사용하여 Adobe Campaign에 연결할 수 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

전용 로그인/암호로 연결할 수도 있습니다.

1. **[!UICONTROL Login]** 필드에 연산자 계정 식별자를 입력합니다.

   식별자는 Adobe Campaign 플랫폼의 관리자가 제공합니다.

1. **[!UICONTROL Password]** 필드에 암호를 입력하십시오.

   데이터베이스에 처음 액세스하면 관리자가 제공한 암호가 암호가 됩니다. 연결되면 **[!UICONTROL Tools > Change password...]** 메뉴를 통해 암호를 변경할 수 있습니다. 연산자 및 연결에 대한 자세한 내용은 [액세스 관리](../../platform/using/access-management.md)에서 확인할 수 있습니다.

1. 확인하려면 **[!UICONTROL LOG IN]**&#x200B;을(를) 클릭하세요.<!--You can also press the **Enter** key to launch connection.-->

이제 [Adobe Campaign 작업 영역](../../platform/using/adobe-campaign-workspace.md)에 액세스할 수 있습니다.

**[!UICONTROL Sign in screen]**&#x200B;에서 일부 키보드 단축키를 사용할 수 있습니다.
* 실행 가능한 모든 항목은 **Tab** 키(위에서 아래로) 또는 **Tab** + **Shift** 키(아래에서 위로)를 통해 선택할 수 있습니다.
* 연결을 시작하려면 **Enter** 키를 누를 수도 있습니다.
* **Esc** 키를 사용하여 **[!UICONTROL Login]** 및 **[!UICONTROL Password]** 필드를 마지막으로 성공한 연결 값으로 재설정할 수 있습니다.

## 연결 설정 {#setting-up-connections}

입력 영역 위의 링크를 통해 서버 연결 설정에 액세스할 수 있습니다.

![](assets/s_ncs_user_connections_management.png)

**[!UICONTROL Connections]** 창에서 **[!UICONTROL Add > Connection]**&#x200B;을(를) 클릭합니다.

그런 다음 연결 설정을 정의해야 합니다. 방법은 다음과 같습니다.

1. 데이터베이스 연결에 이름을 할당하려면 **[!UICONTROL Label]**&#x200B;을(를) 입력하십시오.

1. **[!UICONTROL URL]** 필드에 응용 프로그램 서버의 주소를 추가합니다. 연결 URL을 모르는 경우 관리자에게 문의하십시오.

1. 연산자가 Adobe ID을 사용하여 콘솔에 연결할 수 있는지 **[!UICONTROL Connect with an Adobe ID]**&#x200B;을(를) 확인하십시오. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

1. 유효성을 검사하려면 **[!UICONTROL OK]**&#x200B;을(를) 클릭하십시오.

## 운영자 및 권한 {#operators-and-permissions}

소프트웨어에 대한 액세스 권한 및 해당 권한이 있는 운영자의 식별자 및 암호는 Adobe Campaign 시스템 관리자가 Adobe Campaign 트리의 **[!UICONTROL Administration > Access management > Operators]** 노드에서 정의합니다.

이 기능은 [액세스 관리](../../platform/using/access-management.md) 섹션에 자세히 설명되어 있습니다.

## Adobe Campaign 연결 끊기 {#disconnecting-from-adobe-campaign}

Adobe Campaign에서 연결을 끊으려면 아이콘 막대의 첫 번째 아이콘을 사용하십시오.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>먼저 로그오프하지 않고 애플리케이션을 닫을 수도 있습니다.

## Adobe Campaign 버전 가져오기 {#getting-your-campaign-version}

**[!UICONTROL Help > About...]** 메뉴를 사용하여 다음 정보에 액세스할 수 있습니다.

* Campaign 클라이언트 콘솔 및 응용 프로그램 서버용 **버전** 번호
* Campaign 클라이언트 콘솔 및 응용 프로그램 서버용 **빌드** 번호
* Adobe 고객 지원 센터 연락을 위한 링크
* Adobe 개인정보 처리방침, 사용 약관 및 쿠키 정책 보기

![](assets/about-acc.png)

Adobe 고객 지원 팀에 문의할 때마다 Adobe Campaign 클라이언트 콘솔 및 애플리케이션 서버의 버전 번호 및 빌드 번호를 제공해야 합니다.

**관련 항목**:

* [Adobe Campaign 도움말 및 지원 옵션](../../support.md)
* [Adobe Campaign 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)
* [Adobe Experience Cloud 지원 및 전문가 세션](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
