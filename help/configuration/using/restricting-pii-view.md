---
solution: Campaign Classic
product: campaign
title: PII 보기 제한
description: PII 보기 제한
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---


# PII 보기 제한{#restricting-pii-view}

## 개요 {#overview}

일부 고객은 마케팅 사용자가 데이터 레코드에 액세스할 수 있어야 하지만 이름, 성 또는 이메일 주소와 같은 PII(개인 식별 정보)를 보는 것을 원하지 않습니다. Adobe Campaign은 개인 정보를 보호하고 일반 캠페인 운영자가 데이터를 잘못 사용하지 못하도록 하는 방법을 제안합니다.

## 구현 {#implementation}

모든 요소 또는 속성에 적용할 수 있는 새 속성이 스키마에 추가되어 기존 속성 **[!UICONTROL visibleIf]**&#x200B;을 보완합니다. 이 속성은 다음과 같습니다.**[!UICONTROL accessibleIf]** . 현재 사용자 컨텍스트와 관련된 XTK 식을 포함하는 경우 예를 들어 **[!UICONTROL HasNamedRight]** 또는 **[!UICONTROL $(login)]**&#x200B;을 활용할 수 있습니다.

아래 사용 방법을 보여주는 수신자 스키마 확장 샘플 파일을 찾을 수 있습니다.

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

기본 속성은 다음과 같습니다.

* **[!UICONTROL visibleIf]** :메타데이터에서 필드를 숨겨 스키마 보기, 열 선택 또는 표현식 빌더 내에서 액세스할 수 없습니다. 하지만 이 경우 필드 이름이 식에 수동으로 입력되면 값이 표시됩니다.
* **[!UICONTROL accessibleIf]** :결과 쿼리에서 데이터를 숨김(빈 값으로 바꾸기)합니다. visibleIf가 비어 있으면 **[!UICONTROL accessibleIf]**&#x200B;과 동일한 표현식이 표시됩니다.

다음은 Campaign에서 이 속성을 사용한 결과입니다.

* 데이터는 콘솔에서 일반 쿼리 편집기를 사용하여 표시되지 않습니다.
* 데이터는 개요 목록 및 레코드 목록(콘솔)에 표시되지 않습니다.
* 데이터는 세부 보기에서 읽기 전용이 됩니다.
* 데이터는 필터 내에서만 사용할 수 있습니다. 즉, 특정 이분법 전략을 사용해도 값을 추측할 수 있습니다.
* 제한된 필드를 사용하여 작성한 모든 표현식이 다음과 같이 제한됩니다.lower(@email)은 @email만큼 액세스할 수 있게 됩니다.
* 워크플로우에서는 제한된 열을 대상 모집단에 전환의 추가 열로 추가할 수 있지만 Adobe Campaign 사용자는 여전히 액세스할 수 없습니다.
* 그룹(목록)에 대상 모집단을 저장할 때 저장된 필드의 특성은 데이터 소스와 동일합니다.
* 기본적으로 JS 코드에는 데이터에 액세스할 수 없습니다.

## 추천 {#recommendations}

각 배달에서 이메일 주소는 **[!UICONTROL broadLog]** 및 **[!UICONTROL forecastLog]** 테이블에 복사됩니다.따라서 해당 필드도 보호해야 합니다.

다음은 이를 구현하는 로그 테이블 확장 샘플입니다.

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
>이 제한 사항은 기술 지식이 없는 사용자에게만 적용됩니다.관련 권한이 있는 기술 사용자는 데이터를 검색할 수 있습니다. 따라서 이 방법은 100% 보안이 되지 않습니다.

