---
product: campaign
title: 콘텐츠 관리자 리소스 및 원칙
description: 콘텐츠 관리자 리소스 및 원칙
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Templates
role: User, Developer, Data Engineer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 4%

---

# 콘텐츠 관리자 리소스 및 원칙{#content-manager-resources-and-principles}


각 콘텐츠에 대한 변형 템플릿을 포함하는 게시 템플릿을 정의해야 합니다.

콘텐츠 블록은 데이터 저장을 위해 XML 문서로 구조화됩니다. 편집 인터페이스는 Adobe Campaign 클라이언트 콘솔 또는 웹 브라우저를 통해 콘텐츠를 입력하는 데 사용됩니다. XML 플로우 또는 데이터베이스에서 집계된 데이터를 캡처하여 컨텐츠를 자동으로 입력할 수도 있습니다.

XML 문서와 XSL 또는 JavaScript 템플릿 스타일시트를 결합하면 다양한 형식(HTML, 텍스트)으로 게시 템플릿의 투영이 자동으로 생성됩니다.

![](assets/d_ncs_content_process.png)

콘텐츠 구성에 필요한 리소스는 다음과 같습니다.

* 데이터 스키마: XML 콘텐츠 구조에 대한 설명입니다. 자세한 내용은 다음을 참조하십시오. [데이터 스키마](data-schemas.md).
* 데이터 입력 양식: 데이터 입력 화면 구성 자세한 내용은 다음을 참조하십시오. [입력 양식](input-forms.md).
* 이미지: 데이터 입력 양식에 사용되는 이미지입니다. 자세한 내용은 다음을 참조하십시오. [이미지 관리](formatting.md#image-management).
* 스타일시트: XSLT 언어를 사용하여 출력 문서의 서식을 지정합니다. 자세한 내용은 다음을 참조하십시오. [서식](formatting.md).
* JavaScript 템플릿: JavaScript 언어를 사용하여 출력 문서의 서식을 지정합니다. 자세한 내용은 다음을 참조하십시오. [게시 템플릿](publication-templates.md).
* JavaScript 코드: 데이터 집계를 위한 JavaScript 코드. 자세한 내용은 다음을 참조하십시오. [집계](publication-templates.md#aggregator).
* 게시 템플릿: 게시 템플릿의 정의. 자세한 내용은 다음을 참조하십시오. [게시 템플릿](publication-templates.md).
* 콘텐츠: 만들고 게시할 콘텐츠 인스턴스. 자세한 내용은 다음을 참조하십시오. [콘텐츠 템플릿 사용](using-a-content-template.md).
