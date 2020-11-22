---
solution: Campaign Classic
product: campaign
title: 워크플로우 수명 주기
description: 워크플로우의 수명 주기에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---


# 워크플로우 수명 주기 {#workflow-life-cycle}

워크플로우 주기에 세 가지 주요 단계가 있습니다.

* **편집 중**

   초기 디자인 단계입니다.새 워크플로우가 만들어지면 상태는 &#39;편집 중&#39;입니다. 워크플로우는 서버에서 아직 처리되지 않으며 위험 없이 수정할 수 있습니다.

* **시작됨**

   초기 디자인 단계가 완료되면 워크플로우를 시작할 수 있습니다. 이 단계에서는 인스턴스가 서버에 의해 처리되고 개별 작업이 실행됩니다. 특정 예방 조치로 워크플로우를 수정할 수 있습니다.

* **완료됨**

   진행 중인 작업이 없거나 연산자가 명시적으로 인스턴스를 중지한 경우 워크플로가 &#39;Finished&#39;입니다.

예를 들어, **시작****및** 배달 **활동은 아래 작업** 에서 승인활동이깜박이는 동안 요약되어 있습니다.

![](assets/new-workflow-6.png)

즉, 처음 두 활동이 성공적으로 실행되었으며 승인이 진행 중임을 의미합니다(예: 생성되었지만 아직 완료되지 않은 경우).

배달 **활동 다음의 전환 위에** 574 -Ok **** 문자가 표시되면 배달 준비 시 받는 사람 574명을 대상으로 하고 작업이 성공적으로 완료되었음을 의미합니다. 이 정보는 실행 시 전환 효과에 추가되며 데이터를 처리하는 활동에 의해 계산됩니다.

워크플로가 시작되어 승인 활동에 지정된 그룹에 속하는 연산자가 **결정을** 내리기를 기다리고 있습니다. 해당 그룹에 속한 운영자에게 이메일 주소 또는 모바일 전화 번호를 알려 줍니다.

연산자 관리는 이 [섹션에 자세히 설명되어 있습니다](../../platform/using/access-management.md).

워크플로우를 모니터링하는 방법에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../workflow/using/monitoring-workflow-execution.md).
