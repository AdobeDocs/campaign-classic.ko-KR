---
product: campaign
title: 추가 SQL 함수 추가
description: 추가 SQL 함수 추가
audience: configuration
content-type: reference
topic-tags: api
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 1%

---

# 추가 SQL 함수 추가{#adding-additional-sql-functions}

## 소개 {#introduction}

Adobe Campaign에서는 사용자가 데이터베이스에서 제공하는 함수와 콘솔에서 아직 사용할 수 없는 함수 모두 SQL 함수에 액세스할 수 있는 **개의 자체 함수**&#x200B;를 정의할 수 있습니다. 이 기능은 예를 들어 집계 함수(평균, 최대, 합계)에 유용합니다. 집계 함수는 서버에서만 계산되거나 데이터베이스가 콘솔에 표현식을 &quot;수동으로&quot; 기록하지 않고 특정 기능을 보다 쉽게 구현할 수 있는 경우에 유용합니다(예: 날짜 관리).

이 메커니즘은 Adobe Campaign 콘솔에서 아직 제공하지 않은 최근 또는 흔하지 않은 데이터베이스 엔진 SQL 함수를 사용하려는 경우에도 사용할 수 있습니다.

이러한 함수가 추가되면 미리 정의된 다른 함수와 마찬가지로 표현식 편집기에 표시됩니다.

>[!IMPORTANT]
>
>콘솔의 SQL 함수 호출은 더 이상 자연스럽게 서버로 전송되지 않습니다. 따라서 여기에 설명된 메커니즘은 계획되지 않은 SQL 함수 서버에서&#x200B;**를 호출하는 유일한 방법이**&#x200B;가 됩니다.

## 설치 {#installation}

추가할 함수는 XML 형식&#x200B;**의**&quot;package&quot; 파일에 있으며, 이 파일의 구조는 다음 단락에 자세히 설명되어 있습니다.

콘솔에서 설치하려면 메뉴에서 **도구/고급/가져오기 패키지** 옵션을 선택한 다음 **[!UICONTROL Install from file]** 를 선택하고 가져오기 마법사의 지침을 따릅니다.

>[!IMPORTANT]
>
>경고:가져온 함수 목록이 함수 편집기에 바로 표시되더라도 Adobe Campaign을 다시 시작할 때까지 사용할 수 없습니다.

## 가져올 패키지의 일반 구조 {#general-structure-of-package-to-import}

추가할 함수는 **&quot;package&quot; 파일**&#x200B;에서 XML 형식으로 찾을 수 있습니다. 다음은 한 예입니다.

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

* **name**, **네임스페이스** 및 **label**&#x200B;은(는) 정보용으로만 사용됩니다. 이 구성 요소로 설치된 패키지 목록(탐색기/관리/패키지 관리/설치된 패키지)에 패키지 요약을 볼 수 있습니다.
* **buildVersion** 및 **buildNumber** 필드는 필수입니다. 콘솔이 연결된 서버 번호에 해당해야 합니다. 이 정보는 &quot;도움말/정보&quot; 상자에 있습니다.
* 다음 블록인 **entities** 및 **funclist**&#x200B;는 필수입니다. FuncList에서는 &quot;name&quot; 및 &quot;namespace&quot; 필드가 필수이지만, 해당 이름이 사용자가 결정할 수 있도록 남겨져 함수 목록을 고유하게 지정합니다.

   즉, 동일한 네임스페이스/이름 쌍(여기서 &quot;cus::myList&quot;)을 사용하는 다른 함수 목록을 가져오는 경우 이전에 가져온 함수가 삭제됩니다. 반대로 이 네임스페이스/이름 쌍을 변경하면 가져온 새 일련의 함수가 이전 함수에 추가됩니다.

* **group** 요소를 사용하면 가져온 함수가 함수 편집기에 표시되는 함수 그룹을 지정할 수 있습니다. @name 속성은 이미 존재하는 이름(이 경우 함수는 고려된 그룹에 추가) 또는 새 이름(이 경우 새 그룹에 표시)일 수 있습니다.
* 미리 알림:`<group>` 요소의 @name 속성에 가능한 값은 다음과 같습니다.

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>@label 속성을 완료해야 합니다.사용 가능한 함수 목록에 표시될 이름입니다. 아무 것도 입력하지 않으면 그룹의 이름이 없습니다. 그러나 기존 이름 이외의 이름을 입력하면 전체 그룹의 이름이 변경됩니다.

여러 다른 그룹에 함수를 추가하려면 동일한 목록에서 여러 `<group>` 요소를 추적할 수 있습니다.

마지막으로, `<group>` 요소에는 패키지 파일의 목적인 하나 또는 여러 함수의 정의가 포함될 수 있습니다. `<function>`   요소는 다음 단락에 자세히 설명되어 있습니다.

## 함수 설명자 &lt;함수>&lt;/function> {#function-descriptor--function-}

여기에 제시된 사례는 **함수 구현**&#x200B;을 제공하려는 일반적인 경우입니다.

아래는 연령 사용 시 개인이 성숙된 것으로 간주된 기간을 나타내는 &quot;상대적 성숙도&quot; 기능의 예입니다.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

**@name** 필드는 함수의 이름을 참조하며, &quot;args&quot;는 설명에 표시될 매개 변수의 목록입니다. 이 경우 함수는 함수 선택 창에 &quot;relativeMaturity( `<age>` )로 표시됩니다.

* **** 도움말: 표현식 편집기 창 하단에 표시되는 필드입니다.
* **@** displayis는 유용한 메시지입니다.

   >[!NOTE]
   >
   >@help 및 @display 속성에서 문자열 &quot;$1&quot;은 첫 번째 함수 매개 변수(여기서는 &quot;Age&quot;)에 제공된 이름을 나타냅니다. $2, $3.. 는 다음 매개 변수를 나타냅니다. 아래에 자세히 설명된 @body 속성에서 $1은 호출 중에 함수에 전달된 인수 값을 지정합니다.

   >[!NOTE]
   >
   >설명은 유효한 XML 문자 문자열이어야 합니다.&lt; 및 > 대신 &#39;&lt;&#39; 및 &#39;>&#39;를 사용하십시오.

* **@** typeis는 함수 반환 형식이며 표준 값(long, string, byte, datetime..)입니다. 생략하면 서버가 함수를 구현하는 표현식 내에서 사용할 수 있는 유형 중에서 최상의 유형을 결정합니다.
* **@** minArgument 및  **** maxArgs매개 변수에 대한 매개 변수의 수(최소 및 최대)를 지정합니다. 예를 들어 매개 변수가 2개인 함수의 경우 minArgs 및 maxArgs는 2와 2입니다. 3개의 매개 변수에 1개의 선택 사항을 더한 경우 각각 3과 4가 됩니다.
* 마지막으로 **providerPart** 요소는 함수 구현을 제공합니다.

   * **provider** 속성은 필수입니다. 이 속성은 구현이 제공되는 데이터베이스 시스템을 지정합니다. 예제에서 알 수 있듯이 표현식 구문 또는 기본 함수가 다를 경우 데이터베이스에 따라 대체 구현을 제공할 수 있습니다.
   * **@body** 특성에 함수 구현이 포함되어 있습니다. 참고:이 구현은 데이터베이스 언어로 된 표현식이어야 합니다(코드 블록이 아님). 데이터베이스에 따라 표현식은 단일 값만 반환하는 하위 쿼리(&quot;(여기서... 테이블의 열 선택)&quot;일 수 있습니다. 예를 들어 Oracle의 경우 질의는 대괄호로 작성해야 합니다.

   >[!NOTE]
   >
   >정의된 함수에 의해 하나 또는 두 개의 데이터베이스만 쿼리될 수 있는 경우 항상 이러한 데이터베이스에 해당하는 정의만 제공할 수 있습니다.

## &#39;통과&#39; 함수 설명자 {#pass-through--function-descriptor}

특수 함수 설명자는 지정되지 않은 &quot;공급자&quot; 데이터베이스 시스템을 사용하는 **&quot;pass-through&quot;** 블록입니다. 이 경우 &quot;body&quot; 구현은 사용된 데이터베이스에 종속되지 않는 구문을 사용하는 단일 함수 호출만 포함할 수 있습니다. 반면 &quot;ProviderPart&quot; 블록은 고유합니다.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

이 경우 함수를 추가하면 기본적으로 사용할 수 없을 데이터베이스 함수를 만들 수만 있으며 이제 클라이언트가 볼 수 있습니다.

## 예제 {#examples}

추가 함수 예는 사전 정의된 패키지 &quot;xtkdatakitfuncList.xml&quot;에서 확인할 수 있습니다.
