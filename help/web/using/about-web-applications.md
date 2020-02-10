---
title: 웹 애플리케이션 정보
seo-title: 웹 애플리케이션 정보
description: 웹 애플리케이션 정보
seo-description: null
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 웹 애플리케이션 정보{#about-web-applications}

Adobe Campaign을 사용하면 데이터베이스의 데이터와 연결된 사용자의 권한에 따라 조정된 컨텐츠가 포함된 다이내믹하고 인터랙티브한 웹 애플리케이션을 제작하고 게시할 수 있습니다. 엑스트라넷에서 편집 양식과 같은 페이지를 만들거나 테이블, 차트, 입력 양식 등이 있는 데이터베이스의 데이터를 포함하는 알림 양식을 만들 수 있습니다. 이 기능을 사용하면 사용자가 정보를 조회하거나 입력할 수 있는 웹 페이지를 디자인하고 게시할 수 있습니다.

이것은 아래와 같이 Adobe Campaign 데이터베이스에 포함된 정보와 함께 미리 로드한 데이터가 포함된 구독 양식일 수 있습니다.

![](assets/webapp_form_sample.png)

이 장에서는 웹 응용 프로그램을 관리하는 방법에 대한 개요를 제공합니다.

>[!CAUTION]
>
>개인 정보상의 이유로 모든 외부 리소스에 대해 HTTPS를 사용하는 것이 좋습니다.

## 웹 애플리케이션 범위 {#web-application-scope}

Adobe Campaign의 웹 애플리케이션은 다음 기능을 이용할 수 있습니다.

* 여러 페이지 양식 작성,
* 통합 번역 툴을 통한 다국어 설문 조사 관리,
* 그래픽 페이지 관리 인터페이스, 여러 열로 구성된 페이지 레이아웃,
* 개인화 및 필드 위치 렌더링,
* 응답에 따라 설문 조사 필드 조건부 표시,
* 무작위 질문 표시,
* 조건부 페이지 표시,
* 예상 데이터 유형(번호, 이메일 주소, 날짜 등)에 따라 유효성 검사 전 정보 확인 그리고 필수 필드
* 이메일 초대장 또는 알림,
* 오류 및 종료 메시지의 개인화,
* 이미지, 비디오, 하이퍼텍스트 링크, captcha 등의 사용
* 실시간으로 응답 모니터링

선택적 설문 **조사** 작성 모듈에서는 다음과 같은 추가 기능을 제공합니다.

* 데이터베이스의 동적 확장:초기 데이터 템플릿에 포함되지 않은 응답 작성,
* 전용 보고서 생성.

웹 애플리케이션과 비교하여 설문 조사는 적은 수의 편집 컨트롤과 함께 간소화된 그래픽 인터페이스를 제공합니다.

>[!NOTE]
>
>설문 조사는 [이 섹션에](../../web/using/about-surveys.md)자세히 설명되어 있습니다.
>
>Adobe Campaign의 웹 양식의 전체 기능은 [이 섹션에](../../web/using/about-web-forms.md)자세히 설명되어 있습니다.

## 웹 애플리케이션 구현 {#web-application-implementation}

웹 애플리케이션을 만들고 게시하려면 다음을 수행해야 합니다.

1. 컨텐츠(필드, 목록, 표, 그래프 등)를 만듭니다.

   양식에 사용할 수 있는 필드를 자세히 설명하는 섹션을 볼 수도 있습니다.웹 응용 프로그램에도 이 모든 필드를 사용할 수 있습니다. 이 정보는 [이 페이지에서](../../web/using/adding-fields-to-a-web-form.md)사용할 수 있습니다.

1. 필요에 따라 사전 로드, 테스트 및 저장 단계를 추가하고 액세스 제어 시스템(주로 엑스트라넷 발행물의 프레임워크 내)을 구성할 수 있습니다.
1. 엑스트라넷 또는 Adobe Campaign에서 사용할 수 있도록 웹 애플리케이션을 게시합니다.

## 웹 애플리케이션 초기 구성 {#web-application-initial-configuration}

웹 응용 프로그램은 **[!UICONTROL Web Applications]** 및 **[!UICONTROL Campaigns]** **[!UICONTROL Profiles and targets]** 탭의 링크를 통해 만들어집니다.

웹 애플리케이션은 Adobe Campaign 트리의 **[!UICONTROL Resources > Online > Web Applications]** 노드에 저장됩니다. 구성은 다음 폴더로 분류됩니다.

* **[!UICONTROL Administration > Configuration > Form renderings]**:에는 웹 양식 프레젠테이션(응용 프로그램 및 설문 조사)용 렌더링 템플릿이 포함되어 있습니다. 템플릿을 사용하면 양식을 생성할 수 있습니다. 또한 CSS 스타일 시트도 사용합니다. 이 스타일 시트는 템플릿 수준에서 오버로드될 수 있습니다. For more on this, refer to [this page](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**:에는 양식 템플릿이 포함되어 있습니다. 양식이나 웹 응용 프로그램을 만들려면 템플릿에서 시작해야 합니다.

## 웹 애플리케이션 템플릿 {#web-application-templates}

기본적으로 Adobe Campaign은 사용 가능한 웹 애플리케이션당 하나의 템플릿을 제공합니다.

>[!NOTE]
>
>기존 웹 응용 프로그램을 템플릿으로 변환할 수 있습니다. 이렇게 하려면 양식을 선택하고 마우스 오른쪽 단추를 클릭합니다. 을 **[!UICONTROL Actions > Save as template...]**&#x200B;선택합니다.

Adobe Campaign 트리의 **[!UICONTROL Resources > Templates > Web Application templates]** 노드를 통해 새 템플릿을 만들 수 있습니다.

만들기 마법사를 사용하면 아래에서 보듯이 활성화할 옵션을 선택할 수 있습니다.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>사용 가능한 애플리케이션은 옵션 및 모듈에 따라 다릅니다. 사용권 계약을 확인하십시오.

