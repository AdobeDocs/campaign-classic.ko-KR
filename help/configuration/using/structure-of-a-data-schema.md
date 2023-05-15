---
product: campaign
title: 데이터 스키마 구조
description: 데이터 스키마 구조
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# 데이터 스키마 구조{#structure-of-a-data-schema}

데이터 스키마의 구조는 트리 구조의 형태로 표시됩니다. Adobe Campaign 클라이언트 콘솔에서 그래픽으로 보려면 타깃팅된 스키마를 선택하고 **[!UICONTROL Structure]** 하위 탭.

![](assets/d_ncs_integration_schema_arbo.png)

표준에서는 필드가 먼저 표시됩니다(활성, 활성화 등). 알파벳순으로 표시합니다. 구조 요소는 다음(우편 주소, 위치) 및 마지막으로 링크(이메일 정보, 폴더 등)를 표시합니다.

기본 키는 빨간색 키로 식별되고 외래 키는 노란색 키로 식별됩니다.

링크는 테이블에 속하는지에 따라 그래픽으로 구분됩니다. 테이블에서 시작하는 것, 즉 표에 외래 키가 있는 항목이 먼저 표시됩니다(전자 메일 정보, 폴더, 국가). &quot;역방향&quot; 수집 링크(구독, 주문 등) 끝에 표시됩니다.
