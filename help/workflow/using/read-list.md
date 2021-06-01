---
product: campaign
title: 목록 읽기
description: 목록 읽기 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 목록 읽기{#read-list}

워크플로우에서 처리된 데이터는 이전 세그먼테이션이나 파일 업로드 후 데이터를 미리 준비하거나 구조화한 목록에서 가져올 수 있습니다.

**[!UICONTROL Read list]** 활동을 사용하면 쿼리의 데이터와 같은 데이터를 워크플로우 작업 테이블의 목록에서 복사할 수 있습니다. 그런 다음 워크플로우 전체에서 액세스할 수 있습니다.

처리할 목록을 명시적으로 지정하거나, 스크립트로 계산하거나, 동적으로 현지화할 수 있습니다. 이는 **[!UICONTROL Read list]** 활동에 정의된 옵션과 매개 변수에 따라 결정됩니다.

![](assets/list_edit_select_option_01.png)

목록을 명시적으로 지정하지 않은 경우 해당 구조를 찾기 위해 템플릿으로 사용할 목록을 제공해야 합니다.

![](assets/s_advuser_list_template_select.png)

목록 선택이 구성되면 **[!UICONTROL Edit query]** 옵션을 사용하여 필터를 추가하여 다음 워크플로우에 대한 모집단 중 하나를 유지할 수 있습니다.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>목록 읽기 활동에서 필터를 만들려면 관련 목록이 &quot;파일&quot; 유형이어야 합니다.

홈 페이지의 **[!UICONTROL Profiles and Targets > Lists]** 링크를 통해 Adobe Campaign에서 직접 목록을 만들 수 있습니다. 또한 **[!UICONTROL List update]** 활동을 사용하여 워크플로우에서 만들 수도 있습니다.

**예:보내기 주소 목록 제외**

다음 예제에서는 이메일 주소 목록을 사용하여 이메일 게재 타겟에서 제외할 수 있습니다.

![](assets/s_advuser_list_read_sample_1.png)

**새 연락처** 폴더에 포함된 프로필은 게재 작업에서 타겟팅해야 합니다. 대상에서 제외할 이메일 주소는 외부 목록에 저장됩니다. 이 예에서는 제외에 이메일 주소에 대한 정보만 필요합니다.

1. 목록에 있는 정보와 정렬을 사용하려면 **새 연락처** 폴더 선택 쿼리를 사용하여 선택한 프로필의 이메일 주소를 로드할 수 있어야 합니다.

   ![](assets/s_advuser_list_read_sample_0.png)

1. 여기에서 목록은 **목록** 폴더에 저장되며 해당 레이블이 계산됩니다.

   ![](assets/s_advuser_list_read_sample_2.png)

1. 외부 목록의 이메일 주소를 기본 대상에서 제외하려면 제외 활동을 구성하고 **새 연락처** 폴더에 유지할 데이터가 포함되도록 지정해야 합니다. 이 세트와 제외 활동에서 다른 인바운드 세트 간의 결합 데이터가 대상에서 삭제됩니다.

   ![](assets/s_advuser_list_read_sample_3.png)

   제외 규칙은 편집 도구의 중앙 섹션에서 구성됩니다. 적용할 제외 유형을 정의하려면 **[!UICONTROL Add]** 버튼을 클릭합니다.

   활동의 수신 전환 수에 따라 여러 제외를 정의할 수 있습니다.

1. **[!UICONTROL Exclusion set]** 필드에서 **[!UICONTROL Read list]** 활동을 선택합니다.이 활동의 데이터는 기본 집합에서 제외됩니다.

   이 예제에서는 조인에 대한 제외가 있습니다.목록에 포함된 데이터는 이메일 주소가 포함된 필드를 통해 기본 세트의 데이터와 조정됩니다. 조인을 구성하려면 **[!UICONTROL Change dimension]** 필드에서 **[!UICONTROL Joins]** 을 선택합니다.

   ![](assets/s_advuser_list_read_sample_4.png)

1. 그런 다음 두 세트의 이메일 주소에 해당하는 필드(소스 및 대상)를 선택합니다. 열이 연결되고 이메일 주소가 가져온 주소 목록에 있는 수신자는 대상에서 제외됩니다.
