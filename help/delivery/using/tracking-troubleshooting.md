---
solution: Campaign Classic
product: campaign
title: 추적 문제 해결
description: 이 섹션에서는 Adobe Campaign Classic의 추적 구성 및 구현과 관련된 일반적인 질문을 제공합니다.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: efa36dc08ce4dd59805bb9eba63a4249e14609d7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# 추적 문제 해결 {#tracking-troubleshooting}

이 섹션에서는 Adobe Campaign Classic의 구성 및 구현 추적 관련 일반적인 질문을 확인할 수 있습니다.

## 추적 워크플로에서 {#tracking-workflow-failing}에 실패했습니다.

추적 워크플로가 실패하여 추적 파일에서 손상된 줄을 어떻게 감지할 수 있습니까?

>[!NOTE]
>
>Windows에만 사용 가능

손상된 추적 로그 파일.../nl6/var/&lt;instance_name>/redir/log/0x0000 로그는 추적 작업 과정을 중지할 수 있습니다. 손상된 행을 쉽게 감지하고 제거하여 추적 워크플로우를 다시 시작하려면 아래 명령을 사용할 수 있습니다.

### 나는 어떤 파일이 손상된 줄을 알고 있다

이 경우 손상된 줄은 0x00000000000A00000.log 파일에서 찾을 수 있지만 동일한 프로세스를 파일 집합에 적용할 수 있습니다(하나씩).

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

그런 다음 추적 워크플로우를 중지하고, 손상된 줄을 삭제하고, 워크플로우를 다시 시작할 수 있습니다.

### 이제 손상된 줄이 있는 파일이 없습니다.

1. 다음 명령줄을 사용하여 모든 추적 파일을 체크 인합니다.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. 명령은 손상된 모든 줄을 나열합니다. 예제:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >사용자 에이전트 이전에 캐리지 리턴이 추가되어 더 나은 읽기를 허용했으며 효과적인 렌더링을 반영하지 않습니다.

1. grep 명령을 실행하여 해당 파일을 찾습니다.

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. 파일 이름 및 행 번호를 사용하여 잘못된 로그를 찾습니다. 예제:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >사용자 에이전트 이전에 캐리지 리턴이 추가되어 더 나은 읽기를 허용했으며 효과적인 렌더링을 반영하지 않습니다.

그런 다음 추적 워크플로우를 중지하고, 손상된 줄을 삭제하고, 워크플로우를 다시 시작할 수 있습니다.

## 간헐적으로 링크 추적 실패 {#tracking-links-fail-intermittently}

추적 링크에 액세스하려고 하면 다음 메시지가 표시됩니다.

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. &lt;redirection_server>/r/test URL에 액세스하고 요청이 빌드 번호 및 localhost를 반환했는지 확인합니다.

1. 추적 서버에 대한 serverConf.xml 파일의 spareServer 구성을 확인합니다. 이 구성은 리디렉션 모드여야 합니다.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. &lt;deliveryID>.xml 파일이 ...의 컴퓨터에 있는지 수동으로 확인합니다./nl6/var/&lt;instance_name>/redir/url/&lt;YYYY> 디렉토리(YYYY는 배달 연도를 나타냅니다).

1. &lt;deliveryID>.xml 파일에서 &lt;trackingUrlId>를 찾을 수 있는지 여부를 수동으로 확인합니다.

1. 관련 deliveryID 전달에 broadlogID가 수동으로 있는지 확인합니다.

1. 에서 &lt;deliveryID>.xml 파일 권한을 확인하십시오../nl6/var/&lt;instance_name>/redir/url/year 디렉토리입니다.

   Apache가 요청된 링크를 리디렉션하기 위해 추적 URL을 읽을 수 있도록 644 이상의 권한이 있어야 합니다.

## NmsTracking_Pointer 옵션을 업데이트하시겠습니까?{#updating-option}

NmsTracking_Pointer 옵션을 업데이트할 때는 다음 단계를 수행합니다.

1. 추적 작업 과정을 중지합니다.

1. 추적 로그 서비스를 중지합니다.

1. NmsTracking_Pointer 옵션을 원하는 값으로 업데이트합니다.

1. trackinglogd 서비스를 다시 시작합니다.

1. 추적 작업 과정을 다시 시작합니다.

## 일부 WebMail {#webmail}에서는 추적이 작동하지 않는 것 같습니다.

클릭 추적 공식을 사용자 정의하고 사용자 지정 Adobe Analytics 추적 공식을 지정할 수 있습니다.

이러한 종류의 사용자 지정은 추가적으로 줄 바꿈 문자를 추가하지 않도록 주의해서 수행해야 합니다. javascript 표현식 외부에 있는 모든 줄 바꿈 문자가 최종 공식에 표시됩니다.

추적 URL에서 이러한 종류의 추가 줄 바꿈 문자는 일부 webMail(AOL, GMail 등)에서 발행됩니다.

**첫 번째 예:**

* 잘못된 구문

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>
   &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

* 올바른 구문

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {
   %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
   ```

추가 줄 바꿈 위치를 이해하려면 javascript 표현식을 고정 문자열 STRING으로 바꿀 수 있습니다.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**두 번째 예**

* 잘못된 구문

   ```
   <%@ include option='NmsTracking_ClickFormula' %>
   <% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

* 올바른 구문

   ```
   <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe-Genesis
   var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
   if( $(urlstring).match(pattern) && delivery.FCP == false )
   {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
   
   %>
   ```

추가 줄 바꿈 위치를 이해하려면 javascript 표현식을 고정 문자열 STRING으로 바꿀 수 있습니다.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## 추적 로그 검색이 너무 느립니다 {#slow-retrieval}.

인스턴스가 직접 추적 로그를 검색하지 않지만 멀리 떨어져 있는 Adobe Campaign Classic 서버에서는 remoteTracking 스키마에 정의된 GetTrackingLogs SOAP 호출을 통해 로그가 검색됩니다.

serverConf.xml 파일의 옵션을 사용하면 이 방법을 통해 한 번에 검색되는 로그 수를 설정할 수 있습니다.logCountPerRequest를 참조하십시오.

logCountPerRequest의 기본값은 1000입니다. 일부 경우 너무 작다는 것이 입증될 수 있습니다. 허용된 값은 0에서 10.000 사이여야 합니다.

## 추적 로그를 받는 사람 {#link-recipients}에 연결할 수 없습니다.

Adobe Campaign Classic에서 대상 매핑은 받는 사람 스키마와 브로드로그/trackinglog 스키마 사이의 용어로 고유해야 합니다.

![](assets/tracking-troubleshooting.png)

추적 워크플로에서는 타깃팅 ID로 데이터를 조정할 수 없으므로 동일한 추적 로그 스키마의 여러 타깃팅 스키마를 사용할 수 없습니다.

nms:recipient와 함께 즉시 사용 가능한 대상 매핑을 사용하지 않으려면 다음 방법을 사용하는 것이 좋습니다.

* 사용자 지정 타깃팅 차원을 사용하려면 nms:broadlog를 템플릿으로 사용하여 사용자 정의 broadLog/trackingLog 스키마를 만들어야 합니다(예: nms:broadLogRcp, nms:broadLogSvc 등).

* OOB trackingLogRcp/broadLogRcp를 사용하려면 타깃팅 차원이 nms:recipient여야 하며 필터링 차원은 사용자 지정 스키마일 수 있습니다.
