---
product: campaign
title: 시드 주소 정보
description: 시드 주소 정보
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 1113afb573bad958ec7cc2cf008f71c8e751e8f9
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 9%

---

# 시드 주소 정보{#about-seed-addresses}

![](../../assets/common.svg)

시드 주소는 정의된 대상 기준과 일치하지 않는 수신자를 타겟팅 하는 데 사용됩니다. 이렇게 하면 게재 범위를 벗어나는 수신자는 다른 대상 수신자와 마찬가지로 게재를 받을 수 있습니다.

이러한 규칙을 사용하는 주된 이유 중 하나는 **메일링 목록 보호**&#x200B;입니다. 시드 주소를 메일링 목록에 삽입하면 포함된 시드 주소가 메일링 목록으로 전송된 게재를 수신하므로 타사에서 시드 주소를 사용하고 있는지 확인할 수 있습니다.

또한 시드 주소를 사용하면 증명([시드 주소를 증명으로 사용](steps-defining-the-target-population.md#using-seed-addresses-as-proof))을 보내어 게재를 보내기 전에 **개인화와 렌더링을 미리 보고 테스트할 수 있습니다.**

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](steps-defining-the-target-population.md#seeds-and-proofs-video)

시드 주소 기능은 다음과 같은 이점을 제공합니다.

* 수신자 프로필에서 가져온 데이터로 필드를 임의로 대체: 이렇게 하면 시드 주소 섹션과 같은 전자 메일 주소만 입력할 수 있으며 Campaign에서 자동으로 프로필의 다른 필드를 채우도록 할 수 있습니다( [사용 사례 참조). 필드 대체](use-case--configuring-the-field-substitution.md))를 구성합니다.
* Datamanagement 기능으로 워크플로우를 사용하는 경우, 게재에서 처리된 추가 데이터를 시드 주소 수준에서 입력하여 값을 강제 적용할 수 있습니다. 이는 무작위 값 대체를 회피합니다.
* 시드 주소는 다음 게재 통계의 보고서에서 자동으로 제외됩니다. **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

시드 주소를 가져오거나 게재 또는 캠페인에서 직접 만들어 게재 대상에 추가합니다.

>[!NOTE]
>
>시드 주소는 수신자 테이블에 속하지 않고 별도의 테이블에 생성됩니다. 수신자 테이블을 새 데이터로 확장하는 경우, 시드 주소 테이블과 동일한 데이터를 확장해야 합니다. 그렇지 않으면 시드 주소에 대해 확장 필드가 고려되지 않습니다.
>
>시드 주소 테이블을 확장하는 방법에 대한 예는 이 섹션에 나와 있습니다. [사용 사례: 기준](use-case--selecting-seed-addresses-on-criteria.md)에서 시드 주소를 선택합니다.

DM 게재의 경우 추출 중에 시드 주소가 추가되고 출력 문서에 혼합됩니다.

>[!IMPORTANT]
>
>DM 게재의 경우 추출 파일 형식은 다음 제한 사항을 준수해야 합니다.
>
>* **[!UICONTROL Handle groupings (GROUP BY+HAVING)]** 옵션을 사용하지 않아야 합니다.
>* 요소 컬렉션이 추출되면 **[!UICONTROL Single row (expert user)]** 옵션을 선택하지 않은 한 이러한 필드에는 시드 주소에 대해 빈 값이 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../platform/using/executing-export-jobs.md#step-7---data-formatting)을 참조하십시오.
>

