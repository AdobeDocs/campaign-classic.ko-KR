---
product: campaign
title: 웹 추적 모드
description: 웹 추적 모드를 선택하는 방법을 알아봅니다
feature: Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
exl-id: b0f30c1f-cdc9-4ad2-8a6c-19d5aae4feb3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 1%

---

# 웹 추적 모드{#web-tracking-mode}



Adobe Campaign을 사용하면 애플리케이션에서 추적 로그가 처리되는 방식을 정의하는 웹 추적 모드를 선택할 수 있습니다.

사용 가능한 웹 추적 모드에는 세 가지가 있습니다. **&quot;세션 추적&quot;**,**&quot;영구 추적&quot;** 및 **&quot;익명 추적&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

각 모드에는 특정한 특성이 있습니다. &quot;영구&quot; 웹 추적 모드는 &quot;세션&quot; 웹 추적 모드의 특성을 포함하는 반면, &quot;익명&quot; 모드는 &quot;영구&quot; 및 &quot;세션&quot; 모드의 특성을 포함합니다.

>[!IMPORTANT]
>
>&quot;리드&quot; 패키지가 활성화된 경우 기본적으로 &quot;익명&quot; 웹 추적 모드가 활성화됩니다. 다른 모든 경우에는 기본적으로 &quot;세션&quot; 웹 추적 모드가 활성화됩니다.
>
>인스턴스 배포 마법사에서 언제든지 기본 모드를 변경할 수 있습니다.

를 사용하는 경우 주의하십시오. **영구 웹** 또는 **익명** 추적 모드에서는 추적 테이블(trackingLogXXX)의 &quot;sourceID&quot; 열(uuid230)에 인덱스를 추가해야 합니다.

1. 영구 추적과 관련된 추적 테이블을 식별합니다.
1. 다음 행을 추가하여 이러한 테이블과 일치하는 스키마를 확장합니다.

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**영구** 및 **익명** 웹 추적 모드에는 다음 두 가지 옵션이 포함됩니다. **강제 게재** 및 **마지막 게재**.

다음 **강제 게재** 옵션을 사용하면 추적하는 동안 게재(@jobid)의 식별자를 지정할 수 있습니다.

다음 **마지막 게재** 옵션을 사용하면 현재 추적 로그를 마지막으로 추적된 게재에 연결할 수 있습니다.

**세션 웹 추적 특성:**

이 모드는 세션 쿠키가 있는 사용자에 대한 추적 로그를 만듭니다. 이들은 Adobe Campaign에서 보낸 이메일에서 URL을 클릭했으므로 다음 정보를 추적할 수 있는 사람입니다.

* 게재 ID
* 연락처 ID
* 게재 로그
* 영구 쿠키(uuid230)
* 추적 URL
* 추적 로그 날짜

이 웹 추적 모드를 사용하면 정보 일부가 누락된 경우 애플리케이션에 추적 로그가 작성되지 않습니다.

이 모드는 볼륨(trackingLog 테이블의 제한된 레코드 수) 및 계산(조정 없음) 측면에서 경제적입니다.

**영구 웹 추적 모드의 특성:**

이 웹 추적 모드를 사용하면 영구 uuid230 쿠키의 존재를 기반으로 추적 로그를 만들 수 있습니다. 방문자가 세션을 닫는 경우 Adobe Campaign은 영구 쿠키를 사용하여 이전 추적 로그에서 방문자에 대한 정보를 복구합니다. 현재 세션의 uuid230이 추적 테이블에 이미 저장된 uuid230과 동일한 값을 갖는 경우 Adobe Campaign은 추적 로그를 다시 삽입합니다.

즉, uuid230 값에 대한 조정을 활성화하려면 방문자가 Adobe Campaign에서 (게재를 통해) 이전에 식별되어야 합니다.

기본적으로 이전 추적 로그의 검색은 &quot;trackingLog&quot; 테이블에서 수행됩니다. 리드 패키지가 활성화된 경우 &quot;trackingLog&quot; 테이블을 검색하기 전에 Adobe Campaign은 &quot;incomingLead&quot; 테이블에서 이전 추적 로그 레코드를 검색합니다.

이 모드는 로그 조정 시 계산 측면에서 많은 비용이 소요됩니다.

**익명 웹 추적 모드의 특성:**

이 웹 추적 모드를 사용하면 Adobe Campaign의 익명 탐색에 연결된 추적 로그를 검색할 수 있습니다. 추적 로그는 추적된 URL을 클릭할 때마다 자동으로 생성됩니다. 이 로그에는 uuid230 의 값만 있습니다. 마케팅 캠페인 중에 추적 로그는 모든 식별 정보와 함께 자동으로 만들어집니다(세션 추적 참조). Adobe Campaign은 이 마케팅 캠페인에 대한 추적 로그의 값과 동일한 &quot;uuid230&quot; 값을 이전 로그에서 자동으로 검색합니다. 동일한 값이 발견되면 모든 이전 추적 로그가 마케팅 캠페인 추적 로그의 모든 정보와 함께 입력됩니다.

이 모드는 계산과 부피 측면에서 비용이 가장 많이 든다.

>[!NOTE]
>
>다음과 같은 경우 **[!UICONTROL Leads]** 패키지가 설치되었습니다. 활동 테이블에 대해 동일한 작업을 수행해야 합니다(**crm:incomingLead**)

다음 스키마는 세 웹 추적 모드의 기능을 모두 요약한 것입니다.

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**마지막 게재를 기반으로 하는 영구 웹 추적의 예:**

플로렌스는 게재를 받고 이메일을 열고 링크를 클릭한 후 소매 사이트를 탐색하지만 구매는 하지 않습니다. 다음 날, 피렌체는 소매 사이트로 돌아와 탐색하고 구매합니다. 영구 웹 추적(마지막 게재)이 활성화되었으므로 두 번째 방문의 모든 로그가 전날 전송된 게재에 연결됩니다.
