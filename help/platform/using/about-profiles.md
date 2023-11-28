---
product: campaign
title: 프로필 시작
description: Adobe Campaign에서 프로필 작업
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 16%

---

# 프로필 시작{#about-profiles}



프로필은 Adobe Campaign 데이터베이스에 중앙 집중화됩니다. 프로필을 가져오고 이 데이터베이스를 빌드하는 데 사용할 수 있는 메커니즘은 웹 양식을 통한 온라인 수집, 텍스트 파일 수동 또는 자동 가져오기, 회사 데이터베이스 또는 기타 정보 시스템을 사용한 복제와 같이 다양합니다. Adobe Campaign을 사용하면 마케팅 기록, 구매 정보, 환경 설정, CRM 데이터 및 관련 PI 데이터를 통합 보기에 통합하여 분석하고 조치를 취할 수 있습니다.

&quot;**프로필**&quot;는 최종 고객, 잠재 고객 또는 리드를 나타내는 정보 기록(예: 쿠키 ID, 고객 ID, 모바일 식별자 또는 특정 채널과 관련된 기타 정보가 포함된 외부 테이블 또는 nmsRecipient 테이블의 레코드)을 의미합니다.

Adobe Campaign에서 수신자는 게재(전자 메일, SMS 등)를 보낼 타겟팅된 기본 프로필입니다. 데이터베이스에 저장된 수신자 데이터를 사용하면 지정된 게재를 받을 대상을 필터링하고 게재 콘텐츠에 개인화 데이터를 추가할 수 있습니다. 데이터베이스에 다른 유형의 프로필이 있습니다. 다양한 용도로 디자인되어 있습니다. 예를 들어 최종 대상으로 전송되기 전에 시드 프로필을 테스트하여 게재를 테스트합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 프로필의 개념 이해](#create-profiles-video)

## 프로필 유형 {#profile-types}

Adobe Campaign을 사용하면 생성, 가져오기, 타깃팅, 작업 추적, 업데이트 등 전체 라이프사이클에서 프로필을 관리할 수 있습니다.

각 프로필은 데이터베이스 항목과 일치합니다. 여기에는 개인에 대한 타겟팅, 자격 부여 및 추적에 필요한 모든 정보가 포함됩니다.

저장 공간을 기반으로 프로필을 식별할 수 있습니다. 이는 프로필이 수신자, 방문자, 운영자, 구독자, 잠재 고객 등과 일치할 수 있음을 의미합니다.

## 수신자 프로필 {#recipient-profiles}

게재 수신자는 데이터베이스에 성, 이름, 주소, 구독, 게재 등 연결된 정보가 포함된 프로필로 저장됩니다. 캠페인을 만들 때 단순 또는 고급 기준에 따라 베이스의 프로필 선택에 대한 게재 대상을 정의할 수 있습니다.

또한 프로필이 데이터베이스가 아닌 파일에 저장된 수신자를 대상으로 하는 캠페인을 만들 수도 있습니다. 이를 &quot;외부&quot; 게재라고 합니다. 이 유형의 게재에 대한 자세한 내용은 [이 페이지](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

수신자 프로필을 만드는 주요 방법은 다음과 같습니다.

* 그래픽 인터페이스 화면에 직접 입력,
* 수신자 목록 가져오기,
* 웹 양식을 통한 온라인 수집

>[!NOTE]
>
>파일 및 웹 양식을 가져오는 방법을 알아보려면 다음을 참조하십시오. [일반 가져오기 및 내보내기](../../platform/using/get-started-data-import-export.md).

## 프로필 및 대상 {#profiles-and-targets}

다음 **[!UICONTROL Profiles and targets]** 링크를 사용하여 Adobe Campaign 데이터베이스에 저장된 수신자를 표시할 수 있습니다. 새 수신자를 만들고 기존 수신자를 편집한 다음 해당 프로필에 액세스할 수 있습니다. 자세한 정보는 이 [페이지](../../platform/using/editing-a-profile.md)를 참조하십시오.

![](assets/d_ncs_user_interface_target_link.png)

또한 다음에 대한 액세스 권한을 제공합니다.

* 목록 - [자세히 알아보기](../../platform/using/creating-and-managing-lists.md)
* 구독 서비스 - [자세히 알아보기](../../delivery/using/managing-subscriptions.md)
* 웹 애플리케이션 - [자세히 알아보기](../../web/using/about-web-applications.md)
* 가져오기 및 내보내기(작업) - [자세히 알아보기](../../platform/using/about-generic-imports-exports.md)
* 타겟팅 워크플로우 - [자세히 알아보기](../../workflow/using/building-a-workflow.md#implementation-steps-)

수신자 페이지에서는 프로필에 대해 편집, 업데이트, 추가, 삭제, 정렬 등의 작업을 자주 수행할 수 있습니다.

고급 프로필 조작의 경우 Adobe Campaign 트리를 편집해야 합니다. 이렇게 하려면 **[!UICONTROL Explorer]** Adobe Campaign 홈 페이지의 링크.

기본적으로 수신자는 **[!UICONTROL Profiles and Targets > Recipients]** 트리의 노드. 이 보기에서 수신자를 만들 수 있을 뿐만 아니라 다음과 같은 작업도 수행할 수 있습니다.

* 데이터베이스의 프로필 정렬 및 필터링 - [자세히 알아보기](../../platform/using/filtering-options.md)
* 데이터베이스에서 프로필 이동, 복사 또는 삭제 - [자세히 알아보기](../../platform/using/managing-profiles.md),
* 프로필 업데이트 - [자세히 알아보기](../../platform/using/updating-data.md)
* 수신자 내보내기 - [자세히 알아보기](../../platform/using/exporting-and-importing-profiles.md)
* 수신자 그룹 만들기 - [자세히 알아보기](../../platform/using/creating-and-managing-lists.md)

고급 기능 및 구성에 액세스하려면 **[!UICONTROL Explorer]** 아이콘.

![](assets/d_ncs_user_interface01.png)

Adobe Campaign 탐색기의 일반 레이아웃은에 표시되어 있습니다. [이 페이지](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>Adobe Campaign 트리에서 다음을 클릭하여 이 목록의 고급 보기를 표시할 수도 있습니다. **[!UICONTROL Profiles and targets > Recipients]** 링크를 클릭합니다. 사용자의 요구 사항에 맞게 목록 표시를 구성할 수 있습니다. 열을 추가 또는 삭제하고, 열 순서를 정의하고, 데이터를 정렬하는 등의 작업을 수행할 수 있습니다. 목록 표시 구성은에 설명되어 있습니다. [이 페이지](../../platform/using/adobe-campaign-ui-lists.md).
>
>수신자 보기를 정의할 수도 있습니다. 이 기능에 대한 자세한 내용은 [이 섹션](../../platform/using/access-management-folders.md).

## 활성 프로필 {#active-profiles}

활성 프로필은 청구 용도로 계산되는 프로필입니다.

청구는 다음 프로필에만 관련됩니다. **활성**. 지난 12개월 동안 어떤 채널을 통해 프로필을 타겟팅하거나 통신한 경우 프로필이 활성 상태로 간주됩니다.

여러 게재에서 타겟팅한 프로필은 한 번만 카운트됩니다.

>[!NOTE]
>
>Facebook 및 X(이전의 Twitter) 채널은 고려되지 않습니다.

다음에 대한 활성 프로필 수를 사용할 수 있습니다. **마케팅 인스턴스** 만 해당. 실행 인스턴스에는 사용할 수 없습니다. 즉, MID(중간 소싱) 및 RT(메시지 센터/실시간 메시징) 인스턴스를 의미합니다.

>[!NOTE]
>
>Campaign Campaign 컨트롤 패널에서 직접 인스턴스의 활성 프로필 수를 모니터링할 수도 있습니다. 자세한 내용은 [Campaign 컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html).

## 튜토리얼 비디오 {#create-profiles-video}

프로필 데이터에 액세스하고, 프로필을 정렬 및 필터링하고, 프로필을 수동으로 만들고 관리하는 방법을 알아봅니다.

이 비디오에서는 Adobe Campaign Classic의 일반 데이터 보호 규정 준수에 대해서도 설명합니다.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).

**참조 항목**

* [Campaign의 개인정보 관리](https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html)

* [대상 모집단 정의](../../delivery/using/define-the-right-audience.md)

* [워크플로우에서 쿼리 및 세그먼트 데이터 만들기](../../workflow/using/targeting-data.md)

* [대상 매핑 선택](../../delivery/using/selecting-a-target-mapping.md)

* [대상자 정의 - 모범 사례](../../delivery/using/define-the-right-audience.md)
