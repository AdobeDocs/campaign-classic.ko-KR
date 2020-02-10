---
title: 트랜잭션 메시지의 시드 주소 관리
seo-title: 트랜잭션 메시지의 시드 주소 관리
description: 트랜잭션 메시지의 시드 주소 관리
seo-description: null
page-status-flag: never-activated
uuid: 51c4e79d-53bb-4d46-9c7d-e90066f5317d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 12e7043e-e8b5-48a9-8a2f-99e2e6040c3c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 트랜잭션 메시지의 시드 주소 관리{#managing-seed-addresses-in-transactional-messages}

시드 주소를 사용하면 이메일 또는 SMS를 전달하기 전에 메시지 미리 보기를 표시하거나 증명을 보내고 메시지 개인화를 테스트할 수 있습니다. 시드 주소는 게재와 연결되어 있으므로 다른 게재에 사용할 수 없습니다.

## 시드 주소 만들기 {#creating-a-seed-address}

1. 트랜잭션 메시지 템플릿에서 **[!UICONTROL Seed addresses]** 탭을 클릭합니다.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. 나중에 쉽게 선택할 수 있도록 레이블을 할당합니다.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. 시드 주소(통신 채널에 따라 이메일 또는 휴대폰)를 입력합니다.

   ![](assets/messagecenter_create_seedaddr_003.png)

1. 외부 식별자를 입력합니다.이 선택적 필드를 사용하면 비즈니스 키(고유 ID, 이름 + 이메일 등)를 입력할 수 있습니다. 프로파일을 식별하는 데 사용되는 웹 사이트의 모든 애플리케이션에서 일반적으로 사용됩니다. 이 필드가 Adobe Campaign 마케팅 데이터베이스에도 있는 경우 데이터베이스의 프로필과 이벤트를 조정할 수 있습니다.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. 테스트 데이터를 삽입합니다(개인화 데이터 [참조](../../message-center/using/personalization-data.md)).

   ![](assets/messagecenter_create_custo_001.png)

## 여러 시드 주소 만들기 {#creating-several-seed-addresses}

1. 링크를 **[!UICONTROL Add other seed addresses]** 클릭한 다음 **[!UICONTROL Add]** 단추를 클릭합니다.

   ![](assets/messagecenter_create_seedaddr_004.png)

1. 시드 주소의 구성 단계에 따라 시드 주소 만들기 [섹션에](#creating-a-seed-address) 자세히 설명되어 있습니다.
1. 이 과정을 반복하여 필요한 수만큼 주소를 만듭니다.

   ![](assets/messagecenter_create_seedaddr_008.png)

주소가 만들어지면 미리 보기 및 개인화를 표시할 수 있습니다. 트랜잭션 [메시지 미리 보기를](../../message-center/using/transactional-message-preview.md)참조하십시오.
