---
title: 추가 SQL 함수 추가
seo-title: 추가 SQL 함수 추가
description: 추가 SQL 함수 추가
seo-description: null
page-status-flag: never-activated
uuid: d66b5ca2-ac7d-4654-9f0e-9bfe56490c19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 728a95f8-46fe-49a8-a645-a0dd6eeb6615
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# 추가 SQL 함수 추가{#adding-additional-sql-functions}

## 소개 {#introduction}

Adobe Campaign을 사용하면 데이터베이스에 의해 제공되는 기능과 콘솔에 아직 사용할 수 없는 SQL 함수에 액세스할 수 있는 **고유한 기능을** 정의할 수 있습니다. 이 기능은 집계 함수(평균, 최대, 합계)에 유용합니다. 예를 들어 서버에서만 계산되거나 데이터베이스에서 콘솔에 표현식을 &quot;수동으로&quot; 쓰는 대신 특정 함수를 구현하는 쉬운 방법을 제공하는 경우에 유용합니다.

Adobe Campaign 콘솔에서 아직 제공되지 않는 최신 데이터베이스 엔진 SQL 함수를 사용하려는 경우에도 이 메커니즘을 사용할 수 있습니다.

이러한 함수가 추가되면 미리 정의된 다른 함수와 마찬가지로 표현식 편집기에 나타납니다.

>[!CAUTION]
>
>콘솔의 SQL 함수 호출은 더 이상 자연스럽게 서버로 전송되지 않습니다. 따라서 여기에 설명된 메커니즘은 계획되지 않은 **SQL 함수 서버에서 호출하는** 유일한 방법이 됩니다.

## 설치 {#installation}

추가할 함수는 XML 형식의 **&quot;패키지&quot; 파일에**&#x200B;있으며 이 파일의 구조는 다음 단락에 자세히 나와 있습니다.

콘솔에서 설치하려면 메뉴에서 도구/ **고급/가져오기 패키지** 옵션을 선택한 다음 **[!UICONTROL Install from file]** 을 선택하고 가져오기 마법사의 지침을 따릅니다.

>[!CAUTION]
>
>경고:가져온 함수 목록이 함수 편집기에 바로 표시되더라도 Adobe Campaign을 다시 시작해야 사용할 수 있습니다.

## 가져올 패키지의 일반 구조 {#general-structure-of-package-to-import}

추가할 함수는 **&quot;패키지&quot; 파일에서** XML 형식으로 찾을 수 있습니다. 다음은 예입니다.

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* 이름 **,**&#x200B;네임스페이스 **및** 레이블은 **** 정보 용도로만 사용할 수 있습니다. 이 플러그인을 사용하면 설치된 패키지 목록(탐색기/관리/패키지 관리/설치된 패키지)에 있는 패키지의 요약을 볼 수 있습니다.
* buildVersion **및** buildNumber **** 필드는 필수입니다. 콘솔이 연결된 서버 번호와 일치해야 합니다. 이 정보는 &quot;도움말/정보&quot; 상자에 있습니다.
* 다음 블록, **개체** 및 **곰팡이는** 필수입니다. FuncList에서는 &quot;name&quot; 및 &quot;namespace&quot; 필드가 필수이지만, 필드 이름은 사용자가 결정할 수 있도록 남겨 두고, 함수 목록을 고유하게 지정합니다.

   즉, 동일한 네임스페이스/이름 쌍의 다른 함수 목록(&quot;cus::myList&quot;)을 가져오면 이전에 가져온 함수가 삭제됩니다. 반대로 이 네임스페이스/이름 쌍을 변경하면 가져온 새 함수 시리즈가 이전 함수에 추가됩니다.

* 그룹 **** 요소를 사용하면 함수 편집기에 가져온 함수가 나타날 함수 그룹을 지정할 수 있습니다. @name 속성은 이미 존재하는 이름(이 경우 해당 함수가 고려된 그룹에 추가됨) 또는 새 이름(이 경우 새 그룹에 표시됨)일 수 있습니다.
* 미리 알림:요소의 @name 속성에 가능한 값은 다음과 같습니다. `<group>`

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!CAUTION]
>
>@label 속성을 완료해야 합니다.사용 가능한 함수 목록에 표시될 이름입니다. 아무 것도 입력하지 않으면 그룹에 이름이 없습니다. 그러나 기존 이름 이외의 이름을 입력하면 전체 그룹 이름이 변경됩니다.

여러 그룹에 함수를 추가하려면 동일한 목록에서 여러 `<group>` 요소를 추적할 수 있습니다.

마지막으로, `<group>` 요소에는 패키지 파일의 용도인 하나 또는 여러 함수의 정의가 포함될 수 있습니다. 이 `<function>` 요소는 다음 단락에 자세히 설명되어 있습니다.

## 함수 설명자 &lt;함수>&lt;/function> {#function-descriptor--function-}

여기에 제시된 사례는 **기능 구현을**&#x200B;제공하려는 일반적인 경우입니다.

다음은 나이를 사용하여 사람이 성숙하다고 간주된 기간을 나타내는 &quot;상대적 성숙도&quot; 기능의 예입니다.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

@name **** 필드는 함수의 이름을 참조하며, &quot;args&quot;는 설명에 표시될 매개 변수의 목록입니다. 이 경우 함수는 함수 선택 창에 &quot;relativeMaturity( `<age>` )&quot;로 표시됩니다.

* **help** is the field displayed at the bottom of the expression editor window.
* **@display** is an information message.

   >[!NOTE]
   >
   >@help 및 @display 속성에서 문자열 &quot;$1&quot;은(는) 첫 번째 함수 매개 변수(&quot;Age&quot;)에 지정된 이름을 나타냅니다. $2, $3...는 다음 매개 변수를 나타냅니다. 아래에 자세히 설명된 @body 속성에서 $1은 호출 중에 함수에 전달된 인수 값을 지정합니다.

   >[!NOTE]
   >
   >설명은 유효한 XML 문자 문자열이어야 합니다.&lt; and > 대신 &#39;&lt;&#39; 및 &#39;>&#39;의 사용을 주목하십시오.

* **@type** 은 함수 반환 형식이며 표준 값(long, string, byte, datetime..)입니다. 이 값이 생략되면 서버는 함수를 구현하는 표현식 내에서 사용 가능한 형식 중 최상의 유형을 결정합니다.
* **@minArgs** 및 **maxArgs는** 매개 변수의 매개 변수 수(최소 및 최대)를 지정합니다. 예를 들어 매개 변수가 2개인 함수의 경우 minArgs 및 maxArgs는 2와 2입니다. 3개의 매개 변수와 1개의 선택 사항은 각각 3과 4입니다.
* 마지막으로 **providerPart** 요소는 함수 구현을 제공합니다.

   * 이 **provider** 속성은 필수 요소로서 구현이 제공되는 데이터베이스 시스템을 지정합니다. 이 예제에서 보듯이 표현식 동기화 또는 기본 함수가 다를 경우 데이터베이스에 따라 대체 구현을 제공할 수 있습니다.
   * @body **** 속성에는 함수 구현이 포함됩니다. 참고:이 구현은 데이터베이스 언어의 표현식이어야 합니다(코드 블록이 아님). 데이터베이스에 따라 표현식은 단일 값만 반환하는 하위 쿼리(&quot;(테이블에서 열 선택...)&quot;)일 수 있습니다. 예를 들어 Oracle의 경우 쿼리를 대괄호로 작성해야 합니다.
   >[!NOTE]
   >
   >정의된 함수에 의해 하나 또는 두 개의 데이터베이스만 쿼리될 가능성이 있는 경우, 항상 이러한 데이터베이스에 해당하는 정의만 제공할 수 있습니다.

## &#39;통과&#39; 함수 설명자 {#pass-through--function-descriptor}

특수 함수 설명자는 지정되지 않은 &quot;공급자&quot; 데이터베이스 시스템을 **&quot;통과** &quot; 블록입니다. 이 경우 &quot;body&quot; 구현은 사용된 데이터베이스에 종속되지 않는 구문으로 단일 함수 호출만 포함할 수 있습니다. 반면 &quot;ProviderPart&quot; 블록은 고유합니다.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

이 경우 함수를 추가하면 기본적으로 사용할 수 없었던 데이터베이스 함수가 클라이언트에 표시됩니다.

## 예 {#examples}

함수 예제는 사전 정의된 패키지 &quot;xtkdatakitfuncList.xml&quot;에서 찾을 수 있습니다.
