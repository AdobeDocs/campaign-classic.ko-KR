---
solution: Campaign Classic
product: campaign
title: 대상 동기화
description: 대상 동기화
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 1%

---

# 대상 동기화{#synchronizing-audiences}

Campaign v7 고급 기능을 사용하여 정교한 목록을 작성하고 이 목록을 Campaign Standard(추가 데이터 포함)와 직접 실시간으로 원활하게 공유할 수 있습니다. 그런 다음 Campaign Standard 사용자는 Adobe Campaign Standard에서 대상을 소비할 수 있습니다.

Campaign Standard에서 복제되지 않은 추가 데이터를 포함하는 복잡한 타깃팅은 Campaign v7만 사용하면 됩니다.

또한 Microsoft Dynamics와 같은 커넥터를 통해 받는 수신자 또는 데이터 목록을 Campaign Standard과 공유할 수도 있습니다.

이 사용 사례에서는 Campaign v7에서 게재 대상을 준비하는 방법과 Adobe Campaign Standard을 사용하여 만들어 보낸 게재에서 이 타겟 및 추가 데이터를 다시 사용하는 방법을 보여줍니다.

>[!NOTE]
>
>필요한 모든 데이터가 이미 복제되어 있는 경우 Adobe Campaign Standard의 집계 및 컬렉션을 사용하여 데이터를 보강할 수도 있습니다.

## 필수 구성 요소 {#prerequisites}

이를 위해서는 다음을 수행해야 합니다.

* Campaign v7 데이터베이스에 저장되고 Campaign Standard과 동기화된 수신자입니다. [프로필 동기화](../../integrations/using/synchronizing-profiles.md) 섹션을 참조하십시오.
* Campaign v7 데이터베이스의 nms:recipients와 관련된 테이블에 저장된 구독 또는 트랜잭션과 같은 추가 데이터. 이러한 데이터는 Campaign v7 OOB 스키마나 사용자 지정 테이블에서 얻을 수 있습니다. 동기화되지 않으므로 기본적으로 Campaign Standard에서 사용할 수 없습니다.
* Campaign v7 및 Campaign Standard 모두에서 워크플로우를 실행할 수 있는 권한.
* Campaign Standard에서 게재를 만들고 실행할 수 있는 권한.

## Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}에서 추가 데이터를 사용하여 타깃팅 워크플로우를 만듭니다.

Campaign Standard에서 복제되지 않은 추가 데이터를 포함하는 복잡한 타깃팅은 Campaign v7만 사용하면 됩니다.

타겟 및 추가 데이터가 정의되면 Campaign Standard과 공유할 수 있는 목록으로 저장할 수 있습니다.

>[!NOTE]
>
>이 예는 다음과 같습니다. 요구 사항에 따라 수신자 목록을 쿼리하고 추가 처리 없이 ACS와 공유할 수 있습니다. 다른 데이터 관리 활동을 사용하여 최종 타겟을 준비할 수도 있습니다.

최종 대상자 및 추가 데이터를 가져오려면 다음을 수행하십시오.

1. **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**&#x200B;에서 새 워크플로우를 만듭니다.
1. **[!UICONTROL Query]** 활동을 추가하고 최종 이메일을 보낼 수신자를 선택합니다. 예를 들어, 18세에서 30세 사이의 모든 수신자와 프랑스에 살고 있습니다.

   ![](assets/acs_connect_query1.png)

1. 쿼리 내에서 추가 데이터를 추가합니다. 자세한 내용은 [데이터 추가](../../workflow/using/query.md#adding-data) 섹션을 참조하십시오.

   이 예제에서는 1년에 받은 게재 수를 계산하기 위해 합계를 추가하는 방법을 보여줍니다.

   **[!UICONTROL Query]**&#x200B;에서 **[!UICONTROL Add data...]**&#x200B;을 선택합니다.

   ![](assets/acs_connect_query2.png)

1. **[!UICONTROL Data linked to the filtering dimension]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다 .

   ![](assets/acs_connect_query3.png)

1. **[!UICONTROL Data linked to the filtering dimension]** 을 선택한 다음 **[!UICONTROL Recipient delivery logs]** 노드를 선택하고 **[!UICONTROL Next]** 를 클릭합니다.

   ![](assets/acs_connect_query4.png)

1. **[!UICONTROL Data collected]** 필드에서 **[!UICONTROL Aggregates]**&#x200B;을 선택하고 **[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/acs_connect_query5.png)

1. 지난 365일 동안 생성된 계정 로그만 고려하려면 필터링 조건을 추가하고 **[!UICONTROL Next]** 을 클릭합니다.

   ![](assets/acs_connect_query6.png)

1. 출력 열을 정의합니다. 여기에서 필요한 열은 게재 수를 계산하는 열뿐입니다. 방법은 다음과 같습니다.

   * 창 오른쪽에서 **[!UICONTROL Add]** 을 선택합니다.
   * **[!UICONTROL Select field]** 창에서 **[!UICONTROL Advanced selection]** 을 클릭합니다.
   * **[!UICONTROL Aggregate]**, **[!UICONTROL Count]** 순으로 선택합니다. **[!UICONTROL Distinct]** 옵션을 선택하고 **[!UICONTROL Next]** 를 클릭합니다.
   * 필드 목록에서 **Count** 함수에 사용되는 필드를 선택합니다. 항상 채울 필드(예: **[!UICONTROL Primary key]** 필드)를 선택하고 **[!UICONTROL Finish]** 를 클릭합니다.
   * **[!UICONTROL Alias]** 열에서 표현식을 변경합니다. 이 별칭을 사용하면 최종 게재에서 추가된 열을 쉽게 검색할 수 있습니다. 예: **NBdeliveries**
   * **[!UICONTROL Finish]** 을 클릭하고 **[!UICONTROL Query]** 활동 구성을 저장합니다.

   ![](assets/acs_connect_query7.png)

1. 워크플로우를 저장합니다. 다음 섹션에서는 ACS와 모집단을 공유하는 방법을 보여줍니다.

## Campaign Standard {#share-the-target-with-campaign-standard}과 대상 공유

대상 모집단이 정의되면 **[!UICONTROL List update]** 활동을 통해 ACS와 공유할 수 있습니다.

1. 이전에 만든 워크플로우에서 **[!UICONTROL List update]** 활동을 추가하고 업데이트하거나 만들 목록을 지정합니다.

   Campaign v7에 목록을 저장할 폴더를 지정합니다. 목록은 Campaign Standard에서 공유되면 구현 중에 정의된 폴더 매핑에 따라 영향을 받을 수 있습니다. [권한 변환](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) 섹션을 참조하십시오.

1. **[!UICONTROL Share with ACS]** 옵션이 선택되어 있는지 확인합니다. 기본적으로 선택되어 있습니다.

   ![](assets/acs_connect_listupdate1.png)

1. 워크플로우를 저장하고 실행합니다.

   타겟 및 추가 데이터는 Campaign v7의 목록에 저장되고 Campaign Standard의 목록 대상으로 즉시 공유됩니다. 복제된 프로필만 ACS와 공유됩니다.

**[!UICONTROL List update]** 활동에서 오류가 발생하면 Campaign Standard과 동기화에 실패했을 수 있습니다. 잘못된 내용에 대한 자세한 내용을 보려면 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**&#x200B;로 이동하십시오. 이 폴더에는 **[!UICONTROL List update]** 활동 실행에 의해 트리거되는 동기화 워크플로우가 포함되어 있습니다. [ACS 커넥터 문제 해결](../../integrations/using/troubleshooting-the-acs-connector.md) 섹션을 참조하십시오.

## Campaign Standard에서 데이터를 검색하고 배달 {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}에서 사용합니다.

Campaign v7에서 타깃팅 워크플로우를 실행하면 Campaign Standard의 **[!UICONTROL Audiences]** 메뉴에서 읽기 전용 모드로 목록 대상자를 찾을 수 있습니다.

![](assets/acs_connect_deliveryworkflow_audience.png)

Campaign Standard에서 게재 워크플로우를 만들면 이 대상자와 게재에 포함된 추가 데이터를 사용할 수 있습니다.

1. **[!UICONTROL Marketing activities]** 메뉴에서 새 워크플로우를 만듭니다.
1. **[!UICONTROL Read audience]** 활동을 추가하고 Campaign v7에서 이전에 공유한 대상을 선택합니다.

   이 활동은 선택한 대상자의 데이터를 검색하는 데 사용됩니다. 필요한 경우 이 활동의 해당하는 탭을 사용하여 추가 **[!UICONTROL Source Filtering]**&#x200B;을 적용할 수도 있습니다.

1. **[!UICONTROL Email delivery]** 활동을 추가하고 다른 [이메일 게재 활동](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)으로 구성합니다.
1. 게재 콘텐츠를 엽니다.
1. 개인화 필드 추가. 팝업에서 **[!UICONTROL Additional data (targetData)]** 노드를 찾습니다. 이 노드에는 초기 타겟팅 워크플로우에서 계산된 대상자의 추가 데이터가 포함되어 있습니다. 이를 다른 개인화 필드로 사용할 수 있습니다.

   이 예제의 경우 원래 타겟팅 워크플로우에서 가져오는 추가 데이터는 최근 365일 동안 각 수신자에게 전송된 게재의 수입니다. 타겟팅 워크플로우에 지정된 NBdeliveries 별칭은 여기에 표시됩니다.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. 게재 및 워크플로우를 저장합니다.

   이제 워크플로우를 실행할 준비가 되었습니다. 게재를 분석하고 전송할 준비가 되었습니다.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## 게재 보내기 및 모니터링 {#send-and-monitor-your-delivery}

게재와 해당 컨텐츠가 준비되면 게재를 전송합니다.

1. 게재 워크플로우를 실행합니다. 이 단계에서는 전송을 위한 이메일을 준비합니다.
1. 게재 대시보드에서 게재를 보낼 수 있는지 수동으로 확인합니다.
1. 게재 보고서 및 로그를 모니터링합니다.

   * **Campaign Standard**:게재 [](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) 에  [](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) 대해 게재 관련 보고서 및 로그에 액세스합니다.
   * **Campaign v7 및 Campaign Standard**:게재 ID, 이메일 브로드 로그 및 이메일 추적 로그는 Campaign v7과 동기화됩니다. 그런 다음 Campaign v7에서 마케팅 캠페인을 360° 볼 수 있습니다.

      격리는 자동으로 Campaign v7로 다시 동기화됩니다. 이렇게 하면 Campaign v7에서 수행된 다음 타깃팅을 위해 산출물이 아닌 정보를 고려할 수 있습니다.

      [이 섹션](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en)에서 Campaign Standard에서 격리 관리에 대한 자세한 정보를 찾을 수 있습니다.
