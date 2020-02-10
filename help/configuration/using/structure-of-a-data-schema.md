---
title: 데이터 스키마 구조
seo-title: 데이터 스키마 구조
description: 데이터 스키마 구조
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 데이터 스키마 구조{#structure-of-a-data-schema}

데이터 스키마 구조는 트리 구조의 형태로 표시됩니다. Adobe Campaign 클라이언트 콘솔에서 그래픽을 보려면 타깃팅된 스키마를 선택하고 **[!UICONTROL Structure]** 하위 탭을 클릭합니다.

![](assets/d_ncs_integration_schema_arbo.png)

표준으로, 필드가 먼저 표시됩니다(활성, 활성화 등). 및 알파벳순으로 정렬합니다. 구조화 요소는 다음으로(우편 주소, 위치), 그리고 마지막으로 링크(이메일 정보, 폴더 등)를 가져옵니다.

기본 키는 빨간색 키로 식별되고 외래 키는 노란색 키로 식별됩니다.

링크는 테이블에 속하는지에 따라 그래픽으로 구분됩니다. 테이블에서 시작하는 테이블(즉, 표에 외래 키가 있는 것)이 먼저 표시됩니다(전자 메일 정보, 폴더, 국가). &quot;취소&quot; 컬렉션 링크(구독, 주문 등) 가 끝에 표시됩니다.
