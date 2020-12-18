---
solution: Campaign Classic
product: campaign
title: 운영자에게 개인화된 경고 보내기
description: 운영자에게 개인화된 경고를 보내는 방법 살펴보기
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---


# 운영자에게 개인화된 경고 보내기{#sending-personalized-alerts-to-operators}

이 예에서는 뉴스레터를 열었지만 포함된 링크를 클릭하지 않은 프로필 이름이 포함된 연산자에 경고를 전송하려고 합니다.

프로필의 이름 필드와 성 필드는 **[!UICONTROL Recipients]** 타깃팅 차원에 연결되어 있는 반면 **[!UICONTROL Alert]** 활동은 **[!UICONTROL Operator]** 타깃팅 차원에 연결됩니다. 따라서 조정을 수행하고 첫 번째 및 성 필드를 검색하고 경고 활동에 표시할 두 타깃팅 차원 사이에 사용할 수 있는 필드가 없습니다.

이 프로세스는 다음과 같이 워크플로우를 구축하는 것입니다.

1. 데이터를 타깃팅하려면 **[!UICONTROL Query]** 활동을 사용합니다.
1. 워크플로우에 **[!UICONTROL JavaScript code]** 활동을 추가하여 쿼리 양식을 인스턴스 변수에 저장합니다.
1. **[!UICONTROL Test]** 활동을 사용하여 인구 수를 확인합니다.
1. **[!UICONTROL Test]** 활동 결과에 따라 **[!UICONTROL Alert]** 활동을 사용하여 연산자에게 경고를 보냅니다.

![](assets/uc_operator_1.png)

## 인구를 인스턴스 변수 {#saving-the-population-to-the-instance-variable}에 저장

아래 코드를 **[!UICONTROL JavaScript code]** 활동에 추가합니다.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Javascript 코드가 워크플로우 정보에 해당하는지 확인합니다.

* **[!UICONTROL queryDef schema]** 태그는 쿼리 활동에 사용되는 타깃팅 차원의 이름에 해당해야 합니다.
* **[!UICONTROL node expr]** 태그는 검색할 필드의 이름에 해당해야 합니다.

![](assets/uc_operator_3.png)

이러한 정보를 검색하려면 아래 단계를 따르십시오.

1. **[!UICONTROL Query]** 활동에서 아웃바운드 전환을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL Display the target]** 을 선택합니다.

   ![](assets/uc_operator_4.png)

1. 목록을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL Configure list]**&#x200B;을 선택합니다.

   ![](assets/uc_operator_5.png)

1. 쿼리 타깃팅 차원 및 필드 이름이 목록에 표시됩니다.

   ![](assets/uc_operator_6.png)

## 인구 수 테스트{#testing-the-population-count}

아래 코드를 **[!UICONTROL Test]** 활동에 추가하여 타깃팅된 모집단에 프로필이 하나 이상 포함되어 있는지 확인합니다.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 경고 {#setting-up-the-alert} 설정

모집단 이 원하는 필드가 있는 인스턴스 변수에 추가되었으므로 이러한 정보를 **[!UICONTROL Alert]** 활동에 추가할 수 있습니다.

이렇게 하려면 아래 코드를 **[!UICONTROL Source]** 탭에 추가하십시오.

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>**[!UICONTROL <%= item.target.recipient.@fieldName %>]** 명령을 사용하면 **[!UICONTROL JavaScript code]** 활동을 통해 인스턴스 변수에 저장된 필드 중 하나를 추가할 수 있습니다.\
>JavaScript 코드에 삽입된 한 원하는 만큼 필드를 추가할 수 있습니다.

![](assets/uc_operator_8.png)

