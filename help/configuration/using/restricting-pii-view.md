---
product: campaign
title: PI 보기 제한
description: PI 보기를 제한하는 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: PI
exl-id: 0f32d62d-a10a-4feb-99fe-4679b98957d4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---

# PI 보기 제한{#restricting-pii-view}

## 개요 {#overview}

일부 고객은 마케팅 사용자가 데이터 레코드에 액세스할 수 있어야 하지만 이름, 성 또는 이메일 주소와 같은 PII(개인 식별 정보)를 확인하지 않았으면 합니다. Adobe Campaign은 개인 정보를 보호하고 일반 캠페인 운영자가 데이터를 오용하지 않도록 하는 방법을 제시한다.

## 구현 {#implementation}

모든 요소 또는 속성에 적용할 수 있는 새 속성이 스키마에 추가되었으며 기존 속성을 보완합니다 **[!UICONTROL visibleIf]** . 이 속성은 다음과 같습니다. **[!UICONTROL accessibleIf]** . 현재 사용자 컨텍스트와 관련된 XTK 표현식을 포함할 때 **[!UICONTROL HasNamedRight]** 또는 **[!UICONTROL $(login)]** 예:

아래에서 이 사용을 보여주는 수신자 스키마 확장 샘플을 찾을 수 있습니다.

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

주요 속성은 다음과 같습니다.

* **[!UICONTROL visibleIf]** : 필드를 메타데이터에서 숨기므로 스키마 보기, 열 선택 또는 표현식 빌더 내에서 액세스할 수 없습니다. 그러나 필드 이름을 표현식에 수동으로 입력하면 값이 표시되는 데이터가 표시되지 않습니다.
* **[!UICONTROL accessibleIf]** : 결과 쿼리에서 데이터를 숨깁니다(빈 값으로 바꾸기). visibleIf가 비어 있으면 와 동일한 표현식을 가져옵니다. **[!UICONTROL accessibleIf]** .

다음은 Campaign에서 이 특성을 사용할 때의 결과입니다.

* 콘솔에 일반 쿼리 편집기를 사용하여 데이터가 표시되지 않습니다.
* 데이터는 개요 목록 및 레코드 목록(콘솔)에 표시되지 않습니다.
* 세부 보기에서 데이터는 읽기 전용으로 됩니다.
* 데이터는 필터 내에서만 사용할 수 있습니다(즉, 일부 이분법 전략을 사용하면 값을 추측할 수 있음).
* 제한된 필드를 사용하여 작성된 모든 표현식도 제한됩니다. lower(@email)는 @email 액세스할 수 있게 됩니다.
* 워크플로우에서 제한된 열을 전환의 추가 열로 타겟팅된 모집단에 추가할 수 있지만 Adobe Campaign 사용자는 여전히 액세스할 수 없습니다.
* 그룹(목록)에 대상 모집단을 저장할 때 저장된 필드의 특성은 데이터 소스와 동일합니다.
* 기본적으로 데이터는 JS 코드에 액세스할 수 없습니다.

## 권장 사항 {#recommendations}

각 게재에서 이메일 주소는 **[!UICONTROL broadLog]** 및 **[!UICONTROL forecastLog]** 표: 따라서 이러한 필드도 보호해야 합니다.

다음은 이를 구현하기 위한 로그 테이블 확장의 샘플입니다.

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>이 제한은 기술 사용자가 아닌 사용자에게 적용됩니다. 관련 권한이 있는 기술 사용자는 데이터를 검색할 수 있습니다. 따라서 이 방법은 100% 안전하지 않습니다.
