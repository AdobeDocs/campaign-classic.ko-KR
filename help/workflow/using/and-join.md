---
product: campaign
title: AND-결합
description: AND-결합
feature: Workflows
hide: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
TQID: https://experienceleague.adobe.com/L6SmrK6xHkRqZI69OepbB4drLPfrX-cmvi6h6su3LYk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 195
ht-degree: 22%

---

# AND-결합{#and-join}



가입은 모든 인바운드 전환이 활성화된 경우, 즉 모든 이전 활동이 완료된 경우에만 아웃바운드 전환을 트리거합니다. 이렇게 하면 워크플로를 계속 실행하기 전에 특정 활동이 완료되었는지 확인할 수 있습니다.

예를 들어 콘텐츠 작성 및 게재 전송 자동화 컨텍스트에서 AND-join 활동을 사용하여 타겟 쿼리 및 콘텐츠 업데이트 단계가 완료된 후에만 게재가 시작되도록 할 수 있습니다. [이 섹션](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)에서 전용 사용 사례를 사용할 수 있습니다.

![](assets/and-join-usage.png)

>[!NOTE]
>
>다른 타겟팅 차원으로 구성된 인바운드 전환은 **[!UICONTROL AND-join]** 활동을 사용하여 함께 결합할 수 없습니다.

활동의 아웃바운드 전송 모집단은 활동의 인바운드 전환 중에서 기본 세트를 선택하여 결정됩니다.

아웃바운드 전환에는 인바운드 전환 모집단 중 하나만 포함될 수 있습니다. 활동이 구성되지 않은 경우 아웃바운드 전환은 인바운드 모집단 중 하나를 임의로 선택합니다.

>[!CAUTION]
>
>**AND-join** 형식 활동의 경우 이벤트 변수가 병합되지만 동일한 변수가 두 번 정의되어 있으면 충돌이 발생하고 값이 확인되지 않습니다. 이 작업에 대한 자세한 정보는 [이 섹션](javascript-scripts-and-templates.md#event-variables)을 참조하십시오.
