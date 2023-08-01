---
product: campaign
title: SOAP를 통한 통합(서버측)
description: SOAP를 통한 통합(서버측)
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 4%

---

# SOAP를 통한 통합(서버측){#integration-via-soap-server-side}



오퍼 관리에 제공되는 SOAP 웹 서비스는 Adobe Campaign에서 일반적으로 사용되는 서비스와 다릅니다. 이전 섹션에 설명된 상호 작용 URL을 통해 액세스할 수 있으며, 지정된 연락처에 대한 오퍼를 제시하거나 업데이트할 수 있습니다.

## 오퍼 제안 {#offer-proposition}

SOAP를 통한 오퍼 제안에 대해 **nms:proposition#제안** 명령 뒤에 다음 매개 변수가 옵니다.

* **targetId**: 수신자의 기본 키(복합 키일 수 있음).
* **maxCount**: 연락처에 대한 오퍼 제안 수를 지정합니다.
* **컨텍스트**: 공간 스키마에 컨텍스트 정보를 추가할 수 있습니다. 사용된 스키마가 **nms:interaction**, **`<empty>`** 을 추가해야 합니다.
* **카테고리**: 오퍼가 속해야 하는 범주/코드를 지정합니다.
* **테마**: 오퍼가 속해야 하는 테마를 지정합니다.
* **uuid**: Adobe Campaign 영구 쿠키의 값(&quot;uuid230&quot;).
* **nli**: Adobe Campaign 세션 쿠키의 값(&quot;nlid&quot;)입니다.
* **noProp**: &quot;true&quot; 값을 사용하여 제안 삽입을 비활성화합니다.

>[!NOTE]
>
>다음 **targetId** 및 **maxCount** 설정은 필수입니다. 다른 것들은 선택 사항입니다.

쿼리에 대한 응답으로 SOAP 서비스는 다음 매개 변수를 반환합니다.

* **interactionId**: 인터랙션의 ID입니다.
* **제안**: XML 요소이며, 각각 고유한 ID와 HTML 표현이 있는 제안 목록을 포함합니다.

## 오퍼 업데이트 {#offer-update}

추가 **nms:interaction#UpdateStatus** 다음 매개 변수가 뒤에 옵니다.

* **제안**: 문자열로 구성되며 오퍼 제안 중 출력으로 제공된 제안 ID를 포함합니다. 을(를) 참조하십시오 [오퍼 제안](#offer-proposition).
* **상태**: 문자열 유형으로 오퍼의 새 상태를 지정합니다. 가능한 값은 **제안 상태** 열거형, **nms:common** 스키마. 예를 들어, 기본적으로 숫자 3은 **수락됨** 상태.
* **컨텍스트**: XML 요소를 사용하여 공간 스키마에 컨텍스트 정보를 추가할 수 있습니다. 사용된 스키마가 **nms:interaction**, **`<empty>`** 을 추가해야 합니다.

## SOAP 호출 사용 예 {#example-using-a-soap-call}

다음은 SOAP 호출에 대한 코드의 예입니다.

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
