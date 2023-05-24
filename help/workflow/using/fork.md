---
product: campaign
title: 포크
description: 포크 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 포크{#fork}



다음을 사용할 수 있습니다. **[!UICONTROL Fork]** 활동을 사용하여 여러 아웃바운드 전환을 만들고 동일한 워크플로우 내에서 독립적으로 여러 활동을 실행할 수 있습니다.

>[!IMPORTANT]
>
>다음에 추가하는 아웃바운드 전환 **[!UICONTROL Fork]** 활동이 동시에 실행되지 않습니다. 이 동작은 워크플로우 성능에 영향을 줄 수 있습니다. 사용 **[!UICONTROL Fork]** 활동(여러 활동을 독립적으로 실행해야 하는 경우) 필요한 경우 워크플로우의 후속 부분 전에 아웃바운드 활동에 가입할 수 있습니다.

를 구성하려면 다음을 수행하십시오. **[!UICONTROL Fork]** 활동 및 관련 활동을 보려면 다음 단계를 따르십시오.

1. 를 엽니다. **[!UICONTROL Fork]** 활동을 만들고 아웃바운드 전환의 이름 및 레이블을 정의합니다.

   ![](assets/s_user_segmentation_fork.png)

1. 각 아웃바운드 전환을 열고 구성합니다.
1. 아웃바운드 전환에 참여하려면 AND-join 활동을 추가합니다(선택 사항). [자세히 알아보기](and-join.md)

   워크플로우의 후속 부분은 조인된 아웃바운드 전환이 완료될 때만 실행됩니다.

## 예: 세그먼테이션

이 예제에서는 서로 다른 전자 메일이 서로 다른 모집단 그룹으로 전송됩니다. A **[!UICONTROL Fork]** 활동은 쿼리 다음에 사용되어 두 가지 작업을 동시에 수행합니다.

* 쿼리 결과 저장
* 결과를 세그먼트화하여 여러 게재 보내기

   ![포크 활동은 두 쿼리의 교차를 따르며 목록 업데이트 활동 및 분할 활동 앞에 옵니다.](assets/wkf_fork_example.png)

워크플로우는 다음 활동으로 구성됩니다.

1. **[!UICONTROL Query]** 활동

   두 개의 인구 집단이 선정됩니다: 여성과 파리지앵이죠.

1. **[!UICONTROL Intersection]** 활동

   쿼리 결과의 교차, 즉 파리 여성이 선택됩니다.

1. **[!UICONTROL Fork]** 활동

   계산된 모집단은 저장되고 동시에 두 개의 그룹으로 분할됩니다.

   1. 18세에서 40세 사이의 파리의 여자
   1. 40세 이상의 파리 여성

1. **[!UICONTROL Delivery]** 활동

   각 모집단 그룹에 다른 전자 메일이 전송됩니다.

## 사용 사례: 생일 이메일 보내기

생일 받는 사람 목록으로 되풀이하는 이메일이 전송됩니다. A **[!UICONTROL Fork]** 활동은 윤년에 2월 29일에 태어난 수신자를 포함하는 데 사용됩니다. [자세히 알아보기](sending-a-birthday-email.md) 이 사용 사례 정보.

![포크 활동은 테스트 활동을 따르며 두 쿼리 활동보다 우선합니다.](assets/birthday-workflow_usecase_1.png)

## 사용 사례: 워크플로우를 통해 콘텐츠 자동화

콘텐츠 블록의 만들기 및 게재가 자동화됩니다. A **[!UICONTROL Fork]** 활동은 타겟을 계산하고 동시에 컨텐츠를 만드는 데 사용됩니다. [자세히 알아보기](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) 이 사용 사례 정보.

![포크 활동은 게재 활동을 따르고 쿼리 활동 및 콘텐츠 관리 활동보다 선행하며, 두 활동 모두 AND-결합 활동을 통해 결합됩니다.](../../delivery/using/assets/d_ncs_content_workflow10.png)

그런 다음 각 아웃바운드 전환을 구성한 다음 를 사용하여 함께 연결할 수 있습니다. [AND-결합](and-join.md) 필요한 경우 활동. 이렇게 하면 나머지 워크플로우는 **[!UICONTROL Fork]** 활동의 아웃바운드 전환이 완료되었습니다.

## 관련 항목

* [AND-결합 활동](and-join.md)
* [사용 사례: 생일 이메일](sending-a-birthday-email.md)
* [사용 사례: 콘텐츠 제작 및 게재](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)