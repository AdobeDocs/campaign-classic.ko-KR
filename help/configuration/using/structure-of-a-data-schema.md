---
product: campaign
title: 데이터 스키마 구조
description: 데이터 스키마 구조
feature: Custom Resources
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 10%

---

# 데이터 스키마 구조{#structure-of-a-data-schema}

데이터 스키마의 구조는 트리 구조의 형태로 표시됩니다. Adobe Campaign 클라이언트 콘솔에서 그래픽으로 보려면 타겟팅된 스키마를 선택하고 **[!UICONTROL Structure]** 하위 탭.

![](assets/d_ncs_integration_schema_arbo.png)

기본적으로 필드가 먼저 표시됩니다(활성화, 활성화 등). 그리고 알파벳순으로. 구조 요소는 다음(우편 주소, 위치)에 있고, 마지막으로 링크(이메일 정보, 폴더 등)에 있습니다.

기본 키는 빨간색 키로 식별되며 외래 키는 노란색 키로 식별됩니다.

링크는 테이블에 속하는지 여부에 따라 그래픽으로 구별됩니다. 테이블에서 시작되는 항목, 즉 테이블에 외래 키가 있는 항목이 먼저 표시됩니다(이메일 정보, 폴더, 국가). &quot;역방향&quot; 컬렉션 링크(구독, 주문 등) 끝에 표시됩니다.
