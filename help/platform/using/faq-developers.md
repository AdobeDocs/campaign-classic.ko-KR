---
title: 일반적인 질문
seo-title: 일반적인 질문
description: Campaign Classic FAQ
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# 개발자 FAQ {#dev-faq}

Adobe Campaign은 개방형 솔루션으로 맞춤화 및 고급 애플리케이션 개발을 지원합니다.

## 캠페인 데이터 모델이란 무엇입니까? {#what-is-the-campaign-data-model}

Adobe Campaign 데이터베이스의 개념 데이터 모델은 내장된 테이블 및 상호 작용 세트로 구성됩니다. 응용 프로그램에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 대한 문법을 따릅니다. Adobe Campaign 스키마에 대한 자세한 내용은 이 섹션을 [참조하십시오](../../configuration/using/about-schema-edition.md).

[캠페인 데이터 모델에 대한 자세한 내용을 보려면 여기를 클릭하십시오](https://helpx.adobe.com/campaign/kb/acc-datamodel.html).

우수 사례는 [이 문서에](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)나열되어 있습니다.

## 캠페인 스키마로 작업하는 방법 {#how-to-work-with-campaign-schemas-}

Adobe Campaign에서 데이터 스키마는 다음 용도로 사용됩니다.

* 응용 프로그램 내의 데이터 객체가 기본 데이터베이스 테이블에 연결되는 방식을 정의합니다.
* Campaign 애플리케이션 내에서 서로 다른 데이터 객체 간의 링크를 정의합니다.
* 각 개체에 포함된 개별 필드를 정의하고 설명합니다.

시작하는 [](../../configuration/using/about-schema-edition.md) 테이블 및 스키마를 참조하여 데이터 스키마를 사용하고, Campaign을 확장 및 사용자 지정하여 요구 사항을 해결하는 방법을 알아보십시오.

## 사용자 지정 수신자 테이블을 사용하는 방법 {#how-to-use-a-custom-recipient-table-}

Campaign에서 비표준 수신자 테이블을 만들고 구현하여 메시지를 보낼 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오.](../../configuration/using/about-custom-recipient-table.md)

## Campaign에서 쿼리를 정의하는 우수 사례는 무엇입니까? {#what-are-the-best-practices-to-define-queries-in-campaign-}

Adobe Campaign 쿼리 편집기는 데이터를 살펴보고 세그먼트를 작성하는 데 필요한 강력한 도구입니다.

Adobe Campaign 쿼리 도구는 소프트웨어의 여러 수준에서 찾을 수 있습니다.대상 모집단, 세그먼트 고객, 추적 로그 추출 및 필터, 필터 작성 등을 만듭니다.

일반 쿼리 편집기를 사용하여 Campaign 데이터베이스를 쿼리할 수 있습니다. **도구 > 일반**&#x200B;쿼리 편집기를 통해 액세스합니다.메뉴. 데이터베이스에 저장된 정보를 추출하고 구성, 그룹, 정렬 등을 할 수 있습니다. 예를 들어 사용자는 지정된 기간 동안 뉴스레터 링크에서 &#39;n&#39;번 이상 클릭한 수신자를 복구할 수 있습니다. 이 툴을 사용하면 필요에 따라 결과를 수집, 정렬 및 표시할 수 있습니다. 이 도구는 모든 Adobe Campaign 쿼리 가능성을 결합합니다. 예를 들어 제한 필터를 만들고 저장할 수 있습니다. 즉, 범용 쿼리 편집기에서 만든 사용자 필터를 타깃팅 워크플로우 등의 쿼리 상자에서 사용할 수 있습니다.

쿼리는 선택한 테이블의 필드를 사용하거나 공식을 사용하여 만들어집니다. 캠페인 데이터베이스에 대한 쿼리를 만드는 기본 원칙은 [이 페이지에](../../platform/using/about-queries-in-campaign.md)설명되어 있습니다.

[캠페인 쿼리 편집기를 검색하려면 여기를](../../workflow/using/query.md) 클릭하십시오.

## 데이터 패키지를 가져오려면 어떻게 해야 합니까? {#how-can-i-import-a-data-package-}

Adobe Campaign을 사용하면 플랫폼 구성 및 데이터를 패키지 시스템을 통해 내보내거나 가져올 수 있습니다. 데이터 패키지를 사용하면 Adobe Campaign 데이터베이스의 엔티티가 XML 형식의 파일을 통해 표시됩니다. 패키지에 포함된 각 엔티티는 모든 데이터로 표현됩니다.

데이터 패키지의 원리는 데이터 구성을 내보내고 다른 Adobe Campaign 시스템에 통합하는 것입니다.

[캠페인 구성을 가져오고 내보내려면 여기를](../../platform/using/working-with-data-packages.md) 클릭하십시오.

## Campaign Classic API 목록은 어디에서 찾을 수 있습니까? {#where-can-i-find-the-list-of-campaign-classic-apis}

전체 설명을 포함한 모든 캠페인 API는 이 [전용 설명서에서](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)사용할 수 있습니다.
