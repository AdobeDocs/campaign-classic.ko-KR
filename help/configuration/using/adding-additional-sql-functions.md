---
product: campaign
title: 추가 SQL 함수 추가
description: 추가 SQL 함수 정의 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# 추가 SQL 함수 정의{#adding-additional-sql-functions}

Adobe Campaign을 통해 사용자는 **고유의 기능** 데이터베이스에서 제공하는 SQL 함수와 콘솔에서 아직 사용할 수 없는 SQL 함수를 모두 액세스할 수 있습니다. 이 기능은 예를 들어 집계 함수(평균, 최대, 합계)에 유용합니다. 이 함수는 콘솔에서 표현식을 &quot;수동&quot;으로 작성(예: 날짜 관리)하는 대신, 서버에서 또는 데이터베이스가 특정 함수를 구현하는 더 쉬운 방법을 제공하는 경우에만 계산할 수 있습니다.

이 메커니즘은 Adobe Campaign 콘솔에서 아직 제공되지 않는 최근 또는 흔하지 않은 데이터베이스 엔진 SQL 함수를 사용하려는 경우에도 사용할 수 있습니다.

이러한 함수가 추가되면 다른 사전 정의된 함수와 마찬가지로 표현식 편집기에 나타납니다.

>[!IMPORTANT]
>
>콘솔의 SQL 함수 호출은 더 이상 서버로 자연히 전송되지 않습니다. 따라서 여기에서 설명하는 메커니즘은 다음과 같습니다. **전화할 수 있는 유일한 방법** 예기치 않은 SQL 함수 서버에서 작동합니다.

## 설치 {#installation}

추가할 함수가 **XML 형식의 &quot;package&quot; 파일**: 다음 단락에 구조가 자세히 설명되어 있습니다.

콘솔에서 설치하려면 **도구/고급/가져오기 패키지** 메뉴에서 옵션을 선택한 다음 **[!UICONTROL Install from file]** 을 클릭하고 가져오기 마법사의 지침을 따릅니다.

>[!IMPORTANT]
>
>경고: 가져온 함수 목록이 함수 편집기에 바로 표시되더라도 Adobe Campaign을 다시 시작할 때까지 사용할 수 없습니다.

## 가져올 패키지의 일반 구조 {#general-structure-of-package-to-import}

추가할 함수는에서 찾을 수 있습니다. **&quot;package&quot; 파일** XML 형식에서 사용할 수 있습니다. 예를 들면 다음과 같습니다.

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "7.1"
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

* 다음 **이름**, **네임스페이스** 및 **레이블** 정보 목적으로만 사용됩니다. 설치된 패키지 목록(탐색기/관리/패키지 관리/설치된 패키지)에서 패키지 요약을 볼 수 있습니다.
* 다음 **buildVersion** 및 **buildNumber** 필드는 필수입니다. 콘솔이 연결된 서버 번호와 일치해야 합니다. 이 정보는 &quot;도움말/정보&quot; 상자에서 찾을 수 있습니다.
* 다음 블록, **엔티티** 및 **기능 목록** 필수 항목입니다. funcList에서 &quot;name&quot; 및 &quot;namespace&quot; 필드는 필수이지만 이름은 사용자가 결정할 수 있도록 남겨두고 함수 목록을 고유하게 지정합니다.

   즉, 네임스페이스/이름 쌍이 동일한 다른 함수 목록(여기서 &quot;cus::myList&quot;)을 가져오는 경우 이전에 가져온 함수가 삭제됩니다. 반대로 이 네임스페이스/이름 쌍을 변경하면 가져온 새로운 일련의 함수가 이전 함수에 추가됩니다.

* 다음 **그룹** 요소를 사용하여 가져온 함수가 함수 편집기에 나타날 함수 그룹을 지정할 수 있습니다. @name 속성은 이미 존재하는 이름(이 경우 함수가 고려된 그룹에 추가됨) 또는 새 이름(이 경우 새 그룹에 표시됨)일 수 있습니다.
* 미리 알림: 의 @name 속성에 가능한 값 `<group>` 요소는 다음과 같습니다.

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
>@label 속성을 완료해야 합니다. 이 이름은 사용 가능한 함수 목록에 표시됩니다. 아무 것도 입력하지 않으면 그룹에는 이름이 없습니다. 그러나 기존 이름 이외의 이름을 입력하면 전체 그룹의 이름이 변경됩니다.

여러 개의 다른 그룹에 함수를 추가하려면 여러 개의 함수를 만들 수 있습니다 `<group>`  요소가 동일한 목록에서 추적됩니다.

마지막으로 `<group>` 요소는 패키지 파일의 목적인 하나 또는 여러 함수의 정의를 포함할 수 있습니다. 다음  `<function>`   요소는 다음 단락에 자세히 설명되어 있습니다.

## 기능 설명자 &lt;function>&lt;/function> {#function-descriptor--function-}

여기에 제시된 사례는 우리가 다음을 제공하고자 하는 일반적인 사례이다 **함수 구현**.

아래는 연령을 사용하여 성숙한 것으로 간주된 기간 수를 나타내는 &quot;상대적 성숙&quot; 기능의 예입니다.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

다음 **@name** 필드는 함수의 이름을 참조하고 &quot;args&quot;는 설명에 표시될 매개 변수 목록입니다. 이 경우 함수는 &quot;relativeMaturity( `<age>` )을 클릭하여 제품에서 사용할 수 있습니다.

* **도움말** 는 표현식 편집기 창 하단에 표시되는 필드입니다.
* **@display** 는 유용한 메시지입니다.

   >[!NOTE]
   >
   >@help 및 @display 속성에서 문자열 &quot;$1&quot;은(는) 첫 번째 함수 매개 변수(여기서는 &quot;Age&quot;)에 제공된 이름을 나타냅니다. $2, $3... 은(는) 다음 매개 변수를 나타냅니다. 아래에 설명된 @body 속성에서 $1은 호출 동안 함수에 전달되는 인수 값을 지정합니다.

   >[!NOTE]
   >
   >설명은 유효한 XML 문자의 문자열이어야 합니다. &lt; 및 > 대신 &#39;&lt;&#39; 및 &#39;>&#39;를 사용하십시오.

* **@type** 는 함수 반환 형식이며 표준 값(long, string, byte, datetime...)입니다. 생략하면 서버에서 함수를 구현하는 식 내에서 사용 가능한 형식 중 최상의 형식을 결정합니다.
* **@minArgs** 및 **maxArgs** 매개변수에 대한 매개변수 수(최소 및 최대)를 지정합니다. 예를 들어 매개 변수가 2개인 함수의 경우 minArgs와 maxArgs는 2와 2가 됩니다. 3개의 매개 변수와 1개의 선택적 매개 변수의 경우 각각 3과 4가 됩니다.
* 마지막으로 **providerPart** 요소는 함수 구현을 제공합니다.

   * 다음 **공급자** 속성은 필수 항목이며, 구현이 제공되는 데이터베이스 시스템을 지정합니다. 예제에서 보듯이 표현식 구문 또는 기본 함수가 다른 경우 데이터베이스에 따라 대체 구현이 제공될 수 있습니다.
   * 다음 **@body** 속성에는 함수 구현이 포함됩니다. 참고: 이 구현은 코드 블록이 아닌 데이터베이스 언어로 된 표현식이어야 합니다. 데이터베이스에 따라 표현식은 단일 값만 반환하는 하위 쿼리(&quot;(select column from table where...)&quot;)일 수 있습니다. 예를 들어 Oracle의 경우(쿼리는 대괄호로 작성해야 함)입니다.

   >[!NOTE]
   >
   >정의된 함수에 의해 하나 또는 두 개의 데이터베이스만 쿼리될 가능성이 있는 경우 이러한 데이터베이스에 해당하는 정의만 항상 제공할 수 있습니다.

## &#39;통과&#39; 함수 설명자 {#pass-through--function-descriptor}

특수 함수 설명자는 **&quot;pass-through&quot;** 블록, 지정되지 않은 &quot;공급자&quot; 데이터베이스 시스템 이 경우 &quot;body&quot; 구현에는 사용된 데이터베이스에 종속되지 않은 구문을 사용하는 단일 함수 호출만 포함될 수 있습니다. 한편 &quot;ProviderPart&quot; 블록은 고유합니다.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

이 경우 함수를 추가하는 것은 기본적으로 사용할 수 없었을 데이터베이스 함수를 이제 클라이언트가 볼 수 있도록 하는 역할만 합니다.

## 예제 {#examples}

추가 함수 예는 사전 정의된 패키지 &quot;xtkdatakitfuncList.xml&quot;에서 찾을 수 있습니다.
