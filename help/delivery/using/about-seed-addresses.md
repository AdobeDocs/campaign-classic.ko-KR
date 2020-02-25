---
title: 시드 주소 정보
seo-title: 시드 주소 정보
description: 시드 주소 정보
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3641e438784d40aa097f8c89ca19bdbb52f4bc7d

---


# 시드 주소 정보{#about-seed-addresses}

시드 주소는 정의된 대상 기준과 일치하지 않는 수신자를 타깃팅하는 데 사용됩니다. 이렇게 하면 다른 대상 수신자가 받는 것처럼 배달 범위를 벗어나는 수신자도 배달을 받을 수 있습니다.

한 때 그것들을 사용하는 주된 이유는 **귀하의 메일링 목록 보호입니다**. 메일링 목록에 시드 주소를 삽입하면 서드 파티가 사용 중인지 확인할 수 있습니다. 시드 주소에 포함된 주소 때문에 메일링 목록에 전송된 배달이 수신됩니다.

또한 시드 주소를 사용하면 교정을 위해 교정을 전송하기 전에 게재 개인화 및 렌더링을 **미리 보고 테스트할** 수 있습니다( [시드 주소를 증명으로](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)사용 참조).

시드 주소 기능은 다음과 같은 이점을 제공합니다.

* 수신자 프로필에서 가져온 데이터로 필드를 임의 대체:이렇게 하면 시드 주소 섹션의 이메일 주소만 입력할 수 있고 Campaign이 프로필의 다른 필드를 자동으로 채우도록 할 수 있습니다(사용 [사례 참조:필드 대체](../../delivery/using/use-case--configuring-the-field-substitution.md)구성).
* Datamanmanagement 기능이 있는 워크플로우를 사용할 때 게시에 처리된 추가 데이터를 시드 주소 수준에서 입력하여 값을 강제 적용할 수 있습니다.이 단계 무작위 값 대체를 수행합니다.
* 시드 주소는 다음 배달 통계에 대한 보고서에서 자동으로 제외됩니다. **[!UICONTROL Clicks]**&#x200B;아, **[!UICONTROL Opens]****[!UICONTROL Unsubscriptions]**&#x200B;그래요

시드 주소는 배달 또는 캠페인에서 직접 만들거나 가져와서 게재 대상에 추가됩니다.

>[!NOTE]
>
>시드 주소는 수신자 테이블에 속하지 않고 별도의 테이블에 만들어집니다. 새 데이터로 수신자 테이블을 확장하는 경우 동일한 데이터와 함께 시드 주소 테이블을 확장해야 합니다. 그렇지 않은 경우 확장 필드는 시드 주소를 고려하지 않습니다.
>
>이 섹션에서는 시드 주소 테이블을 확장하는 방법에 대한 예를 제공합니다.사용 [사례:기준의 시드 주소 선택](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

직접 메일 배달의 경우 추출 중에 시드 주소가 추가되고 출력 문서에 혼합됩니다.

>[!CAUTION]
>
>DM 전달의 경우 추출 파일 형식은 다음 제한 사항을 준수해야 합니다.
>
>* 이 옵션은 사용할 수 없습니다 **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* 요소 컬렉션을 추출하면 옵션을 선택하지 않는 한 이 필드에는 시드 주소에 대한 빈 값이 **[!UICONTROL Single row (expert user)]** 있습니다. For more on this, refer to [this section](../../platform/using/exporting-data.md#step-7---data-formatting).
>


