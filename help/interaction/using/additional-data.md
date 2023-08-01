---
product: campaign
title: 추가 데이터
description: 추가 데이터
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 01adb584-5308-4d41-a6f1-223a97efa10f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---

# 추가 데이터{#additional-data}



상호 작용 엔진을 호출하는 동안 상황별 추가 정보를 전송할 수 있습니다. 이 데이터는 워크플로우의 작업 표에 저장된 대상 데이터(아웃바운드 채널) 또는 호출 동안 웹 사이트에서 보낸 호출 데이터(인바운드 채널)에서 가져올 수 있습니다. 이 추가 데이터는 자격 규칙, 오퍼 개인화에서 사용할 수 있으며 제안 테이블에도 저장할 수 있습니다.

인바운드 채널의 경우, 오퍼를 컨설팅하는 사용자의 브라우저 언어나 콜 센터 에이전트의 이름과 같은 정보를 복구하는 것이 유용할 수 있습니다. 그런 다음 자격 규칙에서 이 호출 데이터를 사용하여 프랑스어 또는 영어로 웹 페이지를 보는 사람들에게만 오퍼를 표시할 수 있습니다.

타겟팅 워크플로우(아웃바운드 채널)에서는 엔진을 호출하는 동안 타겟 데이터를 사용할 수 있습니다. 예를 들어 FDA를 통해 수신자 연결된 트랜잭션 또는 외부 데이터베이스의 데이터로 타겟을 보강할 수 있습니다.

## 추가 데이터 구성 {#additional-data-configuration}

다음을 확장해야 합니다. **nms:interaction** 환경에 연결된 스키마를 선언하고 상호 작용 엔진 호출 중에 사용할 추가 필드 목록을 선언합니다. 자격 규칙을 만들거나 오퍼를 개인화할 때에서 이러한 필드에 액세스할 수 있습니다. **상호 작용** 노드( 참조) [추가 데이터 사용](#using-additional-data)).

인바운드 채널의 경우 호출 데이터 필드를 **상호 작용** 노드.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>Xml 컬렉션은 인바운드 채널에서 지원되지만 다른 스키마에 대한 링크는 지원되지 않습니다.

아웃바운드 채널의 경우 다음을 추가해야 합니다 **targetData** 에 추가 필드가 포함된 요소 **상호 작용** 노드.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>컬렉션은 아웃바운드 채널에 대해 지원되지 않습니다. 하지만 다른 스키마에 대한 링크를 만들 수 있습니다.

제안 테이블에 이 데이터를 저장하려면 도 확장해야 합니다. **nms:propositionRcp** 이러한 필드를 스키마하고 선언합니다.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## 추가 데이터 구현 {#additional-data-implementation}

### 입력 채널(웹 페이지) {#input-channel--web-page-}

엔진을 호출할 때 추가 데이터를 전송하려면 다음을 추가해야 합니다 **interactionGlobalCtx** 변수를 웹 페이지의 JavaScript 코드에 추가합니다. 삽입 **상호 작용** 이 변수에 대한 호출 데이터를 포함하는 노드입니다. 에 있는 것과 동일한 xml 구조를 준수해야 합니다. **nms:interaction** 스키마. 다음을 참조하십시오. [추가 데이터 구성](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### 출력 채널 {#output-channel}

와 동일한 xml 구조 및 내부 이름을 고려하여 작업 표에 추가 데이터를 로드하는 타겟팅 워크플로우를 만들어야 합니다. **nms:interaction** 스키마. 다음을 참조하십시오. [추가 데이터 구성](#additional-data-configuration).

## 추가 데이터 사용 {#using-additional-data}

### 자격 규칙 {#eligibility-rules}

오퍼, 카테고리 및 가중치에 대한 자격 규칙에서 추가 데이터를 사용할 수 있습니다.

예를 들어, 영어로 페이지를 보는 사람에게만 오퍼를 제공하도록 선택할 수 있습니다.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>데이터가 정의된 채널에서 규칙을 제한해야 합니다. 이 예제에서는 인바운드 웹 채널(**[!UICONTROL Taken into account if]** field).

### 개인화 {#personalization}

오퍼를 개인화할 때 이 추가 데이터를 사용할 수도 있습니다. 예를 들어 탐색 언어에 대한 조건을 추가할 수 있습니다

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>데이터가 정의된 채널에서 개인화를 제한해야 합니다. 이 예에서는 인바운드 웹 채널에 대한 규칙을 제한하고 있습니다.

추가 데이터를 사용하여 오퍼를 개인화한 경우 이 데이터는 데이터베이스에서 사용할 수 없으므로 기본적으로 미리보기에 표시되지 않습니다. 의 환경에서 **[!UICONTROL Example of call data]** 탭에서 미리 보기에 사용할 값 샘플을 추가해야 합니다. 에 있는 것과 동일한 xml 구조를 존중하십시오. **nms:interaction** 스키마 확장명. 자세한 내용은 다음을 참조하십시오. [추가 데이터 구성](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

미리 볼 때 **[!UICONTROL Content personalization options for the preview]** 및 다음에서 값 선택 **[!UICONTROL Call data]** 필드.

![](assets/ita_calldata_preview2.png)

### 스토리지 {#storage}

엔진을 호출하는 동안에는 제안 테이블에 추가 데이터를 저장하여 데이터베이스를 보강할 수 있습니다. 이 데이터는 보고서, ROI 계산 또는 이후 프로세스 등에 사용할 수 있습니다.

>[!NOTE]
>
>을(를) 연장했어야 합니다. **nms:propositionRcp** 저장할 데이터를 포함할 필드를 스키마와 선언했습니다. 자세한 내용: [추가 데이터 구성](#additional-data-configuration).

오퍼 공간에서 **[!UICONTROL Storage]** 탭을 클릭하고 **[!UICONTROL Add]** 단추를 클릭합니다.

다음에서 **[!UICONTROL Storage path]** 열에서 제안 테이블의 저장 영역 필드를 선택합니다. 다음에서 **[!UICONTROL Expression]** 열에서 추가 필드를 선택합니다 **[!UICONTROL Interaction]** 노드.

제안이 생성되거나 수락될 때(사용자가 오퍼를 클릭할 때) 호출 데이터를 검색할 수 있습니다.

![](assets/ita_calldata_storage.png)
