---
product: campaign
title: 개인화 블록
description: 개인화 블록을 사용하는 방법 알아보기
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Personalization
role: User
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 2%

---

# 개인화 블록{#personalization-blocks}

개인화 블록은 동적이고 개인화된 블록이며 게재에 삽입할 수 있는 특정 렌더링을 포함합니다. 예를 들어 미러 페이지에 로고, 인사말 메시지 또는 링크를 추가할 수 있습니다. 다음을 참조하십시오 [개인화 블록 삽입](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png) 이 기능 살펴보기 [비디오에서](#personalization-blocks-video)

개인화 블록은 **[!UICONTROL Resources > Campaign Management > Personalization blocks]** Adobe Campaign 탐색기의 노드입니다. 기본적으로 여러 블록을 사용할 수 있습니다( 참조) [기본 개인화 블록](#out-of-the-box-personalization-blocks)).

게재 개인화를 최적화할 수 있는 새 블록을 정의할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [사용자 지정 개인화 블록 정의](#defining-custom-personalization-blocks).

>[!NOTE]
>
>개인화 블록은 **[!UICONTROL Digital Content Editor (DCE)]** . 자세한 정보는 이 [페이지](../../web/using/editing-content.md#inserting-a-personalization-block)를 참조하십시오.

## 개인화 블록 삽입 {#inserting-personalization-blocks}

메시지에 개인화 블록을 삽입하려면 아래 단계를 수행합니다.

1. 게재 마법사의 콘텐츠 편집기에서 개인화된 필드 아이콘을 클릭하고 **[!UICONTROL Include]** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 목록에서 개인화 블록을 선택하거나(목록에는 마지막으로 사용된 블록 10개가 표시됨) **[!UICONTROL Other...]** 전체 목록에 액세스하기 위한 메뉴.

   ![](assets/s_ncs_user_personalized_block01.png)

1. 다음 **[!UICONTROL Other...]** 메뉴를 통해 모든 기본 제공 및 사용자 지정 개인화 블록에 액세스할 수 있습니다( 참조) [기본 개인화 블록](#out-of-the-box-personalization-blocks) 및 [사용자 지정 개인화 블록 정의](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. 그런 다음 개인화 블록이 스크립트로 삽입됩니다. 개인화가 생성되면 수신자 프로필에 자동으로 조정됩니다.

   ![](assets/s_ncs_user_personalized_block03.png)

1. 다음을 클릭합니다. **[!UICONTROL Preview]** 을(를) 탭하고 수신자를 선택하여 개인화를 확인합니다.

   ![](assets/s_ncs_user_personalized_block04.png)

게재 콘텐츠에 개인화 블록의 소스 코드를 포함할 수 있습니다. 이렇게 하려면 다음을 선택합니다. **[!UICONTROL Include the HTML source code of the block]** 선택 시.

![](assets/s_ncs_user_personalized_block05.png)

HTML 소스 코드는 게재 콘텐츠에 삽입됩니다. 예를 들어 **[!UICONTROL Greetings]** 다음과 같이 개인화 블록이 표시됩니다.

![](assets/s_ncs_user_personalized_block06.png)

## 개인화 블록 예 {#personalization-blocks-example}

이 예에서는 개인화 블록을 사용하여 수신자가 미러 페이지를 보고, 소셜 네트워크에서 뉴스레터를 공유하고, 향후 게재에서 구독을 취소할 수 있도록 하는 이메일을 만듭니다.

이렇게 하려면 다음 개인화 블록을 삽입해야 합니다.

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>미러 페이지 생성에 대한 자세한 내용은 [미러 페이지 생성](sending-messages.md#generating-the-mirror-page).

1. 새 게재를 만들거나 기존 이메일 유형 게재를 엽니다.
1. 게재 마법사에서 **[!UICONTROL Subject]** 메시지의 제목을 편집하고 제목을 입력합니다.
1. 메시지 본문에 개인화 블록을 삽입합니다. 이렇게 하려면 메시지 콘텐츠를 클릭하고 개인화된 필드 아이콘을 클릭한 다음 **[!UICONTROL Include]** 메뉴 아래의 제품에서 사용할 수 있습니다.
1. 삽입할 첫 번째 블록을 선택합니다. 다른 두 블록을 포함하도록 절차를 갱신합니다.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. 다음을 클릭합니다. **[!UICONTROL Preview]** 탭을 클릭하여 개인화 결과를 확인합니다. 수신자의 메시지를 표시할 수신자를 선택해야 합니다.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. 블록 콘텐츠가 제대로 표시되는지 확인합니다.

## 기본 개인화 블록 {#out-of-the-box-personalization-blocks}

메시지 콘텐츠를 개인화하는 데 도움이 되는 개인화 블록 목록을 기본적으로 사용할 수 있습니다.

>[!NOTE]
>
>개인화 블록 목록은 인스턴스에 설치된 모듈 및 옵션에 따라 다릅니다.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : 수신자의 이름으로 인사말을 삽입합니다. 예: “안녕하세요 John Doe 님,”
* **[!UICONTROL Insert logo]** : 인스턴스를 구성할 때 정의된 기본 로고를 삽입합니다.
* **[!UICONTROL Powered by Adobe Campaign]** : &quot;Powered by Adobe Campaign&quot; 로고를 삽입합니다.
* **[!UICONTROL Mirror page URL]** : 미러 페이지 URL을 삽입하여 게재 디자이너가 링크를 확인할 수 있도록 합니다.

  >[!NOTE]
  >
  >미러 페이지 생성에 대한 자세한 내용은 [미러 페이지 생성](sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : 미러 페이지에 대한 링크를 삽입합니다. &quot;이 메시지를 올바르게 볼 수 없는 경우 여기를 클릭하십시오.&quot;
* **[!UICONTROL Unsubscription link]** : 모든 게재 구독 취소(차단 목록에 추가하다)에 대한 링크를 삽입합니다.
* **[!UICONTROL Formatting function for proper nouns]** : 를 생성합니다. **[!UICONTROL toSmartCase]** 각 단어의 첫 번째 문자를 대문자로 변경하는 Javascript 함수입니다.
* **[!UICONTROL Registration page URL]** : 구독 URL을 삽입합니다( 참조) [서비스 및 구독 기본 정보](about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : 구독 링크를 삽입합니다. 인스턴스를 구성할 때 정의되었습니다.
* **[!UICONTROL Registration link (with referrer)]** : 구독 링크를 삽입하여 방문자 및 게재를 식별합니다. 인스턴스를 구성할 때 링크가 정의되었습니다.

  >[!NOTE]
  >
  >이 블록은 방문자를 타겟팅하는 게재에만 사용할 수 있습니다.

* **[!UICONTROL Registration confirmation]** : 구독을 확인할 수 있는 링크를 삽입합니다.
* **[!UICONTROL Social network sharing links]** : 수신자가 이메일 클라이언트, Facebook, X(이전의 Twitter) 및 LinkedIn과 미러 페이지 컨텐츠에 대한 링크를 공유할 수 있는 버튼을 삽입합니다(참조) [바이럴 마케팅: 친구에게 전달](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** 및 **[!UICONTROL Notification style]** : 사전 정의된 HTML 스타일을 사용하여 이메일 서식을 지정하는 코드를 생성합니다. 이러한 블록은 의 게재 소스 코드에 삽입되어야 합니다. **[!UICONTROL ...]** 섹션, 종료 **`<style>...</style>`** 태그 사이에 코드를 삽입하지 마십시오.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : 상호 작용 오퍼를 설정할 수 있는 URL을 삽입합니다. **[!UICONTROL Accepted]** (참조 [이 섹션](../../interaction/using/offer-analysis-report.md)).

## 사용자 지정 개인화 블록 정의 {#defining-custom-personalization-blocks}

를 통해 개인화된 필드 아이콘에서 삽입할 새 개인화 필드를 정의할 수 있습니다. **[!UICONTROL Include...]** 메뉴 아래의 제품에서 사용할 수 있습니다. 이러한 필드는 개인화 블록에 정의됩니다.

개인화 블록을 만들려면 탐색기로 이동하여 다음 단계를 적용합니다.

1. 다음을 클릭합니다. **[!UICONTROL Resources > Campaign Management > Personalization blocks]** 노드.
1. 블록 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL New]** .
1. 개인화 블록의 설정을 입력합니다.

   ![](assets/s_ncs_user_personalized_block.png)

   * 블록의 레이블을 입력합니다. 이 레이블은 개인화 필드 삽입 창에 표시됩니다.
   * 선택 **[!UICONTROL Visible in the customization menus]** 개인화 필드 삽입 아이콘에서 이 블록에 액세스할 수 있도록 합니다.
   * 필요한 경우 다음을 선택합니다 **[!UICONTROL The content of the personalization block depends upon the format]** HTML 형식의 이메일과 텍스트 형식의 이메일에 대해 두 개의 개별 블록을 정의할 수 있습니다.

     그런 다음 이 편집기의 아래 섹션에 해당 콘텐츠를 정의할 수 있는 두 개의 탭(HTML 콘텐츠 및 텍스트 콘텐츠)이 표시됩니다.

     ![](assets/s_ncs_user_personalized_block_b.png)

   * 컨텐츠 입력(HTML, 텍스트, JavaScript 등) 개인화 블록의 을(를) 클릭하고 **[!UICONTROL Save]**.

## 튜토리얼 비디오 {#personalization-blocks-video}

다이내믹 콘텐츠 블록을 만드는 방법과 이 블록을 사용하여 이메일 게재의 콘텐츠를 개인화하는 방법을 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
