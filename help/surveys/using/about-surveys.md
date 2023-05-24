---
product: campaign
title: 설문 조사 시작
description: Campaign 설문 조사 시작
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# 설문 조사 시작{#about-surveys}



Adobe Campaign에는 웹 애플리케이션을 정의하고 게시하는 그래픽 모듈이 포함되어 있습니다. 엑스트라넷의 편집 양식과 같은 페이지 또는 테이블, 차트, 입력 양식 등이 있는 데이터베이스의 데이터를 포함하는 알림 양식을 만드는 데 사용됩니다. 이 기능을 사용하여 사용자가 정보를 조회하거나 입력할 수 있는 웹 페이지를 디자인하고 게시합니다.

선택 사항 **설문 조사** 추가 기능을 사용하면 새로운 유형의 웹 애플리케이션을 만들어 프로필 정보를 추가하거나 수정하기 위한 양식, 정보 서비스 가입 또는 가입 해지하기, 대회 참가 양식 등과 같은 온라인 설문지를 만들고 관리할 수 있습니다. 응답이 수집되면 데이터베이스나 로컬 변수에 저장됩니다. 데이터 모델은 질문에 대한 답변을 통해 동적으로 확장할 수 있습니다. 결과를 실시간으로 보고, 응답을 필터링하고, 전용 차트를 사용하여 분석할 수 있습니다.

이 장에서는 생성 및 관리 방법에 대해 자세히 설명합니다 **설문 조사**, 필드 및 페이지 관리, 저장 모드 및 레코드.

에서 첫 번째 설문 조사를 만드는 방법 알아보기 [이 페이지](getting-started-with-surveys.md).

>[!NOTE]
>
>* 표준 웹 양식을 만드는 자세한 단계는 [이 문서](../../web/using/about-web-forms.md).
>
>* 웹 애플리케이션 관리에 대한 자세한 내용은 [이 문서](../../web/using/about-web-applications.md). 자세한 내용은 이 장을 참조하십시오.


## 기능 범위 {#campaign-surveys-scope}

Adobe Campaign에서 다음을 사용합니다 [웹 애플리케이션](../../web/using/about-web-forms.md) 끝:

* 여러 페이지로 구성된 양식 만들기,
* 통합 번역 툴을 사용하여 다국어 양식을 관리하고,
* 그래픽 인터페이스, 다중 열 페이지 레이아웃 관리,
* 개인화 추가 및 필드 위치 정의,
* 답변에 따른 설문 조사 필드의 상태 표시,
* 조건 페이지 표시,
* 예상되는 데이터 유형(번호, 이메일 주소, 날짜 등)에 따라 승인 전에 정보를 확인합니다. 및 필수 필드,
* 이메일 초대/알림 보내기,
* 오류 및 종료 페이지 개인화,
* 양식에 이미지, 비디오, 하이퍼텍스트 링크, captcha 등을 추가합니다.

선택 사항인 설문 조사 만들기 모듈은 사용자 친화적인 UI와 다음 추가 기능을 제공합니다.

* 데이터베이스의 동적 확장: 초기 데이터 모델에 속하지 않는 답변 만들기. [자세히 알아보기](../../surveys/using/managing-answers.md#storing-collected-answers)
* 점수 관리. [자세히 알아보기](../../surveys/using/managing-answers.md#score-management)
* 질문을 임의로 표시합니다. [자세히 알아보기](../../surveys/using/building-a-survey.md#adding-questions)
* 답변을 실시간으로 추적합니다. [자세히 알아보기](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking)
* 전용 보고서를 생성하고 있습니다. [자세히 알아보기](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys)


## 구현 단계 {#surveys-implementation-steps}

다음 단계를 적용하여 설문 조사를 만들고 전달하고 결과를 처리합니다.

1. 설문 조사 페이지 및 해당 컨텐츠(입력 필드, 드롭다운 목록, 질문 등)를 만듭니다.
1. 답변을 저장하는 방법을 정의합니다. 데이터베이스에 이미 데이터가 있는 양식을 미리 로드하기 위해 데이터 미리 로드 단계를 삽입할 수 있습니다. 테스트 상자를 추가할 수도 있습니다.
1. 게시한 다음 설문조사를 수신자에게 전달합니다(예: 게재 또는 웹 사이트에 링크 포함).
1. 응답을 모니터링하고 보고서를 봅니다.

이러한 단계의 구성 및 시퀀싱에 대한 자세한 내용은 [이 문서](../../web/using/about-web-forms.md). 설문 조사에 대한 구성만 이 장에 자세히 설명되어 있습니다.

>[!CAUTION]
>
>개인정보 보호를 위해 모든 외부 리소스에 HTTPS를 사용하는 것이 좋습니다.

## 설정 {#settings}

기본적으로 설문 조사는 **[!UICONTROL Resources > Online > Web Applications]** Adobe Campaign 트리의 노드입니다.

설정은 다음 폴더에 저장됩니다.

* **[!UICONTROL Administration > Configuration > Form rendering]**: 웹 양식 표시(응용 프로그램 및 설문 조사)를 위한 렌더링 템플릿이 들어 있습니다.
* **[!UICONTROL Resources > Templates > Web application templates]**: 양식 템플릿을 포함합니다. 양식을 만들려면 템플릿으로 시작해야 합니다.

>[!NOTE]
>
>설정 세부 사항은에서 사용할 수 있습니다. [이 문서](../../web/using/about-web-forms.md).
