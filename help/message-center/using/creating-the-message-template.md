---
product: campaign
title: 트랜잭션 메시지 템플릿 디자인
description: Adobe Campaign Classic에서 트랜잭션 메시지 템플릿을 만들고 디자인하는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 트랜잭션 메시지 템플릿 디자인 {#creating-the-message-template}



각 이벤트를 개인화된 메시지로 변경하려면 각 이벤트 유형과 일치하는 메시지 템플릿을 만들어야 합니다.

>[!IMPORTANT]
>
>이벤트 유형은 미리 만들어야 합니다. 자세한 내용은 다음을 참조하십시오. [이벤트 유형 만들기](../../message-center/using/creating-event-types.md).

트랜잭션 메시지 템플릿에는 트랜잭션 메시지를 개인화하는 데 필요한 정보가 포함되어 있습니다. 템플릿을 사용하여 메시지 미리 보기를 테스트하고 최종 대상에 전달하기 전에 시드 주소를 사용하여 증명을 보낼 수도 있습니다. 자세한 내용은 [트랜잭션 메시지 템플릿 테스트](../../message-center/using/testing-message-templates.md).

## 메시지 템플릿 만들기 {#creating-message-template}

1. 로 이동 **[!UICONTROL Message Center >Transactional message templates]** Adobe Campaign 트리의 폴더입니다.

1. 트랜잭션 메시지 템플릿 목록에서 마우스 오른쪽 단추를 클릭하고 을 선택합니다. **[!UICONTROL New]** 드롭다운 메뉴에서 을(를) 클릭하거나 **[!UICONTROL New]** 트랜잭션 메시지 템플릿 목록 위에 있는 단추입니다.

   ![](assets/messagecenter_create_model_001.png)

1. 게재 창에서 사용할 채널에 적합한 게재 템플릿을 선택합니다.

   ![](assets/messagecenter_create_model_002.png)

1. 필요한 경우 레이블을 변경합니다.

1. 보내려는 메시지와 일치하는 이벤트 유형을 선택합니다.

   ![](assets/messagecenter_create_model_003.png)

   이벤트 유형은 콘솔에서 미리 만들어야 합니다. 자세한 내용은 다음을 참조하십시오. [이벤트 유형 만들기](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >이벤트 유형을 둘 이상의 템플릿에 연결할 수 없습니다.

1. 특성 및 설명을 입력한 다음 **[!UICONTROL Continue]** 메시지 본문을 만들려면( 참조) [메시지 콘텐츠 만들기](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## 메시지 콘텐츠 만들기 {#creating-message-content}

트랜잭션 메시지 콘텐츠의 정의는 Adobe Campaign의 일반 게재와 동일합니다. 예를 들어 이메일 게재의 경우 HTML 또는 텍스트 형식으로 콘텐츠를 만들거나, 첨부 파일을 추가하거나, 게재 개체를 개인화할 수 있습니다. 자세한 내용은 [이메일 게재](../../delivery/using/about-email-channel.md) 챕터.

>[!IMPORTANT]
>
>메시지에 포함된 이미지는 공개적으로 액세스할 수 있어야 합니다. Adobe Campaign은 트랜잭션 메시지에 대한 이미지 업로드 메커니즘을 제공하지 않습니다.\
>JSSP 또는 webApp과 달리 `<%=` 에는 기본 이스케이프가 없습니다.
>
>이 경우 이벤트에서 오는 각 데이터를 제대로 이스케이프 처리해야 합니다. 이 이스케이프는 이 필드의 사용 방식에 따라 다릅니다. 예를 들어 URL 내에서 encodeURIComponent를 사용하십시오. HTML에 표시하려면 escapeXMLString을 사용할 수 있습니다.

메시지 콘텐츠를 정의한 후에는 이벤트 정보를 메시지 본문에 통합하고 개인화할 수 있습니다. 이벤트 정보는 개인화 태그 덕분에 텍스트 본문에 삽입됩니다.

![](assets/messagecenter_create_content_001.png)

* 모든 개인화 필드는 페이로드에서 가져옵니다.
* 트랜잭션 메시지에서 하나 또는 여러 개인화 블록을 참조할 수 있습니다. 실행 인스턴스에 게시하는 동안 블록 콘텐츠가 게재 콘텐츠에 추가됩니다.

개인화 태그를 이메일 메시지 본문에 삽입하려면 다음 단계를 적용합니다.

1. 메시지 템플릿에서 전자 메일 형식(HTML 또는 텍스트)과 일치하는 탭을 클릭합니다.

1. 메시지 본문을 입력합니다.

1. 텍스트 본문에 를 사용하여 태그를 삽입합니다. **[!UICONTROL Real time events > Event XML]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![](assets/messagecenter_create_custo_002.png)

1. 다음 구문을 사용하여 태그를 입력합니다. **요소 이름**.@**속성 이름** 아래와 같이 표시됩니다.

   ![](assets/messagecenter_create_custo_003.png)

1. 콘텐츠를 저장합니다.

이제 메시지를 작성할 준비가 되었습니다. [테스트됨](../../message-center/using/testing-message-templates.md).
