---
product: campaign
title: 확장 예제
description: 확장 예제
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 4%

---

# 확장 예제{#extension-example}



인바운드 연락처(콜 센터 또는 웹 사이트)의 경우 자격 규칙 세트를 사용하여 해당 연락처에 가장 적절한 오퍼를 제안합니다. 오퍼의 자격 기준을 강화하려면 다음을 확장합니다. **nms:interaction** 스키마.

* 새 상호 작용 컨텍스트를 추가하려면 **nms:interaction** 스키마와 만큼 생성 **속성** 스키마에 필요한 요소입니다.

  다음 예에서는 추가된 기준이 국가 코드 및 마지막으로 방문한 페이지입니다.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* 그런 다음 자격 기준 정의를 정의할 때 이전에 생성한 속성을 사용할 수 있습니다.

  다음 예제에서는 사용자의 국가 또는 마지막으로 본 웹 페이지를 기반으로 오퍼를 표시하는 자격 조건을 만들 수 있습니다.

  ![](assets/s_ncs_configuration_offer_context.png)

* SOAP 호출을 구성할 때 **컨텍스트** 상호 작용 스키마에 추가된 컨텍스트 정보를 참조하는 XML 요소입니다. 자세한 내용은 다음을 참조하십시오. [SOAP를 통한 통합(서버측)](../../interaction/using/integration-via-soap--server-side-.md).
