---
title: 통합 구성
seo-title: 통합 구성
description: 통합 구성
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---


# 파이프라인 문제 해결 {#pipeline-troubleshooting}

**&quot;마스크 피선된@&quot;에 해당하는 작업이 없습니다.&quot; 오류**

사용 중인 Adobe Campaign Classic 버전은 파이프라인을 지원하지 않습니다.

1. 피파이프라인 요소가 구성 파일에 있는지 확인합니다. 그렇지 않으면 지원되지 않음을 의미합니다.
1. 버전 6.11 빌드 8705 이상으로 업그레이드하십시오.

**&quot;Aurait dusonencer par &#39;[&#39; ou &#39;{&#39; (iRc=16384)&quot;로 피펜드가 실패합니다.**

NmsPipeline_ **Config** 옵션이 설정되지 않았습니다. JSON 구문 분석 오류입니다.
NmsPipeline_Config 옵션에서 **JSON 구성을 설정합니다**. 이 페이지에서 &quot;라우팅 옵션&quot;을 참조하십시오.

**&quot;주체가 유효한 조직 또는 클라이언트여야 함&quot;으로 피지정되면 실패합니다.**

IMSOrgid 구성이 잘못되었습니다.

1. IMSOrgId가 serverConf.xml에 설정되어 있는지 확인하십시오.
1. 인스턴스 구성 파일에서 기본값을 무시할 수 있는 빈 IMSOrgId를 찾습니다. 만약 그렇다면, 그것을 제거하세요.
1. IMSOrgId가 Experience Cloud의 고객 ID와 일치하는지 확인합니다.

**&quot;잘못된 키&quot;로 피펜드 실패**

인스턴스 구성 파일의 @authPrivateKey 매개 변수가 잘못되었습니다.

1. authPrivateKey가 설정되어 있는지 확인합니다.
1. authPrivateKey 확인: 은 @, 다음으로 끝남 =, 길이는 약 4,000자입니다.
1. 원래 키를 찾아 다음 사항을 확인합니다. 4096비트 길이의 RSA 포맷으로, 다음으로 시작 —BEGIN RSA PRIVATE KEY—
   <br> 필요한 경우 키를 다시 만들어 Adobe Analytics에 등록합니다. 이 [섹션을 참조하십시오](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. 키가 피펜드된 것과 동일한 인스턴스 내에서 인코딩되었는지 확인합니다. <br>필요한 경우 샘플 JavaScript 또는 워크플로우를 사용하여 인코딩을 다시 실행합니다.

**&quot;인증 중에 토큰을 읽을 수 없음&quot;으로 피지정됨 실패**

개인 키의 형식이 잘못되었습니다.

1. 이 페이지에서 키 암호화 단계를 실행합니다.
1. 키가 동일한 인스턴스에서 암호화되었는지 확인합니다.
1. 구성 파일의 authPrivateKey가 생성된 키와 일치하는지 확인합니다. <br>키 쌍을 생성하려면 OpenSSL을 사용해야 합니다. 예를 들어 PuttyGen은 적절한 형식을 생성하지 않습니다.

**트리거가 검색되지 않음**

피파이프라인 프로세스가 실행되고 트리거가 검색되지 않는 경우:

1. 트리거가 Analytics에서 활성화되고 이벤트를 생성하는지 확인하십시오.
1. 파이프라인 프로세스가 실행되고 있는지 확인합니다.
1. 파이프라인 로그에서 오류를 찾습니다.
1. 파이프라인 상태 페이지에서 오류를 찾습니다. 트리거 폐기, 트리거 실패가 0이어야 합니다.
1. 이 옵션에 트리거 이름이 구성되어 있는지 **[!UICONTROL NmsPipeline_Config]** 확인합니다. 확실하지 않은 경우 와일드카드 옵션을 사용하십시오.
1. Analytics에 활성 트리거가 있고 이벤트를 생성하고 있는지 확인합니다. Analytics에서 구성이 활성화된 후 몇 시간 정도 지연될 수 있습니다.

**이벤트가 고객에게 연결되어 있지 않습니다.**

일부 이벤트가 고객에게 연결되지 않은 경우:

1. 적용 가능한 경우 조정 워크플로우가 실행 중인지 확인합니다.
1. 이벤트에 고객 ID가 포함되어 있는지 확인합니다.
1. 고객 ID를 사용하여 고객 테이블에 대한 쿼리를 만듭니다.
1. 고객 가져오기 빈도를 확인합니다. 새 고객은 워크플로우로 Adobe Campaign으로 가져옵니다.

**이벤트 처리에서의 지연**

Analytics 타임스탬프가 Campaign의 이벤트 생성 날짜보다 훨씬 오래된 경우.

일반적으로 트리거가 마케팅 캠페인을 시작하는 데 15-90분이 걸릴 수 있습니다. 이는 데이터 수집 구현, 파이프라인에서 로드, 정의된 트리거의 사용자 지정 구성 및 Adobe Campaign의 워크플로우에 따라 달라집니다.

1. 파이프라인 프로세스가 실행 중인지 확인합니다.
1. 재시도 횟수를 일으킬 수 있는 pipipeline.log에서 오류를 찾습니다. 해당되는 경우 오류를 수정합니다.
1. 큐 크기에 대해 파이프라인 상태 페이지를 확인합니다. 큐 크기가 큰 경우 JS의 성능을 개선하십시오.
1. 지연이 볼륨에 따라 증가하는 것처럼 보이므로, 메시지 수를 줄여 Analytics에 대한 트리거를 구성합니다.
아넥스

**키 암호화 JavaScript 사용 방법**

JavaScript를 실행하여 개인 키를 암호화합니다. 파이프라인 구성에 필요합니다.

다음은 cryptString 함수를 실행하는 데 사용할 수 있는 코드 샘플입니다.

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

서버에서 Javascript를 실행합니다.

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

출력에서 인코딩된 키를 복사하여 콘솔에 붙여 넣습니다.