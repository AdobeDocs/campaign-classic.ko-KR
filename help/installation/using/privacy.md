---
product: campaign
title: 개인 정보 보호
description: 개인 정보 보호에 대해 따라야 하는 모범 사례에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 4%

---

# 개인 정보 보호 {#privacy}

![](../../assets/v7-only.svg)

## 개인 정보 보호 요청

Adobe Campaign은 GDPR 및 CCPA에 대한 개인 정보 보호 규정을 준수하는 데 도움이 되는 도구를 제공합니다.

개인 정보 관리의 정의와 Adobe Campaign의 구현 단계에 대한 일반적인 정보는 [이 페이지](../../platform/using/privacy-management.md)을 참조하십시오. 또한 모범 사례와 사용자 프로세스 및 성향에 대한 개요를 확인할 수 있습니다.

## URL 개인화 {#url-personalization}

컨텐츠에 개인화된 링크를 추가할 때는 잠재적인 보안 격차를 방지하기 위해 항상 URL의 호스트 이름 부분에 개인화를 사용하지 마십시오. 모든 URL 속성 &lt;`a href="">` 또는 `<img src="">`에 다음 예를 사용해서는 안 됩니다.

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 권장 사항

유효성을 검사하고 위에서 사용하지 않는지 확인하려면 [Campaign 일반 쿼리 편집기](../../platform/using/steps-to-create-a-query.md)를 통해 추적 URL 표에 대한 쿼리를 실행하거나 [쿼리 활동](../../workflow/using/query.md)에서 필터 기준을 사용하는 워크플로우를 만드십시오.

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

또한 Campaign 20.2와 [!DNL Gold Standard] 릴리스 이후 개선 사항을 사용하여 이전 빌드에서 생성된 URL을 비활성화할 수 있습니다. 이 기능은 기본적으로 비활성화됩니다. [고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 연락하여 이 기능을 활성화할 수 있습니다.

[!DNL Gold Standard] 19.1.4를 실행하는 경우 추적 링크를 사용한 푸시 알림 게재 또는 앵커 태그를 사용한 게재에 문제가 발생할 수 있습니다. 그럴 경우 URL 서명을 비활성화하는 것이 좋습니다.

Campaign을 온-프레미스에서 실행 중인지 아니면 하이브리드 아키텍처에서 실행 중인지 여부에 따라 [고객 지원 센터](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html)에 연락하여 URL 서명을 비활성화해야 합니다.

하이브리드 아키텍처에서 Campaign을 실행하는 경우 URL 서명을 사용하기 전에 호스팅된 중간 소싱 인스턴스가 다음과 같이 업그레이드되었는지 확인하십시오.
* 온-프레미스 마케팅 인스턴스 전
* 온-프레미스 마케팅 인스턴스와 동일한 버전 또는 약간 더 높은 버전으로 마이그레이션

그렇지 않으면 이러한 문제 중 일부가 발생할 수 있습니다.
* 중간 소싱 인스턴스를 업그레이드하기 전에 이 인스턴스를 통해 URL이 서명 없이 전송됩니다.
* 중간 소싱 인스턴스가 업그레이드되고 두 인스턴스에서 URL 서명이 활성화되면 서명 없이 이전에 전송된 URL이 거부됩니다. 이유는 마케팅 인스턴스에서 제공한 추적 파일에 의해 서명이 요청되기 때문입니다.

이전 빌드에서 생성된 URL을 비활성화하려면 모든 Campaign 서버에서 동시에 다음 단계를 수행하십시오.

1. 서버 구성 파일(serverConf.xml)에서 **blockRedirectForUnsignedTrackingLink**&#x200B;을 **true**&#x200B;로 변경합니다.
1. **nlserver** 서비스를 다시 시작합니다.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

URL 서명을 활성화하려면 모든 Campaign 서버에서 동시에 다음 단계를 수행하십시오.

1. 서버 구성 파일(serverConf.xml)에서 **signEmailLinks**&#x200B;을 **false**&#x200B;로 변경합니다.
1. **nlserver** 서비스를 다시 시작합니다.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

## 데이터 제한

낮은 권한 인증 사용자가 암호화된 암호를 액세스할 수 없도록 해야 합니다. 이를 위해 두 가지 주요 방법이 있습니다. 암호 필드에만 또는 전체 엔터티에 대한 액세스를 제한합니다(빌드 >= 8770 필요).

이 제한 사항으로 암호 필드를 제거할 수 있지만, 모든 사용자의 인터페이스에서 외부 계정에 액세스할 수 있도록 할 수 있습니다. [이 페이지](../../configuration/using/restricting-pii-view.md)를 참조하십시오.

1. **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**&#x200B;로 이동합니다.

1. 새 **[!UICONTROL Extension of a schema]**&#x200B;을(를) 만듭니다.

   ![](assets/privacy-data-restriction.png)

1. **[!UICONTROL External Account]** (extAccount)을 선택합니다.

1. 마지막 마법사 화면에서 새 srcSchema를 편집하여 모든 암호 필드에 대한 액세스를 제한할 수 있습니다.

   기본 요소(`<element name="extAccount" ... >`)를 다음과 같이 바꿀 수 있습니다.

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
   >`$(loginId) = 0 or $(login) = 'admin'` 을 `hasNamedRight('admin')` 로 대체하여 관리자 권한이 있는 모든 사용자가 이러한 암호를 볼 수 있도록 할 수 있습니다.

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

   IIS의 경우 [이 페이지](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)를 참조하십시오.

   Apache의 경우 파일을 **/var/www/robots.txt** (Debian)에 배치할 수 있습니다.

1. 경우에 따라 보안 측면에서 **robots.txt** 파일을 추가해도 충분하지 않습니다. 예를 들어, 다른 웹 사이트에 페이지에 대한 링크가 포함되어 있으면 검색 결과에 표시될 수 있습니다.

**robots.txt** 파일 외에 **X-Robots-Tag** 헤더를 추가하는 것이 좋습니다. Apache 또는 IIS와 **serverConf.xml** 구성 파일에서 이 작업을 수행할 수 있습니다.

자세한 내용은 [이 문서](https://developers.google.com/search/reference/robots_meta_tag)를 참조하십시오.
