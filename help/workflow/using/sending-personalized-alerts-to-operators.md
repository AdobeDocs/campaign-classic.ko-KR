---
title: 운영자에게 개인화된 경고 보내기
description: 운영업체에 개인화된 알림 메시지 전송 방법 살펴보기
page-status-flag: never-activated
uuid: 10dd46b9-df28-4043-91f9-c9316a7c69d3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4d72db10-29bd-4b3c-adb3-bead02890271
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---


# 운영자에게 개인화된 경고 보내기{#sending-personalized-alerts-to-operators}

이 예에서는 뉴스레터를 열었지만 포함된 링크를 클릭하지 않은 프로필 이름이 포함된 연산자에 경고를 전송하려고 합니다.

프로파일의 이름과 성 필드는 타깃팅 차원에 연결된 반면, **[!UICONTROL Recipients]** 활동은 **[!UICONTROL Alert]** **[!UICONTROL Operator]** 타깃팅 차원에 연결됩니다. 따라서 조정을 수행하고 첫 번째 및 성 필드를 검색하고 경고 활동에 표시할 두 타깃팅 차원 사이에 사용할 수 있는 필드가 없습니다.

이 프로세스는 다음과 같이 워크플로우를 구축하는 것입니다.

1. 활동을 **[!UICONTROL Query]** 사용하여 데이터를 타깃팅합니다.
1. 워크플로우에 **[!UICONTROL JavaScript code]** 활동을 추가하여 질의의 모집단을 인스턴스 변수에 저장합니다.
1. 활동을 **[!UICONTROL Test]** 사용하여 인구 수를 확인합니다.
1. 활동 결과에 따라 **[!UICONTROL Alert]** 활동을 사용하여 **[!UICONTROL Test]** 연산자에게 경고를 전송합니다.

![](assets/uc_operator_1.png)

## 인스턴스 변수에 채우기 {#saving-the-population-to-the-instance-variable}

아래 코드를 활동에 **[!UICONTROL JavaScript code]** 추가합니다.

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

* 태그는 **[!UICONTROL queryDef schema]** 쿼리 활동에 사용되는 타깃팅 차원의 이름에 해당됩니다.
* 태그는 **[!UICONTROL node expr]** 검색할 필드의 이름에 해당됩니다.

![](assets/uc_operator_3.png)

이러한 정보를 검색하려면 아래 단계를 수행하십시오.

1. 활동에서 아웃바운드 전환 **[!UICONTROL Query]** 을 마우스 오른쪽 단추로 클릭한 다음 선택합니다 **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. 목록을 마우스 오른쪽 단추로 클릭한 다음 선택합니다 **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. 쿼리 타깃팅 차원 및 필드 이름이 목록에 표시됩니다.

   ![](assets/uc_operator_6.png)

## 모집단 수 테스트 {#testing-the-population-count}

아래 코드를 **[!UICONTROL Test]** 활동에 추가하여 타깃팅된 모집단에 하나 이상의 프로필이 포함되어 있는지 확인합니다.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 경고 설정 {#setting-up-the-alert}

원하는 필드가 있는 인스턴스 변수에 모집단 이 추가되었으므로 이 정보를 활동에 추가할 수 **[!UICONTROL Alert]** 있습니다.

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
>이 **[!UICONTROL <%= item.target.recipient.@fieldName %>]** 명령을 사용하면 활동을 통해 인스턴스 변수에 저장된 필드 중 하나를 추가할 수 **[!UICONTROL JavaScript code]** 있습니다.\
>JavaScript 코드에 삽입된 필드를 원하는 만큼 추가할 수 있습니다.

![](assets/uc_operator_8.png)

