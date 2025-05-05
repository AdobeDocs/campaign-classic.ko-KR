---
product: campaign
title: 파이프라인 구성
description: Campaign - 트리거 통합을 위한 파이프라인을 구성하는 방법을 알아봅니다.
feature: Triggers
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---

# 파이프라인 구성 {#configuring-pipeline}

고객 ID, 개인 키 및 인증 끝점과 같은 인증 매개 변수는 인스턴스 구성 파일에 구성됩니다.

처리할 트리거 목록은 JSON 형식의 옵션으로 구성됩니다.

트리거는 이메일을 보내는 캠페인 워크플로우에서 타겟팅하는 데 사용됩니다. 캠페인은 트리거 이벤트가 모두 있는 고객이 이메일을 받도록 설정됩니다.

## 필수 구성 요소 {#prerequisites}

이 구성을 시작하기 전에 다음을 확인하십시오.

* Adobe Developer 프로젝트
* 올바른 조직 ID - 조직 ID를 찾으려면 [이 페이지](https://experienceleague.adobe.com/ko/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}를 참조하세요.
* 조직에 대한 개발자 액세스 권한
* Adobe Analytics의 유효한 트리거 구성

파이프라인이 Adobe Experience Cloud에서 호스팅되므로 인증이 필요합니다. Adobe Developer 프로젝트를 통해에 지원되는 인증을 사용합니다.

## 1단계: Adobe Developer 프로젝트 만들기/업데이트 {#creating-adobe-io-project}

트리거 통합을 위해 Adobe Developer 계정 토큰을 사용하여 조직을 활성화해야 합니다.

[이 페이지](../../integrations/using/oauth-technical-account.md)에서 Adobe 기술 계정을 만드는 방법을 알아봅니다. Adobe Developer 자격 증명에 API를 추가하는 동안 **[!UICONTROL Adobe Analytics]**&#x200B;을(를) 선택해야 합니다.

## 2단계: 파이프라인 옵션 구성 {#configuring-nmspipeline}

인증이 설정되면 파이프라인이 이벤트를 검색합니다. Adobe Campaign에 구성된 트리거만 처리합니다. 트리거는 Adobe Analytics에서 생성되어 파이프라인으로 푸시되어야 하며 파이프라인은 Adobe Campaign에 구성된 트리거만 처리합니다.

이름과 관계없이 모든 트리거를 catch하기 위해 와일드카드로 옵션을 구성할 수도 있습니다.

1. Adobe Campaign에서 **[!UICONTROL Explorer]**&#x200B;의 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 아래에 있는 옵션 메뉴에 액세스합니다.

1. **[!UICONTROL NmsPipeline_Config]** 옵션을 선택합니다.

1. **[!UICONTROL Value (long text)]** 필드에 두 개의 트리거를 지정하는 다음 JSON 코드를 붙여넣을 수 있습니다. 주석을 제거해야 합니다.

   ```json
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

1. 모든 트리거를 catch하는 다음 JSON 코드를 붙여넣도록 선택할 수도 있습니다.

   ```json
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

### 소비자 매개 변수 설정 {#consumer-parameter}

파이프라인은 공급업체 및 소비자 모델처럼 작동합니다. 메시지는 개별 소비자에 대해서만 소비됩니다. 각 소비자는 메시지의 자체 복사본을 가져옵니다.

**Consumer** 매개 변수는 이러한 소비자 중 하나로 인스턴스를 식별합니다. 인스턴스 ID가 파이프라인을 호출합니다. 클라이언트 콘솔의 모니터링 페이지에 있는 인스턴스 이름으로 채울 수 있습니다.

파이프라인 서비스는 각 소비자가 검색한 메시지를 추적합니다. 서로 다른 인스턴스에 대해 서로 다른 소비자를 사용하면 모든 메시지가 각 인스턴스로 전송되는지 확인할 수 있습니다.

### 파이프라인 옵션 권장 사항 {#pipeline-option-recommendation}

파이프라인 옵션을 구성하려면 다음 권장 사항을 따라야 합니다.

* **[!UICONTROL Triggers]** 아래에 트리거를 추가하거나 편집합니다.
* JSON이 유효한지 확인합니다.
* **Name** 매개 변수는 트리거 ID에 해당합니다. 와일드카드 &quot;*&quot;가 모든 트리거를 catch합니다.
* **Consumer** 매개 변수는 호출 인스턴스 또는 응용 프로그램의 이름에 해당합니다.
* `pipelined`프로세스에서는 &quot;별칭&quot; 항목도 지원합니다.
* 변경한 후에는 항상 `pipelined`프로세스를 다시 시작해야 합니다.

## (선택 사항) 3단계: 추가 구성 {#step-optional}

로드 요구 사항에 따라 일부 내부 매개 변수를 변경할 수 있지만, 프로덕션 환경에 적용하기 전에 테스트해야 합니다.

선택적 매개 변수 목록은 다음과 같습니다.

| 옵션 | 설명 |
|:-:|:-:|
| appName(기존) | 공개 키가 업로드된 Legacy Oath 애플리케이션에 등록된 OAuth 애플리케이션의 AppID입니다. 자세한 정보는 이 [페이지](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md)를 참조하십시오. |
| authGatewayEndpoint(기존) | 게이트웨이 토큰을 가져올 URL입니다. 기본값: ```https://api.omniture.com``` |
| authPrivateKey(기존) | 개인 키, 레거시 Oath 응용 프로그램에 업로드된 공개 부분, XtkKey 옵션으로 암호화된 AES: ```cryptString("PRIVATE_KEY")``` |
| disableAuth(기존) | 인증을 비활성화하면 일부 개발 파이프라인 엔드포인트에서만 게이트웨이 토큰 없이 연결할 수 있습니다. |
| discoverPipelineEndpoint | 이 테넌트에 사용할 파이프라인 서비스 끝점을 찾는 URL입니다. 기본값: ```https://producer-pipeline-pnw.adobe.net``` |
| 덤프 상태 기간 초 | ```var/INSTANCE/pipelined.json.``` <br> 내부 상태에서 내부 상태 프로세스의 두 덤프 사이의 기간은 ```http://INSTANCE:7781/pipelined/status```에서도 필요할 때 액세스할 수 있습니다. |
| forcedPipelineEndpoint | PipelineServicesEndpoint 검색을 비활성화하여 강제 실행 |
| 모니터 서버 포트 | 파이프라인된 프로세스는 ```http://INSTANCE:PORT/pipelined/status```에서 내부 상태 프로세스를 제공하기 위해 이 포트에서 수신 대기합니다. <br>기본값은 7781입니다. |
| pointerFlushMessageCount | 이 메시지 수가 처리되면 오프셋은 데이터베이스에 저장됩니다. <br> 기본값은 1000입니다. |
| pointerFlushPeriodSec | 이 기간이 지나면 오프셋이 데이터베이스에 저장됩니다. <br>기본값은 5초입니다. |
| processingJSThreads | 사용자 지정 JS 커넥터가 있는 메시지를 처리하는 전용 스레드 수입니다. <br> 기본값은 4입니다. |
| 처리 스레드 | 기본 제공 코드가 있는 메시지를 처리하는 전용 스레드 수. <br>기본값은 4입니다. |
| 다시 시도 기간 초 | 처리 오류 시 다시 시도 사이에서 지연. <br>기본값은 30초입니다. |
| retryValiditySec | 이 기간 후에 성공적으로 처리되지 않는 경우 메시지를 무시합니다(재시도 횟수가 너무 많음). <br>기본값은 300초입니다. |

### 파이프라인 프로세스 자동 시작 {#pipelined-process-autostart}

`pipelined` 프로세스를 자동으로 시작해야 합니다.

이를 위해 구성 파일의 `<`pipelined`>` 요소를 autostart=&quot;true&quot;로 설정합니다.

```sql
 <pipelined autoStart="true" ... "/>
```

### 파이프라인 프로세스 다시 시작 {#pipelined-process-restart}

변경 사항을 적용하려면 다시 시작해야 합니다.

```sql
nlserver restart pipelined@instance
```

## 4단계: 유효성 검사 {#step-validation}

프로비저닝에 대한 파이프라인 설정의 유효성을 검사하려면 아래 단계를 수행하십시오.

* `pipelined` 프로세스가 실행 중인지 확인하십시오.
* `pipelined.log`에서 파이프라인 연결 로그를 확인하십시오.
* 연결을 확인하고 Ping이 수신되는지 확인합니다. 호스팅된 고객은 클라이언트 콘솔에서 모니터링을 사용할 수 있습니다.
