---
product: campaign
title: 트랜잭션 메시지 템플릿 디자인
description: Adobe Campaign Classic에서 트랜잭션 메시지 템플릿을 만들고 디자인하는 방법을 알아봅니다.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 트랜잭션 메시지 템플릿 디자인 {#creating-the-message-template}

각 이벤트를 개인화된 메시지로 변경하려면 각 이벤트 유형에 맞게 메시지 템플릿을 만들어야 합니다.

>[!IMPORTANT]
>
>이벤트 유형을 미리 만들어야 합니다. 자세한 내용은 [이벤트 유형 만들기](../../message-center/using/creating-event-types.md)를 참조하십시오.

트랜잭션 메시지 템플릿에는 트랜잭션 메시지를 개인화하는 데 필요한 정보가 포함되어 있습니다. 템플릿을 사용하여 최종 타겟에 게재하기 전에 메시지 미리 보기를 테스트하고 시드 주소를 사용하여 증명을 전송할 수도 있습니다. 자세한 내용은 [테스트 트랜잭션 메시지 템플릿](../../message-center/using/testing-message-templates.md)을 참조하십시오.

## 메시지 템플릿 만들기 {#creating-message-template}

1. Adobe Campaign 트리의 **[!UICONTROL Message Center >Transactional message templates]** 폴더로 이동합니다.

1. 트랜잭션 메시지 템플릿 목록에서 마우스 오른쪽 단추를 클릭하고 드롭다운 메뉴에서 **[!UICONTROL New]** 을 선택하거나 트랜잭션 메시지 템플릿 목록 위에 있는 **[!UICONTROL New]** 버튼을 클릭합니다.

   ![](assets/messagecenter_create_model_001.png)

1. 게재 창에서 사용할 채널에 적합한 게재 템플릿을 선택합니다.

   ![](assets/messagecenter_create_model_002.png)

1. 필요한 경우 레이블을 변경합니다.

1. 전송할 메시지와 일치하는 이벤트 유형을 선택합니다.

   ![](assets/messagecenter_create_model_003.png)

   이벤트 유형은 콘솔에서 미리 만들어야 합니다. 자세한 내용은 [이벤트 유형 만들기](../../message-center/using/creating-event-types.md)를 참조하십시오.

   >[!IMPORTANT]
   >
   >이벤트 유형은 두 개 이상의 템플릿에 연결할 수 없습니다.

1. 특성과 설명을 입력한 다음 **[!UICONTROL Continue]** 을 클릭하여 메시지 본문을 만듭니다( [메시지 콘텐츠 만들기](#creating-message-content) 참조).

   ![](assets/messagecenter_create_model_004.png)

## 메시지 콘텐츠 {#creating-message-content} 만들기

트랜잭션 메시지 콘텐츠의 정의는 Adobe Campaign의 일반 게재와 동일합니다. 예를 들어 이메일 게재의 경우 HTML 또는 텍스트 형식으로 콘텐츠를 만들거나 첨부 파일을 추가하거나 게재 개체를 개인화할 수 있습니다. 자세한 내용은 [전자 메일 배달](../../delivery/using/about-email-channel.md) 장을 참조하십시오.

>[!IMPORTANT]
>
>메시지에 포함된 이미지는 공개적으로 액세스할 수 있어야 합니다. Adobe Campaign은 트랜잭션 메시지를 위한 이미지 업로드 메커니즘을 제공하지 않습니다.\
>JSSP 또는 webApp과 달리 `<%=`에는 기본 이스케이프가 없습니다.
>
>이 경우 이벤트에서 제대로 오는 각 데이터를 이스케이프해야 합니다. 이스케이프는 이 필드를 사용하는 방식에 따라 다릅니다. 예를 들어 URL 내에서 encodeURIComponent를 사용하십시오. HTML에 표시되도록 하려면 escapeXMLString을 사용할 수 있습니다.

메시지 콘텐츠를 정의하고 나면 이벤트 정보를 메시지 본문에 통합하여 개인화할 수 있습니다. 개인화 태그 덕분에 텍스트 본문에 이벤트 정보가 삽입됩니다.

![](assets/messagecenter_create_content_001.png)

* 페이로드에서 모든 개인화 필드를 가져옵니다.
* 트랜잭션 메시지에서 하나 또는 여러 개의 개인화 블록을 참조할 수 있습니다. 실행 인스턴스에 게시하는 동안 블록 컨텐츠가 게재 콘텐츠에 추가됩니다.

이메일 메시지 본문에 개인화 태그를 삽입하려면 다음 단계를 적용합니다.

1. 메시지 템플릿에서 이메일 형식(HTML 또는 텍스트)과 일치하는 탭을 클릭합니다.

1. 메시지 본문을 입력합니다.

1. 텍스트 본문에 **[!UICONTROL Real time events > Event XML]** 메뉴를 사용하여 태그를 삽입합니다.

   ![](assets/messagecenter_create_custo_002.png)

1. 다음 구문을 사용하여 태그를 채웁니다.**요소 이름**.@**특성 이름**&#x200B;은 아래와 같이 표시됩니다.

   ![](assets/messagecenter_create_custo_003.png)

1. 콘텐츠를 저장합니다.

이제 메시지를 [테스트한](../../message-center/using/testing-message-templates.md)에 사용할 준비가 되었습니다.
