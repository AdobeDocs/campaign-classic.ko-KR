---
title: 대상 동기화
seo-title: 대상 동기화
description: 대상 동기화
seo-description: null
page-status-flag: never-activated
uuid: eda67bf7-8a0a-4240-8b31-de364be5d572
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 749a084e-69ee-46b4-b09b-cb91bb1da3cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 대상 동기화{#synchronizing-audiences}

Campaign v7 고급 기능을 사용하여 세련된 목록을 만들고 이 목록을 대상으로 Campaign Standard(추가 데이터 포함)를 통해 실시간으로 직접 공유할 수 있습니다. 그러면 Campaign Standard 사용자는 Adobe Campaign Standard에서 대상을 소비할 수 있습니다.

Campaign Standard에서 복제되지 않은 추가 데이터가 포함된 복잡한 타깃팅은 Campaign v7을 사용해야만 수행할 수 있습니다.

또한 Microsoft Dynamics와 같은 커넥터를 통해 들어오는 수신자 또는 데이터 목록을 Campaign Standard와 간단하게 공유할 수 있습니다.

이 사용 사례는 Campaign v7에서 게재 대상을 준비하는 방법과 Adobe Campaign Standard에서 만들고 보낸 게재에서 이 타겟과 추가 데이터를 재사용하는 방법을 보여줍니다.

>[!NOTE]
>
>필요한 모든 데이터가 이미 복제된 경우 Adobe Campaign Standard의 집계 및 컬렉션을 사용하여 데이터를 강화할 수도 있습니다.

## 사전 요구 사항 {#prerequisites}

이를 실현하려면 다음을 수행해야 합니다.

* 수신자는 Campaign v7 데이터베이스에 저장되고 Campaign Standard와 동기화되었습니다. 프로필 [동기화](../../integrations/using/synchronizing-profiles.md) 섹션을 참조하십시오.
* Campaign v7 데이터베이스의 nms:수신자와 관련된 테이블에 저장된 구독 또는 트랜잭션과 같은 추가 데이터 이러한 데이터는 Campaign v7 OOB 스키마 또는 사용자 지정 테이블에서 가져올 수 있습니다. 동기화되지 않아 기본적으로 Campaign Standard에서 사용할 수 없습니다.
* Campaign v7 및 Campaign Standard 모두에서 워크플로우를 실행할 수 있습니다.
* Campaign Standard에서 배달을 만들고 실행할 권리.

## Campaign v7에서 추가 데이터로 타깃팅 워크플로우 만들기 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Campaign Standard에서 복제되지 않은 추가 데이터가 포함된 복잡한 타깃팅은 Campaign v7을 사용해야만 수행할 수 있습니다.

타겟 및 추가 데이터가 정의되면 Campaign Standard와 공유할 수 있는 목록으로 저장할 수 있습니다.

>[!NOTE]
>
>이 예는 다음과 같습니다. 요구 사항에 따라 수신자 목록을 쿼리하여 추가 처리 없이 ACS와 공유할 수 있습니다. 다른 데이터 관리 활동을 사용하여 최종 목표를 준비할 수도 있습니다.

최종 고객과 추가 데이터를 얻으려면

1. > **[!UICONTROL Profiles and Targets]****[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**&#x200B;에서 새 워크플로우를 만듭니다.
1. 활동을 추가하고 최종 이메일을 보낼 수신자를 선택합니다. **[!UICONTROL Query]** 예를 들어 18세에서 30세 사이의 모든 수신자와 프랑스에서 살고 있습니다.

   ![](assets/acs_connect_query1.png)

1. 쿼리 내에서 데이터를 추가합니다. 자세한 내용은 데이터 추가 [섹션을](../../workflow/using/query.md#adding-data) 참조하십시오.

   이 예에서는 1년 동안 수신자가 받은 배달 수를 계산하기 위해 합계를 추가하는 방법을 보여줍니다.

   에서 **[!UICONTROL Query]**&#x200B;을 선택합니다 **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. 을 선택하고 **[!UICONTROL Data linked to the filtering dimension]** 클릭합니다 **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. 노드를 **[!UICONTROL Data linked to the filtering dimension]** 선택한 다음 **[!UICONTROL Recipient delivery logs]** 을 클릭합니다 **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. 필드에서 **[!UICONTROL Aggregates]** 를 **[!UICONTROL Data collected]** 선택하고 을 **[!UICONTROL Next]**&#x200B;클릭합니다.

   ![](assets/acs_connect_query5.png)

1. 지난 365일 동안 생성된 계정 로그만 고려하려면 필터링 조건을 추가하고 **[!UICONTROL Next]**&#x200B;클릭합니다.

   ![](assets/acs_connect_query6.png)

1. 출력 열을 정의합니다. 여기에서 필요한 열은 배달 수를 계산하는 열뿐입니다. 그렇게 하려면:

   * 창 **[!UICONTROL Add]** 오른쪽에서 선택합니다.
   * 창에서 **[!UICONTROL Select field]** 을 클릭합니다 **[!UICONTROL Advanced selection]**.
   * 을 **[!UICONTROL Aggregate]**&#x200B;선택한 다음 **[!UICONTROL Count]**&#x200B;선택합니다. 옵션을 **[!UICONTROL Distinct]** 선택하고 을 클릭합니다 **[!UICONTROL Next]**.
   * 필드 목록에서 Count 함수에 사용되는 필드를 **선택합니다** . 필드와 같이 항상 채워질 필드를 선택하고 **[!UICONTROL Primary key]** 을 클릭합니다 **[!UICONTROL Finish]**.
   * 열에서 표현식을 **[!UICONTROL Alias]** 변경합니다. 이 별칭을 사용하면 최종 배달에서 추가된 열을 쉽게 검색할 수 있습니다. 예: **NBdelivery**.
   * 활동 구성을 **[!UICONTROL Finish]** **[!UICONTROL Query]** 클릭하고 저장합니다.
   ![](assets/acs_connect_query7.png)

1. 워크플로우를 저장합니다. 다음 섹션에서는 ACS와 인구를 공유하는 방법을 보여줍니다.

## Campaign Standard와 타겟 공유 {#share-the-target-with-campaign-standard}

타겟 모집단이 정의되면 **[!UICONTROL List update]** 활동을 통해 ACS와 공유할 수 있습니다.

1. 이전에 만든 워크플로우에서 **[!UICONTROL List update]** 활동을 추가하고 업데이트하거나 만들 목록을 지정합니다.

   Campaign v7에서 목록을 저장할 폴더를 지정합니다. 목록은 구현 중에 정의된 폴더 매핑의 적용을 받으며, Campaign Standard에서 공유되면 방문자에게 영향을 줄 수 있습니다. 권한 [전환](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) 섹션을 참조하십시오.

1. 옵션이 선택되어 있는지 **[!UICONTROL Share with ACS]** 확인합니다. 기본적으로 선택되어 있습니다.

   ![](assets/acs_connect_listupdate1.png)

1. 워크플로우를 저장하고 실행합니다.

   타겟 및 추가 데이터는 Campaign v7의 목록에 저장되고 Campaign Standard의 목록 대상으로서 즉시 공유됩니다. 복제된 프로필만 ACS와 공유됩니다.

활동에 오류가 발생하면 Campaign Standard와의 동기화가 실패했을 수 있습니다. **[!UICONTROL List update]** 잘못된 내용에 대한 자세한 내용을 보려면 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**&#x200B;를 참조하십시오. 이 폴더에는 **[!UICONTROL List update]** 활동 실행에 의해 트리거된 동기화 워크플로우가 포함되어 있습니다. ACS 커넥터 [문제 해결 섹션을 참조하십시오](../../integrations/using/troubleshooting-the-acs-connector.md) .

## Campaign Standard에서 데이터를 검색하고 배달에서 사용 {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

타깃팅 워크플로가 Campaign v7에서 실행되면 Campaign Standard의 **[!UICONTROL Audiences]** 메뉴에서 읽기 전용 모드에서 목록 대상을 찾을 수 있습니다.

![](assets/acs_connect_deliveryworkflow_audience.png)

그런 다음 Campaign Standard에서 게재 워크플로우를 만들면 이 대상뿐만 아니라 게시에 포함된 추가 데이터를 사용할 수 있습니다.

1. 메뉴에서 새 워크플로우를 **[!UICONTROL Marketing activities]** 만듭니다.
1. 활동을 추가하고 Campaign v7에서 이전에 공유한 대상을 선택합니다. **[!UICONTROL Read audience]**

   이 활동은 선택한 대상의 데이터를 검색하는 데 사용됩니다. 필요한 **[!UICONTROL Source Filtering]** 경우 이 활동의 [기준] 탭을 사용하여 추가 항목을 적용할 수도 있습니다.

1. 활동을 추가하고 다른 **[!UICONTROL Email delivery]** 이메일 배달 활동으로 [](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)구성합니다.
1. 게재 컨텐츠를 엽니다.
1. 개인화 필드를 추가합니다. 팝업에서 **[!UICONTROL Additional data (targetData)]** 노드를 찾습니다. 이 노드에는 초기 타깃팅 워크플로우에서 계산된 대상의 추가 데이터가 포함됩니다. 다른 개인화 필드로 사용할 수 있습니다.

   이 예에서는 원래 타깃팅 워크플로우에서 오는 추가 데이터가 지난 365일 동안 각 수신자에게 전송된 배달 수입니다. 타깃팅 워크플로우에 지정된 NBdelivery 별칭은 여기에 표시됩니다.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. 전달 및 워크플로우를 저장합니다.

   이제 워크플로우를 실행할 준비가 되었습니다. 배달이 분석되고 전송될 준비가 됩니다.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## 전달 보내기 및 모니터링 {#send-and-monitor-your-delivery}

게재와 컨텐츠가 준비되면 [이 섹션에](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)설명된 대로 배달을 보내십시오.

1. 배달 워크플로우를 실행합니다. 이 단계에서는 이메일을 보낼 수 있도록 준비합니다.
1. 배달 대시보드에서 배달이 전송될 수 있는지 수동으로 확인합니다.
1. 배달 보고서 및 로그 모니터링:

   * **Campaign Standard에서**:게재와 관련된 [보고서](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) 및 [로그에](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) 모든 전달에 대해 액세스할 수 있습니다.
   * **캠페인 v7 및 캠페인 표준에서**:배달 ID, 이메일 확장 로그 및 이메일 추적 로그가 Campaign v7에 동기화됩니다. 그런 다음 Campaign v7에서 마케팅 캠페인을 360° 볼 수 있습니다.

      Quarantine은 Campaign v7로 자동 다시 동기화됩니다. 따라서 Campaign v7에서 수행된 다음 타깃팅을 고려하여 산출물이 아닌 정보를 고려할 수 있습니다.

      Campaign Standard에서 격리 관리에 대한 자세한 내용은 [이 섹션에서](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)찾을 수 있습니다.

