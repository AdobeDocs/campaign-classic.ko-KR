---
title: 조건부 컨텐츠
seo-title: 조건부 컨텐츠
description: 조건부 컨텐츠
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# 조건부 컨텐츠{#conditional-content}

조건부 컨텐츠 필드를 구성하면 수신자의 프로파일을 기반으로 동적 개인화를 만들 수 있습니다. 특정 조건이 충족되면 텍스트 블록 및/또는 이미지가 교체됩니다.

## 이메일의 조건 사용 {#using-conditions-in-an-email}

아래 예에서는 수신자의 성별 및 관심사에 따라 동적으로 개인화된 메시지를 만드는 방법을 알아봅니다.

* &quot;Mr.&quot; 표시 표시 또는 &quot;Ms&quot; 데이터 소스의 **[!UICONTROL Gender]** 필드 값(M 또는 F)에 따라
* 표시되거나 감지된 관심사에 따라 뉴스레터 또는 홍보 행사의 개인화된 집합입니다.

   * 관심 영역 1 — > 블록 1
   * 관심 영역 2 — > 블록 2
   * 관심 항목 3 — > 블록 3
   * 관심 영역 4 — > 블록 4

필드의 값에 따라 조건부 컨텐츠를 만들려면 다음 단계를 적용합니다.

1. 개인화 아이콘을 클릭하고 **[!UICONTROL Conditional content > If]**&#x200B;선택합니다.

   ![](assets/s_ncs_user_conditional_content02.png)

   개인화 요소가 메시지 본문에 삽입됩니다. 이제 구성해야 합니다.

1. 그런 다음 **if** 식의 매개 변수를 채웁니다.

   이렇게 하려면:

   * 표현식의 첫 번째 요소를 **`<field>`**&#x200B;선택하고(기본적으로 **if** 표현식을 삽입하는 동안 이 요소가 강조 표시됨) 개인화 아이콘을 클릭하여 테스트 필드로 대체합니다.

      ![](assets/s_ncs_user_conditional_content03.png)

   * 조건이 충족될 필드의 값으로 **`<value>`** 대체합니다. 이 값은 따옴표로 묶어야 합니다.
   * 조건이 충족될 때 삽입할 컨텐츠를 지정합니다. 텍스트, 이미지, 양식, 하이퍼텍스트 링크 등으로 구성될 수 있습니다.

      ![](assets/s_ncs_user_conditional_content04.png)

1. 전달 받는 사람에 따라 메시지 내용을 보려면 **[!UICONTROL Preview]** 탭을 클릭합니다.

   * 조건이 참인 수신자 선택:

      ![](assets/s_ncs_user_conditional_content05.png)

   * 조건이 true가 아닌 받는 사람 선택:

      ![](assets/s_ncs_user_conditional_content06.png)

다른 케이스를 추가하고 하나 이상의 필드의 값에 따라 다른 컨텐츠를 정의할 수 있습니다. 이렇게 하려면 **[!UICONTROL Conditional content > Else]** and를 **[!UICONTROL Conditional content > Else if]**&#x200B;사용하십시오. 이러한 표현식은 **if** 표현식과 동일한 방식으로 구성됩니다.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>JavaScript 구문을 존중하려면 **%> &lt;%** 문자를 Else 및 if **조건을 추가한** 후 **삭제해야** 합니다.

조건부 컨텐츠를 보려면 수신자를 **[!UICONTROL Preview]** 클릭하고 선택합니다.

![](assets/s_ncs_user_conditional_content08.png)

## 다국어 이메일 제작 {#creating-multilingual-email}

아래 예에서는 다국어 이메일을 만드는 방법을 알아봅니다. 컨텐츠는 받는 사람의 기본 언어에 따라 한 언어 또는 다른 언어로 표시됩니다.

1. 이메일을 만들고 타겟 모집단을 선택합니다. 이 예에서는 한 버전 또는 다른 버전을 표시하는 조건이 **수신자** 프로필의 언어 값을 기반으로 합니다. 이 예에서 이러한 값은 EN, **FR**, **ES**&#x200B;로 **설정됩니다**.
1. 이메일 HTML 내용에서 **[!UICONTROL Source]** 탭을 클릭하고 다음 코드를 붙여 넣습니다.

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. 다른 기본 언어로 받는 사람을 선택하여 **[!UICONTROL Preview]** 탭에서 이메일 컨텐츠를 테스트합니다.

   >[!NOTE]
   >
   >이메일 컨텐츠에 다른 버전이 정의되지 않았으므로 이메일을 보내기 전에 타겟 모집단을 필터링해야 합니다.
