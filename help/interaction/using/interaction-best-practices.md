---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic 인터랙션 모범 사례
description: 이 섹션에서는 Adobe Campaign Classic에서 상호 작용 모듈을 관리하는 모범 사례 방법을 설명합니다.
audience: interaction
content-type: reference
topic-tags: interaction-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1193'
ht-degree: 0%

---


# 상호 작용 모범 사례{#interaction-best-practices}

## 일반 권장 사항 {#general-recommendations}

이 섹션에서는 자격 조건 규칙, 사전 정의된 필터, 워크플로우 활동 및 데이터베이스 옵션을 포함하여 Adobe Campaign Classic에서 상호 작용 모듈을 관리하는 우수 사례 방법을 보여 줍니다.

Adobe Campaign에서 인터랙션하려면 관리가 까다로워 효율적으로 작업해야 합니다. 연락처 수와 오퍼 카테고리 및 오퍼 수 간의 균형을 찾아야 합니다. 이러한 요인을 신중하게 처리하지 않으면 Adobe Campaign 인스턴스에 문제가 발생할 수 있습니다.

### 구현 {#implementation}

다음은 인터랙션을 구현하고 구성할 때 기억해야 하는 중요한 요소입니다.

* 일괄 처리 엔진의 경우(일반적으로 이메일과 같은 아웃바운드 커뮤니케이션에서 사용됨), 여러 연락처를 동시에 처리할 수 있으므로 처리량이 주요 문제입니다. 일반적인 병목 현상은 데이터베이스 성능입니다.
* 단일 엔진에 대한 기본 제약 조건(일반적으로 웹 사이트의 배너와 같은 인바운드 커뮤니케이션에서 사용됨)은 누군가 답변을 기다리고 있기 때문에 지연입니다. 일반적인 병목 현상은 CPU 성능입니다.
* 오퍼 카탈로그 디자인은 Adobe Campaign Classic 성능에 큰 영향을 미칩니다.
* 오퍼가 많이 있으면 여러 오퍼 카탈로그로 분할합니다.

### 자격 조건 규칙 {#eligibility-rules}

다음은 자격 조건 규칙과 관련된 몇 가지 우수 사례입니다.

* 규칙 간소화 규칙의 복잡성은 조회 범위를 확장하면서 성능에 영향을 줍니다. 복잡한 규칙은 5개 이상의 조건이 있는 모든 규칙입니다.
* 성능을 높이기 위해 여러 오퍼에서 공유되는 사전 정의된 개별 필터에서 규칙을 분류할 수 있습니다.
* 트리에서 가능한 가장 높은 위치에 가장 제한적인 오퍼 카테고리 규칙을 배치합니다. 이렇게 하면 가장 많은 연락처를 먼저 필터링하여 타겟 번호를 줄이고 추가 규칙에 의해 처리되지 않습니다.
* 가장 비싼 규칙을 나무 아래에 놓거나 처리하는 데 쓰세요. 이렇게 하면 이 규칙은 나머지 대상 대상에서만 실행됩니다.
* 전체 트리를 스캔하지 않도록 특정 카테고리에서 시작합니다.
* 처리 시간을 절약하려면 조인으로 복잡한 규칙을 작성하는 대신 집계를 미리 계산합니다. 이렇게 하려면 자격 조건 규칙 내에서 조회할 수 있는 참조 표에 고객 데이터를 저장해 보십시오.
* 최소 가중치를 사용하여 쿼리 수를 제한합니다.
* 오퍼 공간당 오퍼 수가 제한된 것이 좋습니다. 이렇게 하면 주어진 공간에서 오퍼를 빠르게 검색할 수 있습니다.
* 특히 자주 사용하는 조회 열 시 인덱스를 사용합니다.

### 제안 테이블 {#proposition-table}

다음은 제안 표와 관련된 몇 가지 우수 사례입니다.

* 최소 규칙 수를 사용하여 가능한 빠르게 처리할 수 있습니다.
* 제안 표에서 기록 수를 제한합니다.상태 업데이트를 추적하는 데 필요한 레코드와 규칙에 필요한 내용을 저장한 다음 다른 시스템에 보관합니다.
* 색인 재구성이나 테이블 재생성과 같이 제안 표에서 복잡한 데이터베이스 유지 관리를 수행합니다.
* 대상당 요청 제안 수를 제한합니다. 실제로 사용할 내용 이상으로 설정하지 마십시오.
* 규칙 기준에서 가능한 한 조인을 사용하지 마십시오.

## 오퍼 관리에 대한 팁 및 트릭 {#tips-managing-offers}

이 섹션에는 오퍼를 관리하고 Adobe Campaign Classic에서 상호 작용 모듈을 사용하는 방법에 대한 자세한 설명이 포함되어 있습니다.

### 이메일 배달에서 여러 오퍼 공간 사용 {#multiple-offer-spaces}

오퍼에 오퍼를 포함하면 오퍼는 일반적으로 데이터 연계 강화 활동(또는 다른 유사한 활동)을 통해 캠페인 워크플로우에서 업스트림으로 선택됩니다.

연계 강화 활동에서 오퍼를 선택할 때 사용할 공간을 선택할 수 있습니다. 그러나 선택한 오퍼 공간에 관계없이 배달 사용자 지정 메뉴는 게재에 설정된 오퍼 공간에 따라 달라집니다.

아래 예에서 전달에서 선택한 오퍼 공간은 **[!UICONTROL Email (Environment - Recipient)]**&#x200B;입니다.

![](assets/Interaction-best-practices-offer-space-selected.png)

배달에서 선택하는 오퍼 공간에 HTML 렌더링 함수가 설정되어 있지 않으면 배달 메뉴에 나타나지 않고 선택할 수 없습니다. 다시 말하지만, 이것은 농축 활동에서 선택한 제안 공간과는 별개입니다.

아래 예에서, 배달에서 선택한 오퍼 공간에 렌더링 함수가 있기 때문에 드롭다운 목록에서 HTML 렌더링 함수를 사용할 수 있습니다.

![](assets/Interaction-best-practices-HTML-rendering.png)

이 함수는 다음과 같은 코드를 삽입합니다.`<%@ include proposition="targetData.proposition" view="rendering/html" %>`.

제안을 선택하면 **[!UICONTROL view]** 속성의 값은 다음과 같습니다.
* &quot;rendering/html&quot;:html 렌더링을 참조하십시오. HTML 렌더링 함수를 사용합니다.
* &quot;offer/view/html&quot;:html 콘텐츠를 참조하십시오. HTML 렌더링 함수를 사용하지 않습니다. 여기에는 HTML 필드만 포함됩니다.

단일 이메일 배달에 여러 개의 오퍼 공백이 포함되고 일부 오퍼에 렌더링 기능이 있고 일부 오퍼가 이 오퍼를 가지지 않은 경우, 어느 오퍼가 공백을 사용하고 어느 오퍼 공백이 렌더링 기능을 가지고 있는지 기억해야 합니다.

따라서 문제를 방지하려면 오퍼 공간에 HTML 컨텐츠만 필요한 경우에도 모든 오퍼 공간에 HTML 렌더링 함수가 정의되어 있는 것이 좋습니다.

### 제안 로그 테이블 {#rank-proposition-log-table}에서 등급 설정

오퍼 공백에는 proposition이 생성되거나 수락될 때 제안 테이블에 데이터를 저장할 수 있습니다.

![](assets/Interaction-best-practices-offer-space-storage.png)

하지만 이는 인바운드 상호 작용에만 적용됩니다.

아웃바운드 상호 작용을 사용할 때와 상호 작용 모듈 없이 아웃바운드 오퍼를 사용할 때도 제안 표에 추가 데이터를 저장할 수도 있습니다.

제안 테이블의 필드 이름과 이름이 일치하는 워크플로우 임시 테이블의 모든 필드가 제안 테이블의 동일한 필드에 복사됩니다.

예를 들어, Enrichment에서 수동으로(상호 작용 없음) 오퍼를 선택할 때 표준 필드는 다음과 같이 정의됩니다.

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

@rank 필드와 같은 추가 필드를 추가할 수 있습니다.

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

제안 테이블에 @rank라는 필드가 있으므로 워크플로우 임시 테이블의 값이 복사됩니다.

제안 테이블에 추가 필드를 저장하는 방법에 대한 자세한 내용은 워크플로우](../../interaction/using/integrating-an-offer-via-a-workflow.md#storing-offer-rankings-and-weights)를 통해 오퍼 통합을 참조하십시오.[

상호 작용이 있는 아웃바운드 오퍼의 경우, 여러 오퍼를 선택하고 오퍼가 이메일에 표시되는 순서를 기록하려는 경우에 유용합니다.

또한 현재 비용 수준과 같은 추가 메타데이터를 제안 표에 직접 저장하여 오퍼가 생성된 시간의 지출 내역 기록을 유지할 수도 있습니다.

아웃바운드 상호 작용을 사용할 때 위 예제와 같이 @rank 필드를 추가할 수 있지만 상호 작용에서 반환된 순서에 따라 값이 자동으로 설정됩니다. 예를 들어 상호 작용을 사용하여 3개의 오퍼를 선택하는 경우 @rank 필드에는 1, 2 및 3이 반환됩니다.

상호 작용을 사용하고 오퍼를 수동으로 선택할 때 두 접근 방식을 결합할 수 있습니다. 예를 들어 수동으로 선택한 오퍼에 대해 @rank 필드를 1로 수동으로 설정하고 상호 작용에 의해 반환된 오퍼에 대해 &quot;1 + @rank&quot;과 같은 표현식을 사용할 수 있습니다. 상호 작용이 3개의 오퍼를 선택했다고 가정할 경우, 두 접근 방식이 반환한 오퍼의 등급이 1-4로 지정됩니다.

![](assets/Interaction-best-practices-manual-offer-combined.png)

### nms:offer 스키마 {#extending-nms-offer-schema} 확장

nms:offer 스키마를 확장할 때는 이미 설정된 기본 구조를 따라야 합니다.
* `<element name="view">` 아래의 콘텐트 저장소에 대한 새 필드를 정의합니다.
* 각 새 필드를 두 번 정의해야 합니다. 일반 XML 필드로 한 번, 이름에 &quot;_jst&quot;가 추가된 CDATA XML 필드로 한 번 표시됨 예제:

   ```
   <element label="Price" name="price" type="long" xml="true"/>
   <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
   ```

* 추적할 URL이 포함된 모든 필드는 `<element name="view" >` 아래에 있는 `<element name="trackedUrls">` 아래에 배치해야 합니다.