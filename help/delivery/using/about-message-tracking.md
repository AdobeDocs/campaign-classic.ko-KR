---
product: campaign
title: 추적 시작
description: Adobe Campaign에서의 추적을 위한 일반 지침 자세히 알아보기
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 2%

---

# 메시지 추적 시작 {#get-started-tracking}

>[!IMPORTANT]
>
>Campaign Classic v7 및 Campaign v8에 모두 적용되는 **일반 추적 지침**&#x200B;에 대해서는 [Campaign v8 메시지 추적 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}를 참조하세요.
>
>* [추적된 링크 구성](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [URL 추적 옵션 구성](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [개인화된 링크 추적](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [추적 로그 액세스](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [테스트 추적](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [보고서 추적](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**이 페이지에서는 주로 하이브리드 및 온-프레미스 배포에 대해 Campaign Classic v7별 추적 기능만 문서화합니다**.

## 추적 기능

### 추적 구성 {#configure-tracking}

Campaign Classic v7 **하이브리드/온-프레미스 배포**&#x200B;의 경우 사용하기 전에 인스턴스 수준에서 추적을 구성해야 합니다.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services의 경우 Adobe에서 추적 구성을 수행합니다.

**운영 원칙**

추적을 사용하기 전에 먼저 인스턴스에 대해 구성해야 합니다. Adobe Campaign 애플리케이션 서버 및 웹 서버에서 구성해야 합니다.

Campaign에는 두 가지 유형의 추적이 있습니다.

* **웹 추적**: 이 모드에서는 웹 사이트 페이지 방문 횟수를 추적할 수 있습니다.
* **메시지 추적**: 이 모드에서는 메시지 게재 및 받는 사람 동작을 추적할 수 있습니다.

설치하는 동안 추적 모드가 선택됩니다. 온-프레미스 설치의 경우 인스턴스 수준에서 추적 구성을 정의해야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#operating-principle)

**추적 서버**

추적을 구성하려면 인스턴스를 선언하고 추적 서버에 등록해야 합니다. 추적 서버는 수신자가 클릭한 URL에 대한 정보를 기록하고 검색하는 데 사용됩니다.

온-프레미스 설치의 경우 추적 서버는 일반적으로 Adobe Campaign 웹 애플리케이션을 실행하는 웹 서버입니다. 추적 서버 URL은 인스턴스 구성에 정의되어 있어야 합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#tracking-server)

**추적 저장 중**

추적이 구성되고 URL이 채워지면 추적 서버를 등록해야 합니다. 등록을 통해 Adobe Campaign은 추적 정보를 저장하고 추적된 활동에 대한 보고서와 통계를 제공할 수 있습니다.

온프레미스 설치의 경우 추적 정보는 데이터베이스에 저장되고 기술 워크플로우를 통해 검색됩니다. **추적** 기술 워크플로는 리디렉션 서버에서 수집된 추적 데이터를 처리하고 저장합니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#saving-tracking)

### 웹 애플리케이션 추적 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**웹 응용 프로그램 추적은 Campaign Classic v7에만 해당되며** Campaign v8에서는 사용할 수 없습니다.

**웹 애플리케이션 추적**

추적 태그를 사용하여 웹 애플리케이션 페이지에서 방문을 추적하고 측정할 수도 있습니다. 이 기능은 양식 및 랜딩 페이지와 같은 모든 웹 애플리케이션 유형에 사용할 수 있습니다. [자세히 알아보기](../../web/using/tracking-a-web-application.md)

**웹 애플리케이션 추적 옵트아웃**

웹 애플리케이션 추적 옵트아웃을 사용하면 행동 추적을 옵트아웃한 최종 사용자의 웹 행동 추적을 중지할 수 있습니다. 웹 애플리케이션이나 랜딩 페이지에 배너를 표시하여 사용자가 옵트아웃할 수 있도록 하는 기능을 포함할 수 있습니다. [자세히 알아보기](../../web/using/web-application-tracking-opt-out.md)

## 추적 문제 해결 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

다음 문제 해결 팁은 **Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;에 적용됩니다. 일부 정보는 Campaign v8 온-프레미스 배포에도 적용될 수 있습니다. Campaign v8 관리 클라우드 서비스의 경우 Adobe 담당자에게 지원을 요청하십시오.

Campaign v8의 기본 추적 문제 해결 단계는 Campaign v8 설명서의 [추적 문제 해결](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}을 참조하십시오.

### 기본 검사 {#basic-checks}

**trackinglogd 프로세스가 실행 중인지 확인**

이 프로세스는 IIS/웹 서버 공유 메모리를 읽고 리디렉션 로그를 기록합니다.

인스턴스의 모니터링 탭을 선택하여 홈페이지에서 액세스할 수 있습니다. 인스턴스에서 다음 명령을 실행할 수도 있습니다. `<user>@<instance>:~$ nlserver pdump`

trackinglogd 프로세스가 목록에 없으면 인스턴스에서 다음 명령을 사용하여 시작합니다. `<user>@<instance>:~$ nlserver start trackinglogd`

**추적 기술 워크플로우가 최근에 실행되고 있는지 확인**

폴더 관리 > 프로덕션 > 기술 워크플로우에서 추적 기술 워크플로우를 찾을 수 있습니다.

### 고급 문제 해결 {#advanced-troubleshooting}

+++추적 워크플로우가 실패했습니다

>[!NOTE]
>
>Windows에서만 사용 가능

손상된 추적 로그 파일 .../nl6/var/&lt;instance_name>/redir/log/0x0000 로그는 추적 워크플로우를 중지할 수 있습니다. 손상된 줄을 쉽게 감지하고 제거하여 추적 워크플로우를 다시 시작하려면 아래 명령을 사용할 수 있습니다.

**손상된 줄이 있는 파일을 알고 있습니다**

이 경우 0x00000000000A0000.log 파일에서 손상된 줄을 찾을 수 있지만 동일한 프로세스를 파일 집합에 하나씩 적용할 수 있습니다.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

그런 다음 추적 워크플로우를 중지하고 손상된 라인을 삭제한 다음 워크플로우를 다시 시작할 수 있습니다.

**손상된 줄이 어떤 파일인지 알 수 없습니다**

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

+++

+++링크 추적이 간헐적으로 실패함

추적 링크에 액세스하려고 하면 다음 메시지가 표시됩니다.

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

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

+++

+++NmsTracking_Pointer 옵션 업데이트

NmsTracking_Pointer 옵션을 업데이트할 때 다음 단계를 따르십시오.

1. 추적 워크플로우를 중지합니다.

1. trackinglogd 서비스를 중지합니다.

1. NmsTracking_Pointer 옵션을 원하는 값으로 업데이트합니다.

1. trackinglogd 서비스를 다시 시작합니다.

1. 추적 워크플로우를 다시 시작합니다.

+++

+++일부 WebMail에서는 추적이 작동하지 않습니다.

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

+++

+++추적 로그 검색이 너무 느립니다.

인스턴스가 직접 추적 로그를 검색하지 않지만 멀리 있는 Adobe Campaign Classic 서버에서 검색하는 경우 remoteTracking 스키마에 정의된 GetTrackingLogs SOAP 호출을 통해 로그가 검색됩니다.

serverConf.xml 파일의 옵션을 사용하면 logCountPerRequest 메서드를 통해 한 번에 검색되는 로그 수를 설정할 수 있습니다.

logCountPerRequest의 기본값은 1000이며, 경우에 따라 너무 작을 수 있습니다. 허용되는 값은 0과 10.000 사이여야 합니다.

+++

+++추적 로그를 수신자에게 연결할 수 없습니다.

Adobe Campaign Classic에서 대상 매핑은 수신자 스키마와 브로드로그/추적로그 스키마 측면에서 고유해야 합니다.

![](assets/tracking-troubleshooting.png)

추적 워크플로우에서는 타깃팅 ID로 데이터를 조정할 수 없으므로 동일한 추적 로그 스키마를 사용하여 여러 타깃팅 스키마를 사용할 수 없습니다.

nms:recipient과(와) 함께 기본 제공 대상 매핑을 사용하지 않으려면 다음 방법을 권장합니다.

* 사용자 지정 타겟팅 차원을 사용하려면 nms:broadlog을(를) 템플릿으로 사용하여 사용자 지정 broadLog/trackingLog 스키마를 만들어야 합니다(예: nms:broadLogRcp, nms:broadLogSvc 등).

* OOB trackingLogRcp/broadLogRcp를 사용하려면 타겟팅 차원이 nms:recipient이어야 하며 필터링 차원이 사용자 지정 스키마일 수 있습니다.

+++
