---
product: campaign
title: 콘텐츠 관리
description: 콘텐츠 관리
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 3%

---

# 콘텐츠 관리{#content-management}



A **콘텐츠 관리** 활동을 사용하면 콘텐츠를 만들고 조작할 수 있으며 이 콘텐츠를 기반으로 파일을 생성할 수 있습니다. 그런 다음 &#39;게재&#39; 활동을 통해 이 콘텐츠를 게재할 수 있습니다.

>[!CAUTION]
>
>컨텐츠 관리는 선택적 Adobe Campaign 모듈입니다. 사용권 계약을 확인하십시오.

활동의 속성은 다음 세 단계로 나뉘어 있습니다.

* **콘텐츠 선택**: 컨텐츠는 이전에 생성되었거나 활동을 통해 생성될 수 있습니다.
* **콘텐츠 업데이트**: 작업의 콘텐츠 제목을 수정하거나 모든 XML 콘텐츠를 가져올 수 있습니다.
* **작업**: 결과 콘텐츠를 저장하거나 생성할 수 있습니다.

   ![](assets/content_mgmt_edit.png)

   Adobe Campaign에서의 컨텐츠 관리 구성 및 사용에 대한 자세한 내용은 다음을 참조하십시오. [섹션](../../delivery/using/about-content-management.md).

1. **콘텐츠**

   * **[!UICONTROL Specified in the transition]**

      이 옵션을 사용하면 전환에 지정된 콘텐츠를 사용할 수 있습니다. 즉, 콘텐츠 관리를 활성화하는 이벤트에는 **[!UICONTROL contentId]** 변수를 채우는 방법에 따라 페이지를 순서대로 표시합니다. 이 변수는 이전 콘텐츠 관리 또는 모든 스크립트에 의해 설정할 수 있습니다.

   * **[!UICONTROL Explicit]**

      이 옵션을 사용하면 를 통해 이미 만들어진 콘텐츠를 선택할 수 있습니다. **[!UICONTROL Content]** 필드. 이 필드는 **[!UICONTROL Explicit]** 옵션이 선택되어 있습니다.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      콘텐츠 식별자는 스크립트에 의해 계산됩니다. 다음 **[!UICONTROL Script]** 필드를 사용하면 콘텐츠의 식별자(기본 키)를 평가하는 JavaScript 템플릿을 정의할 수 있습니다. 이 필드는 **[!UICONTROL Calculated by a script]** 옵션이 선택되어 있습니다.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      게시 템플릿에서 새 컨텐츠를 만듭니다. 이 새 콘텐츠는 다음에 지정된 파일에 저장됩니다. **[!UICONTROL String]** 필드. 다음 **[!UICONTROL Template]** 필드는 콘텐츠를 만드는 데 사용할 게시 템플릿을 지정합니다.

      ![](assets/content_mgmt_new.png)

1. **콘텐츠 업데이트**

   * **[!UICONTROL Subject]**

      이 필드에서는 콘텐츠의 제목을 수정할 수 있습니다.

   * **[!UICONTROL Access to data from an XML feed]**

      이 옵션을 사용하면 XSL 스타일시트를 통해 다운로드한 XML 문서에서 컨텐트를 만들 수 있습니다. 이 옵션을 선택하면 **[!UICONTROL URL]** 필드는 XML 콘텐츠 다운로드 URL을 지정합니다. 다음 **[!UICONTROL XSL stylesheet]** 다운로드한 XML 문서를 변환하는 데 사용할 스타일시트를 지정할 수 있습니다. 이 속성은 선택 사항입니다.

      ![](assets/content_mgmt_xmlcontent.png)

1. **실행할 작업**

   * **[!UICONTROL Save]**

      이 옵션은 생성되거나 수정된 콘텐츠를 저장합니다.

      아웃바운드 전환은 콘텐츠가 다음에 저장된 상태로 한 번만 활성화됩니다. **[!UICONTROL contentId]** 변수를 매개 변수로 사용합니다.

   * **[!UICONTROL Generate]**

      이 옵션은 콘텐츠를 저장한 다음 &#39;파일&#39; 유형 게시로 각 변환 템플릿에 대한 출력 파일을 생성합니다.

      ![](assets/content_mgmt_generate.png)

      아웃바운드 전환은에 저장된 컨텐츠의 식별자로 생성된 각 파일에 대해 활성화됩니다. **[!UICONTROL contentId]** 변수를 매개 변수로 사용하고 **[!UICONTROL filename]** 변수를 채우는 방법에 따라 페이지를 순서대로 표시합니다.

## 입력 매개 변수 {#input-parameters}

* contentId

다음에 사용될 콘텐츠 식별자: **[!UICONTROL Specified in the transition]** 옵션이 활성화되어 있습니다.

## 출력 매개 변수 {#output-parameters}

* contentId

   콘텐츠 식별자.

* 파일 이름

   선택한 작업이 다음과 같은 경우 생성된 파일의 전체 이름 **[!UICONTROL Generate]**.

## 예제 {#examples}

예제는 다음과 같습니다 [섹션](../../delivery/using/automating-via-workflows.md#examples).
