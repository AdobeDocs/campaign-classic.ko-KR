---
product: campaign
title: "활용 사례: 웹 양식"
description: "활용 사례: 웹 양식"
feature: Web Forms
exl-id: 7aa4646d-1325-47c2-b553-6fe375c48973
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 1%

---

# 활용 사례: 웹 양식{#use-cases-web-forms}

![](../../assets/common.svg)

## 이중 옵트인으로 구독 양식 만들기 {#create-a-subscription--form-with-double-opt-in}

정보 서비스를 제공할 때 수신자는 연결된 모든 통신을 수신하려면 구독해야 합니다. 부적절한 커뮤니케이션을 방지하고 수신자가 의도적으로 구독했는지 확인하려면 이중 옵트인을 만들기 위해 구독 확인 요청을 보내는 것이 좋습니다. 구독은 사용자가 확인 메시지에 포함된 링크를 클릭한 경우에만 유효합니다.

이 예제는 다음 시나리오를 기반으로 합니다.

1. 임시 서비스를 구독하기 위한 확인란이 포함된 웹 사이트에 뉴스레터 구독 양식 만들기. 이 서비스를 사용하면 구독 확인 메시지를 게재할 수 있습니다.
1. 웹 양식에 연결된 게재 템플릿을 사용하여 구독 확인 게재 만들기. 여기에는 뉴스레터 구독 양식을 호출하고 구독 승인 메시지를 표시하는 확인 링크가 포함되어 있습니다.

### 1단계 - 정보 서비스 만들기 {#step-1---creating-information-services}

1. 수신자에게 제공할 뉴스레터 구독 서비스를 만듭니다. 뉴스레터를 만드는 방법에 대한 자세한 내용은 [이 섹션](../../delivery/using/about-services-and-subscriptions.md).

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1.png)

1. 두 번째 정보 서비스를 만듭니다. 이 서비스는 구독 확인 메시지를 보내기 위한 게재 템플릿에 연결된 임시 서비스입니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1c.png)

### 2단계 - 확인 메시지 만들기 {#step-2---creating-confirmation-messages}

확인 메시지는 임시 서비스 수준에서 참조되는 전용 게재 템플릿을 통해 전송됩니다.

1. 다음에서 **[!UICONTROL Explorer]** , 선택 **[!UICONTROL Resources > Templates > Delivery templates]**.
1. 구독 확인 메시지를 보내기 위한 게재 템플릿을 만듭니다.
1. 다음을 클릭합니다. **[!UICONTROL To]** 의 단추 **[!UICONTROL Email parameters]** 게재 템플릿을 수신자 대신 구독 대상 매핑과 연결합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1d.png)

1. 이 게재 수신자가 승인을 확인하지 않았기 때문에 아직 데이터베이스 차단 목록에 있습니다. 이 사용자가 이 통신을 수신하려면 이 템플릿을 기반으로 하여 수신자를 타겟팅하는 게재를 차단 목록에서 승인해야 합니다.

   이렇게 하려면 **[!UICONTROL Exclusions]** 탭.

1. 다음을 클릭합니다. **[!UICONTROL Edit...]** 링크 및 선택 취소 **[!UICONTROL Exclude recipients who no longer want to be contacted]** 옵션을 선택합니다.

   <!-- ![](assets/s_ncs_admin_survey_double-opt-in_sample_4d.png)-->

   >[!IMPORTANT]
   >
   >이 옵션은 이 유형의 컨텍스트에서만 비활성화될 수 있습니다.

1. 게재를 개인화하고 확인 링크를 메시지 콘텐츠에 삽입합니다. 이 링크를 사용하면 웹 양식에 액세스하여 구독 확인을 기록할 수 있습니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1b.png)

1. DCE를 사용하여 웹 양식에 URL을 연결합니다. 웹 양식이 아직 만들어지지 않았으므로 값을 만드는 즉시 값을 바꿉니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3.png)

1. 마지막으로 이 템플릿을 이전에 만든 임시 서비스에 연결합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3c.png)

### 3단계 - 가입 양식 만들기 {#step-3---creating-the-subscription-form}

웹 양식을 사용하면 수신자 구독과 구독 확인이 모두 가능합니다.

웹 양식 워크플로에는 다음 활동이 포함됩니다.

![](assets/s_ncs_admin_survey_double-opt-in_sample_4c.png)

이렇게 하려면 아래 단계를 수행합니다:

1. 웹 양식을 만들고 템플릿 선택 **[!UICONTROL Newsletter subscription (subNewsletter)]**.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5a.png)

1. 다음에서 **[!UICONTROL Edit]** 탭에서는 가입하려는 수신자에게 확인 메시지를 추가하려고 하므로 기존 워크플로우를 구성해야 합니다.

   이렇게 하려면 다음을 두 번 클릭합니다 **[!UICONTROL Preloading]** 상자를 표시하고 다음과 같이 구성합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5b.png)

   즉, 사용자가 확인 메시지의 링크를 통해 이 양식에 액세스하면 프로필 정보가 로드됩니다. 웹 사이트의 페이지를 통해 웹 양식에 액세스하면 정보가 로드되지 않습니다.

1. 추가 **[!UICONTROL Test]** 활동을 워크플로우에 추가합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6e.png)

   다음 **[!UICONTROL Test]** 활동은 수신자 이메일과 관련될 수 있습니다. 이 경우 다음과 같이 구성합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6d.png)

1. 두 개 추가 **[!UICONTROL Script]** 활동을 워크플로우에 추가합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6f.png)

   첫 번째 **[!UICONTROL Script]** 활동은 수신자가 뉴스레터 구독을 확인할 때까지 차단 목록에 수신자를 추가합니다. 콘텐츠는 다음과 같아야 합니다.

   ```
   ctx.recipient.@blackList=1
   ```

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6bbis.png)

   두 번째 **[!UICONTROL Script]** 활동은 사용자에게 전송할 게재를 승인하고 뉴스레터를 구독합니다. 스크립트의 마지막 두 줄을 사용하면 임시 폴더에서 다른 폴더로 수신자를 전송하고 구독을 확인하는 즉시 기존 프로필과 조정할 수 있습니다.

   ```
   ctx.recipient.@blackList=0
   nms.subscription.Subscribe("INTERNAL_NAME_OF_THE_NEWSLETTER", ctx.recipient, false)
   ctx.recipient.folder = <folder name="nmsRootRecipient"/>
   nms.subscription.Unsubscribe("TEMP", ctx.recipient)
   ```

   >[!NOTE]
   >
   >다음 **[!UICONTROL Temp]** 분할 영역은 워크플로우를 사용하여 정기적으로 제거할 수도 있습니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6b.png)

1. 를 두 번 클릭합니다. **[!UICONTROL Subscription]** 활동을 통해 구독 양식을 개인화하고 확인란을 이전에 만든 임시 서비스와 연결할 수 있습니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5c.png)

1. 구성 **[!UICONTROL Storage]** 활동을 사용하여 양식 페이지에 입력한 정보를 저장합니다.

   이 활동을 사용하면 전용 임시 폴더에 수신자 프로필을 만들어 메시지를 보낼 수 있는 데이터베이스의 프로필과 별도로 설정할 수 있습니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5g.png)

   >[!NOTE]
   >
   >조정 옵션을 정의해서는 안 됩니다.

1. 두 개 추가 **[!UICONTROL End]** 사용자에게 메시지를 표시하는 활동.

   두 번째 **[!UICONTROL End]** 구독이 완료되면 상자에 확인 메시지가 표시됩니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5h.png)

1. 웹 양식을 만들고 구성하고 나면 이제 게재 템플릿에서 웹 양식을 참조하여 확인 메시지를 보낼 수 있습니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_7b.png)

### 4단계 - 양식 게시 및 테스트 {#step-4---publishing-and-testing-the-form}

이제 양식을 게시하여 사용자가 액세스할 수 있도록 할 수 있습니다.

![](assets/s_ncs_admin_survey_double-opt-in_sample_8b.png)

뉴스레터 구독에는 다음 단계가 포함됩니다.

1. 웹 사이트의 사용자는 구독 페이지에 로그인하고 양식을 승인합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8c.png)

   이들은 브라우저의 메시지를 통해 요청이 고려되었다는 알림을 받습니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8d.png)

   사용자가 의 Adobe Campaign 데이터베이스에 추가됩니다. **[!UICONTROL Temp]** 폴더를 만들고 이메일을 통해 구독을 확인할 때까지 프로필을 차단 목록에 추가합니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8f.png)

1. 구독 승인 링크가 포함된 확인 메시지가 전송됩니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8e.png)

1. 방문자가 이 링크를 클릭하면 브라우저에 승인 페이지가 표시됩니다.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8.png)

   Adobe Campaign에서 사용자 프로필은 다음과 같이 업데이트됩니다.

   * 그들은 더 이상 차단 목록에 있지 않습니다.
   * 그들은 정보 서비스에 가입되어 있다.

      ![](assets/s_ncs_admin_survey_double-opt-in_sample_9.png)

## 선택한 값에 따라 다른 옵션 표시 {#displaying-different-options-depending-on-the-selected-values}

다음의 예에서, 사용자는 차량의 유형을 선택하라는 요청을 받는다. 선택한 유형에 따라 사용 가능한 차량 범주를 표시할 수 있습니다. 즉, 오른쪽 열에 표시되는 항목은 사용자의 선택에 따라 달라집니다.

![](assets/s_ncs_admin_survey_condition_sample0.png)

* 사용자가 &#39;자가용&#39;을 선택하면 &#39;컴팩트&#39;와 &#39;미니밴&#39; 중 선택이 제공된다.

   ![](assets/s_ncs_admin_survey_condition_sample2.png)

* 사용자가 &#39;상용차&#39;를 선택하면 선택 항목이 드롭다운 목록에 표시됩니다.

   ![](assets/s_ncs_admin_survey_condition_sample1.png)

이 예에서, 차량 타입은 데이터베이스에 저장되지 않는다. 드롭다운 목록은 다음과 같이 구성됩니다.

![](assets/s_ncs_admin_survey_condition_config1.png)

이 정보는 로컬 변수에 저장됩니다.

오른쪽 열의 조건부 표시가 컨테이너에 구성됩니다.

![](assets/s_ncs_admin_survey_condition_config1bis.png)

* 전용 차량에 대한 필드의 조건부 가시성:

   ![](assets/s_ncs_admin_survey_condition_config2.png)

* 상용차 필드의 조건부 가시성:

   ![](assets/s_ncs_admin_survey_condition_config3.png)
