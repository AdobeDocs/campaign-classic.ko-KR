---
title: 테스트
seo-title: 테스트
description: 테스트
seo-description: null
page-status-flag: never-activated
uuid: 3522f4ac-3a72-4ff1-b3aa-1b4c283ef2bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 78c70ef4-807d-45d4-ac87-2b741c0ef5cb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7ed7e59be2cfbde467b0c80d21cfbf52016a2b8
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 6%

---


# 테스트{#test}

A **Test** type activity activates the first transition that satisfies the condition associated with it. If no condition is satisfied and if the **[!UICONTROL Use the default fork]** option is activated, the default transition will be activated.

조건은 &#39;true&#39; 또는 &#39;false&#39;로 평가되어야 하는 JavaScript 식입니다. 표현식을 입력하려면 조건 이름 오른쪽에 있는 아이콘을 클릭한 다음 선택합니다 **[!UICONTROL Edit...]**.

![](assets/edit_test.png)

워크플로 JavaScript를 통해 액세스할 수 있는 응용 프로그램 서버의 모든 추가 JavaScript 함수 및 SOAP 메서드에 대한 자세한 내용은 [JSAPI 설명서를 참조하십시오](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

이 편집기에서 직접 변수를 삽입할 수도 있습니다. 변수 작업 방법에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../workflow/using/javascript-scripts-and-templates.md#variables).

활동 속성 편집 창에서 조건을 추가, 삭제 또는 주문할 수 있지만 전환에서 수정할 수도 있습니다.

계산의 결과를 다른 조건에 의해 재사용하려는 경우 활동의 초기화 스크립트에서 계산할 수 있습니다. 결과는 조건 스크립트(task.vars.xxx)에서 액세스할 작업의 변수에 저장되어야 합니다.
