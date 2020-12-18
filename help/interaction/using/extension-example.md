---
solution: Campaign Classic
product: campaign
title: 확장 예제
description: 확장 예제
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# 확장 예제{#extension-example}

인바운드 연락처(콜 센터 또는 웹 사이트)의 경우, 가장 관련성이 높은 오퍼는 자격 조건 규칙을 사용하여 지정된 연락처에 제안됩니다. 오퍼의 자격 조건을 강화하려면 **nms:interaction** 스키마를 확장하십시오.

* 새 상호 작용 컨텍스트를 추가하려면 **nms:interaction** 스키마를 확장하고 스키마에 필요한 만큼 **attribute** 요소를 만듭니다.

   다음 예에서, 추가된 기준은 국가 코드와 마지막으로 방문한 페이지입니다.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 그런 다음 자격 조건 정의를 정의할 때 이전에 만든 속성을 사용할 수 있습니다.

   다음 예에서는 사용자의 국가 또는 사용자가 본 마지막 웹 페이지를 기반으로 오퍼를 표시하는 자격 조건을 만들 수 있습니다.

   ![](assets/s_ncs_configuration_offer_context.png)

* SOAP 호출을 구성할 때 상호 작용 스키마에 추가된 컨텍스트 정보를 참조하도록 **context** XML 요소를 삽입합니다. 자세한 내용은 [SOAP를 통한 통합(서버측)](../../interaction/using/integration-via-soap--server-side-.md)을 참조하십시오.

