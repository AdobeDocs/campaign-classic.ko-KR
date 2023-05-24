---
product: campaign
title: Adobe Campaign Classic의 전달성 기본 정보
description: Adobe Campaign에서의 게재 기능 관리에 대해 자세히 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 6%

---

# 메시지 콘텐츠 제어{#control-message-content}



이메일이 수신자에게 도달하고 이메일 게재 가능성을 높이려면 많은 규칙을 준수해야 합니다. 그렇지 않으면 특정 메시지의 콘텐츠가 스팸으로 감지될 수 있습니다. Adobe Campaign은 콘텐츠가 이러한 규칙을 준수하도록 하는 몇 가지 도구를 제공합니다.

메시지 콘텐츠를 디자인할 때는 아래 나열된 원칙을 따르십시오.

* [보낸 사람 주소](#sender-address): 주소가 발신자를 명시적으로 식별해야 합니다. 도메인은 발신자가 소유하고 등록해야 합니다. 도메인 레지스트리를 개인화하면 안 됩니다.
* [개인화](#personalization): 콘텐츠를 개인화하고 수신자당 보내는 시간을 정의하면 메시지가 열릴 가능성이 높아집니다.
* 이미지 및 텍스트: 적절한 텍스트/이미지 비율(예: 텍스트 60% 및 이미지 40%)을 준수합니다.
* [구독 취소 링크](#opt-out) 랜딩 페이지: 구독 취소 링크는 필수입니다. 표시 및 유효해야 하며 양식이 제대로 작동해야 합니다.
* 미리 보기: Adobe Campaign에서 제공하는 도구를 사용하여 이메일 콘텐츠를 확인하고 최적화합니다([받은 편지함 렌더링](#message-responsiveness), [SpamAssassin](#spamassassin)).

콘텐츠를 디자인할 때 게재 능력을 최적화하는 추가 팁은 다음을 참조하십시오. [Adobe 전달성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>전자 메일 콘텐츠 편집에 대한 자세한 내용은 [이메일 콘텐츠 정의](defining-the-email-content.md) 및 [개인화된 콘텐츠 작성](design-and-personalize.md).

## 보낸 사람 주소 {#sender-address}

특정 ISP는 발신자 주소( )의 유효성을 확인합니다.**[!UICONTROL From]**)를 클릭하여 메시지를 수락합니다. 잘못된 형식의 주소는 수신 서버에서 거부될 수 있습니다.

인스턴스 수준(메뉴)에서 올바른 주소가 지정되었는지 확인해야 합니다 **[!UICONTROL Tools > Advanced > Deployment wizard...]**) 또는 를 사용할 필요가 없습니다.

자세한 내용은 [이 페이지](defining-the-email-content.md)를 참조하십시오.

## 개인화 {#personalization}

Adobe Campaign을 사용하면 수신자의 경험을 개선하여 이메일을 열 수 있으므로 메시지를 개인화할 수 있습니다.

Adobe Campaign에서 개인화 필드를 사용하는 방법에 대한 자세한 내용은 [이 섹션](personalization-fields.md).

콘텐츠를 작성할 때 개인화를 최적화하는 몇 가지 팁이에 나와 있습니다. [이 섹션](design-and-personalize.md#optimize-personalization).

## 옵트아웃 링크 및 양식 {#opt-out}

기본적으로 메시지를 분석할 때 [유형화 규칙](steps-validating-the-delivery.md#validation-process-with-typologies) 옵트아웃 링크가 포함되었는지 확인하고 누락된 경우 경고를 생성합니다. 단순 경고가 아닌 오류가 발생하도록 이 규칙을 변경하고 이 링크 없이 게재가 종료되지 않도록 할 수 있습니다.

보낼 때마다 옵트아웃 링크가 제대로 작동하는지 확인해야 합니다. 예를 들어 증명을 보낼 때 링크가 유효한지, 양식이 온라인 상태인지, 그리고 이를 확인하는 것이 의 값을 변경하는지 확인합니다. **[!UICONTROL No longer contact this recipient]** 필드 대상 **[!UICONTROL Yes]**. 링크를 입력하거나 양식을 변경할 때 사람의 오류가 항상 발생할 수 있으므로 이 검사를 체계적으로 수행해야 합니다.

옵트아웃 링크를 삽입하는 방법 알아보기 [이 섹션에서](personalization-blocks.md#personalization-blocks-example).

게재를 시작한 후 구독 취소와 관련하여 문제가 감지되면, 선택 사항을 확인할 수 없는 경우에도 옵트아웃 링크를 클릭하는 수신자에 대해 수동으로 구독 취소를 수행할 수 있습니다(예: 대량 업데이트 기능 사용).

일반적으로 옵트아웃을 원하는 수신자에게 이메일 주소 또는 이름 등의 필드를 작성하도록 요구하여 방해를 받지 마십시오. 양식에는 유효성 검사 버튼이 하나만 있어야 하며, 암호화된 식별자에만 조정이 수행되어야 합니다.

추가 확인 요청은 신뢰할 수 없습니다. 사용자는 두 개의 이메일 주소를 동일한 상자로 리디렉션할 수 있습니다(예: firstname.lastname@club.com 및 firstname.lastname@internet-club.com). 수신자가 첫 번째 주소만 기억할 수 있고 다른 주소로 보낸 메시지를 통해 구독을 취소하려는 경우 암호화된 식별자와 입력한 이메일 주소가 일치하지 않기 때문에 양식이 이를 거부합니다.

## 받은 편지함 렌더링 {#message-responsiveness}

메시지를 보내기 전에 다른 디바이스에서 메시지가 어떻게 표시되는지 확인하여 메시지 응답성을 테스트할 수 있습니다. 이는 다양한 웹 클라이언트, 웹 메일 및 디바이스에서 최적의 방식으로 표시되도록 하기 위한 것입니다.

이를 위해 Adobe Campaign은 렌더링을 캡처하여 전용 보고서에서 사용할 수 있도록 합니다. 이렇게 하면 수신되었을 수 있는 다른 컨텍스트에서 전송된 메시지를 미리 볼 수 있습니다.

자세한 내용은 [받은 편지함 렌더링](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign은 SpamAssassin과 작동하도록 구성할 수 있습니다. 이를 통해 이메일에 점수를 매겨 수신 시 사용되는 스팸 방지 도구에 의해 메시지가 스팸으로 간주될 위험이 있는지 여부를 확인할 수 있습니다.

게재를 시작하기 전에 **[!UICONTROL Preview]** 탭에서는 위험을 평가할 수 있습니다. 경고 메시지는 테스트 결과를 제공합니다.

자세히 알아보기 [섹션](spamassassin.md).
