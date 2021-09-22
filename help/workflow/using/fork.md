---
product: campaign
title: 포크
description: 포크 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 1113afb573bad958ec7cc2cf008f71c8e751e8f9
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 포크{#fork}

![](../../assets/common.svg)

**[!UICONTROL Fork]** 활동을 사용하여 여러 아웃바운드 전환을 만들고 동일한 워크플로우 내에서 독립적으로 여러 활동을 실행할 수 있습니다.

>[!IMPORTANT]
>
>**[!UICONTROL Fork]** 활동 후에 추가하는 아웃바운드 전환은 동시에 실행되지 않습니다. 이 동작은 워크플로우 성능에 영향을 줄 수 있습니다. 여러 활동을 독립적으로 실행해야 하는 경우 **[!UICONTROL Fork]** 활동을 사용하십시오. 워크플로우의 후속 부분 전에 아웃바운드 활동에 참여할 수 있습니다(선택적).

**[!UICONTROL Fork]** 활동 및 관련 활동을 구성하려면 다음 단계를 수행합니다.

1. **[!UICONTROL Fork]** 활동을 열고 아웃바운드 전환의 이름과 레이블을 정의합니다.

   ![](assets/s_user_segmentation_fork.png)

1. 각 아웃바운드 전환을 열고 구성합니다.
1. 아웃바운드 전환에 참여하려면 AND-결합 활동을 추가합니다(선택적). [자세히 알아보기](and-join.md)

   워크플로우의 후속 부분은 조인된 아웃바운드 전환이 완료될 때만 실행됩니다.

## 예: 세분화

이 예제에서는 서로 다른 전자 메일이 다른 모집단 그룹으로 전송됩니다. 쿼리 뒤에 **[!UICONTROL Fork]** 활동을 사용하여 두 작업을 동시에 수행합니다.

* 쿼리 결과를 저장합니다
* 결과를 세분하여 여러 게재를 보냅니다

   ![포크 활동은 두 개의 쿼리의 교차 항목을 따르며 목록 업데이트 활동과 분할 활동 앞에 옵니다.](assets/wkf_fork_example.png)

워크플로우는 다음 활동으로 구성됩니다.

1. **[!UICONTROL Query]** 활동

   두 개의 모집단 그룹이 선택됩니다. 여성과 파리 사람들.

1. **[!UICONTROL Intersection]** 활동

   쿼리 결과의 교차, 즉 파리의 여성이 선택됩니다.

1. **[!UICONTROL Fork]** 활동

   계산된 모집단은 저장되고 두 개의 그룹으로 동시에 분할됩니다.

   1. 18세에서 40세 사이의 파리의 여자
   1. 40세 이상의 파리의 여자

1. **[!UICONTROL Delivery]** 활동

   각 모집단 그룹에 다른 이메일이 전송됩니다.

## 사용 사례: 생일 전자 메일 보내기

생일에 되풀이하는 이메일이 수신자 목록으로 전송됩니다. **[!UICONTROL Fork]** 활동은 윤년에 2월 29일에 출생한 수신자를 포함하는 데 사용됩니다. [이 ](sending-a-birthday-email.md) 사용 사례에 대해 자세히 알아보십시오.

![포크 활동은 테스트 활동을 따르고 두 개의 쿼리 활동 앞에 옵니다.](assets/birthday-workflow_usecase_1.png)

## 사용 사례: 워크플로우를 통해 컨텐츠 자동화

콘텐츠 블록 작성 및 전달이 자동화됩니다. **[!UICONTROL Fork]** 활동은 대상을 계산하는 데 사용되며 컨텐츠를 만드는 데 동시에 사용됩니다. [이 ](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) 사용 사례에 대해 자세히 알아보십시오.

![포크 활동은 게재 활동을 따르며, 쿼리 활동 및 콘텐츠 관리 활동보다 우선하며, 둘 다 AND-결합 활동을 통해 결합됩니다.](../../delivery/using/assets/d_ncs_content_workflow10.png)

그런 다음 각 아웃바운드 전환을 구성한 다음 필요한 경우 [AND-join](and-join.md) 활동을 사용하여 두 전환을 함께 조인할 수 있습니다. 이렇게 하면 나머지 워크플로우는 **[!UICONTROL Fork]** 활동의 아웃바운드 전환이 완료된 다음에만 실행됩니다.

## 관련 항목

* [AND-결합 활동](and-join.md)
* [사용 사례: 생일 전자 메일](sending-a-birthday-email.md)
* [사용 사례: 콘텐츠 만들기 및 게재](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)