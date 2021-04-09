---
solution: Campaign Classic
product: campaign
title: 서버 보안 구성
description: 서버 구성 우수 사례에 대한 자세한 내용
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 3%

---

# 서버 보안 설정 {#server-configuration}

## 파일 업로드 보호

캠페인 클라이언트 콘솔 또는 웹 인터페이스를 사용하여 서버에 업로드하는 파일의 종류를 운영 사용자에게 확인합니다. 비즈니스 요구 사항은 다음과 같습니다.

* 이미지(jpg, gif, png, ...)
* 콘텐트(zip, html, css, ...)
* 마케팅 에셋(doc, xls, pdf, psd, tiff,..)
* 이메일 첨부 파일(문서, pdf, ...)
* ETL(텍스트, csv, 탭, ...)
* 등.

serverConf/shared/datastore/@uploadAllowlist(유효한 Java 정규 표현식)에 모든 매개 변수를 추가합니다. [이 페이지](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files)에서 자세히 알아보십시오.

Adobe Campaign은 파일 크기를 제한하지 않습니다. 하지만 IIS/Apache를 구성하여 수행할 수 있습니다. [이 섹션](../../installation/using/web-server-configuration.md)에서 자세히 알아보십시오.

## 릴레이

자세한 내용은 [이 페이지](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)를 참조하십시오.

기본적으로 웹 모듈이 시작된 컴퓨터의 로컬 Tomcat 서버에 모든 동적 페이지가 자동으로 전달됩니다. 일부는 릴레이하지 않도록 선택할 수 있습니다. 일부 Adobe Campaign 모듈(예: 웹 앱, 상호 작용, 일부 jsp)을 사용하지 않는 경우 릴레이 규칙에서 제거할 수 있습니다.

기본적으로 http(httpAllowed=&quot;true&quot;)를 사용하여 최종 사용자 리소스를 표시하는 기능이 강제로 수행되었습니다. 이러한 페이지에는 일부 PII(예: 이메일 컨텐츠, 주소), 쿠폰 사용, 오퍼 등이 표시될 수 있으므로 이러한 경로에서 다시 HTTPS를 강제 적용해야 합니다.

다른 호스트 이름(공개 이름 및 연산자 이름)을 사용하는 경우 연산자가 필요로 하는 일부 리소스가 공개 DNS 이름으로 재회되는 것을 방지할 수도 있습니다.

## 발신 연결 보호

Campaign Classic 인스턴스에서 워크플로우 등의 JavaScript 코드를 통해 호출할 수 있는 URL의 기본 목록은 이 제한됨 새 URL을 허용하려면 관리자가 [serverConf.xml 파일](../../installation/using/the-server-configuration-file.md)에서 이 URL을 참조해야 합니다.

연결 보호 모드는 다음과 같이 3가지가 있습니다.

* **차단** :허용 목록에 속하지 않는 모든 URL이 차단되며 오류 메시지가 표시됩니다. 업그레이드 후 기본 모드입니다.
* **자유로운** :허용 목록에 속하지 않는 모든 URL이 허용됩니다.
* **경고** :허용 목록에 있는 모든 URL은 허용되지 않지만 JS 인터프리터는 관리자가 수집할 수 있도록 경고를 전송합니다. 이 모드에서는 JST-310027 경고 메시지가 추가됩니다.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

새 클라이언트는 차단 모드를 사용합니다. 새 URL을 허용하려면 관리자에게 문의하여 허용 목록에 추가해야 합니다.

마이그레이션에서 오는 기존 고객은 잠시 경고 모드를 사용할 수 있습니다. 동시에 URLS를 인증하기 전에 아웃바운드 트래픽을 분석해야 합니다.

## 명령 제한(서버측)

몇 가지 명령은 블랙리스트에 추가되어 있으므로 execCommand 함수를 사용하여 실행할 수 없습니다. 외부 명령을 실행하기 위해 전용 Unix 사용자가 추가 보안을 제공합니다. 호스팅된 설치의 경우 이 제한이 자동으로 적용됩니다. 온-프레미스 설치의 경우 [이 페이지](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)의 지침에 따라 이 제한을 수동으로 설정할 수 있습니다. 또한 **[!UICONTROL Script]** 및 **[!UICONTROL External task]** 워크플로우 활동을 사용할 수 없습니다(새로 설치된 인스턴스).

## 기타 구성

모든 페이지에 대해 추가 HTTP 헤더를 추가할 수 있습니다(자세한 내용은 [이 페이지](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands) 참조).

* HSTS, X-FRAME-OPTIONS, CSP 등의 추가 헤더를 추가할 수 있습니다.
* 제작 시 적용하기 전에 테스트 환경에서 테스트해야 합니다.

   >[!IMPORTANT]
   >
   >특정 헤더를 추가하여 Adobe Campaign을 분리할 수 있습니다.

Adobe Campaign에서는 `<dbcnx .../>` 요소에 일반 암호를 설정할 수 있습니다. 이 기능을 사용하지 마십시오.

기본적으로 Adobe Campaign은 특정 IP에 세션을 붙이지 않지만 이 세션을 활성화하여 세션이 도난 당하지 않도록 할 수 있습니다. 이를 수행하려면 [serverConf.xml 파일](../../installation/using/the-server-configuration-file.md)에서 checkIPConsistent 속성을 `<authentication>` 노드의 **true**&#x200B;로 설정합니다.

기본적으로 Adobe Campaign의 MTA는 보안 연결을 사용하여 컨텐츠를 SMTP 서버로 보내지 않습니다. 이 기능을 활성화해야 합니다(배달 속도를 줄일 수 있음). 이렇게 하려면 `<smtp ...>` 노드에서 **enableTLS**&#x200B;을 **true**&#x200B;로 설정합니다.

인증 노드(sessionTimeOutSec 특성)에서 세션의 수명을 줄일 수 있습니다.
