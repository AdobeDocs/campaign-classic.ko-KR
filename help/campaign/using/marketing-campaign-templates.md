---
product: campaign
title: 마케팅 캠페인 템플릿
description: 마케팅 캠페인 템플릿
role: User
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# Campaign 템플릿 만들기 및 구성 {#campaign-templates}

모든 마케팅 캠페인은 주요 특성과 기능을 저장하는 템플릿을 기반으로 합니다. 캠페인 템플릿이 **[!UICONTROL Resources > Templates > Campaign templates]** 노드에서 중앙 집중화되었습니다. 기본 템플릿이 표준으로 제공됩니다. 사용 가능한 모든 모듈(문서, 작업, 시드 주소 등)을 사용하여 새 캠페인을 만들 수 있지만, 제공되는 모듈은 사용자의 권한 및 Adobe Campaign 플랫폼의 구성에 따라 다릅니다.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>홈페이지에서 **[!UICONTROL Explorer]** 아이콘을 클릭하면 트리가 표시됩니다.

특정 구성이 정의되지 않은 캠페인을 만들기 위해 내장 템플릿이 제공됩니다. 캠페인 템플릿을 만들고 구성한 다음 그 템플릿에서 캠페인을 만들 수 있습니다.

![](assets/do-not-localize/how-to-video.png) 캠페인 만들기에 대한 자세한 내용은 [이 비디오](../../campaign/using/marketing-campaign-deliveries.md#create-email-video)를 참조하세요.

## 캠페인 템플릿 만들기 {#creating-or-duplicating-a-campaign-template}

캠페인 템플릿을 만들려면 아래 단계를 수행하십시오.

1. 캠페인 **탐색기**&#x200B;를 엽니다.
1. **리소스 > 템플릿 > 캠페인 템플릿**&#x200B;에서 템플릿 목록 위의 도구 모음에서 **새로 만들기**&#x200B;를 클릭합니다.

   ![](assets/create_campaign_template_1.png)

1. 새 캠페인 템플릿의 레이블을 입력합니다.
1. **저장**&#x200B;을 클릭하고 서식 파일을 다시 엽니다.
1. 필요한 경우 **편집** 탭에서 **내부 이름** 및 기타 값을 입력합니다.
1. **고급 캠페인 설정**&#x200B;을 선택하여 캠페인 템플릿에 워크플로우를 추가하십시오.

   ![](assets/create_campaign_template_2.png)

1. **타깃팅 및 워크플로** 값을 **예**(으)로 변경합니다.

   ![](assets/create_campaign_template_3.png)

1. **타깃팅 및 워크플로** 탭에서 **워크플로 추가...**&#x200B;를 클릭합니다.

   ![](assets/create_campaign_template_4.png)

1. **레이블** 필드를 작성하고 **확인**&#x200B;을 클릭합니다.
1. 요구 사항에 따라 워크플로우를 만듭니다.
1. **저장**&#x200B;을 클릭합니다. 이제 템플릿을 캠페인에서 사용할 준비가 되었습니다.

기본 템플릿을 **복제**&#x200B;하여 다시 사용하고 구성을 조정할 수도 있습니다.

캠페인 템플릿의 다양한 탭과 하위 탭을 사용하여 [일반 구성](#general-configuration)에 설명된 설정에 액세스할 수 있습니다.

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 모듈 선택 {#select-modules}

**[!UICONTROL Advanced campaign settings...]** 링크를 사용하면 이 템플릿을 기반으로 캠페인에 대한 작업을 활성화 및 비활성화할 수 있습니다. 이 템플릿을 기반으로 만든 캠페인에서 활성화할 기능을 선택합니다.

![](assets/s_ncs_user_op_template_tab1.3.png)

기능을 선택하지 않으면 프로세스와 관련된 요소(메뉴, 아이콘, 옵션, 탭, 하위 탭 등)가 은 템플릿의 인터페이스 또는 이 템플릿을 기반으로 하는 캠페인에 표시되지 않습니다. 캠페인 세부 정보의 왼쪽에 있는 탭은 일반적으로 템플릿에서 선택한 프로세스와 일치합니다. 예를 들어 **경비 및 목표**&#x200B;를 선택하지 않으면 해당 **[!UICONTROL Budget]** 탭이 이 템플릿을 기반으로 하는 캠페인에 표시되지 않습니다.

또한 구성 창에 대한 단축키가 캠페인 대시보드에 추가됩니다. 기능을 활성화하면 직접 링크를 통해 캠페인 대시보드에서 액세스할 수 있습니다.

예를 들어 아래 구성이 다음과 같습니다.

![](assets/s_ncs_user_op_template_tab1.4.png)

다음 링크가 캠페인 대시보드에 표시됩니다(**[!UICONTROL Add a task]** 링크가 없음).

![](assets/s_ncs_user_op_template_tab1.3ex.png)

그리고 다음 탭만 표시됩니다.

![](assets/s_ncs_user_op_template_tab1.4ex.png)

그러나 이러한 유형의 구성은 다음과 같습니다.

![](assets/s_ncs_user_op_template_tab2.2ex.png)

다음 링크 및 탭이 표시됩니다.

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 모듈 유형화 {#typology-of-enabled-modules}

* **컨트롤 그룹**

  이 모듈을 선택하면 템플릿 및 이 템플릿을 기반으로 하는 캠페인의 고급 설정에 추가 탭이 추가됩니다. 템플릿을 통해 또는 각 캠페인에 대해 개별적으로 구성을 정의할 수 있습니다. [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)에서 컨트롤 그룹에 대해 자세히 알아보세요.

  ![](assets/s_ncs_user_op_template_activate_1.png)

* **시드 주소**

  이 모듈을 선택하면 템플릿 및 이 템플릿을 기반으로 하는 캠페인의 고급 설정에 추가 탭이 추가됩니다. 템플릿을 통해 또는 각 캠페인에 대해 개별적으로 구성을 정의할 수 있습니다. [이 섹션](../../delivery/using/about-seed-addresses.md)에서 시드 주소에 대해 자세히 알아보세요.

  ![](assets/s_ncs_user_op_template_activate_2.png)

* **문서**

  이 모듈을 선택하면 템플릿의 **[!UICONTROL Edition]** 탭과 이 템플릿을 기반으로 하는 캠페인에 추가 탭이 추가됩니다. 첨부된 문서는 템플릿에서 또는 각 캠페인에 대해 개별적으로 추가할 수 있습니다. [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)의 문서에 대해 자세히 알아보세요.

  ![](assets/s_ncs_user_op_template_activate_3.png)

* **개요**

  이 모듈을 선택하면 **[!UICONTROL Documents]** 탭에 **[!UICONTROL Delivery outlines]** 하위 탭이 추가되어 캠페인에 대한 게재 개요를 정의합니다. [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)에서 게재 개요에 대해 자세히 알아보세요.

  ![](assets/s_ncs_user_op_template_activate_4.png)

* **타깃팅 및 워크플로**

  **[!UICONTROL Targeting and workflows]** 모듈을 선택하면 이 템플릿을 기반으로 캠페인용 워크플로우를 하나 이상 만들 수 있는 탭이 추가됩니다. 이 템플릿을 기반으로 각 캠페인에 대해 개별적으로 워크플로우를 구성할 수도 있습니다. [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)에서 캠페인 워크플로우에 대해 자세히 알아보세요.

  ![](assets/s_ncs_user_op_template_activate_5.png)

  이 모듈이 활성화되면 프로세스 실행 시퀀스를 정의하는 탭이 캠페인의 고급 설정에 추가됩니다.

  ![](assets/s_ncs_user_op_template_activate_5a.png)

* **승인**

  **[!UICONTROL Approval]**&#x200B;을(를) 선택하면 승인할 프로세스와 승인을 담당하는 연산자를 선택할 수 있습니다. [이 섹션](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)에서 승인에 대해 자세히 알아보세요.

  ![](assets/s_ncs_user_op_template_activate_5b.png)

  템플릿 고급 설정 섹션의 **[!UICONTROL Approvals]** 탭을 통해 프로세스 승인을 사용할지 여부를 선택할 수 있습니다. 승인이 선택된 작업은 메시지 게재를 승인해야 합니다.

  활성화된 각 승인에 검토자 운영자 또는 운영자 그룹을 연결해야 합니다.

* **경비 및 목표**

  이 모듈을 선택하면 연결된 예산을 선택할 수 있도록 **[!UICONTROL Budget]** 탭이 템플릿 및 이 템플릿을 기반으로 하는 캠페인의 세부 정보에 추가됩니다.

  ![](assets/s_ncs_user_op_template_activate_7.png)

## 속성 및 실행 {#general-configuration}

### 템플릿 속성 {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

캠페인 템플릿을 만들 때 다음 정보를 입력해야 합니다.

* 템플릿의 **레이블**&#x200B;을(를) 입력하십시오. 이 레이블은 기본적으로 이 템플릿을 통해 만든 모든 캠페인에 할당됩니다.
* 드롭다운 목록에서 캠페인 **자연**&#x200B;을(를) 선택합니다. 이 목록에서 사용할 수 있는 값은 **[!UICONTROL natureOp]** 열거에 저장된 값입니다.

  >[!NOTE]
  >
  >열거형에 대한 자세한 내용은 [시작하기](../../platform/using/managing-enumerations.md) 섹션을 참조하십시오.

* **캠페인 유형**(고유, 반복 또는 정기)을 선택하십시오. 기본적으로 캠페인 템플릿은 고유한 캠페인에 적용됩니다. 반복 및 정기 캠페인은 [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)에 자세히 설명되어 있습니다.
* 캠페인 기간, 즉 캠페인이 진행될 일 수를 지정합니다. 이 템플릿을 기반으로 캠페인을 만들 때 캠페인 시작 및 종료 날짜가 자동으로 채워집니다.

  캠페인이 반복되면 템플릿에서 직접 캠페인 시작 및 종료 날짜를 지정해야 합니다.

* 템플릿의 **관련 프로그램**&#x200B;을 지정하십시오. 이 템플릿을 기반으로 하는 캠페인은 선택한 프로그램에 연결됩니다.

### 템플릿 실행 매개 변수 {#template-execution-parameters}

**[!UICONTROL Advanced campaign settings...]** 링크를 사용하면 게재 대상(컨트롤 그룹, 시드 주소 등)을 처리하기 위한 템플릿의 고급 옵션을 구성할 수 있습니다. 캠페인 측정 및 워크플로우 실행 구성

![](assets/s_ncs_user_op_template_tab1.2.png)

## 캠페인 실행 추적{#campaign-reverse-scheduling}

캠페인에 대한 일정을 만들고 성과를 추적할 수 있습니다. 예를 들어 특정 날짜에 대한 이벤트 일정을 준비할 수 있습니다. 이제 캠페인 템플릿을 사용하여 캠페인의 종료 날짜를 기준으로 작업의 시작 날짜를 계산할 수 있습니다.

작업 구성 상자에서 **[!UICONTROL Implementation schedule]** 영역으로 이동하여 **[!UICONTROL The start date is calculated based on the campaign end date]** 상자를 선택합니다. (여기서 &quot;시작 날짜&quot;는 작업 시작 날짜입니다.) **[!UICONTROL Start]** 필드로 이동하여 간격을 입력하십시오. 이 작업은 캠페인 종료일 훨씬 전에 시작됩니다. 캠페인이 지속되도록 설정된 기간보다 긴 기간을 입력하면 캠페인 전에 작업이 시작됩니다.

![](assets/mrm_task_in_template_start_date.png)

이 템플릿을 사용하여 캠페인을 만들 때 작업 시작 날짜가 자동으로 계산됩니다. 그러나 나중에 언제든지 변경할 수 있습니다.
