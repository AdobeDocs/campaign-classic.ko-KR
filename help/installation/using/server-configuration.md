---
solution: Campaign Classic
product: campaign
title: 서버 구성
description: 서버 구성 우수 사례에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 3%

---


# 서버 구성 {#server-configuration}

## 보안 영역 구성

>[!IMPORTANT]
>
>빌드 8977부터는 보안 영역 셀프 서비스 사용자 인터페이스를 더 이상 사용할 수 없습니다.
>
>* AWS에서 호스팅된 경우 허용 목록에 IP를 추가하는 작업은 Campaign 컨트롤 패널에서 수행해야 합니다. 자세한 내용은 [전용 설명서](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)를 참조하십시오.
>* AWS에서 호스팅되지 않은 경우 Adobe 지원 팀에 연락하여 허용 목록에 IP를 추가합니다.

>
>
인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 섹션](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)에 자세히 나와 있는 단계를 따르십시오.

보안 영역 셀프 서비스 UI를 사용하여 VPN 보안 영역 구성의 항목을 관리하는 방법에 대해 알아보려면 [이 기술 문서](https://helpx.adobe.com/kr/campaign/kb/configuring-security-zones-self-service.html)을 참조하십시오.

* 역방향 프록시가 subNetwork에서 허용되지 않도록 하십시오. 이 경우 **모든** 트래픽이 이 로컬 IP에서 오는 것으로 검색되므로 신뢰할 수 있습니다.

* sessionTokenOnly=&quot;true&quot; 세션의 사용을 최소화합니다.

   * 경고:이 특성이 true로 설정된 경우 연산자는 **CRSF 공격**&#x200B;에 노출될 수 있습니다.
   * 또한 sessionToken 쿠키는 httpOnly 플래그로 설정되어 있지 않으므로 일부 클라이언트측 javascript 코드가 이를 읽을 수 있습니다.
   * 하지만 여러 실행 셀의 메시지 센터에 sessionTokenOnly가 필요합니다.sessionTokenOnly가 &quot;true&quot;로 설정된 새 보안 영역을 만들고 이 영역에 필요한 IP만 **추가합니다.**

* 가능하면 모든 allowHTTP, showErrors를 false(localhost가 아님)로 설정하고 확인합니다.

   * allowHTTP = &quot;false&quot;:연산자가 HTTPS를 사용하도록 강제 설정
   * showErrors = &quot;false&quot;:기술적 오류(SQL 오류 포함)를 숨깁니다. 이렇게 하면 너무 많은 정보가 표시되지 않지만 마케터가 실수를 해결할 수 있는 기능이 줄어듭니다(관리자의 추가 정보 요청 없이).

* 설문 조사, webApps 및 보고서를 만들어야 하는 마케팅 사용자/관리자가 사용하는 IP에 대해서만 allowDebug를 true로 설정합니다. 이 플래그를 사용하면 이러한 IP가 릴레이 규칙을 표시하고 디버깅할 수 있습니다.

* allowEmptyPassword, allowUserPassword, allowSQLInjection을 true로 설정하지 마십시오. 다음 속성은 v5 및 v6.0에서 원활한 마이그레이션을 허용하기 위해서만 여기에 있습니다.

   * **** allowEmptyPasswordlet 연산자는 빈 암호를 가집니다. 이러한 경우 모든 운영자에게 기한을 정하여 암호를 설정하도록 요청합니다. 이 마감일이 지나면 이 속성을 false로 변경합니다.

   * **** allowUserPasswordlet 연산자는 자신의 자격 증명을 매개 변수로 보내기 때문에 apache/IIS/proxy로 기록됩니다. 이 기능은 이전에 API 사용을 단순화하기 위해 사용되었습니다. 일부 제3자 응용 프로그램에서 이것을 사용하는지 여부를 Cookbook(또는 사양에서)에 체크 인할 수 있습니다. 이러한 경우 API를 사용하는 방법을 변경하고 가능한 한 빨리 이 기능을 제거하도록 알려 주어야 합니다.

   * **allow** SQLInjectionlet에서는 사용자가 이전 구문을 사용하여 SQL 주입을 수행할 수 있습니다. 이 속성을 false로 설정할 수 있도록 [이 페이지](../../migration/using/general-configurations.md)에 설명된 수정 사항을 가능한 한 빨리 수행하십시오. /nl/jsp/ping.jsp?zones=true를 사용하여 보안 영역 구성을 확인할 수 있습니다. 이 페이지에는 현재 IP에 대한 보안 조치의 활성 상태(이러한 보안 플래그로 계산됨)가 표시됩니다.

* HttpOnly 쿠키/useSecurityToken:**sessionTokenOnly** 플래그를 참조하십시오.

* 허용 목록에 추가된 IP 최소화:기본적으로 보안 영역에서 개인 네트워크의 3개 범위를 추가했습니다. 이러한 IP 주소를 모두 사용할 가능성은 없습니다. 필요한 것만 보관하세요

* localhost에서만 액세스할 수 있도록 webApp/internal 연산자를 업데이트합니다.

## 파일 업로드 보호

클라이언트/웹 인터페이스를 사용하여 서버에 업로드하는 파일의 종류를 운영 사용자에게 확인합니다. 비즈니스 요구 사항은 다음과 같습니다.

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

기본적으로 Adobe Campaign의 MTA는 보안 연결을 사용하여 컨텐츠를 SMTP 서버로 보내지 않습니다. 이 기능을 활성화해야 합니다(배달 속도를 줄일 수 있음). 이렇게 하려면 `<smtp ...>` 노드에서 enableTLS를 tr**으로 설정합니다.

인증 노드(sessionTimeOutSec 특성)에서 세션의 수명을 줄일 수 있습니다.
