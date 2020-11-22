---
solution: Campaign Classic
product: campaign
title: 시드 주소 기본 정보
description: 시드 주소 기본 정보
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 9%

---


# 시드 주소 기본 정보{#about-seed-addresses}

시드 주소는 정의된 대상 기준과 일치하지 않는 수신자를 타겟팅 하는 데 사용됩니다. 이렇게 하면 배달 범위를 벗어난 수신자가 다른 대상 수신자와 마찬가지로 배달을 받을 수 있습니다.

한 때 그것들을 사용하는 주된 이유 **는 메일링 목록 보호입니다**. 메일링 목록에 시드 주소를 삽입하면 포함된 시드 주소로 메일링 목록에 발송된 배달물을 받을 수 있으므로 타사에서 사용 중인지를 알 수 있습니다.

또한 시드 주소를 사용하면 교정을 보내기 전에 **미리 보고 개인화 및 렌더링을** 테스트할 수 있습니다(시드 주소를 증거로 [사용 참조](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

시드 주소 기능은 다음과 같은 이점을 제공합니다.

* 수신자 프로필에서 가져온 데이터가 있는 필드의 임의 대체:이렇게 하면 시드 주소 섹션의 이메일 주소만 입력할 수 있고 Campaign이 프로필의 다른 필드를 자동으로 채우게 할 수 있습니다( [사용 사례 참조).필드 대체 구성](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Datamanmanagement 기능이 있는 워크플로우를 사용하는 경우, 배달에서 처리된 추가 데이터를 시드 주소 수준에서 입력하여 값을 강제 적용할 수 있습니다.무작위 값 대체를 단계별로 수행합니다.
* 시드 주소는 다음 배달 통계에 대한 보고서에서 자동으로 제외됩니다. **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

시드 주소는 전달이나 캠페인에서 직접 만들어지거나 배달 타겟에 추가됩니다.

>[!NOTE]
>
>시드 주소는 수신자 테이블에 속하지 않고 별도의 테이블에 생성됩니다. 새 데이터로 수신자 테이블을 확장하는 경우 동일한 데이터와 함께 시드 주소 테이블을 확장해야 합니다. 그렇지 않으면 시드 주소를 고려하지 않습니다.
>
>이 섹션에는 시드 주소 테이블을 확장하는 방법의 예가 나와 있습니다. [사용 사례:기준 시드 주소 선택](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

직접 메일 배달의 경우 추출 중에 시드 주소가 추가되고 출력 문서에 혼합됩니다.

>[!IMPORTANT]
>
>DM 전달의 경우 추출 파일 형식은 다음 제한 사항을 준수해야 합니다.
>
>* 이 옵션은 사용할 수 없습니다 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* 요소 컬렉션이 추출되면 옵션을 선택하지 않는 한 이 필드는 시드 주소에 대해 빈 값 **[!UICONTROL Single row (expert user)]** 을 갖게 됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/exporting-data.md#step-7---data-formatting)을 참조하십시오.

>


