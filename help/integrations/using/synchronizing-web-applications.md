---
title: 웹 애플리케이션 동기화
seo-title: 웹 애플리케이션 동기화
description: 웹 애플리케이션 동기화
seo-description: null
page-status-flag: never-activated
uuid: da74e4d3-e439-454a-8a43-6784e4789d1b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: df68ab11-7a8b-4e89-8cc4-8764e8a859b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 웹 애플리케이션 동기화{#synchronizing-web-applications}

이 사용 사례에서는 Campaign v7 웹 애플리케이션에 대한 링크가 포함된 Campaign Standard를 사용하여 통신을 보냅니다. 받는 사람이 이메일의 링크를 클릭하면 웹 응용 프로그램에 받는 사람의 데이터가 미리 로드되는 필드 및 뉴스레터에 대한 구독 링크가 포함된 양식이 표시됩니다. 수신자는 데이터를 업데이트하고 서비스에 가입할 수 있습니다. 이 프로필은 Campaign v7에서 업데이트되며 정보는 Campaign Standard에서 복제됩니다.

Campaign v7에 많은 서비스 및 웹 애플리케이션이 있는 경우 Campaign Standard에서 모두 다시 만들지 않도록 선택할 수 있습니다. ACS 커넥터를 사용하면 모든 기존 Campaign v7 웹 애플리케이션 및 서비스를 사용하고 이를 Campaign Standard에서 보낸 게재에 연결할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

이를 실현하려면 다음을 수행해야 합니다.

* 수신자는 Campaign v7 데이터베이스에 저장되고 Campaign Standard와 동기화되었습니다. 프로필 [동기화](../../integrations/using/synchronizing-profiles.md) 섹션을 참조하십시오.
* Campaign v7에서 만들고 게시한 서비스 및 웹 애플리케이션.
* 웹 응용 프로그램에는 **[!UICONTROL Pre-loading]** **[!UICONTROL Adobe Campaign encryption]** 식별 방법을 사용하는 활동이 포함되어야 합니다.

## 웹 응용 프로그램 및 서비스 만들기 {#creating-the-web-application-and-service}

Campaign v7에서 수신자가 서비스에 가입할 수 있는 웹 애플리케이션을 만들 수 있습니다. 웹 응용 프로그램 및 서비스는 Campaign v7에서 디자인되고 저장되며 Campaign Standard 통신을 통해 이 서비스를 업데이트할 수 있습니다. Campaign v7의 웹 애플리케이션에 대한 자세한 내용은 [이 섹션을](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)참조하십시오.

Campaign v7에서 다음 개체가 만들어졌습니다.

* 뉴스레터 서비스
* 활동, **[!UICONTROL Pre-loading]**&#x200B;및 **[!UICONTROL Page]** **[!UICONTROL Storage]** 활동을 포함하는 웹 응용 프로그램.

1. 기존 웹 응용 프로그램으로 **[!UICONTROL Resources > Online > Web applications]** 이동하여 선택합니다.

   ![](assets/acs_connect_lp_2.png)

1. 활동을 **[!UICONTROL Preloading]** 편집합니다. 이 **[!UICONTROL Auto-load data referenced in the form]** 상자를 선택하면 **[!UICONTROL Adobe Campaign encryption]** 식별 방법이 선택됩니다. 이렇게 하면 웹 응용 프로그램에서 Adobe Campaign 데이터베이스에 저장된 데이터로 양식 필드를 미리 로드할 수 있습니다. 이 [문서를](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)참조하십시오.

   ![](assets/acs_connect_lp_4.png)

1. 를 **[!UICONTROL Page]**&#x200B;편집합니다. 세 개의 필드(이름, 이메일 및 전화)와 수신자를 뉴스레터(**[!UICONTROL Newsletter]** 서비스)에 가입하도록 초대하는 확인란이 포함되어 있습니다.

   ![](assets/acs_connect_lp_3.png)

1. 가서 **[!UICONTROL Profiles and Target > Services and subscriptions]** 서비스를 **[!UICONTROL Newsletter]** 엽니다. Campaign Standard 통신에서 업데이트되는 서비스입니다. 받는 사람이 이 서비스에 아직 가입하지 않은 것을 확인할 수 있습니다.

   ![](assets/acs_connect_lp_5.png)

1. 수신자를 **[!UICONTROL Profiles and Targets > Recipient]** 선택합니다. 그가 아직 그 서비스에 가입하지 않은 것을 볼 수 있다.

   ![](assets/acs_connect_lp_6.png)

## 데이터 복제 {#replicating-the-data}

Campaign v7과 Campaign Standard 간에 필요한 데이터를 복제하기 위해 몇 가지 복제 워크플로 템플릿을 사용할 수 있습니다. 워크플로우는 모든 Campaign v7 받는 사람을 Campaign Standard에 자동으로 복제합니다. **[!UICONTROL Profiles replication]** 기술 [및 복제 워크플로우를](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows)참조하십시오. 이 **[!UICONTROL Landing pages replication]** 워크플로우는 Campaign Standard에서 사용할 웹 애플리케이션을 복제할 수 있도록 합니다.

![](assets/acs_connect_lp_1.png)

데이터가 올바르게 복제되었는지 확인하려면 캠페인 표준의 다음 단계를 따르십시오.

1. 홈 화면에서 을 클릭합니다 **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Campaign v7 수신자를 검색하고 Campaign Standard에 표시되는지 확인합니다.

   ![](assets/acs_connect_lp_8.png)

1. 상단 막대에서 을 클릭하고 Campaign v7 웹 애플리케이션을 **[!UICONTROL Marketing activities]**&#x200B;검색합니다. Campaign Standard에 랜딩 페이지로 표시됩니다.

   ![](assets/acs_connect_lp_9.png)

1. 왼쪽 상단 모서리에서 **[!UICONTROL Adobe Campaign]** 로고를 클릭한 다음 프로필 **및 대상 > 서비스를** 선택하고 Newsletter 서비스도 있는지 확인합니다.

   ![](assets/acs_connect_lp_10.png)

## 이메일 디자인 및 보내기 {#designing-and-sending-the-email}

이 부분에서는 Campaign Standard 이메일에 Campaign v7 웹 애플리케이션에서 복제된 랜딩 페이지에 대한 링크를 포함하는 방법을 살펴봅니다.

이메일을 만들고 디자인하고 보내는 단계는 클래식 이메일과 동일합니다. Adobe Campaign [Standard](https://helpx.adobe.com/support/campaign/standard.html) 설명서를 참조하십시오.

1. 새 이메일을 만들고 하나 이상의 복제된 프로필을 대상으로 선택합니다.
1. 컨텐츠를 편집하고 컨텐츠를 삽입할 수 **[!UICONTROL Link to a landing page]**&#x200B;있습니다.

   ![](assets/acs_connect_lp_12.png)

1. Campaign v7 웹 애플리케이션에서 복제된 랜딩 페이지를 선택합니다.

   ![](assets/acs_connect_lp_13.png)

1. 이메일을 준비하고 교정본을 보내 최종 이메일을 보낼 수 있습니다.
1. 받는 사람 중 한 명이 이메일을 열고 Newsletter 구독 링크를 클릭합니다.

   ![](assets/acs_connect_lp_14.png)

1. 전화 번호를 추가하고 뉴스레터 구독 상자를 확인합니다.

   ![](assets/acs_connect_lp_15.png)

## 업데이트된 정보 검색 {#retrieving-the-updated-information}

수신자가 웹 애플리케이션을 통해 데이터를 업데이트할 때 Adobe Campaign v7은 업데이트된 정보를 동기적으로 검색합니다. 그런 다음 Campaign v7에서 Campaign Standard로 복제됩니다.

1. Campaign v7에서 이동 **[!UICONTROL Profiles and Target > Services and subscriptions]** 및 **[!UICONTROL Newsletter]** 서비스를 엽니다. 이제 수신자가 가입자 목록에 표시됩니다.

   ![](assets/acs_connect_lp_16.png)

1. 수신자로 **[!UICONTROL Profiles and Targets > Recipient]** 이동하여 수신자를 선택합니다. 이제 전화 번호가 저장되었음을 알 수 있습니다.

   ![](assets/acs_connect_lp_17.png)

1. 또한 **[!UICONTROL Subscriptions]** 탭에서 뉴스레터 서비스에 가입했음을 확인할 수 있습니다.

   ![](assets/acs_connect_lp_18.png)

1. 프로필 복제 워크플로우가 실행되도록 몇 분 정도 기다립니다.
1. Campaign Standard에서 수신자 프로필에 액세스하여 업데이트된 데이터가 Campaign v7에서 올바르게 복제되었는지 확인합니다.

   ![](assets/acs_connect_lp_19.png)

1. 프로필을 편집합니다. 전화 번호가 업데이트되었음을 알 수 있습니다.

   ![](assets/acs_connect_lp_20.png)

1. 탭을 **[!UICONTROL Subscriptions]** 클릭합니다. 이제 뉴스레터 서비스가 표시됩니다.

   ![](assets/acs_connect_lp_21.png)

