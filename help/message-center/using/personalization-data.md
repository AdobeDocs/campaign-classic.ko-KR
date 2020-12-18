---
solution: Campaign Classic
product: campaign
title: 개인화 데이터
description: 개인화 데이터
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# 개인화 데이터{#personalization-data}

메시지 템플릿의 데이터를 사용하여 트랜잭션 메시지 개인화를 테스트할 수 있습니다. 이 기능은 미리 보기를 생성하거나 교정을 전송하는 데 사용됩니다. **Deliverability** 모듈을 설치하는 경우 이 데이터를 통해 다양한 인터넷 액세스 공급자에 대한 메시지 렌더링을 표시할 수 있습니다(**받은 편지함 렌더링**:자세한 내용은 [이 섹션](../../delivery/using/inbox-rendering.md))을 참조하십시오.

이 데이터의 목적은 메시지를 최종 전달하기 전에 테스트하는 것입니다. 이러한 메시지는 메시지 센터에서 처리할 실제 데이터와 일치하지 않습니다. 그러나 XML 구조는 아래와 같이 실행 인스턴스에 저장된 이벤트와 동일해야 합니다.

![](assets/messagecenter_create_custo_006.png)

이 정보를 통해 개인화 태그를 사용하여 메시지 컨텐츠를 개인화할 수 있습니다(이 정보에 대한 자세한 내용은 [메시지 내용 만들기](../../message-center/using/creating-message-content.md) 참조).

1. 메시지 템플릿에서 **[!UICONTROL Seed addresses]** 탭을 클릭합니다.
1. 이벤트 내용에서 테스트 정보를 XML 형식으로 입력합니다.

   ![](assets/messagecenter_create_custo_001.png)
