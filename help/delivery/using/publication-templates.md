---
product: campaign
title: 게시 템플릿
description: 게시 템플릿
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Templates
role: User
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 1%

---

# 게시 템플릿{#publication-templates}

## 게시 템플릿 기본 정보 {#about-publication-templates}

게시 템플릿은 게시 프로세스에 사용된 리소스(예:

* 데이터 스키마,
* 입력 양식,
* 각 출력 문서에 대한 변환 템플릿입니다.

## 게시 템플릿 ID {#identification-of-a-publication-template}

게시 템플릿은 이름과 네임스페이스로 식별됩니다.

스타일시트의 식별 키는 네임스페이스와 콜론으로 구분된 이름으로 구성된 문자열입니다. 예를 들면 다음과 같습니다. **cus:newsletter**.

>[!NOTE]
>
>실제로 스키마, 양식 및 게시 템플릿에 동일한 키를 사용하는 것이 좋습니다.

## 템플릿 만들기 및 구성 {#creating-and-configuring-the-template}

게시 템플릿은 기본적으로 **[!UICONTROL Administration > Configuration > Publication templates]** 노드. 새 템플릿을 만들려면 **[!UICONTROL New]** 템플릿 목록 위에 있는 단추입니다.

게시 템플릿을 구성하려면 템플릿의 이름(즉, 이름과 네임스페이스로 구성된 식별 키), 해당 레이블, 데이터 스키마 및 연결된 입력 양식을 채웁니다.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>이 게시 템플릿을 기반으로 콘텐츠를 만들 때마다 레이블이 표시됩니다.

다음 **컨텐츠 생성의 유효성을 검사하려면 상태 확인** 옵션은 콘텐츠 인스턴스의 &quot;확인됨&quot; 상태를 확인하여 파일 생성을 승인하도록 합니다. 자세한 내용은 다음을 참조하십시오. [발행](#publication).

각 출력 문서에 대해 변형 템플릿을 추가해야 합니다. 필요한 수만큼 변환 템플릿을 생성할 수 있습니다.

다음 **[!UICONTROL Name of template]** 필드는 출력 시 렌더링 유형을 설명하는 자유 레이블입니다. 각 변형 템플릿의 경우 탭에서 게시 설정을 사용할 수 있습니다.

### 렌더링 {#rendering}

다음 **[!UICONTROL Rendering]** 탭에서 다음을 선택합니다.

* 출력 문서 투영에 사용되는 렌더링 유형(XSL 스타일시트 또는 JavaScript 템플릿)
* 출력 문서의 형식(HTML, 텍스트, XML 또는 RTF)
* 구성 데이터가 포함된 템플릿(예: 사용할 스타일시트 또는 JavaScript 템플릿).

### 게시 {#publication}

게시 작업에는 선택한 유형이 다음과 같은 경우 출력 문서가 파일 형태로 생성됩니다. **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

다음 게시 옵션을 사용할 수 있습니다.

* 출력 파일 인코딩 문자 집합은 **[!UICONTROL Encoding]** 필드. 기본적으로 라틴 1(1252) 문자 세트가 사용됩니다.
* 다음 **[!UICONTROL Multi-file generation]** 옵션은 특수 문서 게시 모드를 활성화합니다. 이 옵션은 출력 문서의 각 페이지 시작 부분에서 분할 태그를 채우는 것으로 구성됩니다. 콘텐츠를 생성하면 채워진 각 분할 태그에 대한 파일이 생성됩니다. 이 모드는 콘텐츠 블록에서 미니 사이트를 생성하는 데 사용됩니다. 자세한 내용은 다음을 참조하십시오. [다중 파일 생성](#multi-file-generation).
* 다음 **[!UICONTROL Location]** 필드에는 출력 파일의 이름이 포함됩니다. 자동 파일 이름을 생성하기 위해 이름을 변수로 구성할 수 있습니다.

  변수는 다음 형식으로 채워집니다. **`$(<xpath>)`**, 여기서 **`<xpath>`** 은 게시 템플릿 데이터 스키마의 필드 경로입니다.

  파일 이름은 날짜 유형 필드로 구성할 수 있습니다. 이 필드의 서식을 올바르게 지정하려면 **$date-format** 필드의 경로와 출력 형식을 매개 변수로 사용하는 함수.

  기본적으로 파일 이름의 구성 형식은 &quot;@name&quot; 및 &quot;@date&quot; 필드의 변수를 사용합니다.

  ```
  ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
  ```

  생성된 파일 이름은 ct_news12_20110901.htm과 같이 표시됩니다.

  >[!NOTE]
  >
  >콘텐츠 생성에 대한 자세한 내용은 을 참조하십시오. [콘텐츠 인스턴스 만들기](using-a-content-template.md#creating-a-content-instance).

### 게재 {#delivery}

이 탭에서는 콘텐츠에서 직접 게재를 시작하기 위한 시나리오를 선택할 수 있습니다. 이메일의 콘텐츠는 출력 형식(HTML 또는 텍스트)에 따라 자동으로 채워집니다.

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>콘텐츠를 기반으로 한 게재 만들기의 예는 를 참조하십시오. [콘텐츠 인스턴스 게재](using-a-content-template.md#delivering-a-content-instance).

### 집계 {#aggregator}

스크립트나 쿼리 목록에서 데이터를 집계하면 XML 문서를 컨텐츠 데이터로 보강할 수 있습니다. 목표는 링크에서 참조하는 특정 정보를 보완하거나 데이터베이스에서 요소를 추가하는 것입니다.

### 다중 파일 생성 {#multi-file-generation}

여러 파일 생성을 활성화하려면 **[!UICONTROL Multi-file generation]** 게시 모델의 옵션입니다. 이 옵션을 사용하면 출력 문서의 각 페이지 시작 부분에 대해 스타일시트에 분할 태그를 지정할 수 있습니다. 컨텐츠를 생성하면 발생하는 각 분할 태그에 대한 파일이 생성됩니다.

스타일시트에 통합할 분할 태그는 다음과 같습니다.

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** 위치 **`<name_of_file>`** 는 생성할 페이지의 파일 이름입니다.

**예:** cus:book 스키마를 사용하여 여러 파일을 생성합니다.

원칙은 챕터를 나열하는 메인 페이지를 생성하여 외부 페이지에 챕터의 세부 정보를 표시할 수 있습니다.

![](assets/d_ncs_content_chunk.png)

해당 스타일시트(&quot;cus:book.xsl&quot;)는 다음과 같습니다.

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

챕터의 세부 정보를 생성하려면 두 번째 스타일시트(&quot;cus:chapter.xsl&quot;)가 필요합니다.

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

분할 태그는 생성할 파일에 포함될 페이지의 시작 부분에서 채워집니다.

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

파일 이름은 **$(path)** 게시 경로 및 을 포함하는 변수 **`<xsl:value-of select="@id" />`**: 입력 문서에 있는 챕터의 식별자와 일치합니다.

발행 모델은 두 개의 스타일 시트 &quot;cus:book.xsl&quot;과 &quot;cus:chapter.xsl&quot;로 채워야 합니다.

다음 **[!UICONTROL Multi-file generation]** 옵션은 챕터 변환 모델에서 활성 상태여야 합니다.

![](assets/d_ncs_content_chunk2.png)

다음 **[!UICONTROL Location]** 필드는 여러 파일을 생성할 때 사용되지 않지만 게시할 때 오류가 발생하지 않도록 하려면 이 필드를 채워야 합니다.
