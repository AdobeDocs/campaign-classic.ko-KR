---
product: campaign
title: 웹 애플리케이션 동기화
description: 웹 애플리케이션을 ACS 커넥터와 동기화하는 방법 알아보기
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 1%

---

# 웹 애플리케이션 동기화{#synchronizing-web-applications}



이 사용 사례에서는 Campaign v7 웹 애플리케이션에 대한 링크가 포함된 커뮤니케이션을 Campaign Standard을 사용하여 보냅니다. 수신자가 이메일에 있는 링크를 클릭하면 웹 애플리케이션에 수신자의 데이터가 미리 로드된 여러 필드가 포함된 양식과 뉴스레터에 대한 구독 링크가 표시됩니다. 수신자는 자신의 데이터를 업데이트하고 서비스를 구독할 수 있습니다. 이 프로필은 Campaign v7에서 업데이트되고 정보는 Campaign Standard에서 복제됩니다.

Campaign v7에 많은 서비스와 웹 애플리케이션이 있는 경우 Campaign Standard에서 모두 다시 만들지 않도록 선택할 수 있습니다. ACS 커넥터를 사용하면 기존의 모든 Campaign v7 웹 애플리케이션 및 서비스를 사용하고, 이를 Campaign Standard이 보낸 게재에 연결할 수 있습니다.

## 필수 구성 요소 {#prerequisites}

이를 위해서는 다음이 필요합니다.

* Campaign v7 데이터베이스에 저장되고 Campaign Standard과 동기화된 수신자입니다. [프로필 동기화](../../integrations/using/synchronizing-profiles.md) 섹션을 참조하십시오.
* campaign v7에서 만들고 게시하는 서비스 및 웹 애플리케이션입니다.
* 웹 응용 프로그램에는 **[!UICONTROL Adobe Campaign encryption]** 식별 메서드를 사용하는 **[!UICONTROL Pre-loading]** 활동이 있어야 합니다.

## 웹 애플리케이션 및 서비스 만들기 {#creating-the-web-application-and-service}

Campaign v7에서 수신자가 서비스에 가입할 수 있도록 하는 웹 애플리케이션을 만들 수 있습니다. 웹 애플리케이션과 서비스는 Campaign v7에서 디자인 및 저장되며 Campaign Standard 통신을 통해 이 서비스를 업데이트할 수 있습니다. Campaign v7의 웹 응용 프로그램에 대한 자세한 내용은 [이 섹션](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)을 참조하세요.

Campaign v7에서 다음 개체가 생성되었습니다.

* 뉴스레터 서비스
* **[!UICONTROL Pre-loading]**, **[!UICONTROL Page]** 및 **[!UICONTROL Storage]** 활동이 포함된 웹 응용 프로그램입니다.

1. **[!UICONTROL Resources > Online > Web applications]**(으)로 이동하여 기존 웹 응용 프로그램을 선택하십시오.

   ![](assets/acs_connect_lp_2.png)

1. **[!UICONTROL Preloading]** 활동을 편집합니다. **[!UICONTROL Auto-load data referenced in the form]** 상자를 선택하고 **[!UICONTROL Adobe Campaign encryption]** 식별 방법을 선택합니다. 이렇게 하면 웹 응용 프로그램이 Adobe Campaign 데이터베이스에 저장된 데이터를 사용하여 양식의 필드를 미리 로드할 수 있습니다. [이 문서](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)를 참조하세요.

   ![](assets/acs_connect_lp_4.png)

1. **[!UICONTROL Page]** 편집 받는 사람을 뉴스레터(**[!UICONTROL Newsletter]** 서비스)에 가입하도록 초대하는 확인란뿐만 아니라 세 개의 필드(이름, 전자 메일 및 전화)가 포함되었습니다.

   ![](assets/acs_connect_lp_3.png)

1. **[!UICONTROL Profiles and Target > Services and subscriptions]**(으)로 이동하여 **[!UICONTROL Newsletter]** 서비스를 엽니다. Campaign Standard 통신에서 업데이트할 서비스입니다. 아직 이 서비스를 구독한 수신자가 없음을 확인할 수 있습니다.

   ![](assets/acs_connect_lp_5.png)

1. **[!UICONTROL Profiles and Targets > Recipient]**(으)로 이동하여 받는 사람을 선택하세요. 이 프로필이 아직 서비스를 구독하지 않았음을 알 수 있습니다.

   ![](assets/acs_connect_lp_6.png)

## 데이터 복제 {#replicating-the-data}

Campaign v7과 Campaign Standard 간에 필요한 데이터를 복제하기 위해 몇 가지 복제 워크플로우 템플릿을 사용할 수 있습니다. **[!UICONTROL Profiles replication]** 워크플로는 모든 Campaign v7 수신자를 자동으로 Campaign Standard에 복제합니다. [기술 및 복제 워크플로](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows)를 참조하세요. **[!UICONTROL Landing pages replication]** 워크플로를 사용하면 Campaign Standard에서 사용할 웹 응용 프로그램을 복제할 수 있습니다.

![](assets/acs_connect_lp_1.png)

데이터가 올바르게 복제되었는지 확인하려면 Campaign Standard에서 다음 단계를 수행합니다.

1. 홈 화면에서 **[!UICONTROL Customer profiles]**&#x200B;을(를) 클릭합니다.

   ![](assets/acs_connect_lp_7.png)

1. Campaign v7 수신자를 검색하고 이 수신자가 Campaign Standard에 표시되는지 확인합니다.

   ![](assets/acs_connect_lp_8.png)

1. 상단 표시줄에서 **[!UICONTROL Marketing activities]**&#x200B;을(를) 클릭하고 Campaign v7 웹 애플리케이션을 검색합니다. Campaign Standard에서 랜딩 페이지로 표시됩니다.

   ![](assets/acs_connect_lp_9.png)

1. 왼쪽 상단 모서리에서 **[!UICONTROL Adobe Campaign]** 로고를 클릭한 다음 **프로필 및 대상 > 서비스**&#x200B;를 선택하고 뉴스레터 서비스도 있는지 확인하십시오.

   ![](assets/acs_connect_lp_10.png)

## 이메일 디자인 및 보내기 {#designing-and-sending-the-email}

이 부분에서는 Campaign Standard 이메일에 Campaign v7 웹 애플리케이션에서 복제된 랜딩 페이지에 대한 링크를 포함하는 방법을 알아봅니다.

이메일을 만들고, 디자인하고, 전송하는 단계는 클래식 이메일과 동일합니다. [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/campaign-standard-home.html?lang=ko) 설명서를 참조하세요.

1. 새 이메일을 만들고 복제된 프로필을 하나 이상 대상으로 선택합니다.
1. 콘텐츠를 편집하고 **[!UICONTROL Link to a landing page]**&#x200B;을(를) 삽입합니다.

   ![](assets/acs_connect_lp_12.png)

1. Campaign v7 웹 애플리케이션에서 복제된 랜딩 페이지를 선택합니다.

   ![](assets/acs_connect_lp_13.png)

1. 이메일을 준비하고 증명을 보낸 후 최종 이메일을 전송합니다.
1. 수신자 중 한 명이 이메일을 열고 뉴스레터 구독 링크를 클릭합니다.

   ![](assets/acs_connect_lp_14.png)

1. 이 수신자는 전화 번호를 추가하고 뉴스레터 구독 상자를 확인합니다.

   ![](assets/acs_connect_lp_15.png)

## 업데이트된 정보 검색 {#retrieving-the-updated-information}

수신자가 웹 애플리케이션을 통해에서 데이터를 업데이트하면 Adobe Campaign v7이 업데이트된 정보를 동기적으로 검색합니다. 그런 다음 Campaign v7에서 Campaign Standard으로 복제됩니다.

1. Campaign v7에서 **[!UICONTROL Profiles and Target > Services and subscriptions]**(으)로 이동하여 **[!UICONTROL Newsletter]** 서비스를 엽니다. 이제 수신자가 구독자 목록에 표시되는지 확인할 수 있습니다.

   ![](assets/acs_connect_lp_16.png)

1. **[!UICONTROL Profiles and Targets > Recipient]**(으)로 이동하여 받는 사람을 선택하십시오. 이제 전화번호가 저장되어 있음을 알 수 있습니다.

   ![](assets/acs_connect_lp_17.png)

1. **[!UICONTROL Subscriptions]** 탭에서 이 수신자가 뉴스레터 서비스를 구독했음을 확인할 수도 있습니다.

   ![](assets/acs_connect_lp_18.png)

1. 프로필 복제 워크플로우가 실행될 때까지 잠시 기다립니다.
1. Campaign Standard에서 수신자 프로필에 액세스하여 업데이트된 데이터가 Campaign v7에서 올바르게 복제되었는지 확인합니다.

   ![](assets/acs_connect_lp_19.png)

1. 프로필을 편집합니다. 전화번호가 업데이트된 것을 볼 수 있습니다.

   ![](assets/acs_connect_lp_20.png)

1. **[!UICONTROL Subscriptions]** 탭을 클릭합니다. 이제 뉴스레터 서비스가 표시됩니다.

   ![](assets/acs_connect_lp_21.png)
