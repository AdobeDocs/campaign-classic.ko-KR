---
solution: Campaign Classic
product: campaign
title: 필터 조건 정의
description: 필터 조건 정의
audience: platform
content-type: reference
topic-tags: creating-queries
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '3229'
ht-degree: 37%

---


# 필터 조건 정의{#defining-filter-conditions}

## 연산자 {#choosing-the-operator} 선택

필터링 조건 내에서 연산자를 사용하여 두 값을 함께 연결해야 합니다.

![](assets/query_editor_nveau_96.png)

다음은 사용할 수 있는 연산자 목록입니다.

<table> 
 <thead> 
  <tr> 
   <th> 연산자<br /> </th> 
   <th> 목적<br /> </th> 
   <th> 예제<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">같음</span> <br /> </td> 
   <td> 두 번째 값 열에 입력한 데이터와 동일한 결과를 반환합니다.<br /> </td> 
   <td> <strong>'Jones'와 같은 성(@lastName)은</strong> 성이 Jones인 수신자만 반환합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">보다 큼</span> <br /> </td> 
   <td> 입력한 값보다 큰 값을 반환합니다.<br /> </td> 
   <td> <strong>50</strong>보다 큰 연령(@age)은 '50'보다 큰 모든 값을 반환합니다(예:'51', '52' 등<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">보다 작음</span> <br /> </td> 
   <td> 입력한 값보다 작은 값을 반환합니다.<br /> </td> 
   <td> <strong>'DaysAgo(100)'</strong> 앞에 만든 작성 날짜(@created)은 100일 전에 만든 모든 받는 사람을 반환합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">크거나 같음</span> <br /> </td> 
   <td> 입력한 값보다 크거나 같은 모든 값을 반환합니다.<br /> </td> 
   <td> <strong>'30'보다 크거나 같은 연령(@age)은</strong> 30세 이상의 모든 수신자를 반환합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">작거나 같음</span> <br /> </td> 
   <td> 입력한 값보다 작거나 같은 모든 값을 반환합니다.<br /> </td> 
   <td> <strong>연령(@age)이 '60'보다</strong> 작거나 같으면 60세 이하의 모든 수신자가 반환됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">같지 않음</span> <br /> </td> 
   <td> 입력한 값과 동일하지 않은 모든 값을 반환합니다.<br /> </td> 
   <td> <strong>'English'와 같은 언어(@language)</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">다음으로 시작</span> <br /> </td> 
   <td> 입력한 값으로 시작하는 결과를 반환합니다.<br /> </td> 
   <td> <strong>계정 번호 (@account)은 '32010'로 시작합니다.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">다음으로 시작하지 않음</span> <br /> </td> 
   <td> 입력한 값으로 시작하지 않은 결과를 반환합니다.<br /> </td> 
   <td> <strong>계정 번호(@account)이 '20'으로 시작되지 않습니다</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">포함</span> <br /> </td> 
   <td> 입력한 값 이상을 포함하는 결과를 반환합니다.<br /> </td> 
   <td> <strong>이메일 도메인(@domain)에 'mail'이</strong> 들어 있으며 'mail'이 포함된 모든 도메인 이름을 반환합니다. 따라서 'gmail.com' 도메인도 반환됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">포함하지 않음</span> <br /> </td> 
   <td> 입력한 값을 포함하지 않는 결과를 반환합니다.<br /> </td> 
   <td> <strong>이메일 도메인(@domain)에 'vo'가 없습니다</strong>. 이 경우 'vo'가 포함된 도메인 이름은 반환되지 않습니다. 'voila.fr' 도메인 이름이 결과에 나타나지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">비슷함</span> <br /> </td> 
   <td> <span class="uicontrol">비슷함</span>은 <span class="uicontrol">포함</span> 연산자와 매우 유사합니다. 값에 <span class="uicontrol">%</span> 와일드카드 문자를 삽입할 수 있습니다.<br /> </td> 
   <td> <strong>'Jon%s'과(와) 같은 성(@lastName)</strong>. 여기서, 만일 교환자가 'n'과 's' 사이의 누락된 문자를 잊었더라면 "존스"라는 이름을 찾기 위해 와일드카드 문자는 "조커"로 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">비슷하지 않음</span> <br /> </td> 
   <td> <span class="uicontrol">비슷함</span>과 유사합니다 . 입력한 값을 복구할 수 없습니다. 여기서도 입력한 값은 <span class="uicontrol">%</span> 와일드카드 문자를 포함해야 합니다.<br /> </td> 
   <td> <strong>성(@lastName)은 'Smi%h'와(와) 같지 않습니다</strong>. 여기에서 성이 'Smi%h'인 수신자는 반환되지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">비어 있음</span> <br /> </td> 
   <td> 이 경우 두 번째 값 열의 빈 값과 일치하는 결과를 찾습니다.<br /> </td> 
   <td> <strong>모바일(@mobilePhone)은 </strong> 비어 있으면 모바일 번호가 없는 모든 수신자를 반환합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">비어 있지 않음</span> <br /> </td> 
   <td> <span class="uicontrol">Is empty</span> 연산자와 반대로 작동합니다. 두 번째 값 열에 데이터를 입력할 필요가 없습니다.<br /> </td> 
   <td> <strong>이메일(@email)이 비어 있지</strong> 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">다음 항목에 포함</span> <br /> </td> 
   <td> 지정된 값에 포함된 결과를 반환합니다. 이러한 값은 쉼표로 구분해야 합니다.<br /> </td> 
   <td> <strong>생년월일(@birthDate)은 '12/10/1979,12/10/1984'에</strong> 포함되며, 이 날짜 사이에 태어난 수신자가 반환됩니다.  <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">이(가)</span> <br /> </td> 
   <td> <span class="uicontrol">Is included in</span> 연산자와 같이 작동합니다. 여기에서 입력한 값을 기준으로 받는 사람을 제외합니다.<br /> </td> 
   <td> <strong>생년월일(@birthDate)은 '12/10/1979,12/10/1984'에 포함되지 않습니다</strong>. 이전 예제와 달리 이 날짜 내에서 태어난 수신자는 반환되지 않습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## {#using-and--or--except}을 제외한 AND 또는

여러 필터링 조건을 사용하는 쿼리의 경우 조건 사이의 링크를 정의해야 합니다. 다음과 같은 세 가지 링크가 있습니다.

* **[!UICONTROL And]** 두 개의 필터링 조건을 결합할 수 있습니다.
* **[!UICONTROL Or]** 대체 요소를 제공할 수 있도록
* **[!UICONTROL Except]** 예외를 정의할 수 있습니다.

**[!UICONTROL And]**(기본적으로 제공됨)을 클릭하고 드롭다운 목록에서 선택합니다.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**:조건을 추가하고 오버필터링을 활성화합니다.
* **[!UICONTROL Or]**:조건을 추가하고 오버필터링을 활성화합니다.

   다음 예제에서는 이메일 도메인에 &quot;orange.co.uk&quot;이 포함된 수신자를 찾거나 게시물 코드가 &quot;NW&quot;로 시작하는 수신자를 찾을 수 있습니다.

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**:2개의 필터가 있고 첫 번째 필터가 값을 반환하지 않으면 이 유형의 링크는 예외를 만듭니다.

   다음 예제에서는 받는 사람의 이름이 &quot;Smith&quot;인 경우를 제외하고 이메일 도메인에 &quot;orange.co.uk&quot;이 포함된 수신자를 반환합니다.

   ![](assets/query_condition_modif_03.png)

이 예는 다음을 표시할 수 있는 필터를 보여줍니다.스페인어를 사용하거나 휴대폰 번호를 가진 여성 또는 계정 번호가 없는 수신자이고 회사 이름이 &quot;N&quot;자로 시작하는 받는 사람

![](assets/query_editor_nveau_31.png)

## 조건 우선 순위 지정 {#prioritizing-conditions}

이 섹션에서는 도구 모음의 파란색 화살표 덕분에 조건의 우선 순위를 지정하는 방법을 설명합니다.

* 오른쪽에 있는 화살표를 사용하면 필터에 괄호 수준을 추가할 수 있습니다.
* 왼쪽에 있는 화살표를 사용하면 필터에서 선택한 괄호 레벨을 삭제할 수 있습니다.

   ![](assets/query_condition_modif_04.png)

* 세로 화살표를 사용하면 조건을 이동하여 실행 순서를 변경할 수 있습니다.

이 예제에서는 화살표를 사용하여 괄호 레벨을 삭제하는 방법을 보여 줍니다. 다음 필터링 조건에서 시작합니다.**[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

**[!UICONTROL Gender (@gender) equal to Male]** 필터링 조건에 커서를 놓고 **[!UICONTROL Remove a parenthesis level]** 화살표를 클릭합니다.

![](assets/query_editor_nveau_32.png)

**[!UICONTROL Gender (@gender) equal to Male]** 조건이 괄호에서 제거되었습니다. 그것은 &quot;런던과 같은 도시&quot; 상태와 같은 수준으로 이동했다. 이러한 조건은 모두 연결되어 있습니다(**[!UICONTROL And]**).

## {#selecting-data-to-extract} 추출할 데이터 선택

사용 가능한 필드는 한 테이블마다 다릅니다. 모든 필드는 **[!UICONTROL Main element]**&#x200B;이라는 기본 노드에 저장됩니다. 다음 예에서 사용 가능한 필드는 수신자 표에 있습니다. 필드는 항상 알파벳순으로 표시됩니다.

창 아래쪽에 선택한 필드의 세부 정보가 표시됩니다. 예를 들어 **[!UICONTROL Email domain]** 필드는 **[!UICONTROL Calculated SQL field]**&#x200B;이고 그 확장자는 **[!UICONTROL (@domain)]**&#x200B;입니다.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>**[!UICONTROL Search]** 도구를 사용하여 사용 가능한 필드를 찾습니다.

사용 가능한 필드를 두 번 클릭하여 출력 열에 추가합니다. 쿼리가 끝날 때 선택한 각 필드는 **[!UICONTROL Data preview]** 창에 열을 만듭니다.

![](assets/query_editor_nveau_01.png)

고급 필드는 기본적으로 표시되지 않습니다. 사용 가능한 필드의 오른쪽 하단에서 **[!UICONTROL Display advanced fields]**&#x200B;을 클릭하여 모든 항목을 표시합니다. 다시 클릭하여 이전 보기로 돌아갑니다.

예를 들어 수신자 테이블에서 고급 필드는 **Boolean 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]** 등입니다.

다음 예는 수신자 테이블의 고급 필드를 보여줍니다.

![](assets/query_editor_nveau_53.png)

다양한 필드 카테고리:

<table> 
 <thead> 
  <tr> 
   <th> 아이콘<br /> </th> 
   <th> 설명<br /> </th> 
   <th> 예제<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> 단순 필드<br /> </td> 
   <td> 이메일, 성별 등<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> 기본 키. 이 SQL 필드는 테이블의 레코드를 식별하는 방법입니다.<br /> </td> 
   <td> 식별자 수신자는 기본 키이고 식별자는 정의별로 고유합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> 외래 키 다른 테이블에 대한 링크로 사용됩니다.<br /> </td> 
   <td> 받는 사람 외래 키, 서비스 외래 키 등<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> 계산된 필드. 이 유형의 필드는 데이터베이스의 값을 사용하여 요청에 따라 계산됩니다.<br /> </td> 
   <td> 연령, 이메일 도메인 등<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> 긴 텍스트가 포함된 필드입니다.<br /> </td> 
   <td> 주석, 전체 주소 등<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> 인덱싱된 SQL 필드.<br /> </td> 
   <td> 전체 이름, ISO 코드 등 <br /> </td> 
  </tr> 
 </tbody> 
</table>

표 및 컬렉션 요소에 대한 링크:

<table> 
 <thead> 
  <tr> 
   <th> 아이콘<br /> </th> 
   <th> 설명<br /> </th> 
   <th> 예제<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> 특정 테이블에 대한 링크. 이것은 1-1 유형 연인과 일치합니다. 소스 테이블의 항목은 대상 테이블의 한 번만 일치할 수 있습니다. 예를 들어 한 국가에 한 명의 받는 사람만 연결할 수 있습니다.<br /> </td> 
   <td> 폴더, 상태, 국가 등 <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> 특정 테이블의 컬렉션 요소. 이것은 1N형 연인과 일치한다. 하나의 소스 테이블 항목은 대상 테이블의 여러 발생 횟수와 일치할 수 있지만 대상 테이블의 한 항목은 소스 테이블의 한 번만 일치할 수 있습니다. 예를 들어 한 수신자가 'n' 구독 편지에 가입할 수 있습니다.<br /> </td> 
   <td> 가입, 목록, 제외 로그 등<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* 표현식을 편집할 출력 열을 추가하려면 **[!UICONTROL Add]** 단추(사이드 아이콘 막대 위)를 사용합니다. 표현식 편집에 대한 자세한 내용은 [이 섹션](#building-expressions)을 참조하십시오.
>* 빨간색 &#39;x&#39;(**삭제**)를 클릭하여 출력 열을 삭제합니다.
>* 화살표를 사용하여 출력 열의 순서를 변경합니다.
>* **[!UICONTROL Distribution of values]**&#x200B;은 선택한 필드의 값(예: 수신자 도시, 수신자 언어 등에 연결된 배포)의 배포를 보는 방법입니다.


## 계산된 필드 {#creating-calculated-fields} 만들기

필요한 경우 데이터 서식 지정 중에 열을 추가합니다. 계산된 필드는 데이터 미리 보기 섹션에 열을 추가합니다. **[!UICONTROL Add a calculated field]**&#x200B;을(를) 클릭합니다.

![](assets/query_editor_nveau_43.png)

계산된 필드에는 4가지 유형이 있습니다.

* **[!UICONTROL Fixed string]**:문자열을 추가할 수 있습니다.

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**:계산된 필드의 값은 문자 문자열 및 JavaScript 지시문을 결합합니다.

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**:계산된 필드의 값은 JavaScript 함수 평가의 결과입니다. 반환된 값을 입력할 수 있습니다(숫자, 날짜 등).

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**:이 유형의 필드를 사용하면 새 열에 있는 출력 열 중 하나의 컨텐츠를 사용하거나 수정할 수 있습니다.

   열의 소스 값을 사용하여 대상 값을 지정할 수 있습니다. 이 대상 값은 새 출력 열에 표시됩니다.

   계산된 필드 유형 **[!UICONTROL Enumerations]**&#x200B;을(를) 추가하는 예제는 [이 섹션](../../workflow/using/adding-enumeration-type-calculated-field.md)을 참조하십시오.

   ![](assets/query_editor_nveau_63.png)

   **[!UICONTROL Enumerations]** 유형 계산 필드에는 4개의 조건이 포함될 수 있습니다.

   * **[!UICONTROL Keep the source value]** 소스 값을 변경하지 않고 타겟으로 복원합니다.
   * **[!UICONTROL Use the following value]** 정의되지 않은 소스 값에 대한 기본 대상 값을 입력할 수 있습니다.
   * **[!UICONTROL Generate a warning and continue]** 사용자에게 소스 값을 변경할 수 없음을 경고합니다.
   * **[!UICONTROL Generate an error and reject the line]** 행을 계산 및 가져올 수 없도록 합니다.

삽입된 필드의 세부 정보를 보려면 **[!UICONTROL Detail of calculated field]**&#x200B;을 클릭합니다.

이 계산된 필드를 제거하려면 **[!UICONTROL Remove the calculated field]** 십자가를 클릭합니다.

![](assets/query_editor_nveau_58.png)

## 표현식 {#building-expressions} 만들기

표현식 편집 도구를 사용하면 표현식을 사용하여 집계물을 계산하거나 함수를 생성하거나 공식을 편집할 수 있습니다.

다음 예제에서는 기본 키에 대한 카운트를 실행하는 방법을 보여 줍니다.

다음 단계를 적용합니다.

1. **[!UICONTROL Data to extract]** 창에서 **[!UICONTROL Add]**&#x200B;을 클릭합니다. **[!UICONTROL Formula type]** 창에서 식을 입력할 공식 유형을 선택합니다.

   사용할 수 있는 수식의 유형은 다음과 같습니다.**[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   **[!UICONTROL Process on an aggregate function]** 및 **[!UICONTROL Count]**&#x200B;을 선택합니다.**[!UICONTROL Next]**&#x200B;를 클릭합니다.

   ![](assets/query_editor_nveau_54.png)

1. 기본 키가 계산됩니다.

   ![](assets/query_editor_nveau_88.png)

다음은 **[!UICONTROL Formula types]** 창에서 사용할 수 있는 선택 사항에 대한 자세한 보기입니다.

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** 창으로 돌아갈 수  **[!UICONTROL Field to select]** 있습니다.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. 다음은 집계 사용의 몇 가지 예입니다.

   * **[!UICONTROL Count]** 기본 키 개수를 실행할 수 있습니다.
   * **[!UICONTROL Sum]** 고객이 1년 이상 구입한 모든 구매를 합산할 수 있습니다.
   * **[!UICONTROL Maximum value]** &quot;n&quot; 제품을 가장 많이 구매한 고객을 찾을 수 있습니다.
   * **[!UICONTROL Minimum value]** 고객을 분류하고 최근에 오퍼에 가입한 고객을 찾을 수 있습니다.
   * **[!UICONTROL Average]**. 이 함수를 사용하면 받는 사람의 평균 연령을 계산할 수 있습니다.

      **[!UICONTROL Distinct]** 상자를 사용하면 열의 고유 값과 0이 아닌 값을 복구할 수 있습니다. 예를 들어 모든 받는 사람의 추적 로그를 복구할 수 있으며 이러한 추적 로그는 모두 동일한 받는 사람과 관계가 있으므로 값 1로 변경됩니다.

1. **[!UICONTROL Expression]** 창을  **[!UICONTROL Edit the expression]** 엽니다. 이렇게 하면 숫자가 너무 많은 전화 번호를 감지할 수 있으며 입력 오류가 발생할 수 있습니다.

   ![](assets/query_editor_nveau_71.png)

   사용 가능한 모든 함수 목록을 보려면 [함수 목록](#list-of-functions)을 참조하십시오.

## 함수 목록 {#list-of-functions}

**[!UICONTROL Expression]** 유형 공식이 선택된 경우 &quot;표현식 편집&quot; 창으로 이동합니다. 사용 가능한 필드에 다양한 범주의 함수를 연결할 수 있습니다.**[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** 및 **[!UICONTROL Others]**.

표현식 편집기는 다음과 같습니다.

![](assets/s_ncs_user_filter_define_expression.png)

데이터베이스 테이블에서 필드를 선택하고 고급 함수를 추가할 수 있습니다. 다음 기능을 사용할 수 있습니다.

**집계**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>평균</strong><br /> </td> 
   <td> 숫자 유형 열<br />의 평균을 반환합니다. </td> 
   <td> Avg(&lt;값&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>카운트</strong><br /> </td> 
   <td> 열<br />의 null이 아닌 값을 계산합니다. </td> 
   <td> Count(&lt;값&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> 반환된 값(모든 필드)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> 열<br />의 널이 아닌 개별 값을 계산합니다. </td> 
   <td> Countdistinct(&lt;값&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>최대</strong><br /> </td> 
   <td> 숫자, 문자열 또는 날짜 유형 열의 최대 값을 반환합니다.<br /> </td> 
   <td> Max(&lt;값&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>최소</strong><br /> </td> 
   <td> 숫자, 문자열 또는 날짜 유형 열의 최소 값을 반환합니다.<br /> </td> 
   <td> Min(&lt;값&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> 숫자, 문자열 또는 날짜 열의 표준 편차를 반환합니다.<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>합계</strong><br /> </td> 
   <td> 숫자, 문자열 또는 날짜 유형 열의 값 합계를 반환합니다.<br /> </td> 
   <td> Sum(&lt;값&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**문자열**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> 모든 매개 변수가 null이 아니고 비어 있지 않은지 표시<br /> </td> 
   <td> AllNonNull2(&lt;문자열&gt;, &lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> 모든 매개 변수가 null이 아니고 비어 있지 않은지 표시<br /> </td> 
   <td> AllNonNull3(&lt;문자열&gt;, &lt;문자열&gt;, &lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> 문자열에서 첫 번째 문자의 ASCII 값 반환.<br /> </td> 
   <td> Ascii(&lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> 'n' ASCII 코드에 해당하는 문자 반환<br /> </td> 
   <td> Char(&lt;숫자&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> 문자열 1에서 문자열 2의 위치 반환.<br /> </td> 
   <td> Charindex(&lt;문자열&gt;, &lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> 문자열의 n번째(1에서 n까지) 행 반환<br /> </td> 
   <td> GetLine(&lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> 처음 두 매개 변수가 같으면 세 번째 매개 변수를 반환합니다. 없으면 마지막 매개 변수<br />을 반환합니다. </td> 
   <td> IfEquals(&lt;문자열&gt;, &lt;문자열&gt;, &lt;문자열&gt;, &lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> 매개 변수로 전달된 메모가 null인지 표시<br /> </td> 
   <td> IsMemoNull(&lt;메모&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> 매개 변수로 전달된 문자열을 연결합니다. 필요한 경우 문자열 사이에 공백을 추가합니다.<br /> </td> 
   <td> JuxtWords(&lt;문자열&gt;, &lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> 매개 변수로 전달된 문자열을 연결합니다. 필요한 경우 문자열 사이에 공백을 추가합니다<br /> </td> 
   <td> JuxtWords3(&lt;문자열&gt;, &lt;문자열&gt;, &lt;문자열&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> 왼쪽에서 완성된 문자열 반환<br /> </td> 
   <td> LPad(&lt;문자열&gt;, &lt;숫자&gt;, &lt;문자&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> 문자열의 처음 n자 반환<br /> </td> 
   <td> Left(&lt;문자열&gt;, &lt;숫자&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> 문자열<br />의 길이를 반환합니다. </td> 
   <td> Length(&lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> 문자열을 소문자로 반환<br /> </td> 
   <td> Lower(&lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> 문자열 왼쪽의 공백 제거<br /> </td> 
   <td> Ltrim(&lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> 문자열의 MD5 키를 16진수로 반환<br /> </td> 
   <td> Md5Digest(&lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> 메모에 매개 변수로 전달된 문자열이 포함되어 있는지 지정<br /> </td> 
   <td> MemoContains(&lt;메모&gt;, &lt;문자열&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> 오른쪽에 완성된 문자열 반환<br /> </td> 
   <td> RPad(&lt;문자열&gt;, &lt;숫자&gt;, &lt;문자&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> 문자열의 마지막 n자 반환<br /> </td> 
   <td> Right(&lt;문자열&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> 문자열 오른쪽의 공백 제거<br /> </td> 
   <td> Rtrim(&lt;문자열&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> 각 단어의 첫 번째 문자가 대문자로 표시된 문자열 반환<br /> </td> 
   <td> Smart(&lt;문자열&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> 문자열 n1부터 시작 문자 n2<br />까지 하위 문자열을 추출합니다. </td> 
   <td> Substring(&lt;문자열&gt;, &lt;오프셋&gt;, &lt;길이&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> 숫자를 문자열로 변환<br /> </td> 
   <td> ToString(&lt;number&gt;, &lt;number&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> 문자열을 대문자로 반환<br /> </td> 
   <td> Upper(&lt;문자열&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> 다른 두 매개 변수가 동일한 경우 매개 변수로 전달된 링크의 외부 키 반환<br /> </td> 
   <td> VirtualLink(&lt;숫자&gt;, &lt;&lt;숫자&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> 다른 두 매개 변수가 동일한 경우 매개 변수로 전달된 링크의 외부(텍스트) 키 반환<br /> </td> 
   <td> VirtualLinkStr(&lt;문자열&gt;, &lt;숫자&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> 문자열 크기<br />를 반환합니다. </td> 
   <td> dataLength(&lt;string&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**날짜**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> 날짜에 일자 숫자 추가<br /> </td> 
   <td> AddDays(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> 날짜에 시간(시) 숫자 추가<br /> </td> 
   <td> AddHours(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> 날짜에 시간(분) 숫자 추가<br /> </td> 
   <td> AddMinutes(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> 날짜에 개월 숫자 추가<br /> </td> 
   <td> AddMonths(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> 날짜에 시간(초) 숫자 추가<br /> </td> 
   <td> AddSeconds(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> 날짜에 연도 숫자 추가<br /> </td> 
   <td> AddYears(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> 날짜만 반환(00:00 시간 포함)*<br /> </td> 
   <td> DateOnly(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> 날짜의 일자를 나타내는 숫자 반환<br /> </td> 
   <td> Day(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> 날짜<br /> 연도의 일 수를 반환합니다. </td> 
   <td> DayOfYear(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> 현재 날짜에 해당하는 날짜 빼기 n일(<br />)을 반환합니다. </td> 
   <td> DaysAgo(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> 현재 날짜에 해당하는 날짜(정수 yyymmdd)를 n일 빼기(<br />)로 반환합니다. </td> 
   <td> DaysAgoInt(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> 두 날짜 사이의 일자 수<br /> </td> 
   <td> DaysDiff(&lt;종료 날짜&gt;, &lt;시작 날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> 날짜를 일 단위로 반환<br /> </td> 
   <td> DaysOld(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> 서버의 현재 시스템 날짜 반환<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> 날짜의 시간 반환<br /> </td> 
   <td> Hour(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> 두 날짜 사이의 시간(시) 숫자 반환<br /> </td> 
   <td> HoursDiff(&lt;종료 날짜&gt;, &lt;시작 날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> 날짜의 시간(분) 반환<br /> </td> 
   <td> Minute(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> 두 날짜 사이의 시간(분) 숫자 반환<br /> </td> 
   <td> MinutesDiff(&lt;종료 날짜&gt;, &lt;시작 날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> 날짜의 월을 나타내는 숫자 반환<br /> </td> 
   <td> Month(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> 현재 날짜에서 n개월을 뺀 날짜 반환<br /> </td> 
   <td> MonthsAgo(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> 두 날짜 사이의 개월 숫자 반환<br /> </td> 
   <td> MonthsDiff(&lt;종료 날짜&gt;, &lt;시작 날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> 날짜를 월 단위로 반환<br /> </td> 
   <td> MonthsOld(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> 날짜의 시간(초) 반환<br /> </td> 
   <td> Second(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> 두 날짜 사이의 시간(초) 숫자 반환<br /> </td> 
   <td> SecondsDiff(&lt;종료 날짜&gt;, &lt;시작 날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> 날짜에서 일자 숫자 빼기<br /> </td> 
   <td> SubDays(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> 날짜에서 시간(시) 숫자 빼기<br /> </td> 
   <td> SubHours(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> 날짜에서 시간(분) 숫자 빼기<br /> </td> 
   <td> SubMinutes(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> 날짜에서 개월 숫자 빼기<br /> </td> 
   <td> SubMonths(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> 날짜에서 시간(초) 숫자 빼기<br /> </td> 
   <td> SubSeconds(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> 날짜에서 연도 숫자 빼기<br /> </td> 
   <td> SubYears(&lt;날짜&gt;, &lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> 날짜 + 시간을 날짜로 변환<br /> </td> 
   <td> ToDate(&lt;날짜 + 시간&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> 문자열을 날짜 + 시간으로 변환<br /> </td> 
   <td> ToDateTime(&lt;문자열&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> 날짜+시간을 가장 가까운 시간(초)으로 반올림<br /> </td> 
   <td> TruncDate(@lastModified, &lt;시간(초) 숫자&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> 날짜 + 시간을 초 단위의 특정 정밀도로 반올림<br /> </td> 
   <td> TruncDateTZ(&lt;날짜&gt;, &lt;시간(초) 숫자&gt;, &lt;시간대&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> 날짜를 분기로 반올림<br /> </td> 
   <td> TruncQuarter(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> 시간 부분을 가장 가까운 시간(초)으로 반올림<br /> </td> 
   <td> TruncTim(e&lt;date&gt;, &lt;초 수&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 날짜를 요일로 반올림<br /> </td> 
   <td> TruncWeek(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> 날짜 + 시간을 연도의 1월 1일로 반올림<br /> </td> 
   <td> TruncYear(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> 날짜의 요일을 나타내는 숫자 반환<br /> </td> 
   <td> WeekDay(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> 날짜의 연도를 나타내는 숫자 반환<br /> </td> 
   <td> Year(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> 날짜의 연도 및 월을 나타내는 숫자 반환<br /> </td> 
   <td> YearAndMonth(&lt;날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> 두 날짜 사이의 연도 숫자 반환<br /> </td> 
   <td> YearsDiff(&lt;종료 날짜&gt;, &lt;시작 날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> 날짜를 연 단위로 반환<br /> </td> 
   <td> YearsOld(&lt;날짜&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**Dateonly** 함수는 연산자의 시간대가 아니라 서버의 시간대를 고려합니다.

**숫자**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> 숫자의 절대값 반환<br /> </td> 
   <td> Abs(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> 숫자보다 크거나 같은 최소 정수 반환<br /> </td> 
   <td> Ceil(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> 숫자<br />보다 크거나 같은 최대 정수를 반환합니다. </td> 
   <td> Floor(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> 두 숫자 중 큰 숫자 반환<br /> </td> 
   <td> Greatest(&lt;숫자 1&gt;, &lt;숫자 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> 두 숫자 중 작은 숫자 반환<br /> </td> 
   <td> Least(&lt;숫자 1&gt;, &lt;숫자 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> n1의 정수 부분 중 나머지 부분을 n2<br />로 반환합니다. </td> 
   <td> Mod(&lt;숫자 1&gt;, &lt;숫자 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> 백분율로 표현된 두 수의 비율 반환<br /> </td> 
   <td> Percent(&lt;숫자 1&gt;, &lt;숫자 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> 임의 값 반환<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> 숫자를 n개의 소수로 반올림<br /> </td> 
   <td> Round(&lt;숫자&gt;, &lt;소수 자리수&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> 숫자 기호 반환<br /> </td> 
   <td> Sign(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> 정수를 실수로 변환<br /> </td> 
   <td> ToDouble(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> 실수를 64비트 정수로 변환<br /> </td> 
   <td> ToInt64(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> 실수를 정수로 변환<br /> </td> 
   <td> ToInteger(&lt;숫자&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> n1에서 n2까지의 소수점 자르기<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. 통화

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> 소스 통화의 금액을 대상 통화(<br />)의 금액으로 변환합니다. </td> 
   <td> ConvertCurrency(&lt;amount&gt;, &lt;원본 통화&gt;, &lt;대상 통화&gt;, &lt;전환 날짜&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatCurrency</strong><br /> </td> 
   <td> 선택한 통화 설정<br />에 따라 표시되는 금액 형식 지정 </td> 
   <td> FormatCurrency(&lt;amount&gt;, &lt;currency&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**지오마케팅**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> 위도 및 경도로 정의된 두 지점 사이의 거리를 도 단위로 반환합니다.<br /> </td> 
   <td> Distance(&lt;경도 A&gt;, &lt;위도 A&gt;, &lt;경도 B&gt;, &lt;위도 B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**기타**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> 조건이 true이면 값 1을 반환합니다. 그렇지 않으면 값 2를 반환합니다.<br /> </td> 
   <td> Case(When(&lt;조건&gt;, &lt;값 1&gt;), Else(&lt;값 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> 값에서 플래그 삭제<br /> </td> 
   <td> ClearBit(&lt;식별자&gt;, &lt;플래그&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> 값 1이 0이거나 null이면 값 2 반환, 그렇지 않으면 값 1 반환<br /> </td> 
   <td> Coalesce(&lt;값 1&gt;, &lt;값 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> 값 1이 값 2인 경우 값 3을 반환합니다. 값을 반환하지 않는 경우 4.<br /> </td> 
   <td> Decode(&lt;값 1&gt;, &lt;값 2&gt;, &lt;값 3&gt;, &lt;값 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> 값 1 반환(case 함수의 매개 변수로만 사용할 수 있음)<br /> </td> 
   <td> Else(&lt;value 1&gt;, &lt;value 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> 전자 메일 주소<br />에서 도메인을 추출합니다. </td> 
   <td> GetEmailDomain(&lt;값&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> 미러 페이지 서버의 URL 검색<br /> </td> 
   <td> GetMirrorURL(&lt;값&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> 표현식이 true이면 값 1을 반환합니다. 그렇지 않은 경우 값 2<br />을 반환합니다. </td> 
   <td> Iif(&lt;조건&gt;, &lt;값 1&gt;, &lt;값 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> 플래그가 값에 있는지 표시<br /> </td> 
   <td> IsBitSet(&lt;식별자&gt;, &lt;플래그&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> 문자열 1이 비어 있으면 값 2를 반환하고, 그렇지 않으면 값 3<br /> 값을 반환합니다. </td> 
   <td> IsEmptyString(&lt;value 1&gt;, &lt;value 2&gt;, &lt;value 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> 인수가 NULL이면 빈 문자열 반환<br /> </td> 
   <td> NoNull(&lt;값&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> 행 번호 반환<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> 값에 플래그 강제 적용<br /> </td> 
   <td> SetBit(&lt;식별자&gt;, &lt;플래그&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> 숫자를 부울로 변환<br /> </td> 
   <td> ToBoolean(&lt;숫자&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> 표현식이 true이면 값 1을 반환합니다. 그렇지 않으면 값 2를 반환합니다(case 함수의 매개 변수로만 사용할 수 있음)<br /> </td> 
   <td> When(&lt;조건&gt;, &lt;값 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**윈도우 함수**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
   <td> <strong>구문</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> 내림차순 정렬 적용<br /> </td> 
   <td> Desc(&lt;값 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> 파티션 내의 결과 정렬<br /> </td> 
   <td> OrderBy(&lt;값 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> 테이블에서 쿼리 결과 분할<br /> </td> 
   <td> PartitionBy(&lt;값 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> 테이블 파티션 및 정렬 시퀀스에 따라 행 번호 생성.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;값 1&gt;), OrderBy(&lt;값 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>