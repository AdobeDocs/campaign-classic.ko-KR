---
title: Adobe Campaign Classic 상호 작용 우수 사례
description: 이 섹션에서는 Adobe Campaign Classic에서 상호 작용 모듈을 관리하는 모범 사례를 제공합니다.
page-status-flag: never-activated
uuid: 88bcc1d5-be8f-4a63-9b4a-3843b5751abe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: interaction-overview
discoiquuid: 85e8348f-d240-4a36-b7bd-645807dbc227
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 91f80adf0b84d45a71e07079d4e72fd7628b41c1

---


# 인터랙션 모범 사례{#interaction-best-practices}

## 일반 추천 {#general-recommendations}

이 섹션에서는 자격 조건 규칙, 사전 정의된 필터, 워크플로우 활동 및 데이터베이스 옵션을 포함하여 Adobe Campaign Classic에서 상호 작용 모듈을 관리하는 모범 사례를 제공합니다.

Adobe Campaign의 상호 작용을 효율적으로 실행하려면 세심한 관리가 필요합니다. 연락처 수와 오퍼 카테고리 및 오퍼 수 간의 균형을 찾아야 합니다. 이러한 요소가 조심스럽게 처리되지 않으면 Adobe Campaign 인스턴스에 문제가 발생할 수 있습니다.

### 구현 {#implementation}

다음은 인터랙션을 구현하고 구성할 때 기억해야 하는 중요한 요소입니다.

* 일괄 처리 엔진의 경우(일반적으로 이메일과 같은 아웃바운드 커뮤니케이션에서 사용됨), 여러 연락처를 동시에 처리할 수 있으므로, 처리량은 주요 관심사입니다. 일반적인 병목은 데이터베이스 성능입니다.
* 단일 엔진에 대한 기본 제한(일반적으로 웹 사이트의 배너와 같은 인바운드 통신에 사용됨)은 누군가 응답을 예상하고 있기 때문에 지연입니다. 일반적인 병목 현상은 CPU 성능입니다.
* 오퍼 카탈로그 디자인은 Adobe Campaign Classic 성능에 큰 영향을 줍니다.
* 오퍼가 많을 때는 여러 오퍼 카탈로그로 분할하십시오.

### 자격 조건 규칙 {#eligibility-rules}

다음은 자격 조건 규칙과 관련된 몇 가지 우수 사례입니다.

* 규칙 간소화 규칙의 복잡성은 조회 범위를 확장하면서 성능에 영향을 줍니다. 복잡한 규칙은 5개 이상의 조건을 가진 모든 규칙입니다.
* 성능을 높이기 위해 여러 오퍼에서 공유되는 사전 정의된 개별 필터에서 규칙을 분류할 수 있습니다.
* 트리에서 가장 제한적인 오퍼 카테고리 규칙을 가장 높은 위치에 배치합니다. 이렇게 하면 가장 많은 연락처를 먼저 필터링하여 타겟 번호를 줄이고 추가 규칙에 의해 처리되지 않습니다.
* 가장 비싼 규칙을 트리 하단에 배치하거나 처리 시간을 단축하십시오. 이렇게 하면 이 규칙은 나머지 대상 대상에서만 실행됩니다.
* 전체 트리를 스캔하지 않도록 특정 카테고리에서 시작합니다.
* 처리 시간을 절약하려면 조인으로 복잡한 규칙을 작성하는 대신 집계를 미리 계산합니다. 이렇게 하려면 자격 조건 규칙 내에서 조회할 수 있는 참조 표에 고객 데이터를 저장해 보십시오.
* 최소 가중치를 사용하여 쿼리 수를 제한합니다.
* 오퍼 공간당 오퍼 수를 제한하는 것이 좋습니다. 이렇게 하면 주어진 공간에서 오퍼를 빠르게 검색할 수 있습니다.
* 특히 자주 사용하는 조회 열에 인덱스를 사용합니다.

### 제안 테이블 {#proposition-table}

다음은 제안 표와 관련된 몇 가지 우수 사례입니다.

* 최소 규칙 수를 사용하여 가능한 빠르게 처리할 수 있습니다.
* 제안 표에서 레코드 수를 제한합니다.상태 업데이트를 추적하는 데 필요한 레코드와 규칙에 필요한 정보만 보관하고 다른 시스템에 보관합니다.
* 인덱스 재구성이나 테이블 재생성과 같은 제안 테이블에서 데이터베이스 유지 관리를 많이 수행합니다.
* 대상당 요청 제안 수를 제한합니다. 실제로 사용할 내용 이상을 설정하지 마십시오.
* 규칙 기준에서 가능한 한 조인을 사용하지 마십시오.

## 오퍼 관리에 대한 팁 및 기법 {#tips-managing-offers}

이 섹션에는 오퍼 관리와 Adobe Campaign Classic의 상호 작용 모듈 사용에 대한 자세한 정보가 포함되어 있습니다.

### 이메일 배달에서 여러 오퍼 공간 사용 {#multiple-offer-spaces}

오퍼에 오퍼를 포함할 때 오퍼는 일반적으로 데이터 연계 활동(또는 다른 유사한 활동)을 통해 캠페인 워크플로에서 업스트림으로 선택됩니다.

연계 강화 활동에서 오퍼를 선택할 때 사용할 공간을 선택할 수 있습니다. 그러나 선택한 오퍼 공간에 관계없이 배달 사용자 지정 메뉴는 전달에 설정된 오퍼 공간에 따라 달라집니다.

아래 예에서 전달에서 선택한 오퍼 공간은 **[!UICONTROL Email (Environment - Recipient)]**&#x200B;다음과 같습니다.

![](assets/Interaction-best-practices-offer-space-selected.png)

배달에서 선택한 오퍼 공간에 HTML 렌더링 기능이 설정되어 있지 않으면 배달 메뉴에 나타나지 않고 선택할 수 없게 됩니다. 다시 한 번, 이것은 농축활동에서 선택한 제안 공간과는 별개입니다.

아래 예에서, 배달에서 선택한 오퍼 공간에 렌더링 함수가 있기 때문에 드롭다운 목록에서 HTML 렌더링 함수를 사용할 수 있습니다.

![](assets/Interaction-best-practices-HTML-rendering.png)

이 함수는 다음과 같은 코드를 삽입합니다. `<%@ include proposition="targetData.proposition" view="rendering/html" %>`Adobe

제안을 선택하면 속성의 값은 다음과 같습니다. **[!UICONTROL view]**
* &quot;rendering/html&quot;:html 렌더링. HTML 렌더링 함수를 사용합니다.
* &quot;offer/view/html&quot;:html 콘텐츠를 표시합니다. HTML 렌더링 함수를 사용하지 않습니다. 여기에는 HTML 필드만 포함됩니다.

하나의 이메일 배달에 여러 오퍼 공백이 포함되고 일부 오퍼에 렌더링 기능이 없고 일부 오퍼에 렌더링 기능이 없는 경우, 어떤 오퍼가 어떤 오퍼를 사용하는지, 그리고 어떤 오퍼 공백이 렌더링 기능을 가지고 있는지 기억해야 합니다.

따라서 문제를 방지하려면 오퍼 공간에 HTML 컨텐츠만 필요한 경우에도 모든 오퍼 공간에 HTML 렌더링 기능이 정의되어 있는 것이 좋습니다.

### 제안 로그 테이블의 등급 설정 {#rank-proposition-log-table}

오퍼 공백은 제안을 생성하거나 수락할 때 제안 표에 데이터를 저장할 수 있습니다.

![](assets/Interaction-best-practices-offer-space-storage.png)

그러나 이는 인바운드 상호 작용에만 적용됩니다.

아웃바운드 상호 작용을 사용할 때와 상호 작용 모듈 없이 아웃바운드 오퍼를 사용할 때에도 제안 표에 추가 데이터를 저장할 수도 있습니다.

제안 테이블의 필드 이름과 이름이 일치하는 워크플로우 임시 테이블의 모든 필드는 제안 테이블의 동일한 필드에 복사됩니다.

예를 들어, Enrichment에서 수동으로(상호 작용 없음) 오퍼를 선택할 때 표준 필드는 다음과 같이 정의됩니다.

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

@rank 필드와 같은 추가 필드를 추가할 수 있습니다.

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

@rank라는 제안 테이블에 필드가 있으므로 워크플로 임시 테이블의 값이 복사됩니다.

제안 표에 추가 필드를 저장하는 방법에 대한 자세한 내용은 [워크플로우를](../../interaction/using/integrating-an-offer-via-a-workflow.md#storing-offer-rankings-and-weights)통해 오퍼 통합을 참조하십시오.

상호 작용이 있는 아웃바운드 오퍼의 경우, 여러 오퍼를 선택하고 오퍼가 이메일에 표시되는 순서를 기록하려는 경우 유용합니다.

또한 현재 지출 수준과 같은 추가 메타데이터를 제안 표에 직접 저장하여 오퍼가 생성된 시점의 지출에 대한 내역 기록을 유지할 수 있습니다.

아웃바운드 상호 작용을 사용할 때 위 예에서처럼 @rank 필드를 추가할 수 있지만, 이 필드의 값은 상호 작용에서 반환된 순서에 따라 자동으로 설정됩니다. 예를 들어 상호 작용을 사용하여 세 개의 오퍼를 선택하는 경우 @rank 필드에는 값 1, 2 및 3이 반환됩니다.

상호 작용을 사용하고 오퍼를 수동으로 선택할 때 사용자는 두 가지 방법을 결합할 수 있습니다. 예를 들어 사용자가 수동으로 선택한 오퍼에 대해 @rank 필드를 1로 수동으로 설정하고 상호 작용에 의해 반환되는 오퍼에 대해 &quot;1 + @rank&quot;와 같은 표현식을 사용할 수 있습니다. 상호 작용이 세 개의 오퍼를 선택한다고 가정할 경우, 두 접근 방식이 반환하는 오퍼의 등급이 1-4로 지정됩니다.

![](assets/Interaction-best-practices-manual-offer-combined.png)

### nms:오퍼 스키마 확장 {#extending-nms-offer-schema}

nms:offer 스키마를 확장할 때는 이미 설정된 기본 구조를 따라야 합니다.
* 에서 콘텐트 저장소에 대한 새 필드를 `<element name="view">`정의합니다.
* 각 새 필드를 두 번 정의해야 합니다. 한 번 정규 XML 필드로, 한 번은 이름에 &quot;_jst&quot;가 추가된 CDATA XML 필드로 사용됩니다. 예:

   ```
   <element label="Price" name="price" type="long" xml="true"/>
   <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
   ```

* 추적할 URL이 들어 있는 필드는 아래에서 찾을 수 `<element name="trackedUrls">` 있는 위치에 `<element name="view" >`배치해야 합니다.