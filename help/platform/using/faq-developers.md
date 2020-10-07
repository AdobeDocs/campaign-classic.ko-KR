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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 100%

---


# 개발자 FAQ {#dev-faq}

개방형 솔루션인 Adobe Campaign은 사용자 지정 및 고급 애플리케이션 개발을 위한 준비가 되어 있습니다.

## Campaign 데이터 모델은 무엇입니까? {#what-is-the-campaign-data-model}

Adobe Campaign 데이터베이스의 개념적 데이터 모델은 내장된 테이블과 상호 작용으로 구성됩니다. 애플리케이션에 포함된 데이터의 물리적 및 논리적 구조는 XML에 설명되어 있습니다. 스키마라고 하는 Adobe Campaign에 특정된 문법을 따릅니다. Adobe Campaign 스키마에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../configuration/using/about-schema-edition.md).

[Campaign 데이터 모델에 대한 자세한 내용을 보려면 여기를 클릭하십시오](https://helpx.adobe.com/kr/campaign/kb/acc-datamodel.html).

모범 사례는 [이 문서](https://helpx.adobe.com/kr/campaign/kb/acc-data-model-best-practices.html)에 나열되어 있습니다.

## Campaign 스키마로 작업하는 방법 {#how-to-work-with-campaign-schemas-}

Adobe Campaign에서 데이터 스키마는 다음 용도로 사용됩니다.

* 애플리케이션 내의 데이터 개체가 기본 데이터베이스 테이블에 연결되어 있는 방식을 정의합니다.
* Campaign 애플리케이션 내에서 서로 다른 데이터 개체 간의 링크를 정의합니다.
* 각 개체에 포함된 개별 필드를 정의하고 설명합니다.

데이터 스키마로 작업하고, Campaign을 확장 및 사용자 지정하여 필요에 맞게 조정하는 방법을 이해하려면 [테이블 및 스키마 시작하기](../../configuration/using/about-schema-edition.md)를 참조하십시오.

## 사용자 지정 수신자 테이블을 사용하는 방법 {#how-to-use-a-custom-recipient-table-}

Campaign에서 비표준 수신자 테이블을 만들고 구현하여 메시지를 보낼 수 있습니다.

[자세한 내용을 보려면 여기를 클릭하십시오.](../../configuration/using/about-custom-recipient-table.md)

## Campaign에서 쿼리를 정의하는 모범 사례는 무엇입니까? {#what-are-the-best-practices-to-define-queries-in-campaign-}

Adobe Campaign 쿼리 편집기는 데이터를 탐색하고 세그먼트를 빌드할 수 있는 강력한 도구입니다.

Adobe Campaign 쿼리 도구는 대상 모집단, 고객 세그먼트, 추적 로그 추출 및 필터, 필터 빌드 등을 만들기 위해 소프트웨어의 여러 수준에서 찾을 수 있습니다. 

일반 쿼리 편집기를 사용하여 Campaign 데이터베이스를 쿼리할 수 있습니다. **도구 > 일반 쿼리 편집기...** 메뉴를 통해 액세스합니다. 데이터베이스에 저장된 정보를 추출하고 구성, 그룹, 정렬 등을 할 수 있습니다. 예를 들어 사용자는 지정된 기간 동안 뉴스레터 링크에 &#39;n&#39;번 이상 클릭한 수신자를 복구할 수 있습니다. 이 도구를 사용하면 필요에 따라 결과를 수집, 정렬 및 표시할 수 있습니다. 이 도구는 모든 Adobe Campaign 쿼리 가능성을 결합합니다. 예를 들어 제한 필터를 만들고 저장할 수 있습니다. 즉, 일반 쿼리 편집기에서 만든 사용자 필터를 타겟팅 워크플로우 등의 쿼리 상자에서 사용할 수 있습니다.

쿼리는 선택한 테이블의 필드를 사용하거나 공식을 사용하여 만들어집니다. Campaign 데이터베이스에서 쿼리를 만드는 기본 원칙은 [이 페이지](../../platform/using/about-queries-in-campaign.md)에 설명되어 있습니다.

Campaign 쿼리 편집기를 검색하려면 [여기를 클릭](../../workflow/using/query.md)하십시오.

## 데이터 패키지를 가져오려면 어떻게 해야 합니까? {#how-can-i-import-a-data-package-}

Adobe Campaign을 사용하면 패키지 시스템을 통해 플랫폼 구성 및 데이터를 내보내거나 가져올 수 있습니다. 데이터 패키지를 사용하면 Adobe Campaign 데이터베이스의 엔터티가 XML 형식의 파일을 통해 표시될 수 있습니다. 패키지에 포함된 각 엔티티는 모든 데이터로 표시됩니다.

데이터 패키지의 원칙은 데이터 구성을 내보내고 다른 Adobe Campaign 시스템에 통합하는 것입니다.

Campaign 구성을 가져오고 내보내는 데이터 패키지를 사용하여 작업하는 방법을 배우려면 [여기를 클릭](../../platform/using/working-with-data-packages.md)하십시오.

## Campaign Classic API 목록은 어디에서 찾을 수 있습니까? {#where-can-i-find-the-list-of-campaign-classic-apis}

전체 설명을 포함한 모든 캠페인 API는 이 [전용 설명서](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)에서 사용할 수 있습니다.
