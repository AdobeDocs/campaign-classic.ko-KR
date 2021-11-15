---
product: campaign
title: 테스트
description: 테스트 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 6f246d56-01c8-43f5-b12b-c40d258b93c8
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 테스트{#test}

![](../../assets/common.svg)

A **테스트** 유형 활동은 연결된 조건을 충족하는 첫 번째 전환을 활성화합니다. 충족된 조건이 없고 **[!UICONTROL Use the default fork]** 옵션이 활성화되면 기본 전환이 활성화됩니다.

조건은 &#39;true&#39; 또는 &#39;false&#39;로 평가해야 하는 JavaScript 표현식입니다. 표현식을 입력하려면 조건 이름의 오른쪽에 있는 아이콘을 클릭한 다음, 을 선택합니다 **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

워크플로우 JavaScript를 통해 액세스할 수 있는 애플리케이션 서버의 모든 추가 JavaScript 함수 및 SOAP 메서드에 대한 자세한 내용은 다음을 참조하십시오 [JSAPI 설명서](https://experienceleague.adobe.com/developer/campaign-api/api/index.html).

이 편집기에서 직접 변수를 삽입할 수도 있습니다. 변수를 사용하는 방법에 대한 자세한 내용은 [이 섹션](javascript-scripts-and-templates.md#variables).

활동 속성 편집 창에서 조건을 추가, 삭제 또는 정렬할 수 있지만 전환에서 수정할 수도 있습니다.

계산 결과를 다른 조건에서 다시 사용하는 경우 활동의 초기화 스크립트에서 계산할 수 있습니다. 결과는 조건 스크립트(task.vars.xxx)에서 액세스할 작업의 변수에 저장해야 합니다.
