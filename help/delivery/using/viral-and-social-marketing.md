---
product: campaign
title: 바이럴 및 소셜 마케팅
description: 바이럴 및 소셜 마케팅
feature: Social Marketing
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 2%

---

# 바이럴 및 소셜 마케팅{#viral-and-social-marketing}

Adobe Campaign을 사용하면 바이럴 마케팅을 장려하는 도구를 설정할 수 있습니다.

이렇게 하면 게재 수신자 또는 웹 사이트 방문자가 Facebook 또는 X(이전의 Twitter) 프로필에 대한 링크 추가에서 친구에게 메시지를 보내는 것과 같은 정보를 네트워크와 공유할 수 있습니다.

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>추가된 링크가 제대로 작동하려면 일치하는 미러 페이지를 사용할 수 있어야 합니다. 이렇게 하려면 게재에서 미러 페이지에 대한 링크를 포함합니다.

## 소셜 네트워크: 링크 공유 {#social-networks--sharing-a-link}

게재 수신자가 네트워크 구성원과 메시지 콘텐츠를 공유할 수 있도록 하려면 일치하는 개인화 블록을 포함해야 합니다.

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>기본적으로 이 링크는 블록 목록에 제공되지 않습니다. **[!UICONTROL Other...]**&#x200B;을(를) 클릭하고 **[!UICONTROL Social network sharing links]** 블록을 선택하여 액세스할 수 있습니다.

![](assets/s_ncs_user_viral_add_link_via_others.png)

렌더링은 다음과 같습니다.

![](assets/s_ncs_user_viral_add_link_rendering.png)

수신자가 표시된 소셜 네트워크 중 하나의 아이콘을 클릭하면 자동으로 해당 계정으로 리디렉션되고 링크를 통해 메시지 콘텐츠를 공유할 수 있습니다. 이렇게 하면 네트워크 구성원이 통신에 액세스할 수 있습니다.

>[!NOTE]
>
>이 개인화 블록에는 모든 링크(메시지 전송 및 모든 소셜 네트워크와의 공유)가 포함됩니다. 사용자의 요구 사항에 맞게 변경할 수 있습니다. 그러나 구성은 고급 사용자용으로 예약되어 있습니다. 일치하는 개인화 블록을 편집하려면 Adobe Campaign 트리의 **[!UICONTROL Resources > Campaign management > Personalization blocks]** 노드로 이동하십시오.

## 바이럴 마케팅: 친구에게 전달 {#viral-marketing--forward-to-a-friend}

바이럴 서비스를 사용하면 참조 유형의 작업을 수행할 수 있습니다. 이러한 작업을 통해 친구에게 메시지를 전달할 수 있습니다. 심판의 프로필은 데이터베이스(전용 테이블)에 임시로 저장됩니다. 전달된 메시지에는 심판이 구독할 수 있는 링크가 포함됩니다. 링크가 포함되어 있는 경우 Adobe Campaign 데이터베이스에 추가됩니다.

메시지 전달은 소셜 네트워크 링크와 동일한 원칙을 기반으로 합니다.

다음 단계를 적용합니다.

1. **[!UICONTROL Social network sharing links]** 개인화 블록을 원본 메시지 본문에 추가합니다.
1. 메시지 받는 사람이 **[!UICONTROL Email]** 아이콘을 클릭하여 이 메시지를 하나 이상의 친구에게 보낼 수 있습니다.

   ![](assets/s_ncs_user_viral_email_link.png)

   참조 양식을 사용하면 참조의 이메일 주소를 입력할 수 있습니다.

   ![](assets/s_ncs_user_viral_email_msg.png)

   주 수신자가 **[!UICONTROL Next]** 단추를 클릭하면 메시지가 전송됩니다.

   >[!NOTE]
   >
   >이 메시지의 콘텐츠는 사용자의 요구 사항에 맞게 개인화할 수 있습니다. **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 노드에 저장된 **[!UICONTROL Transfer of original message]** 템플릿을 기반으로 만들어집니다.
   >
   >레퍼러가 사용할 수 있는 메시지 전달 양식을 변경할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Resources > Online > Web applications]** 노드에 저장된 **바이러스 양식** 웹 응용 프로그램을 변경해야 합니다.

1. 전달된 메시지에서 링크를 사용하여 심판이 데이터베이스에 프로필을 저장할 수 있습니다. 이를 위해 입력 양식이 제공됩니다.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >이 구성은 조정할 수 있습니다. 이렇게 하려면 **[!UICONTROL Resources > Online > Web applications]** 노드에 저장된 **받는 사람 구독** 웹 응용 프로그램을 수정해야 합니다.
   >
   >웹 응용 프로그램에 대한 자세한 내용은 [이 섹션](../../web/using/about-web-applications.md)을 참조하세요.

   유효성을 검사하면 확인 메시지가 전송됩니다. 확인 메시지에서 링크를 활성화해야만 제대로 등록됩니다. 이 메시지는 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 노드에 저장된 **[!UICONTROL Registration confirmation]** 템플릿을 기반으로 만들어집니다.

   해당 심판이 데이터베이스의 **수신자** 폴더에 추가되고 기본적으로 **뉴스레터** 정보 서비스에 가입됩니다.

## 소셜 네트워크 공유 추적 {#tracking-social-network-sharing}

공유 및 공유 정보에 대한 액세스가 추적됩니다. Adobe Campaign에서 수집한 이 정보는 다음 두 위치에서 액세스할 수 있습니다.

* 게재의 **[!UICONTROL Tracking]** 탭에서(또는 각 수신자에 대해 개별적으로):

  ![](assets/s_ncs_user_network_del_tracking_tab.png)

* 전용 **[!UICONTROL Sharing to social networks]** 보고서에서:

  ![](assets/s_ncs_user_viral_report.png)
