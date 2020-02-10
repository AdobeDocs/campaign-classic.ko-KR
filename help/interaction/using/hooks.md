---
title: 후크
seo-title: 후크
description: 후크
seo-description: null
page-status-flag: never-activated
uuid: 4394717e-8625-4e2f-9492-3fd9b444a732
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 2b799ad7-b729-4b3e-9adc-1df13259f2a9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 후크{#hooks}

상호 작용의 후크를 사용하여 **표준 엔진 동작을**&#x200B;수정할 수 있습니다.

Adobe Campaign에서 **[!UICONTROL Target loading]** 및 **[!UICONTROL Proposition post-processing]** 후크가 오퍼 공간에 구성됩니다.

![](assets/interaction_hooks_1.png)

후크는 Adobe Campaign의 오퍼 가중치로 구성됩니다. **[!UICONTROL Dynamic offer]**

![](assets/interaction_hooks_2.png)

## 대상 로드 {#target-loading}

이 후크를 사용하면 외부 시스템의 추가 데이터와 함께 연락처의 프로필(기본 쿼리에서 로드됨)을 강화할 수 있습니다.

수집된 데이터는 호출 데이터 노드(상호 작용 노드)에 삽입해야 합니다. 통합자는 수집된 데이터의 구조를 정의하려면 먼저 호출 데이터 스키마를 연장해야 합니다. 사용자는 표준 호출 데이터와 같은 방식으로 이 데이터에 액세스할 수 있습니다(자격 조건 규칙 및 개인화 수준).

**입력 매개 변수:**

* xmlInteraction(xml 유형):상호 작용 노드
* aTargetId(테이블 유형):타겟 식별자
* sUuid230(문자열 유형):uuid230 영구 쿠키의 값
* Null(문자열 유형):인스턴스 세션 쿠키의 값

**반환 매개 변수:**

* 풍부해진 상호 작용 노드(이 후크의 첫 번째 매개 변수)

>[!NOTE]
>
>xmlInteraction **** 매개 변수에는 호출 데이터와 기본 쿼리에서 로드한 연락처의 프로필이 모두 포함됩니다.

**예:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## 제안 사후 처리 {#proposition-post-processing-}

이 후크를 사용하면 주어진 인터랙션에서 적합한 속성의 일관성과 호환성을 확인할 수 있습니다. 또한 새로운 점수 또는 가능성 계산 기능을 정의할 수 있습니다.

정합성 보장 규칙 사용 예:

* 동일한 호출에서 동일한 제품 또는 동일한 카테고리에 연결된 제안 수를 제한합니다.
* 동일한 상호 작용에서 제품과 관련된 오퍼만 제공합니다.

사후 처리는 유형 규칙 애플리케이션 및 적절한 제안 정렬 후 우선 순위 단계 전에 실행됩니다.

**입력 매개 변수:**

* 제안:자격 조건을 갖춘 제안 표. 다음은 이 표에 있는 요소의 구조에 대한 예입니다

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer(xml 유형):적격한 오퍼의 모든 속성(오퍼 코드, 카테고리 ID, 카테고리 전체 이름, 시작 날짜, 종료 날짜, 레이블, 내부 이름, 오퍼 ID, 추가 오퍼 필드)의 사전. 예

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget(xml 유형):프로필 데이터 노드
* xmlInteraction(xml 유형):호출 데이터 노드
* iPropNumber(정수 유형):예상 오퍼 수

**반환 매개 변수:**

* 수정된 속성 목록(후크의 첫 번째 매개 변수)
* 수정된 상호 작용 노드

**예:**

```
var aReturnedProps = [];

if( aProposition.length > 0 )
{
  var iReturnedProps = 0;
  for( var iPropIdx = 0; iPropIdx < aProposition.length && iReturnedProps < iPropNumber; iPropIdx ++ )
  {
    // Check a consistency rule for instance
    if( true )
    {
      aReturnedProps.push(aProposition[iPropIdx]);
      iReturnedProps++;
    }
  }
}

return aReturnedProps;
```

## 동적 오퍼 {#dynamic-offer}

이 후크를 사용하면 외부 엔진을 호출하여 오퍼에 연결된 제품 목록을 선택할 수 있습니다. 이것은 자격 조건 규칙 후와 유형 규칙 애플리케이션 전에 오퍼에 구성됩니다.

이전에 통합자는 제품에 대한 추가 **정보와 함께** Proposition PropositionRcp 스키마를 확장해야 합니다. 이 데이터를 저장할 위치를 지정하려면 공간의 **[!UICONTROL Proposition being processed]** **[!UICONTROL Storage]** 탭에서 링크를 사용할 수 있습니다

![](assets/interaction_hooks_3.png)

**입력 매개 변수:**

* xmlOffer(xml 유형):오퍼(오퍼 코드, 카테고리 ID, 카테고리 전체 이름, 시작 날짜, 종료 날짜, 레이블, 내부 이름, 오퍼 ID, 추가 오퍼 필드)
* 가중치:컨텍스트 두께(이중 유형)
* xmlTarget(xml 유형):프로필 데이터 노드
* xmlInteraction(xml 유형):호출 데이터 노드

**반환 매개 변수:**

생성할 제안 테이블이 반환됩니다. 이 표의 각 요소는 다음 정보로 구성됩니다.

* 오퍼 식별자
* 추가 제품 데이터(예: 제품 코드)
* 중량

>[!NOTE]
>
>시스템은 오퍼 ID가 입력 및 반환 매개 변수 모두에 대해 동일한지 확인합니다.

**예:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```

