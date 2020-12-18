---
solution: Campaign Classic
product: campaign
title: 시드 주소 추가
description: 시드 주소 추가
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 5%

---


# 시드 주소 추가{#adding-seed-addresses}

## 배달 {#seed-addresses-in-a-delivery}의 시드 주소

배달을 위한 특정 시드 주소를 추가하려면 **[!UICONTROL To]** 링크를 클릭한 다음 **[!UICONTROL Seed addresses]** 탭을 선택합니다.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

세 가지 삽입 모드를 사용할 수 있습니다.

1. 단일 시드 주소를 입력합니다.

   이렇게 하려면 **[!UICONTROL Add]** 단추를 클릭하고 주소 필드의 내용을 정의합니다. 각 주소에 대해 반복합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address)을 참조하십시오.

1. 주소 템플릿을 가져와 필요에 맞게 변경할 수 있습니다.

   이렇게 하려면 **[!UICONTROL Import seed templates...]** 링크를 클릭하고 주소 템플릿이 포함된 폴더를 선택합니다. 자세한 내용은 [시드 주소 템플릿 만들기](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates)를 참조하십시오.

   필요한 경우 주소를 두 번 클릭하거나 **[!UICONTROL Detail...]** 단추를 클릭하여 각 주소의 컨텐츠를 조정할 수 있습니다.

1. 삽입할 컨트롤 주소를 동적으로 선택하는 조건을 만듭니다.

   이렇게 하려면 **[!UICONTROL Edit the dynamic condition...]** 링크를 클릭한 다음 시드 주소 선택 매개 변수를 입력합니다. 예를 들어 특정 폴더에 포함된 모든 시드 주소 또는 조직의 특정 부서에 속하는 시드 주소를 포함할 수 있습니다.

   이 섹션의 예는 다음과 같습니다.[사용 사례:기준](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)에서 시드 주소 선택

>[!NOTE]
>
>이 옵션은 사용된 받는 사람 테이블이 기본 **nms:recipient** 테이블이 아니며 Adobe Campaign의 **[!UICONTROL Deliverability]** 모듈과 함께 제공된 받은 받은 편지함 렌더링 기능을 사용하는 경우에 사용됩니다.
>
>자세한 내용은 [외부 수신자 테이블 사용](../../delivery/using/using-an-external-recipient-table.md) 및 [받은 편지함 렌더링](../../delivery/using/inbox-rendering.md)에 있는 설명서를 참조하십시오.

배달의 경우 추출 파일에 주소를 삽입하는 방법을 사용자 정의할 수도 있습니다. 기본적으로 출력 파일의 정렬 순서에 삽입되지만 파일의 끝이나 시작 부분에 삽입하거나 기본 대상의 수신자 사이에 임의로 삽입할 수 있습니다.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## 캠페인 {#seed-addresses-in-a-campaign}의 시드 주소

캠페인 타겟에 시드 주소를 추가하려면 작업을 선택하고 **[!UICONTROL Edit]** 탭을 클릭합니다.

**[!UICONTROL Advanced campaign settings...]** 링크를 클릭한 다음 아래와 같이 **[!UICONTROL Seed addresses]** 탭을 클릭합니다.

![](assets/s_ncs_user_edit_op_addresses_tab.png)

캠페인에서 삽입된 시드 주소는 캠페인의 각 게재 대상에 추가됩니다.
