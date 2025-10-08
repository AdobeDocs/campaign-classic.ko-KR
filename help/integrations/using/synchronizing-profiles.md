---
product: campaign
title: 프로필 동기화
description: ACS 커넥터와 프로필을 동기화하는 방법 알아보기
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
source-git-commit: 4d8c4ba846148d3df00a76ecc29375b9047c2b20
workflow-type: tm+mt
source-wordcount: '1155'
ht-degree: 1%

---

# 프로필 동기화{#synchronizing-profiles}



ACS 커넥터는 Campaign v7에서 Campaign Standard으로 데이터를 복제합니다. Campaign v7에서 받은 데이터는 Campaign Standard에서 게재를 만드는 데 사용할 수 있습니다. 아래 나열된 작업을 수행하여 프로필이 동기화되는 방법을 확인할 수 있습니다.

* **새 받는 사람 추가**: Campaign v7에서 새 받는 사람을 만들고 해당 프로필이 Campaign Standard에 복제되었는지 확인합니다. [새 받는 사람 만들기](#creating-a-new-recipient)를 참조하세요.
* **받는 사람 업데이트**: Campaign v7에서 새 받는 사람을 편집하고 Campaign Standard에서 해당 프로필을 보고 업데이트가 복제되었는지 확인합니다. [받는 사람 편집](#editing-a-recipient)을 참조하세요.
* **Campaign Standard에서 워크플로우를 빌드합니다**: Campaign v7에서 복제된 대상자 또는 프로필이 있는 쿼리를 포함하는 워크플로우를 Campaign Standard에서 만듭니다. [워크플로 만들기](#creating-a-workflow)를 참조하십시오.
* **Campaign Standard에서 게재를 만듭니다**: 워크플로우에 따라 게재를 보냅니다. [게재 만들기](#creating-a-delivery)를 참조하세요.
* **구독 취소 링크 확인**: Campaign v7 웹 응용 프로그램을 사용하여 수신자가 서비스 구독을 취소하도록 선택한 내용이 Campaign v7 데이터베이스로 전송되도록 합니다. 서비스 수신을 중지하는 옵션이 Campaign Standard에 복제됩니다. [구독 취소 링크 변경](#changing-the-unsubscription-link)을 참조하세요.

## 필수 구성 요소 {#prerequisites}

다음 섹션에서는 ACS 커넥터를 통해 Campaign v7에서 수신자를 추가 및 편집한 다음 Campaign Standard 게재에서 사용하는 방법에 대해 설명합니다. ACS 커넥터는 다음 조건을 충족해야 합니다.

* Campaign v7의 수신자가 Campaign Standard에 복제되었습니다.
* Campaign v7 및 Campaign Standard 모두에서 워크플로우를 실행할 수 있는 사용자 권한.
* Campaign Standard에서 게재를 만들고 실행할 수 있는 사용자 권한.

## 구독 취소 링크 변경 {#changing-the-unsubscription-link}

수신자가 Campaign Standard에서 보낸 이메일의 구독 취소 링크를 클릭하면 Campaign Standard의 해당 프로필이 업데이트됩니다. 복제된 프로필에 사용자가 서비스 구독을 취소하도록 선택하는 항목이 포함되어 있는지 확인하려면 정보를 Campaign Standard이 아닌 Campaign v7으로 보내야 합니다. 변경 사항을 실행하기 위해 구독 취소 서비스가 Campaign Standard이 아닌 Campaign v7 웹 애플리케이션에 연결됩니다.

>[!NOTE]
>
>아래 단계를 수행하기 전에 컨설턴트에게 구독 취소 서비스에 대한 웹 애플리케이션을 구성하도록 요청하십시오.

## 새 수신자 만들기 {#creating-a-new-recipient}

1. Campaign v7에서 Campaign Standard에 복제할 새 수신자를 만듭니다. 수신자의 성, 이름, 이메일 주소 및 우편 주소 등 가능한 많은 정보를 입력합니다. 그러나 **[!UICONTROL Salutation]**&#x200B;은(는) 다음 섹션인 [받는 사람 편집](#editing-a-recipient)에 추가되므로 선택하지 마십시오.

   ![](assets/acs_connect_profile_sync_01.png)

1. 새 수신자가 Campaign Standard에 추가되었는지 확인합니다. 프로필을 검토할 때 Campaign v7에 입력한 데이터를 Campaign Standard에서도 사용할 수 있는지 확인하십시오. Campaign Standard에서 프로필을 찾는 위치를 알아보려면 [탐색 기본 사항](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=ko)을 참조하세요.

   ![](assets/acs_connect_profile_sync_02.png)

   기본적으로 ACS 커넥터의 정기 복제는 15분마다 한 번씩 수행됩니다. 자세한 내용은 [데이터 복제](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)를 참조하십시오.

## 수신자 편집 {#editing-a-recipient}

데이터의 단일 지점을 변경하는 아래 단계는 데이터 복제를 사용할 때 Campaign v7이 Campaign Standard의 기본 데이터베이스가 되는 간단한 예를 제공합니다. Campaign v7에서 복제된 데이터를 수정하거나 삭제하면 Campaign Standard의 해당 데이터에도 동일한 영향을 줍니다.

1. [새 받는 사람 만들기](#creating-a-new-recipient)에서 새로 만든 받는 사람을 선택하고 받는 사람의 이름을 편집합니다. 예를 들어 받는 사람(예: Mr 또는 Mrs)에 대해 **[!UICONTROL Salutation]**&#x200B;을(를) 선택합니다.

   ![](assets/acs_connect_profile_sync_03.png)

1. 수신자의 이름이 Campaign Standard에서 업데이트되었는지 확인합니다. Campaign Standard에서 프로필을 찾는 위치를 알아보려면 [탐색 기본 사항](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=ko)을 참조하세요.

   ![](assets/acs_connect_profile_sync_04.png)

   기본적으로 ACS 커넥터의 정기 복제는 15분마다 한 번씩 수행됩니다. 자세한 내용은 [데이터 복제](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication)를 참조하십시오.

## 워크플로 만들기 {#creating-a-workflow}

Campaign v7에서 복제된 프로필 및 서비스는 디지털 마케터가 Campaign Standard의 풍부한 데이터를 활용할 수 있습니다. 아래 지침은 Campaign Standard 워크플로우에 쿼리를 추가한 다음 복제된 데이터베이스와 함께 사용하는 방법을 보여 줍니다.

Campaign Standard 워크플로에 대한 자세한 내용과 전체 지침은 [워크플로](../../workflow/using/about-workflows.md)를 참조하십시오.

1. Campaign Standard으로 이동하여 **[!UICONTROL Marketing Activities]**&#x200B;을(를) 클릭합니다.
1. 오른쪽 상단의 **[!UICONTROL Create]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Workflow]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL New workflow]** 및 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Label]** 필드에 워크플로 이름을 입력하고 필요한 경우 추가 정보를 입력합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. 왼쪽의 **[!UICONTROL Targeting]**&#x200B;에서 **[!UICONTROL Query]** 대상을 작업 영역으로 끌어서 놓습니다.

   ![](assets/acs_connect_profile_sync_05.png)

1. **[!UICONTROL Query]** 활동을 두 번 클릭하고 복제된 데이터베이스와 함께 사용할 수 있는 매개 변수를 선택하십시오. 예를 들어 다음과 같은 작업을 수행할 수 있습니다.

   * **[!UICONTROL Profiles]**&#x200B;을(를) 작업 영역으로 끌어서 놓습니다. 필드 풀다운 메뉴를 사용하여 **[!UICONTROL Is external resource]**&#x200B;을(를) 선택하여 Campaign v7에서 복제된 프로필을 찾습니다.
   * 다른 쿼리 매개 변수를 드래그하여 복제된 프로필을 추가로 타겟팅합니다.

## 게재 만들기 {#creating-a-delivery}

>[!NOTE]
>
>게재 만들기 지침은 [워크플로 만들기](#creating-a-workflow)로 시작된 워크플로를 계속합니다.

디지털 마케팅 담당자는 Campaign v7 웹 애플리케이션을 활용하여 수신자의 서비스 구독 취소 선택 사항이 Campaign v7 데이터베이스로 전송되도록 할 수 있습니다. 수신자가 구독 취소 링크를 클릭하면 서비스 수신 중지 옵션이 Campaign v7에서 Campaign Standard으로 복제됩니다. 자세한 내용은 [구독 취소 링크 변경](#changing-the-unsubscription-link)을 참조하세요.

Campaign v7에서 만든 구독 취소 서비스를 사용하는 기존 워크플로우에 이메일 게재를 추가하려면 아래 단계를 따르십시오. Campaign Standard 워크플로에 대한 자세한 내용과 전체 지침은 이 [문서](../../workflow/using/about-workflows.md)를 참조하십시오.

>[!NOTE]
>
>아래 단계를 수행하기 전에 컨설턴트에게 구독 취소 서비스에 대한 웹 애플리케이션을 구성하도록 요청하십시오.

1. 왼쪽의 **[!UICONTROL Channels]**&#x200B;을(를) 클릭합니다.
1. 작업 영역의 기존 워크플로우로 **[!UICONTROL Email delivery]**&#x200B;을(를) 끌어옵니다.

   ![](assets/acs_connect_profile_sync_07.png)

1. **[!UICONTROL Email delivery]** 활동을 두 번 클릭하고 **[!UICONTROL Single send email]** 또는 **[!UICONTROL Recurring email]**&#x200B;을(를) 선택합니다. 옵션을 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Send via email]**&#x200B;을(를) 클릭하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/acs_connect_profile_sync_08.png)

1. **[!UICONTROL Label]** 필드에 게재 이름을 입력하고 필요한 경우 추가 정보를 입력합니다. **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![](assets/acs_connect_profile_sync_09.png)

1. **[!UICONTROL Subject]** 필드에 받는 사람의 전자 메일 받은 편지함에 표시할 제목을 입력합니다.
1. HTML 템플릿을 추가하려면 **[!UICONTROL Change content]**&#x200B;을(를) 클릭하십시오.

   ![](assets/acs_connect_profile_sync_10.png)

1. 서비스 구독을 취소할 링크가 포함된 콘텐츠를 선택합니다. **[!UICONTROL Confirm]**&#x200B;을(를) 클릭합니다.

   ![](assets/acs_connect_profile_sync_11.png)

1. 현재 구독 취소 링크는 컨설턴트가 만든 웹 애플리케이션을 사용하는 새 링크로 대체해야 합니다. 이메일 콘텐츠 하단에서 구독 취소 링크를 찾아 한 번 클릭합니다. 휴지통 아이콘을 클릭하여 링크를 삭제합니다.

   ![](assets/acs_connect_profile_sync_12.png)

1. 동일한 콘텐츠 영역 내부를 클릭하고 **구독 취소 링크**&#x200B;를 입력하세요.

   ![](assets/acs_connect_profile_sync_13.png)

1. 커서를 사용하여 텍스트를 강조 표시하고 체인 아이콘을 클릭합니다.
1. **[!UICONTROL Link to a landing page]**&#x200B;을(를) 클릭합니다.

   ![](assets/acs_connect_profile_sync_14.png)

1. 폴더 아이콘을 클릭하여 랜딩 페이지를 선택합니다.

   ![](assets/acs_connect_profile_sync_15.png)

1. 컨설턴트가 만든 웹 응용 프로그램을 선택하고 **[!UICONTROL Confirm]**&#x200B;을(를) 클릭합니다.

   ![](assets/acs_connect_profile_sync_16.png)

1. **[!UICONTROL Create]**&#x200B;을(를) 클릭합니다.
1. 게재 이름을 클릭하여 워크플로우로 돌아갑니다.

   ![](assets/acs_connect_profile_sync_17.png)

1. **[!UICONTROL Start]**&#x200B;을(를) 클릭하여 게재를 보냅니다. 이메일 게재 아이콘이 깜박이며 게재를 준비하고 있음을 나타냅니다.

   ![](assets/acs_connect_profile_sync_18.png)

1. **[!UICONTROL Email delivery]** 채널을 두 번 클릭하고 **[!UICONTROL Confirm]**&#x200B;을(를) 선택하여 전자 메일을 보냅니다. 메시지를 보내려면 **[!UICONTROL OK]**&#x200B;을(를) 클릭하십시오.

   ![](assets/acs_connect_profile_sync_19.png)

## 구독 취소 서비스 확인 {#verifying-the-unsubscription-service}

아래 단계로 이동하기 전에 [워크플로우 만들기](#creating-a-workflow) 및 [게재 만들기](#creating-a-delivery)의 지침을 따르십시오.

1. 수신자가 이메일 게재에서 구독 취소 링크를 클릭합니다.

   ![](assets/acs_connect_profile_sync_20.png)

1. 수신자가 구독 취소를 확인합니다.

   ![](assets/acs_connect_profile_sync_21.png)

1. Campaign v7의 수신자 데이터는 사용자의 구독 취소를 반영하도록 업데이트됩니다. 받는 사람에 대해 **[!UICONTROL No longer contact (by any channel)]** 상자를 선택했는지 확인하십시오.

   ![](assets/acs_connect_profile_sync_22.png)

1. Campaign Standard 로 이동하여 수신자에 대한 프로필 세부 정보를 엽니다. **[!UICONTROL No longer contact (by any channel)]** 옆에 확인란이 표시되는지 확인하십시오. Campaign Standard에서 프로필을 찾는 위치를 알아보려면 [탐색 기본 사항](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=ko)을 참조하세요.

   ![](assets/acs_connect_profile_sync_23.png)
