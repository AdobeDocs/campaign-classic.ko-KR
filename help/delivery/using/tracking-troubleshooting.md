---
product: campaign
title: 추적 문제 해결
description: 이 섹션에서는 Adobe Campaign의 구성 및 구현 추적과 관련된 일반적인 질문을 제공합니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Monitoring, Troubleshooting
role: User
exl-id: 62e67a39-1e5c-4716-a3f3-b0ca69693cd0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 1%

---

# 추적 문제 해결 {#tracking-troubleshooting}

이 섹션에서는 Adobe Campaign Classic의 추적 구성 및 구현과 관련된 일반적인 질문에 대해 설명합니다.

## 추적 워크플로우가 실패했습니다 {#tracking-workflow-failing}

추적 워크플로우가 실패했습니다. 추적 파일에서 손상된 줄을 검색하려면 어떻게 합니까?

>[!NOTE]
>
>Windows에서만 사용 가능

손상된 추적 로그 파일 .../nl6/var/&lt;instance_name>/redir/log/0x0000 로그는 추적 워크플로우를 중지할 수 있습니다. 손상된 줄을 쉽게 감지하고 제거하여 추적 워크플로우를 다시 시작하려면 아래 명령을 사용할 수 있습니다.

### 손상된 줄이 어떤 파일인지 알 수 있습니다.

이 경우 0x00000000000A0000.log 파일에서 손상된 줄을 찾을 수 있지만 동일한 프로세스를 파일 집합에 하나씩 적용할 수 있습니다.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

그런 다음 추적 워크플로우를 중지하고 손상된 라인을 삭제한 다음 워크플로우를 다시 시작할 수 있습니다.

### 손상된 줄이 있는 파일이 없습니다.

1. 다음 명령줄을 사용하여 모든 추적 파일을 체크 인합니다.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. 이 명령은 손상된 모든 줄을 나열합니다. 예제:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >보다 나은 읽기를 위해 사용자 에이전트 앞에 캐리지 리턴이 추가되었으며 효과적인 렌더링을 반영하지 않습니다.

1. grep 명령을 실행하여 해당 파일을 찾습니다.

```
$ grep -Rn <Log Id>
# for example:
$ grep -Rn 50x000000000FD7EC86
```

1. 파일 이름과 줄 번호가 있는 잘못된 로그를 찾습니다. 예제:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >보다 나은 읽기를 위해 사용자 에이전트 앞에 캐리지 리턴이 추가되었으며 효과적인 렌더링을 반영하지 않습니다.

그런 다음 추적 워크플로우를 중지하고 손상된 라인을 삭제한 다음 워크플로우를 다시 시작할 수 있습니다.

## 링크 추적이 간헐적으로 실패함 {#tracking-links-fail-intermittently}

추적 링크에 액세스하려고 하면 다음 메시지가 표시됩니다.

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&amp;p1=1' cannot be found`

1. &lt;redirection_server>/r/test URL에 액세스하여 요청이 빌드 번호 및 localhost를 반환했는지 확인합니다.

1. serverConf.xml 파일에서 추적 서버에 대한 spareServer 구성을 확인합니다. 이 구성은 리디렉션 모드여야 합니다.

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

1. ../nl6/var/&lt;instance_name>/redir/url/&lt;YYYY> 디렉터리의 시스템에 &lt;deliveryID>.xml 파일이 있는지 수동으로 확인합니다(YYYY는 배달 연도를 나타냄).

1. &lt;deliveryID>.xml 파일에서 &lt;trackingUrlId>을(를) 찾을 수 있는지 수동으로 확인하십시오.

1. 관련된 deliveryID 게재에 broadlogID가 수동으로 있는지 확인하십시오.

1. ../nl6/var/&lt;instance_name>/redir/url/year 디렉토리에서 &lt;deliveryID>.xml 파일 권한을 확인합니다.

   Apache가 요청된 링크를 리디렉션하기 위해 추적 URL을 읽을 수 있도록 최소 644 권한이 있어야 합니다.

## NmsTracking_Pointer 옵션을 업데이트하시겠습니까? {#updating-option}

NmsTracking_Pointer 옵션을 업데이트할 때 다음 단계를 따르십시오.

1. 추적 워크플로우를 중지합니다.

1. trackinglogd 서비스를 중지합니다.

1. NmsTracking_Pointer 옵션을 원하는 값으로 업데이트합니다.

1. trackinglogd 서비스를 다시 시작합니다.

1. 추적 워크플로우를 다시 시작합니다.

## 일부 WebMail에서는 추적이 작동하지 않는 것 같습니다. {#webmail}

클릭 추적 공식을 맞춤화하고 사용자 지정 Adobe Analytics 추적 공식을 지정할 수 있습니다.

이러한 종류의 사용자 지정은 추가 줄 바꿈 문자를 추가하지 않도록 주의하여 수행해야 합니다. JavaScript 표현식 외부에 있는 모든 줄 바꿈 문자는 최종 수식에 표시됩니다.

추적 URL에 있는 이러한 종류의 추가 줄 바꿈 문자는 일부 웹 메일(AOL, GMail 등)에서 문제를 일으킵니다.

**첫 번째 예:**

* 잘못된 구문

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* 올바른 구문

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

추가 줄 바꿈이 있는 위치를 이해하기 위해 JavaScript 표현식을 고정 문자열 STRING으로 바꿀 수 있습니다.

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
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* 올바른 구문

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

추가 줄 바꿈이 있는 위치를 이해하기 위해 JavaScript 표현식을 고정 문자열 STRING으로 바꿀 수 있습니다.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

## 추적 로그 검색이 너무 느립니다. {#slow-retrieval}

인스턴스가 직접 추적 로그를 검색하지 않지만 멀리 있는 Adobe Campaign Classic 서버에서 검색하는 경우 remoteTracking 스키마에 정의된 GetTrackingLogs SOAP 호출을 통해 로그가 검색됩니다.

serverConf.xml 파일의 옵션을 사용하면 logCountPerRequest 메서드를 통해 한 번에 검색되는 로그 수를 설정할 수 있습니다.

logCountPerRequest의 기본값은 1000이며, 경우에 따라 너무 작을 수 있습니다. 허용되는 값은 0과 10.000 사이여야 합니다.

## 추적 로그를 수신자에게 연결할 수 없습니다. {#link-recipients}

Adobe Campaign Classic에서 대상 매핑은 수신자 스키마와 브로드로그/추적로그 스키마 측면에서 고유해야 합니다.

![](assets/tracking-troubleshooting.png)

추적 워크플로우에서는 타깃팅 ID로 데이터를 조정할 수 없으므로 동일한 추적 로그 스키마를 사용하여 여러 타깃팅 스키마를 사용할 수 없습니다.

nms:recipient와 함께 기본 제공 대상 매핑을 사용하지 않으려면 다음 접근 방식을 권장합니다.

* 사용자 지정 타겟팅 차원을 사용하려면 nms:broadlog를 템플릿으로 사용하여 사용자 지정 broadLog/trackingLog 스키마를 만들어야 합니다(예: nms:broadLogRcp, nms:broadLogSvc 등).

* OOB trackingLogRcp/broadLogRcp를 사용하려면 타겟팅 차원이 nms:recipient 이고 필터링 차원은 사용자 지정 스키마일 수 있습니다.
