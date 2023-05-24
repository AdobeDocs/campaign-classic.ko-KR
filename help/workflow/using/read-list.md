---
product: campaign
title: 목록 읽기
description: 목록 읽기 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 목록 읽기{#read-list}



워크플로우에서 처리되는 데이터는 미리(이전 세그먼테이션 또는 파일 업로드 후) 데이터를 준비하거나 구조화한 목록에서 가져올 수 있습니다.

다음 **[!UICONTROL Read list]** 활동을 사용하면 쿼리의 데이터와 같이 워크플로우 작업 테이블의 목록에서 데이터를 복사할 수 있습니다. 그런 다음 워크플로우 전체에서 액세스할 수 있습니다.

처리할 목록은 선택한 옵션과 다음에 정의된 매개 변수에 따라 스크립트로 계산되거나 동적으로 현지화되도록 명시적으로 지정할 수 있습니다. **[!UICONTROL Read list]** 활동.

![](assets/list_edit_select_option_01.png)

목록을 명시적으로 지정하지 않은 경우 템플릿으로 사용할 목록을 제공하여 해당 구조를 찾아야 합니다.

![](assets/s_advuser_list_template_select.png)

목록 선택이 구성되면 다음을 사용하여 필터를 추가할 수 있습니다 **[!UICONTROL Edit query]** 옵션을 사용하여 다음 워크플로우에 대해 모집단의 한 부분을 유지합니다.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>목록 읽기 활동에서 필터를 만들려면 관련 목록이 &quot;파일&quot; 유형이어야 합니다.

목록은 다음을 통해 Adobe Campaign에서 직접 만들 수 있습니다. **[!UICONTROL Profiles and Targets > Lists]** 홈 페이지 링크. 워크플로우에서 다음을 사용하여 만들 수도 있습니다. **[!UICONTROL List update]** 활동.

**예: 전송 주소 목록 제외**

다음 예에서는 이메일 주소 목록을 사용하여 이메일 게재 대상에서 제외할 수 있습니다.

![](assets/s_advuser_list_read_sample_1.png)

에 포함된 프로필 **새 연락처** 폴더는 게재 작업에 의해 타겟팅되어야 합니다. 대상에서 제외할 이메일 주소는 외부 목록에 저장됩니다. 이 예제에서는 이메일 주소에 대한 정보만 제외에 필요합니다.

1. 다음 **새 연락처** 폴더 선택 쿼리를 사용하면 선택한 프로필의 이메일 주소를 로드할 수 있어야 목록의 정보와 정렬할 수 있습니다.

   ![](assets/s_advuser_list_read_sample_0.png)

1. 여기에서는 목록이 **목록** 폴더 및 해당 레이블이 계산됩니다.

   ![](assets/s_advuser_list_read_sample_2.png)

1. 기본 대상에서 외부 목록의 이메일 주소를 제외하려면 제외 활동을 구성하고 다음을 지정해야 합니다. **새 연락처** 폴더에는 보관할 데이터가 포함되어 있습니다. 이 집합과 제외 활동의 다른 인바운드 집합 사이의 공동 데이터는 대상에서 삭제됩니다.

   ![](assets/s_advuser_list_read_sample_3.png)

   제외 규칙은 편집 도구의 중앙 섹션에 구성됩니다. 다음을 클릭합니다. **[!UICONTROL Add]** 버튼을 클릭하여 적용할 제외 유형을 정의합니다.

   활동의 수신 전환 수에 따라 여러 제외를 정의할 수 있습니다.

1. 다음에서 **[!UICONTROL Exclusion set]** 필드에서 **[!UICONTROL Read list]** 활동: 이 활동의 데이터는 기본 세트에서 제외됩니다.

   이 예제에서는 조인에 대한 제외가 있습니다. 목록에 포함된 데이터는 이메일 주소가 포함된 필드를 통해 기본 세트의 데이터와 조정됩니다. 조인을 구성하려면 을 선택합니다. **[!UICONTROL Joins]** 다음에서 **[!UICONTROL Change dimension]** 필드.

   ![](assets/s_advuser_list_read_sample_4.png)

1. 그런 다음 두 세트(소스 및 대상)에서 이메일 주소에 해당하는 필드를 선택합니다. 그러면 열이 연결되고 이메일 주소가 가져온 주소 목록에 있는 수신자는 대상에서 제외됩니다.
