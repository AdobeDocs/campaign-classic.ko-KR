---
product: campaign
title: SOAP를 통한 통합(서버측)
description: SOAP를 통한 통합(서버측)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 3%

---

# SOAP를 통한 통합(서버측){#integration-via-soap-server-side}

![](../../assets/v7-only.svg)

오퍼 관리를 위해 제공된 SOAP 웹 서비스는 일반적으로 Adobe Campaign에서 사용되는 서비스와 다릅니다. 이전 섹션에 설명된 상호 작용 URL을 통해 액세스할 수 있으며 특정 연락처에 대한 오퍼를 표시하거나 업데이트할 수 있습니다.

## 오퍼 제안 {#offer-proposition}

SOAP를 통해 오퍼 제안을 위해 를 추가합니다. **nms:제안#제안** 명령 뒤에 다음 매개 변수가 옵니다.

* **targetId**: 수신자의 기본 키(복합 키일 수 있음).
* **maxCount**: 연락처에 대한 오퍼 제안 수를 지정합니다.
* **컨텍스트**: 공간 스키마에 컨텍스트 정보를 추가할 수 있습니다. 사용된 스키마가 **nms:상호 작용**, **`<empty>`** 를 추가해야 합니다.
* **카테고리**: 오퍼가 속해야 하는 카테고리를 지정합니다.
* **테마**: 오퍼가 속해야 하는 테마를 지정합니다.
* **uuid**: Adobe Campaign 영구 쿠키의 값(&quot;uuid230&quot;).
* **nli**: Adobe Campaign 세션 쿠키의 값(&quot;nlid&quot;).
* **noProp**: 제안 삽입을 비활성화하려면 &quot;true&quot; 값을 사용합니다.

>[!NOTE]
>
>다음 **targetId** 및 **maxCount** 설정은 필수입니다. 다른 항목은 선택 사항입니다.

쿼리에 응답하여 SOAP 서비스는 다음 매개 변수를 반환합니다.

* **interactionId**: 상호 작용 ID입니다.
* **포지션**: XML 요소에는 각각 고유한 ID 및 HTML 표현이 있는 proposition 목록이 포함되어 있습니다.

## 오퍼 업데이트 {#offer-update}

추가 **nms:interaction#UpdateStatus** 명령을 클릭하고 다음 매개 변수를 추가합니다.

* **제안**: 문자 문자열에는 오퍼 제안 중에 출력으로 제공되는 제안 ID가 포함되어 있습니다. 을(를) 참조하십시오. [오퍼 제안](#offer-proposition).
* **상태**: 문자열 유형으로, 오퍼의 새 상태를 지정합니다. 가능한 값은 **propStatus** 열거형, **nms:공통** 스키마. 예를 들어, 기본적으로 3은 **수락됨** 상태.
* **컨텍스트**: XML 요소를 사용하면 공간 스키마에 컨텍스트 정보를 추가할 수 있습니다. 사용된 스키마가 **nms:상호 작용**, **`<empty>`** 를 추가해야 합니다.

## SOAP 호출 사용 예 {#example-using-a-soap-call}

다음은 SOAP 호출에 대한 코드 예입니다.

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
