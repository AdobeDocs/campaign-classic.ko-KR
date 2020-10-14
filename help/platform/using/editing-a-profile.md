---
title: 프로필 편집
seo-title: 프로필 편집
description: 프로필 편집
seo-description: null
page-status-flag: never-activated
uuid: ad3cd54e-b22f-4fae-8d2a-3e0d3e45fffb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 93dd29e8-cf0a-4010-a3cc-f68c52c0d9ef
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 5%

---


# 프로필 편집{#editing-a-profile}

프로필과 관련된 정보를 보려면 프로필 목록에서 해당 이름을 클릭합니다.

프로필 세부 정보가 새 탭에 표시됩니다.

![](assets/s_user_recipient_edit.png)

프로필에 대한 데이터는 탭으로 그룹화됩니다.

탭과 해당 컨텐츠는 구성 및 설치된 패키지에 따라 다릅니다.

>[!CAUTION]
>
>프로필 테이블의 필드와 관련된 XML 스키마 및 양식은 Adobe Campaign 트리의 **[!UICONTROL Administration > Configuration > Data schemas]** 노드를 통해 액세스합니다. 전문가 사용자만 이러한 스키마를 변경할 수 있습니다.
>
>For further information, refer to [this page](../../configuration/using/about-schema-edition.md).

## 일반 탭 {#general-tab}

이 화면은 선택한 프로필에 대한 모든 일반 데이터를 포함합니다. 특히 성, 이름, 이메일 주소, 이메일 수신 형식 등이 포함되어 있습니다. 다음과 같습니다.

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>이 **[!UICONTROL No longer contact (by any channel)]** 옵션을 선택하면 프로필이차단 목록에 있음을 의미합니다. 즉, 프로필은 연락하지 않기를 바란다고 표시했습니다(예: 뉴스레터에서 구독 취소 링크를 클릭해서). 이러한 지표는 더 이상 어떤 채널에서도 게재되지 않습니다(이메일, DM 등). 자세한 정보는 이 [페이지](../../delivery/using/understanding-quarantine-management.md)를 참조하십시오.

## 연락처 정보 탭 {#contact-information-tab}

이 화면은 선택한 프로필의 다이렉트 메일 주소를 포함합니다. 다음과 같습니다.

![](assets/s_ncs_user_profile_details_tab.png)

이 화면에는 주소의 품질 색인과 주소에 포함된 오류 수가 표시됩니다. 이 정보는 이전 배달 중에 발견된 오류 수를 기반으로 메일 운송업체가 직접 사용하며 수동으로 수정할 수 없습니다.

## 기타 탭 {#other-tab}

이 화면에는 요구 사항에 따라 개인화할 수 있는 사용자 정의 필드가 포함되어 있습니다. 아래와 같이 필드 이름을 변경하고 형식을 정의할 수도 **[!UICONTROL Field properties...]**&#x200B;있습니다.

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>필드 속성과 필드 추가에 대한 자세한 내용은 [이 페이지를 참조하십시오](../../configuration/using/new-field-wizard.md).

## 목록 탭 {#lists-tab}

이 화면에는 선택한 프로필이 속하는 그룹이 표시됩니다. 목록 **[!UICONTROL Add]** 에 프로필을 가입하려면 을 클릭합니다. 아이콘을 **[!UICONTROL Detail]** 클릭하여 선택한 목록에 설명 및 프로필 목록을 표시합니다.

![](assets/s_ncs_user_profile_groups_tab_details.png)

자세한 내용은 목록 [만들기 및 관리를 참조하십시오](../../platform/using/creating-and-managing-lists.md).

## 구독 탭 {#subscriptions-tab}

이 화면에는 프로필이 가입한 정보 서비스가 포함되어 있습니다.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

이 **[!UICONTROL Detail]** 단추는 선택한 구독의 속성을 표시합니다. 이 **[!UICONTROL Add]** 단추는 새 구독을 수동으로 추가하는 데 사용됩니다.

자세한 정보는 이 [페이지](../../delivery/using/managing-subscriptions.md)를 참조하십시오.

## 배달 탭 {#deliveries-tab}

이 화면은 선택한 프로필에 대한 배달 로그를 표시합니다. 또한 모든 채널을 통해 프로파일에 명시된 배달 작업의 레이블, 날짜 및 상태를 표시할 수도 있습니다.

![](assets/s_ncs_user_profile_delivery_tab.png)

## 추적 탭 {#tracking-tab}

이 화면에서는 선택한 프로필에 대한 추적 로그를 볼 수 있습니다. 이 정보는 배달 후 프로필 동작을 추적하는 데 사용됩니다.

![](assets/s_ncs_user_profile_tracking_tab.png)

이 탭에는 배달에서 추적된 모든 URL의 누적 합계가 표시됩니다.

목록은 구성할 수 있으며 일반적으로 다음을 포함합니다.클릭한 URL, 클릭 날짜 및 시간, URL이 포함된 문서.

>[!NOTE]
>
>추적 기능에 대한 자세한 내용은 [이 페이지를 참조하십시오](../../delivery/using/monitoring-a-delivery.md).

