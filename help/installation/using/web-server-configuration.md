---
product: campaign
title: 웹 서버 구성
description: 웹 서버 구성 기본 모범 사례에 대해 자세히 알아보기
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: dba90a154e08400ae6ab6478623a50d48d72207c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 웹 서버 구성 {#web-server-configuration}



다음은 웹 서버(Apache/IIS) 구성과 관련된 몇 가지 주요 모범 사례에 대해 설명합니다.

* 기본 오류 페이지를 변경합니다.

* 이전 SSL 버전 및 암호 비활성화:

  **Apache**&#x200B;에서 /etc/apache2/mods-available/ssl.conf을 편집하십시오. 예를 들면 다음과 같습니다.

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **IIS에서**([설명서](https://support.microsoft.com/en-us/kb/245030) 참조), 다음 구성을 수행하십시오.

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL에서 레지스트리 하위 키 추가
   * 시스템에서 기본적으로 협상되지 않는 프로토콜(예: TLS 1.2)을 사용하도록 설정하려면 **Protocol** 키 아래의 다음 레지스트리 키에서 DisabledByDefault 값의 DWORD 값 데이터를 0x0으로 변경하십시오.

     SCHANNEL\Protocol\TLS 1.2\Client

     SCHANNEL\Protocol\TLS 1.2\Server

  **SSL x.0 비활성화**

  SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: DWORD(32비트) 값을 1로

  SCHANNEL\Protocols\SSL 3.0\Server: 활성화됨: DWORD(32비트) 값을 0으로 변환

* **TRACE** 메서드 제거:

  **Apache에서**&#x200B;을(를) /etc/apache2/conf.d/security에서 편집하십시오. TraceEnable **해제**

  **IIS에서**([설명서](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs) 참조), 다음 구성을 수행하십시오.

   * **요청 필터링** 역할 서비스 또는 기능이 설치되어 있는지 확인하십시오.
   * **요청 필터링** 창에서 HTTP 동사 탭을 클릭한 다음 동사 거부를 클릭합니다. 작업 창에서 열린 대화 상자에 TRACE을 입력합니다.

* 배너 제거:

  **Apache**&#x200B;에서 /etc/apache2/conf.d/security를 편집합니다.

   * ServerSignature **꺼짐**
   * 서버 토큰 **Prod**

  **IIS에서** 다음 구성을 수행합니다.

   * **URLcan**&#x200B;을 설치합니다.
   * **RemoveServerHeader=1**&#x200B;이(가) 있도록 **Urlscan.ini** 파일을 편집합니다.

* 중요한 파일이 업로드되지 않도록 쿼리 크기 제한:

  **Apache**&#x200B;에서 / 디렉터리에 **LimitRequestBody** 지시문(크기(바이트)을 추가하십시오.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **IIS에서**([설명서](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits) 참조)의 콘텐츠 필터링 옵션에서 **maxAllowedContentLength**(최대 허용된 콘텐츠 길이)를 설정하십시오.

관련 항목:

* [Adobe Marketing Cloud 규정 준수 개요](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign 보안 개요](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#security)
