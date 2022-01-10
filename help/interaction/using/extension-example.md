---
product: campaign
title: 확장 예제
description: 확장 예제
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 07a5742c6f142c786ad8ba2f8774e7e90e8cd191
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# 확장 예제{#extension-example}

![](../../assets/common.svg)

인바운드 연락처(콜 센터 또는 웹 사이트)의 경우 자격 규칙 세트를 사용하여 주어진 연락처에 가장 연관성 있는 오퍼를 추천합니다. 오퍼의 자격 기준을 보강하려면 **nms:상호 작용** 스키마.

* 새 상호 작용 컨텍스트를 추가하려면 **nms:상호 작용** 스키마 및 만들기 **특성** 스키마에 필요한 요소.

   다음 예에서는 추가된 기준이 국가 코드와 마지막으로 방문한 페이지입니다.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* 그런 다음 자격 기준 정의를 정의할 때 이전에 생성한 속성을 사용할 수 있습니다.

   다음 예에서는 사용자의 국가 또는 마지막으로 본 웹 페이지에 따라 오퍼를 표시하는 자격 기준을 만들 수 있습니다.

   ![](assets/s_ncs_configuration_offer_context.png)

* SOAP 호출을 구성할 때 **컨텍스트** 상호 작용 스키마에 추가된 컨텍스트 정보를 참조하는 XML 요소입니다. 자세한 내용은 [SOAP를 통한 통합(서버측)](../../interaction/using/integration-via-soap--server-side-.md).
