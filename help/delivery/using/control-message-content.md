---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic 제공 정보
description: Adobe Campaign Classic의 전달 가능성 관리에 대한 자세한 내용을 살펴보십시오.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: d6a581ae86e50c17ac20fe54baf305b864e11790
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 4%

---


# 메시지 내용 제어{#control-message-content}

이메일이 수신자에게 도달하고 이메일 전달 비율을 높이려면 많은 규칙을 준수해야 합니다. 그렇지 않으면 특정 메시지의 컨텐츠가 스팸으로 감지될 수 있습니다. Adobe Campaign은 컨텐츠가 이러한 규칙을 준수하도록 만드는 여러 도구를 제공합니다.

메시지 컨텐츠를 디자인할 때 아래 원칙을 따릅니다.

* [보낸 사람 주소](#sender-address):주소는 발신자를 명시적으로 식별해야 합니다. 도메인을 소유해야 하며 발신자에게 등록되어 있어야 합니다. 도메인 레지스트리를 민영화하지 않아야 합니다.
* [개인화](#personalization):컨텐츠를 개인화하고 수신자별로 전송 시간을 정의하면 메시지가 열릴 가능성이 높아집니다.
* 이미지 및 텍스트:적절한 텍스트/이미지 비율(예: 60% 텍스트 및 40% 이미지)을 준수합니다.
* [구독 취소 ](#opt-out) 링크 및 랜딩 페이지:비가입 링크는 필수입니다. 표시 및 유효해야 하며 양식이 제대로 작동하는지 확인해야 합니다.
* 미리 보기:Adobe Campaign에서 제공하는 도구를 사용하여 이메일의 내용을 확인하고 최적화합니다([받은 편지함 렌더링](#message-responsiveness), [SpamAsser](#spamassassin)).

콘텐츠를 디자인할 때 전달 가능성을 최적화하는 추가 팁은 [Adobe 제공 가능성 우수 사례 가이드](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html)를 참조하십시오.

>[!NOTE]
>
>이메일 컨텐츠 편집에 대한 자세한 내용은 [이메일 컨텐츠 정의](../../delivery/using/defining-the-email-content.md) 및 [개인화된 컨텐츠 작성](../../delivery/using/design-and-personalize.md)을 참조하십시오.

## 보낸 사람 주소 {#sender-address}

특정 ISP는 메시지를 수락하기 전에 보낸 사람 주소(**[!UICONTROL From]**)의 유효성을 확인합니다. 형식이 잘못된 주소는 수신 서버에서 거부될 수 있습니다.

올바른 주소가 인스턴스 수준(메뉴 **[!UICONTROL Tools > Advanced > Deployment wizard...]**) 또는 가장 자주 사용하는 시나리오에서 제공되는지 확인해야 합니다.

자세한 내용은 [보낸 사람 정의](../../delivery/using/defining-the-email-content.md)를 참조하십시오.

## 개인화 {#personalization}

Adobe Campaign을 사용하면 수신자의 경험을 향상시키고 이메일 열람을 유도하여 메시지를 개인화할 수 있습니다.

Adobe Campaign에서 개인화 필드 사용에 대한 자세한 내용은 [이 섹션](../../delivery/using/personalization-fields.md)을 참조하십시오.

콘텐츠를 빌드할 때 개인화를 최적화하기 위한 몇 가지 팁은 [이 섹션](../../delivery/using/design-and-personalize.md#optimize-personalization)에 있습니다.

## 옵트아웃 링크 및 양식 {#opt-out}

기본적으로 메시지를 분석하면 [Typical 규칙](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)은 옵트아웃 링크가 포함되었는지 여부를 확인하고 누락된 경우 경고를 생성합니다. 간단한 경고 대신 오류가 발생하고 이 링크 없이 배달이 발송되지 않도록 이 규칙을 변경할 수 있습니다.

보낼 때마다 옵트아웃 링크가 제대로 작동하는지 확인해야 합니다. 예를 들어 교정본을 보낼 때 링크가 유효한지, 양식이 온라인인지, 이 값을 확인하면 **[!UICONTROL No longer contact this recipient]** 필드의 값이 **[!UICONTROL Yes]**&#x200B;로 변경됩니다. 링크를 입력하거나 양식을 변경할 때 항상 인적 오류가 가능하므로 이 확인을 체계적으로 해야 합니다.

이 섹션](../../delivery/using/personalization-blocks.md#personalization-blocks-example)에서 옵트아웃 링크 [을 삽입하는 방법을 알아봅니다.

배달을 시작한 후 가입 해지에 대한 문제가 발견되더라도 옵트아웃 링크를 클릭하는 수신자에 대해 수동으로(예: 대량 업데이트 기능 사용) 가입 해지를 수행할 수 있습니다. 수신자는 선택을 확인할 수 없습니다.

일반적으로 이메일 주소 또는 이름과 같은 필드를 채우도록 요구함으로써 수신을 거부하려는 수신자의 방해가 되지 않도록 합니다. 양식에는 유효성 검사 단추가 하나만 있어야 하며 암호화된 식별자에서만 조정을 수행해야 합니다.

추가 확인 요청을 신뢰할 수 없습니다.사용자는 동일한 상자로 리디렉션된 두 개의 이메일 주소를 가질 수 있습니다(예:firstname.lastname@club.com 및 firstname.lastname@internet-club.com)을 참조하십시오. 수신자가 첫 번째 주소만 기억할 수 있고 다른 주소로 전송된 메시지를 통해 구독을 취소하려는 경우 암호화된 ID와 입력한 이메일 주소가 일치하지 않기 때문에 양식이 거부됩니다.

## 받은 편지함 렌더링 {#message-responsiveness}

메시지를 보내기 전에 메시지가 다른 장치에서 어떻게 보이는지 확인하여 메시지 응답성을 테스트할 수 있습니다. 이는 다양한 웹 클라이언트, 웹 메일 및 장치에서 최적의 방법으로 표시되도록 하기 위한 것입니다.

이를 위해 Adobe Campaign은 렌더링을 캡처하여 전용 보고서에서 사용할 수 있도록 합니다. 이렇게 하면 수신되었을 수 있는 다른 컨텍스트에서 전송된 메시지를 미리 볼 수 있습니다.

자세한 내용은 [받은 편지함 렌더링](../../delivery/using/inbox-rendering.md)을 참조하십시오.

## SpamAssassin {#spamassassin}

Adobe Campaign은 SpamAssaker와 함께 작동하도록 구성할 수 있습니다. 따라서 이메일에 점수를 매겨 메시지가 수신 시 사용되는 스팸 방지 도구에 의해 스팸으로 간주될 수 있는 위험을 실행하는지를 결정할 수 있습니다.

배달을 시작하기 전에 **[!UICONTROL Preview]** 탭을 사용하여 위험을 평가할 수 있습니다. 경고 메시지는 테스트 결과를 제공합니다.

이 [섹션](../../delivery/using/spamassassin.md)에서 자세히 알아보십시오.