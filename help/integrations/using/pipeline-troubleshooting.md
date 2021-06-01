---
product: campaign
title: 통합 구성
description: 통합 구성
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# 파이프라인 문제 해결 {#pipeline-troubleshooting}

**&quot;No task 가 pipelined@&lt;>&quot;라는 오류가 발생하여 피파이프라인이 실패합니다.**

사용 중인 Adobe Campaign Classic 버전은 파이프라인을 지원하지 않습니다.

1. 구성 파일에 [!DNL pipelined] 요소가 있는지 확인합니다. 그렇지 않으면 지원되지 않음을 의미합니다.
1. Campaign 20.3 또는 [!DNL Gold Standard] 11로 업그레이드하십시오.

**&quot;Aurait dunencer par  `[` ou(iRc=16384)&quot; `{` 로 파이프라인이 실패합니다.**

**NmsPipeline_Config** 옵션이 설정되지 않았습니다. 실제로 JSON 구문 분석 오류입니다.
**NmsPipeline_Config** 옵션에서 JSON 구성을 설정합니다. 이 페이지에서 &quot;라우팅 옵션&quot;을 참조하십시오.

**피파이프라인 실패: &quot;주체가 올바른 조직이나 클라이언트여야 함&quot;**

조직 식별자 구성이 잘못되었습니다.

1. IMSOrgId가 serverConf.xml에 설정되어 있는지 확인합니다.
1. 기본값을 무시할 수 있는 인스턴스 구성 파일에서 빈 IMSOrgId를 찾습니다. 그런 경우 제거합니다.
1. IMSOrgId가 Experience Cloud에서 고객의 ID와 일치하는지 확인합니다.

**파이프라인이 &quot;잘못된 키&quot;로 실패합니다.**

인스턴스 구성 파일의 @authPrivateKey 매개 변수가 잘못되었습니다.

1. authPrivateKey 가 설정되어 있는지 확인합니다.
1. authPrivateKey를 확인합니다.다음으로 시작, 종료 =, 길이는 약 4000자입니다.
1. 원래 키를 찾아 다음 키를 확인합니다.RSA 형식으로 4096비트 길이의 RSA PRIVATE KEY로 시작합니다.
   <br> 필요한 경우 키를 다시 만들어 Adobe Analytics에 등록합니다.
1. 키가 [!DNL pipelined] 인스턴스와 동일한 인스턴스 내에서 인코딩되었는지 확인합니다. <br>필요한 경우 샘플 JavaScript 또는 워크플로우를 사용하여 인코딩을 재실행합니다.

**파이프라인이 &quot;인증 중에 토큰을 읽을 수 없습니다.&quot;로 실패합니다.**

개인 키의 형식이 잘못되었습니다.

1. 이 페이지에서 키 암호화 단계를 실행합니다.
1. 키가 동일한 인스턴스에서 암호화되어 있는지 확인합니다.
1. 구성 파일의 authPrivateKey가 생성된 키와 일치하는지 확인합니다. <br>키 쌍을 생성하려면 OpenSSL을 사용해야 합니다. 예를 들어 PuttyGen은 적절한 형식을 생성하지 않습니다.

**트리거가 검색되지 않음**

[!DNL pipelined] 프로세스가 실행 중이고 트리거가 검색되지 않는 경우:

1. 트리거가 Analytics에서 활성화되어 있고 이벤트를 생성하고 있는지 확인합니다.
1. [!DNL pipelined] 프로세스가 실행 중인지 확인합니다.
1. [!DNL pipelined] 로그에서 오류를 찾습니다.
1. [!DNL pipelined] 상태 페이지에서 오류를 찾습니다. trigger-discarted, trigger-failures는 0이어야 합니다.
1. 트리거 이름이 **[!UICONTROL NmsPipeline_Config]** 옵션에 구성되어 있는지 확인합니다. 확실하지 않은 경우 와일드카드 옵션을 사용합니다.
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

1. [!DNL pipelined] 프로세스가 실행 중인지 확인합니다.
1. 다시 시도할 수 있는 pipelined.log에서 오류를 찾습니다. 해당되는 경우 오류를 수정합니다.
1. [!DNL pipelined] 상태 페이지에서 큐 크기를 확인합니다. 큐 크기가 큰 경우 JS 성능을 개선합니다.
1. 지연이 볼륨에 따라 증가하는 것 같으므로 메시지 수를 줄여 Analytics에서 트리거를 구성합니다.
