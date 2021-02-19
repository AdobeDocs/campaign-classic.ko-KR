---
solution: Campaign Classic
product: campaign
title: 시드 주소 기본 정보
description: 시드 주소 기본 정보
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 9%

---


# 시드 주소 기본 정보{#about-seed-addresses}

시드 주소는 정의된 대상 기준과 일치하지 않는 수신자를 타겟팅 하는 데 사용됩니다. 이렇게 하면 배달 범위를 벗어난 수신자가 다른 대상 수신자와 마찬가지로 배달을 받을 수 있습니다.

이 항목을 사용하는 주된 이유는 **메일링 목록 보호**&#x200B;입니다. 메일링 목록에 시드 주소를 삽입하면 포함된 시드 주소로 메일링 목록에 발송되는 배달을 받을 수 있으므로, 제3자가 시드 주소를 사용하고 있는지 확인할 수 있습니다.

또한 시드 주소는 **전송 전에**&#x200B;으로 배달 개인화 및 렌더링을 미리 보고 테스트할 수 있도록 해줍니다. 자세한 내용은 [시드 주소를 증명](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof)으로 사용 참조.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

시드 주소 기능은 다음과 같은 이점을 제공합니다.

* 수신자 프로필에서 가져온 데이터가 있는 필드를 임의 대체:이렇게 하면 이메일 주소만 입력할 수 있습니다(예: 시드 주소 섹션). 그러면 Campaign이 프로필의 다른 필드를 자동으로 채우도록 할 수 있습니다( [사용 사례 참조:필드 대체 구성](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* Datamanmanagement 기능이 있는 워크플로우를 사용하는 경우, 배달에서 처리된 추가 데이터를 시드 주소 수준에서 입력하여 값을 강제 적용할 수 있습니다.이 단계 무작위 값 대체를 수행합니다.
* 시드 주소는 다음 배달 통계에 대한 보고서에서 자동으로 제외됩니다.**[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

시드 주소는 배달 또는 캠페인에서 직접 만들어지거나 배달 타겟에 추가됩니다.

>[!NOTE]
>
>시드 주소는 수신자 테이블에 속하지 않고 별도의 테이블에 생성됩니다. 새 데이터로 수신자 테이블을 확장하는 경우 동일한 데이터와 함께 시드 주소 테이블을 확장해야 합니다. 그렇지 않은 경우 확장 필드는 시드 주소를 고려하지 않습니다.
>
>이 섹션에는 시드 주소 테이블을 확장하는 방법에 대한 예가 나와 있습니다.[사용 사례:기준 ](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md) 시드 주소 선택

직접 메일 배달의 경우 추출 중에 시드 주소가 추가되고 출력 문서에 혼합됩니다.

>[!IMPORTANT]
>
>DM 전달의 경우 추출 파일 형식은 다음 제한 사항을 준수해야 합니다.
>
>* **[!UICONTROL Handle groupings (GROUP BY+HAVING)]** 옵션을 사용할 수 없습니다.
>* 요소 컬렉션이 추출되면 **[!UICONTROL Single row (expert user)]** 옵션을 선택하지 않으면 이 필드는 시드 주소에 대해 빈 값을 갖게 됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/executing-export-jobs.md#step-7---data-formatting)을 참조하십시오.

>


