---
title: 설문 조사 정보
seo-title: 설문 조사 정보
description: 설문 조사 정보
seo-description: null
page-status-flag: never-activated
uuid: 31a07a48-2ebb-4b51-ae24-382f3ce3f04a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: ef7d9b16-506a-409c-a578-000b88cd17a2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 설문 조사 정보{#about-surveys}

Adobe Campaign에는 웹 애플리케이션을 정의하고 게시하는 그래픽 모듈이 포함되어 있습니다. 이 기능은 엑스트라넷의 편집 양식과 같은 페이지를 만들거나 테이블, 차트, 입력 양식 등이 있는 데이터베이스의 데이터를 포함하는 알림 양식을 만드는 데 사용됩니다. 이 기능을 사용하면 사용자가 정보를 조회하거나 입력할 수 있는 웹 페이지를 디자인하고 게시할 수 있습니다.

선택 **사항인** 설문 조사 모듈을 사용하면 새로운 유형의 웹 애플리케이션을 만들어 프로필 정보를 추가 또는 수정할 양식, 정보 서비스 구독 또는 구독 취소, 경쟁 응모 양식을 만들고 관리할 수 있습니다. 대답이 수집되면 데이터베이스 또는 로컬 변수에 저장됩니다. 데이터 모델은 설문 조사에 제공된 답변을 통해 동적으로 확장할 수 있습니다. 실시간으로 결과를 보고, 응답을 필터링하고, 전용 차트를 사용하여 분석할 수 있습니다.

이 장에서는 설문 조사, 필드 및 페이지 **관리**, 저장소 모드 및 레코드를 만들고 관리하는 방법에 대해 자세히 설명합니다.

표준 웹 양식을 만드는 단계는 [이 섹션에](../../web/using/about-web-forms.md)자세히 설명되어 있습니다.

웹 애플리케이션 관리는 [이 섹션에](../../web/using/about-web-applications.md)자세히 설명되어 있습니다. 자세한 내용은 이 장을 참조하십시오.

>[!CAUTION]
>
>개인 정보상의 이유로 모든 외부 리소스에 대해 HTTPS를 사용하는 것이 좋습니다.

## 캠페인 설문 조사 범위 {#campaign-surveys-scope}

Adobe Campaign에서 일반적으로 웹 애플리케이션을 사용하면 다음 기능에 액세스할 수 있습니다.

* 여러 페이지 양식 작성,
* 통합 번역 툴을 통한 다국어 설문 조사 관리,
* 그래픽 페이지 관리 인터페이스, 여러 열로 구성된 페이지 레이아웃,
* 개인화 및 필드 위치 렌더링,
* 응답에 따라 설문 조사 필드 조건부 표시,
* 조건부 페이지 표시,
* 예상 데이터 유형(번호, 이메일 주소, 날짜 등)에 따라 승인 전 정보 확인 및 필수 필드,
* 이메일 초대장/알림,
* 오류 및 종료 메시지의 개인화,
* 이미지, 비디오, 하이퍼텍스트 링크, captcha 등의 사용

>[!NOTE]
>
>웹 양식에 연결된 모든 구성은 [이 섹션에](../../web/using/about-web-forms.md)자세히 설명되어 있습니다. 개념과 Adobe Campaign을 사용한 웹 양식 기능에 대한 자세한 내용은 이 문서를 참조하십시오.

선택적 설문 조사 작성 모듈(**설문 조사**)은 다음과 같은 추가 기능을 제공합니다.

* 데이터베이스의 동적 확장:초기 데이터 모델의 일부가 아닌 답변 작성 자세한 내용은 수집된 대답 [저장을 참조하십시오](../../web/using/managing-answers.md#storing-collected-answers).
* 점수 관리. 자세한 내용은 점수 관리를 [참조하십시오](../../web/using/managing-answers.md#score-management).
* 무작위 질문 표시. 자세한 내용은 질문 [추가를 참조하십시오](../../web/using/building-a-survey.md#adding-questions).
* 응답의 실시간 추적 자세한 내용은 응답 [추적을](../../web/using/publish--track-and-use-collected-data.md#response-tracking)참조하십시오.
* 전용 보고서 생성. 자세한 내용은 설문 조사에 [대한](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys)보고서를 참조하십시오.

웹 애플리케이션과 비교하여 설문 조사는 적은 수의 편집 컨트롤과 함께 간소화된 그래픽 인터페이스를 제공합니다.

## 설문 조사 구현 단계 {#surveys-implementation-steps}

설문 조사를 만들고 전달하고 결과를 처리하려면 다음 단계를 수행하십시오.

1. 설문 조사의 페이지와 해당 컨텐츠(입력 필드, 드롭다운 목록, 질문 등)를 만듭니다.
1. 답변 저장 방법을 정의합니다.

   데이터베이스에 이미 있는 데이터로 양식을 미리 로드하려면 데이터 사전 로드 단계를 삽입할 수 있습니다. 테스트 상자를 추가할 수도 있습니다.

1. 게시한 다음 설문 조사를 수신자에게 제공합니다(예: 게재 또는 웹 사이트에 링크 포함).
1. 응답 모니터링 및 보고서 보기

이러한 단계 구성 및 시퀀스에 대한 자세한 내용은 [이 섹션을](../../web/using/about-web-forms.md)참조하십시오. 이 장에서는 설문 조사 전용 구성만 자세히 설명합니다.

## 설문 조사 구성 {#surveys-configuration}

설문 조사는 Adobe Campaign 트리의 **[!UICONTROL Resources > Online > Web Applications]** 노드에 저장됩니다. 구성은 다음 폴더에 있습니다.

* **[!UICONTROL Administration > Configuration > Form rendering]**:에는 웹 양식 프레젠테이션(응용 프로그램 및 설문 조사)용 렌더링 템플릿이 포함되어 있습니다.
* **[!UICONTROL Resources > Templates > Web application templates]**:에 양식 템플릿이 포함되어 있습니다. 양식을 만들려면 템플릿으로 시작해야 합니다.

>[!NOTE]
>
>구성 정보는 [이 섹션에서](../../web/using/about-web-forms.md)사용할 수 있습니다.

