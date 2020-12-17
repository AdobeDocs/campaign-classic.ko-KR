---
solution: Campaign Classic
product: campaign
title: 파이프라인 구성
description: 파이프라인 구성 방법 알아보기
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 7353abfe07bc177d103c83c7f2a5d57d7fb415a3
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 1%

---


# 파이프라인 구성 {#configuring-pipeline}

고객 ID, 개인 키 및 인증 끝점과 같은 인증 매개 변수가 인스턴스 구성 파일에 구성됩니다.
처리할 트리거 목록은 JSON 형식의 옵션으로 구성됩니다.
트리거는 이메일을 보내는 캠페인 워크플로에 의한 타깃팅에 사용됩니다. 두 개의 트리거 이벤트가 있는 고객이 이메일을 받을 수 있도록 캠페인이 설정됩니다.

>[!CAUTION]
>
>하이브리드 배포의 경우 파이프라인이 중간 인스턴스에 구성되어 있는지 확인합니다.

## 사전 요구 사항 {#prerequisites}

이 구성을 시작하기 전에 다음을 사용 중인지 확인하십시오.

* Adobe Campaign 20.3 또는 Gold Standard 11 릴리스 최소
* Adobe Analytics Standard 버전

또한 다음 작업이 필요합니다.

* Adobe I/O 프로젝트 인증
* 유효한 IMSOrgID, Adobe Analytics이 있는 Experience Cloud 고객의 ID가 추가됨
* IMS 조직에 대한 개발자 액세스
* adobe analytics에서 수행한 트리거 구성

## 인증 및 구성 파일 {#authentication-configuration}

파이프라인이 Adobe Experience Cloud에서 호스팅되므로 인증이 필요합니다.
공개 키와 개인 키를 사용합니다. 이 프로세스는 사용자/암호와 동일한 기능을 갖지만 보안이 강화되었습니다.
Adobe I/O 프로젝트를 통해 Marketing Cloud에 대한 인증이 지원됩니다.

## 1단계:Adobe I/O 프로젝트 {#creating-adobe-io-project} 만들기/업데이트

호스팅 고객의 경우 고객 지원 티켓을 만들어 트리거 통합을 위해 Adobe I/O 기술 계정 토큰으로 조직에서 사용할 수 있도록 할 수 있습니다.

온-프레미스 고객은 [Adobe Experience Cloud 트리거에 대해 Adobe I/O 구성](../../integrations/using/configuring-adobe-io.md) 페이지를 참조하십시오. Adobe I/O 자격 증명에 API를 추가하는 동안 **[!UICONTROL Adobe Analytics]**&#x200B;을 선택해야 합니다.

## 2단계:NmsPipeline_Config 파이프라인 구성 옵션 {#configuring-nmspipeline}

인증이 설정되면 파이프라인이 이벤트를 검색합니다. Adobe Campaign에 구성된 트리거를 처리합니다. 트리거가 Adobe Analytics에서 생성되어 파이프라인으로 푸시되어 Adobe Campaign에 구성된 트리거를 처리합니다.
이름에 상관없이 모든 트리거를 catch하기 위해 이 옵션을 와일드카드로 구성할 수도 있습니다.

1. Adobe Campaign에서 **[!UICONTROL Explorer]**&#x200B;의 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 아래의 옵션 메뉴에 액세스합니다.

1. **[!UICONTROL NmsPipeline_Config]** 옵션을 선택합니다.

1. **[!UICONTROL Value (long text)]** 필드에서 다음 JSON 코드를 붙여넣을 수 있습니다. 이 코드는 두 개의 트리거를 지정합니다. 주석을 제거해야 합니다.

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
           "triggers": [ // Array of triggers.
               {
                   "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                   "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
               }, {
                   "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                   "jsConnector": "cus:triggers.js" // Can use the same JS for all.
               },
           ]
       }
   ]
   }
   ```

1. 모든 트리거를 포함하는 다음 JSON 코드를 붙여넣을 수도 있습니다.

   ```
   {
   "topics": [
     {
       "name": "triggers",
       "consumer":  "customer_dev",
       "triggers": [
         {
           "name": "*",
           "jsConnector": "cus:pipeline.js"
         }
       ]
     }
   ]
   }
   ```

### 소비자 매개 변수 {#consumer-parameter}

파이프라인은 공급자와 소비자 모델처럼 작동합니다. 메시지는 개별 소비자에 대해서만 사용됩니다.각 소비자는 고유한 메시지 사본을 받습니다.

**Consumer** 매개 변수는 인스턴스를 이러한 소비자 중 하나로 식별합니다. 인스턴스의 ID가 파이프라인을 호출합니다. 클라이언트 콘솔의 모니터링 페이지에 있는 인스턴스 이름으로 입력할 수 있습니다.

파이프라인 서비스는 각 소비자가 검색한 메시지를 추적합니다. 각 인스턴스에 대해 서로 다른 소비자를 사용하면 모든 메시지가 각 인스턴스로 전송되도록 할 수 있습니다.

### 파이프라인 옵션 권장 사항 {#pipeline-option-recommendation}

파이프라인 옵션을 구성하려면 다음 권장 사항을 따라야 합니다.

* **[!UICONTROL Triggers]** 아래의 트리거를 추가하거나 편집하면 나머지 트리거를 편집하지 않아야 합니다.
* JSON이 유효한지 확인합니다. JSON 유효성 검사기를 사용할 수 있습니다. 예를 들어 이 [website](http://jsonlint.com/)을 참조하십시오.
* &quot;name&quot;은 트리거 ID에 해당합니다. 와일드카드 &quot;*&quot;는 모든 트리거를 검색합니다.
* &quot;소비자&quot;는 호출 인스턴스 또는 응용 프로그램의 이름에 해당합니다.
* 피펜드는 &quot;별칭&quot; 주제도 지원합니다.
* 변경한 후에는 항상 파이프라인을 다시 시작해야 합니다.

## 3단계:선택적 구성 {#step-optional}

로드 요구 사항에 따라 일부 내부 매개 변수를 변경할 수 있지만 프로덕션에 적용하기 전에 반드시 테스트해야 합니다.

선택적 매개 변수 목록은 아래에서 확인할 수 있습니다.

| 옵션 | 설명 |
|:-:|:-:|
| appName(레거시) | 공개 키가 업로드된 기존 Authit 응용 프로그램에 등록된 OAuth 응용 프로그램의 AppID. 자세한 정보는 이 [페이지](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.)를 참조하십시오 |
| authGatewayEndpoint(레거시) | 게이트웨이 토큰을 가져오기 위한 URL. 기본값:```https://api.omniture.com``` |
| authPrivateKey(이전) | 개인 키, 이전 선서 응용 프로그램에 업로드된 공개 부분, XtkKey 옵션으로 AES가 암호화됨:```cryptString("PRIVATE_KEY")``` |
| disableAuth(이전) | 인증 비활성화. 게이트웨이 토큰 없이 연결하는 것은 일부 개발 파이프라인 끝점에서만 허용됩니다. |
| discoverPipelineEndpoint | 이 테넌트에 사용할 파이프라인 서비스 끝점을 찾는 URL입니다. 기본값:```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | ```var/INSTANCE/pipelined.json.``` <br> 내부 상태는 여기에서 필요할 때 액세스할 수 있습니다.```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | PipelineServicesEndpoint의 검색을 비활성화하여 강제 적용 |
| monitorServerPort | 파이프라인 프로세스는 내부 상태 프로세스를 제공하기 위해 이 포트를 수신합니다.```http://INSTANCE:PORT/pipelined/status```. <br>기본값은 7781입니다. |
| pointerFlushMessageCount | 이 수의 메시지가 처리되면 오프셋이 데이터베이스에 저장됩니다. <br> 기본값은 1000입니다. |
| pointerFlushPeriodSec | 이 기간이 지나면 오프셋이 데이터베이스에 저장됩니다. <br>기본값은 5(초)입니다. |
| processingJSThreads | 사용자 지정 JS 커넥터를 사용하는 전용 스레드 처리 메시지 수입니다. <br> 기본값은 4입니다. |
| processingThreads | 내장 코드가 있는 전용 스레드 처리 메시지 수입니다. <br>기본값은 4입니다. |
| retryPeriodSec | 처리 오류 시 재시도 사이의 지연. <br>기본값은 30(초)입니다. |
| retryValiditySec | 이 기간 이후에 처리되지 않으면 메시지를 버립니다(너무 많은 재시도). <br>기본값은 300초입니다. |

### 파이프라인 프로세스 자동 시작 {#pipelined-process-autostart}

파이프라인 프로세스는 자동으로 시작해야 합니다.

이렇게 하려면 구성 파일의 &lt; pipeline > 요소를 autostart=&quot;true&quot;로 설정합니다.

```
 <pipelined autoStart="true" ... "/>
```

### 파이프라인 프로세스가 다시 시작 {#pipelined-process-restart}

변경 사항을 적용하려면 다시 시작해야 합니다.

```
nlserver restart pipelined@instance
```

## 4단계:유효성 검사 {#step-validation}

프로비저닝에 대한 파이프라인 설정의 유효성을 검사하려면 아래 단계를 따르십시오.

* [!DNL pipelined] 프로세스가 실행 중인지 확인합니다.
* pipeline.log에서 파이프라인 연결 로그를 확인합니다.
* 연결 및 연결이 수신되었는지 확인합니다. 호스팅된 고객은 클라이언트 콘솔에서 모니터링을 사용할 수 있습니다.
