---
product: campaign
title: 콘텐츠 템플릿 사용
description: 콘텐츠 템플릿 사용
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 2%

---

# 콘텐츠 템플릿 사용{#using-a-content-template}

![](../../assets/common.svg)

## 콘텐츠 템플릿 기본 정보 {#about-content-templates}

콘텐츠 템플릿을 직접 참조하고 게재에서 사용할 수 있습니다. [컨텐츠 관리를 통해 게재 만들기](#creating-a-delivery-via-content-management)를 참조하십시오

컨텐츠 인스턴스를 만드는 데 사용할 수도 있습니다. 생성된 인스턴스는 이러한 인스턴스를 게재할 준비가 되었습니다( [컨텐츠 인스턴스 제공](#delivering-a-content-instance) 참조) 또는 내보낼 준비가 되었습니다([컨텐츠 인스턴스 만들기](#creating-a-content-instance) 참조).

## 콘텐츠 관리를 통해 게재 만들기 {#creating-a-delivery-via-content-management}

입력 필드를 사용하여 컨텐츠를 입력하는 보기에서 게재에서 컨텐츠 템플릿을 참조할 수 있습니다. 게재 콘텐츠를 정의하기 위한 추가 탭이 게재 마법사에 추가됩니다.

![](assets/s_ncs_content_deliver_a_content.png)

레이아웃은 선택한 설정에 따라 자동으로 적용됩니다. 보려면 **[!UICONTROL HTML preview]** (또는 **[!UICONTROL Text preview]** )을 클릭하고 개인화 요소를 테스트할 수신자를 선택하십시오.

![](assets/s_ncs_content_deliver_a_content_html.png)

자세한 내용은 전체 구현 예를 참조하십시오. [게재 마법사에서 컨텐츠 만들기](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard)

## 컨텐츠 인스턴스 만들기 {#creating-a-content-instance}

워크플로우에서 사용하거나 내보내거나 새 게재에 직접 삽입할 Adobe Campaign 트리에서 직접 컨텐츠를 만들 수 있습니다.

다음 단계를 적용합니다.

1. 트리의 **[!UICONTROL Resources > Contents]** 노드를 선택하고 마우스 오른쪽 단추를 클릭한 다음 **[!UICONTROL Properties]** 을 선택합니다.

   ![](assets/s_ncs_content_folder_properties.png)

1. 이 폴더에 대해 활성화할 게시 템플릿을 선택합니다.

   ![](assets/s_ncs_content_folder_templates.png)

1. 이제 컨텐츠 목록 위의 **[!UICONTROL New]** 버튼을 사용하여 새 컨텐츠를 만들 수 있습니다.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. 양식에 필드를 입력합니다.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. 그런 다음 **[!UICONTROL HTML preview]** 탭을 클릭하여 렌더링을 봅니다. 여기서는 데이터베이스에서 가져온 개인화 필드를 입력하지 않습니다.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. 만들어진 컨텐츠는 사용 가능한 컨텐츠 목록에 추가됩니다. 레이블, 상태를 변경하거나 기록을 보려면 **[!UICONTROL Properties]** 링크를 클릭하십시오.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. 필요한 경우 컨텐츠가 승인되면 도구 모음의 적절한 단추를 사용하여 생성할 수 있습니다.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >승인되지 않은 컨텐츠의 생성을 승인할 수 있습니다. 이렇게 하려면 게시 템플릿에서 관련 옵션을 변경합니다. 자세한 내용은 [템플릿 만들기 및 구성](publication-templates.md#creating-and-configuring-the-template)을 참조하십시오.

   HTML 및 텍스트 컨텐츠는 기본적으로 Adobe Campaign 인스턴스의 **publishing** 폴더에서 생성됩니다. **NcmPublishingDir** 옵션 덕분에 게시 폴더를 변경할 수 있습니다.

## 콘텐츠 인스턴스 제공 {#delivering-a-content-instance}

컨텐츠 인스턴스를 만들고 게재하려면 이 컨텐츠를 생성하는 데 사용되는 게시 템플릿에 게재 템플릿을 연결해야 합니다. 자세한 내용은 [배달](publication-templates.md#delivery)을 참조하십시오.

또한 컨텐츠 저장소 폴더는 이 게시 템플릿에서 가져온 컨텐츠에만 사용해야 합니다(컨텐츠 폴더를 통해 여러 유형의 컨텐츠를 생성할 수 있는 경우 게재를 자동으로 만들 수 없음).

선택한 컨텐츠에 따라 게재를 자동으로 만들려면 **[!UICONTROL Delivery]** 아이콘을 클릭하고 템플릿을 선택합니다.

![](assets/s_ncs_content_folder_create_the_delivery.png)

텍스트 및 HTML 컨텐츠가 자동으로 입력됩니다.
