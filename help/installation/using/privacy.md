---
product: campaign
title: 개인 정보 보호
description: 개인 정보 보호에 대해 따라야 하는 모범 사례에 대해 자세히 알아보십시오
feature: URL Personalization, Privacy
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 4%

---

# 개인 정보 보호 {#privacy}

![](../../assets/v7-only.svg)

## 개인 정보 보호 요청

Adobe Campaign은 GDPR 및 CCPA에 대한 개인 정보 보호 규정을 준수하는 데 도움이 되는 도구를 제공합니다.

을(를) 참조하십시오. [이 페이지](../../platform/using/privacy-management.md) 개인 정보 관리의 정의와 Adobe Campaign의 구현 단계에 대한 일반적인 정보입니다. 또한 모범 사례와 사용자 프로세스 및 성향에 대한 개요를 확인할 수 있습니다.

## URL 개인화 {#url-personalization}

컨텐츠에 개인화된 링크를 추가할 때는 잠재적인 보안 격차를 방지하기 위해 항상 URL의 호스트 이름 부분에 개인화를 사용하지 마십시오. 다음 예제는 모든 URL 속성에서 사용해서는 안 됩니다. &lt;`a href="">` 또는 `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 권장 사항

유효성을 검사하고 위에서 사용하지 않는지 확인하려면 를 통해 추적 URL 표에 대한 쿼리를 실행하십시오. [Campaign 일반 쿼리 편집기](../../platform/using/steps-to-create-a-query.md) 또는 의 필터 기준으로 워크플로우를 만들 수 있습니다 [쿼리 활동](../../workflow/using/query.md).

예제:

1. 워크플로우를 만들고 쿼리 활동을 추가합니다. 자세히 알아보기.

1. 쿼리 활동을 열고 다음과 같이 nmsTrackingUrl 테이블에서 필터를 만듭니다. 소스 URL은 http://&lt;% 또는 소스 URL이 https://&lt;%로 시작합니다.

1. 워크플로우를 실행하고 결과가 있는지 확인합니다.

1. 그럴 경우 출력 전환을 열어 URL 목록을 확인합니다.

<img src="assets/privacy-query-dynamic-url.png">

### URL 서명

보안을 개선하기 위해 이메일의 링크를 추적하는 서명 메커니즘이 도입되었습니다. 빌드 19.1.4(9032@3a9dc9c) 및 Campaign 20.2에서 사용할 수 있습니다. 이 기능은 기본적으로 활성화되어 있습니다.

>[!NOTE]
>
>잘못된 형식의 서명된 URL을 클릭하면 이 오류가 반환됩니다. &quot;요청된 URL &#39;..&#39;을(를) 찾을 수 없습니다.&quot;

또한 Campaign 20.2 이후 및 [!DNL Gold Standard] 릴리스에서는 향상된 기능을 사용하여 이전 빌드에서 생성된 URL을 비활성화할 수 있습니다. 이 기능은 기본적으로 비활성화됩니다. 에 연결할 수 있습니다 [고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 을 클릭하여 이 기능을 활성화합니다.

19.1.4 빌드에서 실행 중인 경우 추적 링크를 사용한 푸시 알림 게재 또는 앵커 태그를 사용한 게재 문제가 발생할 수 있습니다. 그럴 경우 URL 서명을 비활성화하는 것이 좋습니다.

Campaign을 온-프레미스나 하이브리드 아키텍처에서 실행하든 간에 [고객 지원 센터](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) URL 서명을 사용할 수 없도록 설정했습니다.

하이브리드 아키텍처에서 Campaign을 실행하는 경우 URL 서명을 사용하기 전에 호스팅된 중간 소싱 인스턴스가 다음과 같이 업그레이드되었는지 확인하십시오.
* 온-프레미스 마케팅 인스턴스 전
* 온-프레미스 마케팅 인스턴스와 동일한 버전 또는 약간 더 높은 버전으로 마이그레이션

그렇지 않으면 이러한 문제 중 일부가 발생할 수 있습니다.
* 중간 소싱 인스턴스를 업그레이드하기 전에 이 인스턴스를 통해 URL이 서명 없이 전송됩니다.
* 중간 소싱 인스턴스가 업그레이드되고 두 인스턴스에서 URL 서명이 활성화되면 서명 없이 이전에 전송된 URL이 거부됩니다. 이유는 마케팅 인스턴스에서 제공한 추적 파일에 의해 서명이 요청되기 때문입니다.

이전 빌드에서 생성된 URL을 비활성화하려면 모든 Campaign 서버에서 동시에 다음 단계를 수행하십시오.

1. 서버 구성 파일(serverConf.xml)에서 **blockRedirectForUnsignedTrackingLink** to **true**.
1. 를 다시 시작합니다. **nlserver** 서비스.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

URL 서명을 활성화하려면 모든 Campaign 서버에서 동시에 다음 단계를 수행하십시오.

1. 서버 구성 파일(serverConf.xml)에서 **signEmailLinks** to **false**.
1. 를 다시 시작합니다. **nlserver** 서비스.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

## 데이터 제한

낮은 권한 인증 사용자가 암호화된 암호를 액세스할 수 없도록 해야 합니다. 이를 위해 두 가지 주요 방법이 있습니다. 암호 필드에만 또는 전체 엔터티에 대한 액세스를 제한합니다(빌드 >= 8770 필요).

이 제한 사항으로 암호 필드를 제거할 수 있지만, 모든 사용자의 인터페이스에서 외부 계정에 액세스할 수 있도록 할 수 있습니다. [이 페이지](../../configuration/using/restricting-pii-view.md)를 참조하십시오.

1. 들어가세요 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. 새 만들기 **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. 선택 **[!UICONTROL External Account]** (extAccount).

1. 마지막 마법사 화면에서 새 srcSchema를 편집하여 모든 암호 필드에 대한 액세스를 제한할 수 있습니다.

   기본 요소(`<element name="extAccount" ... >`)

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   따라서 확장된 srcSchema는 다음과 같을 수 있습니다.

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >바꿀 수 있습니다 `$(loginId) = 0 or $(login) = 'admin'` with `hasNamedRight('admin')` 관리자 권한이 있는 모든 사용자가 이러한 암호를 볼 수 있도록 허용

## PII가 포함된 페이지 보호

미러 페이지, 웹 애플리케이션 등과 같은 개인 정보가 포함될 수 있는 페이지를 보호할 것을 온-프레미스 고객에게 강력히 권장합니다.

이 절차의 목적은 이러한 페이지가 색인화되지 않도록 하여 잠재적인 보안 위험을 방지하는 것입니다. 다음은 몇 가지 유용한 문서입니다.

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

페이지를 보호하려면 다음 단계를 수행합니다.

1. 웹 서버(Apache 또는 IIS)의 루트에 robots.txt 파일을 추가합니다. 다음은 파일의 컨텐츠입니다.

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   IIS의 경우 다음을 참조하십시오 [이 페이지](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Apache의 경우 파일을 **/var/www/robots.txt** (Debian).

1. 경우에 따라 추가 **robots.txt** 보안 측면에서 파일이 충분하지 않습니다. 예를 들어, 다른 웹 사이트에 페이지에 대한 링크가 포함되어 있으면 검색 결과에 표시될 수 있습니다.

추가 **robots.txt** 파일, **X-Robots-Tag** 헤더. Apache 또는 IIS와 **serverConf.xml** 구성 파일.

자세한 내용은 [이 문서](https://developers.google.com/search/reference/robots_meta_tag).
