---
product: campaign
title: Adobe Campaign 시작
description: Adobe Campaign 시작
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 8491b3a5d1333f4445f90a8a051cd1f5149691bc
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 11%

---

# Adobe Campaign 시작{#launching-adobe-campaign}

![](../../assets/v7-only.svg)

Campaign 클라이언트 콘솔은

>[!CAUTION]
>
>에서 Adobe Campaign 클라이언트 콘솔과의 시스템 및 도구 호환성을 확인합니다. [호환성 매트릭스](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Adobe Campaign 시작 {#starting-adobe-campaign}

을(를) 선택하여 Adobe Campaign을 시작할 수 있습니다 **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

클라이언트 콘솔 연결 창에서 기존 데이터베이스를 선택하거나 구성하고 사용자 이름과 암호를 사용하여 데이터베이스에 연결할 수 있습니다.

![](assets/acc-logon.png)

## Adobe Campaign에 연결 {#connecting-to-adobe-campaign}

Adobe ID을 사용하여 Adobe Campaign에 연결할 수 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

전용 로그인/암호와 연결할 수도 있습니다.

1. 에 운영자 계정 식별자를 입력합니다. **[!UICONTROL Login]** 필드.

   식별자는 Adobe Campaign 플랫폼 관리자가 제공합니다.

1. 에 암호를 입력합니다. **[!UICONTROL Password]** 필드.

   데이터베이스에 처음 액세스하면 관리자가 제공한 비밀번호가 됩니다. 연결되면 을 통해 암호를 변경할 수 있습니다 **[!UICONTROL Tools > Change password...]** 메뉴 아래의 제품에서 사용할 수 있습니다. 연산자 및 연결에 대한 자세한 내용은 [액세스 관리](../../platform/using/access-management.md).

1. 클릭 **[!UICONTROL LOG IN]** 확인합니다.<!--You can also press the **Enter** key to launch connection.-->

이제 액세스할 수 있습니다 [Adobe Campaign 작업 공간](../../platform/using/adobe-campaign-workspace.md).

일부 키보드 단축키는 **[!UICONTROL Sign in screen]**:
* 모든 실행 가능한 항목은 **탭** 키(위에서 아래로) 또는 **탭** + **Shift** 키(아래쪽에서 위쪽으로).
* 연결을 시작하려면 **Enter 키** 키.
* 를 사용할 수 있습니다 **Esc** 키를 재설정합니다. **[!UICONTROL Login]** 및 **[!UICONTROL Password]** 마지막으로 성공한 연결 값에 대한 필드입니다.

## 연결 설정 {#setting-up-connections}

입력 영역 위의 링크를 통해 서버 연결 설정에 액세스할 수 있습니다.

![](assets/s_ncs_user_connections_management.png)

에서 **[!UICONTROL Connections]** 창 **[!UICONTROL Add > Connection]**.

그런 다음 연결 설정을 정의해야 합니다. 방법은 다음과 같습니다.

1. 을(를) 입력합니다. **[!UICONTROL Label]** 데이터베이스 연결에 이름을 할당합니다.

1. 응용 프로그램 서버의 주소를 **[!UICONTROL URL]** 필드. 연결 URL을 모를 경우 관리자에게 문의하십시오.

1. 확인 **[!UICONTROL Connect with an Adobe ID]** 운영자가 Adobe ID을 사용하여 콘솔에 연결할 수 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

1. 클릭 **[!UICONTROL OK]** 유효성을 검사하려면 다음을 수행하십시오.

## 연산자 및 권한 {#operators-and-permissions}

소프트웨어 및 해당 권한에 대한 액세스 권한이 있는 운영자의 식별자 및 암호는 **[!UICONTROL Administration > Access management > Operators]** 노드 아래에 나열된 상태로 남아 있습니다.

이 기능은 [액세스 관리](../../platform/using/access-management.md) 섹션을 참조하십시오.

## Adobe Campaign에서 연결 끊기 {#disconnecting-from-adobe-campaign}

Adobe Campaign에서 연결을 끊으려면 아이콘 막대에서 첫 번째 아이콘을 사용합니다.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>먼저 로그오프하지 않고 응용 프로그램을 닫을 수도 있습니다.

## Adobe Campaign 버전 가져오기 {#getting-your-campaign-version}

다음 **[!UICONTROL Help > About...]** 메뉴를 사용하면 다음 정보에 액세스할 수 있습니다.

* **버전** Campaign 클라이언트 콘솔 및 애플리케이션 서버의 번호
* **빌드** Campaign 클라이언트 콘솔 및 애플리케이션 서버의 번호
* Adobe 고객 지원 센터 연락을 위한 링크
* Adobe 개인정보 보호정책, 사용 약관 및 쿠키 정책에 대한 링크

![](assets/about-acc.png)

Adobe 고객 지원 팀에 문의할 때마다 Adobe Campaign 클라이언트 콘솔과 애플리케이션 서버의 버전 번호와 빌드 번호를 제공해야 합니다.

실행 중인 경우 [캠페인 [!DNL Gold Standard] 버전](../../rn/using/gold-standard.md)에 표시되는 SHA/1 문자를 공유해야 합니다 **[!UICONTROL About]** 상자. 예를 들어 **Gold Standard 12** 릴리스 시 이 빌드 번호가 표시될 수 있습니다. &quot;build 9032@554dbcd&quot;.

![](assets/about-acc-gs.png)

추가 정보 [!DNL Gold Standard] [이 문서](../../rn/using/gs-overview.md).

**관련 항목**:

* [Adobe Campaign 도움말 및 지원 옵션](../../support.md)
* [Adobe Campaign 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)
* [Adobe Experience Cloud 지원 및 전문가 세션](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
