---
product: campaign
title: Adobe Campaign 및 Adobe Target 작업
description: Adobe Campaign을 Adobe Target과 통합하는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Campaign을 Target과 함께 사용하기{#integrating-with-adobe-target}



Adobe Campaign과 Adobe Target을 함께 사용하여 이메일 콘텐츠를 최적화합니다.

이메일 콘텐츠를 최적화하기 위해 Adobe Target에서 리디렉션 오퍼를 만든 다음, Adobe Campaign을 사용하여 이메일 오퍼를 관리할 수 있습니다. 예를 들어 남성 및 여성 수신자를 위해 다른 오퍼를 표시할 수 있습니다.

통합은 이메일이 열려 있을 때 발생합니다. 고객이 이메일을 열면 Target에 대한 호출이 수행되고 컨텐츠의 동적 버전이 나타납니다. 이 콘텐츠는 모든 브라우저에서 지원하는 정적 이미지로 구성됩니다. Target은 대상 또는 세션 수준에서 오퍼에 대한 반응을 추적하며 해당 데이터는 Target 보고서에서 사용할 수 있습니다. [Adobe Target 설명서에서 자세히 알아보기](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).


>[!NOTE]
>
>통합은 정적 이미지만 지원합니다. 나머지 콘텐츠는 개인화할 수 없습니다.

Adobe Target에서는 몇 가지 유형의 데이터를 사용할 수 있습니다.

* Adobe Campaign 데이터 마트의 데이터
* 사용된 데이터에 법적 제한이 없는 경우 Adobe Target의 방문자 ID에 연결된 세그먼트는
* Adobe Target 데이터: 사용자 에이전트, IP 주소, 지리적 위치 데이터
