---
product: campaign
title: 운영자에게 개인화된 경고 보내기
description: 운영자에게 개인화된 경고를 보내는 방법 알아보기
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# 운영자에게 개인화된 경고 보내기{#sending-personalized-alerts-to-operators}



이 예제에서는 뉴스레터를 열었지만 포함된 링크를 클릭하지 않은 프로필의 이름이 포함된 운영자에게 경고를 보내려고 합니다.

프로필의 이름과 성 필드는 **[!UICONTROL Recipients]** 타겟팅 차원에 연결되어 있지만, **[!UICONTROL Alert]** 활동은 **[!UICONTROL Operator]** 타겟팅 차원에 연결되어 있습니다. 따라서 두 타겟팅 차원 간에는 조정을 수행하고 이름 및 성 필드를 검색하여 경고 활동에 표시하는 데 사용할 수 있는 필드가 없습니다.

프로세스는 다음과 같이 워크플로우를 빌드합니다.

1. 데이터를 타깃팅하려면 **[!UICONTROL Query]** 활동을 사용하십시오.
1. 워크플로우에 **[!UICONTROL JavaScript code]** 활동을 추가하여 쿼리의 모집단을 인스턴스 변수에 저장합니다.
1. **[!UICONTROL Test]** 활동을 사용하여 모집단 수를 확인합니다.
1. **[!UICONTROL Test]** 활동 결과에 따라 **[!UICONTROL Alert]** 활동을 사용하여 운영자에게 경고를 보냅니다.

![](assets/uc_operator_1.png)

## 인스턴스 변수에 모집단 저장 {#saving-the-population-to-the-instance-variable}

**[!UICONTROL JavaScript code]** 활동에 아래 코드를 추가하십시오.

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

* **[!UICONTROL queryDef schema]** 태그는 쿼리 활동에 사용된 타겟팅 차원의 이름과 일치해야 합니다.
* **[!UICONTROL node expr]** 태그는 검색할 필드의 이름과 일치해야 합니다.

![](assets/uc_operator_3.png)

이러한 정보를 검색하려면 아래 단계를 수행합니다.

1. **[!UICONTROL Query]** 활동에서 아웃바운드 전환을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL Display the target]**&#x200B;을(를) 선택합니다.

   ![](assets/uc_operator_4.png)

1. 목록을 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL Configure list]**&#x200B;을(를) 선택합니다.

   ![](assets/uc_operator_5.png)

1. 쿼리 타겟팅 차원 및 필드 이름이 목록에 표시됩니다.

   ![](assets/uc_operator_6.png)

## 모집단 수 테스트 {#testing-the-population-count}

아래의 코드를 **[!UICONTROL Test]** 활동에 추가하여 타겟팅된 모집단에 하나 이상의 프로필이 포함되어 있는지 확인하십시오.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 경고 설정 {#setting-up-the-alert}

모집단을 원하는 필드가 있는 인스턴스 변수에 추가했으므로 이러한 정보를 **[!UICONTROL Alert]** 활동에 추가할 수 있습니다.

이렇게 하려면 **[!UICONTROL Source]** 탭에 아래 코드를 추가하십시오.

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
>JavaScript 코드에 삽입된 필드만 원하는 만큼 추가할 수 있습니다.

![](assets/uc_operator_8.png)
