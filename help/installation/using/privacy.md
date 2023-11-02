---
product: campaign
title: 개인화 및 개인 정보 보호
description: 개인 정보 보호 및 개인화에 대한 보안 모범 사례 알아보기
feature: Installation, Privacy, Privacy Tools, URL Personalization
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: a2106e55617209f28da42c50008d16188563b2da
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 4%

---

# 개인화 및 개인 정보 보호 {#privacy}

## URL 개인화 {#url-personalization}

콘텐츠에 개인화된 링크를 추가할 때 잠재적인 보안 차이를 방지하기 위해 항상 URL의 호스트 이름 부분에 개인화를 두지 마십시오. 다음 예제는 모든 URL 특성 &lt;`a href="">` 또는 `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### 추천

위의 을(를) 사용하고 있지 않은지 확인하고 확인하려면 다음을 통해 추적 URL 테이블에서 쿼리를 실행합니다. [Campaign 일반 쿼리 편집기](../../platform/using/steps-to-create-a-query.md) 또는 의 필터 조건으로 워크플로우를 만듭니다. [쿼리 활동](../../workflow/using/query.md).

예제:

1. 워크플로우 만들기 및 추가 **쿼리** 활동. [자세히 알아보기](../../workflow/using/query.md)

1. 를 엽니다. **쿼리** 활동 및 필터 만들기 `nmsTrackingUrl` 다음과 같은 표:

   `source URL starts with http://<% or source URL starts with https://<%`

1. 워크플로우를 실행하고 결과가 있는지 확인합니다.

1. 그럴 경우 출력 전환을 열어 URL 목록을 확인합니다.

   ![](assets/privacy-query-dynamic-url.png)


### URL 서명

보안을 개선하기 위해 이메일의 링크를 추적하는 서명 메커니즘이 도입되었습니다. 빌드 19.1.4(9032@3a9dc9c) 및 20.2부터 사용할 수 있습니다. 이 기능은 기본적으로 활성화되어 있습니다.

>[!NOTE]
>
>형식이 잘못된 서명 URL을 클릭하면 이 오류가 반환됩니다. `Requested URL '…' was not found.`

또한 향상된 기능을 사용하여 이전 빌드에서 생성된 URL을 비활성화할 수 있습니다. 이 기능은 기본적으로 비활성화되어 있습니다. 다음으로 연락할 수 있습니다. [고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 이 기능을 활성화하려면 다음을 수행하십시오.

19.1.4 빌드에서 실행 중인 경우 추적 링크를 사용한 푸시 알림 게재 또는 앵커 태그를 사용한 게재 문제가 발생할 수 있습니다. 이 경우 URL 서명을 비활성화하는 것이 좋습니다.

Campaign 호스팅, 관리 Cloud Service 또는 하이브리드 고객은 다음에 연결해야 합니다. [고객 지원 센터](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) URL 서명이 비활성화되어 있습니다.

하이브리드 아키텍처에서 Campaign을 실행하는 경우 URL 서명을 활성화하기 전에 호스팅된 중간 소싱 인스턴스가 다음과 같이 업그레이드되었는지 확인하십시오.

* 첫 번째 온프레미스 마케팅 인스턴스
* 그런 다음 온프레미스 마케팅 인스턴스와 동일한 버전 또는 약간 더 높은 버전으로 업그레이드합니다

그렇지 않으면 다음 문제 중 일부가 발생할 수 있습니다.

* 중간 소싱 인스턴스가 업그레이드되기 전에 이 인스턴스를 통해 서명 없이 URL이 전송됩니다.
* 중간 소싱 인스턴스가 업그레이드되고 두 인스턴스에서 URL 서명이 활성화되면 서명 없이 이전에 전송된 URL이 거부됩니다. 그 이유는 마케팅 인스턴스가 제공한 추적 파일에 의해 서명이 요청되기 때문입니다.

이전 빌드에서 생성된 URL을 비활성화하려면 모든 Campaign 서버에서 동시에 다음 단계를 수행하십시오.

1. 서버 구성 파일(`serverConf.xml`), **blockRedirectForUnsignedTrackingLink** 옵션 대상 **true**.
1. 다시 시작 `nlserver` 서비스.
1. 다음에서 `tracking` 서버, 다시 시작 `web` 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS).

URL 서명을 활성화하려면 모든 Campaign 서버에서 동시에 다음 단계를 수행합니다.

1. 서버 구성 파일(`serverConf.xml`), 변경 **signEmailLink** 옵션, 대상 **true**.
1. 다시 시작 **nlserver** 서비스.
1. 다음에서 `tracking` 서버, 다시 시작 `web` 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS).

## 데이터 제한

권한이 낮은 인증된 사용자가 암호화된 암호에 액세스할 수 없도록 해야 합니다. 이렇게 하려면 암호 필드에만 또는 전체 엔터티(빌드 >= 8770 필요)에 대한 액세스를 제한하십시오.

이 제한 사항을 사용하면 암호 필드를 제거할 수 있지만 모든 사용자의 인터페이스에서 외부 계정에 액세스할 수 있습니다. [자세히 알아보기](../../configuration/using/restricting-pii-view.md)

이렇게 하려면 아래 단계를 수행합니다.

1. 다음으로 이동 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** Campaign 탐색기 폴더.

1. 다음과 같이 데이터 스키마 만들기 **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. 선택 **[!UICONTROL External Account]** (extAccount).

1. 마지막 마법사 화면에서 새 &#39;srcSchema&#39;를 편집하여 모든 암호 필드에 대한 액세스를 제한합니다.

   주 요소(`<element name="extAccount" ... >`) 기준:

   ```sql
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

   이렇게 확장된 srcSchema는 다음과 같이 표시됩니다.

   ```sql
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
   >다음을 바꿀 수 있습니다. `$(loginId) = 0 or $(login) = 'admin'` 포함 `hasNamedRight('admin')` 관리자 권한이 있는 모든 사용자가 이러한 암호를 볼 수 있도록 허용합니다.

## PI가 있는 Protect 페이지

미러 페이지, 웹 애플리케이션 등과 같은 개인 정보(PI)가 포함될 수 있는 페이지를 보호하도록 온-프레미스 고객에게 강력히 권장합니다.

이 절차의 목표는 이러한 페이지가 색인화되지 않도록 하여 잠재적인 보안 위험을 방지하는 것입니다. 다음은 몇 가지 유용한 문서입니다.

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

페이지를 보호하려면 다음 단계를 따르십시오.

1. 추가 `robots.txt` 웹 서버(Apache 또는 IIS)의 루트에 있는 파일입니다. 다음은 파일의 컨텐츠입니다.

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   IIS의 경우 다음을 참조하십시오. [이 페이지](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   Apache의 경우 파일을에 배치할 수 있습니다 **/var/www/robots.txt** (Debian).

1. 경우에 따라 **robots.txt** 파일이 보안상 충분하지 않습니다. 예를 들어, 다른 웹 사이트에 페이지에 대한 링크가 포함되어 있으면 검색 결과에 표시될 수 있습니다.

   이외에도 **robots.txt** 파일, 를 추가하는 것이 좋습니다. **- 태그** 머리글입니다. Apache 또는 IIS와 **serverConf.xml** 구성 파일입니다.

   자세한 내용은 다음을 참조하십시오. [이 문서](https://developers.google.com/search/reference/robots_meta_tag).


## 개인정보 보호 요청

을(를) 참조하십시오 [이 페이지](../../platform/using/privacy-management.md) 개인정보 관리의 정의와 Adobe Campaign의 구현 단계에 대한 일반적인 정보입니다. 또한 모범 사례와 사용자 프로세스 및 가상 사용자에 대한 개요를 살펴볼 수 있습니다.
