---
solution: Campaign Classic
product: campaign
title: 콘텐츠 관리자 리소스 및 원칙
description: 콘텐츠 관리자 리소스 및 원칙
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 6%

---


# 콘텐츠 관리자 리소스 및 원칙{#content-manager-resources-and-principles}

각 컨텐츠에 대한 변형 템플릿을 포함하는 게시 템플릿을 정의해야 합니다.

내용 블록은 데이터 저장을 위해 XML 문서로 구성됩니다. 편집 인터페이스는 Adobe Campaign 클라이언트 콘솔 또는 웹 브라우저를 통해 컨텐츠를 입력하는 데 사용됩니다. 또한 XML 흐름이나 데이터베이스에 집계된 데이터를 캡처하여 컨텐츠를 자동으로 입력할 수도 있습니다.

XML 문서와 XSL 또는 JavaScript 템플릿 스타일시트를 결합하면 출판 템플릿의 투영이 다양한 형식(HTML, 텍스트)으로 자동으로 생성됩니다.

![](assets/d_ncs_content_process.png)

콘텐트 구성에 필요한 리소스는 다음과 같습니다.

* 데이터 스키마:XML 내용 구조에 대한 설명입니다. 자세한 내용은 [데이터 스키마](../../delivery/using/data-schemas.md)를 참조하십시오.
* 데이터 입력 양식:데이터 입력 화면 구성 자세한 내용은 [입력 양식](../../delivery/using/input-forms.md)을 참조하십시오.
* 이미지:데이터 입력 양식에 사용된 이미지. 자세한 내용은 [이미지 관리](../../delivery/using/formatting.md#image-management)를 참조하십시오.
* 스타일 시트:XSLT 언어를 사용하여 출력 문서의 서식을 지정합니다. 자세한 내용은 [서식](../../delivery/using/formatting.md)을 참조하십시오.
* JavaScript 템플릿:JavaScript 언어를 사용한 출력 문서의 형식 지정. 자세한 내용은 [발행물 템플릿](../../delivery/using/publication-templates.md)을 참조하십시오.
* JavaScript 코드:데이터 집계를 위한 JavaScript 코드. 자세한 내용은 [수집기](../../delivery/using/publication-templates.md#aggregator)를 참조하십시오.
* 발행물 템플릿:출판 템플릿의 정의입니다. 자세한 내용은 [발행물 템플릿](../../delivery/using/publication-templates.md)을 참조하십시오.
* 컨텐츠:만들고 게시할 컨텐츠 인스턴스입니다. 자세한 내용은 [콘텐츠 템플릿 사용](../../delivery/using/using-a-content-template.md)을 참조하십시오.
