---
solution: Campaign Classic
product: campaign
title: Adobe Analytics 커넥터
description: Adobe Analytics 커넥터에 대해 자세히 알아보십시오
feature: 개요
role: Business Practitioner, Administrator
level: Beginner
exl-id: 5bd12f65-f468-41ab-bbae-e59a6592a803
source-git-commit: 46e5cac1df419de933d96a3f35f7ac491a1defa5
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 0%

---

# Adobe Analytics 커넥터{#adobe-analytics-connector}

## Adobe Analytics 커넥터 통합 정보 {#about-analytics-connector-integration}

>[!CAUTION]
>
>Adobe Analytics 커넥터가 트랜잭션 메시지(메시지 센터)와 호환되지 않습니다.

Adobe Analytics 커넥터를 사용하면 Adobe Campaign 및 Adobe Analytics이 **[!UICONTROL Web Analytics connectors]** 패키지를 통해 상호 작용할 수 있습니다. 이메일 캠페인 후 사용자 행동에 대한 세그먼트 형태로 Adobe Campaign에 데이터를 전달합니다. 반대로 Adobe Analytics에서 제공하는 이메일 캠페인의 지표와 특성을 보냅니다.

Adobe Campaign에는 Adobe Analytics 커넥터를 사용하여 인터넷 대상자(Web Analytics)를 측정하는 방법이 있습니다. 이러한 통합 덕분에 Adobe Campaign은 마케팅 캠페인 후 하나 이상의 사이트에 대한 방문자 동작에 대한 데이터를 복구한 다음(분석 후)보기 로 재마케팅 캠페인을 실행하여 바이어로 전환할 수 있습니다. 반대로 웹 분석 도구를 사용하면 Adobe Campaign에서 지표와 캠페인 속성을 플랫폼에 전달할 수 있습니다.

각 도구의 작업 필드는 다음과 같습니다.

* 웹 분석 역할:

   1. Adobe Campaign으로 시작한 이메일 캠페인을 표시합니다.
   1. campaign 이메일을 클릭한 후 검색한 사이트에서 수신자 동작을 세그먼트 형태로 저장합니다. 세그먼트는 포기한 제품(장바구니에 표시되지만 장바구니에 추가되지 않음), 구매 또는 장바구니 중단과 관련이 있습니다.

* Adobe Campaign의 역할:

   1. indicators 및 campaign 속성을 커넥터로 전송하고 커넥터를 웹 분석 도구에 전달합니다.
   1. 세그먼트 복구 및 분석
   1. 재마케팅 캠페인을 트리거합니다.

## 통합 {#setting-up-the-integration} 설정

Data Connector를 설정하려면 Adobe Campaign 인스턴스에 연결하고 다음 작업을 수행해야 합니다.

1. [Adobe Analytics에서 보고서 세트 만들기](#report-suite-analytics)
1. [전환 변수 및 성공 이벤트 구성](#configure-conversion-success)
1. [Adobe Campaign Classic에서 외부 계정 구성](#external-account-classic)

### Adobe Analytics {#report-suite-analytics}에서 보고서 세트 만들기

Adobe Analytics/Adobe Campaign Classic 통합을 설정하려면 [!DNL Adobe Analytics] 인스턴스에 연결하고 다음 작업을 수행해야 합니다.

1. [!DNL Adobe Analytics]에서 **[!UICONTROL Admin tab]**&#x200B;을 선택한 다음 **[!UICONTROL All admin]**&#x200B;를 클릭합니다.

   ![](assets/analytics_connnector_1.png)

1. **[!UICONTROL Report suites]**&#x200B;을(를) 클릭합니다.

   ![](assets/analytics_connnector_2.png)

1. **[!UICONTROL Report suite manager]** 페이지에서 **[!UICONTROL Create new]** 를 클릭한 다음 **[!UICONTROL Report suite]** 를 클릭합니다.

   **[!UICONTROL Report suite]** 만들기에 대한 자세한 절차는 이 [섹션](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/new-report-suite/t-create-a-report-suite.html?lang=en#prerequisites)을 참조하십시오.

   ![](assets/analytics_connnector_3.png)

1. 템플릿을 선택합니다.

1. 다음 정보로 새 보고서 세트를 구성합니다.

   * **[!UICONTROL Report Suite ID]**
   * **[!UICONTROL Site Title]**
   * **[!UICONTROL Time Zone]**
   * **[!UICONTROL Go Live Date]**
   * **[!UICONTROL Estimated Page Views Per Day]**

   ![](assets/analytics_connnector_4.png)

1. 구성된 경우 **[!UICONTROL Create report suite]** 을 클릭합니다.

### 전환 변수 및 성공 이벤트 구성 {#configure-conversion-success}

**[!UICONTROL Report suite]**&#x200B;을 작성한 후 다음과 같이 **[!UICONTROL Conversion variables]** 및 **[!UICONTROL Success events]**&#x200B;를 구성해야 합니다.

1. 이전에 구성한 **[!UICONTROL Report suite]** 을 선택합니다.

1. **[!UICONTROL Edit settings]** 단추에서 **[!UICONTROL Conversion]** > **[!UICONTROL Conversion variables]**&#x200B;를 선택합니다.

   ![](assets/analytics_connnector_5.png)

1. 이메일 캠페인의 영향을 측정하는 데 필요한 식별자(즉, 내부 캠페인 이름(cid) 및 iNmsBroadlog(bid) 테이블 ID를 만들려면 **[!UICONTROL Add new]** 를 클릭합니다.

   **[!UICONTROL Conversion variables]**&#x200B;을 편집하는 방법에 대해 알아보려면 이 [섹션](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/t-conversion-variables-admin.html?lang=en#admin-tools)을 참조하십시오.

   ![](assets/analytics_connnector_6.png)

1. 완료되면 **[!UICONTROL Save]** 을 클릭합니다.

1. 그런 다음 **[!UICONTROL Success events]**&#x200B;을(를) 만들려면 **[!UICONTROL Edit settings]** 단추에서 **[!UICONTROL Conversion]** > **[!UICONTROL Success events]**&#x200B;를 선택합니다.

   ![](assets/analytics_connnector_7.png)

1. **[!UICONTROL Add new]** 을 클릭하여 다음 **[!UICONTROL Success events]**&#x200B;을 구성합니다.

   * **[!UICONTROL Clicked]**
   * **[!UICONTROL Opened]**
   * **[!UICONTROL Person clicks]**
   * **[!UICONTROL Processed]**
   * **[!UICONTROL Scheduled]**
   * **[!UICONTROL Sent]**
   * **[!UICONTROL Total bounces]**
   * **[!UICONTROL Unique Clicks]**
   * **[!UICONTROL Unique Opens]**
   * **[!UICONTROL Unsubscribed]**

   **[!UICONTROL Success events]**&#x200B;을 구성하는 방법에 대해 알아보려면 이 [섹션](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/success-events/t-success-events.html?lang=en#admin-tools)을 참조하십시오

   ![](assets/analytics_connnector_8.png)

1. 완료되면 **[!UICONTROL Save]** 을 클릭합니다.

보고서 세트가 구성되면 Adobe Campaign Classic에서 **[!UICONTROL External accounts]**&#x200B;을 구성해야 합니다.

### Adobe Campaign Classic {#external-account-classic}에서 외부 계정 구성

>[!IMPORTANT]
>
> 이 통합이 작동하려면 Adobe Campaign에 **[!UICONTROL Web Analytics connectors]** 패키지를 설치해야 합니다.
>
>패키지 설치에 대한 자세한 내용은 이 [page](../../installation/using/installing-campaign-standard-packages.md)을 참조하십시오.

이제 두 솔루션 간에 동기화를 활성화하려면 Adobe Campaign에서 **[!UICONTROL Web Analytics]** 외부 계정을 구성해야 합니다.

외부 계정을 구성할 때 **[!UICONTROL Report suite]**, **[!UICONTROL Conversion variables]** 또는 **[!UICONTROL Success events]** 중 하나가 표시되지 않으면 사용자와 연결된 **[!UICONTROL Product profile]**&#x200B;에서 새로 만든 이 구성 요소에 대한 권한이 누락되었음을 의미합니다.

자세한 내용은 [Adobe Analytics용 제품 프로필](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/permissions/product-profile.html?lang=en#product-profile-admins) 페이지를 참조하십시오.

1. Adobe Campaign 트리의 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** 폴더로 이동하고 **[!UICONTROL New]** 를 클릭합니다.

   ![](assets/analytics_connnector_9.png)

1. 드롭다운 목록을 사용하여 **[!UICONTROL Web Analytics]** 유형과 **[!UICONTROL Integration]** 드롭다운에서 **[!UICONTROL Adobe Analytics]** 유형을 선택합니다.

   ![](assets/analytics_connnector_10.png)

1. **[!UICONTROL Integration]** 드롭다운 옆에 있는 **[!UICONTROL Configure]** 을 클릭합니다.

1. **[!UICONTROL Configure Analytics integration]** 창에서 다음 정보를 제공하는 앞에서 만든 보고서 세트에 외부 계정을 매핑합니다.

   * **[!UICONTROL E-Mail]**
   * **[!UICONTROL IMS Org]**
   * **[!UICONTROL Analytics Company]**
   * **[!UICONTROL Report Suite]**

1. **[!UICONTROL eVars]** 카테고리에서 [!DNL Adobe Analytics]에 구성된 두 **[!UICONTROL Conversion variables]**&#x200B;을 매핑합니다.

   ![](assets/analytics_connnector_11.png)

1. **[!UICONTROL Events]** 카테고리에서 [!DNL Adobe Analytics]에 구성된 10개의 **[!UICONTROL Success events]**&#x200B;을 매핑합니다.

1. 완료되면 **[!UICONTROL Submit]** 을 클릭합니다. Adobe Campaign은 매핑된 Analytics **[!UICONTROL Report Suite]**&#x200B;에 **[!UICONTROL Data source]**, **[!UICONTROL Calculated metrics]**, **[!UICONTROL Remarketing segments]** 및 **[!UICONTROL Classifications]**&#x200B;를 만듭니다.

   [!DNL Adobe Analytics] 과 Adobe Campaign 간의 동기화가 완료되면 창을 닫을 수 있습니다.

1. 설정은 **[!UICONTROL Configure Analytics integration]** 창의 **[!UICONTROL Data Settings]** 탭에서 볼 수 있습니다.

   **[!UICONTROL Sync]** 단추를 사용하면 [!DNL Adobe Campaign]이 [!DNL Adobe Analytics]에서 수행한 이름 변경 사항을 동기화합니다. 구성 요소가 [!DNL Adobe Analytics]에서 삭제되면 구성 요소는 [!DNL Adobe Campaign]에서 취소되거나 **찾을 수 없음** 메시지와 함께 표시됩니다.

   ![](assets/analytics_connnector_12.png)

1. 필요한 경우 **[!UICONTROL Update Segments]** 탭에서 세그먼트를 추가하거나 제거할 수 있습니다.

1. **[!UICONTROL External account]**&#x200B;에서 **[!UICONTROL Enrich the formula...]** 링크를 클릭하여 URL 계산 공식을 변경하여 웹 분석 도구 통합 정보(캠페인 ID)와 활동을 추적해야 하는 사이트의 도메인을 지정합니다.

   ![](assets/analytics_connnector_13.png)

1. 사이트의 도메인 이름을 지정합니다.

   ![](assets/analytics_connnector_14.png)

1. **[!UICONTROL Next]** 을 클릭하고 도메인 이름이 저장되었는지 확인합니다.

   ![](assets/analytics_connnector_15.png)

1. 필요한 경우 계산 공식을 과부로드할 수 있습니다. 이렇게 하려면 상자를 선택하고 창에서 바로 공식을 편집합니다.

   >[!IMPORTANT]
   >
   >이 구성 모드는 전문가 사용자용으로 예약되어 있습니다.이 수식의 오류가 발생하면 이메일 게재가 중지될 수 있습니다.

1. **[!UICONTROL Advanced]** 탭에서는 더 많은 기술 설정을 구성하거나 수정할 수 있습니다.

   * **[!UICONTROL Lifespan]**:기술 워크플로우로 Adobe Campaign에서 웹 이벤트가 복구되는 지연 시간(일)을 지정할 수 있도록 해줍니다. 기본값:180일.
   * **[!UICONTROL Persistence]**:모든 웹 이벤트(예: 구매)가 리마케팅 캠페인에 귀속될 수 있는 기간, 기본값:7일.

>[!NOTE]
>
>여러 대상 측정 도구를 사용하는 경우 외부 계정을 만들 때 **[!UICONTROL Partners]** 드롭다운 목록에서 **[!UICONTROL Other]** 을 선택할 수 있습니다. 게재 속성에서 하나의 외부 계정만 참조할 수 있습니다.따라서 Adobe에서 기대하는 매개 변수와 사용된 다른 모든 측정 도구를 추가하여 추적된 URL의 공식을 조정해야 합니다.

### 웹 분석 프로세스의 기술 워크플로우 {#technical-workflows-of-web-analytics-processes}

Adobe Campaign과 Adobe Analytics 간의 데이터 교환은 백그라운드 작업으로 실행되는 4개의 기술 워크플로우에서 처리됩니다.

이러한 속성은 Adobe Campaign 트리의 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Web analytics process]** 폴더에서 사용할 수 있습니다.

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**:한 시간에 한 번, 이 워크플로우는 주어진 사이트에서 사용자의 행동에 대한 세그먼트를 다운로드하고 Adobe Campaign 데이터베이스에 포함하고 리마케팅 워크플로우를 시작합니다.
* **[!UICONTROL Event purge]**:이 워크플로우를 사용하면 필드에 구성된 기간에 따라 데이터베이스에서 모든 이벤트를 삭제할 수  **[!UICONTROL Lifespan]** 있습니다. 자세한 내용은 Adobe Campaign Classic](#external-account-classic)에서 외부 계정 구성 을 참조하십시오.[
* **[!UICONTROL Identification of converted contacts]**:재마케팅 캠페인 후 구매한 방문자의 디렉토리입니다. 이 워크플로우에서 수집한 데이터는 **[!UICONTROL Re-marketing efficiency]** 보고서에서 액세스할 수 있습니다. 이 [page](#creating-a-re-marketing-campaign)를 참조하십시오.
* **[!UICONTROL Sending of indicators and campaign attributes]**:Adobe Analytics 커넥터를 사용하여 Adobe Campaign을 통해 Adobe Experience Cloud으로 이메일 캠페인 표시기를 전송할 수 있습니다. 이 워크플로우는 매일 오전 4시에 트리거되며 데이터를 Analytics에 전송하는 데 24시간이 걸릴 수 있습니다.

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
   >전송된 데이터는 지표 데이터에서 음수 값을 초래할 수 있는 마지막 스냅샷을 기반으로 하는 델타는 됩니다.

   전송된 속성은 다음과 같습니다.

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (작업/@label):캠페인 패키지 **** 가 설치된 경우에만
   * **[!UICONTROL Nature]** (작업/@nature):캠페인 패키지 **** 가 설치된 경우에만
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (예약/@contactDate)



## Adobe Campaign {#tracking-deliveries-in-adobe-campaign}에서 게재 추적

Adobe Campaign에서 게재를 보낸 후 Adobe Experience Cloud이 사이트에서 활동을 추적할 수 있도록 하려면 게재 속성에서 일치하는 커넥터를 참조해야 합니다. 이렇게 하려면 다음 단계를 적용합니다.

1. 추적할 캠페인 게재를 엽니다.

   ![](assets/webanalytics_delivery_properties_003.png)

1. 게재 속성을 엽니다.
1. **[!UICONTROL Web Analytics]** 탭으로 이동하여 이전에 만든 외부 계정을 선택합니다. Adobe Campaign Classic](#external-account-classic)에서 외부 계정 구성 을 참조하십시오.[

   ![](assets/webanalytics_delivery_properties_002.png)

1. 이제 Adobe Analytics에서 게재를 보내고 보고서에 액세스할 수 있습니다.

## 리마케팅 캠페인 만들기 {#creating-a-re-marketing-campaign}

리마케팅 캠페인을 준비하려면 리마케팅 유형 캠페인에 사용할 게재 템플릿을 만들면 됩니다. 그런 다음 리마케팅 캠페인을 구성하고 세그먼트에 연결합니다. 각 세그먼트에는 다른 리마케팅 캠페인이 있어야 합니다.

Adobe Campaign이 초기 캠페인으로 타겟팅된 사람의 동작을 분석하는 세그먼트 복구를 완료하면 리마케팅 캠페인이 자동으로 시작됩니다. 구매하지 않고 장바구니 포기 또는 제품을 보는 경우, 구매에서 사이트 탐색을 종료하기 위해 관련 수신자에게 게재가 전송됩니다.

Adobe Campaign은 캠페인을 준비하기 위해 사용하거나 데이터베이스를 구축할 수 있는 개인화된 게재 템플릿을 제공합니다.

1. **[!UICONTROL Explorer]**&#x200B;에서 Adobe Campaign 트리의 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** 폴더로 이동합니다.

1. **[!UICONTROL Email delivery (re-marketing)]** 템플릿 또는 Adobe Campaign에서 제공하는 리마케팅 템플릿 예제를 복제합니다.

   ![](assets/webanalytics_delivery_model.png)

1. 필요에 따라 템플릿을 개인화하고 저장합니다.

1. 새 캠페인을 만들고 드롭다운 목록에서 **[!UICONTROL Re-marketing campaign]** 템플릿을 선택합니다.

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. **[!UICONTROL Configure...]** 링크를 클릭하여 캠페인에 연결된 세그먼트 및 게재 템플릿을 지정합니다.

1. 이전에 구성한 외부 계정을 선택합니다.

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. 관련 세그먼트를 선택합니다.

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. 이 리마케팅 캠페인에 사용할 게재 템플릿을 선택한 다음 **[!UICONTROL Finish]** 을 클릭하여 창을 닫습니다.

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. **[!UICONTROL OK]** 을 클릭하여 캠페인 창을 닫습니다.

**[!UICONTROL Re-marketing efficiency]** 보고서는 글로벌 보고서 페이지를 통해 액세스합니다. Adobe Campaign 리마케팅 캠페인 이후 장바구니 포기 수와 관련하여 전환된(즉, 구매된) 연락처 수를 볼 수 있도록 해줍니다. 전환율은 Adobe Campaign과 웹 분석 도구 간의 동기화 시작 이후 매주, 월 또는 단위로 계산됩니다.

![](assets/remarketing_reporting.png)