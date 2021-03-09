---
solution: Campaign Classic
product: campaign
title: 웹 서버 구성
description: 웹 서버 구성 기본 우수 사례에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# 웹 서버 구성 {#web-server-configuration}

웹 서버(Apache/IIS) 구성과 관련된 몇 가지 주요 우수 사례를 살펴보십시오.

* 기본 오류 페이지를 변경합니다.

* 이전 SSL 버전 및 암호 비활성화:

   **Apache에서** /etc/apache2/mods-available/ssl.conf을 편집합니다. 다음은 한 예입니다.

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **IIS** ( [설명서](https://support.microsoft.com/en-us/kb/245030) 참조)에서 다음 구성을 수행하십시오.

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL에서 레지스트리 하위 키 추가
   * 시스템에서 기본적으로 협상되지 않을 프로토콜을 사용하도록 설정하려면(예: TLS 1.2) **프로토콜** 키 아래의 다음 레지스트리 키에서 DisabledByDefault 값의 DWORD 값 데이터를 0x0으로 변경하십시오.

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **SSL x.0 비활성화**

   SCHANNEL\Protocols\SSL 3.0\Client:DisabledByDefault:DWORD(32비트) 값-1

   SCHANNEL\Protocols\SSL 3.0\Server:사용:DWORD(32비트) 값 - 0

* **TRACE** 메서드를 제거합니다.

   **Apache에서** /etc/apache2/conf.d/security에서 편집합니다.TraceEnable  **Off**

   **IIS** ( [설명서](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs) 참조)에서 다음 구성을 수행하십시오.

   * **요청 필터링** 역할 서비스 또는 기능이 설치되어 있는지 확인합니다.
   * **요청 필터링** 창에서 HTTP 동사 탭을 클릭한 다음 거부 동사를 클릭합니다. [작업] 창의 열린 대화 상자에 TRACE을 입력합니다.

* 배너 제거:

   **Apache에서** /etc/apache2/conf.d/security를 편집합니다.

   * ServerSignature **Off**
   * ServerTokens **Prod**

   **IIS** ( [설명서](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs) 참조)에서 다음 구성을 수행하십시오.

   * **URLScan**&#x200B;을(를) 설치합니다.
   * **RemoveServerHeader=1**&#x200B;이(가) 있도록 **Urlscan.ini** 파일을 편집합니다.


* 쿼리 크기를 제한하여 중요한 파일이 업로드되지 않도록 합니다.

   **Apache** ( [설명서](http://httpd.apache.org/docs/2.2/mod/core.html#limitrequestbody) 참조)에서 / 디렉토리에  **** LimitRequestBodydirective(바이트 크기)를 추가합니다.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **IIS에서** ( [설명서](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits) 참조) 콘텐츠 필터링 옵션 **에서 maxAllowedContentLength** (허용되는 최대 내용 길이)를 설정합니다.

관련 항목:

* [Adobe Marketing Cloud 규격 개요](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign 보안 개요](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
