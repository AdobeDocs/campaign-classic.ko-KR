---
title: 단계 설정
seo-title: 단계 설정
description: 단계 설정
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 단계 설정{#setup-stages}

기본 원칙은 웹 사이트의 특정 페이지에 웹 추적 태그를 삽입하는 것입니다.

태그에는 두 가지 유형이 있습니다.

* **웹**:이 태그는 페이지를 방문했는지,
* **트랜잭션**:은 웹 태그처럼 작동하지만 생성된 비즈니스 볼륨에 대한 정보(예: 거래 금액, 구입한 항목 수 등)를 추가할 수 있습니다.

다음 단계를 적용하여 이러한 태그를 설정합니다.

1. 추적할 페이지를 식별하고 해당 유형(웹 또는 트랜잭션)을 결정합니다.
1. 수집할 추가 정보를 확인하고 이 정보에 대한 설명과 함께 **nms:webTrackingLog** 스키마를 확장합니다. 기본적으로 이 스키마는 트랜잭션당 트랜잭션 금액 및 항목 수를 저장할 수 있습니다.
1. 웹 추적 태그 만들기 다음 두 가지 방법으로 이 작업을 수행할 수 있습니다.

   * Adobe Campaign 플랫폼에서 이러한 페이지에 해당하는 URL을 삽입한 다음 클라이언트 콘솔의 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 노드에서 관련 웹 추적 태그를 생성하고 추출합니다.
   * &quot;즉각적인 제작&quot; 모드에서 직접 웹 추적 태그를 만듭니다.이러한 페이지에 해당하는 URL은 Adobe Campaign 플랫폼에 자동으로 삽입됩니다.

1. 추적하려는 페이지에 이러한 태그를 정적이거나 동적으로 추가합니다.

   >[!NOTE]
   >
   >모든 WEB-type 태그는 사이트의 페이지에서처럼 추가할 수 있습니다. 추가 정보(금액, 항목 등)를 포함하려면 TRANSACTION 태그를 동적으로 수정하거나 추가해야 합니다.

**예**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```

