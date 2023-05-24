---
product: campaign
title: 콘텐츠 템플릿 사용
description: 콘텐츠 템플릿 사용
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 2%

---

# 콘텐츠 템플릿 사용{#using-a-content-template}



## 콘텐츠 템플릿 기본 정보 {#about-content-templates}

콘텐츠 템플릿은 게재에서 직접 참조하고 사용할 수 있습니다. 을(를) 참조하십시오 [콘텐츠 관리를 통해 게재 만들기](#creating-a-delivery-via-content-management)

컨텐츠 인스턴스를 만드는 데도 사용할 수 있습니다. 인스턴스가 생성되면 해당 인스턴스를 제공할 수 있습니다( 참조). [콘텐츠 인스턴스 게재](#delivering-a-content-instance)) 또는 내보냄( 참조) [콘텐츠 인스턴스 만들기](#creating-a-content-instance)).

## 콘텐츠 관리를 통해 게재 만들기 {#creating-a-delivery-via-content-management}

입력 필드를 사용하여 콘텐츠를 입력한다는 관점에서 게재 시 콘텐츠 템플릿을 참조할 수 있습니다. 게재 콘텐츠를 정의하기 위해 게재 마법사에 탭이 더 추가됩니다.

![](assets/s_ncs_content_deliver_a_content.png)

선택한 설정에 따라 레이아웃이 자동으로 적용됩니다. 보려면 **[!UICONTROL HTML preview]** (또는 **[!UICONTROL Text preview]** )을 선택한 다음 개인화 요소를 테스트할 수신자를 선택합니다.

![](assets/s_ncs_content_deliver_a_content_html.png)

자세한 내용은 전체 구현 예를 참조하십시오. [게재 마법사에서 콘텐츠 만들기](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## 콘텐츠 인스턴스 만들기 {#creating-a-content-instance}

워크플로우에 사용하거나, 내보내거나, 새 게재에 바로 삽입할 콘텐츠를 Adobe Campaign 트리에서 직접 만들 수 있습니다.

다음 단계를 적용합니다.

1. 다음 항목 선택 **[!UICONTROL Resources > Contents]** 트리의 노드를 마우스 오른쪽 버튼으로 클릭하고 를 선택합니다. **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. 이 폴더에 대해 활성화할 게시 템플릿을 선택합니다.

   ![](assets/s_ncs_content_folder_templates.png)

1. 이제 를 사용하여 새 콘텐츠를 만들 수 있습니다. **[!UICONTROL New]** 콘텐츠 목록 위에 있는 단추입니다.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. 양식에 필드를 입력합니다.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. 그런 다음 **[!UICONTROL HTML preview]** 탭을 클릭하여 렌더링을 확인합니다. 여기에서 데이터베이스에서 가져온 개인화 필드는 입력되지 않습니다.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. 콘텐츠가 만들어지면 사용 가능한 콘텐츠 목록에 콘텐츠가 추가됩니다. 다음을 클릭합니다. **[!UICONTROL Properties]** 레이블, 상태를 변경하거나 기록을 보기 위한 링크입니다.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. 필요한 경우 콘텐츠가 승인되면 도구 모음의 적절한 버튼을 사용하여 생성할 수 있습니다.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >승인되지 않은 콘텐츠 생성을 승인할 수 있습니다. 이렇게 하려면 게시 템플릿에서 관련 옵션을 변경합니다. 자세한 내용은 다음을 참조하십시오. [템플릿 만들기 및 구성](publication-templates.md#creating-and-configuring-the-template).

   HTML 및 텍스트 콘텐츠는 기본적으로 **게시** Adobe Campaign 인스턴스 폴더. 다음 작업 덕분에 게시 폴더를 변경할 수 있습니다. **NcmPublishingDir** 옵션을 선택합니다.

## 콘텐츠 인스턴스 게재 {#delivering-a-content-instance}

콘텐츠 인스턴스를 만들어 게재하려면 게재 템플릿이 이 콘텐츠를 생성하는 데 사용되는 게시 템플릿에 연결되어 있어야 합니다. 자세한 내용은 다음을 참조하십시오. [게재](publication-templates.md#delivery).

또한 콘텐츠 저장소 폴더는 이 게시 템플릿에서 가져온 콘텐츠 전용이어야 합니다(콘텐츠 폴더에서 여러 유형의 콘텐츠를 생성할 수 있는 경우 게재를 자동으로 만들 수 없음).

선택한 콘텐츠를 기반으로 게재를 자동으로 만들려면 **[!UICONTROL Delivery]** 아이콘을 클릭하고 템플릿을 선택합니다.

![](assets/s_ncs_content_folder_create_the_delivery.png)

텍스트 및 HTML 내용은 자동으로 입력됩니다.
