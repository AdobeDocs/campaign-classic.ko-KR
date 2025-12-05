---
product: campaign
title: Adobe Campaign 작업 영역
description: Campaign 작업 영역을 사용하고 맞춤화하는 방법 알아보기
feature: Overview
role: Developer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 354fc8fd5d030ed88e2b279ba1dd3eaf2f314d53
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 4%

---

# Adobe Campaign 작업 영역 {#adobe-campaign-workspace}

## Adobe Campaign 인터페이스 살펴보기 {#about-adobe-campaign-interface}

데이터베이스에 연결되면 Adobe Campaign 홈 페이지에 액세스합니다. 이 페이지는 대시보드이며, 설치 및 일반 플랫폼 구성에 따라 기능에 액세스할 수 있는 링크 및 바로 가기로 구성되어 있습니다.

홈페이지의 중앙 섹션에서 링크를 사용하여 Campaign 설명서 포털, 커뮤니티 및 Adobe 고객 지원 센터 웹 사이트에 액세스할 수 있습니다.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) [비디오](#video)에서 Campaign 작업 영역 검색

>[!NOTE]
>
>인스턴스에서 사용할 수 있는 Adobe Campaign 기능은 설치된 모듈 및 추가 기능에 따라 다릅니다. 사용 권한 및 특정 구성에 따라 일부 쿠키를 사용하지 못할 수도 있습니다.
>
>모듈이나 추가 기능을 설치하기 전에 라이선스 계약을 확인하거나 Adobe 계정 담당자에게 문의해야 합니다.

### 콘솔 및 웹 액세스 {#console-and-web-access}

Adobe Campaign 플랫폼은 콘솔 또는 인터넷 브라우저를 통해 액세스할 수 있습니다. [호환성 매트릭스](../../rn/using/compatibility-matrix.md#Browsers)에서 호환되는 브라우저를 확인하세요.

웹 액세스 인터페이스는 콘솔 인터페이스와 유사합니다. 브라우저에서 콘솔과 동일한 탐색 및 표시 기능을 사용할 수 있지만 캠페인에 대해 축소된 작업 세트만 수행할 수 있습니다. 예를 들어 캠페인을 보고 취소할 수 있지만 캠페인을 수정할 수는 없습니다. 지정된 연산자의 경우 캠페인이 콘솔에 다음 옵션과 함께 표시됩니다.

![운영자는 캠페인의 대시보드에서 캠페인을 보고 취소할 수 있지만 수정할 수도 있고 게재, 문서 및 작업을 추가할 수도 있습니다.](assets/operation_from_console.png)

반면 웹 액세스의 경우 옵션은 주로 다음 보기를 활성화합니다.

![브라우저에서 동일한 연산자만 캠페인을 보고 취소할 수 있습니다.](assets/operation_from_web.png)

[Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-create.html?lang=ko#use-the-web-interface-){target=_blank}에서 웹 인터페이스 사용에 대해 자세히 알아보세요.

### 언어 {#languages}

Adobe Campaign Classic 인스턴스를 설치할 때 언어가 선택됩니다.

![](assets/language.png)

다음 언어 중에서 선택할 수 있습니다.

* 영어(영국)
* 영어(미국)
* 프랑스어
* 독일어
* 일본어

Adobe Campaign Classic 인스턴스에 대해 선택한 언어는 날짜 및 시간 형식에 영향을 줄 수 있습니다. 자세한 내용은 [Campaign v8(콘솔) 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}를 참조하세요.

인스턴스를 만드는 방법에 대한 자세한 내용은 이 [페이지](../../installation/using/creating-an-instance-and-logging-on.md)를 참조하세요.

>[!CAUTION]
>
>인스턴스를 만든 후에는 언어를 변경할 수 없습니다.

## 탐색 기본 사항 {#navigation-basics}

플랫폼의 다양한 기능은 핵심 기능으로 분류됩니다. 인터페이스의 상단 섹션에 표시되는 링크를 사용하여 기능에 액세스합니다.

![](assets/overview_home.png)

액세스할 수 있는 핵심 기능 목록은 설치한 패키지 및 추가 기능과 액세스 권한에 따라 다릅니다.

### 페이지 찾아보기 {#browsing-pages}

각 기능에는 작업 관련 요구 사항 및 사용 컨텍스트를 기반으로 하는 기능 세트가 포함되어 있습니다. 예를 들어 **[!UICONTROL Profiles and targets]** 링크를 사용하면 받는 사람 목록, 구독 서비스, 기존 타겟팅 워크플로 및 이러한 요소를 만드는 바로 가기를 볼 수 있습니다.

**[!UICONTROL Lists]** 인터페이스의 왼쪽 섹션에 있는 **[!UICONTROL Profiles and Targets]** 링크를 통해 목록을 사용할 수 있습니다.

![](assets/recipient_list_overview.png)

### 탭 사용 {#using-tabs}

* 핵심 기능 또는 링크를 클릭하면 관련 페이지가 현재 페이지를 대체합니다. 이전 페이지로 돌아가려면 도구 모음에서 **[!UICONTROL Back]** 단추를 클릭합니다. 홈 페이지로 돌아가려면 **[!UICONTROL Home]** 단추를 클릭하십시오.

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* 메뉴 또는 디스플레이 화면에 대한 바로 가기(예: 웹 애플리케이션, 프로그램, 게재, 보고서 등)의 경우, 일치하는 페이지가 다른 탭에 표시됩니다. 이 경우 탭을 사용하여 한 페이지에서 다른 페이지로 이동할 수 있습니다.

  ![](assets/d_ncs_user_interface_tabs.png)

### 요소 만들기 {#creating-an-element}

각 핵심 기능 섹션을 통해 사용 가능한 요소 간을 검색할 수 있습니다. 이렇게 하려면 **[!UICONTROL Browsing]** 섹션에서 바로 가기를 사용합니다. **[!UICONTROL Other choices]** 링크를 사용하면 환경에 관계없이 다른 모든 페이지에 액세스할 수 있습니다.

화면 왼쪽의 **[!UICONTROL Create]** 섹션에서 바로 가기를 사용하여 새 요소(게재, 웹 애플리케이션, 워크플로 등)를 만들 수 있습니다. 목록 위에 있는 **[!UICONTROL Create]** 단추를 사용하여 새 요소를 목록에 추가하십시오.

예를 들어 게재 페이지에서 **[!UICONTROL Create]** 버튼을 사용하여 새 게재를 만듭니다.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Adobe Campaign 탐색기 사용 {#using-adobe-campaign-explorer}

Adobe Campaign 탐색기는 도구 모음 아이콘을 통해 액세스할 수 있습니다. 모든 Adobe Campaign 기능, 구성 화면 및 일부 플랫폼 요소에 대한 보다 자세한 보기에 액세스할 수 있습니다.

Adobe Campaign 탐색기에 대한 자세한 내용은 **Campaign v8(콘솔) 설명서**&#x200B;에서 다음 페이지를 참조하십시오.

* [Campaign 사용자 인터페이스 개요](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}

* [Campaign UI 설정](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [탐색기에서 폴더 및 보기 관리](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}


## 데이터 작업 {#work-with-data}

### 데이터 필터링 {#filters}

데이터 필터링은 데이터 세트를 특정 기준과 일치하는 레코드로만 좁히는 프로세스입니다. 그런 다음 이 하위 집합을 타겟팅된 작업(예: 업데이트 또는 대상 만들기) 또는 분석에 사용할 수 있습니다.

Campaign을 검색할 때 데이터가 목록에 표시됩니다. 기본 제공 필터를 적용하여 격리된 주소, 타깃팅되지 않은 수신자 또는 특정 기간 범위 또는 생성 날짜 내의 레코드와 같은 정의된 하위 집합에 빠르게 액세스할 수 있습니다. 또한 사용자 정의 필터를 만들고 나중에 사용할 수 있도록 저장하고 다른 Campaign 사용자와 공유할 수 있습니다.

**Campaign v8(콘솔) 설명서**&#x200B;에서 [필터에 액세스, 디자인 및 공유](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/audience/create-filters){target=_blank}하는 방법에 대해 알아봅니다.

### 데이터베이스 쿼리{#about-queries-in-campaign}

쿼리 도구는 애플리케이션의 다양한 수준에서 사용할 수 있으며, 대상 모집단, 고객을 세그먼트화하고 추적 로그를 추출 및 필터링하고 필터를 만드는 데 사용할 수 있습니다.

+++일반 쿼리 편집기 정보

**[!UICONTROL Tools > Generic query editor...]** 메뉴에서 액세스할 수 있는 전용 길잡이(일반 쿼리 편집기)를 제공합니다. 이 편집기를 사용하면 데이터베이스 쿼리에서 정보를 추출, 구성, 그룹화 및 정렬할 수 있습니다. 예를 들어 지정된 기간 동안 뉴스레터 링크를 n번 이상 클릭한 수신자를 검색할 수 있습니다.

일반 쿼리 편집기는 모든 쿼리 기능을 중앙 집중화합니다. 제한 필터를 만들고 저장하여 타겟팅 워크플로우의 쿼리 상자와 같은 다른 컨텍스트에서 재사용할 수 있습니다.

![쿼리 편집기에 액세스하여 테이블 선택](assets/query_editor_nveau_21.png)

+++

>[!BEGINTABS]

>[!TAB 데이터베이스 쿼리]

쿼리를 만드는 단계는 **[Campaign v8(콘솔) 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}**&#x200B;에 자세히 설명되어 있습니다.


[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/data/query/query-editor){target=_blank}


>[!TAB 워크플로우에 쿼리 추가]

**[Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}**&#x200B;에서 워크플로우 컨텍스트에서 쿼리 만들기와 관련된 주요 단계를 알아봅니다

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/automation/workflows/wf-activities/targeting-activities/query){target=_blank}

>[!TAB 필터 조건]

쿼리를 디자인하려면 쿼리 편집기에서 필터링 조건을 선택해야 합니다. 사용 가능한 기능 및 사용 사례는 **[Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}**&#x200B;에 자세히 설명되어 있습니다.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/data/query/filter-conditions){target=_blank}

>[!ENDTABS]

### 목록 관리 {#manage-and-customize-lists}

Campaign 클라이언트 콘솔에서 데이터가 목록에 표시됩니다. 이러한 목록을 필요에 맞게 조정할 수 있습니다. 예를 들어 열을 추가하고, 데이터를 필터링하고, 레코드를 카운트하고, 설정을 저장하고 공유할 수 있습니다.

**Campaign v8(콘솔) 설명서**&#x200B;에서 [목록을 관리하고 사용자 지정](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}하는 방법에 대해 알아봅니다.

### 열거 관리{#managing-enumerations}

열거형(항목별 목록이라고도 함)은 특정 필드를 채우는 데 사용할 수 있는 미리 정의된 값 목록입니다. 열거형을 사용하면 필드 값을 표준화하여 데이터 항목을 보다 일관되게 만들고 쿼리를 단순화할 수 있습니다.

정의된 값은 드롭다운 목록에 표시됩니다. 값을 직접 선택하거나 일치하는 항목을 제안하고 완료하는 예측 입력을 사용하여 입력할 수 있습니다. 일부 필드에는 사전 정의된 열거형이 포함되어 있으며, 필요한 경우 추가 열거형을 만들 수 있습니다.

**Adobe Campaign v8(콘솔) 설명서**&#x200B;에서 [열거형으로 작업](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}하는 방법에 대해 자세히 알아보세요.

## 튜토리얼 비디오 {#video}

이 비디오에서는 Campaign Classic 작업 영역에 대해 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)
