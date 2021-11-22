---
product: campaign
title: 설정 단계
description: 설정 단계
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# 설정 단계{#setup-stages}

![](../../assets/v7-only.svg)

기본 원칙은 웹 사이트의 특정 페이지에 웹 추적 태그를 삽입하는 것입니다.

태그에는 두 가지 유형이 있습니다.

* **웹**: 이 태그는 페이지가 방문되었는지 여부를 알려줍니다.
* **트랜잭션**: 는 웹 태그처럼 작동하지만 생성된 비즈니스 볼륨에 대한 정보(예: 트랜잭션 금액, 구매한 항목 수 등)를 추가할 수 있는 가능성이 있습니다.

다음 단계를 적용하여 이러한 태그를 설정합니다.

1. 추적할 페이지를 식별하고 해당 유형(웹 또는 거래)을 결정합니다.
1. 수집할 추가 정보를 확인하고 **nms:webTrackingLog** 이 정보에 대한 설명이 있는 스키마. 기본적으로 이 스키마는 트랜잭션당 트랜잭션 금액 및 항목 수를 저장할 수 있습니다.
1. 웹 추적 태그 만들기. 다음 두 가지 방법으로 데이터를 수집할 수 있습니다.

   * Adobe Campaign 플랫폼에서 이러한 페이지에 해당하는 URL을 삽입한 다음 연결된 웹 추적 태그를 생성 및 추출합니다( **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 노드)를 포함할 수 없습니다.
   * &quot;즉시 생성&quot; 모드에서 직접 웹 추적 태그를 만듭니다. 이러한 페이지에 해당하는 URL은 Adobe Campaign 플랫폼에 자동으로 삽입됩니다.

1. 추적할 페이지에서 이러한 태그를 정적 또는 동적으로 추가합니다.

   >[!NOTE]
   >
   >모든 웹 유형 태그를 사이트의 페이지에 추가할 수 있습니다. 추가 정보(금액, 항목 등)를 포함하려면 TRANSACTION 태그를 동적으로 수정하거나 추가해야 합니다.

**예제**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```
