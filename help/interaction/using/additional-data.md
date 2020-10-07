---
title: 추가 데이터
seo-title: 추가 데이터
description: 추가 데이터
seo-description: null
page-status-flag: never-activated
uuid: 81a889ce-b02d-4593-95fa-1de5601182e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 29339aad-fd8e-4dae-8f6e-2db87221ad04
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 1%

---


# 추가 데이터{#additional-data}

상호 작용 엔진에 대한 호출 동안 상황에 맞는 추가 정보를 전송할 수 있습니다. 이 데이터는 워크플로우(아웃바운드 채널)의 작업 테이블에 저장된 대상 데이터 또는 호출 동안 웹 사이트에서 보낸 호출 데이터(인바운드 채널)에서 가져올 수 있습니다. 이 추가 데이터를 자격 조건 규칙의 제안 개인화에 사용할 수 있으며, 이 데이터를 제안 표에 저장할 수도 있습니다.

인바운드 채널의 경우, 오퍼에 대해 상담하는 사용자의 브라우저 언어 또는 콜 센터 에이전트의 이름과 같은 정보를 복구하는 데 유용합니다. 그런 다음 자격 조건 규칙에서 이 호출 데이터를 사용하여 웹 페이지를 프랑스어 또는 영어로 보는 사람만 오퍼를 표시할 수 있습니다.

타깃팅 워크플로우(아웃바운드 채널)에서는 엔진에 대한 호출 동안 대상 데이터를 사용할 수 있습니다. 예를 들어 FDA를 통해 수신자 연결 트랜잭션 또는 외부 데이터베이스의 데이터로 대상을 보강할 수 있습니다.

## 추가 데이터 구성 {#additional-data-configuration}

환경에 연결된 **nms:interaction** 스키마를 확장하고 Interaction 엔진에 대한 호출 동안 사용할 추가 필드 목록을 선언해야 합니다. 자격 조건 규칙을 만들거나 오퍼를 개인화할 때 이러한 필드는 **상호 작용** 노드에서 액세스할 수 있게 됩니다(추가 데이터 [사용 참조](#using-additional-data)).

인바운드 채널의 경우 호출 데이터 필드를 **상호 작용** 노드에 추가해야 합니다.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

>[!NOTE]
>
>XML 컬렉션은 인바운드 채널에서 지원되지만 다른 스키마에 대한 링크는 지원되지 않습니다.

아웃바운드 채널의 경우 추가 필드를 포함하는 **targetData** 요소를 **Interaction** 노드에 추가해야 합니다.

```
<element label="Interactions" labelSingular="Interaction" name="interaction">
  <element name="targetData">
    <attribute label="Date of last transaction" name="lastTransactionDate" type="datetime"/>
  </element>
</element>
```

>[!NOTE]
>
>컬렉션은 아웃바운드 채널에서 지원되지 않습니다. 하지만 다른 스키마에 대한 링크를 만들 수 있습니다.

이 데이터를 제안 테이블에 저장하려면 nms:provisionsRcp **** 스키마도 확장하고 이러한 필드를 선언해야 합니다.

```
<element label="Recipient offer propositions" labelSingular="Recipient offer proposition" name="propositionRcp">
  <attribute label="Last transaction date" name="lastTransactionDate" type="datetime"/>
  <attribute label="Navigation language" name="navigationLanguage" type="string"/>
</element>
```

## 추가 데이터 구현 {#additional-data-implementation}

### 입력 채널(웹 페이지) {#input-channel--web-page-}

엔진을 호출할 때 추가 데이터를 전송하려면 **interactionGlobalCtx** 변수를 웹 페이지의 JavaScript 코드에 추가해야 합니다. 이 변수에 **호출** 데이터를 포함하는 상호 작용 노드를 삽입합니다. nms:interaction 스키마에 있는 동일한 xml 구조를 **준수해야** 합니다. 참조: [추가 데이터 구성](#additional-data-configuration).

```
interactionGlobalCtx = "<interaction navigationLanguage='"+myLanguage+"'/>";
```

### 출력 채널 {#output-channel}

nms:interaction **** 스키마와 동일한 xml 구조와 내부 이름을 준수하여 작업 테이블에 추가 데이터를 로드하는 타깃팅 워크플로우를 만들어야 합니다. 참조: [추가 데이터 구성](#additional-data-configuration).

## 추가 데이터 사용 {#using-additional-data}

### 자격 조건 규칙 {#eligibility-rules}

오퍼, 카테고리 및 가중치에 대한 자격 조건 규칙에서 추가 데이터를 사용할 수 있습니다.

예를 들어, 페이지를 영어로 보는 사람에게만 오퍼를 표시하도록 선택할 수 있습니다.

![](assets/ita_calldata_query.png)

>[!NOTE]
>
>데이터가 정의된 채널의 규칙을 제한해야 합니다. 이 예에서는 인바운드 웹 채널(필드)에 대한 규칙을&#x200B;**[!UICONTROL Taken into account if]** 제한합니다.

### 개인화 {#personalization}

오퍼를 개인화할 때 이 추가 데이터를 사용할 수도 있습니다. 예를 들어 탐색 언어의 조건을 추가할 수 있습니다

![](assets/ita_calldata_perso.png)

>[!NOTE]
>
>데이터가 정의된 채널에서 개인화를 제한해야 합니다. 이 예에서는 인바운드 웹 채널에 대한 규칙을 제한합니다.

추가 데이터를 사용하여 오퍼를 개인화한 경우 데이터베이스에서 사용할 수 없으므로 이 데이터는 기본적으로 미리 보기에 나타나지 않습니다. 환경 탭에서 미리 보기에 사용할 값 샘플을 **[!UICONTROL Example of call data]** 추가해야 합니다. nms:interaction **스키마 확장에 있는 동일한 xml 구조를** 존중하십시오. 자세한 내용은 추가 [데이터 구성을 참조하십시오](#additional-data-configuration).

![](assets/ita_calldata_preview.png)

미리 볼 때 필드 **[!UICONTROL Content personalization options for the preview]** 에서 값을 클릭하고 **[!UICONTROL Call data]** 선택합니다.

![](assets/ita_calldata_preview2.png)

### 스토리지 {#storage}

엔진에 대한 호출 동안 추가 데이터를 제안 테이블에 저장하여 데이터베이스를 보완할 수 있습니다. 이 데이터는 보고서, ROI 계산 또는 이후 프로세스에 사용할 수 있습니다.

>[!NOTE]
>
>nms:provisionsRcp **스키마를 확장하고** 저장할 데이터를 포함할 필드를 선언해야 합니다. 자세한 내용: [추가 데이터 구성](#additional-data-configuration).

오퍼 공간에서 **[!UICONTROL Storage]** 탭으로 이동한 후 **[!UICONTROL Add]** 단추를 클릭합니다.

열 **[!UICONTROL Storage path]** 에서 제안 테이블의 저장소 필드를 선택합니다. 열에서 **[!UICONTROL Expression]** 노드에서 추가 필드를 **[!UICONTROL Interaction]** 선택합니다.

제안이 생성되거나 수락될 때(사용자가 오퍼를 클릭할 때) 전화 데이터를 검색할 수 있습니다.

![](assets/ita_calldata_storage.png)

