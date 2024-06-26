---
product: campaign
title: 데이터 업데이트 중
description: 데이터 업데이트 중
feature: Data Management
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 1%

---

# 데이터 업데이트{#updating-data}

>[!NOTE]
>
>이 페이지는 기본 인증을 사용하여 Campaign에 연결하는 운영자에만 적용됩니다.

수신자의 프로필에 연결된 데이터는 수동 또는 자동으로 업데이트할 수 있습니다.

## 자동 업데이트 설정 {#setting-up-an-automatic-update}

워크플로우를 통해 자동 업데이트를 구성할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/update-data.md)을 참조하십시오.

## 대량 업데이트 수행 {#performing-a-mass-update}

수동 업데이트를 수행하려면 선택한 수신자를 마우스 오른쪽 단추로 클릭하여 **[!UICONTROL Actions]** 바로 가기 메뉴 또는 **[!UICONTROL Actions]** 아이콘.

![](assets/s_ncs_user_action_icon.png)

업데이트에는 수신자 집합에 대한 대량 업데이트와 두 프로필 간의 데이터 병합의 두 가지 유형이 있습니다. 각 작업에 대해 마법사를 사용하여 업데이트를 구성할 수 있습니다.

### 대량 업데이트 {#mass-update}

대량 업데이트의 경우 다음을 사용하십시오. **[!UICONTROL Action > Mass update of selected lines...]**. 마법사는 업데이트를 구성하고 실행하는 데 도움이 됩니다.

마법사의 첫 번째 단계는 업데이트할 필드를 지정하는 것입니다.

마법사의 왼쪽 섹션에 사용 가능한 필드 목록이 표시됩니다. 사용 **[!UICONTROL Find]** 필드 : 이러한 필드의 검색을 실행합니다. 누르기 **입력** 키를 눌러 목록을 찾습니다. 항목과 일치하는 필드 이름은 아래와 같이 굵게 표시됩니다.

업데이트할 필드를 두 번 클릭하여 마법사의 오른쪽 섹션에 표시합니다.

![](assets/s_ncs_user_update_wizard01_1.png)

오류가 발생하는 경우 **[!UICONTROL Delete]** 업데이트할 필드 목록에서 필드를 삭제하는 단추입니다.

업데이트할 프로필에 적용할 값을 선택하거나 입력합니다.

![](assets/s_ncs_user_update_wizard01_12.png)

다음을 클릭할 수 있습니다. **[!UICONTROL Distribution of values]** 현재 폴더에 있는 수신자(업데이트의 영향을 받는 수신자만 해당)에 대해 선택한 필드의 값 분포를 표시합니다.

![](assets/s_ncs_user_update_wizard01_2.png)

필터를 정의하여 이 창의 값 분포를 표시하거나 현재 폴더를 수정하여 다른 폴더의 값 분포를 표시할 수 있습니다. 이는 읽기 전용 작업이며 정의 중인 업데이트 구성에는 영향을 주지 않습니다.

![](assets/s_ncs_user_update_wizard01_3.png)

이 창을 닫고 **[!UICONTROL Next]** 두 번째 업데이트 마법사 단계를 표시합니다. 이 단계에서는 다음을 클릭하여 업데이트를 시작할 수 있습니다. **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

업데이트 실행에 관한 정보가 마법사의 위쪽 섹션에 표시됩니다.

다음 **[!UICONTROL Stop]** 업데이트를 취소할 수 있지만 특정 레코드가 업데이트되었을 수 있으며 프로세스를 중지해도 이러한 업데이트가 취소되지 않습니다. 진행률 표시줄에는 작업이 얼마나 진행되었는지 표시됩니다.

### 데이터 병합 {#merge-data}

선택 **[!UICONTROL Merge selected lines...]** 두 수신자 프로필의 병합을 시작합니다. 옵션을 선택하기 전에 병합할 프로필을 선택해야 합니다. 마법사를 사용하여 병합을 구성하고 시작합니다.

마법사는 하나 이상의 소스 프로필에서 완료된 각 필드에 대해 검색할 값을 표시합니다. 병합할 프로필의 하나 이상의 필드에 다른 값이 있는 경우 **[!UICONTROL List of conflicts]** 섹션. 그런 다음 다음 다음 예와 같이 목록 아래의 라디오 단추를 사용하여 기본 프로파일을 선택할 수 있습니다.

![](assets/s_ncs_user_merge_wizard01_1.png)

클릭 **[!UICONTROL Compute]** 을 클릭하여 선택 결과를 표시합니다.

![](assets/s_ncs_user_merge_wizard01_2.png)

다음 확인: **[!UICONTROL Result]** 창의 두 섹션 열 및 **[!UICONTROL Finish]** 병합을 실행합니다.

## 데이터 내보내기 {#exporting-data}

목록의 콘텐츠를 내보낼 수 있습니다. 내보내기를 구성하고 실행하려면 다음 작업을 수행하십시오.

1. 내보낼 레코드를 선택합니다.
1. 마우스 오른쪽 단추를 클릭하고 선택 **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. 그런 다음 추출할 데이터를 선택합니다. 기본적으로 표시되는 모든 열이 출력 열에 추가됩니다.

   ![](assets/s_ncs_user_export_list_start.png)

   내보내기 마법사를 구성하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [이 섹션](../../platform/using/executing-export-jobs.md).

## 서비스 구독 {#subscribing-to-a-service}

대부분의 경우 수신자는에 설명된 대로 전용 랜딩 페이지를 통해 뉴스레터를 구독합니다 [이 섹션](../../delivery/using/managing-subscriptions.md). 단, 필터링된 수신자의 프로필은 서비스(뉴스레터 또는 바이럴 서비스)에 수동으로 가입할 수 있습니다. 방법은 다음과 같습니다.

1. 구독할 수신자를 선택하고 마우스 오른쪽 단추를 클릭합니다.
1. **[!UICONTROL Actions > Subscribe selection to a service]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. 원하는 서비스를 선택하고 **[!UICONTROL Next]**:

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >이 편집기를 사용하면 새 서비스를 만들 수 있습니다. **[!UICONTROL Create]** 단추를 클릭합니다.

1. 다음을 수행할 수 있습니다. **[!UICONTROL Send a confirmation message]** 수신자에게. 이 메시지의 내용은 선택한 서비스에 연결된 구독 시나리오에서 구성할 수 있습니다.
1. 다음을 클릭합니다. **[!UICONTROL Start]** 구독 프로세스를 실행하는 단추입니다.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

창의 위쪽 섹션에서 실행 프로세스를 모니터링할 수 있습니다. 다음 **[!UICONTROL Stop]** 버튼을 사용하면 프로세스를 중지할 수 있습니다. 그러나 이미 처리된 수신자는 구독됩니다.

을(를) 선택 취소하면 **[!UICONTROL Do not keep a trace of this job in the database]** 옵션을 선택하면 이 프로세스에 대한 정보가 저장될 실행 폴더를 선택(또는 생성)할 수 있습니다.

프로세스를 확인하려면 **[!UICONTROL Subscriptions]** 이 작업과 관련된 수신자 프로필의 탭 또는 **[!UICONTROL Subscriptions]** 탭을 통해 액세스함 **[!UICONTROL Profiles and Targets > Services and Subscriptions]** 노드.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>정보 서비스 만들기 및 구성에 대한 자세한 내용은 [이 페이지](../../delivery/using/managing-subscriptions.md).
