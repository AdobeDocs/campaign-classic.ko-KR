---
product: campaign
title: Campaign FDA 모범 사례 및 제한 사항
description: 외부 데이터베이스(FDA) 작업 시 모범 사례 및 제한 사항에 대해 알아봅니다
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---

# 모범 사례 및 제한 사항



## 외부 데이터로 이메일 개인화 최적화 {#optimizing-email-personalization-with-external-data}

전용 워크플로우에서 메시지 개인화를 사전 처리할 수 있습니다. 이 작업을 수행하려면 게재 속성의 **[!UICONTROL Prepare the personalization data with a workflow]** 탭에서 사용할 수 있는 **[!UICONTROL Analysis]** 옵션을 사용하십시오.

게재 분석 시 이 옵션은 외부 데이터베이스에 연결된 테이블의 데이터를 포함하여 대상에 연결된 모든 데이터를 임시 테이블에 저장하는 워크플로우를 자동으로 만들고 실행합니다.

이 옵션은 개인화 단계를 실행할 때 성능을 크게 향상시킵니다.

## 워크플로우에서 외부 데이터베이스의 데이터 사용 {#using-data-from-an-external-database-in-a-workflow}

여러 Adobe Campaign 워크플로우 활동에서 외부 데이터베이스에 저장된 데이터를 사용할 수 있습니다.

* **외부 데이터 필터링** - 쿼리 활동을 통해 외부 데이터를 추가하고 정의된 필터 구성에서 사용할 수 있습니다. 자세한 내용은 [Campaign v8 설명서]https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}를 참조하세요.

* **하위 집합 만들기** - 분할 활동을 사용하면 하위 집합을 만들 수 있습니다. 외부 데이터를 사용하여 사용할 필터링 기준을 정의할 수 있습니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}를 참조하세요.

* **외부 데이터베이스 로드** - RDBMS(데이터 로드) 활동에서 외부 데이터를 사용할 수 있습니다. 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html){target="_blank"}를 참조하세요.

* **정보 및 링크 추가** - 데이터 보강 활동을 통해 워크플로우의 작업 테이블에 데이터를 추가하고 외부 테이블에 대한 링크를 추가할 수 있습니다. 이 컨텍스트에서는 외부 데이터베이스의 데이터를 사용할 수 있습니다. [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}를 참조하세요.

## 가드레일 및 제한 사항 {#fda-limitations}

FDA 옵션은 워크플로우에서 배치 모드로 외부 데이터베이스의 데이터를 조작하도록 설계되었습니다. 성능 문제를 방지하기 위해 개인화, 상호 작용, 실시간 메시징 등과 같은 단일 작업의 컨텍스트에서는 FDA 모듈을 사용하지 않는 것이 좋습니다.

한 데이터베이스에서 데이터를 타겟팅하고 다른 데이터베이스에 속하는 필터링 차원을 사용하여 결과를 필터링하는 기능은 지원되지 않습니다. 한 쿼리에서 서로 다른 데이터 소스에 있는 테이블을 조인할 수 없습니다. 차원 변경과 같은 다른 워크플로우 활동을 사용하여 이 제한을 극복할 수 있습니다.

Adobe Campaign과 외부 데이터베이스를 모두 사용해야 하는 작업을 가능한 한 피하십시오. 모범 사례는 다음과 같습니다.

* Adobe Campaign 데이터베이스를 외부 데이터베이스로 내보내고 결과를 Adobe Campaign으로 다시 가져오기 전에 외부 데이터베이스에서만 작업을 실행합니다.

* 외부 Adobe Campaign 데이터베이스에서 데이터를 수집하고 작업을 로컬로 실행합니다.

외부 데이터베이스의 데이터를 사용하여 게재에서 개인화를 수행하려면 워크플로우에서 사용할 데이터를 수집하여 임시 테이블에서 사용할 수 있도록 하십시오. 그런 다음 임시 테이블의 데이터를 사용하여 게재를 개인화합니다.

FDA 옵션은 사용하는 외부 데이터베이스 시스템의 제한을 따릅니다.
