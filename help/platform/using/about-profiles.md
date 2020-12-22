---
solution: Campaign Classic
product: campaign
title: 프로필 기본 정보
description: 프로필 기본 정보
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 18%

---


# 프로필 기본 정보{#about-profiles}

프로필(고객, 잠재 고객, 뉴스레터 구독자 등) 은 Adobe Campaign 데이터베이스에 중앙 집중화됩니다. 프로필을 가져오고 이 데이터베이스를 빌드하는 데 사용할 수 있는 메커니즘은 웹 양식을 통한 온라인 수집, 텍스트 파일 수동 또는 자동 가져오기, 회사 데이터베이스 또는 기타 정보 시스템을 사용한 복제와 같이 다양합니다. Adobe Campaign을 사용하면 마케팅 내역, 구매 정보, 환경 설정, CRM 데이터 및 관련 PI 데이터를 통합 뷰에 통합하여 분석하고 조치를 취할 수 있습니다.

Adobe Campaign에서 수신자는 게재(전자 메일, SMS 등)를 보낼 타겟팅된 기본 프로필입니다. 데이터베이스에 저장된 수신자 데이터 덕분에 주어진 게재를 받을 대상을 필터링하고 게재 콘텐츠에 개인화 데이터를 추가할 수 있습니다. 데이터베이스에 다른 유형의 프로필이 있습니다. 다양한 용도로 디자인되어 있습니다. 예를 들어 최종 대상으로 전송되기 전에 시드 프로필을 테스트하여 게재를 테스트합니다.

![](assets/do-not-localize/how-to-video.png) [비디오의 프로파일 개념 이해](#create-profiles-video)

## 프로필 유형 {#profile-types}

Adobe Campaign을 사용하면 전체 라이프사이클에서 프로파일을 관리할 수 있습니다.만들기, 가져오기, 타깃팅, 작업 추적, 업데이트 등

각 프로파일은 데이터베이스 항목과 일치합니다. 개인 타깃팅, 자격 부여 및 추적에 필요한 모든 정보가 포함되어 있습니다.

스토리지 공간을 기반으로 프로파일을 식별할 수 있습니다. 즉, 프로필은 일치할 수 있습니다.수신자, 방문자, 운영자, 가입자, 잠재 고객 등

## 수신자 프로필 {#recipient-profiles}

배달 받는 사람은 데이터베이스에 연결된 정보를 포함하는 프로필로 저장됩니다.성, 이름, 주소, 구독, 배달 등 캠페인을 만들 때 단순 또는 고급 기준에 따라 기본에서 선택한 프로파일에 배달의 대상을 정의할 수 있습니다.

또한 프로필이 데이터베이스에 저장되지 않고 파일에 저장되는 수신자를 대상으로 하는 캠페인을 만들 수도 있습니다. 이를 &quot;외부&quot; 배달이라고 합니다. 이 유형의 배달에 대한 자세한 내용은 [이 페이지](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)를 참조하십시오.

수신자 프로필을 만드는 주요 방법은 다음과 같습니다.

* 그래픽 인터페이스 화면에 직접 입력,
* 수신자 목록 가져오기,
* 웹 양식을 통한 온라인 컬렉션

>[!NOTE]
>
>파일과 웹 양식을 가져오는 방법을 알아보려면 [일반 가져오기 및 내보내기](../../platform/using/generic-imports-and-exports.md)를 참조하십시오.

## 프로필 및 대상 {#profiles-and-targets}

**[!UICONTROL Profiles and targets]** 링크를 사용하면 Adobe Campaign 데이터베이스에 저장된 수신자를 표시할 수 있습니다. 새 수신자를 만들고, 기존 수신자를 편집하고, 해당 프로필에 액세스할 수 있습니다. 자세한 정보는 이 [페이지](../../platform/using/editing-a-profile.md)를 참조하십시오.

![](assets/d_ncs_user_interface_target_link.png)

또한 다음과 같은 액세스 권한을 제공합니다.

* lists;[목록 만들기 및 관리](../../platform/using/creating-and-managing-lists.md),
* 구독 서비스;[이 페이지](../../delivery/using/managing-subscriptions.md)를 참조하십시오.
* 웹 애플리케이션;[이 페이지](../../web/using/about-web-applications.md)를 참조하십시오.
* 수입 및 수출(직업);[일반 가져오기 및 내보내기](../../platform/using/generic-imports-and-exports.md) 참조,
* 타깃팅 워크플로우;[이 페이지](../../workflow/using/building-a-workflow.md#implementation-steps-)를 참조하십시오.

수신자 페이지에서는 프로파일에 대해 자주 수행하는 작업을 수행할 수 있습니다.편집, 업데이트, 추가, 삭제, 정렬.

고급 프로필 조작의 경우 Adobe Campaign 트리를 편집해야 합니다. 이렇게 하려면 Adobe Campaign 홈 페이지에서 **[!UICONTROL Explorer]** 링크를 클릭합니다.

기본적으로 수신자는 트리의 **[!UICONTROL Profiles and Targets > Recipients]** 노드에 저장됩니다. 이 보기뿐만 아니라 다음 보기에서 수신자를 만들 수 있습니다.

* 데이터베이스의 프로파일을 정렬 및 필터링합니다.[필터링 옵션](../../platform/using/filtering-options.md),
* 데이터베이스에서 프로파일을 이동, 복사 또는 삭제합니다.[프로필 관리](../../platform/using/managing-profiles.md),
* 업데이트 프로필;[데이터 업데이트](../../platform/using/updating-data.md),
* 받는 사람 내보내기[프로필 내보내기 및 가져오기](../../platform/using/exporting-and-importing-profiles.md),
* 수신자 그룹 만들기;[목록 만들기 및 관리](../../platform/using/creating-and-managing-lists.md)를 참조하십시오.

고급 기능 및 구성에 액세스하려면 **[!UICONTROL Explorer]** 아이콘을 클릭해야 합니다.

![](assets/d_ncs_user_interface01.png)

Adobe Campaign 탐색기의 일반 레이아웃은 [Adobe Campaign 탐색기 사용](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)에 있습니다.

>[!NOTE]
>
>Adobe Campaign 트리에서 **[!UICONTROL Profiles and targets > Recipients]** 링크를 클릭하여 이 목록의 고급 보기를 표시할 수도 있습니다. 목록 표시를 필요에 맞게 구성할 수 있습니다. 열을 추가하거나 삭제할 수 있고 열 순서를 정의할 수 있으며 데이터를 정렬할 수 있습니다. 목록 표시 구성은 [Adobe Campaign 탐색기 사용](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer)에 설명되어 있습니다.
>
>수신자 뷰를 정의할 수도 있습니다. 이 기능에 대한 자세한 내용은 [폴더 및 보기](../../platform/using/access-management.md#folders-and-views)를 참조하십시오.

## 활성 프로필 {#active-profiles}

활성 프로필은 청구 용도로 카운트되는 프로필입니다.

>[!NOTE]
>
>AWS에서 호스팅되고 빌드 8931의 Campaign Classic을 사용하는 경우 Campaign 컨트롤 패널에서 직접 인스턴스에 사용된 활성 프로필의 수를 모니터링할 수도 있습니다. 자세한 내용은 [Campaign 컨트롤 패널 설명서](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html)를 참조하십시오.
>
>활성 프로필 수는 **마케팅 인스턴스**&#x200B;에만 사용할 수 있습니다. 실행 인스턴스에는 사용할 수 없습니다. 즉, MID(mid 소싱) 및 RT(메시지 센터/실시간 메시징) 인스턴스입니다.

&quot;**프로필**&quot;은 정보 레코드를 의미합니다(예:최종 고객, 잠재 고객 또는 리드를 나타내는 쿠키 ID, 고객 ID, 모바일 식별자 또는 특정 채널과 관련된 기타 정보가 포함된 외부 테이블 또는 nmsRecipient 테이블의 레코드

청구에는 **active**&#x200B;인 프로파일만 포함됩니다. 지난 12개월 동안 채널을 통해 프로파일을 타깃팅하거나 커뮤니케이션한 경우 프로파일이 활성 상태로 간주됩니다.

배달 준비 중에 제외된 프로파일(분류 규칙, 격리)은 고려되지 않습니다. 여러 게재에서 타깃팅된 프로필은 한 번만 카운트됩니다.

>[!NOTE]
>
>페이스북과 트위터 채널은 고려되지 않습니다.

Campaign Standard **[!UICONTROL Administration > Campaign Management > Customer metrics]** 메뉴에서 **[!UICONTROL Number of active profiles]**&#x200B;에 대한 개요를 알 수 있습니다. 실제 개수는 **[!UICONTROL Number of active billing profiles]**(**[!UICONTROL billingActiveContactCount]**) [기술 워크플로우](../../workflow/using/about-technical-workflows.md)에 의해 수행되며, 매일 실행되고 **[!UICONTROL Customer metrics]** 메뉴에서 현재 기간 동안 기존 보고서에 새 데이터를 추가합니다. 각 기간은 12개월 동안 지속됩니다.

## 자습서 비디오 {#create-profiles-video}

프로필 데이터에 액세스하고, 프로필을 정렬 및 필터링하고, 프로필을 수동으로 만들고 관리하는 방법을 알아봅니다.

이 비디오에서는 Adobe Campaign Classic의 일반 데이터 보호 규정 준수에 대해서도 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.

**참조 항목**

* [캠페인의 개인 정보 관리](https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html)

* [대상 모집단 정의](../../delivery/using/define-the-right-audience.md)

* [워크플로우에서 쿼리 및 세그먼트 데이터 만들기](../../workflow/using/targeting-data.md)

* [대상 매핑 선택](../../delivery/using/selecting-a-target-mapping.md)

* [대상 정의 - 우수 사례](../../delivery/using/define-the-right-audience.md)
