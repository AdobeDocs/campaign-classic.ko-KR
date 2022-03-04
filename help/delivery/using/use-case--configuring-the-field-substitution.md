---
product: campaign
title: '"활용 사례: 필드 대체 구성"'
description: '"활용 사례: 필드 대체 구성"'
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---

# 활용 사례: 필드 대체 구성{#use-case-configuring-the-field-substitution}

![](../../assets/common.svg)

무작위 필드 대체를 사용하면 사용자가 게재에서 이 값을 사용할 때 비어 있는 시드 주소에 수신자 목록의 값을 지정할 수 있습니다(예: 이름, 도시 등)

이 대체를 사용하면 게재를 만들 때 시간을 절약할 수 있습니다. 원하는 값을 시드 주소에 수동으로 추가하는 대신 대체는 게재가 타겟팅한 수신자 목록에서 이 값을 임의로 복원하여 시드 주소에 적용합니다.

## 컨텍스트 {#context}

이 사용 사례에서는 사이트가 **내 온라인 라이브러리** 고객들이 좋아하는 문학 장르를 바탕으로 할인을 해드리고 싶습니다

게재 관리자는 즐겨찾는 장르와 연결된 개인화 필드를 이메일에 통합했습니다. 목적은 시드 주소를 사용하는 것입니다. 이러한 시드 주소에는 테이블에 개인화 필드가 있지만 저장된 값은 없습니다.

임의 필드 대체를 사용하려면 다음을 수행해야 합니다.

* 하나 또는 여러 개의 개인화 필드를 포함한 게재
* 시드 주소 **데이터 스키마** 게재에서 사용되는 개인화 필드에 따라 수정됩니다.

## 게재 만들기 {#step-1---creating-a-delivery}

게재를 만드는 단계는 [이메일 게재 만들기](creating-an-email-delivery.md) 섹션을 참조하십시오.

이 예에서는 게재 관리자가 뉴스레터를 만들었습니다.

![](assets/dlv_seeds_usecase_24.png)

## 시드 주소 데이터 스키마 편집 {#editing-the-seed-addresses-data-schema}

데이터 스키마를 수정하는 방법에 대한 지침은 섹션에 자세히 설명되어 있습니다.

이 예에서 시드 주소 데이터 스키마는 수신자 데이터 스키마에서 생성된 값을 사용합니다.

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

이 열거형을 사용하면 사용자가 클라이언트의 좋아하는 문학 장르를 지정할 수 있습니다.

시드 주소에서 볼 수 있도록 이 데이터 스키마 수정 **입력 양식**&#x200B;를 업데이트해야 합니다. 자세한 내용은 [입력 양식 업데이트](use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) 섹션을 참조하십시오.

## 개인화 구성 {#configuring-personalization}

1. 게재를 엽니다.

   이 예에서는 게재에 두 개의 개인화 필드가 있습니다. 수신자의 **이름** 수신자의 **인기 문학 장르**.

   ![](assets/dlv_seeds_usecase_25.png)

1. 게재 목록 및 시드 주소를 구성합니다. 을(를) 참조하십시오. [대상 모집단 식별](steps-defining-the-target-population.md).

   이 예에서는 사용자가 **인기 문학 장르** 는 SCI-Fi를 주요 대상 모집단으로 사용합니다.

   ![](assets/dlv_seeds_usecase_26.png)

   사용자는 게재에 시드 주소를 추가합니다.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >에 대한 자세한 내용은 **[!UICONTROL Edit the dynamic condition...]** 링크, [사용 사례: 기준 시드 주소 선택](use-case--selecting-seed-addresses-on-criteria.md).

1. 을(를) 클릭합니다. **[!UICONTROL Preview]** 그런 다음 시드 주소를 선택하여 개인화를 테스트합니다.

   ![](assets/dlv_seeds_usecase_28.png)

   개인화 필드 중 하나가 비어 있는 것을 볼 수 있습니다. 시드 주소에 이 필드에 대한 데이터가 없으므로 HTML 콘텐츠 미리 보기에 값을 표시할 수 없습니다.

   필드의 임의 대체가 수행됩니다 **배달 시**.

1. **[!UICONTROL Send]** 버튼을 클릭합니다.
1. 게재를 분석합니다 **게재 확인**.

   시드 주소는 받은 편지함에서 게재를 받습니다.

   필드 개인화는 효과적입니다.

   ![](assets/dlv_seeds_usecase_08.png)
