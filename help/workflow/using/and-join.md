---
solution: Campaign Classic
product: campaign
title: AND-결합
description: AND-결합
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 6%

---


# AND-결합{#and-join}

조인은 모든 인바운드 전환이 활성화된 경우(즉, 모든 이전 활동이 완료된 경우) 아웃바운드 전환을 트리거합니다. 따라서 워크플로우를 계속 실행하기 전에 특정 활동이 완료되었는지 확인할 수 있습니다.

예를 들어 컨텐츠 생성 및 전달 전송 자동화 컨텍스트에서 AND 참여 활동을 사용하여 대상 쿼리 및 컨텐츠 업데이트 단계가 완료된 경우에만 배달을 시작할 수 있습니다. 전용 사용 사례는 [이 섹션에 있습니다.](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

활동의 아웃바운드 전송 모집단은 활동의 인바운드 전환 중 기본 세트를 선택하여 결정됩니다.

아웃바운드 전환에는 인바운드 전환 모집단 중 하나만 포함할 수 있습니다. 활동이 구성되지 않으면 아웃바운드 전환에서 인바운드 인구 중 하나를 임의로 선택합니다.

>[!CAUTION]
>
>AND- **조인** 유형 활동의 경우 이벤트 변수가 병합되지만 동일한 변수가 두 번 정의된 경우 충돌이 발생하고 값이 확인되지 않은 상태로 유지됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/javascript-scripts-and-templates.md#event-variables)을 참조하십시오.
