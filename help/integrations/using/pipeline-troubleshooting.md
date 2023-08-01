---
product: campaign
title: 파이프라인 문제 해결
description: 파이프라인 문제 해결
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 2%

---

# 파이프라인 문제 해결 {#pipeline-troubleshooting}



**&quot;파이프라인@&lt; 인스턴스 >에 해당하는 작업이 없습니다&quot; 오류와 함께 파이프라인이 실패합니다.**

사용 중인 Adobe Campaign Classic 버전은 파이프라인을 지원하지 않습니다.

1. 다음을 확인함: [!DNL pipelined] 요소가 구성 파일에 있습니다. 그렇지 않으면 지원되지 않는다는 의미입니다.
1. Campaign 20.3으로 업그레이드 / [!DNL Gold Standard] 11 이상.

**&#39;&#39; aurait ducencer par로 파이프라인 실패 `[` ou `{` (iRc=16384)&quot;**

다음 **NmsPipeline_Config** 옵션이 설정되지 않았습니다. 실제로 JSON 구문 분석 오류입니다.
옵션에서 JSON 구성 설정 **NmsPipeline_Config**. 이 페이지의 &quot;라우팅 옵션&quot;을 참조하십시오.

**파이프라인이 &quot;주체가 유효한 조직 또는 클라이언트여야 함&quot;과 함께 실패합니다.**

조직 ID 구성이 잘못되었습니다.

1. 조직 ID(ImsOrgId)가 serverConf.xml에 설정되어 있는지 확인합니다.
1. 인스턴스 구성 파일의 빈 조직 ID가 기본 ID를 재정의할 수 있는지 확인합니다. 그렇다면 빼십시오.
1. 조직 ID가 올바른지 확인합니다. 조직 ID를 찾으려면 다음을 참조하십시오. [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko){_blank}

**파이프라인이 &quot;잘못된 키&quot;로 실패합니다.**

인스턴스 구성 파일의 @authPrivateKey 매개 변수가 잘못되었습니다.

1. authPrivateKey가 설정되어 있는지 확인합니다.
1. authPrivateKey: 가 @으로 시작하며 = 로 끝나고 약 4000자인지 확인하십시오.
1. 원래 키를 찾아 RSA 형식에서 4096비트 길이이며 다음으로 시작하는지 확인합니다. `-----BEGIN RSA PRIVATE KEY-----`.
   <br> 필요한 경우 키를 다시 만들어 Adobe Analytics에 등록합니다.
1. 키가 와 동일한 인스턴스 내에서 인코딩되었는지 확인합니다. [!DNL pipelined]. <br>필요한 경우 샘플 JavaScript 또는 워크플로우를 사용하여 인코딩을 다시 실행합니다.

**파이프라인이 &quot;인증 중 토큰을 읽을 수 없음&quot;과 함께 실패합니다.**

개인 키의 형식이 잘못되었습니다.

1. 이 페이지에서 키 암호화에 대한 단계를 실행합니다.
1. 키가 동일한 인스턴스에서 암호화되었는지 확인합니다.
1. 구성 파일의 authPrivateKey가 생성된 키와 일치하는지 확인하십시오. <br>키 쌍을 생성하려면 OpenSSL을 사용해야 합니다. 예를 들어, PuttyGen은 적절한 형식을 생성하지 않습니다.

**파이프라인이 &quot;더 이상 액세스 토큰을 가져올 수 없음&quot;과 함께 실패합니다.**

로그는 다음과 같아야 합니다.

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

이 오류 메시지는 기존 Omniture 기본 OAuth를 사용하여 인증을 구성함을 의미합니다. 다음을 참조하십시오. [Adobe Experience Cloud Triggers에 대한 Adobe I/O 구성](../../integrations/using/configuring-adobe-io.md) 인증을 업그레이드하기 위한 설명서입니다.

**검색된 트리거가 없습니다.**

다음의 경우 [!DNL pipelined] 프로세스가 실행 중이고 트리거가 검색되지 않습니다.

1. 트리거가 Analytics에서 활성화되어 있고 이벤트를 생성하고 있는지 확인합니다.
1. 다음을 확인하십시오. [!DNL pipelined] 프로세스가 실행 중입니다.
1. 에서 오류를 찾습니다. [!DNL pipelined] 로그합니다.
1. 에서 오류를 찾습니다. [!DNL pipelined] 상태 페이지입니다. trigger-discarted, trigger-failures는 0이어야 합니다.
1. 트리거 이름이 **[!UICONTROL NmsPipeline_Config]** 옵션을 선택합니다. 확실하지 않은 경우 와일드카드 옵션을 사용합니다.
1. Analytics에 활성 트리거가 있으며 이벤트를 생성하고 있는지 확인합니다. 활성화되기 전에 Analytics에서 구성을 완료한 후 몇 시간 정도 지연될 수 있습니다.

**이벤트가 고객에게 연결되지 않음**

일부 이벤트가 고객에게 연결되지 않은 경우:

1. 조정 워크플로우가 실행 중인지 확인합니다(해당하는 경우).
1. 이벤트에 고객 ID가 포함되어 있는지 확인합니다.
1. 고객 ID를 사용하여 고객 테이블에서 쿼리를 만듭니다.
1. 고객 가져오기 빈도를 확인합니다. 새 고객은 워크플로우로 Adobe Campaign으로 가져옵니다.

**이벤트 처리 지연**

Analytics 타임스탬프가 Campaign의 이벤트 생성 날짜보다 훨씬 오래된 경우.

일반적으로 트리거는 마케팅 캠페인을 시작하는 데 15~90분 정도 걸릴 수 있습니다. 이는 데이터 수집 구현, 파이프라인 로드, 정의된 트리거의 사용자 지정 구성 및 Adobe Campaign의 워크플로우에 따라 달라집니다.

1. 다음을 확인함: [!DNL pipelined] 프로세스가 실행 중입니다.
1. 다시 시도를 일으킬 수 있는 pipelined.log에서 오류를 찾습니다. 해당되는 경우 오류를 수정합니다.
1. 다음 확인: [!DNL pipelined] 대기열 크기에 대한 상태 페이지. 큐 크기가 큰 경우 JS의 성능을 개선합니다.
1. 지연은 볼륨에 따라 증가하는 것처럼 보이므로 더 적은 수의 메시지를 사용하여 Analytics에서 트리거를 구성합니다.

**레거시 인증에서 Adobe IO 인증으로 스테이지 인스턴스 업그레이드**

스테이지 인스턴스에서 통합 인증을 변경해도 프로덕션 인스턴스의 구성에 영향을 주지 않습니다. 단계 인스턴스를 업그레이드한 다음 인증을 업데이트하여 IO를 Adobe 하고 단계 인스턴스에서 트리거를 테스트할 수 있습니다.

프로덕션 인스턴스는 레거시 인증을 계속 사용하며 이 변경의 영향을 받지 않습니다.
