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
source-git-commit: b78db689958c9b240da9a0315060fe63bcb48e0a

---


# 테스트{#test}

테스트 **유형** 활동은 연결된 조건을 충족하는 첫 번째 전환을 활성화합니다. 조건이 충족되지 않고 **[!UICONTROL Use the default fork]** 옵션이 활성화되면 기본 전환이 활성화됩니다.

조건은 &#39;true&#39; 또는 &#39;false&#39;로 평가되어야 하는 JavaScript 표현식입니다. 표현식을 입력하려면 조건 이름 오른쪽에 있는 아이콘을 클릭한 다음 **[!UICONTROL Edit...]**&#x200B;을 선택합니다.

![](assets/edit_test.png)

워크플로 JavaScript를 통해 액세스할 수 있는 응용 프로그램 서버의 모든 추가 JavaScript 함수 및 SOAP 메서드에 대한 자세한 내용은 JSAPI [설명서를](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)참조하십시오.

이 편집기에서 직접 변수를 삽입할 수도 있습니다.

활동 속성 편집 창에서 조건을 추가, 삭제 또는 주문할 수 있지만 전환에서 수정할 수도 있습니다.

계산의 결과가 다른 조건에 의해 다시 사용될 경우 활동의 초기화 스크립트에서 계산할 수 있습니다. 결과는 조건 스크립트(task.vars.xxx)에서 액세스할 작업의 변수에 저장해야 합니다.
