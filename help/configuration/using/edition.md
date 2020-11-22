---
solution: Campaign Classic
product: campaign
title: 에디션
description: 에디션
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 2%

---


# 에디션{#edition}

탐색 계층 구성 문서를 만들고 구성하는 화면은 노드를 통해 액세스할 수 **[!UICONTROL Administration > Configuration > Navigation hierarchies]** 있습니다.

![](assets/d_ncs_integration_navigation_arbo.png)

탐색 계층 구성은 여러 XML 문서로 나누어집니다. 스키마 확장과 유사한 원리로 작동합니다.모든 문서가 병합되어 전체 구성이 포함된 단일 문서를 생성합니다. 이 문서는 편집할 수 없으며 &quot;미리 보기&quot; 탭을 통해 표시됩니다.

편집 필드는 XML 문서의 내용을 제공합니다.

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>&quot;이름&quot; 편집 컨트롤을 사용하면 이름과 네임스페이스로 구성된 문서 키를 입력할 수 있습니다. 요소의 &quot;name&quot; 및 &quot;namespace&quot; 속성은 **`<navtree>`** 스키마의 XML 편집 필드에서 자동으로 업데이트됩니다.

미리 보기는 전체 구성이 포함된 병합된 문서를 자동으로 생성합니다.

![](assets/d_ncs_integration_navigation_preview.png)

