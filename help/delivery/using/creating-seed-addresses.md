---
product: campaign
title: 시드 주소 만들기
description: 시드 주소를 만들고 사용하는 방법을 알아봅니다
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 시드 주소 만들기{#creating-seed-addresses}

![](../../assets/common.svg)

시드 주소는 표준 프로필 및 타겟을 통해 관리되지 않고 Adobe Campaign 계층 **[!UICONTROL Resources > Campaign management > Seed addresses]** 의 전용 노드에서 관리됩니다.

시드 주소를 구성하기 위해 하위 폴더를 만들 수 있습니다. 이렇게 하려면 **[!UICONTROL Seed addresses]** 노드를 마우스 오른쪽 버튼으로 클릭하고 **[!UICONTROL Create a new 'Seed addresses' folder]** 를 선택합니다. 하위 폴더의 이름을 지정한 다음 **[!UICONTROL Enter]** 키를 눌러 유효성을 확인합니다. 이제 시드 주소를 이 하위 폴더에 만들거나 복사할 수 있습니다. 자세한 내용은 [주소 정의](#defining-addresses)를 참조하십시오.

또한 Adobe Campaign을 사용하면 관련 게재 및 캠페인의 특정 요구 사항에 따라 게재 또는 캠페인으로 가져와서 채택하는 시드 주소 템플릿을 만들 수 있습니다. [시드 주소 템플릿 만들기](#creating-seed-address-templates)를 참조하십시오.

## 주소 정의 {#defining-addresses}

시드 주소를 만들려면 아래 단계를 수행하십시오.

1. 시드 주소 목록 위에 있는 **[!UICONTROL New]** 단추를 클릭합니다.
1. **[!UICONTROL Recipient]** 탭의 일치 필드에 주소에 연결된 데이터를 입력합니다. 사용 가능한 필드는 게재 수신자 프로필(nms:recipient table)의 표준 필드에 해당합니다. 이름, 이름, 이메일 등

   >[!NOTE]
   >
   >주소의 레이블은 정의한 이름과 이름으로 자동으로 입력됩니다.
   >
   >시드 주소를 만들 때 각 탭의 모든 필드를 입력할 필요는 없습니다. 누락된 개인화 요소는 전달 중에 임의로 입력됩니다.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. **[!UICONTROL Seed fields]** 탭에서 분석 단계(**[!UICONTROL nms:broadLog]** 테이블) 동안 게재 로그에 삽입할 값을 입력합니다.

1. **[!UICONTROL Additional data]** 탭에서 데이터 관리 워크플로우에서 생성된 게재에 사용되는 개인화 데이터를 입력하고 특정 값을 지정할 수 있습니다.

   >[!NOTE]
   >
   >추가 대상 데이터가 **[!UICONTROL Enrichment]** 활동에서 &#39;@&#39;로 시작하는 별칭으로 정의되었는지 확인하십시오. 그렇지 않으면 게재 활동에서 시드 주소와 함께 제대로 사용할 수 없습니다.

## 시드 주소 템플릿 만들기 {#creating-seed-address-templates}

가져올 주소 템플릿을 만들고 각 게재에 대해 수정할 수 있는 주소 템플릿을 만들려면 새 시드 주소를 정의할 때와 동일합니다. 유일한 차이점은 시드 주소 템플릿 주소를 &#39;템플릿&#39; 유형 폴더에 저장해야 한다는 것입니다.

템플릿 폴더를 정의하려면 다음 프로세스를 적용합니다.

1. 새 **[!UICONTROL Seed addresses]** 유형 폴더를 만들고 폴더를 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL Properties...]** 을 선택합니다.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. **[!UICONTROL Restriction]** 탭을 클릭하고 다음 필터링 조건을 추가합니다. **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   이제 이 폴더에 저장된 주소를 주소 템플릿으로 사용할 수 있습니다. 게재 또는 캠페인으로 가져와서 관련된 게재 및 캠페인의 특정 요구 사항에 따라 조정할 수 있습니다([시드 주소 추가](adding-seed-addresses.md) 참조).
