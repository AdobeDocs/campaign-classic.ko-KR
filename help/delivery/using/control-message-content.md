---
product: campaign
title: Adobe Campaign Classic의 게재 기능 기본 정보
description: Adobe Campaign Classic의 게재 기능 관리에 대해 자세히 알아보십시오.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 4%

---

# 메시지 콘텐츠 제어{#control-message-content}

이메일이 수신자에게 도달하고 전자 메일 게재 가능성을 향상하기 위해 많은 규칙을 준수해야 합니다. 그렇지 않으면 특정 메시지의 콘텐츠가 스팸으로 감지될 수 있습니다. Adobe Campaign은 콘텐츠를 이러한 규칙을 준수하도록 하는 몇 가지 도구를 제공합니다.

메시지 콘텐츠를 디자인할 때 아래 나열된 원칙을 따르십시오.

* [보낸 사람 주소](#sender-address):주소는 발신자를 명시적으로 식별해야 합니다. 도메인은 의 소유가 되어야 하며 발신자에게 등록해야 합니다. 도메인 레지스트리를 민영화해서는 안 됩니다.
* [개인화](#personalization):콘텐츠를 개인화하고 수신자당 전송 시간을 정의하면 메시지가 열릴 가능성이 높아집니다.
* 이미지 및 텍스트:적절한 텍스트/이미지 비율(예: 60% 텍스트 및 40% 이미지)을 준수합니다.
* [구독 ](#opt-out) 취소 링크 및 랜딩 페이지:구독 취소 링크는 필수입니다. 이 변수는 표시적이고 유효해야 하며 양식이 작동해야 합니다.
* 미리 보기:Adobe Campaign에서 제공하는 도구를 사용하여 전자 메일의 콘텐츠를 확인 및 최적화합니다([받은 편지함 렌더링](#message-responsiveness), [SpamAssassin](#spamassassin)).

콘텐츠를 디자인할 때 게재 능력을 최적화하는 추가 팁은 [Adobe 게재 가능성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html)를 참조하십시오.

>[!NOTE]
>
>전자 메일 콘텐츠 편집에 대한 자세한 내용은 [전자 메일 콘텐츠 정의](defining-the-email-content.md) 및 [개인화된 콘텐츠 빌드](design-and-personalize.md)를 참조하십시오.

## 보낸 사람 주소 {#sender-address}

특정 ISP는 메시지를 수락하기 전에 보낸 사람 주소(**[!UICONTROL From]**)의 유효성을 검사합니다. 잘못 형성된 주소는 수신 서버에서 거부될 수 있습니다.

인스턴스 수준(메뉴 **[!UICONTROL Tools > Advanced > Deployment wizard...]**)이나 가장 자주 사용하는 시나리오에서 올바른 주소가 지정되었는지 확인해야 합니다.

자세한 내용은 [보낸 사람 정의](defining-the-email-content.md)를 참조하십시오.

## 개인화 {#personalization}

Adobe Campaign을 사용하면 수신자의 경험을 향상하고 이메일을 열도록 할 수 있으므로 메시지를 개인화할 수 있습니다.

Adobe Campaign에서 개인화 필드 사용에 대한 자세한 내용은 [이 섹션](personalization-fields.md)을 참조하십시오.

컨텐츠를 작성할 때 개인화를 최적화하는 몇 가지 팁은 [이 섹션](design-and-personalize.md#optimize-personalization)에 나와 있습니다.

## 옵트아웃 링크 및 양식 {#opt-out}

기본적으로 메시지를 분석할 때 [유형화 규칙](steps-validating-the-delivery.md#validation-process-with-typologies)은(는) 옵트아웃 링크가 포함되어 있는지 여부를 확인하고 누락된 경우 경고를 생성합니다. 간단한 경고 대신 오류가 발생하도록 이 규칙을 변경하고 이 링크 없이 게재가 종료되지 않도록 중단할 수 있습니다.

보낼 때마다 옵트아웃 링크가 올바르게 작동하는지 확인해야 합니다. 예를 들어, 증명을 보낼 때 링크가 유효한지, 양식이 온라인 상태인지 그리고 이를 확인하면 **[!UICONTROL No longer contact this recipient]** 필드 값이 **[!UICONTROL Yes]**&#x200B;로 변경되는지 확인하십시오. 링크를 입력하거나 양식을 변경할 때 항상 인간 오류가 가능하므로 이 검사를 체계적으로 수행해야 합니다.

이 섹션](personalization-blocks.md#personalization-blocks-example)에 옵트아웃 링크 [를 삽입하는 방법을 알아봅니다.

게재 시작 후 구독 취소에 대한 문제가 감지되면, 옵트아웃 링크를 클릭하는 수신자에 대해, 예를 들어, 일괄 업데이트 기능을 사용하여 수동으로 구독 취소를 수행할 수 있습니다. 수신자가 선택을 확인할 수 없어도 됩니다.

일반적으로, 예를 들어 이메일 주소나 이름과 같은 필드를 작성할 것을 요구하여 옵트아웃하려는 수신자의 방해가 되지 않도록 하십시오. 양식에는 하나의 유효성 검사 단추만 있어야 하며, 암호화된 식별자에서만 조정을 수행해야 합니다.

추가 확인 요청을 신뢰할 수 없습니다.사용자는 두 개의 이메일 주소를 동일한 상자로 리디렉션할 수 있습니다(예:firstname.lastname@club.com 및 firstname.lastname@internet-club.com). 수신자가 첫 번째 주소만 기억할 수 있고 다른 주소로 전송된 메시지를 통해 구독을 취소하려는 경우, 암호화된 식별자와 입력한 이메일 주소가 일치하지 않으므로 양식이 이를 거부합니다.

## 받은 편지함 렌더링 {#message-responsiveness}

메시지를 보내기 전에 메시지가 다른 장치에서 어떻게 표시되는지 확인하여 메시지 응답성을 테스트할 수 있습니다. 이는 다양한 웹 클라이언트, 웹 메일 및 장치에서 최적의 방식으로 표시되도록 하기 위한 것입니다.

이를 위해 Adobe Campaign은 렌더링을 캡처하여 전용 보고서에서 사용할 수 있도록 합니다. 이렇게 하면 수신되었을 수 있는 다른 컨텍스트에서 전송된 메시지를 미리 볼 수 있습니다.

자세한 내용은 [받은 편지함 렌더링](inbox-rendering.md)을 참조하십시오.

## SpamAssassin {#spamassassin}

Adobe Campaign이 SpamAssassin에서 작동하도록 구성할 수 있습니다. 이를 통해 이메일에 점수를 매겨 수신 시 사용되는 스팸 방지 도구에 의해 메시지가 스팸으로 간주될 위험이 있는지 확인할 수 있습니다.

게재를 시작하기 전에 **[!UICONTROL Preview]** 탭을 사용하여 위험을 평가할 수 있습니다. 경고 메시지에 테스트 결과가 표시됩니다.

자세한 내용은 이 [섹션](spamassassin.md)을 참조하십시오.
