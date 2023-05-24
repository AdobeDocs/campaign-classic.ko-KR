---
product: campaign
title: 게재
description: 게재 유형 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# 게재{#delivery}



A **게재**-type 활동을 사용하면 게재 작업을 만들 수 있습니다. 게재 유형 활동은 입력 요소를 사용하여 생성할 수 있습니다.

이를 구성하려면 활동을 편집하고 게재 옵션을 입력합니다.

![](assets/edit_diffusion.png)

1. **게재**

   다음을 수행할 수 있습니다.

   * 인바운드 전환에 지정된 게재에 대해 작동합니다. 이렇게 하려면 의 첫 번째 옵션을 선택합니다. **[!UICONTROL Delivery]** 섹션에 있는 마지막 항목이 될 필요가 없습니다.

      이 옵션은 이전 워크플로우 활동이 이미 게재를 만들었거나 지정한 경우 사용할 수 있습니다. 아래 예제와 같이 아웃바운드 전환을 생성한 동일한 유형의 활동을 통해 이 작업을 수행할 수 있습니다.

      다음 예에서는 게재가 처음으로 생성됩니다. 모집단과 콘텐츠는 나중에 정의됩니다. 다음으로, 인바운드 전환을 사용하여 이 세 요소에 대한 정보를 새 게재 활동에 다시 입력하여 전송할 수 있습니다.

      ![](assets/specified_transition_option_exemple.png)

   * 관련 게재를 직접 선택합니다. 이렇게 하려면 **[!UICONTROL Explicit]** 옵션을 선택하고 드롭다운 목록에서 게재를 선택합니다. **[!UICONTROL Delivery]** 필드.

      목록에는에 포함된 완료되지 않은 게재가 표시됩니다. **게재** 기본적으로 폴더입니다. 다른 캠페인에 액세스하려면 다음을 클릭하십시오. **[!UICONTROL Select link]** 아이콘.

      ![](assets/diffusion_edit_1.png)

      의 드롭다운 목록에서 캠페인을 선택합니다. **[!UICONTROL Folder]** 필드 또는 클릭 **[!UICONTROL Display sub-levels]** 하위 폴더에 포함된 모든 게재를 표시하려면 다음 작업을 수행하십시오.

      ![](assets/diffusion_edit_2.png)

      게재 작업을 선택한 후 **[!UICONTROL Edit link]** 아이콘.

   * 게재를 계산하는 스크립트를 만듭니다. 이렇게 하려면 **[!UICONTROL Computed by a script]** 옵션을 선택하고 스크립트를 입력합니다. 다음을 클릭하여 입력 창을 열 수 있습니다. **[!UICONTROL Edit...]** 옵션을 선택합니다. 다음 예제에서는 게재 식별자를 복구합니다.

      ![](assets/diffusion_edit_3.png)

   * 새 게재를 만듭니다. 이렇게 하려면 **[!UICONTROL New, created from a template]** 옵션을 선택하고 게재의 기반이 되는 게재 템플릿을 선택합니다.

      ![](assets/diffusion_edit_4.png)

      다음을 클릭합니다. **[!UICONTROL Select link]** 아이콘을 클릭하여 폴더를 찾은 다음 **[!UICONTROL Edit link]** 아이콘 선택한 템플릿의 콘텐츠를 보려면 을 클릭합니다.

1. **수신자**

   수신자는 파일 가져오기 등의 인바운드 이벤트에 의해 지정되거나 게재 작업에 지정될 수 있습니다. 하나 이상의 파일에 저장할 수도 있습니다.

   ![](assets/diffusion_edit_5.png)

1. **콘텐츠**

   메시지 콘텐츠는 게재 또는 인바운드 이벤트에서 정의할 수 있습니다.

   ![](assets/diffusion_edit_6.png)

1. **실행할 작업**

   게재를 만들고, 준비하고, 시작하고, 대상을 추정하거나, 증명을 보낼 수 있습니다.

   ![](assets/diffusion_edit_7.png)

   수행할 작업 유형을 선택합니다.

   * **[!UICONTROL Save]**: 이 옵션을 사용하면 게재를 만들고 저장할 수 있습니다. 분석하거나 전달하지 않습니다.
   * **[!UICONTROL Estimate the target]**: 이 옵션을 사용하면 게재 대상을 계산하여 잠재력을 평가할 수 있습니다(첫 번째 분석 단계). 이 작업은 다음을 선택하는 것과 같습니다. **[!UICONTROL Estimate the population to be targeted]** 옵션 및 클릭 **[!UICONTROL Analyze]** 를 통해 기본 타겟으로 게재를 보낼 때 **게재**.
   * **[!UICONTROL Prepare]**: 이 옵션을 사용하면 전체 분석 프로세스(대상 계산 및 콘텐츠 준비)를 실행할 수 있습니다. 게재가 전송되지 않았습니다. 이 작업은 다음을 선택하는 것과 같습니다. **[!UICONTROL Deliver as soon as possible]** 옵션 및 클릭 **[!UICONTROL Analyze]** 을(를) 사용하여 기본 타겟으로 게재를 보낼 때 **게재**.
   * **[!UICONTROL Send a proof]**: 이 옵션을 사용하면 게재 증명을 보낼 수 있습니다. 이 작업은 다음을 클릭하면 됩니다. **[!UICONTROL Send a proof]** 을 사용하는 게재 도구 모음의 단추 **게재**
   * **[!UICONTROL Prepare and start]**: 이 옵션은 전체 분석 프로세스(대상 계산 및 콘텐츠 준비)를 시작하고 게재를 전송합니다. 이 작업은 다음을 클릭하는 것과 같습니다 **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]**, 및 **[!UICONTROL Confirm delivery]** 을 사용하여 게재를 기본 타겟으로 보낼 때 옵션 **게재**.

   다음 **[!UICONTROL Act on a delivery]** 워크플로우에서 추가로 사용되는 활동을 통해 게재를 시작하는 데 필요한 나머지 모든 단계(대상 계산, 콘텐츠 준비, 게재)를 시작할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [게재 제어](delivery-control.md).

   다음 옵션도 사용할 수 있습니다.

   * **[!UICONTROL Generate an outbound transition]**

      실행 종료 시 활성화될 아웃바운드 전환을 만듭니다. 아웃바운드 게재의 타겟을 검색할지 여부를 선택할 수 있습니다.

   * **[!UICONTROL Do not recover target]**

      보내는 게재 작업의 대상을 복구하지 않습니다.

   * **[!UICONTROL Processing errors]**

      을(를) 참조하십시오 [게재 제어](delivery-control.md).
   다음 **스크립트** 탭에서는 게재 매개 변수를 수정할 수 있습니다.

   ![](assets/edit_diffusion_fil_script.png)

## 예: 게재 워크플로우 {#example--delivery-workflow}

아래 그래픽에 표시된 대로 새 워크플로우를 만들고 활동을 추가합니다.

![](assets/new-workflow-5.png)

를 엽니다. **게재** 활동 을 설정하고 속성을 다음과 같이 정의합니다.

* 다음에서 **[!UICONTROL Delivery]** 섹션, 선택 **[!UICONTROL New, created from a template]** 게재 템플릿을 선택합니다.
* 다음에서 **[!UICONTROL Recipients]** 섹션, 선택 **[!UICONTROL Specified in the delivery]**.
* 다음에서 **[!UICONTROL Action to execute]** 섹션, 유지 **[!UICONTROL Prepare]** 옵션을 선택합니다.

![](assets/new-workflow-param-delivery.png)

클릭 **[!UICONTROL OK]** 속성 창을 닫습니다. 타겟이 지정될 게재 템플릿을 기반으로 새 게재를 만들고 준비하는 단계로 구성된 활동을 방금 구성했습니다.

를 엽니다. **승인** 활동 을 설정하고 속성을 다음과 같이 정의합니다.

1. 다음에서 **[!UICONTROL Assignment type]** 필드에서 등록할 그룹을 선택합니다. &#39;admin&#39; 계정을 사용하여 연결된 경우 관리 그룹을 선택합니다.
1. 그런 다음 제목을 입력하고 메시지 본문에 다음 텍스트를 삽입합니다.

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   JavaScript로 작성된 표현식을 포함하는 메시지입니다. **[!UICONTROL vars.recCount]** 이전 작업 게재의 타겟팅된 수신자 수를 나타냅니다. JavaScript 표현식에 대한 자세한 내용은 [JavaScript 스크립트 및 템플릿](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   승인 작업은에 자세히 설명되어 있습니다. [승인](approval.md).

## 입력 매개 변수 {#input-parameters}

게재 식별자(다음과 같은 경우) **[!UICONTROL Specified in the transition]** 옵션이에서 선택됨 **[!UICONTROL Delivery]** 섹션.

* deliveryId
* tableName
* 스키마

각 인바운드 이벤트는 이러한 매개 변수로 정의된 대상을 지정해야 합니다.

>[!NOTE]
>
>이 매개 변수는 **[!UICONTROL Specified by inbound event(s)]** 옵션이에서 선택됨 **[!UICONTROL Recipients]** 섹션.

* 파일 이름

   다음과 같은 경우에 생성된 파일의 전체 이름 **[!UICONTROL File(s) specified by inbound event(s)]** 옵션이에서 선택됨 **[!UICONTROL Recipients]** 섹션.

* contentId

   콘텐츠 식별자(다음 경우) **[!UICONTROL Specified by inbound events]** 옵션이에서 선택됨 **[!UICONTROL Content]** 섹션.

## 출력 매개 변수 {#output-parameters}

* tableName
* 스키마
* recCount

이 세 값 세트는 게재 결과 대상을 식별합니다. **[!UICONTROL tableName]** 은 대상의 식별자를 기억하는 표의 이름입니다. **[!UICONTROL schema]** 모집단의 스키마(일반적으로 nms:recipient)이며, **[!UICONTROL recCount]** 는 테이블에 있는 요소의 수입니다.

보체와 관련된 전환은 동일한 매개 변수를 갖는다.

>[!NOTE]
>
>다음과 같은 경우에는 출력 매개 변수가 없습니다. **[!UICONTROL Do not recover target]** 옵션이 선택되어 있습니다.
