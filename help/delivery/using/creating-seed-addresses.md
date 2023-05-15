---
product: campaign
title: 시드 주소 만들기
description: 시드 주소를 만들고 사용하는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 시드 주소 만들기{#creating-seed-addresses}



시드 주소는 표준 프로필 및 타겟을 통해 관리되지 않고 Adobe Campaign 계층 구조의 전용 노드에서 관리됩니다 **[!UICONTROL Resources > Campaign management > Seed addresses]**.

시드 주소를 구성하기 위해 하위 폴더를 만들 수 있습니다. 이렇게 하려면 **[!UICONTROL Seed addresses]** 노드 및 선택 **[!UICONTROL Create a new 'Seed addresses' folder]**. 하위 폴더 이름을 지정한 다음 키를 누릅니다 **[!UICONTROL Enter]** 유효성을 검사하려면 다음을 수행하십시오. 이제 시드 주소를 이 하위 폴더에 만들거나 복사할 수 있습니다. 자세한 내용은 [주소 정의](#defining-addresses).

또한 Adobe Campaign을 사용하면 관련 게재 및 캠페인의 특정 요구 사항에 따라 게재 또는 캠페인으로 가져와서 채택하는 시드 주소 템플릿을 만들 수 있습니다. 을(를) 참조하십시오. [시드 주소 템플릿 만들기](#creating-seed-address-templates).

## 주소 정의 {#defining-addresses}

시드 주소를 만들려면 아래 단계를 수행하십시오.

1. 을(를) 클릭합니다. **[!UICONTROL New]** 시드 주소 목록 위의 단추.
1. 주소 연결된 데이터를 페이지의 **[!UICONTROL Recipient]** 탭. 사용 가능한 필드는 게재 수신자 프로필(nms:recipient table)의 표준 필드에 해당합니다. 이름, 이름, 이메일 등

   >[!NOTE]
   >
   >주소의 레이블은 정의한 이름과 이름으로 자동으로 입력됩니다.
   >
   >시드 주소를 만들 때 각 탭의 모든 필드를 입력할 필요가 없습니다. 누락된 개인화 요소가 게재 분석 중에 임의로 입력됩니다.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. 에서 **[!UICONTROL Address fields]** 탭에서 분석 단계(에서) 동안 게재 로그에 삽입할 값을 입력합니다. **[!UICONTROL nms:broadLog]** 테이블).

1. 에서 **[!UICONTROL Additional data]** 탭에서 데이터 관리 워크플로우에서 만든 게재에 사용되는 개인화 데이터를 입력하고 특정 값을 지정할 데이터를 입력합니다.

   >[!NOTE]
   >
   >추가 대상 데이터가 **[!UICONTROL Enrichment]** 활동. 그렇지 않으면 게재 활동에서 시드 주소와 함께 제대로 사용할 수 없습니다.

## 시드 주소 템플릿 만들기 {#creating-seed-address-templates}

가져올 주소 템플릿을 만들고 각 게재에 대해 수정할 수 있는 주소 템플릿을 만들려면 새 시드 주소를 정의할 때와 동일합니다. 유일한 차이점은 시드 주소 템플릿 주소를 &#39;템플릿&#39; 유형 폴더에 저장해야 한다는 것입니다.

템플릿 폴더를 정의하려면 다음 프로세스를 적용합니다.

1. 새 만들기 **[!UICONTROL Seed addresses]** 유형 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. 을(를) 클릭합니다. **[!UICONTROL Restriction]** 탭하고 다음 필터링 조건을 추가합니다. **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   이제 이 폴더에 저장된 주소를 주소 템플릿으로 사용할 수 있습니다. 게재 또는 캠페인으로 가져와서 관련된 게재 및 캠페인의 특정 요구 사항에 따라 조정할 수 있습니다(참조) [시드 주소 추가](adding-seed-addresses.md)).
