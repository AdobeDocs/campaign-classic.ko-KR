---
product: campaign
title: Adobe Campaign 보고 도구 기본 정보
description: 빌드-인 또는 사용자 정의 보고서에서 캠페인의 성공을 분석합니다
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
exl-id: 1ef30004-e1b0-4dde-8104-0ee9e8aa9d8b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 19%

---

# 보고 시작하기 {#about-adobe-campaign-reporting-tools}



에 더하여 [기본 제공 보고서](../../reporting/using/about-campaign-built-in-reports.md), Adobe Campaign을 사용하면 다양한 컨텍스트에서 보고서를 생성하여 다양한 요구 사항을 충족할 수 있습니다. 사용 및 구현 모드의 원칙은 이 문서에 자세히 설명되어 있습니다.

Adobe Campaign은 전문 보고 도구가 아닙니다. Adobe Campaign에서 생성된 보고서는 주로 집계된 데이터를 볼 수 있도록 해줍니다. 데이터 분석 및 표시 전용인 Adobe Campaign 보고서는 데이터베이스 내보내기를 위해 설계되지 않았습니다.

Adobe Campaign 데이터베이스에서 데이터를 내보내려면 워크플로우를 만들고 데이터 내보내기 활동을 사용해야 합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/about-action-activities.md)을 참조하십시오.

Adobe Campaign은 다음과 같은 몇 가지 보고 도구를 제공합니다.

1. **기본 제공 보고서**: Adobe Campaign은 게재, 캠페인, 플랫폼 활동, 선택적 기능 등에 대한 보고서 세트를 제공합니다. 이러한 보고서는 관련 다양한 기능을 통해 사용할 수 있습니다. 특정 요구 사항에 맞게 조정할 수 있습니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/about-campaign-built-in-reports.md)을 참조하십시오.

1. **설명 데이터 분석**: Adobe Campaign은 데이터베이스의 데이터에 대한 통계를 생성하는 시각적 도구를 제공합니다. 전용 마법사를 사용하여 설명 분석 보고서를 만들고 필요에 따라 콘텐츠와 레이아웃을 조정할 수 있습니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/about-descriptive-analysis.md)을 참조하십시오.

1. **개인화된 보고서**: Adobe Campaign을 사용하면 데이터베이스의 데이터에 대한 보고서를 만들 수 있습니다. 이러한 폴더가 만들어지면 해당 컨텍스트에서 액세스할 수 있게 됩니다.

   쿼리, 계산 및 볼륨의 복잡성에 따라 이러한 보고서에서 분석된 데이터는 쿼리를 통해 수집되고 목록(&#39;데이터 관리&#39; 유형 워크플로우)이나 큐브( Marketing Analytics 사용)에서 미리 집계될 수 있습니다. 피벗 테이블 또는 그룹 목록 형식으로 표시됩니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/about-reports-creation-in-campaign.md)을 참조하십시오.

1. **분석 보고서**: Marketing Analytics를 사용하면 직관적인 데이터 탐색이 가능합니다.

   이 작업에 대한 자세한 정보는 [이 섹션](../../reporting/using/ac-cubes.md)을 참조하십시오.

>[!CAUTION]
>
>간편한 표시 및 조작과 효율적인 내보내기를 위해 보고서에는 1,000개 이상의 행이 포함될 수 없습니다.
