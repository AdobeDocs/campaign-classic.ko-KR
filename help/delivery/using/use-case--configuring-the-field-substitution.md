---
solution: Campaign Classic
product: campaign
title: '"사용 사례: 필드 대체 구성"'
description: '"사용 사례: 필드 대체 구성"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---


# 사용 사례: 필드 대체 구성{#use-case-configuring-the-field-substitution}

임의 필드 대체를 사용하면 사용자가 배달에 이 값을 사용할 때 비어 있는 시드 주소로 수신자 목록의 값을 지정할 수 있습니다(예:이름, 구/군/시 등).

이 대체를 사용하면 배달을 만들 때 시간을 절약할 수 있습니다.원하는 값을 시드 주소에 수동으로 추가하는 대신 대체는 배달이 타깃팅한 받는 사람 목록에서 이 값을 무작위로 회수하여 시드 주소에 적용합니다.

## 컨텍스트 {#context}

이 경우 사이트 **내 온라인 라이브러리**&#x200B;는 고객이 좋아하는 문학 장르를 기준으로 할인 혜택을 보내려고 합니다.

게재 관리자는 이메일에 즐겨 사용하는 장르와 연계된 개인화 필드를 통합했습니다. 그는 약간의 종자 주소를 사용하고 싶어한다. 이러한 시드 주소는 테이블에 개인화 필드가 있지만 값이 저장되지 않습니다.

임의 필드 대체를 사용하려면 다음과 같은 항목이 있어야 합니다.

* 하나 또는 여러 개인화 필드를 통해
* 전달에 사용된 개인화 필드에 따라 **데이터 스키마**&#x200B;가 수정된 시드 주소.

## 배달 {#step-1---creating-a-delivery} 만들기

배달을 만드는 단계는 [이메일 배달 만들기](../../delivery/using/creating-an-email-delivery.md) 섹션에 자세히 설명되어 있습니다.

이 예에서는 게재 관리자가 뉴스레터를 만들었습니다.

![](assets/dlv_seeds_usecase_24.png)

## 시드 편집은 데이터 스키마 {#editing-the-seed-addresses-data-schema} 주소를 해결합니다.

데이터 스키마를 수정하는 방법에 대한 지침은 섹션에 자세히 설명되어 있습니다.

이 예에서 시드 주소 데이터 스키마는 받는 사람 데이터 스키마에서 생성된 값을 사용합니다.

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

이 열거형을 통해 사용자는 클라이언트의 좋아하는 문학 장르를 지정할 수 있습니다.

이 데이터 스키마 수정이 시드 주소 **입력 양식**&#x200B;에서 볼 수 있게 하려면 업데이트해야 합니다. [입력 양식 업데이트](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) 섹션을 참조하십시오.

## 개인화 구성 중 {#configuring-personalization}

1. 배달을 엽니다.

   이 예에서 전달에는 다음과 같은 두 가지 개인화 필드가 있습니다.받는 사람의 **첫 이름** 및 받는 사람의 **가장 좋아하는 문학적 장르**.

   ![](assets/dlv_seeds_usecase_25.png)

1. 배달 목록 및 시드 주소를 구성합니다. [대상 모집단 식별](../../delivery/using/steps-defining-the-target-population.md)을 참조하십시오.

   이 예에서는 사용자가 **가장 좋아하는 문학 장르**&#x200B;가 SCI-Fi를 주 대상 모집단으로 하는 사용자를 선택합니다.

   ![](assets/dlv_seeds_usecase_26.png)

   사용자가 배달에 시드 주소를 추가합니다.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >**[!UICONTROL Edit the dynamic condition...]** 링크에 대한 자세한 내용은 [사용 사례:기준](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)에서 시드 주소 선택.

1. **[!UICONTROL Preview]** 탭을 클릭한 다음 개인화를 테스트할 시드 주소를 선택합니다.

   ![](assets/dlv_seeds_usecase_28.png)

   개인화 필드 중 하나가 비어 있음을 확인할 수 있습니다. 시드 주소에 이 필드에 대한 데이터가 없으므로 HTML 콘텐츠 미리 보기에 값을 표시할 수 없습니다.

   임의 대체 필드는 배달&#x200B;**시**&#x200B;에 수행됩니다.

1. **[!UICONTROL Send]** 버튼을 클릭합니다.
1. 배달 내용을 분석한 다음 **배달 확인**.

   시드 주소는 받은 편지함에 배달됩니다.

   필드 개인화는 효과적입니다.

   ![](assets/dlv_seeds_usecase_08.png)
