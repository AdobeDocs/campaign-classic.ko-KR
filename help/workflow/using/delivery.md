---
product: campaign
title: 게재
description: 게재 유형 워크플로우 활동에 대해 자세히 알아보십시오
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# 게재{#delivery}

![](../../assets/common.svg)

A **배달**-type 활동을 통해 게재 작업을 만들 수 있습니다. 게재 유형 활동은 입력 요소를 사용하여 생성할 수 있습니다.

구성하려면 활동을 편집하고 배달 옵션을 입력합니다.

![](assets/edit_diffusion.png)

1. **게재**

   다음을 수행할 수 있습니다.

   * 인바운드 전환에서 지정된 게재에 대해 작업합니다. 이렇게 하려면 **[!UICONTROL Delivery]** 섹션을 참조하십시오.

      이 옵션은 이전 워크플로우 활동이 이미 게재를 만들거나 지정한 경우 사용할 수 있습니다. 이 작업은 아래 예와 같이 아웃바운드 전환을 생성한 동일한 유형의 활동으로 수행할 수 있습니다.

      다음 예에서는 게재가 처음으로 만들어집니다. 모집단과 컨텐츠는 나중에 정의됩니다. 그런 다음 이 세 요소에 대한 정보를 인바운드 전환을 사용하여 새 게재 활동에 다시 입력하여 전송할 수 있습니다.

      ![](assets/specified_transition_option_exemple.png)

   * 관련 게재를 직접 선택합니다. 이렇게 하려면 **[!UICONTROL Explicit]** 옵션을 선택하고 의 드롭다운 목록에서 게재를 선택합니다 **[!UICONTROL Delivery]** 필드.

      목록에는 **게재** 기본적으로 폴더가 제공됩니다. 다른 캠페인에 액세스하려면 **[!UICONTROL Select link]** 아이콘.

      ![](assets/diffusion_edit_1.png)

      의 드롭다운 목록에서 캠페인을 선택합니다 **[!UICONTROL Folder]** 필드 또는 **[!UICONTROL Display sub-levels]** 하위 폴더에 포함된 모든 게재를 표시하려면 다음을 수행하십시오.

      ![](assets/diffusion_edit_2.png)

      게재 작업을 선택한 후 **[!UICONTROL Edit link]** 아이콘.

   * 스크립트를 만들어 게재를 계산합니다. 이렇게 하려면 **[!UICONTROL Computed by a script]** 옵션을 선택하고 스크립트를 입력합니다. 을 클릭하여 입력 창을 열 수 있습니다 **[!UICONTROL Edit...]** 선택 사항입니다. 다음 예제에서는 게재 식별자를 복구합니다.

      ![](assets/diffusion_edit_3.png)

   * 새 게재를 만듭니다. 이렇게 하려면 **[!UICONTROL New, created from a template]** 옵션을 선택하고 게재의 기반이 되는 게재 템플릿을 선택합니다.

      ![](assets/diffusion_edit_4.png)

      을(를) 클릭합니다. **[!UICONTROL Select link]** 아이콘을 클릭하여 폴더를 찾은 다음 **[!UICONTROL Edit link]** 아이콘 을 클릭하여 선택한 템플릿의 콘텐츠를 확인합니다.

1. **수신자**

   수신자는 파일 가져오기 후 또는 게재 작업에서 지정되는 등의 인바운드 이벤트에 의해 지정할 수 있습니다. 하나 이상의 파일에 저장할 수도 있습니다.

   ![](assets/diffusion_edit_5.png)

1. **컨텐츠**

   메시지의 콘텐츠는 게재 또는 인바운드 이벤트에서 정의할 수 있습니다.

   ![](assets/diffusion_edit_6.png)

1. **실행할 작업**

   게재를 만들고, 준비하고, 시작하거나, 타겟을 예측하거나, 증명을 전송할 수 있습니다.

   ![](assets/diffusion_edit_7.png)

   수행할 작업 유형을 선택합니다.

   * **[!UICONTROL Save]**: 이 옵션을 사용하면 게재를 만들고 저장할 수 있습니다. 분석하거나 전달하지 않습니다.
   * **[!UICONTROL Estimate the target]**: 이 옵션을 사용하면 게재 대상을 계산하여 잠재적(첫 번째 분석 단계)을 평가할 수 있습니다. 이 작업은 을(를) 선택하는 것과 같습니다 **[!UICONTROL Estimate the population to be targeted]** 옵션 및 클릭 **[!UICONTROL Analyze]** 를 통해 주요 타겟에게 게재를 보낼 때 **배달**.
   * **[!UICONTROL Prepare]**: 이 옵션을 사용하면 전체 분석 프로세스(대상 계산 및 컨텐츠 준비)를 실행할 수 있습니다. 게재가 전송되지 않습니다. 이 작업은 을(를) 선택하는 것과 같습니다 **[!UICONTROL Deliver as soon as possible]** 옵션 및 클릭 **[!UICONTROL Analyze]** 을 사용하여 기본 타겟으로 게재를 보낼 때 **배달**.
   * **[!UICONTROL Send a proof]**: 이 옵션을 사용하면 게재 증명을 보낼 수 있습니다. 이 작업은 **[!UICONTROL Send a proof]** 을 사용하여 게재 도구 모음에 있는 단추 **배달**
   * **[!UICONTROL Prepare and start]**: 이 옵션은 전체 분석 프로세스(target 계산 및 컨텐츠 준비)를 시작하고 게재를 전송합니다. 이 작업은 클릭 횟수와 같습니다 **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]**, 및 **[!UICONTROL Confirm delivery]** 을 사용하여 기본 타겟으로 게재를 보낼 때 옵션을 선택합니다. **배달**.

   다음 **[!UICONTROL Act on a delivery]** 워크플로우에서 추가로 사용되는 활동을 사용하면 게재를 시작하는 데 필요한 나머지 모든 단계(타겟 계산, 콘텐츠 준비, 게재)를 시작할 수 있습니다. 자세한 내용은 [게재 제어](delivery-control.md).

   다음 옵션도 사용할 수 있습니다.

   * **[!UICONTROL Generate an outbound transition]**

      실행 종료 시 활성화되는 아웃바운드 전환을 만듭니다. 아웃바운드 게재의 대상을 검색할지 여부를 선택할 수 있습니다.

   * **[!UICONTROL Do not recover target]**

      나가는 게재 작업의 대상을 복구하지 않습니다.

   * **[!UICONTROL Processing errors]**

      을(를) 참조하십시오. [게재 제어](delivery-control.md).
   다음 **스크립트** 탭에서는 게재 매개 변수를 수정할 수 있습니다.

   ![](assets/edit_diffusion_fil_script.png)

## 예: 게재 워크플로우 {#example--delivery-workflow}

새 워크플로우를 만들고 아래 그래픽에 표시된 대로 활동을 추가합니다.

![](assets/new-workflow-5.png)

를 엽니다. **배달** 활동을 수행하고 다음과 같이 속성을 정의합니다.

* 에서 **[!UICONTROL Delivery]** 섹션, **[!UICONTROL New, created from a template]** 게재 템플릿을 선택합니다.
* 에서 **[!UICONTROL Recipients]** 섹션, **[!UICONTROL Specified in the delivery]**.
* 에서 **[!UICONTROL Action to execute]** 섹션에서 **[!UICONTROL Prepare]** 선택 사항입니다.

![](assets/new-workflow-param-delivery.png)

클릭 **[!UICONTROL OK]** 를 클릭하여 속성 창을 닫습니다. 대상을 해당 내에서 지정할 게재 템플릿을 기반으로 새 게재를 만들고 준비하는 활동으로 구성된 활동을 방금 구성했습니다.

를 엽니다. **승인** 활동을 수행하고 다음과 같이 속성을 정의합니다.

1. 에서 **[!UICONTROL Assignment type]** 필드에서 등록할 그룹을 선택합니다. &#39;관리자&#39; 계정을 사용하여 연결된 경우 관리 그룹을 선택합니다.
1. 그런 다음 제목을 입력하고 메시지 본문에 다음 텍스트를 삽입합니다.

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   JavaScript로 작성된 표현식을 포함하는 메시지입니다. **[!UICONTROL vars.recCount]** 이전 작업 전달의 대상 받는 사람 수를 나타냅니다. JavaScript 표현식에 대한 자세한 내용은 [JavaScript 스크립트 및 템플릿](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   승인 작업은 [승인](approval.md).

## 입력 매개 변수 {#input-parameters}

게재 식별자(예: **[!UICONTROL Specified in the transition]** 옵션이 **[!UICONTROL Delivery]** 섹션을 참조하십시오.

* deliveryId
* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

>[!NOTE]
>
>이 매개 변수는 **[!UICONTROL Specified by inbound event(s)]** 옵션이 **[!UICONTROL Recipients]** 섹션을 참조하십시오.

* 파일

   다음의 경우 생성된 파일의 전체 이름 **[!UICONTROL File(s) specified by inbound event(s)]** 옵션이 **[!UICONTROL Recipients]** 섹션을 참조하십시오.

* contentId

   다음의 경우 컨텐츠 식별자 **[!UICONTROL Specified by inbound events]** 옵션이 **[!UICONTROL Content]** 섹션을 참조하십시오.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 집합은 게재의 결과 대상을 식별합니다. **[!UICONTROL tableName]** 는 대상의 식별자를 기억하는 테이블의 이름입니다. **[!UICONTROL schema]** 는 모집단의 스키마(일반적으로 nms:recipient)이며 **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.

보어와 연관된 전환에는 동일한 매개 변수가 있습니다.

>[!NOTE]
>
>를 실행할 때 출력 매개 변수가 없습니다. **[!UICONTROL Do not recover target]** 옵션이 선택되어 있습니다.
