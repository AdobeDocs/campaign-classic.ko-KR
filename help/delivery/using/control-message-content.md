---
title: Adobe Campaign Classic의 제공 정보
description: Adobe Campaign Classic의 전달 기능 관리에 대한 자세한 내용을 살펴보십시오.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# 메시지 내용 제어{#control-message-content}

이메일 배달율을 향상시키고 이메일을 수신자에게 전달하려면 아래에 설명된 일정 수의 규칙을 준수해야 합니다.

## 보낸 사람 주소 {#sender-address}

특정 ISP는 메시지를 수락하기 전에 보낸 사람 주소(보낸 사람)의 유효성을 확인합니다. 형식이 잘못되면 수신 서버에서 주소가 거부될 수 있습니다. 올바른 주소가 인스턴스 수준(메뉴 **[!UICONTROL Tools > Advanced > Deployment wizard...]**) 또는 가장 자주 사용되는 시나리오에서 제공되는지 확인해야 합니다.

## 옵트아웃 링크 및 양식 {#opt-out}

기본적으로 메시지를 분석할 때 유형 분류 규칙은 옵트아웃 링크가 포함되었는지 여부를 확인하고 누락된 경우 경고를 생성합니다. 간단한 경고 대신 오류가 발생하도록 이 규칙을 변경하고 이 링크 없이 배달이 나가는 것을 중지할 수 있습니다.

보낼 때마다 옵트아웃 링크가 제대로 작동하는지 확인해야 합니다. 예를 들어 증명 자료를 보낼 때 링크가 유효한지, 양식이 온라인인지, 이 유효성을 검사하면 **[!UICONTROL No longer contact this recipient]** 필드의 값이 **[!UICONTROL Yes]**&#x200B;변경됩니다. 링크를 입력하거나 양식을 변경할 때 항상 인적 오류가 발생할 수 있으므로 이 확인을 체계적으로 해야 합니다.

배달을 시작한 후 가입 취소와 관련하여 문제가 발견되더라도, 옵트아웃 링크를 클릭하는 수신자에 대해 수동으로(예: 대량 업데이트 기능 사용) 가입 해제를 수행할 수 있습니다.

일반적으로 이메일 주소 또는 이름과 같은 필드를 채우도록 요구하여 수신을 거부하려는 수신자의 방식을 방해하지 마십시오. 양식에는 유효성 검사 단추가 하나만 있어야 하며 암호화된 식별자에서만 조정을 수행해야 합니다. 추가 확인 요청은 신뢰성이 없습니다.사용자는 두 개의 이메일 주소를 동일한 상자로 리디렉션할 수 있습니다(예:firstname.lastname@club.com 및 firstname.lastname@internet-club.com). 수신자가 첫 번째 주소만 기억할 수 있고 다른 주소로 전송된 메시지를 통해 구독을 취소하려면, 암호화된 식별자와 입력한 이메일 주소가 일치하지 않기 때문에 양식이 거부됩니다.

## SpamAsser {#spamassassin}

Adobe Campaign은 SpamCharacter와 함께 작동하도록 구성할 수 있습니다. 따라서 이메일에 점수를 매겨 메시지가 수신 시 사용되는 스팸 방지 도구에 의해 스팸으로 간주될 위험을 실행하는지 여부를 결정할 수 있습니다.

배달을 시작하기 전에 미리 보기 탭을 사용하여 위험을 평가할 수 있습니다. 테스트 결과를 경고 메시지로 표시합니다.

자세한 내용은 이 [섹션을](../../delivery/using/spamassassin.md)참조하십시오.