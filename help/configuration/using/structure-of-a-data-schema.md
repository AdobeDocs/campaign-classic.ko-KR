---
solution: Campaign Classic
product: campaign
title: 데이터 스키마 구조
description: 데이터 스키마 구조
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---


# 데이터 스키마 구조{#structure-of-a-data-schema}

데이터 스키마의 구조는 트리 구조의 형태로 표시됩니다. Adobe Campaign 클라이언트 콘솔에서 그래픽을 보려면 대상 스키마를 선택하고 **[!UICONTROL Structure]** 하위 탭을 클릭합니다.

![](assets/d_ncs_integration_schema_arbo.png)

표준으로서, 필드가 먼저 표시됩니다(활성, 활성화 등). 및 알파벳순으로 정렬합니다. 구조화 요소는 다음으로(우편 주소, 위치) 그리고 마침내 링크(이메일 정보, 폴더 등)가 됩니다.

기본 키는 빨간색 키로 식별되고 외래 키는 노란색 키로 식별됩니다.

링크는 테이블에 속하는지 여부에 따라 그래픽으로 구분됩니다. 테이블에 외래 키가 있는 테이블(즉, 테이블에 있는 외래 키가 있는)부터 시작되는 항목이 먼저 표시됩니다(전자 메일 정보, 폴더, 국가). &quot;취소&quot; 수집 링크(가입, 주문 등) 가 끝에 표시됩니다.
