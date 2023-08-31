---
product: campaign
title: LINE 게재 만들기
description: LINE 메시지를 만드는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Line App
role: User
exl-id: 1baaabbd-9fd7-4d9b-b78e-d2a559d7dddb
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 3%

---

# LINE 게재 만들기{#line-channel}



[!DNL LINE] 은 모든 모바일 OS 및 PC에서 사용할 수 있는 무료 인스턴트 메시징, 음성 및 비디오 통화를 위한 애플리케이션입니다.

[!DNL LINE] 또한 트랜잭션 메시지 모듈과 결합하여 [!DNL LINE] 소비자 모바일 장치에 설치된 앱입니다. 자세한 정보는 이 [페이지](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line)를 참조하십시오.

![](assets/line_message.png)

사용 단계 [!DNL LINE] 채널:

1. [LINE 채널 설정](#setting-up-line-channel)
1. [게재 만들기](#creating-the-delivery)
1. [콘텐츠 유형 구성](#defining-the-content)
1. [게재 모니터링(추적, 격리, 보고서 등)](#accessing-reports)

## LINE 채널 설정 {#setting-up-line-channel}

만들기 전 [!DNL LINE] 계정 및 외부 계정에서는 먼저 인스턴스에 LINE 패키지를 설치해야 합니다. 자세한 내용은 [이 섹션](../../installation/using/installing-campaign-standard-packages.md#line-package).

먼저 다음을 만들어야 합니다. [!DNL LINE] 계정이 포함되어 있으므로 Adobe Campaign에 연결할 수 있습니다. 그런 다음 를 보낼 수 있습니다. [!DNL LINE] 을(를) 추가한 사용자에게 메시지 [!DNL LINE] 모바일 애플리케이션의 계정입니다. 외부 계정 및 [!DNL LINE] 계정은 플랫폼의 기능 관리자만 관리할 수 있습니다.

을(를) 만들고 구성하려면 [!DNL LINE] account, 참조 [LINE 개발자 설명서](https://developers.line.me/).

### LINE 서비스 만들기 및 구성 {#configure-line-service}

다음을 만들려면 [!DNL LINE] 서비스:

1. Adobe Campaign Classic 홈 페이지에서 **[!UICONTROL Profiles and Targets]** 탭.

1. 왼쪽 메뉴에서 **[!UICONTROL Services and Subscriptions]** 및 클릭 **[!UICONTROL Create]**.

   ![](assets/line_service_1.png)

1. 추가 **[!UICONTROL Label]** 및 **[!UICONTROL Internal name]** 새 서비스로 이동합니다.

1. 선택 **[!UICONTROL LINE]** 다음에서 **[!UICONTROL Type]** 드롭다운.

   ![](assets/line_service_2.png)

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다.

구독 및 서비스에 대한 자세한 내용은 [구독 관리](managing-subscriptions.md).

### LINE 외부 계정 구성 {#configure-line-external}

을(를) 만든 후 [!DNL LINE] 서비스에서는 다음을 구성해야 합니다. [!DNL LINE] Adobe Campaign 외부 계정:

1. 다음에서 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** 트리 구조에서 **[!UICONTROL External Accounts]** 탭.

1. 기본 제공 선택 **[!UICONTROL LINE V2 routing]** 외부 계정입니다.

   ![](assets/line_config.png)

1. 다음을 클릭합니다. **[!UICONTROL LINE]** 외부 계정 구성을 시작하려면 외부 계정에서 을 탭하십시오. 다음 필드를 채웁니다.

   ![](assets/line_config_2.png)

   * **[!UICONTROL Channel Alias]**: 은(는) 다음을 통해 제공됩니다. [!DNL LINE] 계정: **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]** 탭.
   * **[!UICONTROL Channel ID]**: 은(는) 다음을 통해 제공됩니다. [!DNL LINE] 계정: **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]** 탭.
   * **[!UICONTROL Channel secret key]**: 은(는) 다음을 통해 제공됩니다. [!DNL LINE] 계정: **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]** 탭.
   * **[!UICONTROL Access token]**: 은(는) 다음을 통해 제공됩니다. [!DNL LINE] 개발자 포털에서 또는 **[!UICONTROL Get access token]** 단추를 클릭합니다.
   * **[!UICONTROL Access token expiration date]**: 액세스 토큰의 만료 날짜를 지정할 수 있습니다.
   * **[!UICONTROL LINE subscription service]**: 사용자가 구독할 서비스를 지정할 수 있습니다.

1. 구성이 완료되면 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

1. 다음에서 **[!UICONTROL Explorer]**, 선택 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL LINE workflows]** 다음을 확인하십시오. **[!UICONTROL LINE V2 access token update (updateLineAccessToken)]** 및 **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** 워크플로우가 시작되었습니다.

다음 [!DNL LINE] 이제 Adobe Campaign에서 가 구성되었으므로 LINE 게재를 만들어 구독자에게 보낼 수 있습니다.

## LINE 게재 만들기 {#creating-the-delivery}

>[!NOTE]
>
>전송 시 [!DNL LINE] 새 수신자에게 처음으로 게재하는 경우 사용 약관 및 동의와 관련된 공식 LINE 메시지를 게재에 추가해야 합니다. 공식 메시지는 [다음 링크](https://terms.line.me/OA_privacy/).

을(를) 만들려면 [!DNL LINE] 게재 다음 단계를 수행해야 합니다.

1. 다음에서 **[!UICONTROL Campaigns]** 탭, 선택 **[!UICONTROL Deliveries]** 그런 다음 **[!UICONTROL Create]** 단추를 클릭합니다.

   ![](assets/line_message_07.png)

1. 선택 **[!UICONTROL LINE V2 delivery]** 게재 템플릿.

   ![](assets/line_message_01.png)

1. 을(를) 통해 게재 식별 **[!UICONTROL Label]**, **[!UICONTROL Delivery code]**, 및  **[!UICONTROL Description]**. 이 작업에 대한 자세한 정보는 [이 섹션](steps-create-and-identify-the-delivery.md#identifying-the-delivery)을 참조하십시오.

1. 클릭 **[!UICONTROL Continue]** 게재를 만들기 위해

1. 게재 편집기에서 **[!UICONTROL To]** 의 수신자를 타겟팅하려면 [!DNL LINE] 게재. 타깃팅은에서 수행됩니다. **[!UICONTROL Visitor subscriptions (nms:visitorSub)]**.

   자세한 내용은 다음을 참조하십시오. [대상 모집단 식별](steps-defining-the-target-population.md).

   ![](assets/line_message_08.png)

1. 클릭 **[!UICONTROL Add]** 을(를) 선택하려면 **[!UICONTROL Delivery target population]**.

   ![](assets/line_message_09.png)

1. 타겟팅할 경우 선택 [!DNL LINE] 구독자를 직접 선택하거나 구독자에 따라 사용자를 타겟팅하려는 경우 [!DNL LINE] 구독 및 클릭 **[!UICONTROL Next]**. 이 예제에서는 **[!UICONTROL By LINE V2 subscription]**.

1. 선택 **[!UICONTROL Line-V2]** 다음에서 **[!UICONTROL Folder]** 드롭다운을 클릭한 다음 [!DNL LINE] 서비스. 클릭 **[!UICONTROL Finish]** 그러면 **[!UICONTROL Ok]** 게재 개인화를 시작합니다.

   ![](assets/line_message_10.png)

1. 게재 편집기에서 **[!UICONTROL Add]** 하나 이상의 메시지를 추가하고 **[!UICONTROL Content type]**.

   다른 것에 대한 자세한 내용은 **[!UICONTROL Content type]** 사용 가능, 다음을 참조하십시오. [콘텐츠 유형 정의](#defining-the-content).

   ![](assets/line_message_11.png)

1. 게재가 올바르게 생성 및 구성되면 이전에 정의된 타겟으로 보낼 수 있습니다.

   게재 전송에 대한 자세한 내용은 [메시지 보내기](sending-messages.md).

1. 메시지를 보낸 후 보고서에 액세스하여 게재의 효과를 측정합니다.

   에 대한 자세한 내용 [!DNL LINE] 보고서, 참조 [보고서 액세스](#accessing-reports).

## 콘텐츠 유형 정의 {#defining-the-content}

의 콘텐츠를 정의하려면 [!DNL LINE] 게재, 먼저 메시지 유형을 게재에 추가해야 합니다. 각 [!DNL LINE] 게재에는 최대 5개의 메시지를 포함할 수 있습니다.

다음 세 가지 메시지 유형 중에서 선택할 수 있습니다.

* [텍스트 메시지](#configuring-a-text-message-delivery)
* [이미지 및 링크](#configuring-an-image-and-link-delivery)
* [비디오 메시지](#configuring-a-video-message-delivery)

### 문자 메시지 게재 구성 {#configuring-a-text-message-delivery}

>[!NOTE]
>
>다음 `<%@ include option='NmsServer_URL' %>/webApp/APP3?id=<%=escapeUrl(cryptString(visitor.id))%>` 구문을 사용하면 LINE 메시지에 웹 앱에 대한 링크를 포함할 수 있습니다.

A **[!UICONTROL Text message]** [!DNL LINE] 게재는 텍스트 양식으로 받는 사람에게 보내는 메시지입니다.

![](assets/line_message_02.png)

이 유형의 메시지는 다음과 같은 구성과 유사합니다 **[!UICONTROL Text]** 이메일. 자세한 내용은 다음을 참조하십시오. [페이지](defining-the-email-content.md#message-content).

### 이미지 및 링크 전달 구성 {#configuring-an-image-and-link-delivery}

An **[!UICONTROL Image and link]** [!DNL LINE] 게재는 하나 이상의 URL이 포함될 수 있는 이미지 형태로 수신자에게 전송되는 메시지입니다.

다음을 사용할 수 있습니다.

* a **[!UICONTROL Personalized image]**,

  >[!NOTE]
  >
  >다음을 사용할 수 있습니다. **%SIZE%** 수신자의 모바일 장치의 화면 크기에 따라 이미지 표시를 최적화하기 위한 변수입니다.

  ![](assets/line_message_04.png)

* an **[!UICONTROL Image URL]** 장치 화면 크기당,

  ![](assets/line_message_03.png)

  다음 **[!UICONTROL Define images per device screen size]** 옵션을 사용하면 다양한 이미지 해상도를 사용하여 모바일 디바이스에서 게재 가시성을 최적화할 수 있습니다. 높이와 너비가 같은 이미지만 지원됩니다.

  이미지는 화면 크기에 따라 정의할 수 있습니다.

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px

  >[!CAUTION]
  >
  >1040x1040 픽셀 크기는 링크가 있는 모든 LINE 이미지에 필수입니다.

  그런 다음 수신자의 모바일 장치에 표시되는 대체 텍스트를 추가해야 합니다.

* 및 **[!UICONTROL Links]**.

  다음 **[!UICONTROL Links]** [섹션]을 사용하면 클릭 가능한 여러 영역으로 이미지를 분할하는 서로 다른 레이아웃 중에서 선택할 수 있습니다. 그런 다음 각 사용자에게 전용 을 할당할 수 있습니다 **[!UICONTROL Link URL]**.

  ![](assets/line_message_05.png)

### 비디오 메시지 게재 구성 {#configuring-a-video-message-delivery}

A **[!UICONTROL Video message]** [!DNL LINE] 게재는 URL을 포함할 수 있는 비디오 형태로 수신자에게 보내는 메시지입니다.

다음 **[!UICONTROL Preview Image URL]** 필드를 사용하면 문자 제한이 1000인 미리보기 이미지의 URL을 추가할 수 있습니다. JPEG 및 PNG는 1MB의 파일 크기 제한으로 지원됩니다.

다음 **[!UICONTROL Video Image URL]** 필드를 사용하면 문자 제한이 1000인 비디오 파일의 URL을 추가할 수 있습니다. mp4 형식만 지원되며 파일 크기는 200MB로 제한됩니다.

일부 장치에서 재생할 때 넓은 비디오나 높은 비디오를 자를 수 있습니다.

![](assets/line_message_06.png)

## 보고서 액세스 {#accessing-reports}

게재를 보낸 후 다음을 볼 수 있습니다. [!DNL LINE] 메뉴를 통한 보고서 **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 다음에서 **[!UICONTROL Explorer]**.

>[!NOTE]
>
>추적 보고서는 클릭스루 비율을 나타냅니다. [!DNL LINE] 열람률은 고려하지 않습니다.

![](assets/line_reports_01.png)

대상 [!DNL LINE] 서비스 보고서, 메뉴에 액세스 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Services and Subscriptions]** > **[!UICONTROL LINE-V2]** 다음에서 **[!UICONTROL Explorer]** 탭. 그런 다음 **[!UICONTROL Reports]** 아이콘 [!DNL LINE] 서비스.

![](assets/line_reports.png)

## 예: 개인화된 LINE 메시지 만들기 및 보내기 {#example--create-and-send-a-personalized-line-message}

이 예제에서는 수신자에 따라 개인화될 데이터가 포함된 이미지와 문자 메시지를 만들고 만들려고 합니다.

1. 사용자 만들기 [!DNL LINE] 다음을 클릭하여 게재 **[!UICONTROL Create]** 단추 **[!UICONTROL Campaign]** 탭.

   ![](assets/line_usecase.png)

1. 다음 항목 선택 **[!UICONTROL LINE V2 delivery]** 게재 템플릿 및 게재 이름 지정.

   ![](assets/line_usecase_01.png)

1. 게재 구성 창에서 대상 모집단을 선택합니다.

   자세한 내용은 다음을 참조하십시오. [대상 모집단 식별](steps-defining-the-target-population.md).

   ![](assets/line_usecase_02.png)

1. 클릭 **[!UICONTROL Add]** 메시지를 만들고 **[!UICONTROL Content type]**.

   여기에서는 먼저 **[!UICONTROL Text message]**.

   ![](assets/line_usecase_03.png)

1. 개인화된 텍스트를 삽입할 위치에 커서를 놓고 드롭다운 아이콘을 클릭한 다음 을 선택합니다 **[!UICONTROL Visitor]** > **[!UICONTROL First name]**.

   ![](assets/line_usecase_05.png)

1. 동일한 절차에 따라 이미지를 추가하고 을 선택합니다 **[!UICONTROL Image and links]** 다음에서 **[!UICONTROL Message type]** 드롭다운.

   사용자 추가 **[!UICONTROL Image URL]**.

   ![](assets/line_usecase_07.png)

1. 다음에서 **[!UICONTROL Links]** 섹션에서 클릭 가능한 여러 영역에 이미지를 분할할 레이아웃을 선택합니다.

1. 이미지의 각 영역에 URL을 지정합니다.

   ![](assets/line_usecase_08.png)

1. 게재를 저장하고 **[!UICONTROL Send]** 를 분석하여 타겟에게 보냅니다.

   게재가 타겟에게 전송됩니다.

   ![](assets/line_usecase_06.png)

