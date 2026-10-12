---
product: campaign
title: 트랜잭션 메시지 템플릿 테스트
description: Adobe Campaign Classic에서 미리 보고 테스트하기 위해 트랜잭션 메시지의 시드 주소를 관리하는 방법을 알아봅니다
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
TQID: 'https://experienceleague.adobe.com/jcmXX4aMPaTBatt4m3s-IAaAeoXnjmPaEE4oqIDoIOI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%
---
# 트랜잭션 메시지 템플릿 테스트 {#testing-message-templates}

[메시지 템플릿](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"}(Campaign v8 설명서)이 준비되면 아래 단계에 따라 미리 보고 테스트하십시오.

Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 시드 주소를 추가하고 트랜잭션 메시지를 미리 보고 증명을 보내는 방법은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}를 참조하세요.

[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}

## 개인화 데이터 {#personalization-data}

메시지 템플릿의 데이터를 사용하여 트랜잭션 메시지 개인화를 테스트할 수 있습니다. 이 기능은 미리보기를 생성하거나 증명을 전송하는 데 사용됩니다. 다양한 인터넷 액세스 공급자에 대해 메시지 렌더링을 표시할 수도 있습니다. 자세한 내용은 [받은 편지함 렌더링](../../delivery/using/inbox-rendering.md)을 참조하세요.

이 데이터의 목적은 최종 게재 전에 메시지를 테스트하는 것입니다. 이러한 메시지는 처리할 실제 데이터와 일치하지 않습니다. 단, XML 구조는 아래와 같이 실행 인스턴스에 저장된 이벤트의 구조와 동일해야 합니다.

![](assets/messagecenter_create_custo_006.png)

이 정보를 통해 개인화 태그를 사용하여 메시지 콘텐츠를 개인화할 수 있습니다. 자세한 내용은 [메시지 콘텐츠 만들기](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/real-time/transactional-template#create-message-content){target="_blank"}(Campaign v8 설명서)를 참조하십시오.

1. 트랜잭션 메시지 템플릿을 선택합니다.

1. 템플릿에서 **[!UICONTROL Seed addresses]** 탭을 클릭합니다.

1. 이벤트 콘텐츠에서 테스트 정보를 XML 형식으로 입력합니다.

   ![](assets/messagecenter_create_custo_001.png)

1. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.
