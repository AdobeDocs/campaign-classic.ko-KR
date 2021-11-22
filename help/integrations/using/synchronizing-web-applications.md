---
product: campaign
title: 웹 애플리케이션 동기화
description: 웹 애플리케이션 동기화
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# 웹 애플리케이션 동기화{#synchronizing-web-applications}

![](../../assets/v7-only.svg)

이 사용 사례에서는 Campaign v7 웹 애플리케이션에 대한 링크가 포함된 Campaign Standard을 사용하여 커뮤니케이션을 보냅니다. 수신자가 이메일의 링크를 클릭하면 웹 애플리케이션에는 수신자의 데이터가 미리 로드된 여러 개의 필드가 포함된 양식과 뉴스레터 구독 링크가 표시됩니다. 수신자는 데이터를 업데이트하고 서비스를 구독할 수 있습니다. 이 프로필은 Campaign v7에서 업데이트되고 정보는 Campaign Standard에서 복제됩니다.

Campaign v7에 많은 서비스와 웹 응용 프로그램이 있는 경우 Campaign Standard에서 모든 서비스 및 웹 응용 프로그램을 다시 만들지 않도록 선택할 수 있습니다. ACS 커넥터를 사용하면 기존의 모든 Campaign v7 웹 애플리케이션 및 서비스를 사용하고 이를 Campaign Standard이 보낸 게재에 연결할 수 있습니다.

## 필수 구성 요소 {#prerequisites}

이를 위해서는 다음을 수행해야 합니다.

* Campaign v7 데이터베이스에 저장되고 Campaign Standard과 동기화된 수신자입니다. 자세한 내용은 [프로필 동기화](../../integrations/using/synchronizing-profiles.md) 섹션을 참조하십시오.
* Campaign v7에서 만들고 게시된 서비스 및 웹 애플리케이션입니다.
* 웹 응용 프로그램에는 **[!UICONTROL Pre-loading]** 활동을 사용하여 **[!UICONTROL Adobe Campaign encryption]** 식별 방법.

## 웹 응용 프로그램 및 서비스 만들기 {#creating-the-web-application-and-service}

Campaign v7에서는 수신자가 서비스에 가입하도록 허용하는 웹 애플리케이션을 만들 수 있습니다. 웹 애플리케이션 및 서비스는 Campaign v7에 설계 및 저장되며 Campaign Standard 통신을 통해 이 서비스를 업데이트할 수 있습니다. Campaign v7의 웹 애플리케이션에 대한 자세한 내용은 [이 섹션](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

Campaign v7에서 다음 개체가 생성되었습니다.

* 뉴스레터 서비스
* 를 포함하는 웹 애플리케이션 **[!UICONTROL Pre-loading]**, **[!UICONTROL Page]** 그리고 **[!UICONTROL Storage]** 활동.

1. 이동 **[!UICONTROL Resources > Online > Web applications]** 기존 웹 응용 프로그램을 선택합니다.

   ![](assets/acs_connect_lp_2.png)

1. 편집 **[!UICONTROL Preloading]** 활동. 다음 **[!UICONTROL Auto-load data referenced in the form]** 상자를 선택하고 **[!UICONTROL Adobe Campaign encryption]** 식별 방법이 선택되어 있습니다. 이렇게 하면 웹 애플리케이션에서 Adobe Campaign 데이터베이스에 저장된 데이터로 양식 필드를 미리 로드할 수 있습니다. 자세한 내용은 [이 문서](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. 편집 **[!UICONTROL Page]**. 3개의 필드(이름, 이메일 및 전화)와 수신자를 뉴스레터에 가입하도록 초대하는 확인란(이름, 이메일 및 전화)이 포함되었습니다&#x200B;**[!UICONTROL Newsletter]** 서비스).

   ![](assets/acs_connect_lp_3.png)

1. 이동 **[!UICONTROL Profiles and Target > Services and subscriptions]** 그리고 **[!UICONTROL Newsletter]** 서비스. Campaign Standard 통신에서 업데이트할 서비스입니다. 수신자가 아직 이 서비스를 구독하지 않았음을 알 수 있습니다.

   ![](assets/acs_connect_lp_5.png)

1. 이동 **[!UICONTROL Profiles and Targets > Recipient]** 수신자를 선택합니다. 이 프로필이 아직 서비스를 구독하지 않았음을 알 수 있습니다.

   ![](assets/acs_connect_lp_6.png)

## 데이터 복제 {#replicating-the-data}

Campaign v7와 Campaign Standard 간에 필요한 데이터를 복제하기 위해 몇 개의 복제 워크플로우 템플릿을 사용할 수 있습니다. 다음 **[!UICONTROL Profiles replication]** 워크플로우는 모든 Campaign v7 수신자를 자동으로 Campaign Standard에 복제합니다. 자세한 내용은 [기술 및 복제 워크플로우](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). 다음 **[!UICONTROL Landing pages replication]** 작업 과정을 통해 Campaign Standard에 사용할 웹 응용 프로그램을 복제할 수 있습니다.

![](assets/acs_connect_lp_1.png)

데이터가 올바르게 복제되었는지 확인하려면 Campaign Standard에서 다음 단계를 수행합니다.

1. 홈 화면에서 **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Campaign v7 수신자를 검색하고 이 수신자가 Campaign Standard에 표시되는지 확인합니다.

   ![](assets/acs_connect_lp_8.png)

1. 상단 막대에서 을(를) 클릭합니다. **[!UICONTROL Marketing activities]**, 그리고 Campaign v7 웹 애플리케이션을 검색합니다. 랜딩 페이지로 표시됩니다.

   ![](assets/acs_connect_lp_9.png)

1. 을(를) 클릭합니다. **[!UICONTROL Adobe Campaign]** 왼쪽 상단 모서리에서 로고를 선택한 다음 **프로필 및 대상 > 서비스** 그리고 뉴스레터 서비스가 있는지 확인합니다.

   ![](assets/acs_connect_lp_10.png)

## 이메일 디자인 및 보내기 {#designing-and-sending-the-email}

이 부분에서는 Campaign Standard 이메일에 Campaign v7 웹 애플리케이션에서 복제된 랜딩 페이지에 링크를 포함하는 방법을 살펴봅니다.

이메일을 만들고, 디자인하고 보내는 단계는 클래식 이메일과 동일합니다. 자세한 내용은 [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=ko) 설명서.

1. 새 이메일을 만들고 하나 이상의 복제된 프로필을 대상으로 선택합니다.
1. 콘텐츠를 편집하고 삽입 **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Campaign v7 웹 애플리케이션에서 복제된 랜딩 페이지를 선택합니다.

   ![](assets/acs_connect_lp_13.png)

1. 이메일을 준비하고 증명을 보내고 최종 이메일을 보냅니다.
1. 수신자 중 한 명이 이메일을 열고 뉴스레터 구독 링크를 클릭합니다.

   ![](assets/acs_connect_lp_14.png)

1. 이 수신자는 전화 번호를 추가하고 뉴스레터 구독 상자를 확인합니다.

   ![](assets/acs_connect_lp_15.png)

## 업데이트된 정보 검색 {#retrieving-the-updated-information}

수신자가 웹 애플리케이션을 통해 데이터를 업데이트하면 Adobe Campaign v7이 업데이트된 정보를 동기식으로 검색합니다. 그런 다음 Campaign v7에서 Campaign Standard으로 복제됩니다.

1. Campaign v7에서 **[!UICONTROL Profiles and Target > Services and subscriptions]** 그리고 **[!UICONTROL Newsletter]** 서비스. 수신자가 이제 구독자 목록에 표시되는지 확인할 수 있습니다.

   ![](assets/acs_connect_lp_16.png)

1. 이동 **[!UICONTROL Profiles and Targets > Recipient]** 수신자를 선택합니다. 이제 전화번호도 저장되어 있는 것을 보실 수 있습니다.

   ![](assets/acs_connect_lp_17.png)

1. 에서 **[!UICONTROL Subscriptions]** 탭에서는 이 수신자가 뉴스레터 서비스에 가입되었음을 확인할 수도 있습니다.

   ![](assets/acs_connect_lp_18.png)

1. 프로필 복제 워크플로우가 실행될 때까지 몇 분 정도 기다립니다.
1. Campaign Standard에서 수신자 프로필에 액세스하여 업데이트된 데이터가 Campaign v7에서 올바르게 복제되었는지 확인합니다.

   ![](assets/acs_connect_lp_19.png)

1. 프로필을 편집합니다. 전화 번호가 갱신되었음을 알 수 있습니다.

   ![](assets/acs_connect_lp_20.png)

1. 을(를) 클릭합니다. **[!UICONTROL Subscriptions]** 탭. 이제 뉴스레터 서비스가 나타납니다.

   ![](assets/acs_connect_lp_21.png)
