---
product: campaign
title: Adobe Analytics 데이터 커넥터
description: Adobe Analytics 데이터 커넥터
feature: Overview
role: User, Admin
level: Beginner
exl-id: 5bd12f65-f468-41ab-bbae-e59a6592a803
hidefromtoc: true
hide: true
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1659'
ht-degree: 98%

---

# Adobe Analytics 데이터 커넥터{#adobe-analytics-data-connector-legacy}

>[!IMPORTANT]
>
>Adobe Analytics 데이터 커넥터는 이제 더 이상 사용되지 않습니다. 사용 중단되는 기능은 계속 사용할 수는 있지만 더 이상 향상 또는 지원되지 않습니다. [이 페이지](../../rn/using/deprecated-features.md)에서 자세히 알아보십시오.

## 데이터 커넥터 통합 정보 {#about-data-connector-integration}

>[!IMPORTANT]
>
>Adobe Analytics 데이터 커넥터는 트랜잭션 메시지(메시지 센터)와 호환되지 않습니다.

데이터 커넥터(이전의 Adobe Genesis)를 사용하면 Adobe Campaign 및 Adobe Analytics가 **웹 분석 커넥터** 패키지를 통해 상호 작용할 수 있습니다. Adobe Analytics 커넥터는 이메일 캠페인 후 사용자 행동에 대한 세그먼트 형태로 Adobe Campaign에 데이터를 전달합니다. 반대로 Adobe Campaign에서 게재하는 이메일 캠페인의 지표와 특성을 Adobe Analytics – 데이터 커넥터로 보냅니다.

Adobe Campaign에는 데이터 커넥터를 사용하여 인터넷 대상자를 측정하는 방법(웹 분석)이 있습니다. 이러한 통합 덕분에 Adobe Campaign은 마케팅 캠페인 후 하나 이상의 사이트에 대한 방문자 동작에 대한 데이터를 복구한 다음 (분석 후) 재마케팅 캠페인을 실행하여 방문자를 바이어로 전환할 수 있습니다. 반대로 웹 분석 도구를 사용하면 Adobe Campaign에서 지표와 캠페인 속성을 플랫폼에 전달할 수 있습니다.

각 도구의 작업 필드는 다음과 같습니다.

* 웹 분석의 역할:

   1. Adobe Campaign으로 시작한 이메일 캠페인을 표시합니다.
   1. 캠페 이메일을 클릭한 후 검색한 사이트에서 수신자 동작을 세그먼트 형태로 저장합니다. 세그먼트는 포기한 제품(장바구니에 표시되지만 장바구니에 추가되지 않음), 구매 또는 장바구니 포기와 관련이 있습니다.

* Adobe Campaign의 역할:

   1. 지표 및 캠페인 속성을 커넥터로 전송하면 커넥터가 이 속성을 웹 분석 도구에 전달합니다.
   1. 세그먼트를 복구하고 분석합니다.
   1. 리마케팅 캠페인을 트리거합니다.

## 통합 설정 {#setting-up-the-integration}

데이터 커넥터를 설정하려면 Adobe Campaign 인스턴스에 연결하고 다음 작업을 수행해야 합니다.

* [1단계: Analytics에서 통합 구성](#step-1--configure-integration-in-analytics)
* [2단계: Campaign에서 외부 계정 만들기](#step-2--create-the-external-account-in-campaign)
* [3단계: Adobe Campaign 및 Adobe Analytics 동기화](#step-3--synchronize-adobe-campaign-and-adobe-analytics)

### 1단계: Analytics에서 통합 구성 {#step-1--configure-integration-in-analytics}

다음 단계에서는 마법사를 사용하여 데이터 커넥터 구성을 자세히 설명합니다.

1. Adobe ID 또는 Enterprise ID을 사용하여 Adobe Experience Cloud에 로그인합니다.

   ![](assets/adobe_genesis_install_001.png)

1. Experience Cloud 솔루션 목록에서 **[!UICONTROL Analytics]**&#x200B;를 선택합니다.

   ![](assets/adobe_genesis_install_013.png)

1. **[!UICONTROL Admin]** 탭에서, **[!UICONTROL Data Connectors]**&#x200B;를 선택합니다.

   **[!UICONTROL Data Connectors]** 메뉴에 액세스하려면 다음 Analytics 도구 권한이 있어야 합니다. 자세한 정보는 이 [페이지](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/permissions/analytics-tools.html?lang=ko)를 참조하십시오.
   * 통합(만들기)
   * 통합(업데이트)
   * 통합(삭제)

   ![](assets/adobe_genesis_install_002.png)

1. 파트너 목록에서 **[!UICONTROL Adobe Campaign Classic]**&#x200B;을 선택합니다.

   ![](assets/adobe_genesis_install_014.png)

1. **[!UICONTROL Add integration]** 대화에서, **[!UICONTROL Activate]**&#x200B;를 클릭합니다.
1. **[!UICONTROL I accept these terms and conditions]**&#x200B;을(를) 확인해서 이 통합에 연결된 **[!UICONTROL Report suite]**&#x200B;을(를) 선택한 다음 커넥터 레이블을 입력합니다.

   완료되면 **[!UICONTROL Create and configure this integration]**&#x200B;을(를) 클릭합니다.

   ![](assets/adobe_genesis_install_015.png)

1. 커넥터를 대신하여 알림을 받을 이메일 주소를 입력한 다음 외부 Adobe Campaign 계정에 나타나는 **[!UICONTROL Account ID]**&#x200B;를 복사합니다. 자세한 내용은 [2단계: Campaign에서 외부 계정 만들기](#step-2--create-the-external-account-in-campaign)를 참조하십시오.

   ![](assets/adobe_genesis_install_005.png)

1. 이메일 캠페인의 영향을 측정하는 데 필요한 식별자, 즉, 내부 캠페인 이름(cid) 및 iNmsBroadlog(bid) 테이블 ID를 지정합니다. 수집할 이벤트에 대한 지표도 지정해야 합니다.
**[!UICONTROL Events]**&#x200B;가 숫자 유형인지 확인하십시오. 그렇지 않으면 드롭다운 메뉴에 나타나지 않습니다.

   ![](assets/adobe_genesis_install_006.png)

1. 필요한 경우 개인화된 세그먼트를 지정합니다.

   ![](assets/adobe_genesis_install_007.png)

1. **[!UICONTROL Data collection]**&#x200B;에서 데이터 복구 방법을 선택합니다. 이 경우 6단계에서 지정된 **[!UICONTROL cid]** 및 **[!UICONTROL bid]** 식별자를 선택합니다.

   ![](assets/adobe_genesis_install_009.png)

1. 대시보드에 표시할 정보를 선택합니다.

   ![](assets/adobe_genesis_install_0112.png)

1. 페이지에서 이전 단계를 합산한 구성을 확인합니다.

   ![](assets/adobe_genesis_install_011.png)

1. 구성을 승인하고 커넥터를 활성화하려면 **[!UICONTROL Activate Now]**&#x200B;를 클릭하십시오.

   ![](assets/adobe_genesis_install_012.png)

   이제 데이터 커넥터가 구성되었습니다.

### 2단계: Campaign에서 외부 계정 만들기 {#step-2--create-the-external-account-in-campaign}

Analytics 플랫폼에 Adobe Campaign을 통합하는 작업은 커넥터를 사용하여 수행됩니다. 애플리케이션을 동기화하려면 다음 프로세스를 적용합니다.

1. Adobe Campaign에 **Web Analytics 커넥터** 패키지를 설치합니다.
1. Adobe Campaign 트리의 **[!UICONTROL Administration > Platform > External accounts]** 폴더로 이동합니다.
1. 외부 계정 목록을 마우스 오른쪽 버튼으로 클릭하고 드롭다운 메뉴에서 **[!UICONTROL New]**&#x200B;를 선택합니다(또는 외부 계정 목록 위에 있는 **[!UICONTROL New]** 버튼을 클릭합니다).
1. 드롭다운 목록을 사용하여 **[!UICONTROL Web Analytics]** 유형을 선택합니다.
1. 커넥터 공급자, 즉, 이 경우 **[!UICONTROL Adobe Analytics - Data Connector]**&#x200B;를 선택합니다.

   ![](assets/webanalytics_ext_account_create_001.png)

1. **[!UICONTROL Enrich the formula...]** 링크를 클릭하여 URL 계산 공식을 변경해서 웹 분석 도구 통합 정보(캠페인 ID)와 활동을 추적해야 하는 사이트의 도메인을 지정합니다.
1. 사이트의 도메인 이름을 지정합니다.

   ![](assets/webanalytics_tracking_001.png)

1. **[!UICONTROL Next]**&#x200B;을 클릭하고 도메인 이름이 저장되었는지 확인합니다.

   ![](assets/webanalytics_tracking_002.png)

1. 필요한 경우 계산 공식에 과부하를 걸 수 있습니다. 이렇게 하려면 상자를 선택하고 창에서 바로 공식을 편집합니다.

   ![](assets/webanalytics_tracking_003.png)

   >[!IMPORTANT]
   >
   >이 구성 모드는 전문가 사용자용으로 예약되어 있습니다. 이 수식에 오류가 발생하면 이메일 게재가 중지될 수 있습니다.

1. **[!UICONTROL Advanced]** 탭에서는 더 많은 기술 설정을 구성하거나 수정할 수 있습니다.

   * **[!UICONTROL Lifespan]**: 기술 워크플로우로 Adobe Campaign에서 웹 이벤트가 복구되는 지연 시간(일)을 지정할 수 있도록 해줍니다. 기본값: 180일.
   * **[!UICONTROL Persistence]**: 모든 웹 이벤트(예: 구매)가 리마케팅 캠페인에 귀속될 기간을 정의할 수 있습니다. 기본값: 7일.

>[!NOTE]
>
>여러 대상 측정 도구를 사용하는 경우 외부 계정을 만들 때 **[!UICONTROL Partners]** 드롭다운 목록에서 **[!UICONTROL Other]**&#x200B;을(를) 선택할 수 있습니다. 게재 속성에서 하나의 외부 계정만 참조할 수 있습니다.따라서 Adobe에서 기대하는 매개 변수와 사용된 다른 모든 측정 도구를 추가하여 추적된 URL의 공식을 조정해야 합니다.

### 3단계: Adobe Campaign 및 Adobe Analytics 동기화 {#step-3--synchronize-adobe-campaign-and-adobe-analytics}

외부 계정을 만든 후에는 두 애플리케이션을 모두 동기화해야 합니다.

1. 이전에 만든 외부 계정으로 이동합니다.
1. 필요에 따라 **[!UICONTROL Label]** 계정을 변경합니다.
1. 데이터 커넥터를 구성하는 동안 선택한 **[!UICONTROL Name]**&#x200B;과 일치하도록 **[!UICONTROL Internal name]**&#x200B;을 변경합니다.

   ![](assets/webanalytics_ext_account_setting_001.png)

1. **[!UICONTROL Approve connection]** 링크를 클릭합니다.

   ![](assets/webanalytics_ext_account_setting_002.png)

   **[!UICONTROL Internal name]**&#x200B;이 데이터 커넥터 구성 마법사에 지정된 **[!UICONTROL Name]**&#x200B;과 일치하는지 확인합니다.

1. 데이터 커넥터 구성 마법사에서 **[!UICONTROL Account ID]**&#x200B;를 입력합니다.

   ![](assets/webanalytics_ext_account_setting_003.png)

1. 데이터 커넥터 마법사 가이드에 따라 단계를 수행한 다음 Adobe Campaign의 외부 계정으로 돌아갑니다.
1. Adobe Campaign과 Adobe Analytics - 데이터 커넥터 간에 데이터 교환을 수행하려면 **[!UICONTROL Next]**&#x200B;을 클릭하십시오.

   동기화가 완료되면 세그먼트 목록이 표시됩니다.

   ![](assets/webanalytics_ext_account_setting_004.png)

Adobe Campaign과 Adobe Analytics - 데이터 커넥터 간의 데이터 동기화가 발효되면 데이터 커넥터 마법사에 정의된 세 개의 기본 세그먼트가 Adobe Campaign에서 복구되고 Adobe Campaign 외부 계정의 **[!UICONTROL Segments]** 탭에서 액세스할 수 있습니다.

![](assets/webanalytics_segments.png)

데이터 커넥터 마법사에서 추가 세그먼트를 구성한 경우 Adobe Campaign에 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Update segment list]** 링크를 클릭하고 외부 계정 마법사에 설명된 단계를 수행합니다. 작업이 수행되면 새 세그먼트가 목록에 표시됩니다.

![](assets/webanalytics_segments_update.png)

### 웹 분석 프로세스의 기술 워크플로우 {#technical-workflows-of-web-analytics-processes}

Adobe Campaign과 Adobe Analytics - 데이터 커넥터 간의 데이터 교환은 백그라운드 작업으로 실행되는 4개의 기술 워크플로우에서 처리합니다.

이러한 속성은 Adobe Campaign 트리의 **[!UICONTROL Administration > Production > Technical workflows > Web analytics process]** 폴더 아래에 있습니다.

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**: 한 시간에 한 번, 이 워크플로우는 주어진 사이트에서 사용자의 행동에 대한 세그먼트를 다운로드하고 Adobe Campaign 데이터베이스에 포함하고 리마케팅 워크플로우를 시작합니다.
* **[!UICONTROL Event purge]**: 이 워크플로우를 사용하면 **[!UICONTROL Lifespan]** 필드에 구성된 기간에 따라 데이터베이스에서 모든 이벤트를 삭제할 수 있습니다. 자세한 내용은 [2단계: Campaign에서 외부 계정 만들기](#step-2--create-the-external-account-in-campaign)를 참조하십시오.
* **[!UICONTROL Identification of converted contacts]**: 리마케팅 캠페인 후 구매한 방문자의 디렉토리. 이 워크플로우에서 수집한 데이터는 **[!UICONTROL Re-marketing efficiency]** 보고서에서 액세스할 수 있습니다. 이 [페이지](#creating-a-re-marketing-campaign)를 참조하십시오.
* **[!UICONTROL Sending of indicators and campaign attributes]**: Adobe Analytics - 데이터 커넥터를 사용하여 Adobe Campaign을 통해 Adobe Experience Cloud로 이메일 캠페인 지표를 보낼 수 있습니다. 이 워크플로우는 매일 오전 4시에 트리거되며 데이터를 Analytics에 전송하는 데 24시간이 걸릴 수 있습니다.

   이 워크플로우를 다시 시작하지 않아야 합니다. 그렇지 않으면 Analytics 결과를 왜곡할 수 있는 모든 이전 데이터가 다시 전송됩니다.

   관련 지표는 다음과 같습니다.

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@processed)
   * **[!UICONTROL Success]** (@success)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@recipientOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personClick)
   * **[!UICONTROL Number of distinct clicks]** (@recipientClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@error)

   >[!NOTE]
   >
   >전송된 데이터는 지표 데이터에서 음수 값을 초래할 수 있는 마지막 스냅샷을 기반으로 하는 델타입니다.

   전송된 속성은 다음과 같습니다.

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label): **Campaign** 패키지가 설치된 경우에만
   * **[!UICONTROL Nature]** (operation/@nature): **Campaign** 패키지가 설치된 경우에만
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (scheduling/@contactDate)


## Adobe Campaign에서 게재 추적 {#tracking-deliveries-in-adobe-campaign}

Adobe Campaign에서 게재를 보낸 후 Adobe Experience Cloud가 사이트에서 활동을 추적할 수 있도록 하려면 게재 속성에서 일치하는 커넥터를 참조해야 합니다. 그렇게 하려면 다음 단계를 적용합니다.

1. 추적할 캠페인 게재를 엽니다.

   ![](assets/webanalytics_delivery_properties_003.png)

1. 게재 속성을 엽니다.
1. **[!UICONTROL Web Analytics]** 탭으로 이동하여 이전에 만든 외부 계정을 선택합니다. [2단계: Campaign에서 외부 계정 만들기](#step-2--create-the-external-account-in-campaign)를 참조하십시오.

   ![](assets/webanalytics_delivery_properties_002.png)

1. 이제 Adobe Analytics에서 게재를 보내고 보고서에 액세스할 수 있습니다.

## 리마케팅 캠페인 만들기 {#creating-a-re-marketing-campaign}

리마케팅 캠페인을 준비하려면 리마케팅 유형 캠페인에 사용할 게재 템플릿을 만들면 됩니다. 그런 다음 리마케팅 캠페인을 구성하고 세그먼트에 연결합니다. 각 세그먼트에는 다른 리마케팅 캠페인이 있어야 합니다.

Adobe Campaign이 초기 캠페인으로 타겟팅된 사람의 동작을 분석하는 세그먼트 복구를 완료하면 리마케팅 캠페인이 자동으로 시작됩니다. 구매하지 않고 장바구니 포기 또는 제품 보기를 하는 경우, 사이트 탐색이 구매에서 종료될 수 있도록 관련 수신자에게 게재가 전송됩니다.

Adobe Campaign은 캠페인을 준비하기 위해 사용하거나 데이터베이스를 구축할 수 있는 개인화된 게재 템플릿을 제공합니다.

1. **[!UICONTROL Explorer]**&#x200B;에서 Adobe Campaign 트리의 **[!UICONTROL Resources > Templates > Delivery templates]** 폴더로 이동합니다.
1. **[!UICONTROL Email delivery (re-marketing)]** 템플릿 또는 Adobe Campaign에서 제공하는 리마케팅 템플릿 예제를 복제합니다.
1. 필요에 따라 템플릿을 개인화하고 저장합니다.

   ![](assets/webanalytics_delivery_model.png)

1. 새 캠페인을 만들고 드롭다운 목록에서 **[!UICONTROL Re-marketing campaign]** 템플릿을 선택합니다.

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. **[!UICONTROL Configure...]** 링크를 클릭하여 캠페인에 연결된 세그먼트 및 게재 템플릿을 지정합니다.
1. 이전에 구성한 외부 계정을 선택합니다.

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. 관련 세그먼트를 선택합니다.

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. 이 리마케팅 캠페인에 사용할 게재 템플릿을 선택한 다음 **[!UICONTROL Finish]**&#x200B;을(를) 클릭하여 창을 닫습니다.

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. **[!UICONTROL OK]**&#x200B;을 클릭하여 캠페인 창을 닫습니다.

**[!UICONTROL Re-marketing efficiency]** 보고서는 글로벌 보고서 페이지를 통해 액세스합니다. 이 보고서는 Adobe Campaign 리마케팅 캠페인 이후 장바구니 포기 수와 관련하여 전환된(즉, 어떤 것을 구매한) 연락처 수를 볼 수 있도록 해줍니다. 전환율은 매주, 매월 또는 Adobe Campaign과 웹 분석 도구 간의 동기화 시작 이후마다 계산됩니다.

![](assets/remarketing_reporting.png)
