---
product: campaign
title: 프로필 편집
description: 프로필 편집
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 5%

---

# 프로필 편집{#editing-a-profile}



프로필과 관련된 정보를 보려면 프로필 목록에서 해당 이름을 클릭합니다.

프로필 세부 사항이 새 탭에 표시됩니다.

![](assets/s_user_recipient_edit.png)

프로필에 대한 데이터는 탭으로 그룹화됩니다.

탭과 해당 콘텐츠는 구성 및 설치된 패키지에 따라 다릅니다.

>[!CAUTION]
>
>프로필 테이블의 필드와 관련된 XML 스키마 및 양식은 **[!UICONTROL Administration > Configuration > Data schemas]** Adobe Campaign 트리의 노드입니다. 전문가 사용자만 이러한 스키마를 변경할 수 있습니다.
>
>자세한 내용은 다음을 참조하십시오. [이 페이지](../../configuration/using/about-schema-edition.md).

## 일반 탭 {#general-tab}

이 화면에는 선택한 프로필에 대한 모든 일반 데이터가 포함되어 있습니다. 특히 성, 이름, 이메일 주소, 이메일 수신 형식 등을 포함하고 있다. 다음과 같습니다.

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>다음의 경우 **[!UICONTROL No longer contact (by any channel)]** 옵션을 선택하면 프로필이 차단 목록에 추가하다임을 의미합니다. 즉, 프로필이 (예를 들어, 뉴스레터에서 구독 취소 링크를 클릭하여) 연락하지 않겠다는 의사를 표현했습니다. 더 이상 모든 채널(이메일, DM 등)의 게재가 타겟팅하지 않습니다. 자세한 정보는 이 [페이지](../../delivery/using/understanding-quarantine-management.md)를 참조하십시오.

## 연락처 정보 탭 {#contact-information-tab}

이 화면에는 선택한 프로필의 DM 주소가 포함됩니다. 다음과 같습니다.

![](assets/s_ncs_user_profile_details_tab.png)

이 화면에는 주소의 품질 인덱스와 주소에 포함된 오류 수가 표시됩니다. 이 정보는 이전 게재 중 발견된 오류 수를 기반으로 하여 통신사에서 직접 사용되며 수동으로 수정할 수 없습니다.

## 기타 탭 {#other-tab}

이 화면에는 요구 사항에 따라 개인화할 수 있는 사용자 정의 필드가 포함되어 있습니다. 를 통해 필드의 이름을 변경하고 해당 형식을 정의할 수도 있습니다. **[!UICONTROL Field properties...]**, 아래와 같이 표시됩니다.

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>필드 속성 및 필드 추가에 대한 자세한 내용은 [이 페이지](../../configuration/using/new-field-wizard.md).

## 목록 탭 {#lists-tab}

이 화면에는 선택한 프로필이 속한 그룹이 표시됩니다. 클릭 **[!UICONTROL Add]** 을 클릭하여 목록에 프로필을 구독합니다. 클릭 **[!UICONTROL Detail]** 선택한 목록에 설명 및 프로필 목록을 표시합니다.

![](assets/s_ncs_user_profile_groups_tab_details.png)

자세한 내용은 다음을 참조하십시오. [목록 만들기 및 관리](../../platform/using/creating-and-managing-lists.md).

## 구독 탭 {#subscriptions-tab}

이 화면에는 프로필이 구독한 정보 서비스가 포함되어 있습니다.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

다음 **[!UICONTROL Detail]** 버튼은 선택한 구독의 속성을 표시합니다. 다음 **[!UICONTROL Add]** 버튼은 새 구독을 수동으로 추가하는 데 사용됩니다.

자세한 정보는 이 [페이지](../../delivery/using/managing-subscriptions.md)를 참조하십시오.

## 게재 탭 {#deliveries-tab}

이 화면에는 선택한 프로필에 대한 게재 로그가 표시됩니다. 모든 채널을 통해 프로필에 지정된 게재 작업의 레이블, 날짜 및 상태를 표시할 수도 있습니다.

![](assets/s_ncs_user_profile_delivery_tab.png)

## 추적 탭 {#tracking-tab}

이 화면에서는 선택한 프로필에 대한 추적 로그를 볼 수 있습니다. 이 정보는 게재 후 프로필 동작을 추적하는 데 사용됩니다.

![](assets/s_ncs_user_profile_tracking_tab.png)

이 탭은 게재에서 추적된 모든 URL의 누적 합계를 보여줍니다.

목록은 구성할 수 있으며, 일반적으로 다음과 같은 항목이 포함됩니다. 클릭한 URL, 클릭한 날짜 및 시간, URL이 포함된 문서.

>[!NOTE]
>
>추적 기능에 대한 자세한 내용은 다음을 참조하십시오. [이 페이지](../../delivery/using/delivery-dashboard.md).
