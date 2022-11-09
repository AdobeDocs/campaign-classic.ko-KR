---
product: campaign
title: 설문 조사 시작
description: Campaign 설문 조사 시작
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 1f80c9967f4859f26dd2890d657f95ada6cf2087
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# 설문 조사 시작{#about-surveys}

![](../../assets/common.svg)

Adobe Campaign에는 웹 애플리케이션을 정의하고 게시할 수 있는 그래픽 모듈이 포함되어 있습니다. 엑스트라넷의 편집 양식 등의 페이지를 만들거나 테이블, 차트, 입력 양식 등이 있는 데이터베이스의 데이터를 포함하는 알림 양식을 만드는 데 사용됩니다. 이 기능을 사용하여 사용자가 정보를 조회하거나 입력할 수 있는 웹 페이지를 디자인하고 게시할 수 있습니다.

선택 사항입니다 **설문 조사** 추가 기능을 사용하면 프로필 정보를 추가 또는 수정할 양식, 정보 서비스 구독 또는 구독 취소 또는 대회 입력 양식 등의 온라인 설문 조사를 만들고 관리할 수 있는 새로운 유형의 웹 애플리케이션을 만들 수 있습니다. 응답이 수집되면 데이터베이스 또는 로컬 변수에 저장됩니다. 데이터 모델은 질문에 주어진 답변을 통해 동적으로 확장될 수 있습니다. 실시간으로 결과를 보고, 응답을 필터링하고, 전용 차트를 사용하여 분석할 수 있습니다.

이 장에서는 생성 및 관리 방법에 대해 자세히 설명합니다 **설문 조사**, 필드 및 페이지 관리, 스토리지 모드 및 레코드

에서 첫 번째 설문 조사를 만드는 방법을 알아봅니다 [이 페이지](getting-started-with-surveys.md).

>[!NOTE]
>
>* 표준 웹 양식을 만드는 자세한 단계는 [이 문서](../../web/using/about-web-forms.md).
>
>* 웹 애플리케이션 관리는 [이 문서](../../web/using/about-web-applications.md). 자세한 내용은 이 장을 참조하십시오.


## 기능 범위 {#campaign-surveys-scope}

Adobe Campaign에서 [웹 애플리케이션](../../web/using/about-web-forms.md) 변환:

* 여러 페이지 양식 만들기,
* 통합 번역 도구를 통해 다국어 양식 관리
* 그래픽 인터페이스, 다중 열 페이지 레이아웃 관리,
* 개인화 추가 및 필드 위치 정의,
* 응답에 따라 설문 조사 필드의 조건 표시,
* 조건 페이지 표시,
* 필요한 데이터 유형(숫자, 이메일 주소, 날짜 등)에 따라 승인 전에 정보를 확인하십시오. 및 필수 필드
* 이메일 초대/알림 보내기,
* 오류 및 최종 페이지 개인화,
* 양식에 이미지, 비디오, 하이퍼텍스트 링크, 캡차 등을 추가합니다

선택 사항인 설문 조사 만들기 모듈은 사용자에게 친숙한 UI와 다음과 같은 추가 기능을 제공합니다.

* 데이터베이스의 동적 확장: 초기 데이터 모델에 속하지 않는 답변 작성. [자세히 알아보기](../../surveys/using/managing-answers.md#storing-collected-answers)
* 점수 관리. [자세히 알아보기](../../surveys/using/managing-answers.md#score-management)
* 질문이 임의로 표시됩니다. [자세히 알아보기](../../surveys/using/building-a-survey.md#adding-questions)
* 실시간 답변 추적. [자세히 알아보기](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)
* 전용 보고서 생성. [자세히 알아보기](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)


## 구현 단계 {#surveys-implementation-steps}

설문 조사를 만들고 전달하고 결과를 처리하려면 다음 단계를 적용합니다.

1. 설문 조사의 페이지와 해당 컨텐츠(입력 필드, 드롭다운 목록, 질문 등)를 만듭니다.
1. 답변을 저장하는 방법을 정의합니다. 데이터베이스에 이미 있는 데이터로 양식을 미리 로드하기 위해 데이터 사전 로드 단계를 삽입할 수 있습니다. 테스트 상자를 추가할 수도 있습니다.
1. 설문 조사를 게시한 다음 수신자에게 전달합니다(예: 게재 또는 웹 사이트에 링크 포함).
1. 응답 모니터링 및 보고서 보기

이러한 단계 구성 및 시퀀싱에 대한 자세한 내용은 [이 문서](../../web/using/about-web-forms.md). 이 장에서는 설문 조사 관련 구성만 자세히 설명합니다.

>[!CAUTION]
>
>개인 정보용으로 모든 외부 리소스에 HTTPS를 사용하는 것이 좋습니다.

## 설정 {#settings}

기본적으로 설문 조사는 **[!UICONTROL Resources > Online > Web Applications]** 노드 아래에 나열된 상태로 남아 있습니다.

설정은 다음 폴더에 저장됩니다.

* **[!UICONTROL Administration > Configuration > Form rendering]**: 웹 양식 프레젠테이션의 렌더링 템플릿이 들어 있습니다(응용 프로그램 및 설문 조사).
* **[!UICONTROL Resources > Templates > Web application templates]**: 에는 양식 템플릿이 들어 있습니다. 양식을 만들려면 템플릿으로 시작해야 합니다.

>[!NOTE]
>
>설정 세부 사항은 [이 문서](../../web/using/about-web-forms.md).
