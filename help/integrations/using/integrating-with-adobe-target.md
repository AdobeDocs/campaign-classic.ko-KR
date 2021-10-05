---
product: campaign
title: Adobe Target과 통합
description: Adobe Target과 통합
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 0996cc313be93300bce2f094c97e45a794cd459e
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Adobe Target과 통합{#integrating-with-adobe-target}

![](../../assets/v7-only.svg)

Adobe Experience Cloud 내에서 Adobe Campaign과 Adobe Target(Classic 및 Standard) 간의 통합을 사용하면 Adobe Target의 오퍼를 Adobe Campaign 이메일 게재에 포함할 수 있습니다.

운영 원칙은 다음과 같습니다. 수신자가 Adobe Campaign을 통해 전송된 이메일을 열면 Adobe Target을 호출하여 컨텐츠의 동적 버전을 표시할 수 있습니다. 이 동적 버전은 이메일을 만들 때 미리 지정한 규칙에 따라 계산됩니다.

>[!NOTE]
>
>통합은 정적 이미지만 지원합니다. 나머지 콘텐츠는 개인화할 수 없습니다.

Adobe Target에서는 몇 가지 유형의 데이터를 사용할 수 있습니다.

* Adobe Campaign 데이터 마트의 데이터
* 사용된 데이터에 법적 제한이 없는 경우 Adobe Target의 방문자 ID에 연결된 세그먼트는
* Adobe Target 데이터: 사용자 에이전트, IP 주소, 지리적 위치 데이터

>[!NOTE]
>
>또한 [Adobe Target 도움말 페이지](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html)에서 Adobe Campaign과 Adobe Target 간의 통합에 대한 정보를 찾을 수 있습니다.
