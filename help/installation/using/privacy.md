---
solution: Campaign Classic
product: campaign
title: 개인 정보
description: 개인정보 보호와 관련하여 따라야 할 모범 사례에 대해 자세히 알아보십시오.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 4%

---


# 개인 정보 {#privacy}

## 개인 정보 요청

Adobe Campaign은 GDPR 및 CCPA에 대한 개인 정보 보호 규정을 준수하는 데 도움이 되는 도구를 제공합니다.

개인 정보 관리의 정의와 Adobe Campaign의 구현 단계에 대한 자세한 내용은 [이 페이지](../../platform/using/privacy-management.md)을 참조하십시오. 또한 모범 사례와 사용자 프로세스 및 성향에 대한 개요를 확인할 수 있습니다.

## URL 개인화

콘텐츠에 개인화된 링크를 추가할 때 잠재적인 보안 격차를 방지하기 위해 항상 URL의 호스트 이름 부분에 개인화를 사용하지 마십시오. 다음 예는 모든 URL 특성 &lt;`a href="">` 또는 `<img src="">`에서 사용해서는 안 됩니다.

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 권장 사항

상기를 사용하고 있지 않은지 확인하고 확인하려면 [캠페인 범용 쿼리 편집기](../../platform/using/steps-to-create-a-query.md)를 통해 추적 URL 테이블에 대한 쿼리를 실행하거나 [쿼리 활동](../../workflow/using/query.md)에서 필터 기준이 있는 워크플로우를 만드십시오.

예제:

1. 워크플로우를 만들고 쿼리 활동을 추가합니다. 자세히 알아보기

1. 쿼리 활동을 열고 다음과 같이 nmsTrackingUrl 테이블에 필터를 만듭니다.소스 URL은 http://&lt;% 또는 소스 URL은 https://&lt;%로 시작합니다.

1. 워크플로우를 실행하고 결과가 있는지 확인합니다.

1. 그렇다면 출력 전환을 열어 URL 목록을 확인합니다.

<img src="assets/privacy-query-dynamic-url.png">

### 서명 메커니즘

보안을 개선하기 위해 이메일의 링크 추적을 위한 새 서명 메커니즘은 빌드 19.1.4(9032@3a9dc9c)에 도입되었으며 빌드 19.1.4(9032@3a9dc9c) 및 Campaign 20.2에서 사용할 수 있습니다. 이 옵션은 모든 고객에 대해 기본적으로 활성화됩니다.

>[!NOTE]
>
>잘못된 형식의 서명된 URL을 클릭하면 다음 오류가 반환됩니다.&quot;요청한 URL &#39;.. &#39;을(를) 찾을 수 없습니다.&quot;

또한 빌드 19.1.4(9032@3a9dc9c 및 9032@800be2e) 및 Campaign 20.2에서 호스팅 및 하이브리드 고객은 향상된 기능을 사용하여 이전 빌드에서 생성된 URL을 비활성화할 수 있습니다. 이 옵션은 기본적으로 비활성화됩니다. [고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 연락하여 이 기능을 활성화할 수 있습니다.

이 새 메커니즘을 활성화하려면 온-프레미스 고객이 모든 Campaign 서버에서 다음 단계를 수행해야 합니다.

1. 서버 구성 파일(serverConf.xml)에서 **blockRedirectForUnsignedTrackingLink**&#x200B;을 **true**&#x200B;로 변경합니다.
1. **nlserver** 서비스를 다시 시작합니다.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

빌드 19.1.4(9032@3a9dc9c)에서 실행하는 고객은 추적 링크를 사용하여 푸시 알림 배달 또는 앵커 태그를 사용한 배달과 관련된 문제를 경험할 수 있습니다. 이러한 경우 Adobe은 링크 추적을 위해 새 서명 메커니즘을 비활성화할 것을 권장합니다.

**호스팅 고객과 하이브리드** 고객은 이 메커니즘을  [비활성화하려면 고객 ](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) 지원 센터에 문의해야 합니다.

**온-프레미스 고객** 은 아래 단계를 따릅니다.

1. 서버 구성 파일(serverConf.xml)에서 **signEmailLinks**&#x200B;을(를) **false**&#x200B;로 변경합니다.
1. **nlserver** 서비스를 다시 시작합니다.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

## 데이터 제한

낮은 권한 인증 사용자에 의해 암호화된 암호에 액세스할 수 없도록 해야 합니다. 이를 위해서는 두 가지 주요 방법이 있습니다.암호 필드에만 또는 전체 엔티티에 대한 액세스를 제한합니다(빌드 >= 8770 필요).

이 제한을 통해 암호 필드를 제거할 수 있지만 인터페이스에서 모든 사용자에 대해 외부 계정에 액세스할 수 있도록 할 수 있습니다. [이 페이지](../../configuration/using/restricting-pii-view.md)를 참조하십시오.

1. **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**&#x200B;로 이동합니다.

1. 새 **[!UICONTROL Extension of a schema]**&#x200B;을(를) 만듭니다.

   ![](assets/privacy-data-restriction.png)

1. **[!UICONTROL External Account]**(extAccount)을 선택합니다.

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

   확장된 srcSchema는 다음과 같습니다.

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
   >`$(loginId) = 0 or $(login) = 'admin'`을(를) `hasNamedRight('admin')`에 다시 배치하여 관리자 권한이 있는 모든 사용자가 이러한 암호를 볼 수 있도록 할 수 있습니다.

## PII가 포함된 페이지 보호

사내 고객은 미러 페이지, 웹 애플리케이션 등과 같은 개인 정보를 포함할 수 있는 페이지를 보호할 것을 적극 권장합니다.

이 절차의 목적은 이러한 페이지가 인덱싱되지 않도록 하여 잠재적인 보안 위험을 방지하는 것입니다. 다음은 유용한 아티클입니다.

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

페이지를 보호하려면 다음 단계를 수행합니다.

1. 웹 서버(Apache 또는 IIS)의 루트에 robots.txt 파일을 추가합니다. 파일의 내용은 다음과 같습니다.

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   IIS의 경우 [이 페이지](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files)를 참조하십시오.

   Apache의 경우 **/var/www/robots.txt**(Debian)에 파일을 배치할 수 있습니다.

1. 경우에 따라 보안 측면에서 **robots.txt** 파일을 추가해도 충분하지 않습니다. 예를 들어 다른 웹 사이트에 페이지에 대한 링크가 포함되어 있으면 검색 결과에 표시될 수 있습니다.

**robots.txt** 파일 외에 **X-Robots-Tag** 헤더를 추가하는 것이 좋습니다. Apache 또는 IIS와 **serverConf.xml** 구성 파일에서 이 작업을 수행할 수 있습니다.

자세한 내용은 [이 문서](https://developers.google.com/search/reference/robots_meta_tag)를 참조하십시오.
