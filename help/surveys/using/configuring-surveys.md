---
product: campaign
title: 온라인 설문 조사 구성
description: 온라인 설문 조사를 구성하는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 387bc362-4064-4181-9385-8e0c3423ba3e
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# 온라인 설문 조사 구성{#configuring-surveys}



## 설문 조사 속성 {#survey-properties}

온라인 설문 조사는 요구 사항을 충족하도록 구성 및 사용자 지정할 수 있습니다. 등록 정보 창에 매개변수를 입력해야 합니다.

사용 가능한 매개 변수는 [이 문서](../../web/using/defining-web-forms-properties.md).

![](assets/s_ncs_admin_survey_properties_general.png)

## 설문 조사 데이터 저장소 {#survey-data-storage}

기본적으로 웹 양식 필드는 수신자 테이블에 저장됩니다. 다른 테이블을 사용하려면 **[!UICONTROL Document type]** 필드. 다음 **[!UICONTROL Zoom]** 아이콘을 사용하면 선택한 테이블의 컨텐트를 볼 수 있습니다.

필드(하지만 로컬 변수)에 저장되지 않는 사용자가 제공하는 설문 조사에 대한 답변은 **설문 조사 답변** 테이블. 를 기반으로 사용되는 스키마를 변경할 수 있습니다 **[!UICONTROL Library]** 필드. 이 필드는 다음에만 사용할 수 있습니다 **설문 조사**.
