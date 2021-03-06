---
product: campaign
title: '파이프라인 문제 해결 '
description: '파이프라인 문제 해결 '
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 1%

---

# 파이프라인 문제 해결 {#pipeline-troubleshooting}

![](../../assets/common.svg)

**&quot;No task 가 pipelled@&lt; instance >&quot;라는 오류가 발생하여 피파이프라인이 실패합니다.**

사용 중인 Adobe Campaign Classic 버전은 파이프라인을 지원하지 않습니다.

1. 다음을 확인하십시오. [!DNL pipelined] 요소가 구성 파일에 있습니다. 그렇지 않으면 지원되지 않음을 의미합니다.
1. Campaign 20.3으로 업그레이드 / [!DNL Gold Standard] 11 이상

**에피셀린드(pipeline)이 &quot;애송이 드온컴펜서 파&quot;로 실패했다 `[` ou `{` (iRc=16384)&quot;**

다음 **NmsPipeline_Config** 옵션이 설정되지 않았습니다. 실제로 JSON 구문 분석 오류입니다.
옵션에서 JSON 구성 설정 **NmsPipeline_Config**. 이 페이지에서 &quot;라우팅 옵션&quot;을 참조하십시오.

**피파이프라인 실패: &quot;주체가 올바른 조직이나 클라이언트여야 함&quot;**

조직 ID 구성이 잘못되었습니다.

1. serverConf.xml에 조직 ID(ImsOrgId)가 설정되어 있는지 확인합니다.
1. 인스턴스 구성 파일의 빈 조직 ID가 기본 조직 ID를 무시할 수 있는지 확인합니다. 그런 경우 제거합니다.
1. 조직 ID가 올바른지 확인합니다. 조직 ID를 찾으려면 다음을 참조하십시오 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko){_blank}

**파이프라인이 &quot;잘못된 키&quot;로 실패합니다.**

인스턴스 구성 파일의 @authPrivateKey 매개 변수가 잘못되었습니다.

1. authPrivateKey 가 설정되어 있는지 확인합니다.
1. authPrivateKey를 확인합니다. 다음으로 시작, 종료 =, 길이는 약 4000자입니다.
1. 원래 키를 찾아 다음 키를 확인합니다. RSA 포맷으로 4096비트 길이의 Dell은 `-----BEGIN RSA PRIVATE KEY-----`.
   <br> 필요한 경우 키를 다시 만들어 Adobe Analytics에 등록합니다.
1. 키가 와 동일한 인스턴스 내에서 인코딩되었는지 확인합니다. [!DNL pipelined]. <br>필요한 경우 샘플 JavaScript 또는 워크플로우를 사용하여 인코딩을 재실행합니다.

**파이프라인이 &quot;인증 중에 토큰을 읽을 수 없습니다.&quot;로 실패합니다.**

개인 키의 형식이 잘못되었습니다.

1. 이 페이지에서 키 암호화 단계를 실행합니다.
1. 키가 동일한 인스턴스에서 암호화되어 있는지 확인합니다.
1. 구성 파일의 authPrivateKey가 생성된 키와 일치하는지 확인합니다. <br>키 쌍을 생성하려면 OpenSSL을 사용해야 합니다. 예를 들어 PuttyGen은 적절한 형식을 생성하지 않습니다.

**파이프라인이 &quot;더 이상 액세스 토큰을 가져올 수 없습니다&quot;로 실패합니다.**

로그는 다음과 같습니다.

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

이 오류 메시지는 기존 Omniture 기본 OAuth를 사용하여 인증이 구성됨을 의미합니다. 자세한 내용은 [Adobe Experience Cloud Triggers에 대한 Adobe I/O 구성](../../integrations/using/configuring-adobe-io.md) 인증을 업그레이드하기 위한 설명서입니다.

**트리거가 검색되지 않음**

이 [!DNL pipelined] 프로세스가 실행되고 있으며 트리거가 검색되지 않습니다.

1. 트리거가 Analytics에서 활성화되어 있고 이벤트를 생성하고 있는지 확인합니다.
1. 다음을 확인합니다. [!DNL pipelined] 프로세스가 실행 중입니다.
1. 에서 오류를 찾습니다. [!DNL pipelined] 로그.
1. 에서 오류를 찾습니다. [!DNL pipelined] 상태 페이지입니다. trigger-discarted, trigger-failures는 0이어야 합니다.
1. 트리거 이름이 **[!UICONTROL NmsPipeline_Config]** 선택 사항입니다. 확실하지 않은 경우 와일드카드 옵션을 사용합니다.
1. Analytics에 활성 트리거가 있고 이벤트를 생성하고 있는지 확인합니다. 활성화되기 전에 Analytics에서 구성이 수행된 후 몇 시간이 지연될 수 있습니다.

**이벤트가 고객에게 연결되지 않음**

일부 이벤트가 고객에게 연결되어 있지 않은 경우:

1. 해당되는 경우 조정 워크플로우가 실행 중인지 확인합니다.
1. 이벤트에 고객 ID가 포함되어 있는지 확인합니다.
1. 고객 ID를 사용하여 고객 테이블에서 쿼리를 만듭니다.
1. 고객 가져오기 빈도를 확인합니다. 새 고객은 워크플로우를 사용하여 Adobe Campaign으로 가져옵니다.

**이벤트 처리 지연**

Analytics 타임스탬프가 Campaign에서 이벤트의 생성 날짜보다 훨씬 오래된 경우.

일반적으로 트리거는 마케팅 캠페인을 시작하는 데 15~90분이 걸릴 수 있습니다. 이것은 데이터 수집 구현, 파이프라인 로드, 정의된 트리거의 사용자 지정 구성 및 Adobe Campaign의 워크플로우에 따라 달라집니다.

1. 다음을 확인하십시오. [!DNL pipelined] 프로세스가 실행 중입니다.
1. 다시 시도할 수 있는 pipelined.log에서 오류를 찾습니다. 해당되는 경우 오류를 수정합니다.
1. 을(를) 확인합니다. [!DNL pipelined] 큐 크기에 대한 상태 페이지입니다. 큐 크기가 큰 경우 JS 성능을 개선합니다.
1. 지연이 볼륨에 따라 증가하는 것 같으므로 메시지 수를 줄여 Analytics에서 트리거를 구성합니다.

**이전 인증에서 Adobe IO 인증으로 단계 인스턴스 업그레이드**

스테이지 인스턴스에서 통합 인증을 변경해도 프로덕션 인스턴스의 구성에 영향을 주지 않습니다. 단계 인스턴스를 업그레이드한 다음 인증을 Adobe IO로 업데이트하고 단계 인스턴스에서 트리거를 테스트할 수 있습니다.

프로덕션 인스턴스는 기존 인증을 계속 사용하며 이러한 변경의 영향을 받지 않습니다.
