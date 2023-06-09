---
product: campaign
title: 서버 보안 구성
description: 서버 구성 모범 사례에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 3c1a0f435dce5e1f54f701e742f393db066ad78f
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 4%

---

# 서버 보안 설정 {#server-configuration}

## 파일 업로드 보호

운영 사용자에게 Campaign 클라이언트 콘솔 또는 웹 인터페이스를 사용하여 서버에 업로드하는 파일 종류를 확인합니다. 비즈니스 요구 사항은 다음과 같을 수 있습니다.

* 이미지(jpg, gif, png, ...)
* 컨텐츠(zip, html, css, ...)
* 마케팅 에셋(doc, xls, pdf, psd, tiff, ...)
* 이메일 첨부 파일(doc, pdf, ...)
* ETL(txt, csv, 탭, ...)
* 등

serverConf/shared/datastore/@uploadAllowlist(유효한 Java 정규 표현식)에 모든 항목을 추가합니다. [이 페이지](../../installation/using/file-res-management.md)에서 자세히 알아보십시오.

Adobe Campaign은 파일 크기를 제한하지 않습니다. 그러나 IIS/Apache를 구성하여 이 작업을 수행할 수 있습니다. [이 섹션](../../installation/using/web-server-configuration.md)에서 자세히 알아보십시오.

## 릴레이

다음을 참조하십시오. [이 페이지](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 추가 정보.

기본적으로 모든 동적 페이지는 웹 모듈이 시작된 시스템의 로컬 Tomcat 서버에 자동으로 전달됩니다. 일부 파일을 릴레이하지 않도록 선택할 수 있습니다. 일부 Adobe Campaign 모듈(예: 웹 앱, 상호 작용, 일부 jsp)을 사용하지 않는 경우 릴레이 규칙에서 제거할 수 있습니다.

기본적으로 http(httpAllowed=&quot;true&quot;)를 사용하여 최종 사용자 리소스를 표시하도록 했습니다. 이러한 페이지에는 일부 PII(예: 이메일 콘텐츠, 주소), 쿠폰, 오퍼가 표시될 수 있으므로 이러한 경로에 HTTPS를 다시 적용해야 합니다.

서로 다른 호스트 이름(하나의 공용 및 하나의 운영자용)을 사용하는 경우 운영자가 필요한 일부 리소스를 공용 DNS 이름으로 릴레이하는 것을 방지할 수도 있습니다.

## 발신 연결 보호

Campaign Classic 인스턴스에서 워크플로우 등의 JavaScript 코드를 통해 호출할 수 있는 URL의 기본 목록은 은(는) 제한적입니다. 새 URL을 허용하려면에서 관리자가 참조해야 합니다. [serverConf.xml 파일](../../installation/using/the-server-configuration-file.md).

세 가지 연결 보호 모드가 있습니다.

* **차단** : 허용 목록에 추가하다에 속하지 않는 모든 URL이 차단되고 오류 메시지가 표시됩니다. 업그레이드 후 기본 모드입니다.
* **허용-** : 허용 목록에 추가하다에 속하지 않는 모든 URL이 허용됩니다.
* **경고** : 허용 목록에 추가하다에 없는 모든 URL이 허용되지만, 관리자가 수집할 수 있도록 URL 인터프리터가 경고를 내보냅니다. 이 모드는 JST 310027 경고 메시지를 추가합니다.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

새 클라이언트는 차단 모드를 사용합니다. 새 URL을 허용하려면 관리자에게 연락하여 허용 목록에 추가하다에 추가해야 합니다.

마이그레이션을 통해 온 기존 고객은 잠시 동안 경고 모드를 사용할 수 있습니다. 한편 URL을 인증하기 전에 아웃바운드 트래픽을 분석해야 합니다.

## 명령 제한(서버측)

차단 목록에는 여러 명령이 포함되어 있으며 execCommand 함수를 사용하여 실행할 수 없습니다. 전용 Unix 사용자는 외부 명령을 실행하기 위해 추가 보안을 제공합니다. 호스팅된 설치의 경우 이 제한이 자동으로 적용됩니다. 온-프레미스 설치의 경우 의 지침에 따라 이 제한을 수동으로 설정할 수 있습니다. [이 페이지](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). 또한, **[!UICONTROL Script]** 및 **[!UICONTROL External task]** 워크플로우 활동을 사용할 수 없습니다(새로 설치된 인스턴스).

## 기타 구성

모든 페이지에 대해 추가 HTTP 헤더를 추가할 수 있습니다(자세한 내용은 다음을 참조하십시오.) [이 페이지](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* HSTS, X-FRAME-HEADERS, CSP와 같은 일부 추가 OPTIONS을 추가할 수 있습니다.
* 프로덕션에 적용하기 전에 테스트 환경에서 테스트해야 합니다.

  >[!IMPORTANT]
  >
  >특정 헤더를 추가하여 Adobe Campaign을 중단할 수 있습니다.

Adobe Campaign을 사용하면 `<dbcnx .../>` 요소를 생성하지 않습니다. 이 기능을 사용하지 마십시오.

기본적으로 Adobe Campaign은 특정 IP에 세션을 연결하지 않지만 세션이 도난되는 것을 방지하기 위해 활성화할 수 있습니다. 다음을 수행합니다. [serverConf.xml 파일](../../installation/using/the-server-configuration-file.md), checkIPConsistent 속성을 다음으로 설정 **true** 다음에서 `<authentication>` 노드.

기본적으로 Adobe Campaign의 MTA는 보안 연결을 사용하여 SMTP 서버로 콘텐츠를 전송하지 않습니다. 이 기능을 활성화해야 합니다(게재 속도를 줄일 수 있음). 이렇게 하려면 다음을 설정합니다. **enableTLS** 끝 **true** 다음에서 `<smtp ...>` 노드.

인증 노드(sessionTimeOutSec 특성)에서 세션의 수명을 줄일 수 있습니다.
