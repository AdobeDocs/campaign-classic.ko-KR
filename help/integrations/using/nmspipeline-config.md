---
product: campaign
title: 파이프라인 옵션 NmsPipeline_Config
description: 파이프라인 옵션 NmsPipeline_Config
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 3%

---


# 파이프라인 옵션 NmsPipeline_Config {#nmspipeline_config}



인증이 작동하면, [!DNL pipelined] 은 이벤트를 검색하고 처리할 수 있습니다. Adobe Campaign에 구성된 트리거만 처리하며 다른 트리거는 무시합니다. 트리거가 Analytics에서 생성되어 미리 파이프라인으로 푸시되었어야 합니다.
이름에 관계없이 모든 트리거를 캐치하도록 와일드카드로 옵션을 구성할 수도 있습니다.

트리거의 구성은 아래의 옵션에서 수행됩니다. **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. 옵션 이름은 다음과 같습니다 **[!UICONTROL NmsPipeline_Config]**. 데이터 유형은 JSON 포맷의 &quot;긴 텍스트&quot;입니다.

이 예에서는 두 개의 트리거를 지정합니다.

이 템플릿의 JSON 코드를 옵션 값에 붙여 넣습니다. 주석을 제거해야 합니다.

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
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

이 두 번째 예는 모든 트리거를 캡처합니다.

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

>[!NOTE]
>
>다음 [!DNL Trigger] Analytics 인터페이스에서 특정 트리거 이름에 대한 UID 값은 트리거 인터페이스에서 URL 쿼리 문자열 매개 변수의 일부로 찾을 수 있습니다. triggerType UID가 파이프라인 데이터 스트림에 전달되고 pipeline.JS에 코드를 작성하여 트리거 UID를 pipelineEvents 스키마의 Trigger Name 열에 저장할 수 있는 사용자에게 친숙한 레이블에 매핑할 수 있습니다.

## 소비자 매개 변수 {#consumer-parameter}

파이프라인은 &quot;공급자 및 소비자&quot; 모델과 함께 작동합니다. 같은 줄에 소비자가 많이 있을 수 있습니다. 메시지는 개별 소비자에 대해서만 &quot;소비&quot;됩니다. 각 소비자는 고유한 메시지 사본을 얻습니다.

&quot;소비자&quot; 매개 변수는 인스턴스를 이러한 소비자 중 하나로 식별합니다. 파이프라인을 호출하는 인스턴스의 ID입니다. 인스턴스 이름으로 입력할 수 있습니다. 파이프라인 서비스는 각 소비자가 검색한 메시지를 추적합니다. 다양한 인스턴스에 서로 다른 소비자를 사용하면 모든 메시지가 각 인스턴스에 전송됩니다.

## 파이프라인 옵션을 구성하는 방법 {#configure-pipeline-option}

&quot;triggers&quot; 배열 아래에서 Experience Cloud 트리거를 추가하거나 편집합니다. 나머지는 편집하지 마십시오.
JSON이 이 ID의 도움을 받아 유효한지 확인합니다 [웹 사이트](https://jsonlint.com/).

* name은 트리거 ID입니다. 와일드카드 &quot;*&quot;가 모든 트리거를 캡처합니다.
* &quot;소비자&quot;는 nlserver 인스턴스를 고유하게 식별하는 고유한 문자열입니다. 일반적으로 인스턴스 이름 자체일 수 있습니다. 여러 환경(개발/스테이지/prod)의 경우 각 인스턴스가 메시지의 사본을 받을 수 있도록 각 환경에 대해 고유한지 확인하십시오.
* [!DNL Pipelined] 또한 &quot;별칭&quot; 항목을 지원합니다.

다시 시작 [!DNL pipelined] 변경한 후
