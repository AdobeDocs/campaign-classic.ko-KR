---
title: About web applications
seo-title: About web applications
description: About web applications
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
source-git-commit: 1667dd0c8a38db0e554c59062cbcc5b6c6d992bb
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---


# 웹 응용 프로그램 정보{#about-web-applications}

Adobe Campaign을 사용하면 데이터베이스의 데이터와 연결된 사용자의 권한에 맞는 컨텐츠가 포함된 다이내믹하고 인터랙티브한 웹 애플리케이션을 제작하여 게시할 수 있습니다.

엑스트라넷에서 편집 양식과 같은 페이지를 만들거나 테이블, 차트, 입력 양식 등이 포함된 데이터베이스의 데이터를 포함하는 알림 양식을 만들 수 있습니다. 이 기능을 사용하면 사용자가 정보를 찾거나 입력할 수 있는 웹 페이지를 디자인하고 게시할 수 있습니다.

This can be a subscription form containing data that has been preloaded with information contained in the Adobe Campaign database, as shown below:

![](assets/webapp_form_sample.png)

이 장에서는 웹 응용 프로그램을 관리하는 방법에 대한 개요를 제공합니다.

>[!NOTE]
>
>웹 응용 프로그램에 대한 보안 [을 최적화하는 방법에 대한 자세한 내용은 보안 및 개인 정보 확인](https://helpx.adobe.com/campaign/kb/acc-security.html) 목록을 참조하십시오.

>[!CAUTION]
>
>개인 정보상의 이유로 모든 외부 리소스에 대해 HTTPS를 사용하는 것이 좋습니다.

## 웹 애플리케이션 범위 {#web-application-scope}

Adobe Campaign의 웹 애플리케이션은 다음 기능에 액세스할 수 있습니다.

* 여러 페이지 양식 작성 For more on this, refer to this [page](../../web/using/about-web-forms.md).
* 통합 번역 툴을 통한 다국어 설문 조사 관리 For more on this, refer to this [page](../../web/using/translating-a-web-application.md).
* 그래픽 페이지 관리 인터페이스, 여러 열로 구성된 페이지 레이아웃. For more on this, refer to this [page](../../web/using/designing-a-web-application.md).
* 개인화 및 필드 위치 렌더링 For more on this, refer to this [page](../../web/using/editing-content.md#adding-personalization-content).
* 응답에 따라 설문 조사 필드 조건부 표시 For more on this, refer to this [page](../../web/using/form-rendering.md#defining-fields-conditional-display).
* 질문이 무작위로 표시됩니다. For more on this, refer to this [page](../../web/using/building-a-survey.md#adding-questions).
* 조건부 페이지 표시. For more on this, refer to this [page](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).
* 예상 데이터 유형(번호, 이메일 주소, 날짜 등)에 따라 검증하기 전에 정보 확인 및 필수 필드입니다. For more on this, refer to this [page](../../web/using/form-rendering.md#defining-control-settings).
* 이메일 초대 또는 알림 For more on this, refer to this [page](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).
* 오류 및 종료 메시지의 개인화 For more on this, refer to this [page](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page).
* 이미지, 비디오, 하이퍼텍스트 링크, captcha 등의 사용 For more on this, refer to this [page](../../web/using/editing-content.md).
* 실시간으로 응답 모니터링 For more on this, refer to this [page](../../web/using/publish--track-and-use-collected-data.md#response-tracking).

선택적 **설문 조사** 작성 모듈에서는 다음과 같은 추가 기능을 제공합니다.

* 데이터베이스의 동적 확장: 초기 데이터 템플릿에 포함되지 않은 응답 만들기 For more on this, refer to this [page](../../web/using/managing-answers.md#storing-collected-answers).
* 전용 보고서 생성 For more on this, refer to this [page](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

웹 애플리케이션과 비교하여 설문 조사에는 적은 수의 편집 컨트롤이 있는 간소화된 그래픽 인터페이스가 있습니다.

>[!NOTE]
>
>설문 조사는 [이 섹션에 자세히 설명되어 있습니다](../../web/using/about-surveys.md).
>
>Adobe Campaign에서 웹 양식의 전반적인 기능은 [이 섹션에 자세히 설명되어 있습니다](../../web/using/about-web-forms.md).

## 웹 애플리케이션 구현 {#web-application-implementation}

웹 애플리케이션을 만들고 게시하려면 다음을 수행해야 합니다.

1. 컨텐츠(필드, 목록, 표, 그래프 등)를 만듭니다.

   양식에 사용할 수 있는 필드에 대한 세부 정보를 제공하는 섹션을 볼 수도 있습니다. 이러한 필드는 모두 웹 응용 프로그램에서도 사용할 수 있습니다. 이 정보는 [이 페이지에서 확인할 수 있습니다](../../web/using/adding-fields-to-a-web-form.md).

1. 필요에 따라 사전 로드, 테스트 및 저장 단계를 추가하고 액세스 제어 시스템(주로 엑스트라넷 발행물의 프레임워크 내)을 구성할 수 있습니다.
1. 외부 또는 Adobe Campaign에서 사용할 수 있도록 웹 애플리케이션을 게시합니다.

## 웹 애플리케이션 초기 구성 {#web-application-initial-configuration}

웹 응용 프로그램은 탭과 **[!UICONTROL Web Applications]** 링크를 통해 **[!UICONTROL Campaigns]** 만들어집니다 **[!UICONTROL Profiles and targets]** .

웹 애플리케이션은 Adobe Campaign 트리의 **[!UICONTROL Resources > Online > Web Applications]** 노드에 저장됩니다. 구성은 다음 폴더로 분류됩니다.

* **[!UICONTROL Administration > Configuration > Form renderings]**: 에는 웹 양식 프레젠테이션(응용 프로그램 및 설문 조사)용 렌더링 템플릿이 포함되어 있습니다. 템플릿을 사용하면 양식을 생성할 수 있습니다. 또한 CSS 스타일 시트도 사용합니다. 이 스타일 시트는 템플릿 수준에서 오버로드될 수 있습니다. For more on this, refer to [this page](../../web/using/form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: 에는 양식 템플릿이 포함되어 있습니다. 양식이나 웹 응용 프로그램을 만들려면 템플릿에서 시작해야 합니다.

## 웹 애플리케이션 템플릿 {#web-application-templates}

기본적으로 Adobe Campaign은 사용 가능한 웹 애플리케이션당 하나의 템플릿을 제공합니다.

>[!NOTE]
>
>기존 웹 응용 프로그램을 템플릿으로 변환할 수 있습니다. 이렇게 하려면 양식을 선택하고 마우스 오른쪽 단추를 클릭합니다. 선택합니다 **[!UICONTROL Actions > Save as template...]**.

Adobe Campaign 트리의 노드를 통해 새 템플릿 **[!UICONTROL Resources > Templates > Web Application templates]** 을 만들 수 있습니다.

만들기 마법사를 사용하면 아래에서 보듯이 활성화할 옵션을 선택할 수 있습니다.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>사용 가능한 애플리케이션은 옵션 및 모듈에 따라 다릅니다. 사용권 계약을 확인하십시오.

